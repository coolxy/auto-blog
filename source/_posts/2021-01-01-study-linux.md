---
title: Linux 学习笔记-以deepin为例(持续更新)
date: 2021-01-01 14:18:45
author: coolxy
categories: 
  - Linux
tags: linux
---
# Linux 学习笔记-以deepin为例（持续更新）

## 第一章 系统安装
   首先下载iso格式镜像。
### 实体机安装
#### 方法一：刻录U盘安装，利用官方工具，可在win、linux环境下
win：

limux：利用dd命令

### VM虚拟机安装
  
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
- *.deb二进制包安装：  
`dpkg -i *.deb`  
- find查找文件  
`find path -name 'file'`  
Eg:`find / -name like.txt`  在'/'目录下查找'like.txt'文件，可用'*'、'?'通配符    



### 2.2文件及目录操作：
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

### 2.3权限操作：  
- chown设置文件/目录拥有者：  
`chown user path(dir/files)`  
- chmod设置文件目录权限：  
`chmod -R 777 path(dir/file)`  
这里的777是权限（详见权限章节）  





### 其他命令
- 创建连接ln：  
`ln -op old_path new_path`  
-op: -s  为软连接  
- tar解压：  
`tar zxvf file.tar.gz`  
- tar压缩打包：  
`tar zcvf file.tar.gz path(dir/files)`  
- 

  
## 第三章 deepin桌面配置

## 第四章 软件操作
### 4.1常用软件

## 第五章 种类技巧