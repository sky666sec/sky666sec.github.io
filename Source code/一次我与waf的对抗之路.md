---
title: 一次我与waf的对抗之路
date: 2018-01-12 12:42:24
tags:
	- 渗透测试
categories:
	- 渗透测试

---

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fnlv0afpidj311y0gzn10.jpg)

<!--more-->

这个站比较特别，主站和旁站都在一台服务器上，所以`waf`对主站和旁站都有作用。另外提示这是安全狗。

以后看到这个可以知道一般都是安全狗。

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fnlv0x907hj306n00la9v.jpg)

接下来就是我与`waf`的对抗之路

我开始是写进去了

![](https://i.imgur.com/qtGCF1v.png)![](https://ws1.sinaimg.cn/large/006Y6f53gy1fnlv1nb1q5j30sb01i0so.jpg)
不过这死狗他过一会就把我给杀了，好气！  

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fnlv24yji8j30sn0eaq60.jpg)

换了各种免杀马都不行，我猜他的判断规则是发现有写入文件的行为，就立马删除这个文件
。因为连`txt`文件都杀了。
不过慢慢我发现他有个`bug`，那就是时间延迟，他不是立即杀，而是过一会才杀。那么我就有个思路了。

<font color=red>既然你过一会才杀我的，那我就不断写入小马，然后在写入小马的同时又赶紧用写入的小马上传大马。利用你这个查杀判断规则具有时间延迟的`bug`进行绕过。通俗的讲就是你杀我就新建，你刚杀完我的我又新建了一个新的同样的文件，让你反应不过来。</font>

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fnlv2yk9lfj30qe07675k.jpg)

最后思路是对的，成功拿到`webshell`。

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fnlv0afpidj311y0gzn10.jpg)



</br>
**总结：**

- 学会去发现`waf`的判断规则及`bug`,利用`waf`的判断规则及`bug`进行绕过。

