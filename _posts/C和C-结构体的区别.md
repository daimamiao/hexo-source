---
title: C和C++结构体的区别
date: 2016-08-15 10:55:24
tags: [C, C++]
categories: C++
thumbnail:
---
最近在学习C++，发现它的结构体使用起来比C语言的结构体还要方便一些。具体的区别如下：

##### 1.C结构体变量定义时,若为`struct  结构体名 变量名`, `struct`不能省,而C++中则可以省去`struct`.

```c
// C
struct Node {
	int val;
	Node *next;
};
struct Node p; // 定义结构变量
struct Node *p1; // 定义结构指针
```
可以看到其中的struct都不可以省略，如果想要省略还需要加上`typedef`。
```c
// C
typedef struct Node {
	int val;
	Node *next;
}Node;
Node p; // 定义结构变量
Node *p1; // 定义结构指针
```
加上`typedef`之后，就可以直接声明变量了。然而在C++中是可以直接声明的。
```cpp
// C++
struct Node {
	int val;
	Node *next;
};
Node p; // 定义结构变量
Node *p1; // 定义结构指针
```
可以看到C++还是方便一些的。

##### 2.C 结构体中只能定义成员变量,而不能定义成员函数,.而C++结构体则可以有成员变量也可以定义成员函数.

##### 3.C 结构体中只能定义成员变量,而不能定义成员函数,.而C++结构体则可以有成员变量也可以定义成员函数.