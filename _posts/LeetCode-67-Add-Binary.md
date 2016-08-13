---
title: 'LeetCode 67: Add Binary'
date: 2016-08-06 11:29:22
tags: [LeetCode, String]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given two binary strings, return their sum (also a binary string). For example, a = `"11"`, b = `"1"`, Return `"100"`.
<!--more-->
### 代码
C语言版本：
```c
char* addBinary(char* a, char* b) {
    int lenA = strlen(a);
    int lenB = strlen(b);
    int len = lenA > lenB ? lenA : lenB;
    char *sum = (char*)calloc(len + 2, sizeof(char));
    sum[len + 1] = '\0';
    lenA--; lenB--;
    int c = 0;
    while (lenA >= 0 || lenB >= 0) {
        c += lenA >= 0 ? a[lenA--] - '0' : 0;
        c += lenB >= 0 ? b[lenB--] - '0' : 0;
        sum[len--] = c % 2 + '0';
        c /= 2;
    }
    if (!c) return sum + 1;
    sum[0] = '1';
    return sum;
}
```
`294 / 294 test cases passed.`
Status: `Accepted`
Runtime: `0 ms`
