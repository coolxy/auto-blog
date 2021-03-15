---
title: Linux 学习笔记-以deepin为例(持续更新)
date: 2021-01-01 14:18:45
author: coolxy
categories: 
  - Linux
tags: linux
top: true
---
# Linux 学习笔记-以deepin为例（持续更新）

## 第一章 系统安装
   首先下载iso格式镜像。
### 实体机安装
#### 方法一：刻录U盘安装，利用官方工具，可在win、linux环境下
win：

limux：利用dd命令

### VM虚拟机安装

### 1.3 系统目录及其作用说明

|目录树|表述|
|----|----|
|/|根目录，其它所有文件和目录均从根目录延伸而出|
|/bin/|存放系统命令的目录，普通用户和超级用户都可以执行|
|/sbin/|存放和系统环境设置相关的命令，只有超级用户可以使用这些命令进行系统环境配置，但有些命令可以允许被普通用户查看|
|/usr/bin/|usr(unix systemm  resourse) 存放系统命令的目录，系统用户和超级用户都可以执行（这些命令和系统启动无关），在单用户模式下不能执行|
|/usr/sbin/|存放根文件系统不必要的系统管理命令|
|/boot/|系统启动目录，保存系统相关的文件，如内核文件和启动引导(grub)|
|/dev/|设备文件保存位置（Linux中所有的硬件设备都以目录文件形式展示在Linuxd的/dev目录下）|
|/etc/|配置文件保存位置（默认）|
|/home|普通用户的家目录|
|/home/user/.config|程序的配置文件目录|
|/lib/|系统调用函数库保存位置|
|/lost+found/|当系统意外崩溃或机器意外关机，而产生一些文件碎片放在此目录下。|
|/media/|/mnt/
|/misc/|挂载目录|
|/opt/|第三方安装软件的保存位置。|
|/proc/|虚拟文件系统，该目录中的数据并不保存在硬盘，而是保存在内存中。主要保存系统的内核，进程，外部设备状态和网络状态。|
|/sys/|虚拟文件系统，保存在内存中，主要保存内核相关信息|
|/root/|超级用户的家目录|
|/srv/|服务数据目录。一些系统服务启动之后，可以在这个目录中保存所需要的数据 |
|/tmp/|系统存放临时文件的目录。|
|/usr/|(unix software resourse)系统软件资源目录|
|/var/|动态数据保存|



## 第二章 常用终端命令
运行命令，不加入路径指在当前目录下操作，加入路径就在路径上操作。  
###  2.1系统管理相关命令
- 以管理员运行：  
`sudo commond`  
- 安装软件：  
`sudo apt-get install SoftName`  
- 卸载软件：  
`sudo apt remove SoftName`
- 查看系统信息  
`uname -a`
- *.deb二进制包安装/卸载：  
安装：`dpkg -i *.deb`  
卸载：`sudo dpkg -r xxSoftName`  
- find查找文件  
`find path -name 'file'`  
Eg:`find / -name like.txt`    在'/'目录下查找'like.txt'文件，可用'*'、'?'通配符    



