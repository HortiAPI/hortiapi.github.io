---
layout: default
title: horti-api/use-case
permalink: /resource/horti-api/use-case
---

# horti-api
## use-case

A [use case](/use-case) of HortiApi: one business scenario with its steps and the fields each step uses.

A server lists the use cases it supports in `useCases` of the [discovery](/use-case/discovery) document, one string per use case. Another party can define use cases of its own under its own name, for example `party-name/use-case:business-scenario`; those are not documented here.

Currently defined use cases
{% assign usecase_pages = site.pages | where_exp: "p", "p.url contains '/use-case/'" | sort: "title" %}{% for p in usecase_pages %}{% assign profile = site.data["use-case"][p.profile] %}{% if profile %}
- [`{{ profile.id }}`]({{ p.url }}) {{ profile.title }} ({{ profile.status }}){% endif %}{% endfor %}
