---
title: AliYunDun bypass
date: 2018-06-04 13:26:46
tags: notes
categories: notes

---






![](https://raw.githubusercontent.com/sky666sec/sky666sec.github.io/hexo/Figure%20Bed/TIM%E6%88%AA%E5%9B%BE20180604123700.png)



用阿里云的主机扫描阿里云的站点是不会封IP的。

<!--more-->

随着越来越多的站点采用阿里云服务器，阿里云自带的云盾waf总是封ip就很讨厌了。



所以就想出了这招以其人之道还治其人之身的手法。



昨天我参考了xz的这篇文章

https://exp10it.cn/2018/04/21/aliyun-waf-bypass.html

发现用阿里云的主机跑阿里云站点的注入，云盾确实是不封ip的。



于是我今天就想到如果我用扫描的方式,云盾它是不是也是不封ip的？



![](https://raw.githubusercontent.com/sky666sec/sky666sec.github.io/hexo/Figure%20Bed/TIM%E5%9B%BE%E7%89%8720180604124809.png)

 





![](https://github.com/sky666sec/sky666sec.github.io/blob/hexo/Figure%20Bed/TIM%E6%88%AA%E5%9B%BE20180604125241.png?raw=true)



先用自己本机进行扫描测试，过了一会，果然封ip了。

![](https://github.com/sky666sec/sky666sec.github.io/blob/hexo/Figure%20Bed/TIM%E6%88%AA%E5%9B%BE20180604125446.png?raw=true)



![](https://github.com/sky666sec/sky666sec.github.io/blob/hexo/Figure%20Bed/TIM%E6%88%AA%E5%9B%BE20180604125656.png?raw=true)







于是用我的阿里云服务器再进行测试

![](https://github.com/sky666sec/sky666sec.github.io/blob/hexo/Figure%20Bed/TIM%E6%88%AA%E5%9B%BE20180604130920.png?raw=true)

不放我的ip，怕被日。（嘻嘻）



![](https://github.com/sky666sec/sky666sec.github.io/blob/hexo/Figure%20Bed/TIM%E6%88%AA%E5%9B%BE20180604123700.png?raw=true)



哈哈哈，扫完了，云盾根本不封ip的。

嫌麻烦，可以用阿里云的代理也行。



总结：
1、阿里云云盾的这个ip封禁策略就跟内外网一样，内网统统信任，外网就统一进行拦截，因为阿里云本身就是一个大的内网，所以这是没办法的事情。
2、学无止境，努力拼搏。

