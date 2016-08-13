---
title: Win下Sublime3美化
date: 2016-07-26 19:20:15
tags: [Sublime, Win10]
categories: Sublime
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/4db1efeb44fd6fb00332a28f3228db7eefc0769e.gif
---
虽然sublime3没有atom的高颜值，但是稍微美化一下也是上得了台面的，再加上极快的启动速度，简直是我心中的神器。<!--more-->
### 主题美化
使用过很多sublime3的主题，最后在laracasts视频中发现了一款十分漂亮的主题[Material Theme](https://packagecontrol.io/packages/Material%20Theme)。
废话不多说，下面是教程：首先在sublime中`Ctrl+Shift+p`出现一个输入面板，再在面板上输入`install package`确认后再次出现一个面板，此时输入`Material theme`确认后等待安装即可。安装完成后在`Preference->Setting-User`中输入一下代码：
```
"color_scheme": "Packages/Material Theme/schemes/Material-Theme.tmTheme",
"theme": "Material-Theme.sublime-theme",
```
最后再重启一下即可。
![Material Theme 主题](http://7xveyh.com1.z0.glb.clouddn.com/3-1024x618.png)
当然这个主题还有一些其他的设置，想要更详细的设置请看官网 [PackageControl](https://packagecontrol.io/packages/Material%20Theme)	
### 编程字体的选择
曾经有段时间我不断在寻找最舒服的编程字体，包括什么`Source Code Pro`、`DeJaVu Sans Mono`、`Droid Sans Mono`、`CamingoCode`、`Courier New`等等，但是都不太满意。比如`Source Code Pro`中`i`的头尖尖的看着让我感到别扭。其他几种各有各的缺点。最后终于发现了`Fira Code`，这是Firefox设计的一款字体。废话不多说上图说明：
![Fira Code 字体](http://7xveyh.com1.z0.glb.clouddn.com/sshot-111.png)
