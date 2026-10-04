---
layout: default
title: Home
---

# Hi, I’m jjgao.

This is a simple GitHub Pages blog.

## Latest posts

<ul>
{% for post in site.posts %}
  <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a> <span class="muted">{{ post.date | date: "%Y-%m-%d" }}</span></li>
{% endfor %}
</ul>
