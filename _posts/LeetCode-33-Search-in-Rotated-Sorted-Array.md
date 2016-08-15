---
title: 'LeetCode 33:Search in Rotated Sorted Array'
date: 2016-08-14 09:18:24
tags: [LeetCode, Binary Search]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Suppose a sorted array is rotated at some pivot unknown to you beforehand. <!--more-->

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).

You are given a target value to search. If found in the array return its index, otherwise return -1.

You may assume no duplicate exists in the array.
### Code
```c
int search(int* nums, int numsSize, int target) {
    int move = 0;
    for (int i  = 0; i < numsSize; i++) {
        if (nums[i] == target) {
            return i;
        }
    }
    return -1;
}
```
#### 使用Binary Search
```c
int search(int* nums, int numsSize, int target) {
    int left = 0;
    int right = numsSize - 1;
    int mid = 0;
    // find the index of smallest value using binary search
    while(left < right) {
        mid = (left + right) / 2;
        if (nums[mid] > nums[right]) {
            left = mid + 1;
        } else {
            right = mid;
        }
    }
    int smallest = left;
    left = 0;
    right = numsSize - 1;
    int realMid = 0;
    while(left <= right) {
        mid = (left + right) / 2;
        realMid = (mid + smallest) % numsSize;
        if(nums[realMid] == target) {
            return realMid;
        }
        if(nums[realMid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return -1;
}
```