<!DOCTYPE html>
<html lang="mr">
<head>
<meta charset="UTF-8">
<title>ZP Shala Card</title>

<!-- Font -->
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+Devanagari:wght@400;700&display=swap" rel="stylesheet">

<script src="https://html2canvas.hertzen.com/dist/html2canvas.min.js"></script>

<style>
body {
  margin: 0;
  font-family: 'Noto Sans Devanagari', sans-serif;
  background: linear-gradient(#f7c873, #f39c12);
  text-align: center;
}

/* CARD */
.card {
  width: 320px;
  margin: 20px auto;
  background: linear-gradient(#fff3d6, #f5c27c);
  border-radius: 25px;
  padding: 20px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.2);
  position: relative;
}

/* LOGO */
.logo {
  width: 60px;
}

/* PHOTO */
.photo {
  width: 120px;
  height: 120px;
  background: #ddd;
  border-radius: 50%;
  margin: 15px auto;
  overflow: hidden;
}

.photo img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* TEXT */
.title {
  color: #d35400;
  font-weight: bold;
  margin: 10px 0;
}

.field {
  margin: 10px 0;
  border-bottom: 1px dashed #333;
  padding-bottom: 5px;
}

/* INPUTS */
input {
  width: 80%;
  padding: 10px;
  margin: 5px;
  border-radius: 10px;
  border: none;
}

/* BUTTONS */
.btn {
  background: #e67e22;
  color: white;
  padding: 10px 20px;
  border-radius: 20px;
  border: none;
  margin: 5px;
  cursor: pointer;
}
</style>
</head>

<body>

<!-- INPUT SECTION -->
<input type="file" onchange="loadImage(event)"><br>
<input type="text" id="name" placeholder="नाव लिहा"><br>
<input type="text" id="address" placeholder="पत्ता लिहा"><br>
<input type="text" id="school" placeholder="शाळेचे नाव"><br>

<button class="btn" onclick="generate()">Generate</button>
<button class="btn" onclick="download()">Download</button>
<button class="btn" onclick="share()">WhatsApp</button>

<!-- CARD -->
<div class="card" id="card">

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/0f/Emblem_of_India.svg/120px-Emblem_of_India.svg.png" class="logo">

<h4>जिल्हा परिषद जळगाव</h4>
<p>शिक्षण विभाग</p>

<div class="photo">
  <img id="preview">
</div>

<h3 class="title">"मी जि. प. शाळेचा विद्यार्थी"</h3>

<div class="field" id="cardName">नाव</div>
<div class="field" id="cardAddress">पत्ता</div>
<div class="field" id="cardSchool">शाळा</div>

</div>

<script>
function generate() {
  document.getElementById("cardName").innerText =
    "नाव: " + document.getElementById("name").value;

  document.getElementById("cardAddress").innerText =
    "पत्ता: " + document.getElementById("address").value;

  document.getElementById("cardSchool").innerText =
    "शाळा: " + document.getElementById("school").value;
}

function loadImage(event) {
  document.getElementById("preview").src =
    URL.createObjectURL(event.target.files[0]);
}

function download() {
  html2canvas(document.getElementById("card")).then(canvas => {
    let link = document.createElement('a');
    link.download = 'zp-card.png';
    link.href = canvas.toDataURL();
    link.click();
  });
}

function share() {
  let text = "मी जि. प. शाळेचा विद्यार्थी!";
  window.open(`https://wa.me/?text=${encodeURIComponent(text)}`);
}
</script>

</body>
</html>
