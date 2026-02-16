<style>
        :root {
            --nav-bg: rgba(13, 17, 23, 0.9);
            --nav-border: #30363d;
            --nav-accent: #58a6ff;
            --nav-hover: #1f6feb;
            --glow-color: rgba(88, 166, 255, 0.5);
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
        }

        /* Launcher (>) */
        #nav-launcher {
            width: 38px;
            height: 38px;
            background: var(--nav-bg);
            border: 1px solid var(--nav-border);
            color: var(--nav-accent);
            border-radius: 10px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.4rem;
            backdrop-filter: blur(8px);
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(0,0,0,0.4);
        }

        #nav-launcher.open {
            color: white;
            background: var(--nav-hover);
            border-color: var(--nav-accent);
        }

        /* Button Group */
        .nav-group {
            display: flex;
            flex-direction: column;
            gap: 10px;
            pointer-events: none;
        }

        .nav-group.active {
            pointer-events: auto;
        }

        .nav-btn {
            width: 34px;
            height: 34px;
            background: var(--nav-bg);
            border: 1px solid var(--nav-border);
            color: #c9d1d9;
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            transform: scale(0.5) translateX(30px);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            text-decoration: none;
            position: relative;
        }

        /* Active/Open State for Buttons */
        .nav-group.active .nav-btn {
            opacity: 1;
            transform: scale(1) translateX(0);
        }

        /* Heartbeat Glow Animation */
        @keyframes heartbeatGlow {
            0% { box-shadow: 0 0 0 0 var(--glow-color); transform: scale(1); }
            50% { box-shadow: 0 0 15px 5px var(--glow-color); transform: scale(1.1); }
            100% { box-shadow: 0 0 0 0 var(--glow-color); transform: scale(1); }
        }

        .heartbeat-active {
            animation: heartbeatGlow 1.2s ease-in-out 2; /* Runs twice on open */
        }

        .nav-btn:hover {
            background: var(--nav-hover);
            color: white;
            border-color: var(--nav-accent);
        }

        /* Staggered transition delays for a smooth "pop-in" effect */
        .nav-group.active .nav-btn:nth-child(1) { transition-delay: 0.1s; }
        .nav-group.active .nav-btn:nth-child(2) { transition-delay: 0.2s; }
        .nav-group.active .nav-btn:nth-child(3) { transition-delay: 0.3s; }

        .nav-btn svg { width: 18px; height: 18px; }
    </style>



    <div class="nav-dock">
        <button id="nav-launcher" onclick="toggleNav()">›</button>

        <div class="nav-group" id="navGroup">
            <button class="nav-btn" onclick="window.scrollTo({top: 0, behavior: 'smooth'})">
                <svg viewbox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"><polyline points="18 15 12 9 6 15"></polyline></svg>
            </button>

            <a href="https://debeatzgh1.github.io/me-/" class="nav-btn">
                <svg viewbox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"></path><polyline points="9 22 9 12 15 12 15 22"></polyline></svg>
            </a>

            <button class="nav-btn" onclick="window.scrollTo({top: document.body.scrollHeight, behavior: 'smooth'})">
                <svg viewbox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"><polyline points="6 9 12 15 18 9"></polyline></svg>
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
                // Trigger heartbeat animation on each button when opened
                buttons.forEach((btn, index) => {
                    // Slight delay before heartbeat starts to match the pop-in
                    setTimeout(() => {
                        btn.classList.add('heartbeat-active');
                    }, (index + 1) * 200);

                    // Remove class after animation ends so it can re-trigger next time
                    setTimeout(() => {
                        btn.classList.remove('heartbeat-active');
                    }, 3000);
                });
            }
        }
    </script>


</!doctype>



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
