---
layout: default
title: Archive
permalink: /archive/
---

<section class="page-intro">
  <p class="eyebrow">Archive</p>
  <h1>All posts</h1>
  <p class="lede">A complete list of everything published here.</p>
</section>

<section class="section-block">
  <div class="post-list">
    {% assign last_year = "" %}
    {% for post in site.posts %}
      {% assign y = post.date | date: "%Y" %}
      {% if y != last_year %}
        <h2 class="archive-year">{{ y }}</h2>
        {% assign last_year = y %}
      {% endif %}
      <a class="post-list-item" href="{{ post.url | relative_url }}">
        <span class="post-list-date">{{ post.date | date: "%Y-%m-%d" }}</span>
        <span class="post-list-title">{{ post.title }}</span>
      </a>
    {% endfor %}
  </div>
</section>
