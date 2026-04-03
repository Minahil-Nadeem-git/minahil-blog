---
layout: page
title: Blog
icon: fas fa-stream
order: 1
---

<div class="container">
  {% for post in site.posts %}
    <div class="card mb-4">
      <div class="row g-0">

        {% if post.image %}
        <div class="col-md-4">
          <img src="{{ post.image.path }}" class="img-fluid h-100" style="object-fit: cover;" alt="{{ post.image.alt }}">
        </div>
        {% endif %}

        <div class="col-md-8">
          <div class="card-body">
            <h5 class="card-title">
              <a href="{{ post.url }}">{{ post.title }}</a>
            </h5>

            <p class="card-text">
              {{ post.excerpt | strip_html | truncate: 150 }}
            </p>

            <p class="card-text">
              <small class="text-muted">{{ post.date | date: "%b %d, %Y" }}</small>
            </p>
          </div>
        </div>

      </div>
    </div>
  {% endfor %}
</div>
