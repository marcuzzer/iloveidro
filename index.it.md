---
layout: default
title: Home
permalink: /it/
lang: it
---

{% for post in site.posts %}
  {% if post.path contains '/it/' %}
    {% include featured-post.html %}
  {% endif %}
{% endfor %}
