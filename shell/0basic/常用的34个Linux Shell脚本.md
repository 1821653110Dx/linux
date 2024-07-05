**strong text****（1）用户猜数字**

```
`

1.  #!/bin/bash
    

3.  # 脚本生成一个 100 以内的随机数,提示用户猜数字,根据用户的输入,提示用户猜对了,
    
4.  # 猜小了或猜大了,直至用户猜对脚本结束。
    

6.  # RANDOM 为系统自带的系统变量,值为 0‐32767的随机数
    
7.  # 使用取余算法将随机数变为 1‐100 的随机数
    
8.  num=$[RANDOM%100+1]
    
9.  echo "$num"
    

11. # 使用 read 提示用户猜数字
    
12. # 使用 if 判断用户猜数字的大小关系:‐eq(等于),‐ne(不等于),‐gt(大于),‐ge(大于等于),
    
13. # ‐lt(小于),‐le(小于等于)
    
14. while :
    
15. do 
    
16.  read -p "计算机生成了一个 1‐100 的随机数,你猜: " cai  
    
17.     if [ $cai -eq $num ]   
    
18.     then     
    
19.         echo "恭喜,猜对了"     
    
20.         exit  
    
21.      elif [ $cai -gt $num ]  
    
22.      then       
    
23.             echo "Oops,猜大了"    
    
24.        else      
    
25.             echo "Oops,猜小了" 
    
26.   fi
    
27. done
    

`

![](https://csdnimg.cn/release/blogv2/dist/pc/img/newCodeMoreWhite.png)


```

**（2）查看有多少远程的 IP 在连接本机**

```


1.  #!/bin/bash
    

3.  #!/bin/bash
    
4.  # 查看有多少远程的 IP 在连接本机(不管是通过 ssh 还是 web 还是 ftp 都统计) 
    

6.  # 使用 netstat ‐atn 可以查看本机所有连接的状态,‐a 查看所有,
    
7.  # -t仅显示 tcp 连接的信息,‐n 数字格式显示
    
8.  # Local Address(第四列是本机的 IP 和端口信息)
    
9.  # Foreign Address(第五列是远程主机的 IP 和端口信息)
    
10. # 使用 awk 命令仅显示第 5 列数据,再显示第 1 列 IP 地址的信息
    
11. # sort 可以按数字大小排序,最后使用 uniq 将多余重复的删除,并统计重复的次数
    
12. netstat -atn  |  awk  '{print $5}'  | awk  '{print $1}' | sort -nr  |  uniq -c
    


```

