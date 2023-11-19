---
layout: default  
title: "Home"
permalink: /en/
lang: en
---


{% for post in site.posts %}
  {% if post.path contains "/en/" %}
    {% include featured-post.html %}  
  {% endif %}
{% endfor %}
