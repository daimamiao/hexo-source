---
title: 'LeetCode 162: Find Peak Element'
date: 2016-08-12 11:40:49
categories: LeetCode
tags: [LeetCode, Array]
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
A peak element is an element that is greater than its neighbors. <!--more--> 

Given an input array where num[i] ≠ num[i+1], find a peak element and return its index.

The array may contain multiple peaks, in that case return the index to any one of the peaks is fine.

You may imagine that `num[-1] = num[n] = -∞`.

For example, in array `[1, 2, 3, 1]`, `3` is a peak element and your function should return the index number `2`.

### Code
```c
int findPeakElement(int* nums, int numsSize) {
    int index = 0;
    for (int i = 0; i < numsSize - 1; i++) {
        if (nums[i] < nums[i+1]) {
            index = i + 1;
        }
    }
    return index;
}
```