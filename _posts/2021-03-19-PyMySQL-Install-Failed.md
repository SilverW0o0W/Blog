---
layout:     post
title:      pip安装cryptography失败导致pymysql无法安装问题
author: Silver
categories: Python
---


# 问题描述
春节回来之后，QA发现了有一些Docker服务自动部署失败

发现pymysql在安装cryptography的时候会发生错误，报错如下图所示
{% highlight ruby %}
ModuleNotFoundError: No module named 'setuptools_rust'
{% endhighlight %}

![0](/resource/2021-03-19-PyMySQL-Install-Failed/0.png)  

# 问题处理过程
这个错误有一个很关键的问题：
只有部分的服务会出现这种情况，而且均在pymysql==0.9.2的环境上发生，使用0.8.0版本的老服务始终没出现过问题

由于我本机使用的virtualenv没有根据服务区分开，所以本地没有重现这个问题。不过既然定位到了问题出现在pymysql的不同版本上，就从pymysql查起。

我分别下载了0.8.0和0.9.2的两份pymysql，查看它们的setup.py文件，发现0.8.0版本没有cryptography的依赖,而0.9.2版本中发现了下图中的代码
![1](/resource/2021-03-19-PyMySQL-Install-Failed/1.png)  

很明显，pymysql==0.9.2依赖的cryptography库并没有指定版本，如果cryptography本身有问题，就会导致pymysql安装失败  
而现在遇到的问题就是，在cryptography的某次升级之后，不再支持我们当前Docker中pip版本直接安装，而最简单的解决方案就是升级pip

# 问题解决方案
将当前的pip版本升级
`pip install --upgrade pip`

# 问题总结
这问题其中一个原因是我们Dockerfile搭建的环境不完善，没有实时更新pip。
另外我们Dockerfile安装服务的requirements.txt时没有使用--no-cache参数，Docker存在缓存，导致两个服务就算是同样的依赖文件，一个有问题而另一个却能够正常部署，增加了定位问题的难度。

另一个罪魁祸首就是pymysql了，setup.py文件中不指定依赖库的版本，导致本应该稳定的依赖库发生了无法正常安装的情况，在生产环境下实在比较危险。