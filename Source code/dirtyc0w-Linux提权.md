---
title: dirtyc0w_Linux提权
date: 2018-01-28 13:50:05
tags:
	- notes
categories:
	- notes
	
---


![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnwa6chcg4j30b40aawhp.jpg)
<!--more-->

### 漏洞编号：
    CVE-2016-5195

### 漏洞名称：
    Dirty COW

### 漏洞危害：
低权限用户利用该漏洞可以在众多`Linux`系统上实现本地提权

### 影响范围：
`Linux kernel >= 2.6.22`（`2007`年发行，到今年`10`月`18`日才修复）

### 漏洞概述：
该漏洞具体为，`Linux`内核的内存子系统在处理写入时复制`（copy-on-write, COW）`时产生了竞争条件`（race condition）`。恶意用户可利用此漏洞，来获取高权限，对只读内存映射进行写访问。`（A race condition was found in the way the Linux kernel’s memory subsystem handled the copy-on-write (COW) breakage of private read-only memory mappings.）`

竞争条件，指的是任务执行顺序异常，可导致应用崩溃，或令攻击者有机可乘，进一步执行其他代码。利用这一漏洞，攻击者可在其目标系统提升权限，甚至可能获得`root`权限。

根据官方发布的补丁信息，这个问题可以追溯到`2007`年发布的`Linux`内核。现在还没有任何证据表明，`2007`年后是否有黑客利用了这个漏洞。不过安全专家`Phil Oester`称发现一名攻击者利用该漏洞部署攻击，并向`Red Hat`通报了最近的攻击事件。

### 修复方法：
进行`Linux`内核维护的`Greg Kroah-Hartman`宣布针对`Linux 4.8、4.7`和`4.4 LTS`内核系列的维护更新（更新后为`Linux kernel 4.8.3、4.7.9`和`4.4.26 LTS`），修复了该漏洞。目前新版本已经登录各GNU/Linux发行版库，包括Arch Linux（测试中）、`Solus`和所有受支持版本的Ubuntu。Debian开发人员前天也宣布稳定版`Debian GNU/Linux 8 “Jessei”`系列内核重要更新——本次更新总共修复4个`Linux`内核安全漏洞，其中也包括了脏牛。

各操作系统供应商应该即刻下载`Linux kernel 4.8.3`、`Linux kernel 4.7.9`和`Linux kernel 4.4.26 LTS`，为用户提供稳定版渠道更新。

软件开发人员可以通过` https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=19be0eaffa3ac7d8eb6784ad9bdbc7d67ed8e619` 重新编译`Linux`修复此漏洞。



### EXP

[http://ys-k.ys168.com/575740248/l6J277L3I4JLH7TjsKkJ/dirty.zip](http://ys-k.ys168.com/575740248/l6J277L3I4JLH7TjsKkJ/dirty.zip "dirty.zip")

#### 内核版本

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnwacrpkjvj30dj02c0sh.jpg)


#### 编译
`
gcc -pthread dirty.c -o dirty -lcrypt`


#### 运行

     chmod 777 dirty

    ./dirty yourpassword


原来的权限：

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnwah1584hj30de04pq2p.jpg)

用脏牛提权后的权限：

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnwahpjw44j30i006u745.jpg)


`uid = 0 root `权限


如果是在反弹的 `shell` 里执行 直接连接 `ssh`

别忘了恢复原来的` passwd` 文件


![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnwam12maoj30d2032we9.jpg)



### 总结：

- 学会了脏牛漏洞提权linux的方法





