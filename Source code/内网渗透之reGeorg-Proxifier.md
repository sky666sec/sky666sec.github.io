---
title: 内网渗透之reGeorg+Proxifier
date: 2017-12-16 19:58:21
tags:  
	- 渗透测试
categories:
	- 渗透测试

---

相信很多人还在使用`lcx`进行转发，并不是说技术新旧问题。而是很多时候如果服务器有杀毒.难道每次都要免杀？
你能确定服务器每次都是你能绕过的杀软吗？所以利用新的手法是趋势了。

<!--more-->

之前遇到一台装有赛门铁克的服务器就是这样，用`lcx`转发不了，问了朋友，才知道还有这种手法。

`reGeorg`是`reDuh`的继承者，利用了会话层的`socks5`协议，效率更高结合`Proxifier`使用 `Proxifier`是一款功能非常强大的`socks5`客户端，可以让不支持通过代理服务器工作的网络程序能通过`HTTPS`或`SOCKS`代理或代理链。 该文件下支持`php`，`asp`，`aspx`，`jsp`。

`reGeorg`项目下载地址：[https://github.com/sensepost/reGeorg](https://github.com/sensepost/reGeorg)


![](https://i.imgur.com/PIQj7Hn.png)

首先我们需要将脚本上传到服务器端，这里是`jsp`服务器，所以我们上传`tunnel.tomcat.5.jsp`，访问显示“`Georg says, 'All seems fine`'”，表示脚本运行正常

![](https://i.imgur.com/IUFawry.png)


运行`reGeorg`监听`6666`端口，可以看到正常运行 。

`reGeorgSocksProxy.py -p 6666 -u http://xxx.xxx.xxx/tunnel.tomcat.5.jsp`

![](https://i.imgur.com/Z8g73BR.png)


下面我们配置`Proxifier`，运行`Proxifier`之后设置代理

![](https://i.imgur.com/Q2yQSKO.png)

设置代理服务器为`6666`

![](https://i.imgur.com/nmXRI2q.png)


代理规则默认即可


![](https://i.imgur.com/buRmYMM.png)



右击“`mstsc.exe`”，选择“`proxifier`”-》`proxy socks5 127.0.0.1`进行远程连接

![](https://i.imgur.com/ujDqYrt.png)


输入内网ip：`192.168.50.2`

![](https://i.imgur.com/gDDpFno.png)


登陆成功，成功转发进入内网

![](https://i.imgur.com/gFeHJLI.png)


**总结：**

- 此手法无是否外网IP条件限制，因为是socket代理，所以更稳定，流量通过web端口转发，就像管理员自己用自己服务器登陆一样，所以更安全。
