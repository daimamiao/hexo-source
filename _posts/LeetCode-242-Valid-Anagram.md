---
title: 'LeetCode 242: Valid Anagram'
date: 2016-08-10 13:08:47
tags: [LeetCode, Sort]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given two strings s and t, write a function to determine if t is an anagram of s. <!--more-->
**For example,**
s = "anagram", t = "nagaram", return true.
s = "rat", t = "car", return false.

Note:
You may assume the string contains only lowercase alphabets.

### 代码
```c
int cmp(const char *a, const char *b) {
	return *a - *b;
}
bool isAnagram(char* s, char* t) {
    int lenS = strlen(s);
    int lenT = strlen(t);
    if (lenS != lenT) {
        return false;
    }
    qsort(s, lenS, sizeof(char), cmp);
    qsort(t, lenT, sizeof(char), cmp);
    for (int i = 0; i < lenS; i++) {
        if (s[i] != t[i]) {
            return false;
        }
    }
    return true;
}
```