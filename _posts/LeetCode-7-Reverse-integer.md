---
title: 'LeetCode 7: Reverse integer'
date: 2016-08-09 08:37:40
tags: [LeetCode, Math]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Reverse digits of an integer. Example1: x = 123, return 321 Example2: x = -123, return -321. <!--more-->

### 代码
```c
int reverse(int x) {
    int res = 0;
    while (x != 0) {
        if (res > INT_MAX/10 ||res < INT_MIN/10) {
            return 0;
        }
        res = x % 10 + res * 10;
        x /= 10;
    }
    return res;
}
```
