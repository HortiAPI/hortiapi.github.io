---
layout: default
title: Error Index
permalink: /error
---

# All errors

{% assign error_pages = site.pages | 
     where_exp: "page", "page.url contains '/error/'" | 
     sort: "title" %}

<ul>{% for page in error_pages %}
  <li><a href="{{ page.url }}">{{ page.title | default: page.name }}</a></li>{% endfor %}
</ul>
