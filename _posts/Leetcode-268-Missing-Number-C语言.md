---
title: 'LeetCode 268: Missing Number'
date: 2016-07-31 15:55:31
tags: [LeetCode, Array]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.<!--more-->For example,Given nums = [0, 1, 3] return 2.
<strong>Note:</strong>
	Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity?
### 题意
考虑一个包含n个不同数字的数组，以0, 1, 2, ..., n,的顺序排列，找到一个数组中缺失的数字。比如，`nums = [0, 1, 3]`则返回2。
### 程序
以我这渣渣水平，一看到题目就想到了一个很渣的算法，如下：
``` c
int cmp(const int* a, const int* b){
    return *a - *b;
}
int missingNumber(int* nums, int numsSize) {
    int left = 0;
    int right = 1;
    int flag = 0;
    qsort(nums, numsSize, sizeof(int), cmp);
    if (numsSize == 1){
        return nums[0]?0:1;
    }
    while (right<numsSize){
        if ( (nums[right]-nums[left]) != 1 ){
            flag++;
            return nums[right]-1;
        }
        left++;
        right++;
    }
    if (!flag){
        return nums[0]?0:(nums[numsSize-1]+1);
    }
    return false;
}
```

结果可以想象得到：
`121 / 121 test cases passed.`
Status: `Accepted`
Runtime: `28 ms`
看了一下，结果果然很渣，打败了4.37%的人。
后来上网学习到了一种很吊的：
``` c
int missingNumber(int* nums, int numsSize) {
    int res = numsSize;
    for(int i = 0; i < numsSize; i++){
        res ^= i ^ nums[i];
    }
    return res;
}
```
结果很感人：
`121 / 121 test cases passed.`
Status: `Accepted`
Runtime: `12 ms`
