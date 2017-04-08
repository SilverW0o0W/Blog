---
layout:     post
title:      Eclipse格式化代码忽略注释格式
categories: Trick
---

Eclipse在格式化代码的时候，经常会把已经设计好格式的注释弄的一团糟，以下的方法可以使我们在格式化代码的时候忽略掉对注释的格式化。

* Window->Preferences->Java->Code Style->Formatter

* 然后点击profile的Edit，如图所示

![0](/resource/2017-04-07-Eclipse-Trick-format/0.png)

* 选择comment选项卡，根据自己的需要来设定是否格式化各种类型的comment

![1](/resource/2017-04-07-Eclipse-Trick-format/1.png)

* 修改之后，由于默认的profile是built in的，无法修改，我们需要修改profile name，然后保存

![2](/resource/2017-04-07-Eclipse-Trick-format/2.png)
![3](/resource/2017-04-07-Eclipse-Trick-format/3.png)

* 接下来就是一路OK的点回去了，继续coding吧，骚年~