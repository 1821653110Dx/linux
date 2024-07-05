# paste/cut/cp/del
## paste/cut/cp/del in '
- pi'
- di'
- yi'
- "_dd'
## paste/cut/cp/del in '' and ''
- pa'
- da'
- ya'
- "_dd'
> the same for "", (), [], {}, <>

# insert
- insert current date and time
	- :r!
- insert stdout of cmd
	- :r! cmd
- insert a file
	- :r file_name

# complete
	Ctrl+X Ctrl+L	整行补全
	Ctrl+X Ctrl+N	根据当前文件里关键字补全
	Ctrl+X Ctrl+K	根据字典补全
	Ctrl+X Ctrl+T	根据同义词字典补全
	Ctrl+X Ctrl+I	根据头文件内关键字补全
	Ctrl+X Ctrl+]	根据标签补全
	Ctrl+X Ctrl+F	补全文件名
	Ctrl+X Ctrl+D	补全宏定义
	Ctrl+X Ctrl+V	补全vim命令
	Ctrl+X Ctrl+U	用户自定义补全方式
	Ctrl+X Ctrl+S	拼写建议
# repeat
	.