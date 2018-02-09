---
title: subprocess模块+去除启动的黑色cmd窗口
date: 2018-02-08 20:02:42
tags: python
categories: python

---


![](https://ws1.sinaimg.cn/large/006Y6f53gy1fo9d9sak0tj30lp05yaa1.jpg)

<!--more-->

### 前言

今天xz跟我说了`subprocess`模块，正好我晚上就用了`subprocess`模块。

我们能从`Python`官方文档里读到应该用`subprocess` 模块来运行系统命令`.subprocess`模块允许我们创建子进程,连接他们的输入/输出/错误管道，还有获得返回值。
`subprocess`模块打算来替代几个过时的模块和函数，比如： `os.system`,` os.spawn*`, `os.popen*`, `popen2.*`命令。
让我们来看一下`subprocess `有哪些不同的函数.

### subprocess.call()

执行由参数提供的命令.
我们可以用数组作为参数运行命令,也可以用字符串作为参数运行命令(通过设置参数`shell=True`)
注意,参数`shell`默认为`False`
我们用`subprocess.call()`来做一个统计磁盘的例子:


> subprocess.call(['df', '-h'])



下面的例子把`shell`设置为`True`

> subprocess.call('du -hs $HOME', shell=True)



注意`python`官方文档里对参数`shell=True`陈述了一个警告:

> Invoking the system shell with shell=True can be a security hazard if combined
with untrusted input


#### Input and Output

`subprocess` 模块能阻止输出,当你不关心标准输出的时候是非常方便的.
它也使你通过一种正确的方式管理输入/输出,有条理地整合`python`脚本中的的`shell`命令.

#### Return Codes

通过`subprocess.call`的返回值你能够判定命令是否执行成功.
每一个进程退出时都会返回一个状态码，你可以根据这个状态码写一些代码。

#### stdin, stdout and stderr

我在使用`subprocess` 时,有一个微妙的部分是怎么使用管道把命令连接起来.
管道表明一个新的子管道应该被创建.
默认的设置为`None,`意味着没有重定向发生
标准错误可以指向标准输出,表明子进程的错误信息会被捕获到和标准输出同一个文件.



### subprocess.Popen()


`subprocess `模块中基本的进程创建和管理由Popen 类来处理.
`subprocess.popen`是用来替代`os.popen`的.
我们来做一些真实的例子,`subprocess.Popen`需要一个数组作为参数:

> import subprocess

>p = subprocess.Popen(["echo", "hello world"], stdout=subprocess.PIPE)

>print p.communicate()

>  &nbsp;>>>('hello world
', None)



注意,虽然你可以使用 "`shell=True`",但并不推荐这样的方式.
如果你知道你只用几个有限的函数,比如`Popen`和`PIPE`,你可以单单指定这几个函数:

> from subprocess import Popen, PIPE

> p1 = Popen(["dmesg"], stdout=PIPE)

> print p1.communicate()


#### Popen.communicate()

`communicate()`函数返回一个`tuple`(标准输出和错误).
`Popen.communicate()` 和进程沟通:发送数据到标准输入.从标准输出和错误读取数据直到遇到结束符.等待进程结束.
输入参数应该是一个字符串,以传递给子进程,如果没有数据的话应该是`None`.
基本上,当你用` communicate()函`数的时候意味着你要执行命令了.



### 用subprocess写Ping程序

我们先问用户地址,然后用`ping`请求这个地址.



> &nbsp;# Import the module

> &nbsp;import subprocess

> &nbsp;# Ask the user for input
> 
host = raw_input("Enter a host to ping: ")    

> &nbsp;# Set up the echo command and direct the output to a pipe


> &nbsp;p1 = subprocess.Popen(['ping', '-c 2', host], stdout=subprocess.PIPE)


> &nbsp;# Run the command


> output = p1.communicate()[0]

> print output



### 去除启动的黑色cmd窗口

开始我用的`o`s模块的`os.system（）`，但是发现有一个`bug`。 
就是启动之后会有黑色的`cmd`窗口这个`bug`，这个不是我们想要的。

![](https://ws1.sinaimg.cn/large/006Y6f53ly1fo9d27zmykj30rl0ef3z2.jpg)


于是我查了查资料，看到了这个。
![](https://ws1.sinaimg.cn/large/006Y6f53gy1fo9d6x8ebpj30r406oaaf.jpg)


原来我们可以使用`subprocess`模块的`subprocess.Popen()`来解决这个`bug`。

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fo9d9sak0tj30lp05yaa1.jpg)


这下启动之后出现的黑色`cmd`窗口没有了，也达到我们的效果。

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fo9dc29cubj30dl094jrq.jpg)


### 总结

- 了解了`subproess`模块

- 学会了用`subproess``模块的subpross.Popen()`解决启动的黑色`cmd`窗口。















