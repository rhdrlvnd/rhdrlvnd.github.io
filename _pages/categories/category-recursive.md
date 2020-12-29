---
title: "Post about Recursive"
layout: archive
permalink: /categories/recursive
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.recursive| sort:"date" %}

{% for post in posts %}
  {% include archive-single.html type=page.entries_layout %}
{% endfor %}

