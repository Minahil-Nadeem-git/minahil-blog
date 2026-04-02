---
title: Blog
icon: fas fa-book
order: 4
layout: page
permalink: /blog/
---

{% for post in site.posts %}
- [{{ post.title }}]({{ post.url }})
{% endfor %}
