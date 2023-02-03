---
layout: page
title: ITSlog
permalink: /itslog/
---

<ul>
  {% for post in site.posts %}
    {% if post.categories contains "miniblog" %}
      <li style="list-style-type: none;">
        {{ post.date | date: "%-d %B %Y" }} -- Link: <a href="{{ post.url }}">{{ post.url }}</a> -- Author: {{ post.author }}
        {{ post.excerpt }}
      </li>
      <hr>
    {% endif %}
  {% endfor %}
</ul>
