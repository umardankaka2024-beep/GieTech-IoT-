<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>GieTech-IoT Kano</title>

  <style>
    *{
      margin:0;
      padding:0;
      box-sizing:border-box;
      font-family: Arial, sans-serif;
    }

    body{
      background:#f4f7fa;
      color:#222;
    }

    header{
      background:#0b1f3a;
      color:white;
      padding:20px 10%;
      display:flex;
      justify-content:space-between;
      align-items:center;
    }

    nav a{
      color:white;
      text-decoration:none;
      margin-left:20px;
      font-weight:bold;
    }

    nav a:hover{
      color:#00bcd4;
    }

    .hero{
      background:url('https://images.unsplash.com/photo-1516321318423-f06f85e504b3') center/cover;
      height:90vh;
      display:flex;
      align-items:center;
      justify-content:center;
      text-align:center;
      color:white;
      padding:20px;
    }

    .hero-content{
      background:rgba(0,0,0,0.6);
      padding:40px;
      border-radius:10px;
    }

    .btn{
      display:inline-block;
      padding:12px 25px;
      background:#00bcd4;
      color:white;
      text-decoration:none;
      border-radius:5px;
      font-weight:bold;
    }

    section{
      padding:60px 10%;
    }

    .section-title{
      text-align:center;
      margin-bottom:40px;
      font-size:35px;
      color:#0b1f3a;
    }

    .services{
      display:grid;
      grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
      gap:25px;
    }

    .card{
      background:white;
      padding:25px;
      border-radius:10px;
      box-shadow:0 5px 15px rgba(0,0,0,0.1);
    }

    .updates{
      display:grid;
      grid-template-columns:repeat(auto-fit,minmax(300px,1fr));
      gap:25px;
    }

    .update-box{
      background:white;
      border-radius:10px;
      overflow:hidden;
      box-shadow:0 5px 15px rgba(0,0,0,0.1);
    }

    .update-box img,
    .update-box video{
      width:100%;
    }

    .update-content{
      padding:15px;
    }

    .admin-panel{
      background:white;
      padding:25px;
      border-radius:10px;
      margin-top:30px;
      box-shadow:0 5px 15px rgba(0,0,0,0.1);
    }

    .admin-panel input,
    .admin-panel textarea{
      width:100%;
      padding:12px;
      margin:10px 0;
      border:1px solid #ccc;
      border-radius:5px;
    }

    button{
      padding:12px 20px;
      background:#0b1f3a;
      color:white;
      border:none;
      cursor:pointer;
      border-radius:5px;
      font-weight:bold;
    }

    footer{
      background:#0b1f3a;
      color:white;
      text-align:center;
      padding:20px;
      margin-top:40px;
    }

    .hidden{
      display:none;
    }
  </style>
</head>

<body>

<header>
  <h1 align="center">GieTech-IoT Kano</h1>
  <nav>
    <a href="#services">Services</a>
    <a href="#updates">Updates</a>
    <a href="#contact">Contact</a>
  </nav>
</header>

<!-- HERO -->
<section class="hero">
  <div class="hero-content">
    <h2>Professional Inverter Repair Services</h2>
    <p>We fix inverters, install solar systems, and provide embedded engineering solutions.</p>
    <a href="#contact" class="btn">Contact Us</a>
  </div>
</section>

<!-- SERVICES -->
<section id="services">
  <h2 class="section-title">Our Services</h2>

  <div class="services">
    <div class="card">Inverter Repair</div>
    <div class="card">Solar Installation</div>
    <div class="card">Battery Maintenance</div>
    <div class="card">Embedded Systems</div>
  </div>
</section>

<!-- UPDATES -->
<section id="updates">
  <h2 class="section-title">Latest Updates</h2>

  <div class="updates" id="updatesContainer">

    <div class="update-box">
      <img src="https://images.unsplash.com/photo-1581092160607-ee22621dd758">
      <div class="update-content">
        <h3>Solar Installation</h3>
        <p>Completed a new inverter solar project.</p>
      </div>
    </div>

  </div>

  <!-- ADMIN LOGIN -->
  <div class="admin-panel" id="loginBox">
    <h2>Admin Login</h2>
    <input type="text" id="username" placeholder="Username">
    <input type="password" id="password" placeholder="Password">
    <button onclick="login()">Login</button>
  </div>

  <!-- ADMIN PANEL -->
  <div class="admin-panel hidden" id="adminBox">
    <h2>Add Update</h2>

    <input type="text" id="title" placeholder="Title">
    <textarea id="desc" placeholder="Description"></textarea>
    <input type="file" id="file">

    <button onclick="addUpdate()">Add Update</button>
  </div>

</section>

<!-- CONTACT -->
<section id="contact">
  <h2 class="section-title">Contact</h2>

  <div class="admin-panel">
    <h3>Send WhatsApp Message</h3>
    <input type="text" id="waMsg" placeholder="Message">
    <button onclick="sendWhatsApp()">Send</button>
  </div>
</section>

<footer>
  © 2026 GieTech-IoT Kano | Engr Umar Dankaka
</footer>

<script>

  // LOGIN
  function login(){

    let user = document.getElementById("username").value;
    let pass = document.getElementById("password").value;

    if(user === "admin" && pass === "12345"){
      alert("Login Successful");

      document.getElementById("loginBox").style.display="none";
      document.getElementById("adminBox").classList.remove("hidden");

    }else{
      alert("Wrong Login Details");
    }
  }

  // ADD UPDATE
  function addUpdate(){

    let title = document.getElementById("title").value;
    let desc = document.getElementById("desc").value;
    let file = document.getElementById("file").files[0];

    if(!title || !desc || !file){
      alert("Fill all fields");
      return;
    }

    let reader = new FileReader();

    reader.onload = function(e){

      let box = document.createElement("div");
      box.className = "update-box";

      let media = "";

      if(file.type.startsWith("image")){
        media = `<img src="${e.target.result}">`;
      }else{
        media = `<video controls><source src="${e.target.result}"></video>`;
      }

      box.innerHTML = `
        ${media}
        <div class="update-content">
          <h3>${title}</h3>
          <p>${desc}</p>
        </div>
      `;

      document.getElementById("updatesContainer").prepend(box);

    };

    reader.readAsDataURL(file);
  }

  // WHATSAPP
  function sendWhatsApp(){

    let msg = document.getElementById("waMsg").value;
    let phone = "+2348103391740";

    let url = "https://wa.me/" + phone + "?text=" + encodeURIComponent(msg);

    window.open(url, "_blank");
  }

</script>

</body>
</html>
