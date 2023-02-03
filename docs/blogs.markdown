---
layout: page
title: Blogs
permalink: /blogs/
---

<ul>
  {% for post in site.posts %}
    {% if post.categories contains "blog" %}
      <li style="list-style-type: none;">
        {{ post.date }}  <a href="{{ post.url }}">{{ post.url }}</a>  Author: {{ post.author }}
        {{ post.excerpt }}
      </li>
      <hr>
    {% endif %}
  {% endfor %}
</ul>


