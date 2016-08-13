---
title: 'LeetCode 263: Ugly Number'
date: 2016-08-05 19:28:12
tags: [LeetCode, Math]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Write a program to check whether a given number is an ugly number. Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. <!--more--> For example, 6, 8 are ugly while 14 is not ugly since it includes another prime factor 7.

Note that 1 is typically treated as an ugly number.

### 代码
C语言版本：
```c
bool isUgly(int num) {
    for (int i=2; i<6 && num; i++) {
        while (num % i == 0) {
            num /= i;
        }
    }
    return num == 1;
}
```
`1012 / 1012 test cases passed.`
Status: `Accepted`
Runtime: `4 ms`