---
layout: default
title: Use-Case Index
permalink: /use-case
---

# All defined use cases

{% assign usecase_pages = site.pages | 
     where_exp: "page", "page.url contains '/use-case/'" | 
     sort: "title" %}

<ul>{% for page in usecase_pages %}
  <li><a href="{{ page.url }}">{{ page.title | default: page.name }}</a></li>{% endfor %}
</ul>
