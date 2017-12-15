---
title: kali安装GDebi程序包管理器
date: 2017-12-14 12:06:39
tags:
	- kali linux
categories:
	- kali

---

`dpkg`是一个功能强大的工具，但它并不自动安装依赖项。为此，我们需要某种程序包安装工具，以便在安装`.deb`程序包的同时，可以去获取所有必要的依赖项。眼下最出色的程序包安装工具非`gdebi`莫属。

<!--more-->

使用的命令来安装它：

    apt-get update -y

	apt-get install gdebi -y 

