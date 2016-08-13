---
title: 'LeetCode 338: Counting Bits'
date: 2016-08-10 11:23:44
tags: [LeetCode, Bit Manipulation]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a non negative integer number num. For every numbers i in the range 0 ≤ i ≤ num calculate the number of 1's in their binary representation and return them as an array. <!--more-->

Example:
For num = 5 you should return [0,1,1,2,1,2].

Follow up:

It is very easy to come up with a solution with run time O(n*sizeof(integer)). But can you do it in linear time O(n) /possibly in a single pass?
Space complexity should be O(n).
Can you do it like a boss? Do it without using any builtin function like __builtin_popcount in c++ or in any other language.

### 代码
```c
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* countBits(int num, int* returnSize) {
    int* res = (int*)malloc((num+1)*sizeof(int));
    res[0] = 0;
    for (int i = 1; i <= num; i++ ) {
        res[i] = res[i>>1] + (i & 1);
    }
    *returnSize = num + 1; 
    return res;
}
```
