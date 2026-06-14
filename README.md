<script>
(function(){

/* ================= CONFIG ================= */
const DBZ_HOME = "https://debeatzgh1.github.io/firebase-front-end-components/";
const BTN_SIZE = 36; // Shrunk down from 52px to a mini size
const BTN_COLOR = "#0f2a44";

/* ================= STYLES ================= */
const css = `
#dbz-btn{
  position:fixed;
  right:16px;
  top:60%;
  transform:translateY(-50%);
  width:${BTN_SIZE}px;
  height:${BTN_SIZE}px;
  border-radius:50%;
  background:${BTN_COLOR};
  color:#fff;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:16px; /* Adjusted icon font-size to look good in 36px space */
  cursor:pointer;
  z-index:999999;
  box-shadow:0 8px 24px rgba(0,0,0,.3);
  animation:dbzPulse 1.6s infinite;
  font-family: system-ui, sans-serif;
}
@keyframes dbzPulse{
  0%,100%{transform:translateY(-50%) scale(1)}
  50%{transform:translateY(-50%) scale(1.06)}
}

#dbz-overlay{
  position:fixed;
  inset:0;
  background:rgba(0,0,0,.3); /* Lightened backdrop so users can see the left screen */
  backdrop-filter:blur(3px);
  display:none;
  z-index:999998;
}

/* Positions Frame strictly from the middle right corner */
#dbz-box{
  position:absolute;
  right:10px;
  bottom:20px;

  width:450px;
  height:60vh;

  background:#fff;
  border-radius:16px;
  overflow:hidden;
  display:flex;
  flex-direction:column;
}

#dbz-bar{
  background:${BTN_COLOR};
  color:#fff;
  padding:6px 12px;
  display:flex;
  justify-content:space-between;
  align-items:center;
  font-size:13px;
  user-select:none;
}

#dbz-bar button{
  background:none;
  border:none;
  color:#fff;
  font-size:14px;
  cursor:pointer;
  margin-left:4px;
  opacity:0.85;
  transition:opacity 0.2s;
}

#dbz-bar button:hover{
  opacity:1;
}
`;
const style = document.createElement("style");
style.innerHTML = css;
document.head.appendChild(style);

/* ================= HTML ================= */
const html = `
<div id="dbz-btn" title="Open Debeatzgh Hub">☰</div>

<div id="dbz-overlay">
  <div id="dbz-box">
    <div id="dbz-bar">
      <div>
        <button id="dbz-back" title="Back">⟵</button>
        <button id="dbz-forward" title="Forward">⟶</button>
      </div>
      <div style="font-family:system-ui,sans-serif;font-weight:600;font-size:11px;letter-spacing:0.5px;">DEBEATZGH</div>
      <div>
        <button id="dbz-full" title="Fullscreen">⛶</button>
        <button id="dbz-close" title="Close">✕</button>
      </div>
    </div>
    <iframe id="dbz-frame" style="flex:1;border:none;background:#fff;"></iframe>
  </div>
</div>
`;
document.body.insertAdjacentHTML("beforeend", html);

/* ================= LOGIC ================= */
const btn = document.getElementById("dbz-btn");
const overlay = document.getElementById("dbz-overlay");
const frame = document.getElementById("dbz-frame");
const box = document.getElementById("dbz-box");

btn.onclick = ()=>{
  frame.src = DBZ_HOME;
  overlay.style.display = "block";
};

// Close when clicking the 'X' button
document.getElementById("dbz-close").onclick = ()=>{
  overlay.style.display = "none";
  frame.src = "";
  if(document.fullscreenElement) document.exitFullscreen();
};

// Close when clicking outside the box frame area
overlay.onclick = (e)=>{
  if(e.target === overlay){
    overlay.style.display = "none";
    frame.src = "";
  }
};

document.getElementById("dbz-back").onclick = ()=>{
  try{frame.contentWindow.history.back()}catch(e){}
};

document.getElementById("dbz-forward").onclick = ()=>{
  try{frame.contentWindow.history.forward()}catch(e){}
};

document.getElementById("dbz-full").onclick = ()=>{
  if(!document.fullscreenElement){
    box.requestFullscreen();
  }else{
    document.exitFullscreen();
  }
};

})();
</script>


<!-- Elfsight Announcement Bar | Ads -->
<script src="https://elfsightcdn.com/platform.js" async></script>
<div class="elfsight-app-da4c4e26-f1fe-4865-98e5-07ab2384d659" data-elfsight-app-lazy></div>



