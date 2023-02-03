---
layout: page
title: ITSlog
permalink: /itslog/
---

<ul>
  {% for post in site.posts %}
    {% if post.categories contains "miniblog" %}
      <li style="list-style-type: none;">
        {{ post.date }}  <a href="{{ post.url }}">{{ post.url }}  Author: {{ post.author }}
        {{ post.excerpt }}
      </li>
      <hr>
    {% endif %}
  {% endfor %}
</ul>
