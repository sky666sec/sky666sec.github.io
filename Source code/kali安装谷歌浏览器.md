---
title: Kali Linux 安装google-chrome浏览器
date: 2017-12-14 10:17:53
tags:
	- Kali Linux
categories: 
	- kali

---


#### 步骤说明

----------

##### 下载 Google Chrome

首先，使用` wget `命令来下载最新版本的 `Google Chrome` 的 `debian` 安装包。


    wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

<!--more-->

##### 安装 Google Chrome
在 `Kali Linux `安装 `Google Chrome `最容易的方法就是使用 `gdebi`，它会自动帮你下载所有的依赖包。


    apt-get install gdebi

使用 `gdebi` 命令来安装` Google Chrome `的` debian `包可以解决依赖问题。

    gdebi google-chrome-stable_current_amd64.deb -y

打开`/usr/share/applications`目录，找到`Google Chrome` 图标，右键打开属性在命令那栏加上 `%U --no-sandbox --user-data-dir `，注意%U前面要加一个空格。

##### 启动 Google Chrome

在应用程序里面找到`Google Chrome`，就可以直接双击打开`Google Chrome`。