<!-- DeBeatzGH Live Workspace Embed Component -->
<div class="dbz-embed-container" style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; margin: 20px auto; max-width: 1000px; border-radius: 16px; overflow: hidden; box-shadow: 0 10px 30px rgba(0,0,0,0.08); border: 1px solid #e2e8f0; background: #ffffff;">
    
    <!-- Control Header -->
    <div style="background: #f8fafc; padding: 12px 20px; border-b: 1px solid #e2e8f0; display: flex; justify-content: space-between; items-center: center; flex-wrap: wrap; gap: 10px;">
        <div style="display: flex; items-center: center; gap: 8px;">
            <span style="width: 10px; height: 10px; border-radius: 50%; background: #ef4444; display: inline-block;"></span>
            <span style="width: 10px; height: 10px; border-radius: 50%; background: #eab308; display: inline-block;"></span>
            <span style="width: 10px; height: 10px; border-radius: 50%; background: #22c55e; display: inline-block;"></span>
            <span style="font-size: 13px; font-weight: 600; color: #475569; margin-left: 10px;">Workspace Viewport | DeBeatzGH</span>
        </div>
        <div>
            <a href="https://debeatzgh.wordpress.com/?page_id=1246" target="_blank" style="font-size: 12px; font-weight: 600; color: #2563eb; text-decoration: none; padding: 6px 12px; border-radius: 6px; background: #eff6ff; transition: all 0.2s;" onmouseover="this.style.background='#dbeafe'" onmouseout="this.style.background='#eff6ff'">
                Open Native Page <span style="font-size: 10px; margin-left: 2px;">↗</span>
            </a>
        </div>
    </div>

    <!-- Active Sandbox Viewport -->
    <div style="position: relative; width: 100%; height: 750px; background: #f1f5f9;">
        <!-- CSS-Only Spinner (Hidden automatically once iframe mounts content threads) -->
        <div id="dbz-embed-loader" style="position: absolute; inset: 0; display: flex; flex-direction: column; align-items: center; justify-content: center; background: #ffffff; z-index: 5;">
            <div style="width: 40px; height: 40px; border: 3px solid #cbd5e1; border-top-color: #2563eb; border-radius: 50%; animation: dbz-spin 0.8s linear infinite;"></div>
            <p style="margin-top: 12px; font-size: 13px; color: #64748b; font-weight: 500;">Establishing portal attachment...</p>
        </div>

        <!-- Embedded Frame Target Node -->
        <iframe 
            src="https://beatzde4.blogspot.com/p/heres-comprehensive-description-of-html.html" 
            style="width: 100%; height: 100%; border: none; opacity: 0; transition: opacity 0.3s ease;" 
            allow="geolocation; microphone; camera; midi; encrypted-media;"
            sandbox="allow-forms allow-modals allow-popups allow-scripts allow-same-origin allow-top-navigation-by-user-activation"
            onload="document.getElementById('dbz-embed-loader').style.display='none'; this.style.opacity='1';">
        </iframe>
    </div>
</div>

<!-- Essential Animation Styles Definition -->
<style>
    @keyframes dbz-spin {
        to { transform: rotate(360deg); }
    }
</style>

<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Creators Hub– AI Tools, Side Hustles & Digital Growth</title>

<!-- Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@500;600;700&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">

<!-- Tailwind -->
<script src="https://cdn.tailwindcss.com"></script>

<script>
tailwind.config = {
  theme: {
    extend: {
      colors: {
        primary: '#0F2A44',
        secondary: '#1E88E5',
        accent: '#00C2A8',
        highlight: '#6C63FF',
        bg: '#F8FAFC'
      },
      fontFamily: {
        heading: ['Poppins','sans-serif'],
        body: ['Inter','sans-serif']
      }
    }
  }
}
</script>

<style>
@keyframes pulseSoft {
  0%,100% { transform: scale(1); }
  50% { transform: scale(1.08); }
}
.floating-btn { animation: pulseSoft 1.8s infinite; }
</style>
</head>

<body class="bg-bg font-body text-gray-800">

<!-- NAVBAR -->
<header class="sticky top-0 z-40 bg-white shadow-sm">
  <div class="max-w-7xl mx-auto px-4 py-4 flex justify-between items-center">
    <button onclick="openFrame('https://debeatzgh1.github.io/Home-/')" class="text-2xl font-heading font-bold text-primary">
      Debeatzgh
    </button>
    <nav class="hidden md:flex gap-8 font-medium">
      <button onclick="openFrame('https://debeatzgh1.github.io/Home-/')" class="hover:text-secondary">Home</button>
      <button onclick="openFrame('https://debeatzgh1.github.io/-My-Brand-Online-Digital-Products-Affiliate-Shop/')" class="hover:text-secondary">Products</button>
      <button onclick="openFrame('https://debeatzgh1.github.io/blogs/')" class="hover:text-secondary">Blogs</button>
      <button onclick="openFrame('https://msha.ke/debeatzgh')" class="hover:text-secondary">Milkshake</button>
    </nav>
    <button onclick="openFrame('https://msha.ke/debeatzgh')" class="bg-secondary text-white px-5 py-2 rounded-xl shadow hover:scale-105 transition">
      Open Hub
    </button>
  </div>
</header>

