---
title: Python代码扫盲
date: 2017-12-16 16:36:08
tags:
	- Python
categories:
	- Python

---


人生苦短，我用Python。

<!--more-->

### Python头部标注

#### #!/usr/bin/env python
为了防止操作系统用户没有将`python`装在默认的`/usr/bin`路径里。当系统看到这一行的时候，首先会到`env`设置里查找`python`的安装路径，再调用对应路径下的解释器程序完成操作。

#### #!/usr/bin/ python
告诉操作系统执行这个脚本的时候，调用`/usr/bin下`的`python`解释器

### 编码
用来指定文件编码为`utf-8`


#### `coding=utf-8 `

#### `coding:utf-8`

#### `--coding:utf-8--`
 
#### ` -*-coding:utf-8 -*-`

### 总结

1. `#!/usr/bin/ python`相当于写死了`python`路径
1. `#!/usr/bin/env python`会去环境设置寻找`python`目录,推荐这种写法。
1. 推荐使用`# -*-coding:utf-8 -*-`



