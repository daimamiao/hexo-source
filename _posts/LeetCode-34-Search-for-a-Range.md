---
title: 'LeetCode 34:Search for a Range'
date: 2016-08-13 08:54:59
tags: [LeetCode, Array, Binary Search]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a sorted array of integers, find the starting and ending position of a given target value. <!--more-->

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return [-1, -1].

For example,
Given [5, 7, 7, 8, 8, 10] and target value 8,
return [3, 4].
### Code
```c
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* searchRange(int* nums, int numsSize, int target, int* returnSize) {
    int* res = (int*)malloc(sizeof(int)*2);
    res[0] = -1;
    res[1] = -1;
    int low = 0;
    int high = numsSize - 1;
    int mid = 0;
    while (low < high) {
        mid = (low + high) / 2;
        if (nums[mid] < target) {
            low = mid + 1;
        } else {
            high = mid;
        }
    }
    if (nums[low] != target) {
        *returnSize = 2;
        return res;
    } else {
        res[0] = low;
    }
    high = numsSize - 1;
    while (low < high) {
        mid = (low + high) / 2 + 1;
        if (nums[mid] > target) {
            high = mid - 1;
        } else {
            low = mid;
        }
    }
    res[1] = high;
    *returnSize = 2;
    return res;
}
```