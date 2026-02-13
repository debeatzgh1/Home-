
<html lang="en">
<head>
    <style>
        :root {
            --nav-glass: rgba(13, 17, 23, 0.85);
            --nav-border: rgba(255, 255, 255, 0.1);
            --color-guide: #00f2fe; /* Cyan */
            --color-home: #70ff03;  /* Green */
            --color-social: #ff007a; /* Pink */
            --color-top: #ffffff;   /* White */
        }

        .side-nav {
            position: fixed;
            top: 50%;
            transform: translateY(-50%);
            z-index: 9999;
            display: flex;
            flex-direction: column;
            gap: 10px; /* Tightened gap */
        }

        .nav-left { left: 0; }
        .nav-right { right: 0; }

        .nav-item {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 48px;
            height: 48px;
            background: var(--nav-glass);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            border: 1px solid var(--nav-border);
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            text-decoration: none;
            position: relative;
            overflow: hidden;
        }

        .nav-left .nav-item { border-radius: 0 10px 10px 0; border-left: none; }
        .nav-right .nav-item { border-radius: 10px 0 0 10px; border-right: none; }

        /* Specific Item Colors */
        .item-guide { color: var(--color-guide); }
        .item-social { color: var(--color-social); }
        .item-home { color: var(--color-home); }
        .item-top { color: var(--color-top); opacity: 0; visibility: hidden; transition: 0.5s; }
        .item-top.visible { opacity: 1; visibility: visible; }

        /* Shake Animation */
        .shake-anim { animation: timely-shake 0.5s ease-in-out; }
        @keyframes timely-shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(4px); }
            50% { transform: translateX(-4px); }
        }

        /* Hover Glows */
        .nav-item:hover { width: 60px; }
        .item-guide:hover { background: var(--color-guide); color: #000; }
        .item-social:hover { background: var(--color-social); color: #fff; }
        .item-home:hover { background: var(--color-home); color: #000; }
        .item-top:hover { background: #fff; color: #000; }

        /* Tooltip Labels */
        .nav-item::after {
            content: attr(data-label);
            position: absolute;
            font-size: 9px;
            font-weight: 900;
            white-space: nowrap;
            opacity: 0;
            transition: 0.3s;
        }
        .nav-left .nav-item::after { left: 65px; color: inherit; }
        .nav-right .nav-item::after { right: 65px; color: inherit; }
        .nav-item:hover::after { opacity: 1; }

        svg { width: 22px; height: 22px; pointer-events: none; }
    </style>
</head>
<body>

    <div class="side-nav nav-left">
        <a href="https://debeatzgh1.github.io/Blogger-sign-up-button-/" target="_blank" class="nav-item item-guide shake-trigger" data-label="Essential Guides">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 19.5A2.5 2.5 0 0 1 6.5 17H20"></path><path d="M6.5 2H20v20H6.5A2.5 2.5 0 0 1 4 19.5v-15A2.5 2.5 0 0 1 6.5 2z"></path></svg>
        </a>
        <a href="https://debeatzgh1.github.io/Blogger-sign-up-button-/" target="_blank" class="nav-item item-social shake-trigger" data-label="Join Community">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 11.5a8.38 8.38 0 0 1-.9 3.8 8.5 8.5 0 1 1-7.6-10.4 8.38 8.38 0 0 1 3.9 1.1L21 3z"></path></svg>
        </a>
    </div>

    <div class="side-nav nav-right">
        <a href="https://debeatzgh1.github.io/blogs/" target="_blank" class="nav-item item-home shake-trigger" data-label="Home Dashboard">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"></path><polyline points="9 22 9 12 15 12 15 22"></polyline></svg>
        </a>
        <div onclick="scrollToTop()" class="nav-item item-top" id="backToTop" data-label="Back To Top">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="18 15 12 9 6 15"></polyline></svg>
        </div>
    </div>

    <script>
        // 1. Shaking Logic
        function startShaking() {
            const icons = document.querySelectorAll('.shake-trigger');
            setInterval(() => {
                icons.forEach((icon, index) => {
                    setTimeout(() => {
                        icon.classList.add('shake-anim');
                        setTimeout(() => icon.classList.remove('shake-anim'), 500);
                    }, index * 200);
                });
            }, 6000); // Shakes every 6 seconds
        }

        // 2. Back to Top Logic
        const topBtn = document.getElementById('backToTop');
        window.onscroll = function() {
            if (document.body.scrollTop > 300 || document.documentElement.scrollTop > 300) {
                topBtn.classList.add('visible');
            } else {
                topBtn.classList.remove('visible');
            }
        };

        function scrollToTop() {
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        window.onload = startShaking;
    </script>
</body>
</html>


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        :root {
            --primary-gradient: linear-gradient(135deg, #1e293b 0%, #334155 100%);
            --accent-blue: #38bdf8;
            --accent-green: #10b981;
            --text-light: #f8fafc;
        }

        .hero-banner {
            font-family: 'Inter', -apple-system, sans-serif;
            background: var(--primary-gradient);
            color: var(--text-light);
            padding: 60px 20px;
            border-radius: 16px;
            text-align: center;
            position: relative;
            overflow: hidden;
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
            margin: 20px auto;
            max-width: 1000px;
        }

        /* Animated Background Element */
        .hero-banner::before {
            content: "";
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(56, 189, 248, 0.1) 0%, transparent 60%);
            animation: rotate 20s linear infinite;
        }

        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        .hero-content {
            position: relative;
            z-index: 2;
        }

        .hero-tagline {
            background: rgba(56, 189, 248, 0.15);
            color: var(--accent-blue);
            padding: 6px 16px;
            border-radius: 20px;
            font-size: 0.9rem;
            font-weight: 600;
            display: inline-block;
            margin-bottom: 20px;
            border: 1px solid rgba(56, 189, 248, 0.3);
        }

        .hero-title {
            font-size: 2.5rem;
            font-weight: 800;
            margin: 0 0 15px 0;
            letter-spacing: -0.02em;
        }

        .hero-subtitle {
            font-size: 1.1rem;
            max-width: 700px;
            margin: 0 auto 30px auto;
            color: #cbd5e1;
            line-height: 1.6;
        }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 15px;
            margin-bottom: 35px;
        }

        .service-pill {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 12px;
            border-radius: 12px;
            backdrop-filter: blur(5px);
            font-size: 0.85rem;
            transition: 0.3s;
        }

        .service-pill:hover {
            background: rgba(255, 255, 255, 0.1);
            border-color: var(--accent-blue);
            transform: translateY(-3px);
        }

        .cta-button {
            background: var(--accent-blue);
            color: #0f172a;
            padding: 14px 32px;
            border-radius: 8px;
            text-decoration: none;
            font-weight: 700;
            display: inline-block;
            transition: 0.3s;
        }

        .cta-button:hover {
            background: #7dd3fc;
            box-shadow: 0 0 20px rgba(56, 189, 248, 0.4);
        }

        @media (max-width: 600px) {
            .hero-title { font-size: 1.8rem; }
            .hero-subtitle { font-size: 1rem; }
        }
    </style>
</head>
<body>

<section class="hero-banner">
    <div class="hero-content">
        <span class="hero-tagline">AI & DIGITAL CREATOR HUB</span>
        <h1 class="hero-title">Empowering the Next Generation of Digital Entrepreneurs</h1>
        <p class="hero-subtitle">
            Insights on technology, AI, and productivity. We build custom chatbots, websites, and mobile apps to help you scale your online presence.
        </p>

        <div class="services-grid">
            <div class="service-pill">🤖 Chatbot Dev</div>
            <div class="service-pill">🌐 Web Design</div>
            <div class="service-pill">📱 App Building</div>
            <div class="service-pill">📈 AI Strategy</div>
        </div>

        <a href="#contact" class="cta-button">Start Building Your Assets</a>
        
        <p style="margin-top: 25px; font-size: 0.8rem; color: #94a3b8; font-style: italic;">
            "Mastering the art of Digital design involves the iteration and innovation of templates for multiple audiences."
        </p>
    </div>
</section>

</body>
</html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Floating Sales Banner</title>
<style>
    /* 1. The Container */
    #float-banner {
        position: fixed;
        bottom: 20px;
        right: 20px;
        width: 320px;
        background-color: #ffffff; /* White background */
        box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        border-radius: 12px;
        border-left: 5px solid #ff4757; /* Accent color */
        padding: 15px;
        z-index: 9999;
        font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
        cursor: pointer;
        opacity: 0; /* Start hidden for fade-in effect */
        transform: translateY(20px);
        transition: all 0.5s ease;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    /* 2. Visible State (added by JS) */
    #float-banner.visible {
        opacity: 1;
        transform: translateY(0);
    }

    /* 3. The Content Area */
    .banner-content {
        flex-grow: 1;
        overflow: hidden;
        height: 24px; /* Fixed height for text slider */
        position: relative;
    }

    .slide-text {
        display: none; /* Hide all by default */
        font-size: 16px;
        font-weight: 600;
        color: #333;
        animation: fadeUp 0.5s ease-in-out;
    }

    .slide-text.active {
        display: block; /* Show active one */
    }

    .slide-sub {
        font-size: 12px;
        color: #666;
        font-weight: normal;
        margin-left: 5px;
    }

    /* 4. The Close Button */
    .close-btn {
        background: none;
        border: none;
        color: #999;
        font-size: 18px;
        cursor: pointer;
        padding: 0 0 0 10px;
        line-height: 1;
    }
    .close-btn:hover {
        color: #333;
    }

    /* 5. CTA Arrow */
    .cta-arrow {
        color: #ff4757;
        font-weight: bold;
        margin-right: 10px;
    }

    /* Animation Keyframes */
    @keyframes fadeUp {
        from { opacity: 0; transform: translateY(10px); }
        to { opacity: 1; transform: translateY(0); }
    }

    /* Mobile Tweaks */
    @media (max-width: 480px) {
        #float-banner {
            width: 90%; /* Fit screen width */
            right: 5%;
            left: 5%;
            bottom: 15px;
        }
    }
</style>
</head>
<body>

<div id="float-banner" onclick="redirectToSales()">
    <div class="banner-content">
        <div class="slide-text active">
            🔥 Limited Time Offer <span class="slide-sub">50% Off</span>
        </div>
        <div class="slide-text">
            🚀 New Arrivals <span class="slide-sub">Check them out</span>
        </div>
        <div class="slide-text">
            💎 Best Sellers <span class="slide-sub">Restocked Now</span>
        </div>
    </div>
    
    <span class="cta-arrow">→</span>
    
    <button class="close-btn" onclick="closeBanner(event)">×</button>
</div>

<script>
    const banner = document.getElementById('float-banner');
    const slides = document.querySelectorAll('.slide-text');
    let currentSlide = 0;
    const slideInterval = 3000; // Change text every 3 seconds

    // 1. Show banner after 1 second (Intro animation)
    setTimeout(() => {
        banner.classList.add('visible');
    }, 1000);

    // 2. Auto-Slide Function
    function cycleSlides() {
        // Remove active class from current
        slides[currentSlide].classList.remove('active');
        
        // Move to next slide (loop back to 0 if at end)
        currentSlide = (currentSlide + 1) % slides.length;
        
        // Add active class to new slide
        slides[currentSlide].classList.add('active');
    }

    // Start the auto-slide loop
    setInterval(cycleSlides, slideInterval);

    // 3. Redirect Function
    function redirectToSales() {
        window.location.href = "https://debeatzgh1.github.io/sales/";
    }

    // 4. Close Function
    function closeBanner(event) {
        // Stop the click from bubbling up to the main banner (prevent redirect)
        event.stopPropagation();
        banner.style.display = 'none';
    }
</script>

</body>
</html>



<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Debeatzgh Hub | Modern Launcher</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap');
        
        body { font-family: 'Inter', sans-serif; scroll-behavior: smooth; }

        .pulse-animation {
            animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: .7; transform: scale(1.05); }
        }

        .glass {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .iframe-container {
            height: 100vh;
            width: 100%;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
        }

        .custom-scrollbar::-webkit-scrollbar { width: 6px; }
        .custom-scrollbar::-webkit-scrollbar-track { background: #1a1a1a; }
        .custom-scrollbar::-webkit-scrollbar-thumb { background: #3b82f6; border-radius: 10px; }
    </style>

    <script async src="https://www.googletagmanager.com/gtag/js?id=UA-XXXXX-Y"></script>
    <script>
      window.dataLayer = window.dataLayer || [];
      function gtag(){dataLayer.push(arguments);}
      gtag('js', new Date());
      gtag('config', 'UA-XXXXX-Y');
    </script>
</head>
<body class="bg-[#0f172a] text-slate-200 custom-scrollbar">

    <nav class="fixed top-0 w-full z-50 glass px-6 py-4 flex justify-between items-center">
        <div class="flex items-center gap-2">
            <div class="w-8 h-8 bg-blue-600 rounded-lg pulse-animation"></div>
            <h1 class="text-xl font-bold tracking-tight">DEBEATZGH <span class="text-blue-500 text-sm">HUB</span></h1>
        </div>
        <div class="flex gap-4">
            <button onclick="scrollToSection('explorer')" class="hover:text-blue-400 transition">Explorer</button>
            <button onclick="scrollToSection('viewer')" class="bg-blue-600 hover:bg-blue-700 px-4 py-2 rounded-full text-sm font-semibold transition">Live View</button>
        </div>
    </nav>

    <header class="pt-24 pb-12 px-6">
        <div class="max-w-6xl mx-auto relative overflow-hidden rounded-3xl h-64 md:h-96 group">
            <div id="carousel" class="flex transition-transform duration-700 ease-in-out h-full">
                </div>
            <div class="absolute bottom-4 left-1/2 -translate-x-1/2 flex gap-2" id="carousel-dots"></div>
        </div>
    </header>

    <section class="px-6 py-8">
        <div class="max-w-6xl mx-auto glass rounded-2xl p-6 border-l-4 border-blue-500">
            <div class="flex items-center gap-2 mb-3">
                <i data-lucide="sparkles" class="text-blue-400 w-5 h-5"></i>
                <h3 class="text-lg font-semibold">AI Ecosystem Summary</h3>
            </div>
            <p id="ai-summary" class="text-slate-400 leading-relaxed italic">
                Scanning project metadata... initializing intelligent overview...
            </p>
        </div>
    </section>

    <section id="explorer" class="px-6 py-12">
        <div class="max-w-6xl mx-auto">
            <div class="flex justify-between items-end mb-8">
                <div>
                    <h2 class="text-3xl font-bold">Project Library</h2>
                    <p class="text-slate-500">Select a tool to launch or preview</p>
                </div>
                <div class="flex gap-2">
                    <span class="px-3 py-1 bg-slate-800 rounded-md text-xs border border-slate-700">18 Total Links</span>
                </div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6" id="project-grid">
                </div>
        </div>
    </section>

    <section id="viewer" class="px-6 py-20 bg-slate-900/50">
        <div class="max-w-6xl mx-auto">
            <div class="flex flex-col md:flex-row justify-between items-center mb-6 gap-4">
                <div class="flex items-center gap-4">
                    <div class="p-3 bg-blue-600/20 rounded-xl">
                        <i data-lucide="monitor" class="text-blue-500"></i>
                    </div>
                    <div>
                        <h2 class="text-2xl font-bold" id="view-title">Smart Preview</h2>
                        <p class="text-slate-500 text-sm" id="view-url">Select a project above to load iframe</p>
                    </div>
                </div>
                <button id="external-link" class="flex items-center gap-2 bg-slate-800 hover:bg-slate-700 px-6 py-3 rounded-xl transition">
                    <span>Open in New Tab</span>
                    <i data-lucide="external-link" class="w-4 h-4"></i>
                </button>
            </div>
            
            <div class="iframe-container bg-slate-800 border border-slate-700 flex items-center justify-center relative">
                <div id="iframe-loader" class="hidden absolute inset-0 flex items-center justify-center bg-slate-900 z-10">
                    <div class="w-12 h-12 border-4 border-blue-500 border-t-transparent rounded-full animate-spin"></div>
                </div>
                <iframe id="main-iframe" src="" frameborder="0" class="w-full h-full"></iframe>
                <div id="iframe-placeholder" class="text-center">
                    <i data-lucide="mouse-pointer-click" class="w-12 h-12 mx-auto mb-4 text-slate-600"></i>
                    <p class="text-slate-500">Click "Launch Preview" on any card to load it here</p>
                </div>
            </div>
        </div>
    </section>

    <footer class="py-12 text-center text-slate-600 text-sm border-t border-slate-800">
        <p>&copy; 2024 Debeatzgh Development Hub. Built for performance.</p>
    </footer>

    <script>
        const projects = [
            { title: "AI Chat Interface", url: "https://debeatzgh1.github.io/ai-chat/", category: "AI Tools", content: "Advanced conversational interface using modern AI models.", thumb: "https://images.unsplash.com/photo-1677442136019-21780ecad995?auto=format&fit=crop&w=800&q=80" },
            { title: "Personal Portfolio", url: "https://debeatzgh1.github.io/Personal-Portfolio-site-/", category: "Web Design", content: "Professional showcase of creative works and technical skills.", thumb: "https://images.unsplash.com/photo-1507238691740-187a5b1d37b8?auto=format&fit=crop&w=800&q=80" },
            { title: "Collaborators Hub", url: "https://debeatzgh1.github.io/Debeatzgh-Collaborators-Hub/", category: "Community", content: "Platform for developers to connect and build together.", thumb: "https://images.unsplash.com/photo-1522071820081-009f0129c71c?auto=format&fit=crop&w=800&q=80" },
            { title: "Decode AI Starter Kit", url: "https://debeatzgh1.github.io/Decode-AI-starter-kit-/", category: "Education", content: "Comprehensive resources for beginning your AI journey.", thumb: "https://images.unsplash.com/photo-1620712943543-bcc4628c975c?auto=format&fit=crop&w=800&q=80" },
            { title: "Side Hustle Guide", url: "https://debeatzgh1.github.io/The-Ultimate-Guide-to-Side-Hustle/", category: "Business", content: "Unlock new revenue streams with these proven strategies.", thumb: "https://images.unsplash.com/photo-1553729459-efe14ef6055d?auto=format&fit=crop&w=800&q=80" },
            { title: "Firebase UI Components", url: "https://debeatzgh1.github.io/firebase-front-end-components/", category: "Development", content: "Plug-and-play UI elements for Firebase backends.", thumb: "https://images.unsplash.com/photo-1614741118887-7a4ee193a5fa?auto=format&fit=crop&w=800&q=80" },
            { title: "Sales Dashboard", url: "https://debeatzgh1.github.io/sales/", category: "Analytics", content: "High-conversion data visualization for sales teams.", thumb: "https://images.unsplash.com/photo-1460925895917-afdab827c52f?auto=format&fit=crop&w=800&q=80" },
            { title: "Modern Tailwind Home", url: "https://debeatzgh1.github.io/Modern-homepage-styling-with-TailwindCSS-/", category: "Web Design", content: "A landing page concept pushing Tailwind limits.", thumb: "https://images.unsplash.com/photo-1555066931-4365d14bab8c?auto=format&fit=crop&w=800&q=80" },
            { title: "Popup Generator", url: "https://debeatzgh1.github.io/popup-html-page-generator-blogger/", category: "Utility", content: "Custom popup creator for Blogger and static sites.", thumb: "https://images.unsplash.com/photo-1586717791821-3f44a563eb4c?auto=format&fit=crop&w=800&q=80" },
            { title: "Smart Floating Dock", url: "https://debeatzgh1.github.io/-Floating-Dock-Smart-Iframe-Modal/#", category: "Utility", content: "Innovative navigation system for multi-app experiences.", thumb: "https://images.unsplash.com/photo-1551650975-87deedd944c3?auto=format&fit=crop&w=800&q=80" }
        ];

        // Initialize Lucide Icons
        lucide.createIcons();

        // Render Carousel
        const carousel = document.getElementById('carousel');
        const dots = document.getElementById('carousel-dots');
        const featured = projects.slice(0, 5);

        featured.forEach((p, i) => {
            const slide = document.createElement('div');
            slide.className = "min-w-full h-full relative";
            slide.innerHTML = `
                <img src="${p.thumb}" class="w-full h-full object-cover opacity-60" />
                <div class="absolute inset-0 flex flex-col justify-end p-10 bg-gradient-to-t from-[#0f172a] to-transparent">
                    <span class="text-blue-400 text-sm font-bold mb-2 tracking-widest uppercase">${p.category}</span>
                    <h2 class="text-4xl font-bold mb-2">${p.title}</h2>
                    <p class="max-w-xl text-slate-300">${p.content}</p>
                </div>
            `;
            carousel.appendChild(slide);
            
            const dot = document.createElement('button');
            dot.className = `w-2 h-2 rounded-full transition-all ${i === 0 ? 'bg-blue-500 w-6' : 'bg-slate-600'}`;
            dots.appendChild(dot);
        });

        // Carousel Logic
        let currentSlide = 0;
        setInterval(() => {
            currentSlide = (currentSlide + 1) % featured.length;
            carousel.style.transform = `translateX(-${currentSlide * 100}%)`;
            Array.from(dots.children).forEach((dot, i) => {
                dot.className = `w-2 h-2 rounded-full transition-all ${i === currentSlide ? 'bg-blue-500 w-6' : 'bg-slate-600'}`;
            });
        }, 5000);

        // Render Grid Cards
        const grid = document.getElementById('project-grid');
        projects.forEach(p => {
            const card = document.createElement('div');
            card.className = "glass rounded-2xl overflow-hidden hover:scale-[1.02] transition-all duration-300 group cursor-pointer border border-slate-800 hover:border-blue-500/50";
            card.innerHTML = `
                <div class="h-40 overflow-hidden relative">
                    <img src="${p.thumb}" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500" />
                    <div class="absolute top-3 right-3 bg-blue-600 text-[10px] font-bold px-2 py-1 rounded uppercase tracking-wider">${p.category}</div>
                </div>
                <div class="p-5">
                    <h3 class="text-lg font-bold mb-2 group-hover:text-blue-400 transition">${p.title}</h3>
                    <p class="text-slate-400 text-sm mb-5 line-clamp-2">${p.content}</p>
                    <div class="flex gap-2">
                        <button onclick="loadPreview('${p.url}', '${p.title}')" class="flex-1 bg-blue-600/10 hover:bg-blue-600 text-blue-400 hover:text-white py-2 rounded-lg text-xs font-bold transition-all border border-blue-500/20">
                            Launch Preview
                        </button>
                        <a href="${p.url}" target="_blank" class="p-2 bg-slate-800 hover:bg-slate-700 rounded-lg transition">
                            <i data-lucide="external-link" class="w-4 h-4"></i>
                        </a>
                    </div>
                </div>
            `;
            grid.appendChild(card);
        });

        // Preview Logic
        function loadPreview(url, title) {
            document.getElementById('iframe-placeholder').classList.add('hidden');
            document.getElementById('iframe-loader').classList.remove('hidden');
            const iframe = document.getElementById('main-iframe');
            
            iframe.src = url;
            document.getElementById('view-title').innerText = title;
            document.getElementById('view-url').innerText = url;
            document.getElementById('external-link').onclick = () => window.open(url, '_blank');
            
            scrollToSection('viewer');

            iframe.onload = () => {
                document.getElementById('iframe-loader').classList.add('hidden');
                // Tracking Event
                gtag('event', 'preview_load', { 'project_title': title });
            };
        }

        // AI Summary Logic (Simulated)
        const summaryText = "The Debeatzgh ecosystem currently features a diverse array of 18 digital assets. High-performance modules include a centralized AI Chat platform and the newly launched 'Floating Dock' system. The codebase shows a strong preference for TailwindCSS and Firebase integration, suggesting a scalable, cloud-first architecture optimized for side-hustle automation.";
        
        let charIndex = 0;
        function typeSummary() {
            if (charIndex < summaryText.length) {
                document.getElementById('ai-summary').innerHTML += summaryText.charAt(charIndex);
                charIndex++;
                setTimeout(typeSummary, 20);
            }
        }
        window.onload = () => {
            document.getElementById('ai-summary').innerHTML = "";
            typeSummary();
            lucide.createIcons();
        };

        function scrollToSection(id) {
            document.getElementById(id).scrollIntoView({ behavior: 'smooth' });
        }
    </script>
</body>
</html>


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


