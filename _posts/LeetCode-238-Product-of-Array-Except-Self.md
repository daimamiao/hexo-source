---
title: 'LeetCode 238: Product of Array Except Self'
date: 2016-07-31 21:28:39
tags: [LeetCode, Array]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given an array of n integers where n > 1, nums, return an array output such that output[i] is equal to the product of all the elements of nums except nums[i].<!--more-->
Solve it without division and in O(n).
For example, given `[1,2,3,4]`, return `[24,12,8,6]`.
### 题意
### 代码
``` c
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* productExceptSelf(int* nums, int numsSize, int* returnSize) {
    int* res = (int*)malloc(sizeof(int)*numsSize); //the result array;
    for (int i = 0, tmp = 1; i < numsSize; i++) {
        res[i] = tmp;
        tmp *= nums[i];
    }
    for (int i = numsSize - 1, tmp = 1; i >= 0; i--) {
        res[i] *= tmp;
        tmp *= nums[i];
    }
    *returnSize = numsSize;
    return res;
}
```
