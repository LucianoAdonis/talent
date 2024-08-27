---
layout: custom
title: Simpsons
description: Extra Points in Retrospectives and Feedback for each Simpson Reference
---

<div class="gallery-container">
  {% for image in site.static_files %}
    {% if image.path contains '/assets/images/simpsons/' %}
      <img src="{{ image.path | relative_url }}" alt="{{ image.name }}" onclick="openModal(this)">
    {% endif %}
  {% endfor %}
</div>
