---
title: Python系统命令调用
date: 2018-02-08 21:28:00
tags: python
categories: python

---


![](https://ws1.sinaimg.cn/large/006Y6f53gy1fo9eb6x7uyj31240o0jsi.jpg)

<!--more-->
### 前言

`Python 3`不再推荐使用老的`os.system()`、`os.popen()`、`commands.getstatusoutput()`等方法来调用系统命令，而建议统一使用`subprocess`库所对应的方法如：`Popen()`、`getstatusoutput()`、`call()`。


推荐并记录一些常用的使用范例：


### Popen


> import subprocess


> try:


> &nbsp;&nbsp;&nbsp;&nbsp; proc = subprocess.Popen([`ls`, `-a`, `/`], stdout=subprocess.PIPE)


> &nbsp;&nbsp;&nbsp;&nbsp; print(proc.stdout.read())  
    
> except:

> &nbsp;&nbsp;&nbsp;&nbsp; print("error when run `ls` command")



### call

> import subprocess

>try:

>&nbsp;&nbsp;&nbsp;&nbsp; retcode = subprocess.call("mycmd" + " myarg", shell=True)
>&nbsp;&nbsp;&nbsp;&nbsp; if retcode < 0:

>&nbsp;&nbsp;&nbsp;&nbsp; print("Child was terminated by signal", -retcode, file=sys.stderr)

>&nbsp;&nbsp;&nbsp;&nbsp;  else:

>&nbsp;&nbsp;&nbsp;&nbsp;        print("Child returned", retcode, file=sys.stderr)

> except OSError as e:

>&nbsp;&nbsp;&nbsp;&nbsp;    print("Execution failed:", e, file=sys.stderr)

### getstatusoutput/getoutput

>&nbsp;  >>> subprocess.getstatusoutput('ls /bin/ls')

> (0, '/bin/ls')

>&nbsp;>>> subprocess.getoutput('ls /bin/ls')

> '/bin/ls'



详细可以查阅`Python 3`官方文档：

- os: [https://docs.python.org/3/library/os.html](https://docs.python.org/3/library/os.html)

- subprocess: [https://docs.python.org/3/library/subprocess.html](https://docs.python.org/3/library/subprocess.html)