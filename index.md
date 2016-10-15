---
layout: default
---

# $ cat about.txt
{:id="about"}

# $ cat contact.txt
{:id="contact"}

# $ cat projects.txt
{:id="projects"}

<ul>
{% for project in site.categories.projects %}
<li><a href="{{ project.link }}">{{ project.title }}</a> - {{ project.description }}</li>
{% endfor %}
</ul>

# $ cat posts.txt
{:id="posts"}

<ul>
{% for post in site.categories.posts %}

<li>{{ post.title }} :: <a href="{{ post.url }}" title="{{ post.description }}">en</a></li>

{% endfor %}
</ul>

