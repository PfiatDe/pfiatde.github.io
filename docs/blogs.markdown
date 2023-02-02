---
layout: page
title: Blogs
permalink: /blogs/
---

<ul>
  {% for post in site.posts %}
    {% if post.categories contains "blog" %}
      <li>
        <h1>{{ post.title }}</h1>
        <a href="{{ post.url }}">{{ post.url }}</a>
        {{ post.excerpt }}
      </li>
    {% endif %}
  {% endfor %}
</ul>


