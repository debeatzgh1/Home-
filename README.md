
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Debeatzgh Digital Hub</title>

<style>
/* ===== BASE ===== */
body{
  margin:0;
  font-family:system-ui,-apple-system,BlinkMacSystemFont;
  background:#f3f4f6;
}

/* ===== FLOATING BUTTON ===== */
#floating-launcher{
  position:fixed;
  top:20px;
  right:20px;
  background:#16a34a;
  color:#fff;
  padding:8px 16px;
  font-size:13px;
  font-weight:600;
  border-radius:20px;
  box-shadow:0 4px 12px rgba(0,0,0,.25);
  cursor:pointer;
  z-index:9999;
}

/* ===== CAROUSEL ===== */
.carousel-wrapper{
  padding:40px 16px;
}
.carousel-wrapper h2{
  text-align:center;
}
.search-wrapper{
  max-width:420px;
  margin:16px auto 24px;
}
#searchInput{
  width:100%;
  padding:12px 16px;
  border-radius:14px;
  border:1px solid #ddd;
  font-size:14px;
  outline:none;
}
#searchInput:focus{
  border-color:#16a34a;
}
.carousel{
  display:flex;
  gap:20px;
  overflow-x:auto;
  scroll-snap-type:x mandatory;
}
.card{
  min-width:300px;
  background:#fff;
  border-radius:18px;
  box-shadow:0 10px 30px rgba(0,0,0,.15);
  scroll-snap-align:center;
  display:flex;
  flex-direction:column;
}
.card img{
  height:160px;
  width:100%;
  object-fit:cover;
  border-radius:18px 18px 0 0;
}
.card-content{
  padding:18px;
  flex:1;
}
.card h3{
  margin:0 0 8px;
}
.card p{
  font-size:14px;
  color:#555;
}
.card button{
  margin-top:14px;
  background:#16a34a;
  color:#fff;
  border:none;
  padding:12px;
  border-radius:14px;
  font-weight:700;
  cursor:pointer;
}

/* ===== OVERLAY ===== */
#overlay{
  position:fixed;
  inset:0;
  background:#fff;
  display:none;
  flex-direction:column;
  z-index:10000;
}
#overlay-top{
  background:#111;
  color:#fff;
  padding:12px;
  display:flex;
  justify-content:space-between;
  align-items:center;
}
#overlay-close{
  cursor:pointer;
  font-size:20px;
}
#overlay iframe{
  flex:1;
  width:100%;
  border:none;
}
</style>
</head>

<body>

<!-- FLOATING WEB BUTTON -->
<div id="floating-launcher">menu</div>

<!-- MAIN CONTENT -->
<section class="carousel-wrapper">
  <h2>🚀 Digital Products Hub</h2>

  <!-- SEARCH -->
  <div class="search-wrapper">
    <input type="search" id="searchInput"
      placeholder="Search AI, business, tools, side hustle…" />
  </div>

  <!-- CAROUSEL -->
  <div class="carousel" id="carousel"></div>
</section>

<!-- IFRAME OVERLAY -->
<div id="overlay">
  <div id="overlay-top">
    <span id="overlay-title">Loading…</span>
    <span id="overlay-close">✖</span>
  </div>
  <iframe id="overlay-frame"
    sandbox="allow-scripts allow-same-origin allow-forms allow-popups">
  </iframe>
</div>

<script>
/* ===== DATA ===== */
const products = [
  {
    title:"Creator Tools",
    desc:"Professional tools and guides for digital creators.",
    img:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createamoderncleanthumbnaildigitaltool.png",
    url:"https://debeatzgh1.github.io/Debeatzgh-Collaborators-Hub/"
  },
  {
    title:"Decode AI Starter Kit",
    desc:"Beginner-friendly AI resources and workflows.",
    img:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createaicleanstarterkitthumbnail.png",
    url:"https://debeatzgh1.github.io/Decode-AI-starter-kit-/"
  },
  {
    title:"Side Hustle Starter Kit",
    desc:"Actionable side hustle ideas for online income.",
    img:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/sidehustlethumbnail.png",
    url:"https://debeatzgh1.github.io/Side-hustle-starter-kit-/"
  },
  {
    title:"Online Business Kit",
    desc:"Everything you need to start and scale an online business.",
    img:"https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/onlinebusinessthumbnail.png",
    url:"https://debeatzgh1.github.io/Online-business-kit/"
  }
];