<!-- HERO -->
<section class="max-w-7xl mx-auto px-4 py-20 grid md:grid-cols-2 gap-12 items-center">
  <div>
    <h2 class="text-4xl md:text-5xl font-heading font-bold text-primary">
      Build Income with <span class="text-secondary">AI Tools</span> & Smart Side Hustles
    </h2>
    <p class="mt-6 text-lg text-gray-600">
      AI tools, blogging guides, and digital products — all curated to help you earn online.
    </p>
    <div class="mt-8 flex gap-4">
      <button onclick="openFrame('https://debeatzgh1.github.io/-My-Brand-Online-Digital-Products-Affiliate-Shop/')" class="bg-secondary text-white px-6 py-3 rounded-xl shadow hover:scale-105 transition">
        View Products
      </button>
      <button onclick="openFrame('https://debeatzgh1.github.io/blogs/')" class="border border-secondary text-secondary px-6 py-3 rounded-xl hover:bg-secondary hover:text-white transition">
        Read Blogs 
      </button>
    </div>
  </div>

  <div class="bg-white rounded-xl shadow-lg p-6">
    <img src="https://images.unsplash.com/photo-1674027444485-cec3da58eef4" class="rounded-xl">
  </div>
</section>

<!-- FEATURES -->
<section class="bg-white py-16">
  <div class="max-w-7xl mx-auto px-4">
    <h3 class="text-3xl font-heading font-semibold text-center text-primary">
      What You’ll Find
    </h3>

    <div class="grid md:grid-cols-3 gap-8 mt-12">
      <button onclick="openFrame('https://debeatzgh.wordpress.com/')" class="p-6 rounded-xl shadow hover:shadow-lg transition text-left">
        <span class="bg-accent text-white px-3 py-1 rounded-full text-sm">HUB</span>
        <h4 class="mt-4 font-heading text-xl font-semibold">Central Link Hub</h4>
        <p class="mt-2 text-gray-600">Access all Debeatzgh tools, products & platforms.</p>
      </button>

      <button onclick="openFrame('https://form.jotform.com/241335470278053')" class="p-6 rounded-xl shadow hover:shadow-lg transition text-left">
        <span class="bg-highlight text-white px-3 py-1 rounded-full text-sm">TOOLS</span>
        <h4 class="mt-4 font-heading text-xl font-semibold">Digital Tools</h4>
        <p class="mt-2 text-gray-600">AI prompts, resources & affiliate tools.</p>
      </button>

      <button onclick="openFrame('https://tally.so/r/3jkE29')" class="p-6 rounded-xl shadow hover:shadow-lg transition text-left">
        <span class="bg-secondary text-white px-3 py-1 rounded-full text-sm">GUIDE</span>
        <h4 class="mt-4 font-heading text-xl font-semibold">Side Hustle Playbook</h4>
        <p class="mt-2 text-gray-600">Proven ways to start earning online.</p>
      </button>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer class="bg-primary text-gray-300 py-10 text-center">
  <h4 class="font-heading text-xl text-white">Debeatzgh</h4>
  <p class="mt-2 text-sm">AI • Blogging • Side Hustles • Digital Growth</p>
  <p class="mt-4 text-xs opacity-70">© 2025 Debeatzgh</p>
</footer>

<!-- FLOATING BUTTON -->
<button onclick="openFrame('https://a4b45e9212e142d58780cdadee65af5b.elf.site')" class="fixed bottom-6 right-6 bg-accent text-white w-14 h-14 rounded-full shadow-lg floating-btn text-2xl">
  ☰
</button>

<!-- IFRAME OVERLAY -->
<div id="iframeOverlay" class="fixed inset-0 bg-black/70 hidden z-50">
  <div class="absolute inset-4 bg-white rounded-xl overflow-hidden flex flex-col">
    
    <!-- CONTROLS -->
    <div class="flex items-center justify-between bg-primary text-white px-4 py-2">
      <div class="flex gap-4 text-lg">
        <button onclick="frameBack()">⟵</button>
        <button onclick="frameForward()">⟶</button>
      </div>
      <div class="flex gap-4 text-lg">
        <button onclick="toggleFullscreen()">⛶</button>
        <button onclick="closeFrame()">✕</button>
      </div>
    </div>

    <!-- IFRAME -->
    <iframe id="contentFrame" class="flex-1 w-full border-none"></iframe>
  </div>
</div>

<script>
const frame = document.getElementById('contentFrame');
const overlay = document.getElementById('iframeOverlay');

function openFrame(url){
  frame.src = url;
  overlay.classList.remove('hidden');
}

function closeFrame(){
  frame.src = '';
  overlay.classList.add('hidden');
}

function frameBack(){
  frame.contentWindow.history.back();
}

function frameForward(){
  frame.contentWindow.history.forward();
}

function toggleFullscreen(){
  const box = overlay.querySelector('div');
  if(!document.fullscreenElement){
    box.requestFullscreen();
  } else {
    document.exitFullscreen();
  }
}
</script>

</body>
</html>
