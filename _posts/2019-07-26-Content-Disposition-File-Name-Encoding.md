---
layout:     post
title:      Python3 支持下载文件名中文编码
author: Silver
categories: Python
---


# Content-Disposition

写下载歌词接口的时候遇到了一个问题，`中文.lrc`的文件下载之后的文件名的编码始终有问题，找了很久也没解决
过程暂且不表
最后靠自己解决了问题(靠!)

{% highlight ruby %}
from urllib import parse
    self.set_header('Content-Type', 'application/octet-stream;')
    self.set_header('Content-Disposition', "attachment; filename*=UTF-8''{}".format(parse.quote(file_name)))
{% endhighlight %}
