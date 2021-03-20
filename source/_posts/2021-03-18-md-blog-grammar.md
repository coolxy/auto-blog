---
title: md博客文章用到的markdown语法
date: 2021-03-18 22:11:02
author: coolxy
hide: true
categories: 
 - 教程技巧
 - md博客语法
tags: 
password: 123
abstract: 此文章已加密了, 需要输入密码查看.
message: 您好, 这里需要密码.
wrong_pass_message: 抱歉, 这个密码看着不太对, 请再试试.
wrong_hash_message: 抱歉, 这个文章不能被校验, 不过您还是能看看解密后的内容.
---

# <center>md博客文章用到的markdown语法</center>

需要在文章消息头部写什么呢，大概需要以下内容

```
---
title: 
date: 
author: 
sticky: 
hide: false
categories: 
tags: 
password: 
abstract: 此文章已加密了, 需要输入密码查看.
message: 您好, 这里需要密码.
wrong_pass_message: 抱歉, 这个密码看着不太对, 请再试试.
wrong_hash_message: 抱歉, 这个文章不能被校验, 不过您还是能看看解密后的内容.
banner_img: 
index_img: 
---

Copy
```

写md文章时，手动输入，需要在文章消息头部写什么呢，大概需要以下内容

```
---
title: 
这是文章标题

date: 
文章日期 如 2021-02-25 10:31

author: 
填写作者名字

sticky: 
主题的排序，直接填数字，可以用来做顶置

hide: 
是否隐藏文章 是true 否false或空着

categories: 
分类 输入分类名称即可

tags:
标签 输入标签名称即可

tags:
- 加密文章
password: 
abstract: 此文章已加密了, 需要输入密码查看.
message: 您好, 这里需要密码.
wrong_pass_message: 抱歉, 这个密码看着不太对, 请再试试.
wrong_hash_message: 抱歉, 这个文章不能被校验, 不过您还是能看看解密后的内容.
这个如果文章需要加密时，可设置

banner_img: 
这个是顶上的大图

index_img: 
这个是封面图

---


Copy
```

有些属性还是得根据主题，来修改，上面这些是根据我自己的主题来的

加密文章需要安装插件 [[1\]](https://xin520.xyz/wz/#fn:1)
头部信息(Front-matter)配置参考[[2\]](https://xin520.xyz/wz/#fn:2)