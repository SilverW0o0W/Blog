---
layout:     post
title:      Bing每日美图API
author: Silver
categories: Python
---

最近研究了一下Bing搜索的每日图片，感觉暂时没空弄这个玩意，先把API放出来好了...

* 国内版: `https://cn.bing.com/HPImageArchive.aspx?format=js&n=20&nc=1528453352419&pid=hp`
* 国际版: `https://cn.bing.com/HPImageArchive.aspx?format=js&n=20&nc=1528453352419&pid=hp&FORM=BEHPTB`

#### 参数

* `format`: js return JSON, default return XML
* `n`: return image count (max = 8 for now)
* `nc`: timestamp
