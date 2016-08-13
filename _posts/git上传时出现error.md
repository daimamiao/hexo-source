---
title: Git上传时出现error
date: 2016-07-27 13:24:55
tags: Git
categories: Git
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/338398_7fde_6.jpg
---
今天使用git上传文件到github上时出现错误，提示是`error: src refspec master does not match any`，后来上网查了一下，问题解决了。<!--more-->为了防止以后再遇到类似问题又给忘记了，所以还是把这个方法简单记录在此。
### git工作大致流程
> 1、在github上创建项目
  2、使用git clone https://github.com/xxxxxxx/xxxxx.git克隆到本地
  3、编辑项目
  4、git add . （将改动添加到暂存区）
  5、git commit -m "提交说明"
  6、git push origin master 将本地更改推送到远程master分支。

这样你就完成了向远程仓库的推送。
### 解决措施
如果在github的remote上已经有了文件，会出现错误。此时应当先pull一下，即：
```git
	git pull origin master
```
然后再进行：
```git
git push origin master
```
这样就不会出现错误提示了。