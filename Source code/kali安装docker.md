---
title: kali安装docker
date: 2018-01-19 13:43:27
tags:  
	- kali linux
categories:
	- kali
	
---

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fnmq4jq021j30a905l0ta.jpg)

<!--more-->

### 安装步骤

#### 第一步

>apt-get update

>apt-get install -y apt-transport-https ca-certificates

>apt-get install dirmngr


#### 第二步

>apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 \
--recv-keys 58118E89F3A912897C070ADBF76221572C52609D

#### 第三步

>echo 'deb https://apt.dockerproject.org/repo debian-stretch main' > \
/etc/apt/sources.list.d/docker.list


#### 第四步

apt-get update
 
 
apt-get install docker-engine
 


</br>

**总结**

- 找个好教程比较关键

转载自：[https://www.cnblogs.com/DeeLMind/p/7816110.html](https://www.cnblogs.com/DeeLMind/p/7816110.html)

 demon团队的一位二进制大佬，我感觉教程简洁明了，步骤分明。