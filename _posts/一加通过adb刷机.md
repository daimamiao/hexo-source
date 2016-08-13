title: 一加通过adb刷机
tags:
  - Oneplus
  - Android
date: 2016-05-27 23:26:19
categories: Android
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/buzz.jpg
---
经常刷Android机的朋友应该知道刷机方法有两种：一种是线刷，另一种是卡刷。两种方式都十分简单。下面就两种方法分别介绍：<!--more-->
## 线刷包与卡刷包的区别
1.名字的不同
一般而言，名字中带有fastboot的都是线刷包

![Fastboot](http://static.oneplus.cn/data/attachment/forum/201407/21/182216ab5afo8abnabi7nf.png)

2.文件中的区别
卡刷包
![sdcard_file](http://static.oneplus.cn/data/attachment/forum/201407/21/175207d8fj4xx46jyijv4y.png.w_768.png)
线刷包
![usb_file](http://static.oneplus.cn/data/attachment/forum/201407/21/175205g4iopo48kdl4l7kd.png.w_768.png)

## adb 刷机

```bash
adb sideload rom.zip
```