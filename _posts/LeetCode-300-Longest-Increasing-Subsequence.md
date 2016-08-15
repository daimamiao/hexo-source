---
title: 'LeetCode 300:Longest Increasing Subsequence'
date: 2016-08-14 09:00:09
tags: [LeetCode, Binary Search]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given an unsorted array of integers, find the length of longest increasing subsequence. <!--more-->

For example,
Given [10, 9, 2, 5, 3, 7, 101, 18],
The longest increasing subsequence is [2, 3, 7, 101], therefore the length is 4. Note that there may be more than one LIS combination, it is only necessary for you to return the length.

Your algorithm should run in O(n2) complexity.

Follow up: Could you improve it to O(n log n) time complexity?
### Code
```c
int lengthOfLIS(int* nums, int numsSize) {
    int* tails = (int*)malloc(sizeof(int)*numsSize);
    int size = 0;
    for (int i = 0; i < numsSize; i++) {
        int left = 0, right = size;
        while(left != right) {
            int mid = (left + right) / 2;
            if (tails[mid] < nums[i])
                left = mid + 1;
            else
                right = mid;
        }
        tails[left] = nums[i];
        if (left == size) ++size;
    }
    return size;
}
```