/* ===== ELEMENTS ===== */
const carousel = document.getElementById("carousel");
const searchInput = document.getElementById("searchInput");
const overlay = document.getElementById("overlay");
const frame = document.getElementById("overlay-frame");
const overlayTitle = document.getElementById("overlay-title");

/* ===== RENDER ===== */
function render(list){
  carousel.innerHTML="";
  list.forEach(item=>{
    carousel.innerHTML+=`
      <div class="card">
        <img src="${item.img}">
        <div class="card-content">
          <h3>${item.title}</h3>
          <p>${item.desc}</p>
          <button onclick="openOverlay('${item.url}','${item.title}')">
            Open
          </button>
        </div>
      </div>
    `;
  });
}
render(products);

/* ===== SEARCH FILTER ===== */
searchInput.addEventListener("input",()=>{
  const q = searchInput.value.toLowerCase();
  render(
    products.filter(p =>
      p.title.toLowerCase().includes(q) ||
      p.desc.toLowerCase().includes(q)
    )
  );
});

/* ===== OVERLAY LOGIC ===== */
function openOverlay(url,title){
  overlay.style.display="flex";
  frame.src=url;
  overlayTitle.innerText=title;
}
document.getElementById("overlay-close").onclick=()=>{
  overlay.style.display="none";
  frame.src="";
};

/* ===== FLOATING BUTTON ===== */
document.getElementById("floating-launcher").onclick=()=>{
  openOverlay("https://debeatzgh1.github.io/firebase-front-end-components/","Welcome to my Links");
};

/* ===== SOCIALCREATOR → NEW TAB ===== */
frame.addEventListener("load",()=>{
  try{
    frame.contentDocument.querySelectorAll("a").forEach(a=>{
      if(a.href.includes("socialcreator.com")){
        a.target="_blank";
        a.rel="noopener";
      }
    });
  }catch(e){}
});
</script>

