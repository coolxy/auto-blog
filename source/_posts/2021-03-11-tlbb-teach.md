---
title:  "天龙八部私服架设教程"
date:   2021-03-11 22:03:25
author: coolxy
categories: 
  - 游戏人生
  - 天龙八部
tags: 天龙八部,架设教程
---

# 天龙八部私服架设教程

## 一、环境架设

安装好Linux，一般用ubuntu centos等，可直接使用已搭建好mysql和驱动的ubuntu，或者CentOS。这里略过。

可用VMware 直接启动系统，在VM中Edit -> virtual network setting -> VMnet8 -> NAT -> Subnet IP 192.168.1.0

## 二、换端操作

### 1、上传服务端版本

利用Winscp 将tlbb.tar.gz 服务端上传到/home 目录，再用CRT连接后，解压：

```
cd /home
sudo tar zxvf tlbb.tar.gz
```

### 2、更改配置文件

配置文件在/home/tlbb/Server/Config内，共有个文件：ServerInfo.ini、LoginInfo.ini、Share***.ini



### 3、运行

```
cd /home
sudo ./run.sh
```

## 三、



