本文链接: https://blog.csdn.net/xietansheng/article/details/115559070

[Python3 学习笔记（目录）](https://blog.csdn.net/xietansheng/article/details/109266600)

Python Shell 操作相关函数和类, Python Docs:

- [os.system(command)](https://docs.python.org/zh-cn/3/library/os.html#os.system)
- [os.popen(cmd, mode=‘r’, buffering=-1)](https://docs.python.org/zh-cn/3/library/os.html#os.popen)
- [subprocess — Subprocess management](https://docs.python.org/zh-cn/3/library/subprocess.html)

# <a id="t0"></a><a id="1_ossystem_16"></a>1\. os.system()

函数原型:

```
`# 在子 shell 中执行命令（字符串）。该函数是调用标准 C 函数 system() 来实现的，
# 因此限制条件与该函数相同。对 sys.stdin 等的更改不会反映在执行命令的环境中。
# command 产生的任何输出将被发送到解释器标准输出流。
# 返回一个 int 类型的 code，一般返回 0 表示执行成功。
os.system(command)` 
```

代码示例:

```
`>>> import os
>>> 
>>> result = os.system("python3 -V")
Python 3.7.3
>>> result
0
>>> os.system("python3 -V")
Python 3.7.3
0` 
```

# <a id="t1"></a><a id="2_ospopen_42"></a>2\. os.popen()

函数原型:

```
`# 打开一个管道执行 cmd 命令, 返回值是连接到管道的 文件对象。
# 只能和管道单向通讯, 返回值只能是 写入 或 读取 对象。
# mode 为 'r', 表示返回的的是 读取对象, 可以对管道 read()、 readlines()
# mode 为 'w', 表示返回的的是 写入对象, 可以对管道 write()、writelines()
# 返回的文件对象只能读写字符串, 不能是字节类型。
os.popen(cmd, mode='r', buffering=-1)` 
```

## <a id="t2"></a><a id="21___56"></a>2.1 读取对象 代码示例:

文件: demo.py

```
`print("hello world")` 
```

执行命令:

```
`>>> import os
>>> 
>>> fr = os.popen("python3 demo.py")
>>> fr.read()
'hello world\n'
>>> fr.close()` 
```

## <a id="t3"></a><a id="22___76"></a>2.2 写入对象 代码示例:

文件: demo.py

```
`print("hello")
s = input()
print(s)
print("world")` 
```

文件: app.py

```
`import os

fw = os.popen("python3 demo.py", mode="w")
fw.write("你好")
fw.close()` 
```

执行命令:

```
`$ python3 app.py
hello
你好
world` 
```

# <a id="t4"></a><a id="3__subprocess_106"></a>3\. 子进程管理: subprocess

`subprocess`模块允许你创建新的子进程，可以连接子进程输入、输出、错误 管道，并获取子进程的返回码。

Python 推荐使用`subprocess.run()`函数掉用子进程，更高级的用法也可以使用底层的`class subprocess.Popen`接口。

## <a id="t5"></a><a id="31_subprocessrun_112"></a>3.1 subprocess.run()

Python Docs: [subprocess.run()](https://docs.python.org/zh-cn/3/library/subprocess.html#subprocess.run)

函数原型:

```
`subprocess.run(args, 
               *, 
               stdin=None, input=None, stdout=None, stderr=None,
               capture_output=False, shell=False, cwd=None, timeout=None,
               check=False, encoding=None, errors=None, text=None, env=None, 
               universal_newlines=None, **other_popen_kwargs)
# 部分参数说明:
#
# args: 
#    需要执行的命令, str 或 list/tuple 类型, 如果携带参数需要使用 list/tuple 类型, 
#    将命令以及每个参数组成 list/tuple, 例如: ["python3", "-m", "pip", "list"]
#
# stdin, stdout, stderr:
#    子进程的标准 输入、输出、错误输出
#
# cwd:
#    执行命令时的工作目录
#
# timeout:
#    超时时间, 超过该时间子进程还没有结束, 则杀掉子进程并抛出异常
#
# env:
#    为子进程设置环境变量, 字典类型, 默认继承自父进程
#
# 等待命令执行完成后, 返回一个 subprocess.CompletedProcess 实例, 
# 可以通过 CompletedProcess.returncode 属性判断子进程的返回 Code。` 
```

代码示例:

```
`>>> import subprocess
>>> 
>>> r = subprocess.run("ls")
aa_dir          aa.jpg          aa.txt
>>> r.returncode
0
>>> subprocess.run(["ls", "-l"])
total 720
drwxr-xr-x  3 xiets  staff     96 Oct 11  2019 aa_dir
-rw-r--r--@ 1 xiets  staff  82182 Sep 18 09:56 aa.jpg
-rw-r--r--  1 xiets  staff  64441 Sep 28 11:29 aa.txt
CompletedProcess(args=['ls', '-l'], returncode=0)
>>> 
>>> subprocess.run(["python3", "-m", "pip", "list"])
Package    Version
---------- ---------
pip        20.2.2
setuptools 41.2.0
CompletedProcess(args=['python3', '-m', 'pip', 'list'], returncode=0)
>>>
>>> subprocess.run("pwd", cwd="/Users")
/Users
CompletedProcess(args='pwd', returncode=0)` 
```

## <a id="t6"></a><a id="32_subprocessPopen_176"></a>3.2 subprocess.Popen

Python Docs:

- 构造方法: [class subprocess.Popen](https://docs.python.org/zh-cn/3/library/subprocess.html#subprocess.Popen)
- 实例方法: [popen-objects](https://docs.python.org/zh-cn/3/library/subprocess.html#popen-objects)

`subprocess.Popen`类构造方法:

```
`class subprocess.Popen(args, bufsize=-1, executable=None, 
                       stdin=None, stdout=None, stderr=None, 
                       preexec_fn=None, close_fds=True, shell=False, 
                       cwd=None, env=None, universal_newlines=None, 
                       startupinfo=None, creationflags=0, restore_signals=True,
                       start_new_session=False, pass_fds=(), *, 
                       encoding=None, errors=None, text=None)
# 部分参数说明:
#
# args: 
#    需要执行的命令, str 或 list/tuple 类型, 如果携带参数需要使用 list/tuple 类型, 
#    将命令以及每个参数组成 list/tuple, 例如: ["python3", "-m", "pip", "list"]
#
# stdin, stdout, stderr:
#    子进程的标准 输入、输出、错误输出
#
# cwd:
#    执行命令时的工作目录
#
# timeout:
#    超时时间, 超过该时间子进程还没有结束, 则杀掉子进程并抛出异常
#
# env:
#    为子进程设置环境变量, 字典类型, 默认继承自父进程` 
```

`subprocess.Popen`实例的方法:

```
`# 检查子进程是否已被终止, 如果终止则返回 returncode, 否则返回 None
Popen.poll()

# 等待子进程被终止, 并返回 returncode, 可以指定等待时间, 超过则抛出异常
Popen.wait(timeout=None)

# 杀死子进程, 发送 SIGKILL 信号到子进程
Popen.kill()

# 发送 signal 信号到子进程
Popen.send_signal(signal)

# 与进程交互: 将数据发送到 stdin。从 stdout 和 stderr 读取数据, 直到到达文件末尾。
# 等待进程终止并设置 returncode 属性。
# 可选输入参数应该是要发送到子进程的数据, 如果没有数据要发送到子进程, 则为 None。
# 如果以文本模式打开流，则输入必须为字符串。否则，它必须是字节。
# 返回一个 (stdout_data, stderr_data) 元组。如果文件以文本模式打开则为字符串, 否则为字节。
Popen.communicate(input=None, timeout=None)

# 停止子进程。在 POSIX 操作系统上, 该方法将 SIGTERM 发送给子进程。
# 在Windows上, 将调用 Win32 API 函数 TerminateProcess（）来停止子进程。
Popen.terminate()

# 传递给 Popen 的命令参数序列或字符串
Popen.args

# 子进程的标准输入
Popen.stdin

# 子进程的标准输出
Popen.stdout

# 子进程的错误输出
Popen.stderr

# 子进程的进程ID
Popen.pid

# 子进程的退出码, 由 poll() 和 wait() 设置（以及直接由 communicate() 设置）。
# None 表示子进程还没有结束。
Popen.returncode` 
```

代码示例:

```
import subprocess

p = subprocess.Popen(["java", "-version"])
p.wait()
print(p.returncode)
```