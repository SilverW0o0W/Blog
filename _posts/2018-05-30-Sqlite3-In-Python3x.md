---
layout:     post
title:      Python 3.x 版本中sqlite3错误
author: Silver
categories: Python
---

Linux系统下Python 3调用sqlite模块会以下错误

```text
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/lib/python3.6/sqlite3/__init__.py", line 23, in <module>
    from sqlite3.dbapi2 import *
  File "/usr/local/lib/python3.6/sqlite3/dbapi2.py", line 27, in <module>
    from _sqlite3 import *

ModuleNotFoundError: No module named '_sqlite3'
```

由于Python 3.x不再支持 pysqlite，所以pysqlite替代的方案也无法使用。

#### 解决方案:

* `yum -y install sqlite-devel`
* 重新编译安装Python 3，路径不变，过程不再赘述

#### 参考链接：

* [no-module-named-sqlite3][1]
* [ubuntu环境下 python 3.0以上版本对sqlite3的支持问题][2]


[1]: https://stackoverflow.com/questions/1210664
[2]: https://blog.csdn.net/sparkexpert/article/details/69944835