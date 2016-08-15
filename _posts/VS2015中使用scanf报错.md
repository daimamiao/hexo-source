---
title: VS2015中使用scanf报错
date: 2016-08-14 18:30:48
tags: [VS2015, IDE]
categories: VS2015
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/VS2015.png
---
今天使用VS2015编译C文件时，发现scanf报错了，提示我们使用scanf_s替代scanf。如果我们坚持要使用scanf，那怎么办呢？ <!--more-->

### 解决办法

1. 方法一：在程序最前面加#define _CRT_SECURE_NO_DEPRECATE；

2. 方法二：在程序最前面加#define _CRT_SECURE_NO_WARNINGS；

3. 方法三：在程序最前面加#pragma warning(disable:4996)；

4. 方法四：把scanf改为scanf_s；

5. 方法五：无需在程序最前面加那行代码，只需在新建项目时取消勾选“SDL检查”即可；

6. 方法六：若项目已建立好，在项目属性里关闭SDL也行；