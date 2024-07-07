系统安装过程中
# 在安装系统的过程中安装缺失的固件
1. 制作一个fat32u盘，U盘里有其它文件也没有关系，只要在U盘中创建一个名为firmware的文件夹，并把缺少的固件文件放入此文件夹中即可。
![a56f5c71f74f80be52de19ab4c2f9ad7.png](../../_resources/a56f5c71f74f80be52de19ab4c2f9ad7.png)
2. 插入电脑后照常安装系统
---
---
系统安装完后
# 添加当前用户到sudo

    切换到root
       su root
    使用以下命令编辑sudoers文件
        nano /etc/sudoers
    在文件末尾添加
        {user_name} ALL=(ALL:ALL) ALL
    保存并退出
    注销后重新登陆(取消勾选保存会话用于将来登陆)

# tty

## 字号

    sudo dpkg-reconfigure console-setup
    OK
    OK
    select Terminus 
    set font size

## fbterm

    sudo adduser username video
    fbterm
    分别打开当前用户的~/.fbtermrc，设置font-size和font-names(改为DejaVu Sans Mono)

# terminal

    编辑.首选项
        一般
            滚动
                滚动条在：已禁用
            光标(可不做)
                光标形状：下划线
            标题
                初始标题：Terminal
                动态设置标题：不显示
        外观
            字体　liberation mono regular 14
            背景    无
            打开新窗口
                关闭在新窗口显示菜单栏

# 安装缺失字体

    进入/usr/share/fonts
    复制缺失的字体到当前目录
    fc-cache -fv

# 设置“设置管理器”

## 窗口管理器   
	标题字体：
        Liberation Mono Regular
	键盘：
		移动窗口至上一工作区    C super Home
		移动窗口至下一工作区    C super End
		移动窗口至工作区 1    C super 1    
		移动窗口至工作区 2    C super 2
		移动窗口至工作区 3    C super 3
		移动窗口至工作区 4    C super 4
		移动窗口至工作区 5    C super 5
		移动窗口至工作区 6    C super 6
		移动窗口至工作区 7    C super 7
		移动窗口至工作区 8    C super 8
		移动窗口至工作区 9    C super 9
		窗口平铺在顶部       super up
		窗口平铺在底部       super down
		窗口平铺在左边       super left
		窗口平铺在右边       super right
		窗口平铺在左上       super Home
		窗口平铺在右上       super Pgup
		窗口平铺在左下       super End
		窗口平铺在右下       super Pgdn
		显示桌面快捷键	super D
		上方工作区         C super up
		下方工作区         C super down
		左边工作区         C super left
		右边工作区         C super right
		工作区1              super F1
		工作区2              super F2
		工作区3              super F3
		工作区4              super F4
		工作区5              super F5
		工作区6              super F6
		工作区7              super F7
		工作区8              super F8
		工作区9              super F9
		工作区10         super F10
		工作区11         super F11
		工作区12         super F12
		添加工作区         Super Insert
		添加相邻工作区       S Super Insert
		删除最后一个工作区     Super Delete
		删除当前工作区           Shift Super Delete
     高级
         隐藏窗口内容
             关闭"移动时"、"调整大小时"

## 窗口管理器微调

    焦点
        焦点:激活焦点防窃取
        窗口提升自己时：选择‘切换至窗口的工作区’
    辅助功能：
        用来获取和移动窗口的按键： super
        最大化窗口时隐藏标题： 打勾
        关闭：在桌面上使用鼠标滚轮切换工作区
    合成器：
        关闭：
            在弹出窗口下显示阴影
            在dock窗口下显示阴影
            在常规窗口下显示阴影

## 面板

    显示
        自动隐藏面板：总是
            取消锁定面板，移动面板至下方，启用锁定面板
    外观
        开启‘暗黑模式’
    项目    
        添加并放置“CPU频率显示器”，设置如下
             字体:~
             打开
                 显示单行文字
            关闭
                显示CPU图标
        配置窗口按钮
            启用：
                使用扁平按钮
            关闭：
                显示按钮标签
                显示控制器
        添加并放置"whisker 菜单"
        移除：通知

