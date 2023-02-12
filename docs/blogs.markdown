---
layout: page
title: Blogs
permalink: /blogs/
---

<ul>
  {% for post in site.posts %}
    {% if post.categories contains "blog" %}
    <div style="margin: 10px 5px; border:white outset">
      <li style="list-style-type: none;">
        <img src = "/assets/svg/calendar-days-solid.svg" style="height: 1em;"/> {{ post.date | date: "%-d %B %Y" }}  &emsp;<img src = "/assets/svg/robot-solid.svg" style="height: 1em;"/> {{ post.author }}  &emsp;<img src = "/assets/svg/link-solid.svg" style="height: 1em;"/> <a href="{{ post.url }}">{{ post.url }}</a>
        {{ post.excerpt }}
      </li>
      </div>
    {% endif %}
  {% endfor %}
</ul>


