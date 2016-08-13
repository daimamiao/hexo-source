---
title: Chrome52中Mactype无效怎么回退版本
date: 2016-08-10 10:18:59
tags: [Mactype, Chrome, Win10]
categories: [Mactype]
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/c607f818657741d740da284d822d73fe_b.jpg
---
今天在chrome自动更新到523版本后，突然被chrome上显示的字体吓了一下，还以为什么坏了。后来才发现是mactype无效了，因为Chrome52后禁用DirectWrite渲染的选项已经没有了。<!--more--> 

没有办法只能去找各种各样的解决办法，先是试了stylish的方式，效果不明显。后来又去找mactype有没有新的版本。一直折腾了好久后，终于下定决心把chrome回退到上一个版本。 

可是怎么回退呢？卸载掉再重新装吗？
答案是不用这么麻烦。下面是解决办法，来自知乎 [Dorawei](https://www.zhihu.com/people/zhen-ming-36-24)：
C:\Program Files (x86)\Google\Chrome\Temp\ 下的一个文件夹中有old_chrome.exe，把它复制到C:\Program Files (x86)\Google\Chrome\Application 中改为 chrome.exe 就可以返回上一版了。
