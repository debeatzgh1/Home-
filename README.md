
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
