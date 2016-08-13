---
title: 通信协议之Http
date: 2016-06-16 10:54:50
tags: [HTTP, 通信协议]
categories: HTTP
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/http.png
---

生活中我们接触的比较多的通信协议有HTTP、TCP、UDP等等。特别是HTTP协议，因为我们每天上网在浏览器中<!--more-->输入的网址基本都可以看到以`http://`开头的字符串。那么什么是通信协议呢？简而言之就是通信时所遵守的规则，只有双方按照这个规则“说话”，对方才能理解或为之服务。这里只是很口语化的解释，详细的解释可以到这里查看： [百度百科](http://baike.baidu.com/link?url=P27xXVhoV-DcTkvSD2ne3Q0nkKPEik_7S-iblr0Jn-s1ZzLCpub1FUMBwUSEJKVqI0wAI-FVJiqBp2gSXp17na) [维基百科](https://zh.wikipedia.org/wiki/%E7%BD%91%E7%BB%9C%E4%BC%A0%E8%BE%93%E5%8D%8F%E8%AE%AE)

### HTTP、TCP、UDP的区别
TCP/IP是个协议组，可分为四个层次：网络接口层、网络层、传输层和应用层。
* 在网络层有IP协议、ICMP协议、ARP协议、RARP协议和BOOTP协议。
* 在传输层中有TCP协议与UDP协议。
* 在应用层有FTP、HTTP、TELNET、SMTP、DNS等协议。
因此，HTTP本身就是一个协议，是从Web服务器传输超文本到本地浏览器的传送协议。

### 什么是HTTP协议
HTTP全称是HyperText Transfer Protocal，即：超文本传输协议，从1990年开始就在WWW上广泛应用，是现今在WWW上应用最多的协议，    Http是应用层协议，当你上网浏览网页的时候，浏览器和Web服务器之间就会通过HTTP在Internet上进行数据的发送和接收。Http是一个基于请求/响应模式的、无状态的协议。即我们通常所说的`Request/Response`。

### URL
URL(Uniform Resource Locator) 地址用于描述一个网络上的资源,  基本格式如下
```
schema://host[:port#]/path/.../[?query-string][#anchor]

scheme			指定低层使用的协议(例如：http, https, ftp)
host            	HTTP服务器的IP地址或者域名
port#                   HTTP服务器的默认端口是80，这种情况下端口号可以省略。如果使用了别的端口，必须指明，例如 http://www.cnblogs.com:8080/
path                    访问资源的路径
query-string            发送给http服务器的数据
anchor-                 锚
```

URL 的一个例子
```
http://www.mywebsite.com/sj/test/test.aspx?name=sviergn&x=true#stuff

Schema:                 http
host:                   www.mywebsite.com
path:                   /sj/test/test.aspx
Query String:           name=sviergn&x=true
Anchor:                 stuff
```

### HTTP的Request/Response
先看Request 消息的结构,Request消息分为3部分
* 第一部分叫Request line。
* 第二部分叫Request header。
* 第三部分是body. header和body之间有个空行。

![Request图](http://ww1.sinaimg.cn/mw690/6941baebtw1epet82gukfj20in0kfn2r.jpg)

第一行中的Method表示请求方法,比如”POST”,”GET”,  Path-to-resoure表示请求的资源， Http/version-number 表示HTTP协议的版本号
当使用的是”GET” 方法的时候， body是为空的比如我们打开博客园首页的request 如下
GET http://www.cnblogs.com/ HTTP/1.1
Host: www.cnblogs.com
抽象的东西，难以理解，老感觉是虚的， 所谓眼见为实, 实际见到的东西，我们才能理解和记忆。 我们今天用Fiddler，实际的看看Request和Response.下面我们打开Fiddler 捕捉一个博客园登录的Request 然后分析下它的结构, 在Inspectors tab下以Raw的方式可以看到完整的Request的消息。如下图：
![Request示例图](http://ww1.sinaimg.cn/mw690/6941baebtw1epet82gukfj20in0kfn2r.jpg)
