---
layout: page
title: Blog
permalink: /archive/
order: 2
---

{% raw %}{% for post in site.posts %}
<div class="post-preview">
  <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
  <p class="post-meta">{{ post.date | date: "%B %d, %Y" }}</p>
  {% if post.tags %}
  <p class="post-tags">
    Tags: 
    {% for tag in post.tags %}
      <span class="tag">{{ tag }}</span>
    {% endfor %}
  </p>
  {% endif %}
  {% if post.excerpt %}
  <p class="post-excerpt">{{ post.excerpt }}</p>
  {% endif %}
</div>
<hr>
{% endfor %}{% endraw %}
