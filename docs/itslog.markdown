---
layout: page
title: ITSlog
permalink: /itslog/
---

<ul>
  {% for post in site.posts %}
    {% if post.categories contains "miniblog" %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a>
        {{ post.excerpt }}
      </li>
    {% endif %}
  {% endfor %}
</ul>

