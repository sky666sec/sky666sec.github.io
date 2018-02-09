---
title: Hardentools
date: 2018-02-08 13:25:29
tags: tools
categories: tools

---


![](https://ws1.sinaimg.cn/large/006Y6f53gy1fo8zc77g9pj30h40fq0tf.jpg)
<!--more-->

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fo8zcleuusj303k03k0sl.jpg)


### 前言

由于本人现在主要用Windows,又比较注重安全性，有一次跟`demon`讨论如何对`Windows`系统进行安全加固，他说最好禁用`Powershell`和`.net`。那天正好看见他分享了这个工具，可以一键禁用`Powershell` 。

### Hardentools

`Hardentools`是一个简单的实用程序，旨在禁用操作系统（`Microsoft Windows`）以及主要应用程序公开的许多“功能”。这些通常为企业客户所设想的功能，对于普通用户来说通常是无用的，而且由于攻击者非常普遍地滥用其在受害者的计算机上执行恶意代码而构成危险。这个工具的目的是通过禁这些无用的功能来减少攻击面。`Hardentools`适用于有风险的个人，他们可能希望以某种可用性为代价获得额外的安全级别。它不适用于企业环境。

> 警告：这只是一个实验，它并不意味着公开使用。此外，此工具会禁用许多功能，包括`Microsoft Office`，`Adobe Reader`和`Windows`，这些功能可能会导致某些应用程序出现故障。使用这个需要您自担风险。


请记住，在运行`Hardentools`之后，例如，您将无法使用`Microsoft Office Excel`或使用命令行终端进行复杂的计算，但这些几乎是唯一具有稍微更安全的`Windows`的“缺点”环境。



`github`项目地址：
https://github.com/securitywithoutborders/hardentools

### 如何使用它

一旦你双击图标，根据你的`Windows`安全设置，你应该被提示用户访问控制对话框，要求你确认以允许`Hardentools`运行。点击“是”。

![](https://ws1.sinaimg.cn/large/006Y6f53gy1fo8zgimtbej30de07wjrm.jpg)

然后，你会看到主要的`Hardentools`窗口。这很简单，只需点击“强化”按钮，该工具将对`Windows`配置进行更改，以禁用一组有风险的功能。一旦完成，您将被要求重新启动您的计算机进行所有更改才能生效。


![](https://ws1.sinaimg.cn/large/006Y6f53gy1fo8zhf8ysdj30h40fq0tf.jpg)


如果您希望恢复原始设置并还原`Hardentools`所做的更改（例如，如果您需要使用`cmd.exe`），则可以简单地重新运行该工具，系统会提示您一个“恢复”按钮。同样，单击它并等待修改被还原。

请注意：由`Hardentools`所做的修改仅仅是用于运行该工具的`Windows`用户帐户的上下文。如果你想`Hardentools`也改变其他`Windows`用户的设置，你将不得不从其中每一个登录运行它。


### 这个工具不是什么
- 它不会阻止软件被利用。
- 它不能防止滥用每一个可用的危险功能。
- 这不是一个杀毒软件。它不保护你的电脑。它不识别，阻止或删除任何恶意软件。
- 它不会阻止它实现的变化被还原。如果恶意代码在系统上运行，并且能够恢复它们，工具的效果就失效了，不是吗？

### 禁用的功能

#### 通用Windows功能
- 禁用`Windows`脚本主机。`Windows Script Host`允许在`Windows`操作系统上执行`VBScript`和`Javascript`文件。这是常见的恶意软件（如勒索软件）以及有针对性的恶意软件常用的。

- 禁用自动运行和自动播放。禁用所有设备的自动运行/自动播放。例如，这可以防止应用程序在将`USB`设备插入计算机时自动执行。

- 通过`Windows`资源管理器禁用`powershell.exe`，`powershell_ise.exe`和`cmd.exe`执行。您将无法使用该终端，并且应该阻止恶意代码尝试感染系统来使用`PowerShell`。

- 将用户帐户控制（`UAC`）设置为始终要求许可（即使只是更改配置）并使用“安全桌面”。

- 禁用主要用于恶意目的的文件扩展名。禁用`.hta`，`.js`，`.JSE`，`.WSH`，`.WSF`，`.scf`，`.scr`，`.vbs`，`.vbe`，`.pif` “当前用户的文件扩展名（以及系统范围的默认设置，只对新创建的用户有用）。


#### 微软办公软件

- 禁用宏。有时，`Microsoft Office`用户使用宏来脚本化和自动化某些活动，特别是使用`Microsoft Excel`进行的计算。然而，宏目前是安全瘟疫，并被广泛用作妥协的工具。使用`Hardentools`，宏被禁用，并且“启用此内容”通知也被禁用，以防止用户被欺骗。

- 禁用`OLE`对象执行。`Microsoft Office`应用程序能够嵌入所谓的“`OLE`对象”并执行它们，有时也会自动（例如通过PowerPoint动画）。也可以将`Windows`可执行文件（如间谍软件）作为对象进行嵌入和执行。这也是我们一次又一次地观察到的安全灾难，特别是在对被压迫地区的激进分子的袭击中。`Hardentools`完全禁用了这个功能。

- 禁用`ActiveX`。禁用所有`Office`应用程序的`ActiveX`控件。

- 禁用`DDE`。为`Word`和`Excel`禁用`DDE`。


#### 爱看阅读器

- 在`PDF`文档中禁用`JavaScript`。`Acrobat Reader`允许从`PDF`文档执行`JavaScript`代码。这被广泛滥用于利用和恶意活动。

禁止执行嵌入在`PDF`文档中的对象。`Acrobat Reade`r也允许通过打开它们来执行嵌入的对象。这通常会引发安全警报，但鉴于这种合法使用是罕见且有限的，`Hardentools`禁用此功能。

- 打开保护模式（在当前版本中默认启用）

- 打开受保护的视图，查看来自不受信任来源的所有文件

- 打开增强安全性（在当前版本中默认启用）


### 作者


这个工具由`Claudio Guarnieri`，`Mariano Graziano`和`Florian Probst`开发。


参考：[https://github.com/securitywithoutborders/hardentools](https://github.com/securitywithoutborders/hardentools)




