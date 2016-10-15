---
layout: default
---

<ul>
{% for post in site.categories.posts %}

<li>{{ post.author }} : {{ post.date | date: "%b %d" }} : <a href="{{ post.url }}" title="{{ post.description }}">{{ post.title }}</a></li>

{% endfor %}
</ul>

