---
title: 'LeetCode 350: Intersection of Two Arrays II'
date: 2016-08-05 07:25:38
tags: [LeetCode, Linked List]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given two arrays, write a function to compute their intersection. Example: Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2, 2]. <!--more-->

**Note:**
* Each element in the result should appear as many times as it shows in both arrays.
* The result can be in any order.

### 思路

### 代码
C语言版本：
```c
int cmp(const int* a, const int* b){
    return *a - *b;
}
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* intersect(int* nums1, int nums1Size, int* nums2, int nums2Size, int* returnSize) {
    qsort(nums1, nums1Size, sizeof(int), cmp);
    qsort(nums2, nums2Size, sizeof(int), cmp);
    int i = 0, j = 0, k = 0;
    int* intersect = (int*)malloc(sizeof(int)*(nums1Size+nums2Size));
    while ( i < nums1Size && j < nums2Size ) {
        if ( nums1[i] < nums2[j]) {
            i++;
        }else if ( nums1[i] > nums2[j] ) {
            j++;
        }else {
            intersect[k++] = nums1[i];
            i++;
            j++;
        }
    }
    *returnSize = k;
    return intersect;
}
```
`60 / 60 test cases passed.`
Status: `Accepted`
Runtime: `4 ms`