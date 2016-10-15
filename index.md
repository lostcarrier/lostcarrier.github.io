---
layout: default
---

<ul>
{% for post in site.categories.posts %}

<li>-rw-r--r--  1 lostcarrier  staff 12345 {{ post.date | date: "%B %d" }} <a href="{{ post.url }}" title="{{ post.description }}">{{ post.title }}</a></li>

{% endfor %}
</ul>
