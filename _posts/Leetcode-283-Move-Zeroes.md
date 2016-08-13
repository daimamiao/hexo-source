---
title: 'Leetcode 283: Move Zeroes'
date: 2016-07-30 18:48:47
tags: [LeetCode, Array]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.<!--more-->For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].
Note:
1. You must do this in-place without making a copy of the array.
2. Minimize the total number of operations.

### 题意
考虑一个数组，写一个函数使用该数组的0移动到数组尾部，而非零的数保持一定的顺序。比如，给一个数组nums =`[0, 1, 0, 3, 12]`,经过该函数处理后，nums应该变为`[1, 3, 12, 0, 0]`;
### 程序(C语言)
```c
void swap(int* nums, int left, int right){
	if (left == right){
		return;
	}else{
		nums[left] ^= nums[right];
		nums[right] ^= nums[left];
		nums[left] ^= nums[right];
	}
}

void moveZeroes(int* nums, int numsSize){
	int left = 0;
	int right = 0;
	while (right < numsSize){
		if (nums[right] != 0){
			swap(nums, left, right);
			left++;
		}
		right++;
	}
}
```
### 结果
`21 / 21 test cases passed.`
Status: `Accepted`
Runtime: `8 ms`
