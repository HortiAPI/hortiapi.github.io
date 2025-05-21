---
layout: default
title: Resource Index
permalink: /resources/
---

# All resources

{% assign resource_docs = site.docs
   | where_exp: "doc", "doc.url contains '/resources/'" %}

<ul>
  {% for doc in resource_docs %}
    <li><a href="{{ doc.url }}">{{ doc.title }}</a></li>
  {% endfor %}
</ul>
