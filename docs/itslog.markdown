---
layout: page
title: ITSlog
permalink: /itslog/
---

<ul>
  {% for post in site.posts %}
    {% if post.categories contains "miniblog" %}
      <li>
        {{ post.excerpt }}
        Full Post here: <a href="{{ post.url }}">{{ post.url }}</a>
      </li>
      <hr>
    {% endif %}
  {% endfor %}
</ul>
