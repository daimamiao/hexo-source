---
title: 'LeetCode 53: Maximum Subarray'
date: 2016-08-12 09:20:36
categories: LeetCode
tags: [LeetCode, Array]
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Find the contiguous subarray within an array (containing at least one number) which has the largest sum. <!--more-->
For example, given the array `[−2,1,−3,4,−1,2,1,−5,4]`,
the contiguous subarray `[4,−1,2,1]` has the largest `sum = 6`.
### Code
```c
int maxSubArray(int* nums, int numsSize) {
    int move = 0;
    int sum = 0;
    int res = nums[0];
    for (int i = 0; i < numsSize; i++) {
        if (sum < 0) {
            sum = 0;
        }
        sum += nums[i];
        if (res <= sum) {
            res = sum;
        }
    }
    return res;
}
```