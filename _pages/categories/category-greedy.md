---
title: "Post about Greedy"
layout: archive
permalink: /categories/greedy
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.greedy| sort:"date" %}

{% for post in posts %}
  {% include archive-single.html type=page.entries_layout %}
{% endfor %}