## 通知

    常规-外观
        不透明度：100%
    动画
        关闭“淡出”

## 外观

    样式： Adwaita-dark
    图表： Adwaita
    字体
        默认字体，默认等宽字体： Liberation Mono Regular 10
        渲染： 关闭自动抗锯齿

## 设置键盘

    应用程序快捷键 
        添加 xfce4-popup-whiskermenu 命令及其快捷键 super M

## 电源管理器

    显示
        使用电池：全部改为从不
        插入电源：全部改为从不

## 鼠标和触摸板

    设备中开启触摸板的“轻点触摸板点击” 
     触摸板和鼠标加速设置为10

# 配置火狐浏览器

    登陆
    设置dns：
        自动检测此网络的代理设置
    常规
        语言与外观-网站外观
            深色
        在“性能”中关闭
            使用推荐的性能设置
    "搜索-默认搜索引擎" 改为
        bing
    "隐私与安全-Firefox 数据收集与使用"
        全关闭
    拓展和主题（C S a）
        主题
            启用深邃
        插件
            点击所有视频编码器的右上角，选择“一律激活”
	
	about:config, layers.acceleration.force-enabled=True
# 换源

    打开网址:
        https://mirrors.tuna.tsinghua.edu.cn/help/debian/（已收藏至linux标签页）
    debian版本切换为当前版本，开启“使用非自由软件源”，复制软件源
    复制一份"/etc/apt/sources.list"，把复制的内容覆盖到原文件中，保存并关闭
    sudo apt update

# 软件包处理

## 安装pigchax

