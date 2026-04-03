---
layout: page
title: Blog
icon: fas fa-stream
order: 1
---

<div class="container">

  {% for post in site.posts %}

  <div class="card mb-4 shadow-sm border-0" style="border-radius: 12px; overflow: hidden;">
    <div class="d-flex flex-row">

      {% if post.image %}
      <div style="flex: 0 0 300px;">
        <img src="{{ post.image.path | relative_url }}"
             alt="{{ post.image.alt }}"
             style="height: 100%; width: 100%; object-fit: cover;">
      </div>
      {% endif %}

      <!-- ✅ Added spacing here -->
      <div class="p-4" style="flex: 1; margin-left: 15px;">

        <h4 class="mb-2">
          <a href="{{ post.url | relative_url }}" class="text-decoration-none text-dark">
            {{ post.title }}
          </a>
        </h4>

        <p class="mb-3 text-muted">
          {{ post.excerpt | strip_html | truncate: 130 }}
        </p>

        <!-- ✅ Read More Button -->
        <a href="{{ post.url | relative_url }}" class="btn btn-sm btn-primary">
          Read More →
        </a>

        <div class="mt-3">
          <small class="text-muted">
            {{ post.date | date: "%b %d, %Y" }}
          </small>
        </div>

      </div>

    </div>
  </div>

  {% endfor %}

</div>
