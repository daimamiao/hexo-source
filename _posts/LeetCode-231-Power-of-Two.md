---
title: 'LeetCode 231: Power of Two'
date: 2016-08-08 15:33:15
tags: [LeetCode, Math]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
这个题跟`Power of Three`的思路基本一模一样，解法也差不多。但是因为是2啊，毕竟是计算机的进制数，所以`&`,`|`这些位操作总能出奇迹。
<!--more-->
### 思路
我们可以列几个2的次幂数就可以发现，他们的二进制数的最高位为1，其他位都是0。所以让她与比她小的一个数的数做一下位与`&`即有结果为0。
### 代码
```c
bool isPowerOfTwo(int n) {
    return n > 0 && !(n & (n - 1));
}
```