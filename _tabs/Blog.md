---
layout: page
title: Blog
icon: fas fa-stream
order: 1
---

<div class="row">
  {% for post in site.posts %}
    <div class="col-12 col-md-6 col-lg-4">
      <div class="card mb-4">

        {% if post.image %}
        <img src="{{ post.image.path }}" class="card-img-top" alt="{{ post.image.alt }}">
        {% endif %}

        <div class="card-body">
          <h5 class="card-title">
            <a href="{{ post.url }}">{{ post.title }}</a>
          </h5>

          <p class="card-text">
            {{ post.excerpt | strip_html | truncate: 120 }}
          </p>

        </div>
      </div>
    </div>
  {% endfor %}
</div>
