
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Multi-Tab Launcher — debeatzgh1</title>
  <meta name="description" content="Launcher for my GitHub Pages projects with iframe preview, auto carousel, AI summary, and tracking." />

  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&display=swap" rel="stylesheet">

  <style>
    :root{
      --bg:#0f172a;
      --card:#0b1220;
      --muted:#94a3b8;
      --accent:#7c3aed;
      --glass: rgba(255,255,255,0.03);
      --glass-2: rgba(255,255,255,0.02);
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      font-family:Inter,system-ui,-apple-system,"Segoe UI",Roboto,"Helvetica Neue",Arial;
      background:linear-gradient(180deg,#071024 0%, #07122a 60%);
      color:#e6eef8;
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      padding:28px;
    }

    .container{max-width:1200px;margin:0 auto}

    header{display:flex;align-items:center;gap:16px;margin-bottom:18px}
    .brand{
      display:flex;flex-direction:column;
      gap:4px;
    }
    .title{font-weight:800;font-size:20px;letter-spacing:-0.4px}
    .subtitle{font-size:13px;color:var(--muted)}

    /* Tabs */
    .tabs{display:flex;gap:8px;margin:12px 0 20px}
    .tab{
      background:var(--glass);
      padding:8px 12px;border-radius:10px;border:1px solid rgba(255,255,255,0.03);
      cursor:pointer;color:var(--muted);font-weight:600;font-size:13px;
    }
    .tab.active{background:linear-gradient(90deg,#2b076e,#5b21b6);color:white;box-shadow:0 6px 16px rgba(92,33,182,0.18);transform:translateY(-2px)}

    /* layout */
    .grid{display:grid;grid-template-columns: 1fr 360px; gap:18px; align-items:start}
    .left{min-height:60vh}
    .right{position:relative}

    /* Carousel */
    .carousel{background:linear-gradient(180deg, rgba(255,255,255,0.02), transparent); padding:14px;border-radius:12px;border:1px solid rgba(255,255,255,0.03);margin-bottom:16px}
    .carousel-viewport{position:relative;overflow:hidden;border-radius:10px}
    .carousel-track{display:flex;transition:transform 650ms cubic-bezier(.2,.9,.2,1)}
    .carousel-item{
      min-width:100%;display:flex;gap:12px;padding:18px;align-items:center;
    }
    .carousel-thumb{width:160px;height:90px;border-radius:8px;flex-shrink:0;overflow:hidden;background:#031029;display:flex;align-items:center;justify-content:center;color:var(--muted);font-weight:700}
    .carousel-meta{flex:1}
    .carousel-meta h3{margin:0 0 6px;font-size:18px}
    .carousel-meta p{margin:0;color:var(--muted);font-size:13px}

    .carousel-controls{display:flex;justify-content:space-between;margin-top:10px;align-items:center}
    .dots{display:flex;gap:6px}
    .dot{width:10px;height:10px;border-radius:10px;background:rgba(255,255,255,0.06);cursor:pointer}
    .dot.active{background:var(--accent);box-shadow:0 6px 12px rgba(124,58,237,0.12)}

    /* cards */
    .cards{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:12px}
    .card{
      background:linear-gradient(180deg, rgba(255,255,255,0.02), transparent);
      border-radius:12px;padding:12px;border:1px solid rgba(255,255,255,0.03);
      display:flex;flex-direction:column;gap:10px;
    }
    .thumb{
      height:120px;border-radius:8px;background:#031029;display:flex;align-items:center;justify-content:center;color:var(--muted);
      overflow:hidden;position:relative;
    }
    .thumb img{width:100%;height:100%;object-fit:cover;display:block}
    .meta h4{margin:0;font-size:15px}
    .meta p{margin:0;color:var(--muted);font-size:13px}

    .actions{display:flex;gap:8px}
    .btn{
      padding:8px 10px;border-radius:10px;background:var(--glass);border:1px solid rgba(255,255,255,0.03);cursor:pointer;color:#fff;font-weight:600;font-size:13px;
    }
    .btn.ghost{background:transparent;border:1px dashed rgba(255,255,255,0.04);color:var(--muted)}
    .btn.primary{background:linear-gradient(90deg,#7c3aed,#5b21b6);box-shadow:0 8px 24px rgba(92,33,182,0.14)}

    .pulse{
      animation: pulse 1.6s infinite;
    }
    @keyframes pulse {
      0%{ box-shadow: 0 0 0 0 rgba(124,58,237,0.15); }
      70%{ box-shadow: 0 0 0 12px rgba(124,58,237,0); }
      100%{ box-shadow: 0 0 0 0 rgba(124,58,237,0); }
    }

    /* iframe preview */
    .preview{
      background:linear-gradient(180deg, rgba(255,255,255,0.02), transparent);
      border-radius:12px;padding:12px;border:1px solid rgba(255,255,255,0.03);
      height:60vh;display:flex;flex-direction:column;
    }
    .preview-header{display:flex;align-items:center;justify-content:space-between;gap:12px;margin-bottom:10px}
    .preview-iframe{flex:1;border-radius:8px;border:1px solid rgba(255,255,255,0.04);overflow:hidden}
    iframe{width:140%;height:140%;border:0}

    .analytics{font-size:12px;color:var(--muted);margin-top:8px;display:flex;gap:12px;align-items:center}
    .summary{background:var(--glass-2);padding:10px;border-radius:10px;font-size:13px;color:var(--muted);max-height:160px;overflow:auto}

    /* responsive */
    @media (max-width:960px){
      .grid{grid-template-columns:1fr;gap:12px}
      .right{order:-1}
    }
  </style>

  <!-- Google Analytics (change MEASUREMENT_ID) -->
  <!-- Replace G-XXXXXXX with your Measurement ID or remove if not using GA -->
  <script>
    window.GA_MEASUREMENT_ID = "G-REPLACE_WITH_YOURS"; // <-- set your GA id here
    (function(){
      if(!window.GA_MEASUREMENT_ID || window.GA_MEASUREMENT_ID.includes("REPLACE")) return;
      // gtag
      window.dataLayer = window.dataLayer || [];
      function gtag(){dataLayer.push(arguments)}
      gtag('js', new Date());
      gtag('config', window.GA_MEASUREMENT_ID);
      var s = document.createElement('script');
      s.async = true;
      s.src = "https://www.googletagmanager.com/gtag/js?id=" + window.GA_MEASUREMENT_ID;
      document.head.appendChild(s);
      window.gtag = gtag;
    })();
  </script>

</head>
<body>
  <div class="container">
    <header>
      <div style="width:56px;height:56px;border-radius:12px;background:linear-gradient(135deg,#7c3aed,#06b6d4);display:flex;align-items:center;justify-content:center;font-weight:800;font-size:20px">
        D
      </div>
      <div class="brand">
        <div class="title">DebeatzGH Multi-Tab Launcher</div>
        <div class="subtitle">Quick access, previews, summaries, and tracking — built for GitHub Pages</div>
      </div>
    </header>

    <div class="tabs" role="tablist" aria-label="Filters">
      <button class="tab active" data-filter="all">All</button>
      <button class="tab" data-filter="iframe">Iframe Preview</button>
      <button class="tab" data-filter="newtab">Open New Tab</button>
      <button class="tab" data-filter="featured">Featured (Carousel)</button>
    </div>

    <div class="grid">
      <div class="left">
        <!-- Carousel -->
        <div class="carousel">
          <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px">
            <div style="font-weight:700">Featured</div>
            <div style="font-size:13px;color:var(--muted)">Auto-slide showcase</div>
          </div>
          <div class="carousel-viewport" id="carouselViewport">
            <div class="carousel-track" id="carouselTrack"></div>
          </div>
          <div class="carousel-controls">
            <div class="dots" id="carouselDots"></div>
            <div style="display:flex;gap:8px">
              <button class="btn ghost" id="prevSlide">Prev</button>
              <button class="btn ghost" id="nextSlide">Next</button>
            </div>
          </div>
        </div>

        <!-- Cards -->
        <div class="cards" id="cardsGrid" aria-live="polite"></div>
      </div>

      <aside class="right">
        <div class="preview" aria-label="Preview area">
          <div class="preview-header">
            <div style="display:flex;gap:8px;align-items:center">
              <div style="font-weight:700">Iframe Preview</div>
              <div style="font-size:12px;color:var(--muted)">Load a site into the embedded frame</div>
            </div>
            <div style="display:flex;gap:8px">
              <button class="btn ghost" id="reloadFrame">Reload</button>
              <button class="btn primary" id="openNewTabPreview">Open in New Tab</button>
            </div>
          </div>
          <div class="preview-iframe" id="previewFrameWrap">
            <iframe id="previewFrame" src=""></iframe>
          </div>

          <div style="display:flex;gap:8px;margin-top:12px">
            <input id="searchInput" placeholder="Filter by title..." style="flex:1;padding:10px;border-radius:10px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:inherit" />
            <button class="btn" id="clearSearch">Clear</button>
          </div>

          <div class="analytics" style="margin-top:10px">
            <div id="clickCount">Clicks: 0</div>
            <div id="lastAction" style="color:var(--muted)">No actions yet</div>
          </div>

          <div style="margin-top:12px">
            <div style="font-weight:700;margin-bottom:8px">AI Summary</div>
            <div style="display:flex;gap:8px;margin-bottom:8px">
              <button class="btn" id="summarizeBtn">Summarize current preview</button>
              <button class="btn ghost" id="openAIConfig">Use OpenAI (serverless)</button>
            </div>
            <div class="summary" id="summaryBox">No summary yet. Click "Summarize current preview" — uses a public CORS proxy to fetch page HTML and returns the first 2–3 sentences as a quick summary (works best on text-based pages).</div>
          </div>
        </div>
      </aside>
    </div>
  </div>

<script>
/*
  CONFIG
  - Edit the "sites" array below to add/remove pages.
  - Update GA_MEASUREMENT_ID at top of file.
  - For better AI summaries (OpenAI) add a serverless function and set OPENAI_ENDPOINT below and it will POST { url } to your server to summarize.
*/
const OPENAI_ENDPOINT = ""; // Optional: set to your serverless summary endpoint (POST { url })
const sites = [
  { title: "Home 1", url: "https://debeatzgh1.github.io/1/", desc:"Landing demo and index.", thumb: "https://via.placeholder.com/320x180.png?text=Home+1", tags:["iframe","newtab"], featured:true },
  { title: "AI Chat", url: "https://debeatzgh1.github.io/ai-chat/", desc:"An AI chat demo.", thumb: "https://via.placeholder.com/320x180.png?text=AI+Chat", tags:["iframe","newtab"], featured:true },
  { title: "Posts", url: "https://debeatzgh1.github.io/posts/", desc:"Blog posts and updates.", thumb: "https://via.placeholder.com/320x180.png?text=Posts", tags:["iframe","newtab"] },
  { title: "Personal Portfolio", url: "https://debeatzgh1.github.io/Personal-Portfolio-site-/", desc:"Portfolio site.", thumb: "https://via.placeholder.com/320x180.png?text=Portfolio", tags:["iframe","newtab"] },
  { title: "Collaborators Hub", url: "https://debeatzgh1.github.io/Debeatzgh-Collaborators-Hub/", desc:"Collaborator portal.", thumb: "https://via.placeholder.com/320x180.png?text=Hub", tags:["iframe","newtab"] },
  { title: "Decode AI Starter", url: "https://debeatzgh1.github.io/Decode-AI-starter-kit-/", desc:"Starter kit for AI projects.", thumb: "https://via.placeholder.com/320x180.png?text=Decode+AI", tags:["iframe","newtab"] },
  { title: "Guide to Side Hustle", url: "https://debeatzgh1.github.io/The-Ultimate-Guide-to-Side-Hustle/", desc:"Guides and resources.", thumb: "https://via.placeholder.com/320x180.png?text=Side+Hustle", tags:["iframe","newtab"] },
  { title: "Firebase UI", url: "https://debeatzgh1.github.io/firebase-front-end-components/", desc:"Reusable components.", thumb: "https://via.placeholder.com/320x180.png?text=Firebase+UI", tags:["iframe","newtab"] },
  { title: "Sales", url: "https://debeatzgh1.github.io/sales/", desc:"Sales pages.", thumb: "https://via.placeholder.com/320x180.png?text=Sales", tags:["iframe","newtab"] },
  { title: "Me", url: "https://debeatzgh1.github.io/me-/", desc:"About me page.", thumb: "https://via.placeholder.com/320x180.png?text=Me", tags:["iframe","newtab"] },
  { title: "DebeatzGH", url: "https://debeatzgh1.github.io/debeatzgh/", desc:"Project hub.", thumb: "https://via.placeholder.com/320x180.png?text=DebeatzGH", tags:["iframe","newtab"] },
  { title: "Side Hustle Kit", url: "https://debeatzgh1.github.io/Side-hustle-starter-kit-/", desc:"Starter kit.", thumb: "https://via.placeholder.com/320x180.png?text=Starter+Kit", tags:["iframe","newtab"] },
  { title: "Online Business Kit", url: "https://debeatzgh1.github.io/Online-business-kit/", desc:"Business resources.", thumb: "https://via.placeholder.com/320x180.png?text=Business+Kit", tags:["iframe","newtab"] },
  { title: "Tailwind Homepage", url: "https://debeatzgh1.github.io/Modern-homepage-styling-with-TailwindCSS-/", desc:"Styling guide.", thumb: "https://via.placeholder.com/320x180.png?text=Tailwind+Guide", tags:["iframe","newtab"] },
  { title: "Menu Widget", url: "https://debeatzgh1.github.io/menu-widget-/", desc:"UI widget.", thumb: "https://via.placeholder.com/320x180.png?text=Menu+Widget", tags:["iframe","newtab"] },
  { title: "MB Online", url: "https://debeatzgh1.github.io/MB--online-/", desc:"Marketplace demo.", thumb: "https://via.placeholder.com/320x180.png?text=MB+Online", tags:["iframe","newtab"] },
  { title: "Popup Generator", url: "https://debeatzgh1.github.io/popup-html-page-generator-blogger/", desc:"Popup generator tool.", thumb: "https://via.placeholder.com/320x180.png?text=Popup+Gen", tags:["iframe","newtab"] },
  { title: "Floating Dock", url: "https://debeatzgh1.github.io/-Floating-Dock-Smart-Iframe-Modal/#", desc:"Floating dock demo.", thumb: "https://via.placeholder.com/320x180.png?text=Floating+Dock", tags:["iframe","newtab"] }
];

// Simple local tracking
let clickCounter = Number(localStorage.getItem('launcher_clicks')||0);
const updateTrackingUI = (action) => {
  clickCounter++;
  localStorage.setItem('launcher_clicks', clickCounter);
  document.getElementById('clickCount').innerText = 'Clicks: ' + clickCounter;
  document.getElementById('lastAction').innerText = action + ' • ' + (new Date()).toLocaleTimeString();
  // send to gtag if configured
  if(window.gtag) {
    window.gtag('event','launcher_interaction',{event_category:'launcher',event_label:action});
  }
};

// Build UI
const cardsGrid = document.getElementById('cardsGrid');
const previewFrame = document.getElementById('previewFrame');
const previewFrameWrap = document.getElementById('previewFrameWrap');
const openNewTabPreviewBtn = document.getElementById('openNewTabPreview');
const reloadFrameBtn = document.getElementById('reloadFrame');
const summaryBox = document.getElementById('summaryBox');

function createCard(site){
  const el = document.createElement('div');
  el.className = 'card';
  el.innerHTML = `
    <div class="thumb">
      <img loading="lazy" src="${site.thumb}" alt="${site.title} thumbnail" />
    </div>
    <div class="meta">
      <h4>${site.title}</h4>
      <p>${site.desc}</p>
    </div>
    <div style="display:flex;justify-content:space-between;align-items:center">
      <div class="actions">
        <button class="btn primary" data-action="iframe" title="Open in iframe">Preview</button>
        <button class="btn ghost" data-action="newtab" title="Open in new tab">Open</button>
        <button class="btn" data-action="summary" title="AI summary">Summary</button>
      </div>
    </div>
  `;
  // wiring actions
  el.querySelector('[data-action="iframe"]').addEventListener('click', () => {
    loadPreview(site.url);
    updateTrackingUI('Preview: ' + site.title);
    // set pulse animation temporarily
    el.querySelector('.thumb').classList.add('pulse');
    setTimeout(()=>el.querySelector('.thumb').classList.remove('pulse'), 1600);
  });
  el.querySelector('[data-action="newtab"]').addEventListener('click', () => {
    window.open(site.url, '_blank', 'noopener');
    updateTrackingUI('Open New Tab: ' + site.title);
  });
  el.querySelector('[data-action="summary"]').addEventListener('click', () => {
    summarizeUrl(site.url);
    updateTrackingUI('Summary requested: ' + site.title);
  });

  return el;
}

function renderCards(filter='all', query=''){
  cardsGrid.innerHTML = '';
  const list = sites.filter(s => {
    if(filter === 'iframe') return s.tags.includes('iframe');
    if(filter === 'newtab') return s.tags.includes('newtab');
    if(filter === 'featured') return s.featured;
    return true;
  }).filter(s => s.title.toLowerCase().includes(query.toLowerCase()));
  if(list.length === 0){
    cardsGrid.innerHTML = '<div style="color:var(--muted)">No results</div>';
    return;
  }
  for(const s of list){
    cardsGrid.appendChild(createCard(s));
  }
}

// preview iframe
let currentPreview = null;
function loadPreview(url){
  // Use srcdoc trick for internal or same origin? We'll just set src
  previewFrame.src = url;
  currentPreview = url;
  updatePreviewButtons();
}

function updatePreviewButtons(){
  openNewTabPreviewBtn.onclick = ()=>{ if(currentPreview) window.open(currentPreview,'_blank','noopener'); updateTrackingUI('Open new tab from preview: '+currentPreview); }
  reloadFrameBtn.onclick = ()=>{ if(currentPreview) { previewFrame.src = currentPreview; updateTrackingUI('Reload preview: '+currentPreview); } };
}

document.getElementById('searchInput').addEventListener('input', (e)=> {
  renderCards(document.querySelector('.tab.active').dataset.filter || 'all', e.target.value);
});
document.getElementById('clearSearch').addEventListener('click', ()=>{ document.getElementById('searchInput').value=''; renderCards(document.querySelector('.tab.active').dataset.filter || 'all', ''); });

// Tabs
document.querySelectorAll('.tab').forEach(t => {
  t.addEventListener('click', ()=> {
    document.querySelectorAll('.tab').forEach(tt => tt.classList.remove('active'));
    t.classList.add('active');
    const filter = t.dataset.filter;
    renderCards(filter, document.getElementById('searchInput').value);
    // For featured switch, also jump to carousel
    if(filter === 'featured') {
      // show only featured in cards as well
      renderCards('featured', document.getElementById('searchInput').value);
    }
  });
});

// Carousel Implementation
const carouselTrack = document.getElementById('carouselTrack');
const carouselDots = document.getElementById('carouselDots');
const featured = sites.filter(s=>s.featured);
let slideIndex = 0;
function buildCarousel(){
  carouselTrack.innerHTML = '';
  carouselDots.innerHTML = '';
  if(featured.length === 0){
    carouselTrack.innerHTML = `<div class="carousel-item"><div style="padding:18px">No featured items</div></div>`;
    return;
  }
  featured.forEach((s, i) => {
    const item = document.createElement('div');
    item.className = 'carousel-item';
    item.innerHTML = `
      <div class="carousel-thumb">
        <img src="${s.thumb}" alt="${s.title}" style="width:100%;height:100%;object-fit:cover"/>
      </div>
      <div class="carousel-meta">
        <h3>${s.title}</h3>
        <p>${s.desc}</p>
        <div style="margin-top:10px;display:flex;gap:8px">
          <button class="btn primary" data-url="${s.url}">Preview</button>
          <button class="btn ghost" data-url="${s.url}">Open</button>
        </div>
      </div>
    `;
    carouselTrack.appendChild(item);
    const dot = document.createElement('div');
    dot.className = 'dot' + (i===0? ' active':'');
    dot.addEventListener('click', ()=>{ goToSlide(i); pauseAutoSlide(); });
    carouselDots.appendChild(dot);
    // action buttons
    item.querySelectorAll('button').forEach(btn => {
      btn.addEventListener('click',(ev)=>{
        const u = ev.currentTarget.dataset.url;
        if(ev.currentTarget.classList.contains('primary')){
          loadPreview(u);
          updateTrackingUI('Carousel preview: '+u);
        } else {
          window.open(u,'_blank','noopener');
          updateTrackingUI('Carousel open: '+u);
        }
      });
    });
  });
}
function goToSlide(i){
  if(i < 0) i = featured.length-1;
  if(i >= featured.length) i = 0;
  slideIndex = i;
  const width = carouselTrack.clientWidth;
  carouselTrack.style.transform = `translateX(-${i*width}px)`;
  // dots
  Array.from(carouselDots.children).forEach((d, idx)=> d.classList.toggle('active', idx===i));
}
window.addEventListener('resize', ()=>goToSlide(slideIndex));

document.getElementById('prevSlide').addEventListener('click', ()=>{ goToSlide(slideIndex-1); pauseAutoSlide(); });
document.getElementById('nextSlide').addEventListener('click', ()=>{ goToSlide(slideIndex+1); pauseAutoSlide(); });

let autoSlideInterval = null;
function startAutoSlide(){
  if(autoSlideInterval) clearInterval(autoSlideInterval);
  autoSlideInterval = setInterval(()=> { goToSlide(slideIndex+1); }, 5000);
}
function pauseAutoSlide(){ if(autoSlideInterval) { clearInterval(autoSlideInterval); autoSlideInterval = null; setTimeout(startAutoSlide, 6000); } }

// AI Summary (simple client-side)
async function summarizeUrl(url){
  summaryBox.innerText = "Generating summary… (attempting to fetch page)";
  try{
    // If a server endpoint is configured to handle OpenAI, use it (safer)
    if(OPENAI_ENDPOINT){
      const resp = await fetch(OPENAI_ENDPOINT, {
        method:'POST',headers:{'Content-Type':'application/json'},body:JSON.stringify({url})
      });
      const data = await resp.json();
      summaryBox.innerText = data.summary || (data.text || "No summary returned");
      return;
    }

    // Fallback: use public CORS proxy to fetch raw HTML. Note: reliability depends on proxy.
    const proxy = 'https://api.allorigins.win/raw?url=';
    const fetchUrl = proxy + encodeURIComponent(url);
    const res = await fetch(fetchUrl);
    if(!res.ok) throw new Error('Fetch failed: ' + res.status);
    const html = await res.text();
    // extract visible text using DOMParser
    const parser = new DOMParser();
    const doc = parser.parseFromString(html, 'text/html');
    // remove scripts and styles
    doc.querySelectorAll('script,style,nav,header,footer,form').forEach(n=>n.remove());
    const paragraphs = Array.from(doc.querySelectorAll('p')).map(p=>p.textContent.trim()).filter(Boolean);

    let summary = '';
    if(paragraphs.length >= 1){
      // pick first 2 paragraphs and trim to first 2 sentences
      const text = paragraphs.slice(0,3).join(' ');
      const sentences = text.match(/[^\.!\?]+[\.!\?]+/g) || [text];
      summary = sentences.slice(0,3).join(' ').trim();
    } else {
      // fallback: use title and meta description
      const title = doc.querySelector('title') ? doc.querySelector('title').textContent : '';
      const descMeta = doc.querySelector('meta[name="description"]') ? doc.querySelector('meta[name="description"]').getAttribute('content') : '';
      summary = [title, descMeta].filter(Boolean).join(' — ');
    }
    summaryBox.innerText = summary || 'No textual content extracted for summary.';
  } catch(err){
    console.error(err);
    summaryBox.innerText = 'Summary failed: ' + (err.message || err);
  }
}

// "OpenAI (serverless)" modal hook (basic instructions)
document.getElementById('openAIConfig').addEventListener('click', ()=>{
  alert('To use a stronger AI summary (OpenAI), deploy a small serverless endpoint that accepts { url } and returns { summary }.\n\nFor security, do NOT expose your OpenAI key in the client. Set OPENAI_ENDPOINT in the script to your endpoint URL.');
});

// quick initialization
renderCards();
buildCarousel();
startAutoSlide();
updateTrackingUI('Launcher opened');

// expose some helpers for debugging
window._launcher = { loadPreview, summarizeUrl, sites };

</script>
</body>
</html>


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

  
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CREATOR HUB| Premium Hub</title>
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
            <h1 style="font-size: 3.2rem;"> Digital</h1>
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


