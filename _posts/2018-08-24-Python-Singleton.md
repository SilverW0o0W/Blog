---
layout:     post
title:      Python单例模式
categories: Python
---

### 单例模式（无锁）
{% highlight ruby %}
class Singleton(object):
    _instance = None
    def __new__(cls,*args,**kwargs):
        if not cls._instance:
            cls._instance=super(Singleton,cls).__new__(
                cls,*args,**kwargs
            )
            return cls._instance
{% endhighlight %}  
### 单例模式（双检锁）
{% highlight ruby %}
import threading

class Singleton(object):
    objs={}
    objs_locker = threading.Lock()

    def __new__(cls,*args,**kv):
        if cls in cls.objs:
            return cls.objs[cls]
        with objs_locker:
            if cls in cls.objs:
                return cls.objs[cls]
            cls.objs[cls]=object.__new__(cls)
{% endhighlight %}  

Reference： [Code下载地址][1]

[1]:
https://github.com/SilverW0o0W/Blog-Code/blob/master/%E6%94%B9%E5%96%84Python%E7%A8%8B%E5%BA%8F%E7%9A%8491%E4%B8%AA%E5%BB%BA%E8%AE%AE/Suggestion%2050/singleton.py