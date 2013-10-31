---
layout: page
title: 用jekyll搭建github主页
category: 技术
tags: github
---
{% include JB/setup %}

今天终于把github上个人主页搭建起来了。虽然视觉效果远谈不上华丽，但是对我个人来说已经足够了。以后就在这里用markdown写文章吧。
这里总结一下参考文档，做个记录。

#####理念
[http://www.yangzhiping.com/tech/writing-space.html](http://www.yangzhiping.com/tech/writing-space.html)

#####入口
[http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html)

#####官方教程(一步一步来，很好用)
[http://jekyllbootstrap.com/](http://jekyllbootstrap.com/)

#####参考
[http://yanping.me/cn/blog/2011/12/15/building-static-sites-with-jekyll/](http://yanping.me/cn/blog/2011/12/15/building-static-sites-with-jekyll/)

#####排查错误
[http://www.mceiba.com/develop/jekyll-introduction.html](http://www.mceiba.com/develop/jekyll-introduction.html)   
[http://chxt6896.github.io/blog/2012/02/13/blog-jekyll-native.html](http://chxt6896.github.io/blog/2012/02/13/blog-jekyll-native.html)

#####经验教训
######上传了文章之后，github却没有生效
查看邮箱，可能会受到build error的邮件。  
把代码下载到Linux，运行jekyll server，查看是否有报错，一般都是新增文章的markdown语法无法解析造成，修改语法，重新上传，搞定！
