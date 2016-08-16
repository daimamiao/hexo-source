---
title: 'LeetCode 171:Excel Sheet Column Number'
date: 2016-08-16 11:08:39
tags: [LeetCode, Stack]
categories: LeetCode
thumbnail:
---
Related to question Excel Sheet Column Title

Given a column title as appear in an Excel sheet, return its corresponding column number.

For example:
```
    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
```

### Code
```c
int titleToNumber(char* s) {
    int result = 0;
    int size = strlen(s);
    for (int i = 0; i < size; i++) {
        result = result * 26 + (s[i] - 'A' + 1);
    }
    return result;
}
```