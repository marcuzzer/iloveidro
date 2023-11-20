---
layout: home  
title: Home
permalink: /en/
lang: en
---


{% for post in site.posts %}
  {% if post.path contains "/en/" %}
post.path <BR><BR><BR><BR> {{ post.path }} <BR><BR><BR><BR><BR><BR><BR><BR><BR><BR><BR><BR><BR>

  
    {% include featured-post.html %}  
  {% endif %}
{% endfor %}
