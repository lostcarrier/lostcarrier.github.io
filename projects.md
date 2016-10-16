---
layout: default
title: Projects
permalink: /projects/
---
<h1>Projects</h1>
<ul>
{% for post in site.categories.projects %}
<li>{{ post.date | date: "%b %d" }} <a href="{{ post.url }}" title="{{ post.description }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
