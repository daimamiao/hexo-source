---
title: 'LeetCode 349: Intersection of Two Arrays'
date: 2016-08-10 13:25:50
tags: [LeetCode, Sort]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given two arrays, write a function to compute their intersection. <!--more-->

**Example:**
Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2].

**Note:**
Each element in the result must be unique.
The result can be in any order.
### 代码
```c
int cmp(const int *a, const int *b) {
    return *a - *b;
}
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* intersection(int* nums1, int nums1Size, int* nums2, int nums2Size, int* returnSize) {
    qsort(nums1,nums1Size,sizeof(int),cmp);
    qsort(nums2,nums2Size,sizeof(int),cmp);
    int size = nums1Size < nums2Size ? nums1Size : nums2Size;
    int* arr = (int*)malloc(sizeof(int)*size); //the size of the result will at most be size;
    int top = -1;
    int p1=0, p2=0;
    while(p1<nums1Size && p2<nums2Size)
    {
        if(nums1[p1] > nums2[p2]) p2++;
        else if(nums1[p1] < nums2[p2]) p1++;
        else //only collect the equal one;
        {
            if(top==-1 || arr[top]!=nums1[p1])  //avoid duplicates;
                arr[++top] = nums1[p1];
            p1++, p2++;
        }
    }
    *returnSize = top+1;
    return arr;
}
```