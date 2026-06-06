---
layout: default
title: Accueil
---

Bienvenue sur **Mathemagie Blog** — articles techniques sur l'IA, les LLM
et les workflows de développement assisté par agents.

## Articles

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      — <small>{{ post.date | date: "%d/%m/%Y" }}</small>
    </li>
  {% endfor %}
</ul>

<p><a href="{{ '/about/' | relative_url }}">À propos</a></p>
