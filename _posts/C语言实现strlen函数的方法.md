---
title: C语言实现strlen函数的方法
date: 2016-08-05 21:42:17
tags: C语言
categories: C语言
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/Array-of-Characters-in-C.png
---
不使用中间变量求const字符串长度，即实现求字符串长度库函数strlen函数。函数接口声明如下：int strlen(const char *p)； <!--more-->
### 思路
在字符串中通常可以利用最后一个结束符’\0’，但此处参数为const，只读，那么我们不能打他的主意。
函数运行过程中不占用内存基本不可能，除非都使用了寄存器。“不使用中间变量”只是说程序员不能显示的申请内存而已，即不能有局部变量或者动态内存申请。如果函数自动申请栈内存或者使用寄存器存储变量，或者使用立即数寻址即常量，那么就相当于“不使用中间变量”。
从函数原型看，返回值为int，那么在函数内部必定需要一个地方存储这个值，要么是常数要么是寄存器。长度不为1时不能一次就求出来，说明必须有递归调用，这样递归时函数会自动申请栈内存，这样就相当于程序员“不使用中间变量”了。中间返回的值通过寄存器自动保存，最后一次返回时拷贝到int中去。
### 代码
```c
#include <stdio.h>
#include <string.h>
#include <assert.h>

int mStrlen(const char *str);
int mStrlen1(const char *str);
int mStrlen2(const char *str);

int main()
{
    char *str=NULL;
    str = "Hello Jay!";
    printf("original strlen():%d\n",strlen(str));
    printf("myStrlen():%d\n",myStrlen(str));
    printf("myStrlen1():%d\n",myStrlen1(str));
    printf("myStrlen2():%d\n",myStrlen2(str));
}

int mStrlen(const char *str)   // 不用中间变量，用递归实现，很容易看懂
{
    if ( (str == NULL) || (*str == '\0') ) {
        return 0;
    }
    else {
        return myStrlen(str+1)+1;
    }
}

int mStrlen1(const char *str)  // 不用中间变量，也是用递归实现，写得更简洁而已
{
    assert(str != NULL);
    return *str ? (myStrlen1(++str) + 1) : 0;
}

int mStrlen2(const char *str)  // 使用了一个int型变量
{
    if(str==NULL) return 0;
    int len = 0;
    for(; *str++ != '\0'; )
    {
        len++;
    }
    return len;
}
```