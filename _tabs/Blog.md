---
layout: page
title: Blog
icon: fas fa-stream
order: 1
---

<div class="container">

  {% for post in site.posts %}

  <div class="card mb-4 shadow-sm border-0">
    <div class="d-flex flex-row">

      {% if post.image %}
      <div style="flex: 0 0 300px;">
        <img src="{{ post.image.path | relative_url }}"
             alt="{{ post.image.alt }}"
             style="height: 100%; width: 100%; object-fit: cover; border-radius: 10px 0 0 10px;">
      </div>
      {% endif %}

      <div class="p-3" style="flex: 1;">

        <h4 class="mb-2">
          <a href="{{ post.url | relative_url }}" class="text-decoration-none text-dark">
            {{ post.title }}
          </a>
        </h4>

        <p class="mb-2 text-muted">
          {{ post.excerpt | strip_html | truncate: 130 }}
        </p>

        <!-- ✅ Read More Button -->
        <a href="{{ post.url | relative_url }}" class="btn btn-sm btn-primary mt-2">
          Read More →
        </a>

        <br>

        <small class="text-muted">
          {{ post.date | date: "%b %d, %Y" }}
        </small>

      </div>

    </div>
  </div>

  {% endfor %}

</div>
