---
title: Git命令add和commit的区别
date: 2016-07-27 08:42:34
tags: Git
categories: Git 
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/57c83535399791a07f83e3ad9782fcab.png
---
要想弄明白`git add`和`git commit`的区别，首先我们需要知道三个概念：`工作区(Working Directory)`、`版本库(Repository)`、`暂存区(Stage or index)`。<!--more-->
#### 工作区
当你在开发一个项目时，主目录就是你的工作区。
#### 版本库
工作区中有一个隐藏目录`.git`，这个就是git的版本库了。
#### 暂存区
Git的版本库里存了很多文件，其中包括称为Stage或index的暂存区，还有一个git为我们自动创建的第一个分支`master`，以及指向`master`的一个指针`HEAD`。
下面就是三个区的示意图：图片来着廖雪峰老师的 [博客](http://www.liaoxuefeng.com)。
![三个区的示意图](http://7xveyh.com1.z0.glb.clouddn.com/0.jpg)
#### 区别
`git add`和`git commit`的区别就在于：
`git add`把文件添加进去，实际上就是把文件修改添加到暂存区；
`git commit`提交更改，实际上就是把暂存区的所有内容提交到当前分支。
因为我们创建Git版本库时，Git自动为我们创建了唯一一个master分支。所以，git commit就是往master分支上提交更改。
你可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。

所以要想将修改提交到master中一定要先`git add`到暂存区中，再`git commit`到master分支。