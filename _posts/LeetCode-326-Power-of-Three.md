---
title: 'LeetCode 326: Power of Three'
date: 2016-08-08 15:02:06
tags: [LeetCode, Math]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
今天突然发现做LeetCode上Math的题目真心很有趣，不仅解法多样，还能时不时被绝妙的想法高潮一波。<!--more-->
Given an integer, write a function to determine if it is a power of three.
**Follow up:**
Could you do it without using any loop / recursion?
### 思路
这道题目因为有int的限制，所以知道3的次幂的数肯定大不过1162261467。
### 代码
```c
bool isPowerOfThree(int n) {
    return (n > 0 && 1162261467 % n == 0);
}
```
利用log实现
```c
bool isPowerOfThree(int n) {
    return fmod(log10(n)/log10(3), 1)==0;
}
```
题目说明了不可以使用循环或递归：
```c
// 递归
bool isPowerOfThree(int n) {
	return n>0 && (n==1 || (n%3==0 && isPowerOfThree(n/3)));
}
```
```c
// 循环
bool isPowerOfThree(int n) {
	if(n>1)
        while(n%3==0) n /= 3;
    return n==1;
}
```
`21038 / 21038 test cases passed.`
Status: `Accepted`
Runtime: `120 ms`
