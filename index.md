---
layout: default
title: Home
---

<section class="hero">
  <p class="eyebrow">Hello</p>
  <h1>Hi, I’m jjgao.</h1>
  <p class="lede">A place for essays, trip writeups, and the occasional note.</p>
</section>

<section class="section-block">
  <div class="section-heading">
    <p class="eyebrow">Latest</p>
    <h2>Recent posts</h2>
  </div>
  <div class="post-grid">
    {% for post in site.posts limit: 6 %}
      {% include post-card.html post=post %}
    {% endfor %}
  </div>
</section>

<section class="section-block callout-row">
  <div>
    <p class="eyebrow">Archive</p>
    <h2>Want the full list?</h2>
    <p>Head to the archive for everything in one place.</p>
  </div>
  <a class="button" href="{{ '/archive/' | relative_url }}">Browse archive</a>
</section>