**(3）helloworld**

```


1.  #!/bin/bash
    

3.  function example {
    
4.  echo "Hello world!"
    
5.  }
    
6.  example
    


```

**（4）打印 tomcat 的pid**

```


1.  #!/bin/sh`
    

3.  v1="Hello"
    
4.  v2="world"
    
5.  v3=${v1}${v2}
    
6.  echo $v3
    

8.  pidlist=`ps -ef|grep apache-tomcat-7.0.75|grep -v "grep"|awk '{print $2}'`
    
9.  echo $pidlist
    
10. echo "tomcat Id list :$pidlist"  //显示pid
    


```

**（5）脚本编写 剪刀 、 石头、布游戏**

```
`

1.  #!/bin/bash
    

3.  game=(石头 剪刀 布)
    
4.  num=$[RANDOM%3]
    
5.  computer=${game[$sum]}
    

7.  echo "请根据下列提示选择您的出拳手势"
    
8.  echo " 1. 石头"
    
9.  echo " 2. 剪刀"
    
10. echo " 3. 布 "
    

12. read -p "请选择 1-3 ：" person
    
13. case $person in
    
14. 1)
    
15.   if [ $num -eq 0 ]
    
16.   then 
    
17.     echo "平局"
    
18.     elif [ $num -eq 1 ]
    
19.     then
    
20.       echo "你赢"
    
21.     else 
    
22.       echo "计算机赢"
    
23. fi;;
    
24. 2)
    
25.  if [ $num -eq 0 ]
    
26.  then
    
27.     echo "计算机赢"
    
28.     elif [ $num -eq 1 ] 
    
29.     then
    
30.      echo "平局"
    
31.     else 
    
32.       echo "你赢"
    
33. fi;;
    
34. 3)
    
35.  if [ $num -eq 0 ]
    
36.  then  
    
37.    echo "你赢"
    
38.    elif [ $num -eq 1 ]
    
39.    then 
    
40.      echo "计算机赢"
    
41.    else 
    
42.       echo "平局"
    
43. fi;;
    
44. *)
    
45.   echo "必须输入1-3 的数字"
    
46. esac
    

`

![](https://csdnimg.cn/release/blogv2/dist/pc/img/newCodeMoreWhite.png)


```

**（6）九九乘法表**

```


1.  #!/bin/bash
    

3.  for i in `seq 9`
    
4.  do 
    
5.   for j in `seq $i`
    
6.   do 
    
7.   echo -n "$j*$i=$[i*j] "
    
8.   done
    
9.      echo
    
10. done
    


```

**（7）脚本用源码来安装 memcached 服务器**

```


1.  #!/bin/bash
    
2.  # 一键部署 memcached 
    

4.  # 脚本用源码来安装 memcached 服务器
    
5.  # 注意:如果软件的下载链接过期了,请更新 memcached 的下载链接
    
6.  wget http://www.memcached.org/files/memcached-1.5.1.tar.gz
    
7.  yum -y install gcc
    
8.  tar -xf  memcached‐1.5.1.tar.gz
    
9.  cd memcached‐1.5.1
    
10. ./configure
    
11. make
    
12. make install
    


```

**（8）检测本机当前用户是否为超级管理员**

```


1.  #!/bin/bash
    

3.  # 检测本机当前用户是否为超级管理员,如果是管理员,则使用 yum 安装 vsftpd,如果不
    
4.  # 是,则提示您非管理员(使用字串对比版本) 
    
5.  if [ $USER == "root" ] 
    
6.  then 
    
7.   yum -y install vsftpd
    
8.  else 
    
9.   echo "您不是管理员，没有权限安装软件"
    
10. fi
    


```

**（9）if 运算表达式**

```


1.  #!/bin/bash -xv
    

3.  if [ $1 -eq 2 ] ;then
    
4.   echo "wo ai wenmin"
    
5.  elif [ $1 -eq 3 ] ;then 
    
6.   echo "wo ai wenxing "
    
7.  elif [ $1 -eq 4 ] ;then 
    
8.   echo "wo de xin "
    
9.  elif [ $1 -eq 5 ] ;then
    
10.  echo "wo de ai "
    
11. fi
    


```

**（10）脚本 杀掉 tomcat 进程并重新启动**

```
``

1.  #!/bin/bash
    

3.  #kill tomcat pid
    

5.  pidlist=`ps -ef|grep apache-tomcat-7.0.75|grep -v "grep"|awk '{print $2}'`  #找到tomcat的PID号
    

7.  echo "tomcat Id list :$pidlist"  //显示pid
    

9.  kill -9 $pidlist  #杀掉改进程
    

11. echo "KILL $pidlist:" //提示进程以及被杀掉
    

13. echo "service stop success"
    

15. echo "start tomcat"
    

17. cd /opt/apache-tomcat-7.0.75
    

19. pwd 
    

21. rm -rf work/*
    

23. cd bin
    

25. ./startup.sh #;tail -f ../logs/catalina.out
    

``

![](https://csdnimg.cn/release/blogv2/dist/pc/img/newCodeMoreWhite.png)


```

**（11）打印国际象棋棋盘**

```
`

1.  #!/bin/bash
    
2.  # 打印国际象棋棋盘
    
3.  # 设置两个变量,i 和 j,一个代表行,一个代表列,国际象棋为 8*8 棋盘
    
4.  # i=1 是代表准备打印第一行棋盘,第 1 行棋盘有灰色和蓝色间隔输出,总共为 8 列
    
5.  # i=1,j=1 代表第 1 行的第 1 列;i=2,j=3 代表第 2 行的第 3 列
    
6.  # 棋盘的规律是 i+j 如果是偶数,就打印蓝色色块,如果是奇数就打印灰色色块
    
7.  # 使用 echo ‐ne 打印色块,并且打印完成色块后不自动换行,在同一行继续输出其他色块
    
8.  for i in {1..8}
    
9.  do
    
10.    for j in {1..8}
    
11.    do
    
12.     sum=$[i+j]
    
13.   if [  $[sum%2] -eq 0 ];then
    
14.     echo -ne "\033[46m  \033[0m"
    
15.   else
    
16.    echo -ne "\033[47m  \033[0m"
    
17.   fi
    
18.    done
    
19.    echo
    
20. done
    

`

![](https://csdnimg.cn/release/blogv2/dist/pc/img/newCodeMoreWhite.png)


```

**（12）统计当前 Linux 系统中可以登录计算机的账户有多少个**

```


1.  #!/bin/bash
    

3.  # 统计当前 Linux 系统中可以登录计算机的账户有多少个
    
4.  #方法 1:
    
5.  grep "bash$" /etc/passwd | wc -l
    
6.  #方法 2：
    
7.  awk -f : '/bash$/{x++}end{print x}' /etc/passwd
    


```

**（13）备份 MySQL 表数据**

```


1.  #!/bin/sh
    

3.  source /etc/profile
    
4.  dbName=mysql
    
5.  tableName=db
    
6.  echo [`date +'%Y-%m-%d %H:%M:%S'`]' start loading data...'
    
7.  mysql -uroot -proot -P3306 ${dbName} -e "LOAD DATA LOCAL INFILE '# /home/wenmin/wenxing.txt' INTO TABLE ${tableName} FIELDS TERMINATED BY ';'"
    
8.  echo [`date +'%Y-%m-%d %H:%M:%S'`]' end loading data...'
    
9.  exit
    
10. EOF
    


```

**（14）使用死循环实时显示 eth0 网卡发送的数据包流量**

```


1.  #!/bin/bash
    

3.  # 使用死循环实时显示 eth0 网卡发送的数据包流量 
    

5.  while :
    
6.  do 
    
7.   echo '本地网卡 ens33 流量信息如下：'
    
8.   ifconfig ens33 | grep "RX pack" | awk '{print $5}'
    
9.       ifconfig ens33 | grep "TX pack" | awk '{print $5}'
    
10.  sleep 1
    
11. done
    


```

**（15）编写脚本测试 192.168.4.0/24 整个网段中哪些主机处于开机状态，哪些主机处于关机**

```


1.  #!/bin/bash
    

3.  # 编写脚本测试 192.168.4.0/24 整个网段中哪些主机处于开机状态,哪些主机处于关机
    
4.  # 状态(for 版本)
    
5.  for i in {1..254}
    
6.  do 
    
7.   # 每隔0.3秒ping一次，一共ping2次，并以1毫秒为单位设置ping的超时时间
    
8.   ping -c 2 -i 0.3 -W 1 192.168.1.$i &>/dev/null
    
9.       if [ $? -eq 0 ];then
    
10.  echo "192.168.1.$i is up"
    
11.  else 
    
12.  echo "192.168.1.$i is down"
    
13.  fi
    
14. done
    


```

**（16）编写脚本：提示用户输入用户名和密码,脚本自动创建相应的账户及配置密码。如果用户**

```
`

1.  #!/bin/bash
    
2.  # 编写脚本:提示用户输入用户名和密码,脚本自动创建相应的账户及配置密码。如果用户
    
3.  # 不输入账户名,则提示必须输入账户名并退出脚本;如果用户不输入密码,则统一使用默
    
4.  # 认的 123456 作为默认密码。
    

6.  read -p "请输入用户名：" user
    
7.  #使用‐z 可以判断一个变量是否为空,如果为空,提示用户必须输入账户名,并退出脚本,退出码为 2
    
8.  #没有输入用户名脚本退出后,使用$?查看的返回码为 2
    
9.  if [ -z $user ]; then
    
10.  echo " 您不需要输入账户名" 
    
11.  exit 2
    
12. fi 
    
13. #使用 stty ‐echo 关闭 shell 的回显功能
    
14. #使用 stty  echo 打开 shell 的回显功能
    
15. stty -echo 
    
16. read -p "请输入密码：" pass
    
17. stty echo 
    
18. pass=${pass:-123456}
    
19. useradd "$user"
    
20. echo "$pass" | passwd --stdin "$user"
    

`

![](https://csdnimg.cn/release/blogv2/dist/pc/img/newCodeMoreWhite.png)


```

**（17）使用脚本对输入的三个整数进行排序**

```


1.  #!/bin/bash
    

3.  # 依次提示用户输入 3 个整数,脚本根据数字大小依次排序输出 3 个数字
    
4.  read -p " 请输入一个整数：" num1
    
5.  read -p " 请输入一个整数：" num2
    
6.  read -p " 请输入一个整数:  " num3
    

8.  # 不管谁大谁小,最后都打印 echo "$num1,$num2,$num3"
    
9.  # num1 中永远存最小的值,num2 中永远存中间值,num3 永远存最大值
    
10. # 如果输入的不是这样的顺序,则改变数的存储顺序,如:可以将 num1 和 num2 的值对调
    
11. tmp=0
    
12. # 如果 num1 大于 num2,就把 num1 和和 num2 的值对调,确保 num1 变量中存的是最小值
    
13. if [ $num1 -gt $num2 ];then
    
14.  tmp=$num1
    
15.  num1=$num2
    
16.  num2=tmp
    
17. fi
    
18. # 如果 num1 大于 num3,就把 num1 和 num3 对调,确保 num1 变量中存的是最小值
    
19. if [ $num1 -gt $num3 ];then
    
20.  tmp=$num1
    
21.  num1=$num3
    
22.  num3=$tmp
    
23. fi
    
24. # 如果 num2 大于 num3,就把 num2 和 num3 对调,确保 num2 变量中存的是最小值
    
25. if [ $num2 -gt $num3 ];then
    
26.  tmp=$num2
    
27.  num2=$num3
    
28.  num3=$tmp
    
29. fi
    
30. echo "排序后数据（从小到大）为：$num1,$num2,$num3"
    


```

**（18）根据计算机当前时间，返回问候语，可以将该脚本设置为开机启动**

```
`

1.  #!/bin/bash
    
2.  # 根据计算机当前时间,返回问候语,可以将该脚本设置为开机启动 
    

4.  # 00‐12 点为早晨,12‐18 点为下午,18‐24 点为晚上
    
5.  # 使用 date 命令获取时间后,if 判断时间的区间,确定问候语内容
    
6.  tm=$(date +%H)
    
7.  if [ $tm -le 12 ];then
    
8.   msg="Good Morning $USER"
    
9.  elif [ $tm -gt 12 -a $tm -le 18 ];then
    
10.    msg="Good Afternoon $USER"
    
11. else
    
12.    msg="Good Night $USER"
    
13. fi
    
14. echo "当前时间是:$(date +"%Y‐%m‐%d %H:%M:%S")"
    
15. echo -e "\033[34m$msg\033[0m"
    

`

![](https://csdnimg.cn/release/blogv2/dist/pc/img/newCodeMoreWhite.png)


```

**（19）将 I lov cls 写入到 txt 文件中**

```


1.  #!/bin/bash
    

3.  cd /home/wenmin/
    
4.  touch wenxing.txt
    
5.  echo "I lov cls" >>wenxing.txt
    


```

**（20）脚本编写 for 循环判断**

```
`

1.  #!/bin/bash
    

3.  s=0;
    
4.  for((i=1;i<100;i++))
    
5.  do 
    
6.   s=$[$s+$i]
    
7.  done 
    

9.  echo $s
    

11. r=0;
    
12. a=0;
    
13. b=0;
    
14. for((x=1;x<9;x++))
    
15. do 
    
16.  a=$[$a+$x] 
    
17. echo $x
    
18. done
    
19. for((y=1;y<9;y++))
    
20. do 
    
21.  b=$[$b+$y]
    
22. echo $y
    

24. done
    

26. echo $r=$[$a+$b]
    

`

![](https://csdnimg.cn/release/blogv2/dist/pc/img/newCodeMoreWhite.png)


```

**（21）脚本编写 for 循环判断**

```


1.  #!/bin/bash
    

3.  for i in "$*"
    
4.  do 
    
5.   echo "wenmin xihuan $i"
    
6.  done
    

8.  for j in "$@"
    
9.  do 
    
10.  echo "wenmin xihuan $j"
    
11. done
    


```

**（22）脚本 每周 5 使用 tar 命令备份/var/log 下的所有日志文件**

```


1.  #!/bin/bash
    
2.  # 每周 5 使用 tar 命令备份/var/log 下的所有日志文件
    
3.  # vim  /root/logbak.sh
    
4.  # 编写备份脚本,备份后的文件名包含日期标签,防止后面的备份将前面的备份数据覆盖
    
5.  # 注意 date 命令需要使用反引号括起来,反引号在键盘<tab>键上面
    

7.  tar -czf log-`date +%Y%m%d`.tar.gz /var/log 
    

9.  # crontab -e #编写计划任务，执行备份脚本
    
10. 00 03 * * 5 /home/wenmin/datas/logbak.sh
    


```

**（23）脚本编写 求和 函数运算 function xx()**

```
`

1.  #!/bin/bash
    

3.  function sum()
    
4.  {
    
5.   s=0;
    
6.   s=$[$1+$2]
    
7.   echo $s
    
8.  }
    
9.  read -p "input your parameter " p1
    
10. read -p "input your parameter " p2
    

12. sum $p1 $p2
    

14. function multi()
    
15. {
    
16.  r=0;
    
17.  r=$[$1/$2]
    
18.  echo $r
    
19. }
    
20. read -p "input your parameter " x1
    
21. read -p "input your parameter " x2
    

23. multi $x1 $x2
    

25. v1=1
    
26. v2=2
    
27. let v3=$v1+$v2
    
28. echo $v3
    

`

![](https://csdnimg.cn/release/blogv2/dist/pc/img/newCodeMoreWhite.png)


```

**（24）脚本编写 case — esac 分支结构表达式**

```
`

1.  #!/bin/bash 
    

3.  case $1 in 
    
4.  1) 
    
5.   echo "wenmin "
    
6.  ;;
    
7.  2)
    
8.   echo "wenxing "
    
9.  ;; 
    
10. 3)  
    
11.  echo "wemchang "
    
12. ;;
    
13. 4) 
    
14.  echo "yijun"
    
15. ;;
    
16. 5)
    
17.  echo "sinian"
    
18. ;;
    
19. 6)  
    
20.  echo "sikeng"
    
21. ;;
    
22. 7) 
    
23.  echo "yanna"
    
24. ;;
    
25. *)
    
26.  echo "danlian"
    
27. ;; 
    
28. esac
    

`

![](https://csdnimg.cn/release/blogv2/dist/pc/img/newCodeMoreWhite.png)


```

**（25）# 定义要监控的页面地址，对 tomcat 状态进行重启或维护**

```
`

1.  #!/bin/sh  
    
2.  # function:自动监控tomcat进程，挂了就执行重启操作  
    
3.  # author:huanghong  
    
4.  # DEFINE  
    

6.  # 获取tomcat PPID  
    
7.  TomcatID=$(ps -ef |grep tomcat |grep -w 'apache-tomcat-7.0.75'|grep -v 'grep'|awk '{print $2}')  
    

9.  # tomcat_startup  
    
10. StartTomcat=/opt/apache-tomcat-7.0.75/bin/startup.sh  
    

13. #TomcatCache=/usr/apache-tomcat-5.5.23/work  
    

15. # 定义要监控的页面地址  
    
16. WebUrl=http://192.168.254.118:8080/
    

18. # 日志输出  
    
19. GetPageInfo=/dev/null  
    
20. TomcatMonitorLog=/tmp/TomcatMonitor.log  
    

22. Monitor()  
    
23.   {  
    
24.    echo "[info]开始监控tomcat...[$(date +'%F %H:%M:%S')]"  
    
25.    if [ $TomcatID ]
    
26.  then  
    
27.       echo "[info]tomcat进程ID为:$TomcatID."  
    
28.       # 获取返回状态码  
    
29.       TomcatServiceCode=$(curl -s -o $GetPageInfo -m 10 --connect-timeout 10 $WebUrl -w %{http_code})  
    
30.       if [ $TomcatServiceCode -eq 200 ];then  
    
31.           echo "[info]返回码为$TomcatServiceCode,tomcat启动成功,页面正常."  
    
32.       else  
    
33.           echo "[error]访问出错，状态码为$TomcatServiceCode,错误日志已输出到$GetPageInfo"  
    
34.           echo "[error]开始重启tomcat"  
    
35.           kill -9 $TomcatID  # 杀掉原tomcat进程  
    
36.           sleep 3  
    
37.           #rm -rf $TomcatCache # 清理tomcat缓存  
    
38.           $StartTomcat  
    
39.       fi  
    
40.       else  
    
41.       echo "[error]进程不存在!tomcat自动重启..."  
    
42.       echo "[info]$StartTomcat,请稍候......"  
    
43.       #rm -rf $TomcatCache  
    
44.       $StartTomcat  
    
45.     fi  
    
46.     echo "------------------------------"  
    
47.    }  
    
48.    Monitor>>$TomcatMonitorLog
    

`

![](https://csdnimg.cn/release/blogv2/dist/pc/img/newCodeMoreWhite.png)


```

**（26）通过位置变量创建 Linux 系统账户及密码**

```


1.  #!/bin/bash
    

3.  # 通过位置变量创建Linux 系统账户及密码
    

5.  # $1 是执行脚本的第一个参数，$2  是执行脚本的第二个参数
    

7.  useradd "$1"
    
8.  echo "$2" | passwd --stdin "$1"
    


```

**（27）对变量的传入与获取个数及打印**

```


1.  #!/bin/bash
    
2.  echo "$0 $1 $2 $3"  // 传入三个参数
    
3.  echo $#    //获取传入参数的数量
    
4.  echo $@    //打印获取传入参数
    
5.  echo $*    //打印获取传入参数
    


```

**（28）实时监控本机内存和硬盘剩余空间，剩余内存小于500M、根分区剩余空间小于1000M时，发送报警邮件给root管理员**

```
`

1.  #!/bin/bash
    

3.  # 实时监控本机内存和硬盘剩余空间,剩余内存小于500M、根分区剩余空间小于1000M时,发送报警邮件给root管理员
    

5.  # 提取根分区剩余空间
    
6.  disk_size=$(df / | awk '/\//{print $4}')
    

8.  # 提取内存剩余空空间
    
9.  mem_size=$(free | awk '/Mem/{print $4}')
    
10. while :
    
11. do 
    
12. # 注意内存和磁盘提取的空间大小都是以 Kb 为单位
    
13. if  [  $disk_size -le 512000 -a $mem_size -le 1024000  ]
    
14. then
    
15.     mail  ‐s  "Warning"  root  <<EOF
    
16.  Insufficient resources,资源不足
    
17. EOF
    
18. fi
    
19. done
    

`

![](https://csdnimg.cn/release/blogv2/dist/pc/img/newCodeMoreWhite.png)


```

**（29）检查指定目录下是否存在 对应 文件**

```


1.  #!/bin/bash
    

3.  if [ -f /home/wenmin/datas ]
    
4.  then 
    
5.  echo "File exists"
    
6.  fi
    


```

**（30）脚本定义while循环语句**

```
`

1.  #!/bin/bash
    

3.  if [ -f /home/wenmin/datas ]
    
4.  then 
    
5.  echo "File exists"
    
6.  fi
    

8.  [root@rich datas]# cat while.sh 
    
9.  #!/bin/bash
    

11. s=0
    
12. i=1
    
13. while [ $i -le 100 ]
    
14. do
    
15.         s=$[$s + $i]
    
16.         i=$[$i + 1]
    
17. done
    

19. echo $s
    
20. echo $i
    

`

![](https://csdnimg.cn/release/blogv2/dist/pc/img/newCodeMoreWhite.png)


```

**（31）一键部署 LNMP（RPM 包版本）**

```


1.  #!/bin/bash 
    

3.  # 一键部署 LNMP(RPM 包版本)
    
4.  # 使用 yum 安装部署 LNMP,需要提前配置好 yum 源,否则该脚本会失败
    
5.  # 本脚本使用于 centos7.2 或 RHEL7.2
    
6.  yum -y install httpd
    
7.  yum -y install mariadb mariadb-devel mariadb-server
    
8.  yum -y install php php-mysql
    

10. systemctl start httpd mariadb
    
11. systemctl enable httpd mariadb
    


```

**（32）读取控制台传入参数**

```


1.  #!/bin/bash
    
2.  read -t 7 -p "input your name " NAME
    
3.  echo $NAME
    

5.  read -t 11 -p "input you age " AGE
    
6.  echo $AGE
    

8.  read -t 15 -p "input your friend " FRIEND
    
9.  echo $FRIEND
    

11. read -t 16 -p "input your love " LOVE
    
12. echo $LOVE
    


```

**（33）脚本实现 复制**

```


1.  #!/bin/bash
    

3.  cp $1 $2
    


```

**（34）脚本实现文件存在与否的判断**

```


1.  #!/bin/bash
    

3.  if [ -f file.txt ];then
    
4.   echo "文件存在"
    
5.  else 
    
6.   echo "文件不存在"
    
7.  fi
    


```