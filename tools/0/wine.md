# 如何在 Ubuntu 中安装 Wine

作者： [Abhishek Prakash](https://itsfoss.com/install-wine-ubuntu/) 译者： [LCTT](https://linux.cn/lctt/) [郑](https://linux.cn/lctt/robsean)

| 2023-07-24 09:20   评论: [*5*](https://linux.cn/portal.php?mod=comment&id=16028&idtype=aid "查看全部评论") 收藏: *1*    

> 想在 Ubuntu 上运行仅限 Windows 的软件？Wine 就是你的朋友。学习在 Ubuntu Linux 中安装 Wine。

只要稍加努力，你可以使用 Wine 来 [在 Linux 上运行 Windows 应用程序](https://itsfoss.com/use-windows-applications-linux/) 。当你必须在 Linux 上运行一个仅有 Windows 版本的应用程序时，Wine 是一个你可以尝试的工具。

请注意：**你不能使用 Wine 来运行每一个 Windows 游戏或软件**。请浏览 [已支持的应用程序的数据库](https://appdb.winehq.org/)。评估为白金级或黄金级的软件更有可能与 Wine 一起平稳的运行。

如果你已经找到一个仅有 Windows 版本的软件，并且 [Wine](https://www.winehq.org/) 也很好地支持它，现在希望使用它，这篇教程将帮助你在 Ubuntu 上安装 Wine 。

> 💡 如果你在此之前已经安装了 Wine ，你应该完全地移除它，以避免一些冲突。此外，你应该参考它的 [下载页面](https://wiki.winehq.org/Download) 来获取特定 Linux 发行版的附加说明。

### 在 Ubuntu 上安装 Wine

这里有很多方法来在你的系统上安装 Wine 。几乎所有的 Linux 发行版都在它们的软件包存储库中提供 Wine 。

大多数的时候，Wine 的最新稳定版本都可以通过软件包存储库获得。

- 从 Ubuntu 的存储库中安装 Wine（简单，但是可能不是最新的版本）
- 从 Wine 的存储库中安装 Wine（稍微复杂一些，但是提供最新的版本）

请耐心等待，按照步骤逐步安装和 Wine 。这里有一些相关的步骤。

> 🚧 请记住，Wine 会安装很多很多的软件包。你将看到一份庞大的软件包列表，安装大小差不多 1.3 GB 。

<img width="1109" height="580" src="../../../_resources/092011dkikj822okk6mj22_f87d296513f44526a34829fef10.png"/>

*Wine download and installed size*

#### 方法 1\. 从 Ubuntu 安装 Wine（简单）

Wine 可以在 Ubuntu 的官方存储库中获得，你可以在那里简单地安装它。不过，这种方法获取的版本可能不能最新的。

即使你正在使用一个 64 位的 Ubuntu 安装，你也想要在你的发行版上添加 32 位架构的支持，这将有利于你安装特殊的软件。

输入下面的命令:

```


1.  `sudo dpkg --add-architecture i386`


```

接下来，安装 Wine 使用:

```


1.  `sudo apt update`
2.  `sudo apt install wine`


```

#### 方法 2: 从 Wine 的存储库安装最新的版本

Wine 是一个日新月异的程序。因此，始终建议安装 Wine 的最新稳定版本，以获取更多软件的支持。

首先，移除已存在的 Wine 安装。

步骤 1: 确保添加 32 位架构支持:

```


1.  `sudo dpkg --add-architecture i386`


```

步骤 2: 下载和添加存储库密钥:

```


1.  `sudo 
    
     mkdir 
    
     -pm755 /etc/apt/keyrings`
2.  `sudo 
    
     wget 
    
     -O /etc/apt/keyrings/winehq-archive.key https://dl.winehq.org/wine-builds/winehq.key`


```

步骤 3: 现在，下载 WineHQ 源文件文件。

> 🚧 这个步骤取决于你正在使用的 Ubuntu 或 Mint 的版本。请 [检查你的 Ubuntu 版本](https://itsfoss.com/how-to-know-ubuntu-unity-version/) 或 [Mint 版本](https://itsfoss.com/check-linux-mint-version/) 。在你掌握这些信息后，分别使用针对你的相对应的版本的命令。

针对 **Ubuntu 23.04 Lunar Lobster** ，使用下面的命令:

```


1.  `sudo 
    
     wget 
    
     -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/lunar/winehq-lunar.sources`


```

如果你持有 **Ubuntu 22.04 或 Linux Mint 21.X 系列**，使用下面的命令:

```


1.  `sudo 
    
     wget 
    
     -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/jammy/winehq-jammy.sources`


```

如果你正在运行 **Ubuntu 20.04 或 Linux Mint 20.X 系列**，使用:

```


1.  `sudo 
    
     wget 
    
     -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/focal/winehq-focal.sources`


```

**Ubuntu 18.04 或 Linux Mint 19.X 系列**用户，可以使用下面的命令来添加源文件文件:

```


1.  `sudo 
    
     wget 
    
     -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/bionic/winehq-bionic.sources`


```

在完成后，更新软件包信息和安装 Wine 的稳定版本软件包。

```


1.  `sudo apt install --install-recommends winehq-stable`


```

如果你现有开发版本或暂存版本，相应地使用 `winehq-devel` 或 `winehq-staging` 。

### 初始化 Wine 配置

在 Wine 安装后，运行下面的命令:

```


1.  `winecfg`


```

这将创建用于安装 Windows 应用程序的 **虚拟的 C: 驱动器** 。

<img width="1109" height="546" src="../../../_resources/092011vmcm0100ates3oc9_070c8fffcd054a1ca0cf07692e3.png"/>

*C: Drive created by winecfg in Home directory*

在按照这些步骤时，有时，你可能在文件管理器的邮件菜单中找不到 “使用 Wine Windows 程序加载器打开Open With Wine Windows Program Loader” 的选项。

在这种情况下，通过 [创建软链接](https://learnubuntu.com/ln-command/) 到适当的目录来修复它:

```


1.  `sudo 
    
     ln 
    
     -s /usr/share/doc/wine/examples/wine.desktop /usr/share/applications/`


```

然后，重新启动你的系统来获取更改。

### 使用 Wine 来运行 Windows 应用程序

在你安装 Wine 并通过运行 `winecfg` 将其配置后, 现在是安装 Windows 应用程序的时间了。

在这里，7Zip.exe 文件是用于演示目的的。我知道我应该使用一个更好的示例，因为 7Zip 在 Linux 上是可获得的。不过，对于其它的应用程序来说，接下来的流程是相同的。

首先，从它的 [官方下载页面](https://www.7-zip.org/download.html) 下载 7Zip 文件。

现在，在该文件上右键单击，并选择“使用 Wine Windows 程序加载器打开”选项：

<img width="1109" height="664" src="../../../_resources/092012z52epaiyftm7iz5t_eeb9d8f629574a40bf2336fb1dc.png"/>

*Open 7zip exe file using Wine WIndows Program Loader in Nemo file manager*

这将提示我们安装该文件。单击 “安装**Install**” 并让其完成。在完成后，你可以像其它的一些原生应用程序一样打开 7zip 。

![Open 7Zip from Ubuntu Activities Overview](../../../_resources/092043qp9m6app42dfzl2a_9446a257535a4cf386941d7b587.jpg)

*Open 7Zip from Ubuntu Activities Overview*

你可以使用 `wine uninstaller` 命令来卸载任意已安装的应用程序。

这里是一篇关于在 Linux 上 [使用 Wine 来运行 Windows 软件](https://itsfoss.com/use-windows-applications-linux/) 的专业教程。

### 从 Ubuntu 中移除 Wine

如果你没有发现 Wine 有趣，或者，如果 Wine 不能正确地运行你想要的应用程序，你可能需要卸载 Wine 。为此，按照下面的步骤。

#### 通过 Ubuntu 存储库移除已安装的 Wine

为通过存储库移除已安装的 Wine ，首先运行:

```


1.  `sudo apt remove --purge wine`


```

更新你的软件包信息:

```


1.  `sudo apt update`


```

现在，使用 `autoclean` 命令来清理本地存储库中已检索取回的几乎不再有用的软件包文件。

```


1.  `sudo 
    
     apt-get autoclean`
2.  `sudo 
    
     apt-get clean`


```

移除那些已安装但不再需要的软件包:

```


1.  `sudo apt autoremove`


```

现在，重新启动系统。

#### 如果 Wine 存储库移除 Wine 安装

移除已安装的 `wine-stable` 软件包。

```


1.  `sudo apt remove --purge wine-stable`


```

更新你的软件包信息:

```


1.  `sudo apt update`


```

现在，使用 `autoclean` 和 `clean` 命令来清理本地存储库中已检索取回的几乎不再有用的软件包文件。

```


1.  `sudo 
    
     apt-get autoclean`
2.  `sudo 
    
     apt-get clean`


```

移除先前添加的源文件文件。使用你的相对应的发行版文件夹。在这里，使用的是 Ubuntu 22.04 。

```


1.  `sudo 
    
     rm 
    
     /etc/apt/sources.list.d/winehq-jammy.sources`


```

在这移除后，更新你的系统信息:

```


1.  `sudo apt update`


```

可选，如果你希望的话，移除你先前添加的密钥文件。

```


1.  `sudo 
    
     rm 
    
     /etc/apt/keyrings/winehq-archive.key`


```

现在，手动移除剩余的一些的文件。

### 还有一些关于使用 Wine 的问题？

你也可以翻阅我们关于使用 Wine 的教程。它应该能回答你可能想要解决的问题。

没有比 Wine 工程的网站更好的地方了。它们有一个专业的常见问题解答页面:

> **[Wine 的 FAQ](https://wiki.winehq.org/FAQ)**

如果你还有问题，你可以浏览 [它们的维基](https://wiki.winehq.org/Main_Page) 来查看详细的 [文档](https://www.winehq.org:443/documentation) 或者在 [它们的论坛](https://forum.winehq.org/) 中询问你的疑问。

或者，如果你不介意花一些钱，你可以选择 CrossOver 。它基本上就是 Wine ，但是有高级的支持。你也可以联系他们的团队来解决你的问题。

我的意见是，在你不能找到一款你必需使用的替换软件时，你应该求助于 Wine 。事实上，在这种情况下，不能保证与 Wine 一起工作。

但是，Wine 为从 Windows 迁移到 Linux 提供了一些希望。
