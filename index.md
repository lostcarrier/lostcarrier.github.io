8 -rw-r--r--   1 lostcarrier  staff   766 Oct 15 11:08 disqus.html
---
layout: default
---

<ul>
{% for post in site.categories.posts %}

<li>8 -rw-r--r--   1 {{ post.author }}  staff   766 {{ post.date | date: "%B %-d }} <a href="{{ post.url }}" title="{{ post.description }}">{{ post.title }}</a></li>

{% endfor %}
</ul>
