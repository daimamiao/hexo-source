---
title: 'LeetCode 345: Reverse Vowels of a String'
date: 2016-08-06 09:11:36
tags: [LeetCode, String]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Write a function that takes a string as input and reverse only the vowels of a string.<!--more-->

**Example 1:**
Given s = "hello", return "holle".
**Example 2:**
Given s = "leetcode", return "leotcede".

Note:
The vowels does not include the letter "y".
### 代码
C语言版本：
```c
int isVowelsChar(char p) {
    return (p == 'a' || p == 'e' || p == 'i' || p == 'o' || p == 'u' || p=='A' || p=='E' || p == 'I' || p == 'O' || p =='U');
}
char* reverseVowels(char* s) {
    int left = 0;
    int right = strlen(s) - 1;
    if (strlen(s) < 1) {
        return s;
    }
    while (left < right) {
        while (!isVowelsChar(s[left]) && left < right) {
            left++;
        }
        while (!isVowelsChar(s[right]) && left < right) {
            right--;
        }
        char temp = s[left];
		s[left] = s[right];
		s[right] = temp;
        left++;
		right--;
    }
    return s;
}
```
`481 / 481 test cases passed.`
Status: `Accepted`
Runtime: `4 ms`
