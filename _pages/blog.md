---
layout: default
title: blog
---

<div class="post">

  {% assign blog_name_size = site.blog_name | size %}
  {% assign blog_description_size = site.blog_description | size %}

  {% if blog_name_size > 0 or blog_description_size > 0 %}
  <div class="header-bar">
    <h1>{{ site.blog_name }}</h1>
    <h2>{{ site.blog_description }}</h2>
  </div>
  {% endif %}

  <ol class="post-list">
    {% for post in site.posts %}
    <li>
      {% if post.redirect == blank %}
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      {% elsif post.redirect contains '://' %}
        <a href="{{ post.redirect }}" target="_blank">{{ post.title }}</a>
      {% else %}
        <a href="{{ post.redirect | relative_url }}">{{ post.title }}</a>
      {% endif %}
    </li>
    {% endfor %}
  </ol>

</div>