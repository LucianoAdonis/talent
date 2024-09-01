---
layout: custom
title: Series
description: Whatever is not an anime
---

<div class="gallery-container">
  {% for image in site.static_files %}
    {% if image.path contains '/assets/images/series/' %}
      <img src="{{ image.path | relative_url }}" alt="{{ image.name }}" onclick="openModal(this)">
    {% endif %}
  {% endfor %}
</div>

.custom-image {
  border: 2px solid #000;
  border-radius: 4px;
  padding: 5px;
}

.gallery-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
  gap: 10px;
}