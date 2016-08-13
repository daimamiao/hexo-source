---
title: 'LeetCode 35: Search Insert Position'
date: 2016-08-12 09:01:23
categories: LeetCode
tags: [LeetCode, Array]
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order. <!--more-->
You may assume no duplicates in the array.
Here are few examples.
`[1,3,5,6]`, 5 → 2
`[1,3,5,6]`, 2 → 1
`[1,3,5,6]`, 7 → 4
`[1,3,5,6]`, 0 → 0

### Code
```c
int searchInsert(int* nums, int numsSize, int target) {
    int move = 0;
    while(move < numsSize) {
        if (nums[move] > target) {
            return move > 0 ? move : 0;
        } else if (nums[move] == target) {
            return move;
        }
        move++;
    }
    return move;
}
```