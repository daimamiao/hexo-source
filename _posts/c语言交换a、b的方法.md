---
title: c语言交换a、b的方法
date: 2016-06-13 23:42:03
tags: [C语言, 算法]
categories: C语言
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/desk-notebook-office-grey.jpg
---
C语言中要实现两个变量值的交换一般而言可以分为两种方法：不引入中间变量和引入中间变量。具体代码如下：<!--more-->
## 常规方法
一般而言，在C语言中交换a、b两个值时，我们常用的是使用指针来交换。具体的代码如下：
```c
void swap(int *a ,int *b)	//通过指针交换两者的值
{
    int c;
    c = *a;
    *a = *b;
    *b= c;
}
```

## 通过异或来实现
除了上面的方法，还有一种更加简洁的办法如下：
```c
void swap(int &a,int &b)	//通过异或交换两者的值
{
    a =a^b;
    b= a^b;
    a = b^a;
}
```
