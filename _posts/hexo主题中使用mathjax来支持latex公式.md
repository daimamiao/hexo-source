---
title: hexo主题中使用mathjax来支持LaTex公式
date: 2016-07-31 13:19:44
tags: [LaTex, hexo]
categories: hexo
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/latex_latin_symbols.jpg
---
今天发现在要写很多公式时，页面显示会有点乱。或者要表达一些复杂的符号时，发现不知道怎么写出来。<!--more-->后来上网查了一下发现有mathjax这个东西，实在好用。
### 使用步骤
因为mathjax这个js文件每次加载都有点慢，而且很多时候并用不到这个插件，所以我们的策略是按是否需要使用为前提而加载。而且如果哪天我们都不需要mathjax了，我们还要加上全局的控制的功能。所以为了实现上面的功能，我们需要修改几个文件。
#### 主题的_config.yml文件
在主题文件夹下的_config.yml中加入下面的代码，为了实现全局的控制，这里加上`enable: true`, false的话就会全站禁止了
``` yml
# ---------------------------------------------------------------
# Third Party Services Settings 
# ---------------------------------------------------------------

# MathJax Support
mathjax:
  enable: true
  cdn: http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML
```
上面的cdn觉得慢的话，可以自己找一个。
#### 按文章加载
在文章需要调用 Mathjax 时, 只需在 front-matter 前加上 mathjax: true 即可, 即
``` markdown
---
title: hexo主题中使用mathjax来支持LaTex公式
date: 2016-07-31 13:19:44
tags: [LaTex, hexo]
categories: hexo
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/latex_latin_symbols.jpg
mathjax: true
---
```
#### 加载mathjax文件
有了上面的修改，这时候就可以按需要加载mathjax脚本文件了。我主题加载js文件都是在script.ejs中判断后加载的(你们可以根据自己的情况来处理)，所以这里加上下面这段代码：
``` ejs
<% if (page.mathjax){ %>
	<%- partial('plugin/mathjax') %>
<% } %>
```
上面代码说明如果mardkown文件中写了上面说的`mathjax: ture`，那么if条件为ture，则加载`plugin/mathjax`
#### mathjax.ejs文件
``` javascript
<% if (theme.mathjax.enable){ %>
  <script type="text/x-mathjax-config">
    MathJax.Hub.Config({
      tex2jax: {
        inlineMath: [ ['$','$'], ["\\(","\\)"]  ],
        processEscapes: true,
        skipTags: ['script', 'noscript', 'style', 'textarea', 'pre', 'code']
      }
    });
  </script>

  <script type="text/x-mathjax-config">
    MathJax.Hub.Queue(function() {
      var all = MathJax.Hub.getAllJax(), i;
      for (i=0; i < all.length; i += 1) {
        all[i].SourceElement().parentNode.className += ' has-jax';
      }
    });
  </script>
  <script type="text/javascript" src="<%= theme.mathjax.cdn %>"></script>
<% } %>
```
可以看到代码中的`theme.mathjax.cdn`就是主题配置文件中的mathjax下的cdn啦。
### 说明
我的主题使用的是ejs模板语言写的，如果是swig或者其他语言，还要稍微修改一下，具体怎么改可以上网搜索一下。
下面放张效果图：
![Latex效果](http://7xveyh.com1.z0.glb.clouddn.com/sshot-2221.png)
