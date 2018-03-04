---
title: PHPWEB重装漏洞+%00截断拿webshell
date: 2018-03-04 13:02:19
tags: 渗透测试
categories: 渗透测试

---

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fp0qgdv9rrj310q0h7t9r.jpg)

<!--more-->

首先我们看到需要数据库服务器地址

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fp0pct202uj31180i9js4.jpg)




那么我们就自己搭建一台数据库服务器。



![](https://ws1.sinaimg.cn/large/006Y6f53gy1fp0pe0y0lvj311y0kg3ze.jpg)


继续下一步

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fp0pfmxr5cj311b0ie40v.jpg)

接下来我们可以重置后台管理员密码

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fp0pgsaengj310s0i0mxs.jpg)

重置管理员密码成功

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fp0phw1i3wj311d0i6mxr.jpg)

正如安装完成的提示所说，请删除【install】目录（可是大部分安全意识不强的站长并没有删除，啪啪啪，打脸了）。



成功进入后台管理系统

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fp0pjyv5kwj311g0i6gsy.jpg)



`phpweb ``cms` 添加文章上传存在经典的%00截断漏洞。




截断的产生核心，就是`chr(0)`字符 。

这个字符即不为空`(Null)`，也不是空字符`("")`，更不是空格！

当程序在输出含有`chr(0)`变量时，`chr(0)`后面的数据会被停止，换句话说，就是误把它当成结束符，后面的数据直接忽略，这就导致漏洞产生的原因。

在`php 5.3.4`中修复了`0`字符，但是在之前的版本中仍然危害巨大。

简单测试一下 (`PHP` 版本`<5.3.4`)

> <?php

> $data = $_GET["filename"]`;

> echo $data;

>?>

`url`中输入`xx.php?filename=test.php%00.txt`，实际输出为`test.php`.



常见利用方法：



- 1.上传时路径可控，使用00截断
- 2.文件下载时，00截断绕过白名单检查
- 3.文件包含时，00截断后面限制(主要是本地包含时)
- 4.其它与文件操作有关的地方都可能使用00截断


下面请看实例

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fp0qcv8ydsj30a603jq2w.jpg)


成功拿到webshell

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fp0qgdv9rrj310q0h7t9r.jpg)


总结： 

> 正如安装完成的提示所说，请删除【install】目录。

> 及时升级php版本以便修复缺陷。

