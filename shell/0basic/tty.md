# change font size
- sudo dpkg-reconfigure console-setup
- OK
- OK
- select Terminus
- set font size

# display img
## packages
    sudo apt-fast install fim

    
    
# tty lan
## en
    LANG = en
## cn
    LANG = zh_CN.UTF-8
# problems
## can not display chinese characters
https://www.cnblogs.com/boyzgw/p/6610323.html
- sudo apt-get install fbterm
- sudo adduser username video
- sudo fbterm
> if still not display chinese characters:
>> LANG=zh_CN.utf-8 fbterm
