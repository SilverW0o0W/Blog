---
layout:     post
title:      Python单例模式
author: Silver
categories: Python
---

### 继承模式-无锁

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

### 继承模式-双检锁

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

### 元类(metaclass)模式-无锁

{% highlight ruby %}
class Singleton(type):
    def __init__(cls,name,bases,dic):
        super(Singleton,cls).__init__(name,bases,dic)
        cls.instance = None
    
    def __call__(cls,*args,**kwargs):
        if cls.instance is None:
            print "creating a new instance"
            cls.instance=super(Singleton,cls).__call__(*args,**kwargs)
        else:
            print "warning: only allowed to create one instance, instance already exists!"
        return cls.instance

class MySingleton(object):
    __metaclass__ = Singleton
{% endhighlight %}

### import模式-无需加锁

{% highlight ruby %}
# singleton.py
class Singleton(object):
    def __init__(self):
        pass
    def do_sth(self):
        pass

single = Singleton()
# main.py
import singleton

print singleton.single.do_sth()

{% endhighlight %}

##### Reference：

* [继承模式][1]
* [元类模式][2]

[1]:https://github.com/SilverW0o0W/Blog-Code/blob/master/%E6%94%B9%E5%96%84Python%E7%A8%8B%E5%BA%8F%E7%9A%8491%E4%B8%AA%E5%BB%BA%E8%AE%AE/Suggestion%2050/singleton.py
[2]:https://github.com/SilverW0o0W/Blog-Code/blob/master/%E6%94%B9%E5%96%84Python%E7%A8%8B%E5%BA%8F%E7%9A%8491%E4%B8%AA%E5%BB%BA%E8%AE%AE/Suggestion%2062/singleton.py
