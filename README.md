
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Creator OS | Matrix Hub</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;500;700&family=JetBrains+Mono:wght@400;700&display=swap');
        
        :root {
            --notify-red: #ff3e3e;
            --gist-blue: #58a6ff;
            --glass-dark: rgba(10, 15, 28, 0.9);
        }

        body { background: #02040a; color: #e2e8f0; font-family: 'Space Grotesk', sans-serif; overflow: hidden; margin: 0; }
        #bg-canvas { position: fixed; inset: 0; z-index: -1; }
        .glass { background: var(--glass-dark); backdrop-filter: blur(20px); border: 1px solid rgba(56, 189, 248, 0.1); }

        /* --- LEFT MIDDLE NOTIFICATION --- */
        #notification-wrapper {
            position: fixed;
            left: 20px;
            top: 50%;
            transform: translateY(-50%);
            display: flex;
            align-items: center;
            z-index: 9999;
        }

        #gist-notifier {
            width: 45px; /* Shrunk size */
            height: 45px;
            background: var(--glass-dark);
            border: 1px solid rgba(88, 166, 255, 0.3);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            box-shadow: 0 0 20px rgba(88, 166, 255, 0.2);
            order: 1; /* Bell on left */
            position: relative;
        }

        #notify-bubble {
            background: #fff;
            color: #0d1117;
            padding: 8px 15px;
            border-radius: 10px;
            margin-left: 12px; /* Gap from left bell */
            font-size: 11px;
            font-weight: 800;
            opacity: 0;
            transform: translateX(-10px);
            transition: 0.4s;
            white-space: nowrap;
            order: 2; /* Text on right of bell */
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
            pointer-events: none;
        }
        #notify-bubble.show { opacity: 1; transform: translateX(0); }

        /* --- HUB LAUNCHER (MINI) --- */
        #hub-launcher {
            position: fixed;
            left: 0;
            top: 50%;
            transform: translateY(-50%);
            background: var(--glass-dark);
            color: var(--gist-blue);
            padding: 15px 8px;
            border-radius: 0 10px 10px 0;
            font-size: 9px;
            font-weight: 900;
            writing-mode: vertical-rl;
            text-orientation: mixed;
            letter-spacing: 2px;
            border: 1px solid rgba(88, 166, 255, 0.2);
            border-left: none;
            cursor: pointer;
            display: none;
            z-index: 9998;
            transition: 0.3s;
        }
        #hub-launcher:hover { background: var(--gist-blue); color: #000; }

        /* --- FORM OVERLAY --- */
        #gist-overlay { position: fixed; inset: 0; background: rgba(0,0,0,0.95); backdrop-filter: blur(10px); display: none; z-index: 10000; justify-content: center; align-items: center; }
        .modal-container { width: 95%; max-width: 600px; height: 85vh; background: #0d1117; border-radius: 20px; display: flex; flex-direction: column; border: 1px solid #30363d; overflow: hidden; }
        iframe { width: 100%; height: 100%; border: none; display: none; }
        
        .spinner-box { display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 15px; }
        .spinner { width: 30px; height: 30px; border: 2px solid rgba(88, 166, 255, 0.1); border-top: 2px solid var(--gist-blue); border-radius: 50%; animation: spin 0.8s linear infinite; }
        @keyframes spin { 100% { transform: rotate(360deg); } }

        @keyframes shake { 0%, 100% { transform: rotate(0); } 20% { transform: rotate(10deg); } 40% { transform: rotate(-10deg); } }
        .shake { animation: shake 0.5s ease-in-out; }
    </style>
</head>
<body>

    <audio id="notify-sound" src="https://assets.mixkit.co/active_storage/sfx/2358/2358-preview.mp3"></audio>

    <canvas id="bg-canvas"></canvas>

    <div id="main-ui" class="max-w-4xl mx-auto px-6 pt-20">
        <h1 class="text-4xl font-black text-white">MATRIX_<span class="text-cyan-500">OS</span></h1>
        <p class="text-slate-500 text-xs mt-2 tracking-widest">SYSTEM STATUS: NOMINAL</p>
    </div>

    <div id="notification-wrapper">
        <div id="gist-notifier" onclick="handleFormLaunch()">
            <span id="comment-badge" class="absolute -top-1 -right-1 bg-red-500 w-3 h-3 rounded-full hidden"></span>
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#58a6ff" stroke-width="2.5"><path d="M18 8A6 6 0 0 0 6 8c0 7-3 9-3 9h18s-3-2-3-9"></path><path d="M13.73 21a2 2 0 0 1-3.46 0"></path></svg>
        </div>
        <div id="notify-bubble"><span id="type-text"></span></div>
    </div>

    <button id="hub-launcher" onclick="handleFormLaunch()">OPEN_INPUT_FORM</button>

    <div id="gist-overlay">
        <div class="modal-container">
            <div class="flex justify-between items-center p-4 bg-[#161b22] border-b border-[#30363d]">
                <span class="text-[9px] font-bold text-slate-500 tracking-widest uppercase">Secure_Form_Channel</span>
                <button onclick="closeOverlay()" class="text-white text-xl">&times;</button>
            </div>
            <div id="form-loader" class="spinner-box">
                <div class="spinner"></div>
                <div class="text-[9px] text-cyan-500 font-bold uppercase tracking-tighter">Connecting to Server...</div>
            </div>
            <iframe id="form-iframe" src=""></iframe>
        </div>
    </div>

    <script>
        // Background Particles
        const canvas = document.getElementById('bg-canvas');
        const ctx = canvas.getContext('2d');
        let particles = [];
        function initBg() {
            canvas.width = window.innerWidth; canvas.height = window.innerHeight;
            particles = Array.from({length: 40}, () => ({
                x: Math.random()*canvas.width, y: Math.random()*canvas.height,
                vx: (Math.random()-0.5)*0.2, vy: (Math.random()-0.5)*0.2
            }));
        }
        function animateBg() {
            ctx.clearRect(0,0,canvas.width,canvas.height);
            particles.forEach(p => {
                p.x += p.vx; p.y += p.vy;
                if(p.x<0||p.x>canvas.width) p.vx*=-1;
                if(p.y<0||p.y>canvas.height) p.vy*=-1;
                ctx.fillStyle = 'rgba(88,166,255,0.1)';
                ctx.beginPath(); ctx.arc(p.x, p.y, 1, 0, Math.PI*2); ctx.fill();
            });
            requestAnimationFrame(animateBg);
        }

        // Typewriter logic
        function typeWriter(text, i=0) {
            if (i < text.length) {
                document.getElementById('type-text').innerHTML += text.charAt(i);
                setTimeout(() => typeWriter(text, i+1), 40);
            }
        }

        function checkNotification() {
            if (localStorage.getItem('form_seen')) {
                document.getElementById('notification-wrapper').style.display = 'none';
                document.getElementById('hub-launcher').style.display = 'block';
            } else {
                setTimeout(() => {
                    document.getElementById('notify-bubble').classList.add('show');
                    document.getElementById('comment-badge').classList.remove('hidden');
                    document.getElementById('gist-notifier').classList.add('shake');
                    typeWriter("Incoming Form Request...");
                    document.addEventListener('mouseover', () => { document.getElementById('notify-sound').play().catch(()=>{}) }, {once:true});
                }, 1500);
            }
        }

        function handleFormLaunch() {
            const iframe = document.getElementById('form-iframe');
            const overlay = document.getElementById('gist-overlay');
            const loader = document.getElementById('form-loader');
            
            overlay.style.display = 'flex';
            if (iframe.src === "" || iframe.src !== "https://form.svhrt.com/60f4a0aeedc1993c8c7b3989") {
                iframe.src = "https://form.svhrt.com/60f4a0aeedc1993c8c7b3989";
                iframe.onload = () => {
                    loader.style.display = 'none';
                    iframe.style.display = 'block';
                };
            }
            
            localStorage.setItem('form_seen', 'true');
            document.getElementById('notification-wrapper').style.display = 'none';
            document.getElementById('hub-launcher').style.display = 'block';
        }

        function closeOverlay() { document.getElementById('gist-overlay').style.display = 'none'; }

        window.onload = () => { initBg(); animateBg(); checkNotification(); };
        window.onresize = initBg;
    </script>
</body>
</html>



## Welcome to creators Hub, Access Your productivity tools in one place 
Through these channels, are insights on technology, artificial intelligence, and productivity. It is a digital hub focused on empowering entrepreneurs, creators, and businesses in the digital space. Offers are a range of services including custom chatbot development, website creation, and mobile app building, alongside digital guides and strategic partnerships.,  I also provide tools and strategies for building an online presence, generating revenue, and leveraging AI for productivity and business growth. 


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        :root {
            --nav-bg: rgba(13, 17, 23, 0.95);
            --nav-border: #30363d;
            /* Updated to Deep Pink */
            --nav-accent: #FF1493; 
            --nav-hover: #FF69B4;
            --glow-color: rgba(255, 20, 147, 0.5);
        }

        /* Dock Container */
        .nav-dock {
            position: fixed;
            right: 20px;
            top: 50%;
            transform: translateY(-50%);
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 15px;
            z-index: 10000;
            font-family: sans-serif;
        }

        /* Launcher Button */
        #nav-launcher {
            width: 42px;
            height: 42px;
            background: var(--nav-bg);
            border: 2px solid var(--nav-border);
            color: var(--nav-accent);
            border-radius: 12px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            backdrop-filter: blur(8px);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            box-shadow: 0 4px 15px rgba(0,0,0,0.4);
            padding: 0;
            line-height: 1;
        }

        #nav-launcher.open {
            color: white;
            background: var(--nav-accent);
            border-color: var(--nav-accent);
            transform: rotate(-180deg);
        }

        /* Button Group */
        .nav-group {
            display: flex;
            flex-direction: column;
            gap: 12px;
            pointer-events: none;
            visibility: hidden;
        }

        .nav-group.active {
            pointer-events: auto;
            visibility: visible;
        }

        .nav-btn {
            width: 38px;
            height: 38px;
            background: var(--nav-bg);
            border: 1px solid var(--nav-border);
            color: #c9d1d9;
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            transform: scale(0.5) translateX(40px);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            text-decoration: none;
        }

        /* Active State for Buttons */
        .nav-group.active .nav-btn {
            opacity: 1;
            transform: scale(1) translateX(0);
        }

        /* Heartbeat Glow Animation */
        @keyframes heartbeatGlow {
            0% { box-shadow: 0 0 0 0 var(--glow-color); transform: scale(1); }
            50% { box-shadow: 0 0 15px 8px var(--glow-color); transform: scale(1.15); }
            100% { box-shadow: 0 0 0 0 var(--glow-color); transform: scale(1); }
        }

        .heartbeat-active {
            animation: heartbeatGlow 1s ease-in-out;
        }

        .nav-btn:hover {
            background: var(--nav-accent);
            color: white;
            border-color: var(--nav-accent);
        }

        /* Staggered transition delays */
        .nav-group.active .nav-btn:nth-child(1) { transition-delay: 0.1s; }
        .nav-group.active .nav-btn:nth-child(2) { transition-delay: 0.2s; }
        .nav-group.active .nav-btn:nth-child(3) { transition-delay: 0.3s; }

        .nav-btn svg { width: 20px; height: 20px; }
    </style>
