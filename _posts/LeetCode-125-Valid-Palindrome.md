---
title: 'LeetCode 125: Valid Palindrome'
date: 2016-08-07 10:07:53
tags: [LeetCode, String]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases. <!--more-->

For example,
"A man, a plan, a canal: Panama" is a palindrome.
"race a car" is not a palindrome.

**Note:**
Have you consider that the string might be empty? This is a good question to ask during an interview.
For the purpose of this problem, we define empty string as valid palindrome.
### 思路
我的想法是定义一个start指针和end指针，start从头部往尾部移动，end从尾部往头部移动，其中遇到非数字和字母时，要跳过。每次都做一下对比，不同就return 0。否则一直循环下去，如果一路顺利都是匹配的话，那么return 1。      不过有个地方需要注意，匹配是不区分大小写的，所以比较前要先把大写转化为小写。
### 代码
```c
int isAlphanumeric(char p) {
    return ('a' <= p && p <= 'z') || ('A' <= p && p <= 'Z') || ('0' <= p && p <= '9');
}
char lower2Upper(char p) {
	if ('A' <= p && p <= 'Z') {
		return p + 32;
	}
	else {
		return p;
	}
}
bool isPalindrome(char* s) {
    int len = strlen(s);
    if (len < 2) {
        return s;
    }
    int start = 0;
    int end = len - 1;
    while (start < end) {
        while (!isAlphanumeric(s[start])) {
		if (start < end) {
			start++;
		}else{
			return 1;
		}
	}
	while (!isAlphanumeric(s[end])) {
		if (start < end) {
			end--;
		}else {
			return 1;
		}
	}
        if (lower2Upper(s[start]) != lower2Upper(s[end])) {
            return 0;
        }
        start++;
        end--;
    }
    return 1;
}
```
`476 / 476 test cases passed.`
Status: `Accepted`
Runtime: `4 ms`