[pigchax](http://120.232.240.71:8888/?platform=linux_x86_64&cur_version=1693818944&deviceinfo=freather-ben%7CDebian%20GNU%2FLinux%2012%20%28bookworm%29&deviceid=3805ab00fcb444f5921c00cdd1110158)

## apt-fast

        sudo apt-get install aptitude wget
        安装
            按照https://github.com/ilikenwf/apt-fast#quick-install的方法，或
                /bin/bash -c "$(curl -sL https://git.io/vokNn)"
        配置
            按照https://github.com/ilikenwf/apt-fast#configuration的方法，或
                打开 /etc/apt-fast.conf
                取消注释
                    _APTMGR=apt-get
                    _MAXNUM=5
                    DOWNLOADBEFORE=true
                修改_MAXNUM为16
                保存并退出
            sudo apt-fast update

## 系统更新

    sudo apt-get autoremove --purge 'libreoffice?' ibus* -y
    sudo apt-fast update ;sudo apt-fast dist-upgrade -y ; sudo apt-get autoremove -y
    重启

## 执行以下命令

    sudo apt-fast install tmux git dos2unix tree tlp zsh growisofs xorriso wodim ffmpeg htop cpufrequtils sysfsutils git python3-pip pipx texlive-full cjk-latex latex-cjk-chinese fcitx5 fcitx5-chinese-addons xclip p7zip-rar timeshift blueman  neovim flatpak pandoc okular pandoc -y
        sh -c "$(wget https://gitee.com/gloriaied/oh-my-zsh/raw/master/tools/install.sh -O -)"

## git

    配置git
        git config --global user.name '1821653110Dx'
        git config --global user.email '3440423865@qq.com'
    生成公钥
        ssh-keygen -t rsa -C "3440423865@qq.com"
    添加到gitee
    在喜欢的目录执行以下命令
        git clone git@gitee.com:free-ben/work.git
        git clone git@gitee.com:free-ben/school.git

## zsh

    git clone https://gitee.com/mo2/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
    修改.zshrc
        设置
            ZSH_THEME='wedisagree'
            plugins=(git zsh-syntax-highlighting)
        添加
            bindkey \^U backward-kill-line

## pipx(不适用用于安装第三方库，适合用于cmd工具)

    pip3 config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
    pipx ensurepath
    重新开启终端
    pipx install  virtualenv
    pipx ensurepath

## python虚拟环境

    在～/tool/python/ 下执行 
        virtualenv venv
    启动 venv(不要去动移动venv，否则使用pip必报错)
        source ~/tool/python/venv/bin/activate
    pip install sympy numpy matplotlib ipython simpy scipy
    deactivate

## flatpak

    换源
        sudo flatpak remote-modify flathub --url=https://mirror.sjtu.edu.cn/flathub

# cpu配置

## 设置默认governor

    edit "/etc/sysfs.conf" and add
        devices/system/cpu/cpu<first core>/cpufreq/scaling_governor = <governor>
        ...
        devices/system/cpu/cpu<last core>/cpufreq/scaling_governor = <governor>
```txt
devices/system/cpu/cpu0/cpufreq/scaling_governor = schedutil
devices/system/cpu/cpu1/cpufreq/scaling_governor = schedutil
devices/system/cpu/cpu2/cpufreq/scaling_governor = schedutil
devices/system/cpu/cpu3/cpufreq/scaling_governor = schedutil
devices/system/cpu/cpu4/cpufreq/scaling_governor = schedutil
devices/system/cpu/cpu5/cpufreq/scaling_governor = schedutil
devices/system/cpu/cpu6/cpufreq/scaling_governor = schedutil
devices/system/cpu/cpu7/cpufreq/scaling_governor = schedutil
devices/system/cpu/cpu8/cpufreq/scaling_governor = schedutil
devices/system/cpu/cpu9/cpufreq/scaling_governor = schedutil
devices/system/cpu/cpu10/cpufreq/scaling_governor = schedutil
devices/system/cpu/cpu11/cpufreq/scaling_governor = schedutil
devices/system/cpu/cpu12/cpufreq/scaling_governor = schedutil
devices/system/cpu/cpu13/cpufreq/scaling_governor = schedutil
devices/system/cpu/cpu14/cpufreq/scaling_governor = schedutil
devices/system/cpu/cpu15/cpufreq/scaling_governor = schedutil
```
## 创建切换governor的脚本

    mkdir ~/tool/cpu/ -p
    在那个目录下创建 "powersave.sh" "schedutil.sh" "ondemand.sh" "performance.sh"，内容格式如下
        #!/usr/bin/zsh
    
        # ?_1 = the number of CPUS ; ?_2 = the type of governor
    
        for core in {0..?_1}
        do
        sudo cpufreq-set -g ?_2 -c $core
        done

# 输入法配置

    Fcitx配置
        输入法-拼音-设置
            页大小：10
            开启"启用云拼音"
            关闭“在程序中显示预编辑文本”“将嵌入预编辑文本的光标固定在开头”
            - [ ] 切换输入法时的行为=清空
            - [ ] 上一页,
            - [ ] 下一页.
            快速输入的触发键: Super ;
            - [ ] 关闭“使用v来触发快速输入”
        全局选项
            切换启用/禁用输入法
                "control+空格"改为: 右S
                "全角半角""韩文"删除
            删除
                临时在当前和第一个输入法之间切换
                向前切换输入法
                向后切换输入法
        附加组件
            云拼音
                后端：baidu
            经典用户界面（建议不用管）
                字体（只改大小）
                菜单字体（只改大小）
                托盘字体（只改大下）
                主题
        在/usr/share/fcitx5/punctuation/punc.mb.zh_CN中
        replace · with 【
        replace 「」with 】
        add ` ·

# 常用alias

```
# 对于bash，直接复制到/etc/bash.bashrc
# xalias
alias blender="/home/freather-ben/app/blender/blender"
alias freecad="/home/freather-ben/app/FreeCAD.AppImage"

alias ondemand="/home/freather-ben/tool/cpu/ondemand.sh"
alias performance="/home/freather-ben/tool/cpu/performance.sh"
alias powersave="/home/freather-ben/tool/cpu/powersave.sh"
alias schedutil="/home/freather-ben/tool/cpu/schedutil.sh"

alias activate="source ~/tool/python/venv/bin/activate"

alias bat0="upower -i /org/freedesktop/UPower/devices/battery_BAT0 | grep percentage"
alias freeram="echo 1 >/proc/sys/vm/drop_caches"
alias Rsync="rsync -aPv"
alias rsync_del="rsync --delete-before -av ~/trash/"
alias Aria2c="aria2c -s 16 -x 16 -j 16"
```

# 常用环境变量

```
# 对于bash，直接复制到/etc/bash.bashrc
public=/home/freather-ben/公共
templates=/home/freather-ben/模板
videos=/home/freather-ben/视频
pictures=/home/freather-ben/图片
documents=/home/freather-ben/文档
downloads=/home/freather-ben/下载
music=/home/freather-ben/音乐
desktop=/home/freather-ben/桌面

# 引号里面的是命令所在的目录，用于解决command not found 的问题
export PATH="$PATH:/usr/sbin/"
export PATH="$PATH:/usr/local/sbin/"

# 开启extglob
shopt -s extglob
```

# 应用的配置

## nano

    在/etc/nanorc下写入
        set autoindent
        set smarthome
        set nonewlines
        set softwrap
        set atblanks
        set linenumbers
        set tabsize 4
        set zap

## vim

    在root和当前用户目录下创建.vimrc，内容如下
        set guioptions-=T
        set autoindent nu cursorline nocompatible smarttab foldenable linebreak cindent
        set tabstop=4
        set shiftwidth=4
        set shortmess=atI
        set fdm=indent
        set guifont=Liberation\ Mono\ Regular\ 14
        set dictionary=/usr/share/dict/words
        color industry
        syntax on
        set mouse=a
        set hlsearch
        set ignorecase
        set incsearch
        set autochdir
        let g:markdown_fenced_languages =['c', 'cpp', 'python', 'html', 'tex', 'zsh', 'bash', 'make']
        imap ( ()<ESC>i
        imap [ []<ESC>i
        imap { {}<ESC>i
        imap （ （）<ESC>i
        imap 【 【】<ESC>i
        imap 《 《》<ESC>i
        inoremap " ""<ESC>i
        set wildmenu
        set wildmode=longest:list,full
        filetype on
        filetype indent on
        filetype plugin on
        set scrolloff=8
        set sidescrolloff=8
        set splitright
        set splitbelow

## neovim

    在root和当前用户下创建 .config/nvim/init.lua
            -- 编码方式 utf8
            vim.o.filetype = true
            vim.cmd('filetype plugin on')
    
            --vim.g.encoding = "UTF-8"
            --vim.o.fileencoding = "utf-8"
    
            -- jkhl 移动时光标周围保留8行
            vim.o.scrolloff = 8
            vim.o.sidescrolloff = 8
            -- 设置光标
            vim.opt.guicursor = "a:block"
            -- vim.opt.guicursor = "n-v-c-i:block"
            -- vim.opt.guicursor = "n-v-c:hor20-CursorNormal,i-ci:hor20-CursorInsert,r-cr:hor20-CursorReplace,o:hor20-CursorOther"
    
            -- 显示行号
            vim.wo.number = true
            -- 高亮所在行
            vim.wo.cursorline = true
            -- 显示左侧图标指示列
            -- vim.wo.signcolumn = "yes"
            -- 右侧参考线
            -- vim.wo.colorcolumn = "160"
            -- 缩进字符
            vim.o.tabstop = 4
            vim.bo.tabstop = 4
            vim.o.softtabstop = 4
            vim.o.shiftround = true
            -- >> << 时移动长度
            vim.o.shiftwidth = 4
            vim.bo.shiftwidth = 4
            -- 空格替代
            -- vim.bo.expandtab = true
            -- 新行对齐当前行
            vim.o.autoindent = true
            vim.bo.autoindent = true
            vim.o.smartindent = true
            -- 搜索大小写不敏感，除非包含大写
            vim.o.ignorecase = true
            vim.o.smartcase = true
            -- 搜索高亮
            vim.o.hlsearch = true
    
            vim.o.incsearch = true
            -- 命令模式行高
            -- vim.o.cmdheight = 1
            -- 自动加载外部修改
            vim.o.autoread = true
            vim.bo.autoread = true
            -- 折行
            -- vim.wo.wrap = true
            vim.wo.linebreak = true
            -- 光标在行首尾时<Left><Right>可以跳到下一行
            vim.o.whichwrap = "<,>,[,]"
            -- 允许隐藏被修改过的buffer
            vim.o.hidden = true
            -- 鼠标支持
            vim.o.mouse = "a"
            -- 禁止创建备份文件
            vim.o.backup = false
            vim.o.writebackup = false
            vim.o.swapfile = false
            -- 分割
            vim.o.splitbelow = true
            vim.o.splitright = true
            -- 自动补全不自动选中
            vim.g.completeopt = "menu,menuone,noselect,noinsert"
            -- 样式
            vim.o.background = "dark"
            vim.o.termguicolors = true
            vim.opt.termguicolors = true
            -- 菜单
    
            vim.o.wildmenu = true
    
            vim.o.shortmess = vim.o.shortmess .. "c"
            -- 补全显示10行
            vim.o.pumheight = 10
            vim.o.clipboard = "unnamedplus"
            -- 设置代码折叠
            vim.o.foldmethod = "indent"
            -- 目录
            vim.o.autochdir = true
            -- keymap
            vim.api.nvim_set_keymap('i', '(', '()<Left>', { noremap = true })  
            vim.api.nvim_set_keymap('i', '[', '[]<Left>', { noremap = true })  
            vim.api.nvim_set_keymap('i', '{', '{}<Left>', { noremap = true })
            vim.api.nvim_set_keymap('i', '"', '""<Left>', { noremap = true })
            vim.api.nvim_set_keymap('i', '（', '（）<Left>', { noremap = true })
            vim.api.nvim_set_keymap('i', '【', '【】<Left>', { noremap = true })
            vim.api.nvim_set_keymap('i', '《', '《》<Left>', { noremap = true })
            -- markdown高亮
            vim.g.markdown_fenced_languages = {'c', 'cpp', 'python', 'html', 'tex', 'zsh', 'bash', 'make'}
    
            -- 选区配色方案
            -- 淡灰色
            --vim.cmd([[  
            --    highlight Visual guibg=#D3D3D3 guifg=#000000 ctermbg=7
            --]])
            -- 淡蓝色
            --vim.cmd([[  
            --  highlight Visual guibg=#ADD8E6 guifg=#000000 ctermbg=102  
            --]])
            -- 淡黄色
            --vim.cmd([[  
            --  highlight Visual guibg=#FFFFE0 guifg=#000000 ctermbg=15  
            --]])
            -- 白色
            --vim.cmd([[  
            --  highlight Visual guibg=#FFFFFF guifg=#000000 ctermbg=white  
            --]])
            -- 淡紫色
            vim.cmd([[  
            highlight Visual guibg=#DDA0DD guifg=#FFFFFF ctermbg=130  
            ]])
            -- 深紫色
            --vim.cmd([[  
            --highlight Visual guibg=#800080 guifg=#FFFFFF ctermbg=52  
            --]])
    
            -- 状态栏
            vim.o.laststatus = 1
    
            -- 候选菜单
            vim.cmd([[  
            highlight Pmenu guibg=#333333 guifg=#FFFFFF gui=none ctermbg=235 ctermfg=15  
            highlight PmenuSel guibg=#FFFF00 guifg=#000000 gui=none ctermbg=136 ctermfg=0  
            ]])
    
            -- 终端模式
            local term_mode = vim.api.nvim_create_augroup("TERM_MODE", {clear = true})
            vim.api.nvim_create_autocmd({"TermOpen"}, {
            pattern = "*",
            group = term_mode,
            command = [[normal i]]
            })
            -- 用M = 快速开启和关闭zsh终端
            vim.api.nvim_set_keymap("n", "<A-=>", ":split term://zsh<CR>", {noremap = true, silent = true})
            vim.api.nvim_set_keymap("t", "<A-=>", "<C-\\><C-n>:bdelete! %<CR>", {noremap = true, silent = true})
            -- 用<ESC>进入普通模式
            vim.api.nvim_set_keymap("t", "<ESC>", "<C-\\><C-n>", {noremap = true, silent = true})
            -- 匹配括号颜色
            vim.cmd("highlight MatchParen  guifg=none")
    
            -- 折叠行颜色
            vim.cmd("highlight Folded guibg=#9999FF guifg=#DDDDDD")

## tmux

    创建.tmux.conf，内容如下
        set -g mouse on  
        setw -g mode-keys vi
    复制.vimrc到root和当前用户目录

## wps

    sudo chmod 000 /opt/kingsoft/wps-office/office6/wpscloudsvr
    杀死所有 wpscloudsvr
    设置
        其他-切换窗口管理模式
            多组件模式
        皮肤-皮肤和外观设置-自定义外观-界面-字体字号v
            设置合适的缩放
        pdf问题        
            添加该镜像源：deb http://security.debian.org/debian-security buster/updates main
            sudo apt-fast install libtiff5
            删除该镜像源

## obsidian

- #### 设置
    - 关于
        - disable 自动更新
    - 编辑器
	    - 新标签页的默认视图 = 阅读模式（new）
	    - disable 显示缩进参考线（new）
	    - disable 拼写检查
    - 文件与链接
        - 删除文件设置 = 移至软件回收站
        - 附件默认存放路径=指定的附件文件夹
        - 附件文件夹路径 = _resources
    - 外观
        - 字体-字体大小
        - 高级-缩放比例
        - CSS代码片段
    - 快捷键
        - C F1..6
    - 核心插件
        - 打开
            - 工作区
            - 斜杠命令
        - 关闭
            - 文件恢复
            - 日记
            - 字数统计
            - 反向链接
    - 白板
        - 新建画布文件的默认位置 = 指定的附录文件夹
- #### 族谱
    - 筛选
        - 关闭孤立文件
- #### 额外插件(new)
	- image toolkit
		- 快捷键设置-为触发弹出查看图片设置快捷键=CTRL
	- quick latex
	- mousewheel image zoom
	- docxer
## timeshift

- 位置
  
  - 计划
    - 取消每日
  - 用户
    - 选择Include all
      
      ## mousepad

- 编辑首选项
  
  - 视图
    
    - 显示
      - 打开“显示行号，高亮当前行，高亮括号对，为长行换行”
    - 字体
      - ～
    - 配色方案
      - oblivion
  
  - 编辑器
    
    - 缩进
      - tab宽度=4
      - 开启“启用自动缩进
    - 智能键
      - Home/End : 设置为总是
        
        ## thunar
        
        按C 2
        文件管理器首选项-行为-交互菜单
        enable 显示永久删除...
        
        ## librecad
        
        options-widget_options
        enable style, choose Adwaita-dark
        
        ## freecad
        
        Edit-Preferences-general
        style-sheet = Dark-modern-blue
        
        ## gimp
        
        首选项-主题，打开当前主题目录下的gtkrc
        修改font_name的11为12
        
        ## texstudio
        
        Options-configure_texstudio
        enable "show Advanced Options"
        General
        set [style, color scheme, font, fontsize] = [Orion Dark, Modern-dark, Dejavu Sans, 13]
        Editor
        set [font Family, font size] = [Dejavu Sans mono, 13]
        set Show_line_number = All_line_number
        Adv.Editor
        disable "Try to automatically choose best dispaly options"
        enable "Disable fixed pitch mode"
        
        ## 非deb应用
        
        在当前用户目录下创建app/icons，把所有非deb应用移动到app
    
    
    blender
      interface
    
          resolution
          tooltips-python_tooltops
          text rendering
              turn off "anti-aliasing"
    
      viewport
    
          quality
              viewport anti-aliasing = no anti-aliasing
              smooth wires = all turn off
    
      navigation
    
          orbit&pan
              orbit method = trackball
    
      keymap
    
          pan view = C mouse3
          zoom = S mouse3
    
    把所有的icon移动到icons,获取方法
      /tmp/.xxx/usr/share/application
    把每个的*.desptop复制到/usr/share/applications,并修改Exec,Icon
    
    # 新利得软件管理器
    
    设置-首选项
      常规信息-系统升级 = 总是询问
    
    # n卡驱动安装
    
    一、安装必须的工具

```bash
sudo apt install dkms build-essential gcc make linux-headers-$(uname -r)
```

二、禁止系统自带nouveau显卡驱动

1.修改/etc/default/grub文件，在启动时直接禁用nouveau驱动：

```bash
sudo vim /etc/default/grub
```

在文件中的GRUB_CMDLINE_LINUX参数中加入下面内容：

```bash
rd.driver.blacklist=nouveau
```

更新grub：

```bash
update-grub
```

2.在系统中禁用nouveau驱动：

```bash
echo "blacklist nouveau" | sudo tee -a /etc/modprobe.d/blacklist-nvidia-nouveau.conf
echo "options nouveau modeset=0" | sudo tee -a /etc/modprobe.d/blacklist-nvidia-nouveau.conf
sudo update-initramfs -u
```

三、安装nvidia驱动：

1.下载驱动并设置执行权限：

```bash
进入https://www.nvidia.cn/Download/index.aspx?lang=cn
    设置
        产品类型:GeForce
            产品系列：GeForce RTX 30 series (Notebooks)
            产品家族：GeForce RTX 3060 Laptop GPU
            操作系统: Linux 64-bit
            下载类型：生产分支
            语言:Chinese(Simplified)
    下载.run    
进入tty运行
    sudo /etc/init.d/lightdm stop
    sudo /etc/init.d/lightdm status

sudo chmod +x NVIDIA-Linux-x86_64-550.67.run
```

2.安装：

```bash
sudo ./NVIDIA-Linux-x86_64-550.67.run
```

4.重启：

```bash
reboot
```

四、禁用内核升级

内核升级后需要重新安装驱动，为省事，禁用内核升级：

```bash
dpkg --get-selections | grep linux
apt-mark hold linux-image-<版本号>-amd64 linux-headers-<版本号>-amd64 linux-headers-<版本号>-common
```

其中的版本号直接抄dpkg中查到的数字。

五、查看驱动

```bash
nvidia-smi
```

六、安装中遇到的一些问题

1.安装时会提示是否需要考虑兼容32位应用，提问："install nvidia's 32-bit compattibility libraries"。如果需要，应在安装驱动前按下面步骤处理，并在安装中选择yes：

1）更新apt源

```bash
sudo apt update
```

2）安装32位兼容库：

```bash
sudo apt install lib32ncurses5 lib32z1 lib32bz2-1.0
```

# else

    设置
        显示
            点击"主显示器右边"的灯泡
                输出：主要的
    处理开机亮度最大
        vim ~/tool/brightness.sh，内容如下
            #!/usr/bin
            echo 75 > /sys/class/backlight/nvidia_0/brightness
        sudo chmod +x ~/tool/brightness.sh
        sudo crontab -e,添加如下内容    # sudo crontab -e 是以root权限自动执行脚本
            @reboot /home/freather-ben/tool/brightness.sh
---
---
#  如果缺失的模块没有在安装完系统后仍然缺失
## 方法1
    把固件文件放到/lib/firmware/中
        没有这个目录，先apt-get install firmware-*,如果目录仍然没有,自己手动建一个

## 方法2
### intel 网卡

    # 安装无线网卡驱动
    sudo apt-get update
    sudo apt-get install firmware-iwlwifi
    # 重新载入模块
    modprobe -r iwlwifi
    modprobe  iwlwifi
