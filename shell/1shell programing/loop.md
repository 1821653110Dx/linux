# for
```bash
#!/usr/bin/bash

if [ ! -d ./backup ]	# if dir ./backup not exsist
then
	mkdir ./backup
fi

flist=`ls`	# run ls | save to flist

for file_name in $flist # for each file_name in flist
do
	if [ $# = 1 ]	# if the number of return arguments of ls = 1
	then
		if [ $1 = $file_name ]	# if 1st argument = file_name
		then
			echo "$file_name found"	# printf "{ file_name } found\n"
			exit	# exit program
		fi
	else	## otherwise
		cp $file_name ./backup
		echo "$file_name copied"
	fi
done
```
# while
```bash
#!/usr/bin/bash

if [ $# = 2 ]	# if arguments received = 2
then
	loop=$2	# save 2nd argument to loop
else	# otherwise
	loop=5	# set loop to 5
fi

i=1	# set i = 1
while [ $i -lt $loop ]	# do the internal while i < loop
do
	> $1$i	# create an empty file named "{ first argument }{ i }"
	i = `expr $i + 1`	# calc i + 1 | overwrite to i
done
```
# break continue
```bash
#!/usr/bin/bash

if [ $# = 0 ]	# if received arguments = 0
then
	echo "Numeric arguments required\n"	# printf "Numeric arguments required\n"
	exit	# exit program
elif [ $# -gt 10 ]	# not previous condition and received arguments > 10
then
	echo "Only ten arguments allowed"
	exit
fi

for number	# for each number in reveiced arguments
do
	count=`expr $number % 2`	# calc number % 2 | save to count
	if [ $count = 1 ]	# if count = 1
	then
		continue	# next number
	else	# otherwise
		output="$output $number"	# overwite output with "{ output } { number }"
	fi
done
echo "Even numbers: $output"
```
