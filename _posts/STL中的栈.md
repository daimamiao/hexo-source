---
title: STL中的栈
date: 2016-08-15 13:21:50
tags:
categories:
thumbnail:
---
栈是一种数据项按序排列的数据结构，只能在它的一端进行删除和插入。 <!--more-->最近在学习STL中一些基础数据结构的模板。因为C语言在使用这些数据结构之前还得自己实现一遍，很是麻烦。而STL中已经帮我们封装好了这些数据结构的内部操作。

### 栈的基本用法
##### 头文件
首先使用stack标准模板之前我们需要在加上头文件`#include <stack>`。并要声明使用标准命名空间`using namespace std;`。

然后使用`stack<int> S;`定义一个保存int类型数据的栈S，这样所有有关栈实现的内部操作，STL都已经帮我们实现好了。

##### 内部操作
1. 使用`S.push()`向栈中压进一个数值为i的元素。

2. 使用`int x = S.top()`读取栈顶元素，并将其值赋予给x。

3. 使用`S.pop()`弹出栈顶元素。

### 具体例子
#### 括号匹配问题
##### 题目描述：
在某个字符串（长度不超过100）中有左括号、右括号和大小写字母；规定（与常见的算数式子一样）任何一个左括号都从内到外与在它右边且距离最近的右括号匹配。写一个程序，找到无法匹配的左括号和右括号，输出原来字符串，并在下一行标出不能匹配的括号。不能匹配的左括号用"$"标注,不能匹配的右括号用"?"标注.
##### 输入：
输入包括多组数据，每组数据一行，包含一个字符串，只包含左右括号和大小写字母，字符串长度不超过100。
注意：cin.getline(str,100)最多只能输入99个字符！
##### 输出：
对每组输出数据，输出两行，第一行包含原始输入字符，第二行由"$","?"和空格组成，"$"和"?"表示与之对应的左括号和右括号不能匹配。
##### 样例输入：
```
)(rttyy())sss)(
```

##### 样例输出：
```
)(rttyy())sss)(
?            ?$
```

##### Code
```c
#include <stdio.h>
#include <stack>
using namespace std;

stack<int> S;
char str[110];
char res[110];

int main() {
	while(scanf("%s", str) != EOF) {
		for (int i = 0; str[i] != 0; i++) {
			if (str[i] == '(') {
				S.push(i);
				res[i] = ' ';
			} else if (str[i] == ')') {
				if (S.empty() == false) {
					S.pop();
					res[i] = ' ';
				} else {
					res[i] = '?';
				}
			} else {
				res[i] = ' ';
			}
		}
		while (!S.empty()) {
			res[S.top()] = '$';
			S.pop();
		}
		res[i] = 0;
		puts(str);
		puts(res);
	}
	return 0;
}
```

#### 简单计数器
##### 题目描述：
读入一个只包含 +, -, *, / 的非负整数计算表达式，计算该表达式的值。
##### 输入：
测试输入包含若干测试用例，每个测试用例占一行，每行不超过200个字符，整数和运算符之间用一个空格分隔。没有非法表达式。当一行中只有0时输入结束，相应的结果不要输出。
##### 输出：
对每个测试用例输出1行，即该表达式的值，精确到小数点后2位。
##### 样例输入：
```
1 + 2
4 + 2 * 5 - 7 / 11
0
```
##### 样例输出：
```
3.00
13.36
```
##### Code
```c
#define _CRT_SECURE_NO_DEPRECATE
#include <stdio.h>
#include <stack>
using namespace std;

stack<double> digit;
stack<int> op;
char str[110];
int mat[][5] = {
	1, 0, 0, 0, 0,
	1, 0, 0, 0, 0,
	1, 0, 0, 0, 0,
	1, 1, 1, 0, 0,
	1, 1, 1, 0, 0
};
// reto is true => oparator
// reto is false => number
void getOp(bool &reto, int &retn, int &i) {
	if (i == 0 && op.empty()) {
		reto = true;
		retn = 0;
		return;
	}
	if (str[i] == 0) {
		reto = true;
		retn = 0;
		return;
	}
	if (str[i] >= '0' && str[i] <= '9') {
		reto = false;
		retn = 0;
		for (; str[i] != ' ' && str[i] != 0; i++) {
			retn *= 10;
			retn += str[i] - '0';
		}
		if (str[i] == ' ') {
			i++;
		}
		return;
	}
	else {
		reto = true;
		if (str[i] == '+') {
			retn = 1;
		} else if (str[i] == '-') {
			retn = 2;
		} else if (str[i] == '*') {
			retn = 3;
		} else if (str[i] == '/') {
			retn = 4;
		}
		i += 2;
		return;
	}

}

int main() {
	while (gets_s(str)) {
		if (str[0] == '0' && str[1] == 0) {
			break;
		}
		bool retop;
		int retnum;
		int idx = 0;
		while (!op.empty()) {
			op.pop();
		}
		while (!digit.empty()) {
			digit.pop();
		}
		while (true) {
			getOp(retop, retnum, idx);
			if (retop == false) {
				digit.push((double)retnum);
			} 
			else {
				double tmp;
				if (op.empty() == true || mat[retnum][op.top()] == 1) {
					op.push(retnum);
				} 
				else {
					while (mat[retnum][op.top()] == 0) {
						int ret = op.top();
						op.pop();
						double b = digit.top();
						digit.pop();
						double a = digit.top();
						digit.pop();
						if (ret == 1) {
							tmp = a + b;
						} 
						else if (ret == 2) {
							tmp = a - b;
						} 
						else if (ret == 3) {
							tmp = a * b;
						} 
						else {
							tmp = a / b;
						}
						digit.push(tmp);
					}
					op.push(retnum);
				}

			}
			if (op.size() == 2 && op.top() == 0) {
				break;
			}
		}
		printf("%.2f\n", digit.top());
	}
	return 0;
}
```