</body>
</html>

  <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DeBeatzGH | Premium Hub</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #2563eb;
            --secondary: #0f172a;
            --accent: #38bdf8;
            --bg: #f8fafc;
            --card-bg: #ffffff;
            --text: #0f172a;
            --glass: rgba(255, 255, 255, 0.9);
            --transition: 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        [data-theme="dark"] {
            --bg: #0f172a;
            --card-bg: #1e293b;
            --text: #f8fafc;
            --secondary: #020617;
            --glass: rgba(15, 23, 42, 0.9);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Inter', sans-serif; }
        body { background-color: var(--bg); color: var(--text); transition: background var(--transition), color var(--transition); overflow-x: hidden; }

        /* --- Top Bar & Clock --- */
        .top-bar {
            position: fixed; top: 0; width: 100%; padding: 12px 30px;
            display: flex; justify-content: space-between; align-items: center;
            z-index: 100; background: var(--glass); backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(128,128,128,0.2);
        }
        .clock-display { font-weight: 700; color: var(--primary); font-family: monospace; }

        /* --- Welcome Popup --- */
        #welcome-modal {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.8); display: none; z-index: 2000;
            justify-content: center; align-items: center;
        }
        .welcome-content {
            background: var(--card-bg); padding: 40px; border-radius: 20px;
            text-align: center; max-width: 450px; position: relative;
            box-shadow: 0 20px 50px rgba(0,0,0,0.3);
        }
        .welcome-content h2 { margin-bottom: 15px; color: var(--primary); }

        /* --- Hero Section --- */
        .hero {
            background: linear-gradient(rgba(15, 23, 42, 0.8), rgba(15, 23, 42, 0.8)), 
                        url('https://debeatzgh.wordpress.com/wp-content/uploads/2026/01/gemini_generated_image_e3b3h0e3b3h0e3b38843226607488610379.png');
            background-size: cover; background-position: center;
            height: 50vh; display: flex; align-items: center; justify-content: center;
            text-align: center; color: white; padding-top: 50px;
        }

        /* --- Main UI Elements --- */
        .container { max-width: 1200px; margin: -40px auto 40px; padding: 0 20px; }
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px; }
        .card { 
            background: var(--card-bg); padding: 30px; border-radius: 16px; 
            box-shadow: 0 10px 30px rgba(0,0,0,0.05); text-align: center;
            border: 1px solid rgba(128,128,128,0.1); transition: var(--transition);
        }
        .card:hover { transform: translateY(-8px); border-color: var(--primary); }
        
        .btn-open { 
            display: inline-block; margin-top: 20px; padding: 12px 25px; 
            background: var(--primary); color: white; border-radius: 8px; 
            text-decoration: none; cursor: pointer; font-weight: 600;
        }

        /* --- Iframe Modal --- */
        #iframe-overlay {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.95); display: none; z-index: 1500;
            justify-content: center; align-items: center;
        }
        .modal-body { width: 95%; max-width: 1000px; height: 90vh; background: white; border-radius: 15px; overflow: hidden; position: relative; }
        .close-btn { position: absolute; top: 10px; right: 20px; font-size: 40px; cursor: pointer; color: #000; z-index: 1600; }
        iframe { width: 100%; height: 100%; border: none; }

        /* --- Auto Slider --- */
        .slider-wrap { background: var(--secondary); padding: 40px 0; overflow: hidden; color: white; }
        .slider-track { display: flex; width: calc(250px * 14); animation: scroll 35s linear infinite; }
        .mini-card { width: 220px; flex-shrink: 0; margin: 0 15px; padding: 20px; background: rgba(255,255,255,0.05); border-radius: 10px; text-align: center; cursor: pointer; }

        @keyframes scroll { 0% { transform: translateX(0); } 100% { transform: translateX(calc(-250px * 7)); } }
        
        footer { padding: 30px; text-align: center; background: var(--secondary); color: white; }
    </style>
</head>
<body>

    <div id="welcome-modal">
        <div class="welcome-content">
            <i class="fas fa-rocket" style="font-size: 3rem; color: var(--primary); margin-bottom: 20px;"></i>
            <h2 id="greeting-text">Welcome!</h2>
            <p>Explore our premium digital solutions. Use the dashboard below to place orders or manage your projects.</p>
            <button class="btn-open" onclick="closeWelcome()">Explore Now</button>
        </div>
    </div>

    <div class="top-bar">
        <div class="clock-display" id="liveClock">00:00:00</div>
        <div style="display: flex; gap: 20px; align-items: center;">
            <i class="fas fa-moon" id="themeIcon" style="cursor:pointer;" onclick="toggleTheme()"></i>
        </div>
    </div>

    <div id="iframe-overlay">
        <span class="close-btn" onclick="closeFrame()">&times;</span>
        <div class="modal-body">
            <iframe id="main-iframe" src=""></iframe>
        </div>
    </div>

    <section class="hero">
        <div style="padding: 20px;">
            <h1 style="font-size: 3.2rem;">DeBeatzGH Digital</h1>
            <p style="opacity: 0.9; font-size: 1.2rem;">Professionalism. Efficiency. Results.</p>
        </div>
    </section>

    <div class="container">
        <div class="grid">
            <div class="card">
                <i class="fas fa-id-card"></i>
                <h3>Client Portal</h3>
                <p>Sign in to track your orders.</p>
                <div class="btn-open" onclick="openFrame('https://docs.google.com/forms/d/e/1FAIpQLSdXCPUz1JBq0W8MHN9VOE0p6cnp5Wtr74Ox2gqLLyzKi0UwKA/viewform')">Login</div>
            </div>
            <div class="card">
                <i class="fas fa-rocket"></i>
                <h3>SEO Optimization</h3>
                <p>Get found on the first page.</p>
                <div class="btn-open" onclick="openFrame('https://docs.google.com/forms/d/e/1FAIpQLSfS_zQJx3CksS-zfLU6sNgXlqI3tq7nmpKeW7_8iWUYpCJpDQ/viewform')">Order SEO</div>
            </div>
            <div class="card">
                <i class="fas fa-laptop-code"></i>
                <h3>Web Projects</h3>
                <p>Custom websites built for you.</p>
                <div class="btn-open" onclick="openFrame('https://docs.google.com/forms/d/e/1FAIpQLSdipVP7tU1hjTjECfWUdnhzWN-PROdQp19ng25EUDJk5-8JzA/viewform')">Start Now</div>
            </div>
        </div>
    </div>

    <div class="slider-wrap">
        <p style="text-align:center; opacity:0.5; font-size:0.8rem; margin-bottom:20px;">QUICK ACCESS SERVICES</p>
        <div class="slider-track">
            <div class="mini-card" onclick="openFrame('https://docs.google.com/forms/d/e/1FAIpQLSfBDlR6TcU9sWjbeVOp6dtb4GMKdL6SP_i0KB08IrtbLT9wwA/viewform')"><i class="fas fa-phone"></i><br>Contact</div>
            <div class="mini-card" onclick="openFrame('https://docs.google.com/forms/d/e/1FAIpQLSdx2yQU28hg4L4Rm8rSdvjR4FZPpbys7XKEZDFul5yubv3Olg/viewform')"><i class="fas fa-comment"></i><br>Suggestions</div>
            <div class="mini-card" onclick="openFrame('https://docs.google.com/forms/d/e/1FAIpQLSd5sIJkuaBveQLFp4-W2WLvU33oDbAZMwy61MLwpMZuXrEk7Q/viewform')"><i class="fas fa-columns"></i><br>Formatting</div>
            <div class="mini-card" onclick="openFrame('https://docs.google.com/forms/d/e/1FAIpQLSd2fIJuPsH_fybU1esTlCaeci2s-ERDLt2L7lAp3kW4QL6D7w/viewform')"><i class="fas fa-edit"></i><br>Blogging</div>
            <div class="mini-card" onclick="window.location.href='https://debeatzgh1.github.io/1/'"><i class="fas fa-link"></i><br>Main Site</div>
            <div class="mini-card" onclick="openFrame('https://docs.google.com/forms/d/e/1FAIpQLSfBDlR6TcU9sWjbeVOp6dtb4GMKdL6SP_i0KB08IrtbLT9wwA/viewform')"><i class="fas fa-phone"></i><br>Contact</div>
            <div class="mini-card" onclick="openFrame('https://docs.google.com/forms/d/e/1FAIpQLSdx2yQU28hg4L4Rm8rSdvjR4FZPpbys7XKEZDFul5yubv3Olg/viewform')"><i class="fas fa-comment"></i><br>Suggestions</div>
            </div>
    </div>

    <footer>
        <p>&copy; 2026 DeBeatzGH | Digital Solutions Provider</p>
    </footer>

    <script>
        // Welcome Logic
        window.onload = function() {
            if (!localStorage.getItem('visited')) {
                document.getElementById('welcome-modal').style.display = 'flex';
                setGreeting();
            }
        };

        function setGreeting() {
            const hour = new Date().getHours();
            let g = "Welcome to DeBeatzGH!";
            if (hour < 12) g = "Good Morning!";
            else if (hour < 18) g = "Good Afternoon!";
            else g = "Good Evening!";
            document.getElementById('greeting-text').innerText = g;
        }

        function closeWelcome() {
            document.getElementById('welcome-modal').style.display = 'none';
            localStorage.setItem('visited', 'true');
        }

        // Clock
        setInterval(() => {
            document.getElementById('liveClock').innerText = new Date().toLocaleTimeString();
        }, 1000);

        // Theme
        function toggleTheme() {
            const b = document.body;
            const icon = document.getElementById('themeIcon');
            if (b.getAttribute('data-theme') === 'dark') {
                b.setAttribute('data-theme', 'light');
                icon.className = 'fas fa-moon';
            } else {
                b.setAttribute('data-theme', 'dark');
                icon.className = 'fas fa-sun';
            }
        }

        // Iframe
        function openFrame(u) {
            document.getElementById('main-iframe').src = u;
            document.getElementById('iframe-overlay').style.display = 'flex';
            document.body.style.overflow = 'hidden';
        }
        function closeFrame() {
            document.getElementById('iframe-overlay').style.display = 'none';
            document.body.style.overflow = 'auto';
        }
    </script>
</body>
</html>