### 2.2文件及目录操作命令：
- 打印目录列表：  
` ls -all`  
- 文件/目录复制：  
`cp old new`  
- 文件/目录移动：  
`mv old new`  
- 删除文件/目录（非空目录加-r递归，加-f不提示）：  
`rm -op path`  
- 改变目录 cd:  
`cd path`  
- 打印当前路径pwd：  
`pwd'
- 新建文件夹mkdir：  
`mkdir name`  
`mkdir -r path`  #-r为递归创建  
- 运行当前目录下文件：  
`./filename`  
- 编辑文件vim 
`vim file`  
编辑按i键  退出按ESC  再按：  
:q   为退出不写入
:wq  为写入并退出  
:!q  为强制退出  
- 查看文件内容：  
cat file  

### 2.3 权限操作命令：  
- chown设置文件/目录拥有者：  
`chown user path(dir/files)`  
- chmod设置文件目录权限：  
`chmod -R 777 path(dir/file)`  
这里的777是权限（详见权限章节）  

### 2.4 网络操作命令  
* 2.4.1 ssh 终端远程连接：  
`ssh -p [port] user@[ip or URL]`  
Eg:`ssh -p 222 root@abc.cn`

* 2.4.2 查看本机ip地址  
`ifconfig -a`

* 修改IP地址（Ubuntu）  
方法一：修改网络配置文件：  
\# vim /etc/network/interfaces  

* 重启网络服务：  
  \# /etc/init.d/networking restart



### 其他命令
- 创建连接ln：  
`ln -op old_path new_path`  
-op: -s  为软连接  
- tar解压：  
`tar zxvf file.tar.gz`  
- tar压缩打包：  
`tar zcvf file.tar.gz path(dir/files)`  
OP：-c 建立压缩文件  
-x 解开压缩包  
-z 具有gzip属性？  
-j 同时具有bzip属性？  
-f 使用档名，后立即接档名  
* zip/unzip命令  
zip -r zip_file.zip FilesDir  
unzip zip_file.zip  
-r 递归处理，将指定目录下所有文件和子目录一并处理  

  


## 第三章 deepin桌面配置
### 3.1 win10与deepin之间共享访问

#### 3.1.1 windows与Linux之间的共享，需要samba组件支持，连接通道，所以windows与Linux都要安装samba组件。

* windows安装：

  控制面板—>卸载程序—>启用或关闭Windows功能—>勾选smb—>重启计算机

* Linux安装：

  sudo apt-get install samba

#### 3.1.2 deepin访问win10共享



### 3.2 创建桌面及开始菜单快捷方式

开始菜单路径：/usr/share/applications

创建快捷方式：
```
cd /usr/share/applications
touch file.desktop
```
file.desktop快捷方式内容：  
```
[Desktop Entry]
Type=Application
Name=应用名称
GenericName=Folder Comparison and Synchronization
GenericName[de_DE]=Ordnervergleich und Synchronisation
Exec=应用路径
Icon=ICO图标路径
NoDisplay=false
Terminal=false
Categories=Utility;FileTools;
StartupNotify=true
```

### 3.3 
#### 3.3.1 设置定时关机
编辑/etc/crontab:添加一条命令：  
`vim /etc/crontab`  
`15 18 * * * root /sbin/shutdown -h now`  
即可实现每天18:15关机。

### 3.4




## 第四章 软件操作
### 4.1 ISO镜像操作
* **把光盘复制成ISO文件**
* 方法一：  
> 把光盘放入光驱，系统会自动挂载光盘，桌面上出现光盘图标，用鼠标右键点击光盘图标选择“复制光盘”，在出现的对话框里选择制作镜像文件即可

* 方法二：  
> 假设光盘设备文件是/dev/cdrom，使用如下命令即可  
> #cp /dev/cdrom filename.iso

上述命令把光盘复制生成一个ISO文件filename.iso。


*  **文件和目录制作成ISO：**
使用 mkisofs 命令：  
#mkisofs -o filename.iso dir1 dir2 file1 file2  
上述命令会把目录dir1、dir2和文件file1、file2一起制作成一个ISO文件filename.iso

* ISO文件的挂载：  
要使用ISO文件，只需要把该ISO文件挂载到系统的某个空目录即可，比如：  
#mkdir /mnt/iso
#mount -o loop filename.iso /mnt/iso   
上述命令会把ISO文件filename.iso挂载到/mnt/iso目录里，访问 /mnt/iso目录即是访问ISO文件里的内容。

* ISO镜像文件的卸载：  
`sudo umount /mnt/iso`  

第二种挂载方法：  
使用 Furius ISO Mount 软件，该方法的优点是无需记住以上命令，也无需输入用户密码提权，推荐大家使用。
首先安装 Furius ISO Mount，Ubuntu 用户可在 Ubuntu 软件中心搜索安装，或者在终端中输入sudo apt-get install furiusisomount。其他 Linux 发行版请使用相应软件包管理器安装或自行编译安装。
注：由于权限问题，部分发行版（Ubuntu 用户无需进行此操作）可能需要将用户添加到 fuse 组，执行sudo adduser username fuse即可。

## 第五章 各类技巧