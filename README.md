
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
    <title>DeBeatzGH | Professional Digital Solutions</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #2563eb;
            --secondary: #0f172a;
            --accent: #38bdf8;
            --text-light: #f8fafc;
            --glass: rgba(255, 255, 255, 0.95);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', sans-serif;
        }

        body {
            background-color: #f1f5f9;
            color: var(--secondary);
            line-height: 1.6;
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(rgba(15, 23, 42, 0.8), rgba(15, 23, 42, 0.8)), 
                        url('https://debeatzgh.wordpress.com/wp-content/uploads/2026/01/gemini_generated_image_e3b3h0e3b3h0e3b38843226607488610379.png');
            background-size: cover;
            background-position: center;
            height: 80vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: white;
            padding: 20px;
        }

        .hero-content h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
            letter-spacing: -1px;
        }

        .hero-content p {
            font-size: 1.2rem;
            max-width: 700px;
            margin: 0 auto 2rem;
            opacity: 0.9;
        }

        .btn-main {
            background: var(--primary);
            color: white;
            padding: 12px 30px;
            border-radius: 8px;
            text-decoration: none;
            font-weight: 600;
            transition: 0.3s;
            display: inline-block;
        }

        .btn-main:hover {
            background: var(--accent);
            transform: translateY(-2px);
        }

        /* Services Grid */
        .container {
            max-width: 1100px;
            margin: -50px auto 50px;
            padding: 0 20px;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }

        .card {
            background: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.05);
            transition: 0.3s;
            border: 1px solid #e2e8f0;
        }

        .card:hover {
            transform: translateY(-10px);
            border-color: var(--primary);
        }

        .card i {
            font-size: 2.5rem;
            color: var(--primary);
            margin-bottom: 20px;
        }

        .card h3 {
            margin-bottom: 10px;
            font-size: 1.4rem;
        }

        .card p {
            color: #64748b;
            font-size: 0.95rem;
            margin-bottom: 20px;
        }

        .form-link {
            color: var(--primary);
            text-decoration: none;
            font-weight: 700;
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        /* Footer */
        footer {
            background: var(--secondary);
            color: white;
            padding: 40px 20px;
            text-align: center;
            margin-top: 50px;
        }

        .nav-links {
            margin-bottom: 20px;
        }

        .nav-links a {
            color: white;
            margin: 0 15px;
            text-decoration: none;
            font-size: 0.9rem;
            opacity: 0.7;
        }

        .nav-links a:hover { opacity: 1; }

        @media (max-width: 768px) {
            .hero-content h1 { font-size: 2rem; }
        }
    </style>
</head>
<body>

    <section class="hero">
        <div class="hero-content">
            <h1>DeBeatzGH Digital Hub</h1>
            <p>Premium SEO Optimization, Professional Blog Management, and High-End Web Projects Tailored for Your Success.</p>
            <a href="https://docs.google.com/forms/d/e/1FAIpQLSdXCPUz1JBq0W8MHN9VOE0p6cnp5Wtr74Ox2gqLLyzKi0UwKA/viewform?usp=header" class="btn-main">Sign In to Dashboard</a>
        </div>
    </section>

    <div class="container">
        <div class="grid">
            <div class="card">
                <i class="fas fa-search-dollar"></i>
                <h3>SEO Optimization</h3>
                <p>Boost your search rankings and visibility with our professional SEO order processing.</p>
                <a href="https://docs.google.com/forms/d/e/1FAIpQLSfS_zQJx3CksS-zfLU6sNgXlqI3tq7nmpKeW7_8iWUYpCJpDQ/viewform?usp=header" class="form-link">Place SEO Order &rarr;</a>
            </div>

            <div class="card">
                <i class="fas fa-pen-nib"></i>
                <h3>Blog Management</h3>
                <p>Quality content creation and blog structuring services for your brand's voice.</p>
                <a href="https://docs.google.com/forms/d/e/1FAIpQLSd2fIJuPsH_fybU1esTlCaeci2s-ERDLt2L7lAp3kW4QL6D7w/viewform?usp=header" class="form-link">Order Blog Post &rarr;</a>
            </div>

            <div class="card">
                <i class="fas fa-laptop-code"></i>
                <h3>Project Development</h3>
                <p>Custom web projects and digital solutions built with modern frameworks.</p>
                <a href="https://docs.google.com/forms/d/e/1FAIpQLSdipVP7tU1hjTjECfWUdnhzWN-PROdQp19ng25EUDJk5-8JzA/viewform?usp=header" class="form-link">Start a Project &rarr;</a>
            </div>

            <div class="card">
                <i class="fas fa-file-invoice"></i>
                <h3>Content Formatting</h3>
                <p>Transform your raw data into professional, readable, and SEO-friendly formats.</p>
                <a href="https://docs.google.com/forms/d/e/1FAIpQLSd5sIJkuaBveQLFp4-W2WLvU33oDbAZMwy61MLwpMZuXrEk7Q/viewform?usp=header" class="form-link">Format Content &rarr;</a>
            </div>

            <div class="card">
                <i class="fas fa-lightbulb"></i>
                <h3>Suggestions</h3>
                <p>Have an idea to improve our services? We value your professional feedback.</p>
                <a href="https://docs.google.com/forms/d/e/1FAIpQLSdx2yQU28hg4L4Rm8rSdvjR4FZPpbys7XKEZDFul5yubv3Olg/viewform?usp=header" class="form-link">Submit Idea &rarr;</a>
            </div>

            <div class="card">
                <i class="fas fa-headset"></i>
                <h3>Support Desk</h3>
                <p>Need direct assistance? Contact our team for professional support and inquiries.</p>
                <a href="https://docs.google.com/forms/d/e/1FAIpQLSfBDlR6TcU9sWjbeVOp6dtb4GMKdL6SP_i0KB08IrtbLT9wwA/viewform?usp=header" class="form-link">Contact Us &rarr;</a>
            </div>
        </div>
    </div>

    <footer>
        <div class="nav-links">
            <a href="https://debeatzgh1.github.io/1/">Official Website</a>
            <a href="https://docs.google.com/forms/d/e/1FAIpQLSdXCPUz1JBq0W8MHN9VOE0p6cnp5Wtr74Ox2gqLLyzKi0UwKA/viewform?usp=header">Client Portal</a>
        </div>
        <p>&copy; 2026 DeBeatzGH Digital. All rights reserved.</p>
    </footer>

</body>
</html>


