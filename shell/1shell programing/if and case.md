# if
```bash
#!/usr/bin/zsh

if [ -f $file ]   # if { file } is FILE
then
   echo "File $file exsists"   # print "File { file } exsists\n"
fi

if [ -d $HOME/$file ]   # if { HOME }/{ file } is DIR
then
    echo "File $file is in a dir\c" # print "File { file } is in a dir"
fi
```
```bash
#!/usr/bin/zsh

if [ $USER=root ]   # if USER = 'root'
then
    echo "root" ;   # print "root\n"
    echo "$UID" ;   # print "{ UID }\n"
else    # otherwise
    echo "user" ;   # print "user\n"
    echo "$UID" ;   # print "{ UID }\n"
fi
```
```bash
#!/usr/bin/zsh

if [ $USER = root ] # if { USER } = 'root'
then
    echo "root" ;   # print "root\n"
elif [ $USER = user ]   # not previous condition and { USER } = 'user'
then
    echo "user" ;   # print "user\n"
else    # otherwise
    echo "other user\c" ;   # print "other user"
fi
```
```bash
#!/usr/bin/zsh

if [ $UID = 0 ]  # if UID = 0
then
    echo "please run" ; # print "please run\n"
    if [ -x ./test.sh ] # if ./test.sh is executable
    then
        print "run" ;   # print "run\n"
    fi
else    # otherwise
    echo "switch user root\c"   # print "switch user root"
fi
```
# case(str only)
```bash
#!/usr/bin/zsh

## echo "input integer :", let user input "{ integer }" | save to num
echo "input integer :\c" ;
read num ;

case $num in	# switch to do which by num
	1)	# if = '1'
		echo "Monday"	# print "Monday\n"
		;;
	2)	# not previous condition and = '2'
		echo "Tuesday"	# print "Tuesday\n"
		;;
	3) # not previous condition and = '3'
		echo "Wednesday"	# print "Wednesday\n"
		;;
	4)	# not previous condition and = '4'
		echo "Thursday"	# print "Thursday\n"
		;;
	5)	# not previous condition and = '5'
		echo "Friday"	# print "Friday\n"
		;;
	6)	# not previous conditiont and = '6'
		echo "Saturday"	# print "Saturday\n"
		;;
	7)	# not previous condition and = '7'
		echo "Sunday"	# print "Sunday\n"
		;;
	*)	# otherwise
		echo "error\n"	# print "error\n"
		;;
esac
```
```bash
#!/usr/bin/zsh

if [ $# -eq 0 ]	# if received argument counts = 0
then
	echo "No argument is declared"	# print "No argument is declared\n"
	exit	# exit program
fi

case $1 in	# swich next step by first received argument
	fil12)	# if = 'file1'
		echo "User selects file1"	# print "User selects file1\n"
		;;
	file2)	# not previous condition and = 'file2'
		echo "User selects file2"	# print "User selects file2\n"
		;;
	*)	# otherwise
		echo "You must select either file1 or file2!"# print "You must select either file1 or file2!\n"
		;;
esac
```