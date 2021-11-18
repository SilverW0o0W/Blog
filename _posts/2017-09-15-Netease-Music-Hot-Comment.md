---
layout:     post
title:      获取网易云音乐精彩评论API
author: Silver
categories: Python
---

## 这篇文章需要爬取对网易云音乐评论API有一定了解。

通常，我们处理过请求需要的参数之后，需要将Request发送到 `http://music.163.com/weapi/v1/resource/comments/R_SO_4_(id)/?csrf_token=` 来获取评论。  
在返回的JSON里面会含有普通评论和精彩评论。  
![0](/resource/2017-09-15-Netease-Music-Hot-Comment/0.png)

但是，实际上这个API的效果只是网页版的网易云音乐而已。当Request中的参数 `offset` 和 `limit` 是默认值的时候，获取到的数据实际是网页版网易云音乐的JSON罢了。  
![1](/resource/2017-09-15-Netease-Music-Hot-Comment/1.png)

当Request中配置了`offset` 和 `limit` 获取第2页评论的时候就会发现，JSON不会再返回精彩评论，这和网页版网易云音乐也是一样的。  
但是PC端的网易云音乐里，有一个查看更多精彩评论的功能。也就是说，网页版的精彩评论实际上是不全的，还有更多的精彩评论没有获取出来，这点从JSON中 `moreHot` 中也能够看的出来。  
![2](/resource/2017-09-15-Netease-Music-Hot-Comment/2.png)

作为一个在某些方面特别强迫症的人来说(= =)，没有获取到所有的内容这种事情简直是不被允许的，所以开始想办法获取到所有的精彩评论。  
由于网页上显示的精彩评论并不全，所以直接放弃了从网页上抓包的想法。使用Fiddler对PC端进行抓包之后，并没有抓到东西，这是PC端并没有使用http协议。  
在网上搜索解决方案，得到的结果是PC端支持设置使用IE代理。这样就可以抓到http包了。  
设置如下图所示，确定之后需要重启客户端：  

![3](/resource/2017-09-15-Netease-Music-Hot-Comment/3.png)

然后运行Fiddler，设置只抓云音乐进程的包。注意这步要在设置代理后进程重启之后执行，否则抓的就不是同一个进程了。  
![4](/resource/2017-09-15-Netease-Music-Hot-Comment/4.png)

选择一个歌曲，然后点击客户端中查看更多评论，更多的评论会随着下翻操作动态加载，这个时候我们就可以看一眼抓包的成果了。  
![5](/resource/2017-09-15-Netease-Music-Hot-Comment/5.png)
![6](/resource/2017-09-15-Netease-Music-Hot-Comment/6.png)

获取精彩评论的API为： `http://music.163.com/eapi/v1/resource/hotcomments/R_SO_4_(id)` 看起来与获取普通评论差别不大。
