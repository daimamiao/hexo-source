---
title: Win10上使用Mactype
date: 2016-07-26 10:21:47
categories: Mactype
tags: [Mactype, Win10]
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/0d49052fd8609b99b2d99f8a7795a86d.png
---
由于window系统上字体渲染很不舒服，故我一直使用mactype来改善一下。但是升级到win10后发现一打开mactype就出现黑屏或者打开界面显示有问题。<!--more-->后面查了一些教程后发现在win10上还需要做一些文件替换。下面是教程：
## 安装
首先，安装mactype，到网上随便找一个下载即可。这里提供了百度网盘的下载路径 [Mactype](http://pan.baidu.com/s/1qYUv0Hu)。安装的话没什么需要特别注意的。
## 文件替换
安装完成后，先不要打开mactype否则可能会出现黑屏等等问题。先打开mactype的安装目录，像我是在`C:\Program Files (x86)\MacType`这里，这时候用`EasyHk32.dll`、`EasyHk64.dll`、`MacType.dll`、`MacType64.dll`文件替换掉mactype安装目录下的对应文件。替换文件在刚刚提供的百度网盘里面有。此时打开mactype再设置一番就大功告成了。下面是效果图：
![使用mactype前](http://7xveyh.com1.z0.glb.clouddn.com/QQ%E6%88%AA%E5%9B%BE20160726104637.png)
![使用mactype后](http://7xveyh.com1.z0.glb.clouddn.com/QQ%E6%88%AA%E5%9B%BE20160726104706.png)
可以看到效果还是十分明显的，mactype加载方式我是使用兼容加载的，用注册表加载可能很方便但是会导致较慢的开机速度。

