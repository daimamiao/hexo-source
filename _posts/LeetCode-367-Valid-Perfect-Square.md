---
title: 'LeetCode 367:Valid Perfect Square'
date: 2016-08-14 10:51:34
tags: [LeetCode, Math]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a positive integer num, write a function which returns True if num is a perfect square else False. <!--more-->

Note: Do not use any built-in library function such as sqrt.

**Example 1:**

>Input: 16
Returns: True

**Example 2:**

>Input: 14
Returns: False

### Code
```c
bool isPerfectSquare(int num) {
    int i = 1;
    while (num > 0) {
        num -= i;
        i += 2;
    }
    return num == 0;
}
```