</head>
<body>

    <div class="nav-dock">
        <button id="nav-launcher" onclick="toggleNav()">›</button>

        <div class="nav-group" id="navGroup">
            <button class="nav-btn" onclick="window.scrollTo({top: 0, behavior: 'smooth'})" title="Scroll to Top">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"><polyline points="18 15 12 9 6 15"></polyline></svg>
            </button>

            <a href="https://debeatzgh1.github.io/Home-/" class="nav-btn" title="Go Home">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"></path><polyline points="9 22 9 12 15 12 15 22"></polyline></svg>
            </a>

            <button class="nav-btn" onclick="window.scrollTo({top: document.body.scrollHeight, behavior: 'smooth'})" title="Scroll to Bottom">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"><polyline points="6 9 12 15 18 9"></polyline></svg>
            </button>
        </div>
    </div>

    <script>
        function toggleNav() {
            const group = document.getElementById('navGroup');
            const launcher = document.getElementById('nav-launcher');
            const buttons = document.querySelectorAll('.nav-btn');
            
            const isOpen = group.classList.toggle('active');
            launcher.classList.toggle('open');
            launcher.innerText = isOpen ? '‹' : '›';

            if (isOpen) {
                buttons.forEach((btn, index) => {
                    // Remove previous instance if any
                    btn.classList.remove('heartbeat-active');
                    
                    // Trigger reflow to restart animation
                    void btn.offsetWidth; 

                    // Stagger the pulse
                    setTimeout(() => {
                        btn.classList.add('heartbeat-active');
                    }, (index + 1) * 150);
                });
            }
        }
    </script>
