<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<title>प्रमाण पत्र Generator</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body{margin:0;font-family:Arial;background:#eee;}
.container{display:flex;flex-wrap:wrap;}
.form{
  width:30%;
  min-width:250px;
  background:#fff;
  padding:15px;
}
input,button{
  width:100%;
  margin:8px 0;
}
button{
  background:green;
  color:white;
  border:none;
  padding:10px;
  font-size:16px;
}
.preview{width:70%;padding:20px;}
.certificate{
  background:white;
  border:8px solid green;
  padding:20px;
  position:relative;
}
.logo-left{
  position:absolute;
  top:20px;left:20px;width:80px;
}
.logo-right{
  position:absolute;
  top:20px;right:20px;width:80px;
}
.user-photo{
  position:absolute;
  right:40px;
  top:120px;
  width:120px;
  border:3px solid green;
}
h1{text-align:center;}
p{text-align:center;}
.name{font-size:22px;font-weight:bold;text-align:center;}
</style>
</head>

<body>

<div class="container">

<div class="form">
  <h3>Certificate Form</h3>

  <label>User Name</label>
  <input type="text" id="name" placeholder="अपना नाम लिखें">

  <label>User Photo</label>
  <input type="file" onchange="loadPhoto(this)">

  <button onclick="generate()">Generate</button>
</div>

<div class="preview">
  <div class="certificate">

    <!-- Fixed Logos -->
    <img src="left-logo.png" class="logo-left">
    <img src="right-logo.png" class="logo-right">

    <img id="userPhoto" class="user-photo">

    <h1>प्रमाण पत्र</h1>
    <p>खेजड़ी बचाओ – पर्यावरण बचाओ अभियान</p>
    <p>यह प्रमाणित किया जाता है कि</p>

    <div class="name" id="cname">__________</div>

    <p>ने इस अभियान में सक्रिय सहभागिता निभाई।</p>
    <p><b>दिनांक:</b> 2 फरवरी 2026</p>
    <p><b>स्थान:</b> राजकीय पॉलिटेक्निक कॉलेज ग्राउंड, बीकानेर</p>

  </div>
</div>

</div>

<script>
function generate(){
  document.getElementById("cname").innerText =
  document.getElementById("name").value || "__________";
}

function loadPhoto(input){
  if(input.files && input.files[0]){
    let reader=new FileReader();
    reader.onload=e=>{
      document.getElementById("userPhoto").src=e.target.result;
    }
    reader.readAsDataURL(input.files[0]);
  }
}
</script>


</body>
</html>
