---
title: 'LeetCode 12: Integer to Roman'
date: 2016-08-09 08:18:43
tags: [LeetCode, Math]
categories: LeetCode
series: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given an integer, convert it to a roman numeral. Input is guaranteed to be within the range from 1 to 3999. <!--more-->

### 代码
```c
char* intToRoman(int num) {
    char *str = (char *)malloc(100);
    memset(str,0,100);
	char *strM[] = { "", "M", "MM", "MMM" };
	char *strC[] = { "", "C", "CC", "CCC", "CD", "D", "DC", "DCC", "DCCC", "CM" };
	char *strX[] = { "", "X", "XX", "XXX", "XL", "L", "LX", "LXX", "LXXX", "XC" };
	char *strI[] = { "", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX" };
	strcpy(str, strM[num / 1000]);
	strcat(str, strC[(num % 1000) / 100]);
	strcat(str, strX[(num % 100) / 10]);
	strcat(str, strI[num % 10]);
	return str;
}
// 这里不太明白char str[100] = {0} 为什么不行
```