</body>
</html>



<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        :root {
            --banner-bg: rgba(13, 17, 23, 0.85);
            --accent-pink: #FF1493;
            --accent-glow: rgba(255, 20, 147, 0.4);
            --text-white: #ffffff;
            --border-glass: rgba(255, 255, 255, 0.1);
        }

        /* Floating Banner Container */
        .top-floating-banner {
            position: fixed;
            top: 15px;
            left: 50%;
            transform: translateX(-50%);
            width: 90%;
            max-width: 700px;
            height: 50px;
            background: var(--banner-bg);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid var(--border-glass);
            border-radius: 100px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 10px 0 25px;
            z-index: 10000;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.5);
            overflow: hidden;
            animation: slideDown 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        /* Carousel Wrapper */
        .carousel-wrapper {
            flex: 1;
            overflow: hidden;
            position: relative;
            margin-right: 15px;
        }

        .carousel-content {
            display: flex;
            white-space: nowrap;
            animation: scrollText 15s linear infinite;
        }

        .carousel-content span {
            font-family: 'Segoe UI', Roboto, sans-serif;
            font-size: 0.85rem;
            color: var(--text-white);
            font-weight: 500;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        /* Launch Button */
        .banner-btn {
            background: var(--accent-pink);
            color: white;
            border: none;
            padding: 8px 20px;
            border-radius: 50px;
            font-size: 0.8rem;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 6px;
            box-shadow: 0 0 15px var(--accent-glow);
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .banner-btn:hover {
            transform: scale(1.05);
            background: #ff69b4;
            box-shadow: 0 0 25px var(--accent-glow);
        }

        /* Modal Overlay for Milkshake */
        #milkshake-modal {
            position: fixed;
            inset: 0;
            background: rgba(0, 0, 0, 0.9);
            display: none;
            z-index: 10001;
            flex-direction: column;
            animation: fadeIn 0.3s ease;
        }

        .modal-header {
            padding: 15px 25px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #161b22;
        }

        .close-btn {
            background: #f85149;
            color: white;
            border: none;
            padding: 5px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
        }

        #msha-iframe {
            width: 100%;
            flex-grow: 1;
            border: none;
        }

        /* Animations */
        @keyframes scrollText {
            0% { transform: translateX(100%); }
            100% { transform: translateX(-100%); }
        }

        @keyframes slideDown {
            from { transform: translate(-50%, -100px); opacity: 0; }
            to { transform: translate(-50%, 0); opacity: 1; }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        /* Mobile Adjustments */
        @media (max-width: 600px) {
            .carousel-content span { font-size: 0.75rem; }
            .banner-btn span { display: none; }
            .banner-btn { padding: 8px 12px; }
        }
    </style>
</head>
<body>

    <div class="top-floating-banner">
        <div class="carousel-wrapper">
            <div class="carousel-content">
                <span>
                    💻 Access your lifestyle, productivity tools and ideas All in one place! 🚀 💡 📈
                </span>
            </div>
        </div>
        
        <button class="banner-btn" onclick="openMilkshake()">
            <span>Launch Hub</span> ⭐️
        </button>
    </div>

    <div id="milkshake-modal">
        <div class="modal-header">
            <span style="color:white; font-family: sans-serif; font-weight: bold;">Debeatzgh Hub</span>
            <button class="close-btn" onclick="closeMilkshake()">✕ Close</button>
        </div>
        <iframe id="msha-iframe" src=""></iframe>
    </div>

    <script>
        function openMilkshake() {
            const modal = document.getElementById('milkshake-modal');
            const iframe = document.getElementById('msha-iframe');
            
            // Set source only when clicked to save performance
            iframe.src = "https://msha.ke/debeatzgh";
            modal.style.display = "flex";
            document.body.style.overflow = "hidden"; // Disable scroll
        }

        function closeMilkshake() {
            const modal = document.getElementById('milkshake-modal');
            const iframe = document.getElementById('msha-iframe');
            
            modal.style.display = "none";
            iframe.src = ""; // Stop the iframe content
            document.body.style.overflow = "auto"; // Re-enable scroll
        }
    </script>

</body>
</html>




<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Debeatzgh Digital Ecosystem</title>
    <style>
        :root {
            --bg: #0d1117;
            --card: #161b22;
            --accent: #FF1493; /* Deep Pink */
            --accent-glow: rgba(255, 20, 147, 0.3);
            --text-main: #e6edf3;
            --text-dim: #8b949e;
            --border: #30363d;
        }

        * { box-sizing: border-box; transition: all 0.3s ease; }

        body {
            margin: 0;
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            background-color: var(--bg);
            color: var(--text-main);
            overflow-x: hidden;
        }

        /* --- SECTION 1: INTERACTIVE BANNER OVERLAYS --- */
        .banner-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            padding: 40px 5%;
            margin-top: 20px;
        }

        .banner-card {
            position: relative;
            height: 180px;
            background: linear-gradient(135deg, #1c2128 0%, #0d1117 100%);
            border: 1px solid var(--border);
            border-radius: 16px;
            overflow: hidden;
            cursor: pointer;
            display: flex;
            flex-direction: column;
            justify-content: center;
            padding: 25px;
        }

        .banner-card:hover {
            border-color: var(--accent);
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        .banner-card h3 {
            margin: 0;
            font-size: 1.2rem;
            color: var(--accent);
        }

        .banner-card p {
            font-size: 0.85rem;
            color: var(--text-dim);
            margin: 10px 0 0;
        }

        .banner-card::after {
            content: 'Launch Preview ↗';
            position: absolute;
            bottom: 15px;
            right: 15px;
            font-size: 0.7rem;
            font-weight: bold;
            opacity: 0.5;
        }

        /* --- SECTION 2: AUTO-SLIDE GLOBAL FEED --- */
        .marquee-section {
            background: #000;
            padding: 50px 0;
            border-top: 1px solid var(--border);
            overflow: hidden;
        }

        .marquee-container {
            display: flex;
            width: max-content;
            animation: scroll 60s linear infinite;
        }

        .marquee-item {
            display: flex;
            align-items: center;
            gap: 15px;
            padding: 15px 30px;
            background: var(--card);
            border: 1px solid var(--border);
            border-radius: 50px;
            margin-right: 20px;
            text-decoration: none;
            color: inherit;
            white-space: nowrap;
        }

        .marquee-item:hover {
            border-color: var(--accent);
            background: #21262d;
        }

        .badge {
            background: var(--accent);
            color: white;
            padding: 2px 8px;
            border-radius: 4px;
            font-size: 0.6rem;
            font-weight: bold;
            text-transform: uppercase;
        }

        .category-tag {
            color: var(--text-dim);
            font-size: 0.7rem;
            font-family: monospace;
        }

        /* --- IFRAME OVERLAY SYSTEM --- */
        #overlay-container {
            position: fixed;
            inset: 0;
            background: rgba(0,0,0,0.9);
            backdrop-filter: blur(10px);
            display: none;
            z-index: 10000;
            flex-direction: column;
        }

        .overlay-header {
            height: 60px;
            padding: 0 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            background: var(--card);
            border-bottom: 1px solid var(--border);
        }

        .close-trigger {
            background: var(--accent);
            color: white;
            border: none;
            padding: 8px 20px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
        }

        #overlay-iframe {
            width: 100%;
            flex-grow: 1;
            border: none;
        }

        /* --- ANIMATIONS --- */
        @keyframes scroll {
            0% { transform: translateX(0); }
            100% { transform: translateX(-50%); }
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.95); }
            to { opacity: 1; transform: scale(1); }
        }

        .section-title {
            padding: 0 5%;
            font-size: 0.8rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            color: var(--accent);
            margin-top: 40px;
        }
    </style>
