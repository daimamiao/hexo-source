---
title: 'LeetCode 191: Number of 1 Bits'
date: 2016-08-10 11:42:49
tags: [LeetCode, Bit Manipulation]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Write a function that takes an unsigned integer and returns the number of ’1' bits it has (also known as the Hamming weight). <!--more-->
For example, the 32-bit integer ’11' has binary representation `00000000000000000000000000001011`, so the function should return `3`.

### 代码
```c
int hammingWeight(uint32_t n) {
    int nums = 0;
    while ( n != 0) {
        nums = nums + (n & 1);
        n = n >> 1;
    }
    return nums;
}
```