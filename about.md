---
layout: default
title: About
permalink: /about/
---

<section class="page-intro">
  <p class="eyebrow">About</p>
  <h1>A personal blog for essays, trip writeups, and notes.</h1>
  <p class="lede">Mostly about things I wanted to remember, explain, or share with a little more polish.</p>
</section>

<section class="section-block">
  <div class="section-heading">
    <p class="eyebrow">Recent posts</p>
    <h2>What’s here now</h2>
  </div>
  <div class="post-grid">
    {% for post in site.posts limit: 3 %}
      {% include post-card.html post=post %}
    {% endfor %}
  </div>
</section>
