---
title: wampserver配置多站点
date: 2016-06-14 12:54:06
tags: [Wampserver, Wordpress]
categories: Wampserver
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/19b0f58e42efb956a1dab2c171adfe98.jpg
---
一般而言，当我们在本地调试网站时都会有多个站点。这时候为了方便区分各个网站，就需要设置多站点，即给每个站点取一个网址。<!--more-->当然，这个网址只能在本地打开。这里，就介绍一下wampserver在win10下怎么设置多站点。
### 修改wampserver配置文件
在`wampserver安装位置\bin\apache\apache\apache2.4.17\conf\httpd.conf`文件中查找`Include conf/extra/httpd-vhosts.conf`，去掉前面的注释#。打开`wampserver安装位置\bin\apache\apache\apache2.4.17\conf\extra/httpd-vhosts.conf`文件；在最后加入类似内容：（文件路径是自己安装程序的路径）

```html
<VirtualHost *:80>
	DocumentRoot "D:/wamp/www/blog"(这是你放程序的文件路径)
	ServerName www.yoursite.com   （这是自己定义的域名）
</VirtualHost>
```

### 修改windows下的hosts文件
通过`win+R`在run下输入drivers，打开`etc\hosts`文件，在最后加入`127.0.0.1  www.yoursite.com （这是自己定义的域名）`

### 结论

```apache
# localhost name resolution is handled within DNS itself.
#	127.0.0.1       localhost
#	::1             localhost

127.0.0.1       blog.iamxcc.com
127.0.0.1       www.sf.com
```
以上是我的hosts文件内容，可以看出我定义了两个站点一个是`blog.iamxcc.com`, 另一个是`www.sf.com`。

```html
<VirtualHost *:80>
    DocumentRoot "D:\Web\wamp64\www\my-site\blog"
    ServerName blog.iamxcc.com
</VirtualHost>

<VirtualHost *:80>
    DocumentRoot "D:\Web\wamp64\www\my-site\sf"
    ServerName www.sf.com
</VirtualHost>
```
其中`blog.iamxcc.com`指向位于`D:\Web\wamp64\www\my-site\blog`下的站点，`www.sf.com`指向`D:\Web\wamp64\www\my-site\blog`下的站点。
到此为止，wampserver配置多任务已经成功。