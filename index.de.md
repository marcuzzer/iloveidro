---
layout: home  
title: Home
permalink: /de/
lang: de
---
file tedesco: {% page.lang %}

{% assign lang_folder = page.lang %}
{% for post in site.posts %}
  {% if post.path contains lang_folder %}
   {% include featured-post.html %}  
  {% endif %}
{% endfor %}
