---
title: Hexo常见问题
date: 2017-12-12 19:59:21
tags:
	- notes
categories: 
	- notes
	
---

![](https://github.com/sky666sec/sky666sec.github.io/blob/hexo/Figure%20Bed/006Y6f53gy1fnlugpttewj30tl0gn0ts.jpg?raw=true)

<!--more-->


> 
1、先hexo g再执行hexo d布署，也可直接用hexo d -g。




<!--more-->




>  
2、hexo 更新到3.0之后，deploy的type 的github需要改成git 。

<!--more-->
>  
3、在执行 hexo deploy 后，出现 <font color=red>error deployer not found:git</font> 的错误处理。

输入代码：

    npm install hexo-deployer-git --save