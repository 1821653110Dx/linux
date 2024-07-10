# batch批量
## create
touch test{0001...2000}.txt  
## rename
rename -v 's/abc/ABC/' *
- \* all files
- -n non-action
- -v print the result if successed

# list
	tree [选项] [目录 ]
	-a 显示所有文件，包括隐藏文件
	-d 只显示目录
	-f 显示每个文件的绝对路径
	-i 不显示树枝，常与 -f 参数配合使用
	-L level 遍历目录的最大层数，level为大于0的正整数
	-h 大小
# cp files
	if dir many
		rsync -aPv [Source Dir] [Target Dir] (--delete)
		# without --delete, append
		# with --delete, Source Dir = Target Dir
		# --remove-source-files
		# --exclude='*.txt'
		# --append-verify: continue to transfer file from the last interruption-point and check the integrity完整性 of the file
	if dir less
		cd [Source Dir]; tar cf - . | (cd [Target Dir]; tar xvf -)
# synchronization
rsync -rtvu --delete source_folder/ destination_folder/
# remove files
## bash
    rm -r !(a)
    rm -r !(a|b)
## zsh
    # make sure you've add "setopt extended_glob" to .zshrc
    rm ^a
    rm ^(alb)
## quick
	rsync --delete-before -av ~/trash/ ./

# encoding编码
## check
- cmd  

`file -i file_name`
- vim

`:set fileencoding`
## modify
- cmd

`iconv -f original_encoding -t wanted_encoding input_file -o output_file`
- vim

`set fileencoding=utf-8`

# pack_unpack
## p7zip(recommend)
-  normal_pack
	- 7z a -r  xxx.7z xxx/*  -mmt=16 -ms -m0=lzma2
		- -xr\! = ignore dir
		- -x\! = ignore file
		- -mmt = multi threads
		- -ms solid-mode
		- -sdel = delete source files
		- limit_pack
		- mx=9 
		- ms=200m -- 开启固实模式，设置固实数据流大小为200MB。
		- mf -- 开启可执行文件压缩过滤器。
		- mhc -- 开启档案文件头压缩。
		- mhcf -- 开启档案文件头完全压缩。
		- -m0 设置算法
- pack into many pkgs, size of each = 10m
	- 7z a -r  archives.7z *.txt -v10m
-  unpack
	- 7z x manager.7z -r -o/home/xx
- extract all .txt from the .7z
	- 7z e -r archives.7z \*.txt 
-  list
	- 7z l &lt;pkg&gt;
	- 7z l -slt archives.7z
- update *.doc in archive.zip
	- 7z u archive.zip *.doc
- rm dir a in archive.zip
	- 7z d -r archive.zip a
- append ./*.txt to archive.zip
	- 7z a archive.zip *.txt
 - compression ratio
	 - mx0 仅存储不压缩，zip大小等同原始文件夹
	- mx1 极速压缩
	- mx3 快速压缩
	- mx5 标准压缩
	- mx7 最大压缩
	- mx9 极限压缩
## tar
-  pack(.tar.gz)
```bash
tar -P -cfz .tar.gz path
z = .tar.gz
J = .tar.xz
j = .tar.bz2
```
-  unpack
```bash
tar –xvf file.tar -C path
tar -xzvf file.tar.gz
tar -xjvf file.tar.bz2
tar –xZvf file.tar.Z
```
-  check
```bash
tar -tf .tar
```

## problem
	After decompressing .zip, the file name displays garbled code
		unar -e GBK xxx.zip

# link
## symbolic link(windows's shortcuts, suggested)
> points to the path of a file
>> the file can be nonexistent when creating
>> support  dir
>> can cross the file system

ln -s file symlink.link
> echo "123" > symlink.link

## hard link
> points to the innode文件索引 of a file
>> the file must be existent when creating
>> not supprt dir
>> can't cross the file system
>> access spees speed > symlink
>> occpied mem < symlink

ln file hardlink.link
> echo "123" > hardlink.link

# else
## 图片反色
    find . -name "*.png" -type f -exec sh -c 'convert $0 $0 && convert -negate $0 $0' {} \;

