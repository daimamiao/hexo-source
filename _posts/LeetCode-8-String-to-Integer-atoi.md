---
title: 'LeetCode 8: String to Integer(atoi)'
date: 2016-08-06 13:38:56
tags: [LeetCode, String]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Implement atoi to convert a string to an integer. Hint: Carefully consider all possible input cases. <!--more-->If you want a challenge, please do not see below and ask yourself what are the possible input cases.

**Notes:** It is intended for this problem to be specified vaguely (ie, no given input specs). You are responsible to gather all the input requirements up front.

### 代码
C语言版本：
```c
int myAtoi(char* str) {
    int sign = 1;
    int res = 0;
    if (!str) {
        return str;
    }
    while(' ' == *str) {
        str++;
    }
    if ('-' == *str || '+' == *str) {
        sign = *str++ == '+' ? 1 : -1;
    }
    while(*str >= '0' && *str <= '9') {
	if (res > INT_MAX / 10 || (res == INT_MAX / 10 && *str - '0' > 7)) {
		return sign > 0 ? INT_MAX : INT_MIN;
	}
	res = res * 10 + (((int)*str++) - '0');
    }
    return res * sign;
}
```
`1047 / 1047 test cases passed.`
Status: `Accepted`
Runtime: `4 ms`