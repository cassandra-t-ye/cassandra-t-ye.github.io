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

  <!-- Debug: Let's see if we have any posts -->
  <p>Total posts found: {{ site.posts | size }}</p>
  
  <ol class="post-list">
    {% for post in site.posts %}
    <li>
      <strong>{{ post.title | default: "No Title" }}</strong> - 
      Date: {{ post.date | date: "%Y-%m-%d" }} - 
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
  
  <!-- If no posts show up above, let's try a different approach -->
  {% if site.posts.size == 0 %}
  <p>No posts found. Checking _posts directory...</p>
  {% endif %}

</div>