---
layout: default
title: Capability Index
permalink: /capability
---

# All defined capabilities

{% assign capability_pages = site.pages | 
     where_exp: "page", "page.url contains '/capability/'" | 
     sort: "title" %}

<ul>{% for page in capability_pages %}
  <li><a href="{{ page.url }}">{{ page.title | default: page.name }}</a></li>{% endfor %}
</ul>
