---
title: 'LeetCode 229: Majority Element II'
date: 2016-07-31 22:29:46
tags: [LeetCode, Array]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given an integer array of size n, find all elements that appear more than ⌊ n/3 ⌋ times. The algorithm should run in linear time and in O(1) space.<!--more-->
Hint:
1. How many majority elements could it possibly have?
2. Do you have a better hint? Suggest it!

### 题意
### 思路
这道题让我们求出现次数大于n/3的众数，而且限定了时间和空间复杂度，那么就不能排序，也不能使用哈希表，这么苛刻的限制条件只有一种方法能解了，那就是摩尔投票法 Moore Voting，这种方法在之前那道题Majority Element 求众数中也使用了。题目中给了一条很重要的提示，让我们先考虑可能会有多少个众数。那么有了这个信息，我们使用投票法的核心是找出两个候选众数进行投票，需要两遍遍历，第一遍历找出两个候选众数，第二遍遍历重新投票验证这两个候选众数是否为众数即可，选候选众数方法和前面那篇Majority Element 求众数一样，由于之前那题题目中限定了一定会有众数存在，故而省略了验证候选众数的步骤，这道题却没有这种限定，即满足要求的众数可能不存在，所以要有验证。代码如下：
### 代码
C语言版本：
``` c
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* majorityElement(int* nums, int numsSize, int* returnSize) {
    int* res = (int*)malloc(sizeof(int)*numsSize);
    int firstNum = 0, secondNum = 0, countFN = 0, countSN = 0; 
    for(int i=0; i<numsSize; i++){
        if (nums[i] == firstNum){
            countFN++;
        }else if (nums[i] == secondNum){
            countSN++;
        }else if (countFN == 0){
            firstNum = nums[i];
            countFN = 1;
        }else if (countSN == 0){
            secondNum = nums[i];
            countSN = 1;
        }else{
            countFN--;
            countSN--;
        }
    }
    countFN = countSN = 0;
    for (int i=0; i<numsSize; i++) {
        if (nums[i] == firstNum){
            ++countFN;
        } 
        else if (nums[i] == secondNum){
            ++countSN;
        } 
    }
    if (countFN > numsSize/3){
        res[0] = firstNum;
    }
    if (countSN > numsSize/3){
        res[1] = secondNum;
    }
    *returnSize = numsSize;
    return res;
    
}
```
C++版本：
``` cpp
class Solution {
public:
    vector<int> majorityElement(vector<int>& nums) {
        vector<int> res;
        int m = 0, n = 0, cm = 0, cn = 0;
        for (auto &a : nums) {
            if (a == m) ++cm;
            else if (a ==n) ++cn;
            else if (cm == 0) m = a, cm = 1;
            else if (cn == 0) n = a, cn = 1;
            else --cm, --cn;
        }
        cm = cn = 0;
        for (auto &a : nums) {
            if (a == m) ++cm;
            else if (a == n) ++cn;
        }
        if (cm > nums.size() / 3) res.push_back(m);
        if (cn > nums.size() / 3) res.push_back(n);
        return res;
    }
};
```