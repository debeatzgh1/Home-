
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
            <a href="https://forms.gle/Pm5PK45qN5KGELbt7" class="bg-cyan-500 text-black px-6 py-2 rounded-xl font-extrabold text-[10px] uppercase tracking-tighter hover:scale-105 transition">Sign Up</a>
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
            <a href="https://wa.me/233549757544" class="bg-white text-black px-10 py-5 rounded-2xl font-black text-sm uppercase tracking-wider hover:bg-cyan-400 transition">Hire Me</a>
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
            <a href="https://docs.google.com/forms/d/e/1FAIpQLSdipVP7tU1hjTjECfWUdnhzWN-PROdQp19ng25EUDJk5-8JzA/viewform" class="text-cyan-400 font-bold uppercase text-xs border-b border-cyan-400/30 pb-1">Enquire for Custom Docs</a>
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
                    <a href="https://forms.gle/SArJCF7yj1J46hdw9" class="p-4 bg-white/5 border border-white/10 rounded-2xl hover:border-cyan-400 transition flex justify-between">
                        <span class="font-bold text-sm">Suggestions Form</span> <i class="fas fa-arrow-right"></i>
                    </a>
                    <a href="https://forms.gle/Pm5PK45qN5KGELbt7" class="p-4 bg-white/5 border border-white/10 rounded-2xl hover:border-cyan-400 transition flex justify-between">
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
        <a href="https://wa.me/233549757544" class="w-14 h-14 bg-[#25D366] text-white rounded-full shadow-2xl flex items-center justify-center hover:scale-110 transition">
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
