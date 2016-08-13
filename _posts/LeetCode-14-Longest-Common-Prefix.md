---
title: 'LeetCode 14: Longest Common Prefix'
date: 2016-08-06 10:19:56
tags: [LeetCode, String]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Write a function to find the longest common prefix string amongst an array of strings. <!--more-->
### 代码
C语言版本：
```c
char* longestCommonPrefix(char** strs, int strsSize) {
    if (strs == NULL || *strs == NULL) {
        return "";
    }
    int len = strlen(strs[0]);
    int max = 0;
    char *res;
    while (max < len) {
        for (int i = 1; i < strsSize; i++) {
            if (strs[i][max] != strs[0][max]) {
                len = max;
                break;
            }
        }
        if (max < len) max++;
    }
    res = (char*)malloc(sizeof(char)*(max+1));
    for (int i = 0; i < max; i++) {
        res[i] = strs[0][i];
    }
    res[max] = '\0';
    return res;
}
```
`117 / 117 test cases passed.`
Status: `Accepted`
Runtime: `0 ms`