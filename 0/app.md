# add the appimage to the app list
<https://zhuanlan.zhihu.com/p/215507075>  
  
cp ***/tmp/.xxx/xxx.desktop*** to ***/usr/share/applications***  
edit the blow of ***xxx.desktop***  
```bash
Exec=xxx
Icon=xxx
```
## get the icon
get one from /tmp/.xxx/usr/share/application  
# Set default launcher for a file with specific format
<https://www.cnblogs.com/KoiC/p/17112703.html>  
  
add the below code to /usr/share/applications/defaults.list  
```bash
'unknownformat'=app.desktop;
```
# make app autostart
```txt
add '.desktop' to /etc/xdg/autostart
```
## can remove
mintupdate.desktop