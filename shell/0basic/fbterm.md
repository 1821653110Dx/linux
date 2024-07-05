# basic configuration
## configuration file
~/.fbtermrc 
## modify font-type
font-names=DejaVu Sans Mono,WenQuanYi Zen Hei Sharp
> en_font: DejaVu Sans Mono
> 
> cn_font： WenQuanYi Zen Hei Sharp
## modify font-size
font-size=16
# display information about fbterm的
## install packages needed
    sudo apt-fast install fbset
## usage
sudo fbset -i
# print screen
## packages
    sudo apt-fast install fbgrab
## usage
- print the screen of tty_N
    - sudo fbgrab -c N filename.png
- switch to tty_N. then print the screen
    - sudo fbgrab -C N filename.png
- print the screen after N seconds
    - sudo fbgrab -s N filename.png
