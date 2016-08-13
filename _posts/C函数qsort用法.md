---
title: C函数qsort的用法
date: 2016-07-30 15:37:31
tags: C语言
categories: C语言
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/qsort2.png
---
qsort()函数是ANSI C标准中提供的，其声明在stdlib.h文件中，是根据二分发写的，其时间复杂度为n*log(n)。<!--more-->为了了解
### 排序方式
排序方式有很多种，比如：选择排序、冒泡排序、归并排序、快速排序等等。顾名思义快速排序是目前公认的一种比较好的排序算法，其比选择排序、冒泡排序都要快。因为它的速度很快，所以系统也在库里实现这个算法，便于我们使用，这个函数就是qsort了。
### qsort简介
qsort的函数原型是:
```c
void qsort(void* base, size_t nelem, size_t width, cmp)
```
其中：
1. *base为要排序的数组
2. nelem为要排序的数组的长度
3. width为每个数组元素的大小(以字节为单位)
4. cmp为自己定义的比较函数，其作用在于方便使用者实现对数组、字符串、结构体等结构进行升序或降序排列。

### cmp函数
```c
int cmp(const void *a, const void *b)
```
cmp函数中有两个元素作为参数，返回一个int值，如果比较函数返回大于0，qsort就认为a>b；如果返回等于0，qsort就认为a=b；如果返回小于0，qsort就认为a小于b。
因此，qsort函数知道元素大小，就可以把大的放到前面去。
如果你把cmp函数的返回值1与-1的位置调换，那么就造成了升降序的差别了。
### 实例操作
为了加深理解，下面以数组、字符串、结构体为例说明情况
#### 对int数组进行排序
```c
int nums[100];
int cmp ( const void *a , const void *b ){ 
	return *(int *)a - *(int *)b; 
}
qsort(num,100,sizeof(num[0]),cmp);
```
#### 对char类型数组排序
```c
char word[100];
int cmp( const void *a , const void *b ){ 
	return *(char *)a - *(int *)b;
}
qsort(word,100,sizeof(word[0]),cmp);
```
#### 对double类型数组排序
```c
double nums[100];
int cmp( const void *a , const void *b ){ 
	return *(double *)a - *(double *)b;
}
qsort(nums,100,sizeof(nums[0]),cmp);
```
### 对结构体类型排序
```c
struct Node{ 
	double data; 
	int other; 
}s[100]

//按照data的值从小到大将结构体排序,关于结构体内的排序关键数据data的类型可以很多种，
//参考上面的例子写
int cmp( const void *a ,const void *b){ 
	return (*(Node *)a).data - (*(Node *)b).data ? 1 : -1; 
}
qsort(s,100,sizeof(s[0]),cmp);
```
#### 对结构体二级排序
```c
struct Node{ 
	int x; 
	int y; 
}s[100];

//按照x从小到大排序，当x相等时按照y从大到小排序
int cmp( const void *a , const void *b ){
	struct Node *c = (Node *)a; 
	struct Node *d = (Node *)b;
	if(c->x != d->x)
		return c->x - d->x;
	else
		return d->y - c->y;
}
qsort(s,100,sizeof(s[0]),cmp);
```
#### 对字符串进行排序
```c
struct Node { 
	int data; 
	char str[100]; 
}s[100];

//按照结构体中字符串str的字典顺序排序
int cmp ( const void *a , const void *b ){
	return strcmp( (*(Node *)a)->str , (*(Node *)b)->str );
}
qsort(s,100,sizeof(s[0]),cmp);
```