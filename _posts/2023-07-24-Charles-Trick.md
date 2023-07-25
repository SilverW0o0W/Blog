---
layout:     post
title:      Charles实用技巧
author: Silver
categories: Trick
---

### First of All

Charles更新频率较低(2023.2月，现已恢复更新)，苹果M系列芯片兼容性问题迟迟未解决，建议换成Proxyman，功能只多不少。(刚上来就推荐别的软件似乎有点过分?

链接: https://proxyman.io/

### 抓包请求导入到Postman中

1. 在Charles请求上右键，将请求复制为cURL Request

2. Postman中使用File -> Import -> Raw text 即可将完整请求导入到Postman中

### 关闭抓取电脑请求

使用Charles抓包时，电脑上的请求会影响抓包效率。可以通过取消勾选Proxy -> macOS Proxy选项来关闭Charles抓取电脑请求，只抓手机。Windows系统也存在类似选项。

### Mac M1/M2芯片机器软件卡顿（版本4.6.3）

4.6.3版本Charles(4.6.3)存在bug，苹果系统为浅色模式时软件会非常卡。 目前软件更新频率较低，以下为临时解决办法: 将苹果系统改为深色模式 。

tips: 目前Charles的主题颜色根据系统自动改变，无法单独修改。只能将全局改为深色模式解决。
