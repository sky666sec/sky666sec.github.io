---
title: 内网渗透之reDuh
date: 2018-01-28 14:19:58
tags:  
	- 渗透测试
categories:
	- 渗透测试
	
---



![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnwbl9mn08j30ic0hbmxk.jpg)

<!--more-->


###  reDuh原理介绍
`reDuh`最开始是由`SensePost`在`BlackHat USA 2008`会议上发表的一个议题中的一部分。它的出现是针对当前Web安全渗透测试经常会面临的一个问题，同时也是`Web`服务器加固方面一个很重要的部分， 那就是`Web`服务器对外只开放一个`80`端口。`Web`服务器的安全防护可以是操作系统的端口定制或者是网管防火前的端口定制。这时渗透测试人员如果想进一步 测试内网的话必须先拿下目标服务器并拥有一定的控制权限。`reDuh GUI`是由诺赛科技从原有的JAVA语言上移植到C++语言的一个`Windows GUI`版本，具有如下一些特性：

不需要`JAVA`运行环境 
可视化操作 
支持`HTTP/HTTPS `
支持二级代理 
以前渗透测试人员常用的一些方法是通过上传一些针对操作系统的可执行文件到目标服务器，并且必须要通过进程的方式执行该程序。这就存在两个问题：1、通过 渗透测试拿到的权限不一定允许执行进程；2、目标服务器的种类可能很多，比如`Windows、Linux、Solaris`等等，且对于库依赖性比较强，这 样就要求渗透测试人员必须维护一个不小的程序库以满足渗透测试的场景。
事实上，我们容易忽略的一点就是，其实脚本代码本身就支持`SOCKET`套接字的操作，它完全可以制作成为一个`SOCKET`中转代理（当然这也是有一定的限 制的，就比如在PHP中需要启用`SOCKET`模块）。那么这种代理是可以直接绕过防火墙进入到内网的。我们举个现实生活中比较常见的例子说明：`A`是一台` web`服务器，`B`是与`A`在同一内网一个文件服务器，由于工作需要及简化操作，`B`的文件访问是对内网公开的，也就是没有任何的认证要求。同时为了保证`B`服务 器的安全性，在网关防火墙上做了端口过滤：只允许外网访问`A`的`80`端口。这时我们如果想要从测试点访问`B`，传统的做法是控制`A`，上传执行文件，做一个程序 级的端口转发器。假设目标服务器根本就不允许从`web`上来的请求执行程序，换句话说是不允许执行进程，那么我们就没有办法拿到`B`的文件了吗？这里，我们就 可以想到`reDuh`了。



![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnwawsjj4vj30gy09taaj.jpg)


由图示上我们也可以看出，从`MSTSC`客户端到目标的`Terminal`服务器中间其实是走了一个这样的流程：
`Mstsc`客户端–>`reDuh`代理–>`HTTP tunne`–>`Web`服务器–>`Terminal`服务器
当然，对于`MSTSC`客户端而言，这些过程都是透明的，我们只需要在`MSTSC`中指定连接的端口为本地`reDuh`监听的端口即可。




### 首先我们上传reDuh脚本

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnwb20f3l3j30gt035mx1.jpg)


文件可以访问，继续下一步。


### 然后我们配置好代理端

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnwb4ym17nj30fn0bb0sq.jpg)

### 最后我们开始通过reDuh转发进内网


可以看到，成功转发。

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnwbakn8c8j30if0hagly.jpg)

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnwbl9mn08j30ic0hbmxk.jpg)


![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnwbmcfy97j30fl0b93yo.jpg)



### 总结：

- 还有很多姿势有待我们去挖掘

