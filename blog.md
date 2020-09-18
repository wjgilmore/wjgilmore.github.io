---
layout: page
title: Blog
---

<ul>
  {% for post in site.posts %}
    {% if post.published == true %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
    {% endif %}
  {% endfor %}
</ul>