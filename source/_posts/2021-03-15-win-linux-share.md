---
title: Linux桌面环境与Win10之间共享文件夹的互相访问（基于Samba，以Deepin为例）
date: 2021-03-15 01:30:25
author: coolxy
---

# Linux桌面环境与Win10之间共享文件夹的互相访问（基于Samba，以Deepin为例）

## 一、解决理念
一直喜欢Deepin系统，也好用，但办公室的办公PC因为涉及到要随时用OA的web系统收发文（有UKEY），要盖电子印章（有Ukey），无法使用Deepin，故此办公PC 是Win10系统，另有一台笔记本安装Deepin，之前传文件一直用“飞鸽传书”解决，为解决文件的互相共享，百度了许多文章，终端自己解决了。
## 二、从Deepin访问Win10共享
Win10设置共享后，其它的Win系统均可无问题访问，但Deepin访问一直没办法，查了许久资料加上自己试了之后 ，确定为Win10系统安装时默认不安装Samba组件，而Deepin下访问是用Samba访问，所以肯定访问不了。
前提：首先得在同一个局域网段
### 1、Win10安装Samba组件：
控制面板—>卸载程序—>启用或关闭Windows功能—>勾选smb

### 2、设置共享文件夹
这一步简单，许多人都会，不多说。在实际设置中，我已经关闭了windows的防火墙（是因为关闭防火墙，Deepin云打印机才能使用）
### 3、Deepin下安装Samba，这个Deepin是已经安装的了
安装命令：sudo apt install samba
访问：在文件管理器地址栏输入：smb://win10IP/ 回车后就可以看到win10共享出来的文件夹了

也可以直接将共享内容挂载到系统下：
#mkdir /mnt/共享文件夹 (自己建一个目录，这个根据自己的情况而定)
#mount -t cifs //192.168.1.122/共享文件夹 -o username=本机用户名,password=本机密码 /mnt/共享文件夹  （即将win10共享出来的“共享文件夹”文件夹挂载到“/mnt/共享文件夹”下）
至此就可以直接访问了，但每次开机后要重新输入和挂载，很烦，可设置开机自动挂载：
通过修改fstab文件，开机自动挂载
修改/etc/fstab文件，文件最后加入：
//192.168.1.122/共享文件夹   /mnt/共享文件夹 cifs auto,username=本机用户名,password=本机密码 0 0 



## Win10访问Deepin共享文件夹
### 1、首先还是要安装samba
sudo apt-get install samba
### 2、设置共享目录
在目录上右键—>属性—>设置共享，并将目录权限设置为777

mkdir /home/share  
sudo chmod 777 /home/share

### 3 修改samba配置文件
修改 /etc/samba/smb.conf  
sudo vim /etc/samba/smb.conf

在smb.conf文件最后加上以下内容:
```
[share]
path = /home/share
public = yes
writable = yes
valid users = name
create mask = 0644
force create mode = 0644
directory mask = 0755
force directory mode = 0755
available = yes
```
关于smb.conf的几点解释：
(1) [share]表示共享文件夹的别名，也就是在其它机子上看到的共享文件夹名，之后将直接使用这个别名
(2)  valid users “name”设置为你当前的Linux用户名，例如我的是”name”，因为第一次打开共享文件夹时，需要验证权限。
### 4 设置登录密码
新建/etc/samba/smbpasswd文件，这是存储密码的文件
sudo touch /etc/samba/smbpasswd 
根据3设置的valid users，设置用户name的密码，新增用户name
sudo smbpasswd -a name
输入两次密码后，会提示 Added user name. 表示设置成功

重新启动samba服务器

sudo /etc/init.d/samba restart

 测试是否共享成功
安装samba的linux客户端：
sudo apt-get install smbclient 
smbclient -L //localhost/share
如果出现让你输入密码的界面，那么就是设置成功了，输入之前设置的密码即可以看到共享的内容了。
5.在windows上测试
打开windows文件管理器，输入 \\ip地址或主机名\share
Linux的ip地址可通过ifconfig查看
选择记住凭据，下次输入地址后无需登录
第一次打开可能需要几秒时间，耐心一点

* 心得：
原来Windows之间共享的时候太顺利，用同样的方式在Deepin与Win之间共享，无论如何也成功不了，原因在于Deepin与win之间的共享通道是Samba，win系统上要安装samba组件，就打开了通道，共享成功
Deepin共享文件夹后，在win系统打开要网络凭据，原来一直以来要用Deepin系统账户和密码，可无论如何也不行，后来一想，如果Deepin系统账户密码都给人了，系统就危险了，所以要在samba内重新创新用户名和密码才行。


* 扩展知识：
Mount远程目录并让本地非root用户可读可写

远程与本地是两台Linux机器，要实现如题效果，传统的nfs的mount方式虽然简单方便却不行
nfs的方式：
sudo mount -t nfs  -o rw 192.168.0.xx:/path  /mnt/test
在本地你会发现/mnt/test下的文件用户为nobody，普通用户可以读，但是非root用户写不了(不用sudo不用su)，
有的人想通过改/etc/fstab 或者远程主机的/etc/exports来实现，
我告诉你趁早放弃，nfs没有这个功能，它无法指定uid gid 用户名，密码。
 
cifs可以解决这个问题，通俗点讲就是samba的方式
远程主机安装samba服务
部分/etc/samba/smb.conf 内容
[testuser]
    path = /home/testuser/share
    read only = no
;    browseable = yes
    valid users = testuser
共享目录/home/testuser/share，有效用户为testuser
 
本地操作如下
安装 cifs-utils       sudo apt-get install  cifs-utils 神马的
命令id得到本地用户localuser的id,gid     
比如得到uid=1000(localuser) gid=1000(localuser)   
修改/etc/fstab
//192.168.0.xx/testuser/  /mnt/test/   cifs    rw,noauto,defaults,username=testuser,password=testuserpassword,uid=1000,gid=1000    0       0
然后sudo mount /mnt/test就会挂载，此时localuser翻身做主人了,注意为了安全fstab中可以不写password=testuserpassword这段，然后在mount时手动输入密码，如果要开机自动挂载，可以把noauto改成auto,或者在启动脚本中mount