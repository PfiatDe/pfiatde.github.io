---
layout: page
title: Blogs
permalink: /blogs/
---

<ul>
  {% for post in site.posts %}
    {% if post.categories contains "blog" %}
      <li style="list-style-type: none;">
        {{ post.excerpt }}
        Full Post here: <a href="{{ post.url }}">{{ post.url }}</a>
      </li>
      <hr>
    {% endif %}
  {% endfor %}
</ul>


