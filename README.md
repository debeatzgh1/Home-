<iframe id="JotFormIFrame-232295354707561" title="De-I" allow="geolocation; microphone; camera" src="https://www.jotform.com/app/232295354707561?appEmbedded=1" style="height:600px; width:375px; border: 0;"></iframe>




<iframe src="https://msha.ke/debeatzgh" width="100%" height="400" frameborder="0" allowfullscreen></iframe>



<div id="smart-float-container" class="float-wrapper">
    <div id="float-nudge" class="float-nudge">
        <p>Claim your <strong>.wordpress.com</strong> site!</p>
        <button onclick="dismissNudge()" class="nudge-close">×</button>
    </div>

    <div class="float-main-btn" onclick="launchWPSignup()">
        <i class="fab fa-wordpress"></i>
        <span class="btn-label">Create Site</span>
    </div>
</div>

<style>
    .float-wrapper {
        position: fixed;
        bottom: 20px;
        left: 50%;
        transform: translateX(-50%);
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 12px;
        z-index: 10005;
        font-family: 'Plus Jakarta Sans', sans-serif;
    }

    /* Floating Nudge Bubble */
    .float-nudge {
        background: rgba(10, 10, 12, 0.9);
        backdrop-filter: blur(10px);
        border: 1px solid rgba(0, 242, 255, 0.3);
        padding: 8px 15px;
        border-radius: 12px;
        color: #f0f6fc;
        font-size: 11px;
        white-space: nowrap;
        box-shadow: 0 10px 25px rgba(0,0,0,0.5);
        display: none; /* Controlled by JS */
        animation: slideUpFade 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        align-items: center;
        gap: 10px;
    }

    .nudge-close {
        background: none;
        border: none;
        color: #64748b;
        font-size: 16px;
        cursor: pointer;
        padding: 0 2px;
        line-height: 1;
    }

    .nudge-close:hover { color: #00f2ff; }

    /* Main Button */
    .float-main-btn {
        background: #00f2ff;
        color: #000;
        padding: 10px 20px;
        border-radius: 99px;
        display: flex;
        align-items: center;
        gap: 8px;
        cursor: pointer;
        font-weight: 800;
        text-transform: uppercase;
        font-size: 10px;
        letter-spacing: 1px;
        box-shadow: 0 0 20px rgba(0, 242, 255, 0.3);
        transition: all 0.3s ease;
    }

    .float-main-btn:hover {
        transform: translateY(-3px) scale(1.05);
        background: #fff;
        box-shadow: 0 0 30px rgba(255, 255, 255, 0.4);
    }

    .float-main-btn i { font-size: 14px; }

    @keyframes slideUpFade {
        from { opacity: 0; transform: translateY(15px); }
        to { opacity: 1; transform: translateY(0); }
    }

    @media (max-width: 480px) {
        .float-main-btn { padding: 10px 16px; }
        .btn-label { display: none; } /* On mobile, only show icon to save space */
    }
</style>

<script>
    const NUDGE_KEY = 'wp_nudge_dismissed';

    function showNudge() {
        const isDismissed = localStorage.getItem(NUDGE_KEY);
        if (!isDismissed) {
            document.getElementById('float-nudge').style.display = 'flex';
        }
    }

    function dismissNudge() {
        document.getElementById('float-nudge').style.display = 'none';
        // Remember dismissal for 24h
        localStorage.setItem(NUDGE_KEY, 'true');
    }

    function launchWPSignup() {
        const targetUrl = "https://debeatzgh1.github.io/Blogger-sign-up-button-/";
        
        // Use existing overlay logic if available
        if (typeof openLink === "function") {
            openLink(targetUrl);
        } else if (typeof openFrame === "function") {
            openFrame(targetUrl);
        } else {
            window.open(targetUrl, '_blank');
        }
    }

    // Auto-popup nudge after 8 seconds
    window.addEventListener('load', () => {
        setTimeout(showNudge, 8000);
    });
</script>


<div id="wp-identity-popup" class="wp-popup-overlay">
    <div class="wp-popup-card">
        <button onclick="closeWPPopup()" class="wp-close-btn">
            <i class="fas fa-times"></i>
        </button>

        <div class="wp-header">
            <div class="wp-icon-box">
                <i class="fab fa-wordpress text-2xl text-white"></i>
            </div>
            <div class="wp-badge">Free Lifetime Access</div>
        </div>

        <div class="wp-body">
            <h2 class="wp-title">Secure Your <span class="text-cyan-400">Identity</span></h2>
            
            <div class="wp-slider-container">
                <div class="wp-slider-track">
                    <div class="wp-slide">Create <strong>name.debeatzgh.com</strong> today.</div>
                    <div class="wp-slide">Professional hosting, $0.00 cost.</div>
                    <div class="wp-slide">Launch your portfolio in 60 seconds.</div>
                </div>
            </div>

            <p class="wp-description">
                Join the DeBeatzGH network. Claim your custom WordPress site and start building your digital presence with premium tools.
            </p>

            <button onclick="launchWPSignup()" class="wp-submit-btn">
                <span>Create My Free Site</span>
                <i class="fas fa-arrow-right ml-2"></i>
            </button>
            
            <p class="text-[9px] text-gray-500 mt-4 uppercase tracking-[0.2em]">No credit card required • Instant Activation</p>
        </div>
    </div>
</div>

<style>
    .wp-popup-overlay {
        position: fixed;
        inset: 0;
        background: rgba(5, 5, 7, 0.9);
        backdrop-filter: blur(8px);
        z-index: 30000;
        display: none; /* Controlled by JS */
        align-items: center;
        justify-content: center;
        padding: 20px;
    }

    .wp-popup-card {
        background: rgba(15, 15, 20, 0.95);
        width: 100%;
        max-width: 420px;
        border-radius: 24px;
        border: 1px solid rgba(0, 242, 255, 0.2);
        position: relative;
        overflow: hidden;
        box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5), 0 0 20px rgba(0, 242, 255, 0.1);
        animation: wpPopIn 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    }

    @keyframes wpPopIn {
        from { transform: scale(0.9) translateY(30px); opacity: 0; }
        to { transform: scale(1) translateY(0); opacity: 1; }
    }

    .wp-close-btn {
        position: absolute;
        top: 15px;
        right: 15px;
        width: 30px;
        height: 30px;
        border-radius: 50%;
        background: rgba(255, 255, 255, 0.05);
        border: none;
        color: #64748b;
        cursor: pointer;
        transition: 0.3s;
        z-index: 10;
    }

    .wp-close-btn:hover { background: #ef4444; color: white; }

    .wp-header {
        height: 120px;
        background: linear-gradient(135deg, #00f2ff22 0%, #3b82f622 100%);
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        position: relative;
    }

    .wp-icon-box {
        width: 50px;
        height: 50px;
        background: #21759b; /* WordPress Blue */
        border-radius: 12px;
        display: flex;
        align-items: center;
        justify-content: center;
        box-shadow: 0 0 20px rgba(33, 117, 155, 0.4);
    }

    .wp-badge {
        margin-top: 12px;
        font-size: 9px;
        font-weight: 900;
        text-transform: uppercase;
        color: #00f2ff;
        letter-spacing: 1px;
        background: rgba(0, 242, 255, 0.1);
        padding: 4px 12px;
        border-radius: 99px;
    }

    .wp-body { padding: 30px; text-align: center; }

    .wp-title {
        font-size: 24px;
        font-weight: 800;
        letter-spacing: -0.5px;
        margin-bottom: 15px;
    }

    /* Slider Styles */
    .wp-slider-container {
        height: 20px;
        overflow: hidden;
        margin-bottom: 20px;
    }

    .wp-slider-track {
        animation: wpSlideMove 9s infinite;
    }

    .wp-slide {
        height: 20px;
        font-size: 13px;
        color: #94a3b8;
    }

    @keyframes wpSlideMove {
        0%, 28% { transform: translateY(0); }
        33%, 61% { transform: translateY(-20px); }
        66%, 94% { transform: translateY(-40px); }
        100% { transform: translateY(0); }
    }

    .wp-description {
        font-size: 13px;
        color: #64748b;
        line-height: 1.6;
        margin-bottom: 25px;
    }

    .wp-submit-btn {
        width: 100%;
        background: #00f2ff;
        color: #000;
        border: none;
        padding: 16px;
        border-radius: 14px;
        font-weight: 900;
        font-size: 12px;
        text-transform: uppercase;
        letter-spacing: 1px;
        cursor: pointer;
        transition: 0.3s;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .wp-submit-btn:hover {
        background: white;
        transform: translateY(-2px);
        box-shadow: 0 10px 20px rgba(0, 242, 255, 0.2);
    }
</style>

<script>
    function showWPPopup() {
        document.getElementById('wp-identity-popup').style.display = 'flex';
        document.body.style.overflow = 'hidden';
    }

    function closeWPPopup() {
        document.getElementById('wp-identity-popup').style.display = 'none';
        document.body.style.overflow = 'auto';
    }

    function launchWPSignup() {
        const targetUrl = "https://debeatzgh1.github.io/Blogger-sign-up-button-/";
        
        // Closes the popup and opens the URL in your master overlay
        closeWPPopup();
        
        if (typeof openLink === "function") {
            openLink(targetUrl);
        } else if (typeof openFrame === "function") {
            openFrame(targetUrl);
        } else {
            window.open(targetUrl, '_blank');
        }
    }

    // Auto-trigger popup after 5 seconds for demonstration
    window.onload = () => {
        setTimeout(showWPPopup, 5000);
    };
</script>


<html lang="en-GB">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Creators Hub – AI Tools, Side Hustles & Digital Growth</title>

    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@500;600;700&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
    
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
    /* Custom Animations */
    @keyframes heartbeat {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.1); }
    }
    .animate-heartbeat { animation: heartbeat 1.5s infinite; }

    /* Glassmorphism Header for Iframe */
    .glass-header {
      background: rgba(15, 42, 68, 0.85);
      backdrop-filter: blur(12px);
      -webkit-backdrop-filter: blur(12px);
      border-bottom: 1px solid rgba(255,255,255,0.1);
    }

    /* Prevent scrolling when overlay is open */
    .no-scroll { overflow: hidden; }
    </style>
</head>

<body class="bg-bg font-body text-gray-800 transition-colors duration-300">

<header class="sticky top-0 z-40 bg-white/80 backdrop-blur-md shadow-sm border-b border-gray-100">
  <div class="max-w-7xl mx-auto px-4 py-4 flex justify-between items-center">
    <button onclick="openFrame('https://github.com/apps/dkonsult')" class="text-2xl font-heading font-bold text-primary hover:text-secondary transition">
      Debeatzgh
    </button>
    <nav class="hidden md:flex gap-8 font-medium">
      <button onclick="openFrame('https://debeatzgh1.github.io/Home-/')" class="hover:text-secondary transition">Home</button>
      <button onclick="openFrame('https://debeatzgh1.github.io/-My-Brand-Online-Digital-Products-Affiliate-Shop/')" class="hover:text-secondary transition">Products</button>
      <button onclick="openFrame('https://debeatzgh1.github.io/The-Ultimate-Guide-to-Side-Hustle/')" class="hover:text-secondary transition">Side Hustle</button>
      <button onclick="openFrame('https://msha.ke/debeatzgh')" class="hover:text-secondary transition">Hub</button>
    </nav>
    <button onclick="openFrame('https://msha.ke/debeatzgh')" class="bg-secondary text-white px-5 py-2 rounded-xl shadow-lg hover:bg-primary transition-all hover:scale-105 active:scale-95">
      Open Hub
    </button>
  </div>
</header>

<section class="max-w-7xl mx-auto px-4 py-16 grid md:grid-cols-2 gap-12 items-center">
  <div class="animate-fade-in">
    <h2 class="text-4xl md:text-5xl font-heading font-bold text-primary leading-tight">
      Build Assets with <span class="text-secondary">AI Tools</span> & Smart Side Hustles
    </h2>
    <p class="mt-6 text-lg text-gray-600">
      Premium AI tools, blogging guides, and digital products — curated to help you scale your online presence.
    </p>
    <div class="mt-8 flex flex-wrap gap-4">
      <button onclick="openFrame('https://debeatzgh1.github.io/-My-Brand-Online-Digital-Products-Affiliate-Shop/')" class="bg-secondary text-white px-8 py-3 rounded-xl shadow-md hover:scale-105 transition">
        View Products
      </button>
      <button onclick="openFrame('https://debeatzgh1.github.io/debeatzgh/')" class="border-2 border-secondary text-secondary font-bold px-8 py-3 rounded-xl hover:bg-secondary hover:text-white transition">
        Get the Guide
      </button>
    </div>
  </div>

  <div class="relative group cursor-pointer" onclick="openFrame('https://debeatzgh.wordpress.com/')">
    <div class="absolute -inset-1 bg-gradient-to-r from-secondary to-accent rounded-2xl blur opacity-25 group-hover:opacity-50 transition duration-1000"></div>
    <div class="relative bg-white rounded-xl shadow-xl overflow-hidden">
      <img src="https://images.unsplash.com/photo-1674027444485-cec3da58eef4" class="w-full h-full object-cover transform group-hover:scale-105 transition duration-500">
    </div>
  </div>
</section>

<section class="bg-white py-16">
  <div class="max-w-7xl mx-auto px-4">
    <div class="grid md:grid-cols-3 gap-8">
      <div onclick="openFrame('https://debeatzgh.wordpress.com/')" class="p-8 rounded-2xl border border-gray-100 shadow-sm hover:shadow-xl hover:-translate-y-2 transition-all cursor-pointer">
        <span class="bg-accent/10 text-accent font-bold px-3 py-1 rounded-lg text-xs">MAIN HUB</span>
        <h4 class="mt-4 font-heading text-xl font-bold">Central Link Hub</h4>
        <p class="mt-2 text-gray-600 text-sm">Every tool and platform you need, consolidated in one place.</p>
      </div>

      <div onclick="openFrame('https://github.com/apps/dkonsult')" class="p-8 rounded-2xl border border-gray-100 shadow-sm hover:shadow-xl hover:-translate-y-2 transition-all cursor-pointer">
        <span class="bg-highlight/10 text-highlight font-bold px-3 py-1 rounded-lg text-xs">RESOURCES</span>
        <h4 class="mt-4 font-heading text-xl font-bold">Digital Tools</h4>
        <p class="mt-2 text-gray-600 text-sm">Access exclusive AI prompts and digital asset libraries.</p>
      </div>

      <div onclick="openFrame('https://debeatzgh1.github.io/debeatzgh/')" class="p-8 rounded-2xl border border-gray-100 shadow-sm hover:shadow-xl hover:-translate-y-2 transition-all cursor-pointer">
        <span class="bg-secondary/10 text-secondary font-bold px-3 py-1 rounded-lg text-xs">STRATEGY</span>
        <h4 class="mt-4 font-heading text-xl font-bold">Side Hustle Guide</h4>
        <p class="mt-2 text-gray-600 text-sm">Step-by-step blueprints for launching your digital business.</p>
      </div>
    </div>
  </div>
</section>

<div class="fixed bottom-6 left-6 flex flex-col gap-3 z-40">
    <button onclick="openFrame('https://debeatzgh.wordpress.com/dkonsult/')" class="bg-accent text-white w-14 h-14 rounded-full shadow-2xl flex items-center justify-center text-2xl animate-heartbeat hover:scale-110 active:scale-95 transition">
      ❯
    </button>
</div>

<div id="iframeOverlay" class="fixed inset-0 bg-primary/95 hidden z-[100] backdrop-blur-md">
  <div class="absolute inset-2 md:inset-6 bg-white rounded-2xl shadow-2xl overflow-hidden flex flex-col border border-white/10">
    
    <div class="flex items-center justify-between glass-header text-white px-4 py-3">
      <div class="flex gap-6 items-center">
        <button onclick="frameBack()" class="hover:text-accent transition">⟵</button>
        <button onclick="frameForward()" class="hover:text-accent transition">⟶</button>
        <button id="authBtn" onclick="disableLoop()" class="text-xs font-bold px-3 py-1 border border-white/20 rounded-full hover:bg-white/10 transition">Sign In to Disable Loop</button>
      </div>
      <div class="flex gap-5 items-center">
        <button onclick="toggleFullscreen()" class="hover:text-accent text-xl">⛶</button>
        <button id="closeBtn" onclick="closeFrame()" class="bg-red-500/20 text-red-400 hover:bg-red-500 hover:text-white px-4 py-1 rounded-full text-sm font-bold transition duration-300">Wait (3s)</button>
      </div>
    </div>

    <iframe id="contentFrame" class="flex-1 w-full bg-white" title="Debeatzgh Content"></iframe>
  </div>
</div>

<script>
const frame = document.getElementById('contentFrame');
const overlay = document.getElementById('iframeOverlay');
const closeBtn = document.getElementById('closeBtn');
const authBtn = document.getElementById('authBtn');
let popupInterval;
let countdownInterval;

function openFrame(url){
  // Referral check: Don't pop if already coming from the same domain
  if (document.referrer.includes("debeatzgh")) return;

  frame.src = url;
  overlay.classList.remove('hidden');
  document.body.classList.add('no-scroll');
  startCloseCountdown();
}

function startCloseCountdown() {
  let timer = 3;
  closeBtn.disabled = true;
  closeBtn.classList.add('opacity-50', 'cursor-not-allowed');
  closeBtn.innerText = `Wait (${timer}s)`;

  clearInterval(countdownInterval);
  countdownInterval = setInterval(() => {
    timer--;
    if (timer > 0) {
      closeBtn.innerText = `Wait (${timer}s)`;
    } else {
      clearInterval(countdownInterval);
      closeBtn.innerText = "Close [X]";
      closeBtn.disabled = false;
      closeBtn.classList.remove('opacity-50', 'cursor-not-allowed');
    }
  }, 1000);
}

function closeFrame(){
  if (closeBtn.disabled) return;
  overlay.classList.add('hidden');
  document.body.classList.remove('no-scroll');
  frame.src = '';
}

function disableLoop() {
  clearInterval(popupInterval);
  authBtn.innerText = "Loop Deactivated ✓";
  authBtn.classList.add('bg-green-500/20', 'text-green-400');
  authBtn.disabled = true;
}

// 15-Second Auto Pop-up Logic
popupInterval = setInterval(() => {
    if (overlay.classList.contains('hidden')) {
        openFrame('https://debeatzgh.wordpress.com/');
    }
}, 6000);

function frameBack(){ frame.contentWindow.history.back(); }
function frameForward(){ frame.contentWindow.history.forward(); }

function toggleFullscreen(){
  const box = overlay.querySelector('div');
  if(!document.fullscreenElement) box.requestFullscreen().catch(e => console.log(e));
  else document.exitFullscreen();
}

// Initial Trigger on Load
window.onload = () => {
    setTimeout(() => openFrame('https://debeatzgh.wordpress.com/'), 1500);
};
</script>

</body>
</html>



<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DeBeatzGH | Creative Design Hub v4.0</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;600;800&display=swap');

        :root {
            --accent: #00f2ff;
            --bg-dark: #050505;
            --glass: rgba(255, 255, 255, 0.03);
            --glass-border: rgba(255, 255, 255, 0.08);
        }

        body { background-color: var(--bg-dark); font-family: 'Plus Jakarta Sans', sans-serif; color: white; scroll-behavior: smooth; }

        /* GLASS UTILS */
        .glass-card {
            background: var(--glass); backdrop-filter: blur(15px); -webkit-backdrop-filter: blur(15px);
            border: 1px solid var(--glass-border); border-radius: 24px; transition: all 0.4s ease;
        }
        .glass-card:hover { border-color: var(--accent); transform: translateY(-5px); box-shadow: 0 10px 30px rgba(0, 242, 255, 0.15); }

        /* FLOATING CHATBOT */
        #ai-chat-widget {
            position: fixed; bottom: 100px; right: 30px; width: 320px;
            height: 400px; background: #111; border: 1px solid var(--glass-border);
            border-radius: 20px; display: none; flex-direction: column; z-index: 999;
            box-shadow: 0 20px 50px rgba(0,0,0,0.8); overflow: hidden;
        }

        /* AUTO-SCROLLING CAROUSEL */
        .scroller { overflow: hidden; white-space: nowrap; background: rgba(255,255,255,0.02); padding: 20px 0; border-y: 1px solid var(--glass-border); }
        .scroller-inner { display: inline-flex; gap: 50px; animation: scroll 30s linear infinite; }
        @keyframes scroll { from { transform: translateX(0); } to { transform: translateX(-50%); } }

        /* AUTH OVERLAY */
        #auth-overlay {
            position: fixed; inset: 0; background: rgba(0,0,0,0.95);
            backdrop-filter: blur(20px); display: none; z-index: 10001; align-items: center; justify-content: center;
        }

        .status-online { width: 10px; height: 10px; background: #34A853; border-radius: 50%; display: inline-block; box-shadow: 0 0 10px #34A853; animation: pulse 2s infinite; }
        @keyframes pulse { 0% { opacity: 1; } 50% { opacity: 0.3; } 100% { opacity: 1; } }
    </style>
</head>
<body>

    <nav class="fixed top-0 w-full z-50 bg-black/60 backdrop-blur-xl border-b border-white/5 px-8 py-5 flex justify-between items-center">
        <div class="flex items-center gap-3">
            <span class="status-online"></span>
            <span class="font-extrabold text-2xl tracking-tighter">DEBEATZ<span class="text-cyan-400">GH</span></span>
        </div>
        <div class="hidden lg:flex gap-10 text-[10px] font-bold uppercase tracking-[2px] text-gray-400">
            <a href="#ideology" class="hover:text-cyan-400 transition">Ideology</a>
            <a href="#tools" class="hover:text-cyan-400 transition">Tools & Widgets</a>
            <a href="#collab" class="hover:text-cyan-400 transition">Collaborate</a>
            <a href="https://debeatzgh1.github.io/blogs/" class="hover:text-cyan-400 transition">Firebase UI</a>
        </div>
        <div class="flex gap-4">
            <button onclick="toggleAuth()" class="text-xs font-bold text-gray-300 hover:text-white transition">Sign In</button>
            <a href="https://github.com/apps/dkonsult" class="bg-cyan-500 text-black px-6 py-2 rounded-xl font-extrabold text-[10px] uppercase tracking-tighter hover:scale-105 transition">Sign Up</a>
        </div>
    </nav>

    <section class="min-h-screen pt-40 px-6 flex flex-col items-center justify-center text-center">
        <div class="inline-block px-4 py-1 border border-cyan-500/30 rounded-full text-[10px] font-bold text-cyan-400 uppercase tracking-widest mb-8" data-aos="fade-down">
            Your Personal AI Visual Designer Has Arrived
        </div>
        <h1 class="text-5xl md:text-8xl font-extrabold mb-8 leading-[0.9] tracking-tighter" data-aos="fade-up">
            WELCOME TO THE <br><span class="text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 to-blue-600">CREATIVE HUB.</span>
        </h1>
        <p class="max-w-3xl text-gray-400 text-lg md:text-xl font-light mb-12" data-aos="fade-up" data-aos-delay="100">
            Mastering the art of Blogging, Freelancing, and Digital Design through the iteration and innovation of content for multiple audiences.
        </p>
        <div class="flex flex-wrap justify-center gap-6" data-aos="zoom-in" data-aos-delay="200">
            <a href="https://wa.me/233270201181" class="bg-white text-black px-10 py-5 rounded-2xl font-black text-sm uppercase tracking-wider hover:bg-cyan-400 transition">Hire Me</a>
            <a href="#docs" class="glass-card px-10 py-5 rounded-2xl font-black text-sm uppercase tracking-wider">Productivity Tools</a>
        </div>
    </section>

    <div class="scroller">
        <div class="scroller-inner text-xs font-bold uppercase tracking-widest text-gray-500">
            <span><i class="fab fa-android mr-2"></i> Android Dev</span>
            <span><i class="fas fa-robot mr-2"></i> AI Strategy</span>
            <span><i class="fas fa-fire mr-2 text-orange-500"></i> Firebase UI</span>
            <span><i class="fas fa-shopping-cart mr-2"></i> E-Commerce</span>
            <span><i class="fas fa-share-alt mr-2"></i> Social Management</span>
            <span><i class="fas fa-map-marker-alt mr-2"></i> Google Maps Discovery</span>
            <span><i class="fab fa-android mr-2"></i> Android Dev</span>
            <span><i class="fas fa-robot mr-2"></i> AI Strategy</span>
            <span><i class="fas fa-fire mr-2 text-orange-500"></i> Firebase UI</span>
        </div>
    </div>

    <section id="docs" class="max-w-7xl mx-auto px-6 py-24">
        <div class="flex justify-between items-end mb-16">
            <div data-aos="fade-right">
                <h2 class="text-4xl font-extrabold mb-4">Google Docs Content</h2>
                <p class="text-gray-500 max-w-lg">Unlock efficiency with ready-made templates for students, entrepreneurs, and freelancers.</p>
            </div>
            <a href="https://github.com/apps/dkonsult" class="text-cyan-400 font-bold uppercase text-xs border-b border-cyan-400/30 pb-1">Enquire for Custom Docs</a>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
            <div class="glass-card p-6" data-aos="fade-up">
                <img src="https://via.placeholder.com/300x400/111/cyan?text=Business+Plan" class="w-full rounded-xl mb-6 opacity-80">
                <h3 class="font-bold text-lg mb-2">Startup Pitch Deck</h3>
                <p class="text-xs text-gray-500">Ready-to-use business strategy layout.</p>
            </div>
            <div class="glass-card p-6" data-aos="fade-up" data-aos-delay="100">
                <img src="https://via.placeholder.com/300x400/111/purple?text=CV+Template" class="w-full rounded-xl mb-6 opacity-80">
                <h3 class="font-bold text-lg mb-2">Pro Resume Node</h3>
                <p class="text-xs text-gray-500">Optimized for search & ATS parsing.</p>
            </div>
            <div class="glass-card p-6" data-aos="fade-up" data-aos-delay="200">
                <img src="https://via.placeholder.com/300x400/111/blue?text=Affiliate+Kit" class="w-full rounded-xl mb-6 opacity-80">
                <h3 class="font-bold text-lg mb-2">Affiliate Tracker</h3>
                <p class="text-xs text-gray-500">Manage links and revenue streams.</p>
            </div>
            <div class="glass-card p-6" data-aos="fade-up" data-aos-delay="300">
                <img src="https://via.placeholder.com/300x400/111/green?text=SEO+Content" class="w-full rounded-xl mb-6 opacity-80">
                <h3 class="font-bold text-lg mb-2">Blog SEO Planner</h3>
                <p class="text-xs text-gray-500">Command attention with design principles.</p>
            </div>
        </div>
    </section>

    <section id="collab" class="max-w-7xl mx-auto px-6 py-24 border-t border-white/5">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-20 items-center">
            <div data-aos="fade-right">
                <h2 class="text-5xl font-extrabold mb-8">Author Benefits & <br><span class="text-cyan-400">Collaborator Hub</span></h2>
                <div class="space-y-6">
                    <div class="flex gap-4">
                        <div class="w-10 h-10 bg-cyan-500/10 rounded-full flex items-center justify-center shrink-0"><i class="fas fa-check text-cyan-400"></i></div>
                        <div><h4 class="font-bold">Monetization Perk</h4><p class="text-sm text-gray-500">Receive rewards if your shared content gains high engagement.</p></div>
                    </div>
                    <div class="flex gap-4">
                        <div class="w-10 h-10 bg-cyan-500/10 rounded-full flex items-center justify-center shrink-0"><i class="fas fa-globe text-cyan-400"></i></div>
                        <div><h4 class="font-bold">Search Bot Exposure</h4><p class="text-sm text-gray-500">Visible to Chrome bot, search, and Google Map users.</p></div>
                    </div>
                    <div class="flex gap-4">
                        <div class="w-10 h-10 bg-cyan-500/10 rounded-full flex items-center justify-center shrink-0"><i class="fas fa-laptop-house text-cyan-400"></i></div>
                        <div><h4 class="font-bold">Work From Home</h4><p class="text-sm text-gray-500">All projects are freelance-based and remote.</p></div>
                    </div>
                </div>
            </div>
            <div class="glass-card p-10" data-aos="fade-left">
                <h3 class="text-2xl font-bold mb-6 text-center">Inquiry & Feedback</h3>
                <div class="flex flex-col gap-4">
                    <a href="https://github.com/apps/dkonsult" class="p-4 bg-white/5 border border-white/10 rounded-2xl hover:border-cyan-400 transition flex justify-between">
                        <span class="font-bold text-sm">Suggestions Form</span> <i class="fas fa-arrow-right"></i>
                    </a>
                    <a href="https://github.com/apps/dkonsult" class="p-4 bg-white/5 border border-white/10 rounded-2xl hover:border-cyan-400 transition flex justify-between">
                        <span class="font-bold text-sm">Sign In / Sign Up</span> <i class="fas fa-user-plus"></i>
                    </a>
                </div>
            </div>
        </div>
    </section>

    <div id="ai-chat-widget">
        <div class="p-4 bg-cyan-600 text-black font-black text-xs uppercase flex justify-between">
            <span>AI Assistant Bot</span>
            <button onclick="toggleChat()"><i class="fas fa-times"></i></button>
        </div>
        <div class="flex-grow p-4 overflow-y-auto text-xs text-gray-300 space-y-3" id="chat-messages">
            <p class="p-3 bg-white/5 rounded-lg border border-white/10">Welcome! I am your AI assistant. How can I help you with custom chatbot development or website creation today?</p>
        </div>
        <div class="p-3 border-t border-white/10 flex">
            <input type="text" placeholder="Type message..." class="bg-transparent text-xs w-full outline-none">
            <button class="text-cyan-400"><i class="fas fa-paper-plane"></i></button>
        </div>
    </div>

    <div class="fixed bottom-8 right-8 flex flex-col gap-4 z-50">
        <button onclick="toggleChat()" class="w-14 h-14 bg-cyan-500 text-black rounded-full shadow-2xl flex items-center justify-center hover:scale-110 transition">
            <i class="fas fa-comment-dots text-xl"></i>
        </button>
        <a href="https://wa.me/233270201181" class="w-14 h-14 bg-[#25D366] text-white rounded-full shadow-2xl flex items-center justify-center hover:scale-110 transition">
            <i class="fab fa-whatsapp text-2xl"></i>
        </a>
    </div>

    <div id="auth-overlay">
        <div class="glass-card p-10 w-full max-w-md">
            <div class="text-center mb-8">
                <h3 class="text-2xl font-extrabold mb-2">Member Node</h3>
                <p class="text-xs text-gray-500 uppercase tracking-widest font-bold">Firebase Authentication System</p>
            </div>
            <form class="space-y-4">
                <input type="email" placeholder="Email Address" class="w-full bg-white/5 border border-white/10 px-6 py-4 rounded-xl outline-none focus:border-cyan-400 transition">
                <input type="password" placeholder="Secure Password" class="w-full bg-white/5 border border-white/10 px-6 py-4 rounded-xl outline-none focus:border-cyan-400 transition">
                <button class="w-full bg-cyan-500 text-black font-black py-4 rounded-xl hover:bg-white transition">CONNECT NODE</button>
            </form>
            <div class="mt-8 flex justify-between text-[10px] font-bold text-gray-500">
                <button onclick="toggleAuth()">CANCEL</button>
                <a href="https://forms.gle/Pm5PK45qN5KGELbt7" class="text-cyan-400">APPLY FOR ACCESS</a>
            </div>
        </div>
    </div>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        AOS.init({ duration: 1000, once: true });

        function toggleAuth() {
            const el = document.getElementById('auth-overlay');
            el.style.display = (el.style.display === 'flex') ? 'none' : 'flex';
        }

        function toggleChat() {
            const el = document.getElementById('ai-chat-widget');
            el.style.display = (el.style.display === 'flex') ? 'none' : 'flex';
        }

        // Close auth on ESC
        document.addEventListener('keydown', e => { if(e.key === 'Escape') { toggleAuth(); } });
    </script>
</body>
</html>



<iframe src="https://beatzde4.blogspot.com/" width="100%" height="400" frameborder="0" allowfullscreen></iframe>


<iframe src="https://debeatzgh1.github.io/-My-Brand-Online-Digital-Products-Affiliate-Shop/" width="100%" height="400" frameborder="0" allowfullscreen></iframe>

<iframe src="https://debeatzgh1.github.io/blogs/" width="100%" height="400" frameborder="0" allowfullscreen></iframe>


<iframe src="https://debeatzgh1.github.io/Floating-buttom-Template-/" width="100%" height="400" frameborder="0" allowfullscreen></iframe>


<iframe src="https://debeatzgh1.github.io/pages" width="100%" height="400" frameborder="0" allowfullscreen></iframe>


<script src="https://gist.github.com/debeatzgh1/f68a1fc289664ed8eb57d5b94fb1b914.js"></script>
