---
title: 通过HTTP头伪造IP
date: 2018-03-10 18:27:05
tags: notes
categories: notes

---

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fp7xjdrzebj30b405kt8m.jpg)

<!--more-->



以前做CTF看到过这种姿势，刚好又在xz博客看到了；就转载过记录一下。（其实是老发些没技术含量的没意思,23333）


在`CTF`比赛中会遇到一种题目，例如你的`IP`是来自德国的才可以拿到`flag`。所以，我们的思路就是进行数据包头欺骗，伪造我们的`IP`，骗过服务器。下面来说说伪造IP的几种方式。


> X-Originating-IP: 8.8.8.8

> X-Forwarded-For: 8.8.8.8


> X-Real-IP: 8.8.8.8

> X-Remote-IP: 8.8.8.8

> X-Remote-Addr: 8.8.8.8



大多都跟反向代理有关

`X-Originating-IP` 主要出现在邮件头里

`X-Forwarded-For` 不多说 代理转发的 `IP`

`X-Real-IP` 跟 `X-Forwarded-For` 类似

`X-Remote-IP` 和 `X-Remote-Addr` 远程主机的 `IP`

因为都是从脚本层获取的 所以可以进行伪造

`Modify Header Value` 插件




![](https://ws1.sinaimg.cn/large/006Y6f53gy1fp7xjutdhaj314t08dmxz.jpg)

`PHP $_SERVER` 变量输出

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fp7xkntsg9j3088037mx7.jpg)




转载自：[https://exp10it.cn/index.php/archives/1056](https://exp10it.cn/index.php/archives/1056 "xz")