---
title: "Post about Date Structure"
layout: archive
permalink: /algoritms/datastructure
author_profile: true
sidebar_main: true
---

{% assign posts = site.algoritms.datastructure | sort:"date" %}

{% for post in posts %}
  {% include archive-single.html type=page.entries_layout %}
{% endfor %}
