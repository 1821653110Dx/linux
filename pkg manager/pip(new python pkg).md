# venv
> you can upgrade pip  in venv
## create
virtualenv venv
## activate
source venv/bin/activate
## deactivate
deactivate

# pkg
## List
### Installed
	pip3 list
### can-be-upgraded
	pip3 list --outdated

## Remove
	pip3 uninstall {pkg}

## Upgrade
	pip3 install -U {pkg}

## Rm the downloads
	pip3 cache purge

# change source for CURRENT USER
## temporary
- 清华源
pip3 install markdown -i https://pypi.tuna.tsinghua.edu.cn/simple
- 阿里源
pip3 install markdown -i https://mirrors.aliyun.com/pypi/simple/
- 腾讯源
pip3 install markdown -i http://mirrors.cloud.tencent.com/pypi/simple
- 豆瓣源
pip3 install markdown -i http://pypi.douban.com/simple/

## forever
- 清华源
pip3 config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
- 阿里源
pip3 config set global.index-url https://mirrors.aliyun.com/pypi/simple/
- 腾讯源
pip3 config set global.index-url http://mirrors.cloud.tencent.com/pypi/simple
- 豆瓣源
pip3 config set global.index-url http://pypi.douban.com/simple/

## switch to the original
pip3 config unset global.index-url