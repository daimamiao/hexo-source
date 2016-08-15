---
title: git推送文件到github步骤
date: 2016-08-13 11:41:50
tags: Git
categories: Git
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/git.jpg
---
每次想用git推送文件到github时，总是忘记那几个命令，如果出错还不知道是怎么回事。所以在这里做个记录，方便下次翻阅。<!--more-->

### 推送到新的仓库
```bash
echo "# hexo-source" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:iamxcc/hexo-source.git
git push -u origin master
```
### 推送到已有仓库
```bash
git add .
git commit -m "first commit"
git remote add origin git@github.com:iamxcc/hexo-source.git
git push -u origin master
```
如果已经推送过了，那么可以省略`git remote add origin git@github.com:iamxcc/hexo-source.git`这句。