</head>
<body>

    <h2 class="section-title">01. Interactive Workspaces</h2>
    <div class="banner-grid" id="bannerGrid">
        </div>

    <h2 class="section-title">02. Global Resource Marquee</h2>
    <div class="marquee-section">
        <div class="marquee-container" id="marqueeTrack">
            </div>
    </div>

    <div id="overlay-container">
        <div class="overlay-header">
            <span id="overlay-title" style="font-weight: bold; color: var(--accent);">Resource Preview</span>
            <button class="close-trigger" onclick="closeOverlay()">Close Workspace</button>
        </div>
        <iframe id="overlay-iframe" src=""></iframe>
    </div>

    <script>
        const resources = [
            { name: "Master Hub", url: "https://debeatzgh1.github.io/1/", cat: "System", desc: "Core ecosystem dashboard" },
            { name: "AI Chat Assistant", url: "https://debeatzgh1.github.io/ai-chat/", cat: "Intelligence", desc: "Next-gen LLM interface" },
            { name: "Community Feed", url: "https://debeatzgh1.github.io/posts/", cat: "Social", desc: "Latest updates and threads" },
            { name: "Digital Portfolio", url: "https://debeatzgh1.github.io/Personal-Portfolio-site-/", cat: "Personal", desc: "Showcase of expertise" },
            { name: "Collaborators Hub", url: "https://debeatzgh1.github.io/Debeatzgh-Collaborators-Hub/", cat: "Growth", desc: "Network & Build together" },
            { name: "AI Starter Kit", url: "https://debeatzgh1.github.io/Decode-AI-starter-kit-/", cat: "Tools", desc: "Beginner AI resource guide" },
            { name: "Side Hustle Guide", url: "https://debeatzgh1.github.io/The-Ultimate-Guide-to-Side-Hustle/", cat: "Business", desc: "Monetize your skills" },
            { name: "Frontend Components", url: "https://debeatzgh1.github.io/firebase-front-end-components/", cat: "Dev", desc: "Reusable UI logic" },
            { name: "Sales Engine", url: "https://debeatzgh1.github.io/sales/", cat: "Business", desc: "Convert leads to customers" },
            { name: "Identity Bio", url: "https://msha.ke/debeatzgh", cat: "Profile", desc: "Unified link management" },
            { name: "Tailwind Styling", url: "https://debeatzgh1.github.io/Modern-homepage-styling-with-TailwindCSS-/", cat: "Design", desc: "Modern utility CSS" },
            { name: "Popup Generator", url: "https://debeatzgh1.github.io/popup-html-page-generator-blogger/", cat: "Marketing", desc: "Custom lead capture" },
            { name: "Floating Dock", url: "https://debeatzgh1.github.io/-Floating-Dock-Smart-Iframe-Modal/#/", cat: "Utility", desc: "Smart navigation system" }
        ];

        // Load Section 1 (Banners)
        const grid = document.getElementById('bannerGrid');
        resources.forEach(res => {
            const div = document.createElement('div');
            div.className = 'banner-card';
            div.onclick = () => openOverlay(res.url, res.name);
            div.innerHTML = `
                <span class="category-tag">// ${res.cat}</span>
                <h3>${res.name}</h3>
                <p>${res.desc}</p>
            `;
            grid.appendChild(div);
        });

        // Load Section 2 (Marquee) - Doubled for infinite effect
        const track = document.getElementById('marqueeTrack');
        [...resources, ...resources].forEach(res => {
            const a = document.createElement('a');
            a.className = 'marquee-item';
            a.href = res.url;
            a.target = "_blank";
            a.innerHTML = `
                <span class="badge">${res.cat}</span>
                <strong>${res.name}</strong>
                <span class="category-tag">↗ New Tab</span>
            `;
            track.appendChild(a);
        });

        function openOverlay(url, name) {
            const overlay = document.getElementById('overlay-container');
            const iframe = document.getElementById('overlay-iframe');
            document.getElementById('overlay-title').innerText = name + " [Workspace]";
            
            iframe.src = url;
            overlay.style.display = 'flex';
            document.body.style.overflow = 'hidden';
        }

        function closeOverlay() {
            document.getElementById('overlay-container').style.display = 'none';
            document.getElementById('overlay-iframe').src = '';
            document.body.style.overflow = 'auto';
        }
    </script>
</body>
</html>
