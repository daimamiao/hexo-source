---
title: 'LeetCode 136: Single Number'
date: 2016-08-01 23:43:43
tags: [LeetCode, Bit Manupulation]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given an array of integers, every element appears twice except for one. Find that single one. <!--more-->
**Note:**
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?
### 题意
考虑一个整数数组， 除了一个整数外其他整数都出现了两次，请把这个整数找出来。
### 思路
我们知道两个相同的整数异或会为0，而0跟任何整数异或等于该整数。所以只要把数组的整数不断取出并异或，最后的结果就是那个值。
### 代码
C语言版本：
``` c
int singleNumber(int* nums, int numsSize) {
    int res = 0;
    for (int i = 0; i < numsSize; i++){
        res ^= nums[i];
    }
    return res;
}
```
结果：
`15 / 15 test cases passed.`
Status: `Accepted`
Runtime: `8 ms`