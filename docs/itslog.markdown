---
layout: page
title: ITSlog
permalink: /itslog/
---

# IT-Security-Blog -- ITSLOG
Be carefull, links might contain malware and dangerous and malicious exploits. You are responsible yourself! if you find something malicious, plase let me know.

<ul>
  {% for post in site.posts %}
    {% if post.categories contains "miniblog" %}
      <div style="margin: 10px 5px; border:white outset">
      <li style="list-style-type: none;">
        Date: {{ post.date | date: "%-d %B %Y" }} -- Author: {{ post.author }} -- Link: <a href="{{ post.url }}">{{ post.url }}</a>
        {{ post.excerpt }}
      </li>
      </div>
    {% endif %}
  {% endfor %}
</ul>
