---
layout: post
title: Github Pages 个人博客及域名配置
categories: Blog
---
这是这个网站的第一篇博客，谁知道会不会有第二篇。如果这篇好用的话，就讲讲配了一天的Github Pages + jekyll的配置好了。  
。。。  
从头折腾这个东西还是挺麻烦的，网上的教程不是时间太久不靠谱了，就是有些奇葩的问题找不到。

## Github Pages配置
  * 创建一个 repository

网页右上角，加号+，怼它，对，使劲  
![1](/resource/2017-03-09-Hello-Blog/1.png)  
给repository起一个名字，选中Initialize this repository with a README，create repository  
![2](/resource/2017-03-09-Hello-Blog/2.png)  

 * 设置repository setting

找到repository setting，眼神不大好使，找了好几秒(((φ(◎ロ◎;)φ)))  
![3](/resource/2017-03-09-Hello-Blog/3.png)  
打开setting页面之后直接翻到底部，找到Github Pages选项卡  
source选择master branch，点击save  
![4](/resource/2017-03-09-Hello-Blog/4.png)  
save之后，选项卡中会出现提示，生成了Github Pages的URL： [https://silverw0o0w.github.io/Test/][1]  
![5](/resource/2017-03-09-Hello-Blog/5.png)  
访问 [https://silverw0o0w.github.io/Test/][1] ，首页出现啦~  
(￣▽￣)～■ □～(￣▽￣)~*  
![6](/resource/2017-03-09-Hello-Blog/6.png)  
到这里，Github Pages配置完成。接下来如果有需要的话，可以将Github Pages定向到自己的域名。  
在这之前我建议你最好先记住现在的URL，别问我为什么_(:з」∠)_  

## 个人域名配置
 * 配置Github CNAME文件
打开repository首页，Create new file  
![7](/resource/2017-03-09-Hello-Blog/7.png)  
输入文件名CNAME，以及自己的域名。注意CNAME没有后缀名，且需要大写  
![8](/resource/2017-03-09-Hello-Blog/8.png)
![9](/resource/2017-03-09-Hello-Blog/9.png)  
在chrome输入域名试试~当然...不好使╮(╯▽╰)╭  
![10](/resource/2017-03-09-Hello-Blog/10.png)

 * ping Github Pages 的公网IP

Win+R，cmd 打开控制台  
ping 之前URL的域名：silverw0o0w.github.io，没记住就傻了吧~  
～(￣▽￣～)(～￣▽￣)～  
![11](/resource/2017-03-09-Hello-Blog/11.png)  
记录域名对应的ip

 * 解析域名

打开个人域名所在的域名服务商网站，找到控制台， 选择域名，解析  
以上步骤自行解决┑(￣Д ￣)┍  
在域名解析中新增两条解析记录  
类型A 主机记录www 记录值为公网ip地址  
类型A 主机记录@ 记录值为公网ip地址  
![12](/resource/2017-03-09-Hello-Blog/12.png)  
最后一步，等着~  
最最后一步，访问个人的域名  
![13](/resource/2017-03-09-Hello-Blog/13.png)  
成功~  
撒花~  

*★,°*:.☆(￣▽￣)/$:*.°★* 。  
*★,°*:.☆(￣▽￣)/$:*.°★* 。  
*★,°*:.☆(￣▽￣)/$:*.°★* 。  
接下来会另开一篇讲解jekyll的配置

[1]: https://silverw0o0w.github.io/Test/