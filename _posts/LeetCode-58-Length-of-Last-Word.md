---
title: 'LeetCode 58: Length of Last Word'
date: 2016-08-05 18:23:40
tags: [LeetCode, String]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string. <!--more-->

If the last word does not exist, return 0.
Note: A word is defined as a character sequence consists of non-space characters only.

**For example,**
Given `s = "Hello World"`,
return `5`.

### 代码
C语言版本：
```c
int isChar(char p) {  
    return ('a'<=p && p<='z')||('A'<=p && p<='Z');  
}  
int lengthOfLastWord(char* s) {
    int size = strlen(s);
    int begin;
    int end = size - 1;
    if (size < 1) {
        return 0;
    }
    while(end >= 0 && s[end] == ' ') {
        end--;
    }
    begin = end;
    while ( begin >= 0 && isChar(s[begin])) {
            begin--;
    }
    return end - begin;
}
```