---
layout: kali
title: kali linux添加更新源
date: 2017-12-13 16:44:58
tags:
	- Kali Linux
categories: 
	- kali

---




推荐使用清华大学更新源，这个比较稳定。

<!--more-->

### 添加步骤

#### 首先找到所需要添加的源的地址。

##### 清华大学:
    deb http://mirrors.tuna.tsinghua.edu.cn/kali/  kali-rolling contrib main non-free

	deb-src http://mirrors.tuna.tsinghua.edu.cn/kali/  kali-rolling contrib main non-free

##### 阿里云:

    deb http://mirrors.aliyun.com/kali kali-rolling main non-free contrib

    deb-src http://mirrors.aliyun.com/kali kali-rolling main non-free contrib

##### 中科大:

    deb http://mirrors.ustc.edu.cn/kali kali-rolling main non-free contrib

    deb-src http://mirrors.ustc.edu.cn/kali kali-rolling main non-free contrib

##### 官方源:


    deb http://http.kali.org/kali kali-rolling main non-free contrib

    deb-src http://http.kali.org/kali kali-rolling main non-free contrib



#### 然后终端输入：`leafpad /etc/apt/sources.list`

打开后把上面的源加进去，然后保存。


#### 最后执行`apt-get update`

>`apt clean`  这个命令会把安装的软件的备份也删除，但是这样不会影响软件的使用。

> `apt autoclean `   定期运行这个命令来清除那些已卸载的软件包的.deb文档。通过这种方式，您能够释放大量的磁盘空间。

> `apt update `在修改`/etc/apt/sources.list`或`/etc/apt/preferences`之后运行该命令。此外您需要定期运行这一命令以确保您的软件包列表是最新的。

> `apt upgrade` 可以使用这条命令更新软件包，apt-get upgrade不仅可以从相同版本号的发布版中更新软件包，也可以从新版本号的发布版中更新软件包，尽管实现后一种更新的推荐命令为`apt-get dist-upgrade`。
>

> `apt dist-upgrade` 将系统升级到新版本。


> `apt-get autoremove`   删除为了满足其他软件包的依赖而安装的，但现在不再需要的软件包。









