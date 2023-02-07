---
layout: page
title: Blogs
permalink: /blogs/
---

<ul>
  {% for post in site.posts %}
    {% if post.categories contains "blog" %}
    <div style="margin: 0px 10px 0px 10px">
      <li style="list-style-type: none;">
        Date: {{ post.date | date: "%-d %B %Y" }} -- Author: {{ post.author }} -- Link: <a href="{{ post.url }}">{{ post.url }}</a>
        {{ post.excerpt }}
      </li>
      <div>
      <hr>
    {% endif %}
  {% endfor %}
</ul>


