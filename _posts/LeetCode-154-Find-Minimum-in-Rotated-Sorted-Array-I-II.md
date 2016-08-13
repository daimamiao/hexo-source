---
title: 'LeetCode 154:Find Minimum in Rotated Sorted Array I,II'
date: 2016-08-13 07:33:20
tags: [LeetCode, Array, Binary Search]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Suppose a sorted array is rotated at some pivot unknown to you beforehand. <!--more-->

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).

Find the minimum element.

You may assume no duplicate exists in the array.
```c
int findMin(int* nums, int numsSize) {
    int move = 0;
    int min = nums[0];
    while (move < numsSize) {
        if (nums[move] < min) {
            min = nums[move];
        }
        move++;
    }
    return min;
}
```

Binary Search
```c
int findMin(int* nums, int numsSize) {
    int low = 0;
    int high = numsSize - 1;
    int mid = 0;
    while (low < high) {
        mid = (low + high) / 2;
        if (nums[mid] < nums[high]) {
            high = mid;
        } else if (nums[mid] > nums[high]) {
            low = mid + 1;
        } else {
            high--;
        }
    }
    return nums[low];
}
```