---
layout:     post
title:      排序-位图排序
categories: Algorithm
---


## 位图排序(BitMapSort)

位图排序也许是排序中最简单的一种，没有复杂的算法，只需要把源数据遍历一次即可。

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
