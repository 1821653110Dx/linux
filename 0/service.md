# check status
## single services
systemct | status \<.service\> 
## all services
service --status-all
## let .sh autostart
为了实现目的，我们需要创建一个 systemd 启动服务，并把它放置在 /etc/systemd/system/ 目录下。

我们创建的 systemd 启动服务如下。请注意，这时后缀是 .service ，而不是 .sh 。

```javascript
$ vim auto_run_script.service

[Unit]
Description=Run a Custom Script at Startup
After=default.target

[Service]
ExecStart=/home/alvin/auto_run_script.sh

[Install]
WantedBy=default.target
```

从服务的内容可以看出来，我们最终还是会调用 /home/alvin/auto\_run\_script.sh 这个脚本。

然后，我们再把这个脚本放置在 /etc/systemd/systerm/ 目录下，之后我们再运行下面两条命令来更新 systemd 配置文件，并启动服务。

```javascript
$ systemctl daemon-reload
$ systemctl enable auto_run_script.service
```

万事俱备之后，我们就可以重启系统啦。

```javascript
$ reboot
```