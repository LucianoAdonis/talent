<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Image Gallery</title>
  <style>
    .gallery img {
      width: 150px;
      margin: 10px;
      border: 2px solid #000;
      border-radius: 4px;
      cursor: pointer;
    }
    .modal {
      display: none;
      position: fixed;
      z-index: 1000;
      padding-top: 50px;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0,0,0,0.9);
    }
    .modal-content {
      margin: auto;
      display: block;
      max-width: 80%;
      max-height: 80%;
    }
    .close {
      position: absolute;
      top: 15px;
      right: 35px;
      color: #fff;
      font-size: 40px;
      font-weight: bold;
      transition: 0.3s;
    }
    .close:hover,
    .close:focus {
      color: #bbb;
      text-decoration: none;
      cursor: pointer;
    }
    #copyUrl {
      display: none;
      color: white;
      position: fixed;
      bottom: 10px;
      left: 50%;
      transform: translateX(-50%);
      padding: 10px;
      background-color: #333;
      border-radius: 4px;
    }
  </style>
</head>
<body>

<div class="gallery">
  {% for image in site.static_files %}
    {% if image.path contains '/assets/images/gallery/' %}
      <img src="{{ image.path | relative_url }}" alt="{{ image.name }}" onclick="openModal(this)">
    {% endif %}
  {% endfor %}
</div>

<!-- The Modal -->
<div id="myModal" class="modal">
  <span class="close">&times;</span>
  <img class="modal-content" id="img01">
</div>

<!-- URL Copy Feedback -->
<div id="copyUrl">URL copied to clipboard!</div>

<script>
function openModal(imgElement) {
  var modal = document.getElementById("myModal");
  var modalImg = document.getElementById("img01");
  modal.style.display = "block";
  modalImg.src = imgElement.src;

  modalImg.onclick = function() {
    copyToClipboard(imgElement.src);
  };
}

document.querySelector('.close').onclick = function() { 
  document.getElementById("myModal").style.display = "none";
};

document.onkeydown = function(event) {
  if (event.key === "Escape") {
    document.getElementById("myModal").style.display = "none";
  }
};

function copyToClipboard(text) {
  var dummy = document.createElement("input");
  document.body.appendChild(dummy);
  dummy.setAttribute("value", text);
  dummy.select();
  document.execCommand("copy");
  document.body.removeChild(dummy);
  
  var copyAlert = document.getElementById("copyUrl");
  copyAlert.style.display = "block";
  setTimeout(function() {
    copyAlert.style.display = "none";
  }, 2000);
}
</script>

</body>
</html>
