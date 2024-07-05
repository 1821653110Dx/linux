# install
sudo add-apt-repository ppa:apt-fast/stable  
sudo apt-get install apt-fast  
select apt-get  
select yes  
set to 16  
sudo apt-fast update  
# 配置 APT-Fast

安装完 APT-Fast 后，您可以根据自己的需求自定义配置：

1使用 vi 或 nano 等文本编辑器打开以下配置文件：



```
sudo vi /etc/apt-fast.conf
```

2在配置文件中，找到 `_MAXNUM` 变量，并将其设置为期望的连接数。例如，如果希望将最大连接数设置为 `10`，可以使用以下配置：



```
_MAXNUM=10
```

3如果要在 Axel 和 Aria2 之间切换，请在配置文件中找到 `_DOWNLOADER` 行，并相应地更改下载管理器。例如，如果要使用 [Aria2](https://aria2.github.io/)，配置行可以改成：



```
_DOWNLOADER='aria2c --no-conf -c -j ${_MAXNUM} -x ${_MAXCONPERSRV} -s ${_SPLITCON} --min-split-size=${_MINSPLITSZ} --stream-piece-selector=${_PIECEALGO} -i ${DLLIST} --connect-timeout=600 --timeout=600 -m0 --header "Accept: */*"'
```

如果喜欢使用 [Axel](https://github.com/axel-download-accelerator/axel)，可以将配置行更改为：



```
_DOWNLOADER='axel -n ${_MAXNUM}'
```

<img width="720" height="445" src="../../_resources/ubuntu-apt-fast-5_faa61e376a1d4be9aec80db8a8990705.jpg"/>

配置 APT-Fast 下载管理器

4APT-Fast 可以利用多个镜像来加快软件包的下载速度。要配置镜像，需要设置 `MIRRORS` 参数。在该参数中，您可以添加或修改镜像列表。例如，您可以添加以下行来同时使用[腾讯云](https://mirrors.tencent.com/)和[阿里云](https://developer.aliyun.com/mirror/)的镜像：



```
MIRRORS=( 

 'http://archive.ubuntu.com/ubuntu, https://mirrors.cloud.tencent.com/ubuntu, https://mirrors.aliyun.com/ubuntu' 

 )
```

<img width="720" height="475" src="../../_resources/ubuntu-apt-fast-6_c4befb454a574c918ecccc133add959c.jpg"/>

配置 APT-Fast 多镜像源

5配置完成后，保存更改并退出文本编辑器。

## 步骤 3：使用 APT-Fast

APT-Fast 旨在与现有的 APT 命令无缝配合使用。以下是一些使用 APT-Fast 替代 APT 的示例：

1要使用 APT-Fast 更新软件包列表，请在「终端」中运行：



```
sudo apt-fast update
```

2要安装软件包，如 Htop，请在「终端」中运行：



```
sudo apt-fast install htop
```

3要使用 APT-Fast 更新系统软件包，请在「终端」中运行：



```
sudo apt-fast upgrade
```

<img width="720" height="445" src="../../_resources/ubuntu-apt-fast-7_7b200f20a9814d6a8e62aaca29802d56.jpg"/>

使用 APT-Fast 更新系统软件包

4要执行 Ubuntu 版本升级，如从 Ubuntu 20.04 升级到 22.04，请在「终端」中运行：



```
sudo apt-fast dist-upgrade
```

Ubuntu 版本升级可能需要一些时间，并且应谨慎进行。在继续之前，请确保先备份个人数据。

* * *