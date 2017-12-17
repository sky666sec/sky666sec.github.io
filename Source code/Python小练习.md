---
title: Python小练习
date: 2017-12-16 22:50:41
tags:
	- Python
categories:
	- Python

---




### Python raw_input() 函数
#### Python 内置函数 



<!--more-->

`python raw_input()` 用来获取控制台的输入。

`raw_input() `将所有输入作为字符串看待，返回字符串类型。



>  注意：`input()` 和 `raw_input() `这两个函数均能接收 字符串 ，但` raw_input()` 直接读取控制台的输入（任何类型的输入它都可以接收）。而对于` input()` ，它希望能够读取一个合法的 `python` 表达式，即你输入字符串的时候必须使用引号将它括起来，否则它会引发一个 `SyntaxError` 。

> 除非对 `input()` 有特别需要，否则一般情况下我们都是推荐使用 `raw_input() `来与用户交互。

> 注意：`python3 `里 `input() `默认接收到的是` str` 类型。



#### 函数语法
    raw_input([prompt])

#### 练习源码

    #!/usr/bin/env python
	#-*-coding:utf-8-*-`
    print "by sky666"
    Nickname = str(raw_input("Enter your Nickename:"))
    print (Nickname)
    


上述源码的意思是通过raw_input函数从键盘上获取你输入的呢称，然后用print函数给打印出来。


### 总结：
- 在此练习中，我犯了由于把从键盘输入的呢称变量给打印出来时的变量名称写错，导致出错，因为那个变量并没有定义，所以肯定打印不出来，从而导致报错。
- <font color=red>**细节很重要！细节很重要！细节很重要！**</font>
