---
layout: page
title: It's time to escape
tagline: with me ...              jinbin
---
{% include JB/setup %}

## 文章列表

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

### 友情链接

<ul class="posts">
	<li>Weibo : <a href="http://weibo.com/jinbinforever" target="_BLANK">@金斌v</a></li>
	<li>Twitter : <a href="htttp://twitter.com/jinbinv" target="_BLANK">@jinbinv</a></li>
</ul>


