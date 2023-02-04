---
layout: page
title: Blogs
permalink: /blogs/
---

<ul>
  {% for post in site.posts %}
    {% if post.categories contains "blog" %}
      <li style="list-style-type: none;">
        Date: {{ post.date | date: "%-d %B %Y" }} -- Author: {{ post.author }} -- Link: <a href="{{ post.url }}">{{ post.url }}</a>
        {{ post.excerpt }}
      </li>
      <hr>
    {% endif %}
  {% endfor %}
</ul>


