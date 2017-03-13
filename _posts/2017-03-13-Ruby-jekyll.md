---
layout: post
title: Windows下配置Ruby与jekyll
categories: Blog
---


对于一个对Ruby一无所知的菜鸡来说，这篇blog包含了很多的血泪故事呢...

今天就用我的鲜血来帮助后人吧！（正经脸）

## 安装Git

安装Git还是比较简单的，这里只说一下简要的步骤

* 下载Git

点击 [这个链接][1] 就可以自动下载了

* 安装Git

 这个就不细说了，反正我是一路next下去的（请轻喷）

 安装成功之后，右键菜单会出现Git的两个选项（Git安装时默认配置，可选）
 ![0](/resource/2017-03-13-Ruby-Jekyll/0.png)

## 安装Ruby

* 下载RubyInstaller

嗯，第一个坑爹的地方开始了，首先去下载Ruby的安装包。

[RubyInstaller安装包下载][2]

嗯？你问我为啥不是 [www.ruby-lang.org/zh_cn/downloads/][3] ？

我也很想知道啊！下了半天才看见这句话想过我是什么感觉吗？！
![1](/resource/2017-03-13-Ruby-Jekyll/1.png)

咳咳...不发牢骚了，继续哈...32位64位按照自己喜好来，虽然这个站点访问速度有点问题，下载速度还是可以的
![2](/resource/2017-03-13-Ruby-Jekyll/2.png)
![3](/resource/2017-03-13-Ruby-Jekyll/3.png)

* 安装RubyInstaller

Language 选 English，I accept 也不知道同意了啥...

接下来这个地方比较重要。勾选第二个选项，安装程序自动添加安装路径到环境变量中。看提示，安装路径的文件夹不能有空格，我也是第二次才发现（捂脸），建议安装位置使用默认路径。

没有Ruby经验的菜鸟们，如果不想在下完jekyll之后卸载Ruby再重来一遍，建议乖乖还是默认路径吧...
![4](/resource/2017-03-13-Ruby-Jekyll/4.png)

安装成功之后，右键->Git Bash Here，输入 `ruby -v` ，验证Ruby安装成功。
![5](/resource/2017-03-13-Ruby-Jekyll/5.png)

* 配置UTF-8环境变量

这个部分其实应该放在更后边一点的位置，不过这个属于Ruby的问题，就放在这里面说了。

Ruby默认不支持中文编码，在Blog里面使用中文的话，Jekyll会生成失败。修改方式网上各式各样，有临时修改控制台编码的方式，也有其他的方式就不细说了。
我选择的这个我觉得有好处也有弊端吧，好处是修改之后是永久生效的，不用每次都改。坏处是直接在环境变量里面修改可能对其他程序有影响，但是我暂时还没发现（甩锅脸）。

修改环境变量的步骤这个不用细说吧...计算机->属性->高级->环境变量

在用户变量里面增加两条

LANG : `en_US.UTF-8`

LC_ALL : `en_US.UTF-8`

添加完成，另外我们可以在Path里面看到安装Ruby时我们选中选项的结果。
![6](/resource/2017-03-13-Ruby-Jekyll/6.png)

## 安装jekyll

正常来说，安装jekyll是没有什么难度的问题。但是由于天朝那个世界七大奇迹（you-know-who），导致我们需要翻个山越个岭...

* 修改 gem 数据源

在git中输入 `gem sources` ，查看当前source。

当前sources为https://rubygems.org/ ，由于国内访问有问题，需要删除这个数据源。

`gem sources -r https://rubygems.org/` ，

注意：后边的URL要和显示中的完全一致，否则就会报错。
![7](/resource/2017-03-13-Ruby-Jekyll/7.png)

`gem sources -a http://gems.ruby-china.org/` ，

另一个注意：这个地方最好使用http而不是https，由于证书的问题，https还是无法正常访问站点，所以避免折腾，还是用http比较靠谱。
![8](/resource/2017-03-13-Ruby-Jekyll/8.png)

还有一个注意：这里提供的URL只是可用的站点其中之一，不过鉴于其他站点不是不可用就是已经弃用，菜鸡经过了很多尝试...不想折腾还是用这个吧。

[gems.ruby-china][4]

* 安装jekyll

`gem install jekyll`

这个地方等待的时间会稍微长一会，如果上边的步骤有问题，这个地方就无法正确安装jekyll。
安装完成会输出一大堆结果
![9](/resource/2017-03-13-Ruby-Jekyll/9.png)

* 安装bundler

`gem install bundler`

这个东西吧...港真，菜鸡表示不懂...是我寄几用jekyll的时候发现的，没有这个东西jekyll运行不起来（捂脸）。有兴趣的话自己去了解一下吧。
![10](/resource/2017-03-13-Ruby-Jekyll/10.png)

* 验证安装结果

`bundler -v`
`jekyll -v`

![11](/resource/2017-03-13-Ruby-Jekyll/11.png)

## 生成Blog

这个步骤其实没有必要，这里做一下只是为了验证jekyll的结果。通常大家都会选择一些更好看的theme而不是直接使用默认生成的。
可以熟悉一下用来jekyll的操作。

* 创建一个Site

在资源管理器里面找一个文件夹，作为创建Site的父文件夹

鼠标右键Git Bash Here。当然，从别的地方cd过来也是可以的╭(╯^╰)╮

`jekyll new test`，test为创建的子文件夹的名字

一大堆绿油油的东西滚过去...

![12](/resource/2017-03-13-Ruby-Jekyll/12.png)

* 发布Site

切换到Site的目录下 `cd test`

发布网站 `jekyll server` 或 `jekyll server` 我再或 `jekyll s`
![13](/resource/2017-03-13-Ruby-Jekyll/13.png)

如图中所示，Site的URL为http://127.0.0.1:4000/

另外使用ctrl+c来停止发布网站
![14](/resource/2017-03-13-Ruby-Jekyll/14.png)

## 发布到Github Pages上

这个步骤就不再细述了，就是把代码提交到Github上的过程。不喜欢用console就下载一个Github桌面版，GUI操作很简单。

[Github Desktop][5]

* blog repository clone到本地

根据上一篇博客创建过的repository，里面应该是只有README.md。如果配置了域名的话，还会有一个CNAME文件。

我们只需要将jekyll生成的或者下载的jekyll theme模版copy到repository目录即可。README.md可以被覆盖，但是CNAME文件需要保留。

* jekyll server试运行

使用 `jekyll s` 运行一下，检查Blog网站是否能够成功运行，这步也可以避免遗落什么文件。

* 提交给Github

将repository目录添加的所有文件提交到Github上，访问Github Pages验收结果。

到这里，jekyll的配置就基本完成了。多谢支持~

~\(≧▽≦)/~

**一些值得参考的网站**

[jekyll中文版][6] （内容不全）

[jekyll英文版][7]

[jekyll themes][8]

[1]: https://git-scm.com/download/win
[2]: http://rubyinstaller.org/downloads/
[3]: http://www.ruby-lang.org/zh_cn/downloads/
[4]: http://gems.ruby-china.org/
[5]: https://desktop.github.com/
[6]: http://jekyll.com.cn/
[7]: http://jekyllrb.com/
[8]: http://jekyllthemes.org/