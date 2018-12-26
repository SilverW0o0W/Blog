---
layout:     post
title:      重构Proxy
categories: Python
---

最近一直打算用Tornado重写[Netease-Music-Web][1]，但是感觉作为基础的Netease-Music和Proxy越来越坑，所以一直像无头苍蝇一样这改一点那改一点。
最后感觉之前Proxy的代理池实现方式怎么看怎么别扭，就决定先弄这玩意了 = =
[Proxy][2]

[1]: https://github.com/SilverW0o0W/Netease-Music-Web
[2]: https://github.com/SilverW0o0W/Proxy