---
title: 'LeetCode 69: Sqrt(x)'
date: 2016-08-09 10:08:51
tags: [LeetCode, Math]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Implement int sqrt(int x). Compute and return the square root of x. <!--more-->
### 思路
这里使用的方法是：牛顿迭代法快速寻找平方根。如果想详细了解，可以看看这篇文章一个Sqrt函数引发的血案 [一个Sqrt函数引发的血案](http://diducoder.com/sotry-about-sqrt.html)
### 代码
```c
int mySqrt(int x) {
    long r = x;
    while (r*r > x)
        r = (r + x/r) / 2;
    return r;
}
```