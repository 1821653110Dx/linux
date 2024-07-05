# match lines
### from files
#### the first 100 lines
head -n 100 \<file\>  
#### the last 50 lines
tail -n 50 \<file\>  
#### from 75 to the last line
tail -n +75 \<file\>  
#### from 100 to 200
sed -n '100,200p' \<file\>  
#### match lines with 'abc' from contents in file1 and file2
grep abc./file1 file2  
#### display number of lines containing 'abc' from file1
grep -c abc./file1 
#### match 'specified str'('ss') in row 1 and column 3 of 'file'
cat 'file' | grep 'ss' | sed -n '1p' | awk {'print $3'}  
&emsp;1p = row 1  
&emsp;$3 = column 3  
### from path
#### match files (contain directory) 
#### match files with names containing 'abc' from /root/
find /root/ -type f | xards grep 'abc'  
&emsp;-type f = find files only  
#### match '.php' files with names containing 'abc' from current path
find -name '*.php' | xargs grep -l 'abc'
#### match columns
### 1
awk '{print $1}'  
### from 1 to 9 
awk -F' ' '{print $1,$9}' file&emsp;&emsp;//' ' = space between columns  
  
awk -F',' '{print $1,$9}' file&emsp;&emsp;//',' = , between columns  
### 1 and 2
awk '{print $1 $2}' filename  
## match lines and columns
sed -n '2p' filename | awk '{print $1}'  

awk 'NR\=\=1 {print $2}' filename  
&emsp;&emsp;NR==1 = row 1
# match files
## match files named 'abc.log' from '/'
find / -name 'abc.log'  
## match files with names contain 'ab' from '/'
find / -name '\*ab\*'  
## match files with names contain 'a' and 'c' from '/'
find / -name '\*a\*c\*' 
## move all files in path 0 except A to path 
ls path0 | grep -v '^A$' | xargs mv -t path1  
&emsp;-v inversion反转  
## move all files in path 0 except A and B to path 1
ls path0 | grep -Ev '^A\$|^B$' | xargs mv -t path1  
&emsp;-E extend regular expressions拓展的正则表达式  
&emsp;-v inversion反转  
# command
## sort
### ascending sort in bytes  
du -b | sort -n  
### descening sort in MB  
du -m | sort -nr  
### descening sort in kb  
du -k | sort -nr  
### sort the 2nd column of 'test.txt' in ascending order, with space as the delimiter
sort -t ' ' -k2 test.txt  
### display the first n lines of 'test.txt'
head -n 5 test.txt  
