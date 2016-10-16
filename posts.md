---
layout: default
title: Posts
permalink: /posts/
---

<ul>
{% for post in site.categories.posts %}
<li>{{ post.date | date: "%b %d" }} <a href="{{ post.url }}" title="{{ post.description }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
