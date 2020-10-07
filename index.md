## MSTIFIY的学习笔记

#### Linux(ubuntu)入门

##### linux 和 ubuntu 关系

##### ![](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_png/IP70Vic417DMCpvv1p04F06oj5HoUFouNAwuHMunQSoY9IG7IslpibT0QAOBHw7Dng22V7vwiayUIoibKTlhklrURA/640?wx_fmt=png)



##### ubuntu 发行版本

**Ubuntu**严格来说不能算一个独立的发行版本，Ubuntu是基于Debian的unstable版本加强而来，可以这么说，Ubuntu就是 一个拥有Debian所有的优点，以及自己所加强的优点的近乎完美的 Linux桌面系统。根据选择的桌面系统不同，有三个版本可供选择，基于Gnome的Ubuntu，基于KDE的Kubuntu以及基于Xfc的 Xubuntu。特点是界面非常友好，容易上手，对硬件的支持非常全面，是最适合做桌面系统的Linux发行版本。

Ubuntu 发布版本的官方名称是 Ubuntu X.YY ，其中 X 表示年份（减去2000），YY 表示发布的月份。

Ubuntu 没有像其它软件一样有 1.0 版本，是因为其第一个版本是发布于 2004 年。所以Ubuntu的生日是10月20日。

“ubuntu”一词（译为[乌班图](https://zh.wikipedia.org/wiki/乌班图)），意思是“人性”、“我的存在是因为大家的存在”。

每两年的 4 月份，都会推出一个长期支持版本（LTS），其支持期长达五年，而非 LTS 版本的支持期通常只有半年。



##### ubuntu 文件目录结构

-  Linux没有盘符这个概念，只有一个根目录，所有文件都在它（/）下面，每个用户都是在/home目录下面建立自己的文件夹。

- 根目录是整个系统最重要的一个目录，因为不但所有的目录都是由根目录衍生出来的， 同时根目录也与开机/还原/系统修复等动作有关。 由于系统开机时需要特定的开机软件、核心文件、开机所需程序、 函式库等等文件数据，若系统出现错误时，根目录也必须要包含有能够修复文件系统的程序才行。

  ```
  在终端使用"ls"命令后，蓝色表示目录，青色表示链接，黑色表示文件。
  ```

- ```
  /   根目录  
      │  
      ├boot/      启动文件。所有与系统启动有关的文件都保存在这里  
      │    └grub/   Grub引导器相关的文件  
      │  
      ├dev/       设备文件  
      ├proc/      内核与进程镜像  
      │  
      ├mnt/      临时挂载  
      ├media/   挂载媒体设备  
      │  
      ├root/      root用户的$HOME目录  
      ├home/           
      │    ├user/   普通用户的$HOME目录  
      │    └.../  
      │  
      ├bin/      系统程序  
      ├sbin/      管理员系统程序  
      ├lib/      系统程序库文件  
      ├etc/      系统程序和大部分应用程序的全局配置文件  
      │   ├init.d/   SystemV风格的启动脚本  
      │   ├rcX.d/   启动脚本的链接，定义运行级别  
      │   ├network/   网络配置文件  
      │   ├X11/      图形界面配置文件  
      │  
      ├usr/        
      │   ├bin/      应用程序  
      │   ├sbin/   管理员应用程序  
      │   ├lib/      应用程序库文件  
      │   ├share/   应用程序资源文件  
      │   ├src/      应用程序源代码  
      │   ├local/        
      │   │     ├soft/      用户程序        
      │   │     └.../      通常使用单独文件夹  
      │   ├X11R6/   图形界面系统  
      │  
      ├var/         动态数据  
      │  
      ├temp/         临时文件  
      ├lost+found/   磁盘修复文件
  ```

- ```
  隐藏文件查看：
  方案一，若使用桌面可视化窗口，进入该待显示的文件路径，进入ctrl+h，则显示隐藏文件
  
  方案二，若使用命令行，则使用命令：ls-a显示所有文件，也包括隐藏文件
  ```



#####  linux 快捷键和常见终端命令

```
常用命令

一、文件目录类

1.建立目录：mkdir 目录名
2.删除空目录：rmdir 目录名
3.无条件删除子目录： rm -rf 目录名
4.改变当前目录：cd 目录名 (进入用户home目录：cd ~;进入上一级目录：cd -)
5.查看自己所在目录：pwd
6.查看当前目录大小：du
7.显示目录文件列表：ls -l (-a：增加显示隐含目录)
其中：蓝：目录;绿：可执行文件;红：压缩文件;浅蓝：链接文件;灰：其他文件;红底白字：错误的链接文件
8.浏览文件：more 文件名.txt;less 文件名.txt
9.复制文件： cp 源文件 目标文件 (-r：包含目录)
10.查找文件：(1)find (2)locate 命令名
11.链接：(1)建立hard链接：ln 来源文件 链接文件(-d：创建目录链接）；(2)建立符号链接：ln -s 来源文件 链接文件

二.驱动挂载类

1.检查硬盘使用情况：df -T -h
2.检查磁盘分区：fdisk -l
3.挂载软硬光区：mount -t /dev/fdx|hdax /mnt/目录名
其中：：modos--FAT16;vfat--FAT32;ntfs--NTFS;光驱--iso9660
支持中文名：mount -o iocharset=x /dev/hdax /mnt/目录名(其中：x=cp936或
挂载光驱：mount -t auto /dev/cdrom /mnt/cdrom
挂载ISO文件：mount -t iso9660 -o loop xxx.iso /path
4.解除挂载：umount /mnt/目录名
解除所有挂载：umount -a
5.建立文件系统：mkfs -t /dev/hdxx。其中：ftype：ext2、ext3、swap等

三.程序安装类

1.RPM包安装：(1)安装 rpm -ivh somesoft.rpm
(2)反安装 rpm -e somefost.rpm
(3)查询 rpm -q somefost 或 rpm -qpi somefost.rpm(其中：p未安装;i包含的信息)
(4)查询安装后位置：rpm -ql somefost.rpm
(5)升级安装：rpm -Uvh somesoft.rpm
(6)强制安装：rpm -ivh --nodeps somesoft.rpm 或 rpm -ivh --nodeps --force somesoft.rpm
2.源代码包安装：
查阅README
基本用法 (1)配置：解压目录下 ./configure
(2)编译：解压目录下 make
(3)安装：解压目录下 make install
3.src.rpm的安装

四.压缩解压类

1.tar.gz类：(1)解压：tar -xvzf 文件.tar.gz；(2)tar.gz解至tar：gzip -d 文件.tar.gz(2)压缩：gzip待压缩文件
2.tar未压缩类：(1)解包：tar -xvf 文件.tar；(2)打包：tar -cvf 文件.tar 文件列表
3.zip类：(1)解压：unzip 文件.zip -d dir；(2)压缩：zip zipfile 待压缩文件列表
4.bz2类：(1)解压：bunzip2 文件.bz2或bzip2 -d 文件.bz2；(2)压缩：bzip2 待压缩文件
5.z类：(1)解压：uncompress 文件.z；(2)压缩：compress 文件

五.进程控制类

1.列出当前进程ID：ps -auxw
2.终止进程：(1)终止单一进程：kill 进程ID号
(2)终止该程序所有进程：Killall 程序名
(3)终止X-Window程序：xkill
3.查看资源占用情况：(1)top (2)free (3)dmesg
4.查看环境变量值：env
5.重启：(1)reboot (2)Ctrl Alt Del (3)init 6
6.关机：(1)shutdown -h now (2)halt (3)init 0
7.切换桌面：switchdesk gnome|KDE|...

六.程序运行类

1.查询命令：whereis 命令名
2.后台运行X-Window程序：程序名&
3.强行退出X-Window程序：Ctrl Alt Backspace
4.查看帮助：
(1)简明帮助：命令名 --help | less
(2)更多帮助：man 命令名
(3)info 命令名
(4)help 命令名
5.查看系统路径：echo $PATH
6.查看当前shell堆栈：echo $SHLVL
7.< / >：输入/输出重定向;|：管道左的输入是管道右输入

六.用户帐号类

1.增加用户帐号：(1)用 户 名：adduser 用户帐号名
(2)设置密码： passwd 用户帐号名
2.删除用户帐号：userdel 用户帐号名
3.增加用户组：groupadd 用户组名
4.删除用户组：groupdel 用户组名
5.暂时终止用户帐号：passwd -l 用户帐号名
6.恢复被终止帐号：passwd -u 用户帐号名
7.权限设定
(1)chmod -a|u|g|o |-|=r|w|x 文件/目录名
其中：a--所有用户(all);u--本用户(user);g--用户组(group);o--其他用户(other users)
--增加权限;---删除权限;=--设置权限
文件：r--只读权限(read);w--写权限(write);x--执行权限(execute)
目录：r--允许列目录下文件和子目录;w--允许生成和删除目录下文件;x--允许访问该目录
(2)chmod xxx 文件/目录名
其中：execute=1;write=2;read=4 x取值：0--没有任何权限(常用);1--只能执行(不常见);2--只能写(不常见);3--只能写和执行(不常见);4--只读(常见);5--只读和执行(常见);6--读和写(常见);7--读.写和执行

七.vi编辑类
打开文件 vi filename
1.进入后为命令模式：(1)插入i；(2)打开0；(3)修改c；(4)取代r；(5)替换s
2.经(1)后进入全屏幕编辑模式。
3.命令模式-->编辑模式(a/i)；编辑模式-->命令模式(Esc)；命令模式-->末行模式(：)。
4.：w/w newfile保存
5.：q/q!退出vi（或者shift+zz退出）；：wq保存退出

八.网络服务

1.显示网络接口参数：ifconfig
2.显示系统邮件：mail
3.启动/终止web服务：httpd -k start|stop|restart
4.查看网络状况：(1)联机状况：ping xxx.xxx.xxx.xxx；
(2)显示网络状况：netstat ，其中：options：-a==所有sockets；-l==包含网络设备；-n==数字IP；-o==其他信息；-r==路由表；
-t==只列TCP sockets；-u==只列UDP sockets；-w==只列raw sockets；-x==只列unix Domain sockets

来源： https://www.cnblogs.com/aijianshi/p/5764215.html
 
常用快捷键
一.移动光标快捷键
　　ctrl+f  向前移动一个字符  (f: forward)
　　ctrl+b 向后移动一个字符  (b: backward)
　　alt+f   向前移动一个单词  
　　alt+b  向后移动一个单词  
　　ctrl+a 移动到当前行首   (a: ahead)
　　ctrl+e 移动到当前行尾   (e: end)
　　ctrl+l  清屏，并在屏幕最上面开始一个新行
　　ctrl+r  检索使用过的历史命令 （r retrieve）
 
二.编辑命令行快捷键
　　ctrl+d  删除当前的字符
　　ctrl+t  交换当前字符和前一个字符的位置
　　alt+t   交换当前单词和前一个单词的位置
　　alt+u  把当前单词变成大写
　　alt+l   把当前单词变成小写
　　alt+c  把当前单词变成首字母大写的单词
　　ctlr+v 添加一个特殊字符，例如，要添加一个制表符，按ctrl+v+tab
 
三.剪切、粘贴快捷键
　　ctrl+k  剪切文本直到行的末尾
　　ctrl+u  剪切文本直到行的起始
　　ctrl+w  剪切光标前的单词
　　alt+d   剪切光标后的单词
　　ctrl+y  粘贴最近剪切的文本
　　alt+y   回退到先前剪切的文本并粘贴它
　　ctrl+c  删除整行
　　
source命令
用法：source FileName
作用：在当前bash环境下读取并执行FileName中的命令。
注：该命令通常用命令“.”来替代。
```



##### vim



