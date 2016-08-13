---
title: 'LeetCode 28: Implement strStr()'
date: 2016-08-06 18:12:33
tags: [LeetCode, String]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Implement strStr(). Returns the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.
<!--more-->
### 思路
一开始想的是暴力法，就是匹配串与被匹配串从开头开始比较，一发现不对劲，匹配串就向右移动一个单位重新开始比较，一直循环下去直到找到正确匹配位置。后来上网查了一下发现，这是个经典的字符串匹配问题，实现的算法有很多。比如：著名而难以理解的KMP算法、Brute-Force算法、Boyer-Moore算法、Sunday算法......。下面提供的就是Brute-Force算法。
### 代码
C语言版本：
```c
int strStr(char* haystack, char* needle) {
    int m = strlen(haystack);
    int n = strlen(needle);
    if (!n) {
        return 0;
    }
    for (int i = 0; i < m - n + 1; i++) {
        int j = 0;
        for (; j < n; j++){
            if (haystack[i+j] != needle[j]){
                break;
            }
        }
        if (j == n) {
            return i;
        }
    }
    return -1;
}
```
`72 / 72 test cases passed.`
Status: `Accepted`
Runtime: `4 ms`