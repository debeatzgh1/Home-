
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DeBeatzGH | Member Dashboard</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;600;800&display=swap');

        :root {
            --accent: #00f2ff;
            --bg-dark: #0a0a0b;
            --sidebar-glass: rgba(15, 15, 15, 0.6);
            --card-glass: rgba(255, 255, 255, 0.03);
        }

        body {
            background-color: var(--bg-dark);
            font-family: 'Plus Jakarta Sans', sans-serif;
            color: #e2e8f0;
            overflow: hidden; /* Prevent body scroll, use container scroll */
        }

        /* 1. GLASS SIDEBAR */
        .sidebar {
            width: 260px;
            height: 100vh;
            background: var(--sidebar-glass);
            backdrop-filter: blur(25px);
            border-right: 1px solid rgba(255, 255, 255, 0.05);
            transition: 0.3s ease;
        }

        .nav-item {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 14px 24px;
            color: #94a3b8;
            font-size: 13px;
            font-weight: 600;
            border-radius: 12px;
            margin: 4px 16px;
            transition: 0.3s;
        }

        .nav-item:hover, .nav-item.active {
            background: rgba(0, 242, 255, 0.08);
            color: var(--accent);
        }

        /* 2. DASHBOARD CARDS */
        .stat-card {
            background: var(--card-glass);
            border: 1px solid rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            padding: 24px;
            transition: 0.4s;
        }

        .stat-card:hover {
            border-color: var(--accent);
            background: rgba(255, 255, 255, 0.05);
        }

        /* 3. TASK FEED */
        .task-item {
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid rgba(255, 255, 255, 0.03);
            border-radius: 16px;
            padding: 16px;
            margin-bottom: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        /* 4. CUSTOM SCROLLBAR */
        ::-webkit-scrollbar { width: 5px; }
        ::-webkit-scrollbar-track { background: transparent; }
        ::-webkit-scrollbar-thumb { background: #1e293b; border-radius: 10px; }

        .status-dot { width: 8px; height: 8px; border-radius: 50%; display: inline-block; }
        .bg-online { background: #10b981; box-shadow: 0 0 8px #10b981; }
    </style>
</head>
<body class="flex">

    <aside class="sidebar flex flex-col py-8 shrink-0">
        <div class="px-8 mb-10 flex items-center gap-2">
            <div class="w-8 h-8 bg-cyan-500 rounded-lg flex items-center justify-center">
                <i class="fas fa-cube text-black text-sm"></i>
            </div>
            <span class="font-black text-lg tracking-tighter">DEBEATZ<span class="text-cyan-400">HUB</span></span>
        </div>

        <nav class="flex-grow">
            <p class="px-8 text-[10px] font-bold text-gray-600 uppercase tracking-widest mb-4">Main Panel</p>
            <a href="#" class="nav-item active"><i class="fas fa-th-large"></i> Dashboard</a>
            <a href="https://debeatzgh1.github.io/blogs/" target="_blank" class="nav-item"><i class="fas fa-fire"></i> Firebase Components</a>
            <a href="https://debeatzgh1.github.io/appdategh/" target="_blank" class="nav-item"><i class="fas fa-rocket"></i> App Repository</a>
            
            <p class="px-8 text-[10px] font-bold text-gray-600 uppercase tracking-widest mt-8 mb-4">Creator Tools</p>
            <a href="#" class="nav-item"><i class="fas fa-paint-brush"></i> AI Design Prompts</a>
            <a href="#" class="nav-item"><i class="fas fa-file-invoice"></i> Google Docs Kits</a>
            <a href="https://forms.gle/Pm5PK45qN5KGELbt7" class="nav-item"><i class="fas fa-user-edit"></i> Profile Settings</a>
        </nav>

        <div class="px-6 mt-auto">
            <div class="bg-white/5 p-4 rounded-2xl flex items-center gap-3 border border-white/5">
                <div class="w-10 h-10 rounded-full bg-gradient-to-tr from-cyan-500 to-blue-500 flex items-center justify-center font-bold text-black">
                    DB
                </div>
                <div>
                    <p class="text-xs font-bold">Member Node</p>
                    <p class="text-[10px] text-gray-500">Verified Contributor</p>
                </div>
            </div>
        </div>
    </aside>

    <main class="flex-grow h-screen overflow-y-auto px-10 py-10">
        
        <header class="flex justify-between items-center mb-10">
            <div>
                <h1 class="text-2xl font-bold">Welcome back, <span class="text-cyan-400">Creator</span></h1>
                <p class="text-sm text-gray-500">System Node: <span class="text-green-500">Active</span> | <span class="status-dot bg-online"></span> 0549757544</p>
            </div>
            <div class="flex gap-4">
                <button class="bg-white/5 w-10 h-10 rounded-full flex items-center justify-center border border-white/10 hover:border-cyan-400 transition">
                    <i class="fas fa-bell text-sm"></i>
                </button>
                <a href="https://wa.me/233549757544" class="bg-cyan-500 text-black px-6 py-2 rounded-full font-bold text-sm flex items-center gap-2">
                    <i class="fas fa-plus"></i> New Project
                </a>
            </div>
        </header>

        <div class="grid grid-cols-1 md:grid-cols-4 gap-6 mb-10">
            <div class="stat-card">
                <p class="text-xs text-gray-500 font-bold uppercase mb-2">Total Earnings</p>
                <h2 class="text-3xl font-black text-white">$0.00</h2>
                <p class="text-[10px] text-cyan-400 mt-2"><i class="fas fa-arrow-up"></i> 0% From Last Month</p>
            </div>
            <div class="stat-card">
                <p class="text-xs text-gray-500 font-bold uppercase mb-2">Content Reach</p>
                <h2 class="text-3xl font-black text-white">1.2K</h2>
                <p class="text-[10px] text-gray-500 mt-2">Active Across Hubs</p>
            </div>
            <div class="stat-card">
                <p class="text-xs text-gray-500 font-bold uppercase mb-2">Active Tasks</p>
                <h2 class="text-3xl font-black text-white">04</h2>
                <p class="text-[10px] text-yellow-500 mt-2">Requires Action</p>
            </div>
            <div class="stat-card">
                <p class="text-xs text-gray-500 font-bold uppercase mb-2">SEO Status</p>
                <h2 class="text-3xl font-black text-white">Indexed</h2>
                <p class="text-[10px] text-green-500 mt-2">Chrome Bot Active</p>
            </div>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
            
            <div class="lg:col-span-2">
                <div class="flex justify-between items-center mb-6">
                    <h3 class="font-bold text-lg">Collaboration Opportunities</h3>
                    <a href="https://forms.gle/SArJCF7yj1J46hdw9" class="text-xs text-cyan-400 font-bold">View All</a>
                </div>
                
                <div class="task-item">
                    <div class="flex items-center gap-4">
                        <div class="w-10 h-10 bg-blue-500/10 rounded-xl flex items-center justify-center"><i class="fab fa-facebook-f text-blue-400"></i></div>
                        <div>
                            <p class="text-sm font-bold">Social Media Management</p>
                            <p class="text-[10px] text-gray-500">Post as page on Facebook/Instagram</p>
                        </div>
                    </div>
                    <span class="text-[10px] font-black bg-cyan-500/20 text-cyan-400 px-3 py-1 rounded-full">AVAILABLE</span>
                </div>

                <div class="task-item">
                    <div class="flex items-center gap-4">
                        <div class="w-10 h-10 bg-orange-500/10 rounded-xl flex items-center justify-center"><i class="fas fa-fire text-orange-400"></i></div>
                        <div>
                            <p class="text-sm font-bold">Firebase UI Contribution</p>
                            <p class="text-[10px] text-gray-500">Develop login components for GitHub Io</p>
                        </div>
                    </div>
                    <span class="text-[10px] font-black bg-white/5 text-gray-500 px-3 py-1 rounded-full">IN REVIEW</span>
                </div>

                <div class="task-item">
                    <div class="flex items-center gap-4">
                        <div class="w-10 h-10 bg-purple-500/10 rounded-xl flex items-center justify-center"><i class="fas fa-robot text-purple-400"></i></div>
                        <div>
                            <p class="text-sm font-bold">AI Chatbot Training</p>
                            <p class="text-[10px] text-gray-500">Optimize response nodes for E-Hub</p>
                        </div>
                    </div>
                    <span class="text-[10px] font-black bg-cyan-500/20 text-cyan-400 px-3 py-1 rounded-full">AVAILABLE</span>
                </div>
            </div>

            <div class="space-y-8">
                <div class="stat-card bg-gradient-to-br from-cyan-900/20 to-transparent border-cyan-500/20">
                    <h3 class="font-bold mb-4">Author Benefits</h3>
                    <ul class="text-xs space-y-4">
                        <li class="flex items-start gap-3"><i class="fas fa-check-circle text-cyan-400 mt-1"></i> <span>Monetization enabled for viral content.</span></li>
                        <li class="flex items-start gap-3"><i class="fas fa-check-circle text-cyan-400 mt-1"></i> <span>Google Maps discovery for shared locations.</span></li>
                        <li class="flex items-start gap-3"><i class="fas fa-check-circle text-cyan-400 mt-1"></i> <span>Direct hired orders from clients.</span></li>
                    </ul>
                </div>

                <div class="stat-card">
                    <h3 class="font-bold mb-4">Quick Links</h3>
                    <div class="grid grid-cols-2 gap-3">
                        <a href="https://debeatzgh1.github.io/blogs/" class="bg-white/5 p-3 rounded-xl text-center hover:bg-white/10 transition">
                            <i class="fas fa-blog block mb-2 text-cyan-400"></i>
                            <span class="text-[10px] font-bold">Blog</span>
                        </a>
                        <a href="https://debeatzgh1.github.io/E-Hub-/" class="bg-white/5 p-3 rounded-xl text-center hover:bg-white/10 transition">
                            <i class="fas fa-tv block mb-2 text-purple-400"></i>
                            <span class="text-[10px] font-bold">E-Hub</span>
                        </a>
                    </div>
                </div>
            </div>

        </div>

    </main>

    <a href="https://wa.me/233549757544?text=Hi%20DeBeatz,%20I'm%20in%20the%20member%20dashboard%20and%20need%20help." 
       class="fixed bottom-10 right-10 w-14 h-14 bg-cyan-500 text-black rounded-full flex items-center justify-center shadow-2xl hover:scale-110 transition z-50">
        <i class="fas fa-headset text-xl"></i>
    </a>

</body>
</html>
