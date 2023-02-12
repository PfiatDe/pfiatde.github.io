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
        <img src = "/assets/svg/calendar-days-solid.svg" style="height: 1em;"/> {{ post.date | date: "%-d %B %Y" }} <img src = "/assets/svg/robot-solid.svg" style="height: 1em;"/> {{ post.author }} <img src = "/assets/svg/link-solid.svg" style="height: 1em;"/> <a href="{{ post.url }}">{{ post.url }}</a>
        {{ post.excerpt }}
      </li>
      </div>
    {% endif %}
  {% endfor %}
</ul>
