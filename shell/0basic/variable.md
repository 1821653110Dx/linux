# use
```bash
echo $variable
```
# check all variables
```bash
set
```
# custom variable
## define
```bash
variable = value
```
## change value
```bash
variable='$variable'new_value
```
## remove
```bash
unset variable
```
## permanently add
### for current user
add the following txt to '~/.bashrc' or '~/.bash_profile'(suggected) 
variable=value 
### for all user
add the folling txt to '/etc/enviroment'  
variable=value

# PATH
    export PATH="$PATH:"

