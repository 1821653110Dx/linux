# modify file permission
chmod {-R} {pv of owner}{pv of group}{pv of the others} {file}  
&emsp;pv = permission value  
&emsp;-R = recursion递归  
  
pv:  
&emsp;r 4  
&emsp;w 2  
&emsp;x 1  
&emsp;rwx 4+2+1=7  
# check file permission
ls -l  
# explain file permission
## column 1
- normal  
d directory  
p management  
l linkage file  
b block device file  
c charactor devive file  
s socket  
## column 2 3 4
r read  
w write  
x executable  
- none  
  
2 = owner permissions  
3 = group user permissions  
4 = the others' permissions  
## column 5
for normal file = number of linkage  
for directory file = number of 1st subdirectories  
## column 6 7 
6 = user name  
7 = group name  
## column 8
disk usage (byte)  
## column 9
last modification time  
## column 10
file name  
# change owner, group
## change owner
chown \[-R\] owner file/dir  
## change group
chgrp \[R\] group file/dir  

