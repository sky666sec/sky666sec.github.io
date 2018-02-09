---
title: Kali2017搭建Node.js环境
date: 2017-12-15 17:55:07
tags:
	- kali linux
categories:
	- kali
	
---


近期由于要学习`JavaScript`所以想连带`Node.js`一起学了,开始发现`kali`的软件仓库里提供了`Node`，所以就使用`apt install nodejs` 来安装，装完以为OK了，结果用的时候发现是个坑……所以

<!--more-->

#### 官网下载适合自己系统的版本

`https://nodejs.org`


##### 解压:
>  `tar -zxJf `下载的`Node`文件

##### 移动:
> `mv` 解压后的文件夹     &nbsp;&nbsp; &nbsp;&nbsp;  路径 &nbsp;&nbsp; &nbsp;&nbsp;    //不是必须的，想放那个文件夹都行

#### 设置环境变量（重中之重）

> `ln -s` 上面解压后的文件夹所移动的路径`/bin/node /usr/local/bin/node`

> `ln -s` 上面解压后的文件夹所移动的路径`/usr/local/node-v8.4/bin/npm /usr/local/bin/npm`



##### 上述命令是创建软链接 

>`ln -s `安装软件的目录    ` /usr/local/bin/node `
    
>`ln -s `安装软件的目录 `/usr/local/bin/node`





#### 验证

> `node -v`

> `npm -v`
