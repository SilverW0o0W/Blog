---
layout:     post
title:      ShadowSocks环境搭建
categories: Blog
---

#### 安装setuptools  
* `yum install wget -y`  
* `wget "https://pypi.python.org/packages/source/s/setuptools/setuptools-2.0.tar.gz"`
* `tar zxvf setuptools-2.0.tar.gz`
* `cd setuptools-2.0`
* `python setup.py install`

#### 安装pip
* `wget "https://pypi.python.org/packages/11/b6/abcb525026a4be042b486df43905d6893fb04f05aac21c32c638e939e447/pip-9.0.1.tar.gz#md5=35f01da33009719497f01a4ba69d63c9"`
* `tar -xzvf pip-9.0.1.tar.gz`
* `cd pip-9.0.1`
* `python setup.py install`

#### 安装ShadowSocks
* `pip install shadowsocks`