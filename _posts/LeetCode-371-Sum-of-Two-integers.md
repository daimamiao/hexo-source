---
title: 'LeetCode 371: Sum of Two integers'
date: 2016-08-02 18:43:25
tags: [LeetCode, Bit Manupulation]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Calculate the sum of two integers a and b, but you are not allowed to use the operator + and -.Example: Given a = 1 and b = 2, return 3.<!---more-->
### 题意
计算a和b的和，但是不能使用`+`和`-`号。
### 思路
这里要求我们不能用加法、减法等运算符来实现加法运算。这里应该使用位运算来实现加法运算，实际上，这也是计算机CPU内部实现加法运算的方案。 
**x ^ y真值表:**

| x   			| y 			| x^y 	|
| ------------- |:-------------:| -----:|
| 0   			| 0 			| 0 	|
| 0   			| 1 			| 1 	|
| 1   			| 0 			| 1 	|
| 1	  			| 1 			| 0 	|


**x & y真值表:**

| x 			| y 			| x&y 	|
| ------------- |:-------------:| -----:|
| 0 			| 0 			| 0 	|
| 0 			| 1 			| 0 	|
| 1 			| 0 			| 0 	|
| 1 			| 1 			| 1 	|
我们可以基于以上的真值表用&和^运算来实现加法，每一位的^运算得到每一位上的不加进位的和，用&运算得到每一位的进位。
### 代码
C语言版本：
``` c
int getSum(int a, int b) {
    int sum = a;
    int carry = b;
    int tmp;
    while ( carry ){
        tmp = sum;
        sum = sum ^ carry;
        carry = (carry & tmp) << 1;
    }
    return sum;
}
```