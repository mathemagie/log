---
layout: default
title: Accueil
---

## Articles

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      — <small>{{ post.date | date: "%d/%m/%Y" }}</small>
      {% for tag in post.tags %}<code>#{{ tag }}</code> {% endfor %}
    </li>
  {% endfor %}
</ul>