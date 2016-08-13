---
title: 'LeetCode 169 Majority Element'
date: 2016-07-31 21:40:08
tags: [LeetCode, Array]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given an array of size n, find the majority element. The majority element is the element that appears more than `n/2` times.<!--more-->You may assume that the array is non-empty and the majority element always exist in the array.
### 题意
### 代码
C语言版本：
``` c
int majorityElement(int* nums, int numsSize) {
    int major=nums[0], count = 1;
    for(int i=1; i<numsSize;i++){
        if(count==0){
            count++;
            major=nums[i];
        }else if(major==nums[i]){
            count++;
        }else{
            count--;
        } 
    }
    return major;
}
```