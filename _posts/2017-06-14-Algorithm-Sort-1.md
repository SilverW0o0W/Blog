---
layout:     post
title:      排序-位图排序(BitMapSort)
author: Silver
categories: Algorithm Sort
---

## 位图排序(BitMapSort)

位图排序也许是排序中最简单的一种，没有复杂的算法，只需要把源数据遍历一次即可。  
时间复杂度: $$ O(N) $$  
以下是C#的code  
{% highlight ruby %}
private List<int> BitMapSort(int max, List<int> numbers)
{
    List<int> sortNumber = new List<int>();
    BitArray bits = new BitArray(max);
    bits.SetAll(false);
    numbers.ForEach(number => bits.Set(number, true));
    for (int i = 0; i < max; i++)
    {
        if (bits[i])
        {
            sortNumber.Add(i);
        }
    }
    return sortNumber;
}
{% endhighlight %}  
Reference: [Programming Pearls Charter01 Question03][1]

[1]: https://github.com/SilverW0o0W/Blog-Code/blob/b069cd6e2c840b6723bacbd246fd3e17305096ae/Programming%20Pearls/Charter01/Charter01/Question_03.cs