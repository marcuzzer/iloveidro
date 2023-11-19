---
layout: home  
title: Home
permalink: /de/
lang: de
---


{% for post in site.posts %}
  {% if post.path contains "/de/" %}
    {% include featured-post.html %}  
  {% endif %}
{% endfor %}
