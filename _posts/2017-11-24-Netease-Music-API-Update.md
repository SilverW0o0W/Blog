---
layout:     post
title:      网易云音乐评论API更新
author: Silver
categories: Python
---

最近网易云音乐更新了获取评论API的逻辑，增加了一些反爬虫的机制。  
但是其实更新的东西并不复杂，只需要在原来的基础上处理一下request的参数，再处理一下response就好了。  
话说回来...连我这种菜鸡都挡不住的反爬机制，也是够菜的呢= =  
原来的code中，我们的request header是这样的:
{% highlight ruby %}
__headers = {
    'Cookie': 'appver=1.5.0.75771;',
    'Referer': 'http://music.163.com/'
}
{% endhighlight %}
现在使用这种header发送request的话，只会得到这样的结果：
`'{"code":-460,"msg":"Cheating"}'`  
在用Fiddler重新抓了一下评论API的包之后，发现header发生了变化。下面是筛选过后，能够正常获取response的header。  
{% highlight ruby %}
__headers = {
    'Host': 'music.163.com',
    'Proxy-Connection': 'keep-alive',
    'Origin': 'http://music.163.com',
    'User-Agent': 'Mozilla/5.0 (Windows NT 6.3; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36',
    'Content-Type': 'application/x-www-form-urlencoded',
    'Accept': '*/*',
    'Accept-Encoding': 'gzip, deflate',
    'Accept-Language': 'zh-CN,zh;q=0.8'
}
{% endhighlight %}  
看起来加了不少的东西，剩下的这些我也不确定所有的都是完全必要的，不过好用的话就没什么问题了吧= =