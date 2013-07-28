---
layout: page
title: 我们的征途是星辰大海
tagline: It's time ...
---
{% include JB/setup %}

## 文章列表

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

#### 友情链接

<ul class="posts">
	<li>Weibo : <a href="http://weibo.com/jinbinforever" target="_BLANK">@金斌v</a></li>
	<li>Twitter : <a href="htttp://twitter.com/jinbinv" target="_BLANK">@jinbinv</a></li>
	<li>Github : <a href="http://github.com/jinbin" target="_BLANK">jinbin</a></li>
</ul>

#### About Me
<ul class="posts">
	<li>Email: bin.jinb@qq.com</li>
</ul>
