---
layout: default
---

# % cat projects.txt
{:id="projects"}

<ul>
{% for project in site.categories.projects %}
<li><a href="{{ project.link }}">{{ project.title }}</a> - {{ project.description }}</li>
{% endfor %}
</ul>

# % cat posts.txt
{:id="posts"}

<ul>
{% for post in site.categories.posts %}

<li>{{ post.date }} :: <a href="{{ post.url }}" title="{{ post.description }}">{{ post.title }}</a></li>

{% endfor %}
</ul>
