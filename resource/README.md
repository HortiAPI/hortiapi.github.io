---
layout: default
title: Resource Index
permalink: /resource
---

# All defined resources

A resource is written as a resource string, for example `order/state:draft`. See [resource strings](/resource-string) for how such a text is built and how to compare it.

{% assign error_pages = site.pages | 
     where_exp: "page", "page.url contains '/resource/'" | 
     sort: "title" %}

<ul>{% for page in error_pages %}
  <li><a href="{{ page.url }}">{{ page.title | default: page.name }}</a></li>{% endfor %}
</ul>
