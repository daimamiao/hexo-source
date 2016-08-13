---
title: 'LeetCode 50: Pow(x, n)'
date: 2016-08-09 09:57:20
tags: [LeetCode, Math]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Implement pow(x, n). <!--more-->

### 代码
```c
double myPow(double x, int n) {
    double res = 1;
    double flag = x;
    int m = n;
	if (n < 0) {
		x = 1 / x;
		if (n == INT_MIN) {
			n = INT_MAX;
		} else {
			n = -n;
		}
	}
	while (n>0) {
		if (n & 1 == 1) {
			res = res*x;
		}
		x *= x;
		n = n >> 1;
	}
	if (m == INT_MIN) {
	    if (flag < 0) {
	        return -res;
	    }
	}
    return res;
}
```
