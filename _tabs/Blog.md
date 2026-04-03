---
layout: page
title: Blog
icon: fas fa-stream
order: 1
---

<div class="container">
  {% for post in site.posts %}
    <div class="card mb-4 shadow-sm">

      <div class="row g-0 align-items-center">

        {% if post.image %}
        <div class="col-md-4">
          <img src="{{ post.image.path | relative_url }}"
               class="img-fluid rounded-start"
               style="height: 200px; width: 100%; object-fit: cover;"
               alt="{{ post.image.alt }}">
        </div>
        {% endif %}

        <div class="col-md-8">
          <div class="card-body">

            <h5 class="card-title">
              <a href="{{ post.url | relative_url }}" class="text-decoration-none">
                {{ post.title }}
              </a>
            </h5>

            <p class="card-text">
              {{ post.excerpt | strip_html | truncate: 120 }}
            </p>

            <p class="card-text">
              <small class="text-muted">
                {{ post.date | date: "%b %d, %Y" }}
              </small>
            </p>

          </div>
        </div>

      </div>

    </div>
  {% endfor %}
</div>
