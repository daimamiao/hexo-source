---
title: 'Leetcode 217: Contains Duplicate'
date: 2016-07-30 18:34:47
tags: [LeetCode, Array]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given an array of integers, find if the array contains any duplicates. Your function should return true if any value appears at least twice in the array<!--more-->,and it should return false if every element is distinct.
### 题意
大概为, 考虑一个整型的数组，找出是否该数组有重复的数。如果有数出现超过两次，那么你的函数返回`ture`，否则返回`false`。
### 程序(C语言)
```c
int cmp(const int* a, const int* b){
    return *a - *b;
}
bool containsDuplicate(int* nums, int numsSize) {
    qsort(nums, numsSize, sizeof(int), cmp);
    if (numsSize < 2){
        return false;
    }
    int i;
    for (i=0; i<(numsSize-1); i++){
        if (nums[i] == nums[i+1]){
            return true;
        }
    }
    return false;
}
```
### 结果
`16 / 16 test cases passed.`
Status: `Accepted`
Runtime: `12 ms`


