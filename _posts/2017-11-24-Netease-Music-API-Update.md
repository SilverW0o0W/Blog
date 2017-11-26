---
layout:     post
title:      网易云音乐评论API更新
categories: Python
---

最近网易云音乐更新了获取评论API的逻辑，增加了一些反爬虫的机制。

但是其实更新的东西并不复杂，只需要在原来的基础上处理一下request的参数，再处理一下response就好了。

话说回来...连我这种菜鸡都挡不住的反爬机制，也是够菜的呢= =

