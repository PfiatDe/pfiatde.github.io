---
layout: page
title: Blogs
permalink: /blogs/
---

<ul>
  {% for post in site.posts %}
    {% if post.categories contains "blog" %}
      <li>
        {{ post.excerpt }}
        Full Post:<a href="{{ post.url }}">{{ post.url }}</a>
      </li>
    {% endif %}
  {% endfor %}
</ul>


