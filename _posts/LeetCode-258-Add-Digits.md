---
title: 'LeetCode 258: Add Digits'
date: 2016-08-09 10:42:38
tags: [LeetCode, Math]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a non-negative integer num, repeatedly add all its digits until the result has only one digit. <!--more-->For example:Given num = 38, the process is like: 3 + 8 = 11, 1 + 1 = 2. Since 2 has only one digit, return it.
### 代码
```c
int addDigits(int num) {
    int res = num % 9;
    return (res != 0 || num == 0) ? res : 9;
}
```