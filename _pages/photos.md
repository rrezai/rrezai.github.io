---
layout: page
title: photos
permalink: /photos/
description: A growing collection of your cool photos.
nav: true
nav_order: 3
display_categories: [work, fun]
horizontal: false
---

<!-- pages/photos.md -->
<div class="photos">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized photos -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_photos = site.photos | where: "category", category %}
  {% assign sorted_photos = categorized_photos | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_photos %}
      {% include photos_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_photos %}
      {% include photos.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display photos without categories -->

{% assign sorted_photos = site.photos | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_photos %}
      {% include photos_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_photos %}
      {% include photos.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
