<div class="gallery-container">
  {% for image in site.static_files %}
    {% if image.path contains '/assets/images/anime/' %}
      <img src="{{ image.path | relative_url }}" alt="{{ image.name }}" onclick="openModal(this)">
    {% endif %}
  {% endfor %}
</div>
