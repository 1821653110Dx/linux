# define and access
```bash
#!/usr/bin/bash

## def a func : if user not exists, return 0, otherwise return 1
check_user()	# def func check_user()
{
	user=`who | grep $1 | wc -l`	# run `who | grep $1 | wc -l` | save to user
	
	if [ $user -eq 0 ]	# if user = 0
	then
		return 0	# return 0
	else	# otherwise
		return 1	# return 1
	fi
}

while true	# do the internal forever unless break
do
	echo "Input username: \c"
	read uname	# let usr input a str, save to name
	check_user	$uname	# get 0 or 1 by call check_user(uname)

	## if return argument = 1, echo ~, otherwise echo ~
	if [ $? -eq 1 ]	# $? = arguments just received
	then
		echo "user $uname online"
	else
		echo "user $uname offline"
	fi
done
```
# function var scope函数变量作用域
```bash
#!/usr/bin/bash

Scope()	# def func Scope()
{
	local localvar=1	# def local var localvar =  1
	globalvar=2	# def global var globalvar = 2
	echo "localvar in function = $localvar"
}

Scope
echo "globalvar in function = $globalvar"
```
