---
title: Metasploit基础命令新手指南
date: 2017-12-16 11:02:33
tags: 
	- Metasploit
categories:
	- Metasploit

---

![](https://i.imgur.com/A1M02XZ.png)
<!--more-->

#### 基础命令概览：

back （返回）： 从目前的情况下向后移动
banner ：Display an awesome metasploit banner
cd： 改变当前的工作目录
color： 切换颜色
connect（远程连接）： 与主机通信

<!--more-->

edit （编辑）： 编辑与$ VISUAL或$ EDITOR当前模块的
exit （退出命令行）： 退出控制台
get （获取变量）： 获取特定上下文变量的值
getg （全局获取变量）： 获取一个全局变量的值
go_pro ： 启动Metasploit的网页图形用户界面


grep： grep的另一个命令的输出
help（帮助） ： 帮助菜单
info（获取模块信息）： 关于一个或多个模块显示信息
irb： 进入irb脚本模式
jobs：显示和管理职位
kill（结束进程）： 结束一个进程
load （加载）： 加载一个框架插件
loadpath ： 搜索和负载从一个路径模块
makerc： 保存自开始进入到一个文件中的命令
popm： 弹出最新的模块从堆栈中并使其活跃

previous ： 将以前加载模块作为当前模块
pushm ： 推主动或模块列表在模块栈
quit （退出控制台）： 退出控制台
reload_all Reloads ： 从所有定义的模块路径的所有模块
rename_job ： 重命名工作
resource ： 运行存储命令在文件
route ： 通过会话路由流量
save： 将数据存储主动
search（搜索exp等模块关键字）： 搜索模块的名称和说明
sessions（会话功能）： 转储会话列表和显示有关会话的信息

set （设置参数）： 设置一个特定的上下文变量的值
setg（全局设置参数）： 设置一个全局变量的值
show （展示参数模块）： 给定类型的显示模块或所有模块
sleep ： 什么都不做对的指定秒数
spool ： 写控制台输出到一个文件以及屏幕
threads ： 查看和操作后台线程
unload （卸载某个插件）： 卸载一个框架插件
unset （删除某个设置参数）： 取消设置一个或多个特定的上下文变量
unsetg （取消全局某个设置参数）： 取消设置一个或多个全局变量的
use （使用某个模块）： 选择按名称模块
version（查看版本信息）： 显示的框架和控制台库版本号



#### 命令作用详解：

##### back：
切换上下模块

一旦你已经完成了工作与一个特定的模块,或者如果你无意中选择了错误的模块,你可以“恢复”命令将当前上下文。

##### check：
检查exp是否有效，检查各项参数是否设置正确

##### connect：
通过发行“连接”命令有一个`ip`地址和端口号,你可以连接到一个远程主机从内部`msfconsole`一样你会`netcat`或`telnet`。



##### exit：
退出命令行



##### help：
列出命令和帮助信息


##### info：
info命令将提供关于一个特定模块的详细信息包括所有选项,目标,和其他信息。之前一定要总是读模块描述使用一些可能un-desired效果。



##### jobs：
（查看已后台运行的模块，如会话等。）

工作是在后台运行的模块。工作命令提供了列表和终止这些工作的能力。



##### kill：
`kill`命令将结束任何运行时工作提供的id

`msf exploit(ms08_067_netapi) > kill 0
Stopping job: 0…`

[*] `Server stopped`.



##### load：
从`Metasploit load`命令加载插件的插件目录。参数是作为关键= `val shell`传递。




#####  loadpath
`loadpath`命令将可以跳转到第三方模块加载树的路径你可以点`Metasploit` `0-day`利用、编码器、载荷等。


#####  unload：
卸载模块插件



#####  route：
`Metasploit`的“路线”命令允许您通过一个会话路由套接字或“通讯”,提供基本的旋转功能。添加一个路线,你通过目标子网和网络掩码会话(通讯)数量紧随其后。

 meterpreter > route


#####   search：
msfconsole包括一个广泛的基于正则表达式的搜索功能。如果你有一个总体的想法你正在寻找你可以通过“搜索”搜索。在下面的输出中,搜索是ms08-067。搜索功能将在模块定位这个字符串名称、描述、参考文献等。



##### help:
搜索关键字

##### name：
搜索名称

##### path：
搜索路径


##### type：
搜索模块类型


##### platform：
您可以使用“platform”来缩小你的搜索范围,影响特定平台的模块。



#### sessions
“会话”命令允许您列出,与交互,并杀死了会话。会话可以壳,`Meterpreter`会话,`VNC`,等等。

#### set:
“设置”命令允许您配置框架选项和参数为当前模块处理。



#### unset:
取消设置


#### setg:
全局变量设置


#### auxiliary
执行“显示辅助”将显示清单`Metasploit`内所有可用的辅助模块。如前所述,辅助模块包括扫描仪、拒绝服务模块,`fuzz`等等。


#### exploits
自然,“展示利用”将命令你最感兴趣的运行以来的核心,`Metasploit`就是剥削。展示利用的运行以获得一个清单中包含的所有功绩的框架。也可以用`run`命令来代替，功能是一样的。


####  payloads：展示所有有效的攻击载荷
正如您可以看到的,有很多可用的有效载荷。幸运的是,当你在一个特定的背景下开发,运行显示有效载荷的只会显示特定的载荷,兼容利用。例如,如果它是一个`Windows`开发,你将不会显示`Linux`载荷。


####  options：

是保证`metasploit`框架中的各个模块正确运行所需的各种设置





####  targets：


如果你不确定一个操作系统很容易受到特定的开发,运行显示目标的命令从一个开发模块的上下文中看到哪些目标是支持。




####   use:
当你已经决定在一个特定的模块使用,使用的命令以选中它。使用的命令改变你的环境到一个特定的模块,将特定类型的命令。注意在下面的输出任何以前的全局变量设置已经配置


 参考资料：[https://www.offensive-security.com/metasploit-unleashed/msfconsole-commands/](https://www.offensive-security.com/metasploit-unleashed/msfconsole-commands/)








