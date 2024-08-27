---
layout: custom
title: Talent
description: There's no War in Talent
---

<div class="gallery-container">
  {% for image in site.static_files %}
    {% if image.path contains '/assets/images/talent/' %}
      <img src="{{ image.path | relative_url }}" alt="{{ image.name }}" onclick="copyToClipboard('{{ image.path | relative_url }}')">
    {% endif %}
  {% endfor %}
</div>

<div id="popup-message" class="popup-message">Copied to clipboard!</div>

