---
layout: default  # The layout file to use. Ensure you have a 'default' layout or use another layout that exists in your _layouts directory.
title: Home  # Title of your webpage
permalink: /en/  # URL for this page, '/en/' will make this page accessible at 'www.yoursite.com/en/'
lang: en  # Language identifier
---

{% for post in site.posts %}
  {% if post.path contains '/en/' %}
    {% include featured-post.html %}  # Assuming you have a file '_includes/featured-post.html' to format how posts are displayed.
  {% endif %}
{% endfor %}
