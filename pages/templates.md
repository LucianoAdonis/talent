---
layout: custom
title: Templates
description: Making memes with high quality
---


<div class="gallery-container">
  {% for image in site.static_files %}
    {% if image.path contains '/assets/images/templates/' %}
      <img src="{{ image.path | relative_url }}" alt="{{ image.name }}" onclick="copyToClipboard('{{ image.path | relative_url }}')">
    {% endif %}
  {% endfor %}
</div>

<div id="popup-message" class="popup-message">Copied to clipboard!</div>

<script>
  function copyToClipboard(imageUrl) {
    // Create a temporary input element to hold the text
    const tempInput = document.createElement('input');
    document.body.appendChild(tempInput);
    tempInput.value = window.location.origin + imageUrl;
    tempInput.select();
    document.execCommand('copy');
    document.body.removeChild(tempInput);

    // Show the popup message
    const popup = document.getElementById('popup-message');
    popup.classList.add('show');
    
    // Hide the popup message after 2 seconds
    setTimeout(() => {
      popup.classList.remove('show');
    }, 2000);
  }
</script>

