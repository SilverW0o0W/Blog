---
layout:     post
title:      Jekyll无法正确解析.md文件问题
author: Silver
categories: Blog
---

### Important

#### 在Windows环境下保存.md文件一定要使用UTF-8 without BOM方式，否则可能无法正确解析文件

* Virtual Studio

1. 打开文件->高级保存选项  
![0](/resource/2017-03-30-Damn-Encoding/0.png)  
2. 选择Unicode(UTF-8无签名),然后保存  
![1](/resource/2017-03-30-Damn-Encoding/1.png)

* NotePad++  
NotePad++比较好找，Encoding->选中Encode in UTF-8 without BOM即可  
![2](/resource/2017-03-30-Damn-Encoding/2.png)