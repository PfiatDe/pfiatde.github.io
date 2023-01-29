---
layout: page
title: test
permalink: /test/
---


# IT Security Mini Blogposts


{% for tag in site.tags %}
  <h3>{{ tag[0] }}</h3>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}

# Categories

{% for categorie in site.categories %}
  <h3>{{ categorie[0] }}</h3>
  <ul>
    {% for post in categorie[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}