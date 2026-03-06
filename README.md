<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DeBeatzGH | Admin Command Center</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;600;800&display=swap');

        :root {
            --admin-accent: #f87171; /* Red for Admin Priority */
            --node-cyan: #00f2ff;
            --bg-deep: #050505;
            --glass: rgba(255, 255, 255, 0.02);
        }

        body { background-color: var(--bg-deep); font-family: 'Plus Jakarta Sans', sans-serif; color: #f1f5f9; overflow: hidden; }

        .admin-sidebar { width: 80px; height: 100vh; background: #000; border-right: 1px solid rgba(255,255,255,0.05); display: flex; flex-direction: column; align-items: center; py: 30px; }
        
        .admin-nav-icon { width: 45px; height: 45px; border-radius: 12px; display: flex; align-items: center; justify-content: center; margin-bottom: 25px; transition: 0.3s; color: #475569; }
        .admin-nav-icon:hover, .admin-nav-icon.active { background: var(--admin-accent); color: white; box-shadow: 0 0 15px rgba(248, 113, 113, 0.3); }

        .content-scroll { height: calc(100vh - 100px); overflow-y: auto; padding-right: 10px; }
        
        .submission-row {
            background: var(--glass); border: 1px solid rgba(255,255,255,0.05); border-radius: 16px;
            padding: 15px 20px; margin-bottom: 12px; display: flex; align-items: center; justify-content: space-between;
            transition: 0.3s;
        }
        .submission-row:hover { border-color: var(--node-cyan); background: rgba(0, 242, 255, 0.02); }

        .badge-pending { background: rgba(234, 179, 8, 0.1); color: #eab308; border: 1px solid rgba(234, 179, 8, 0.3); padding: 2px 10px; border-radius: 50px; font-size: 10px; font-weight: 800; }
        
        /* CUSTOM SCROLLBAR */
        ::-webkit-scrollbar { width: 4px; }
        ::-webkit-scrollbar-thumb { background: #334155; border-radius: 10px; }
    </style>
</head>
<body class="flex">

    <aside class="admin-sidebar">
        <div class="mb-12"><i class="fas fa-shield-alt text-2xl text-red-500"></i></div>
        <div class="admin-nav-icon active"><i class="fas fa-database"></i></div>
        <div class="admin-nav-icon"><i class="fas fa-users"></i></div>
        <div class="admin-nav-icon"><i class="fas fa-chart-line"></i></div>
        <div class="admin-nav-icon mt-auto mb-8"><i class="fas fa-cog"></i></div>
    </aside>

    <main class="flex-grow p-10">
        
        <header class="flex justify-between items-center mb-12">
            <div>
                <h1 class="text-3xl font-black tracking-tighter">NODE <span class="text-red-500">ADMIN</span></h1>
                <p class="text-xs text-gray-500 uppercase tracking-widest font-bold">Protocol v4.0 | Root Access</p>
            </div>
            <div class="flex gap-4">
                <div class="text-right mr-4">
                    <p class="text-xs font-bold text-gray-400">System Uptime</p>
                    <p class="text-xs text-green-500 font-mono">99.98% Stable</p>
                </div>
                <button onclick="window.open('https://wa.me/233549757544')" class="bg-white/5 border border-white/10 px-6 py-3 rounded-xl font-bold text-xs hover:bg-white/10 transition">
                    <i class="fab fa-whatsapp mr-2 text-green-500"></i> Broadcast to 0549757544
                </button>
            </div>
        </header>

        <div class="grid grid-cols-1 lg:grid-cols-3 gap-10">
            
            <div class="lg:col-span-2">
                <div class="flex items-center justify-between mb-6">
                    <h3 class="font-bold text-lg uppercase tracking-widest text-gray-400 text-xs">Queue: Pending Approvals</h3>
                    <span class="text-xs font-bold text-red-400">03 New Submissions</span>
                </div>

                <div class="content-scroll">
                    <div class="submission-row">
                        <div class="flex items-center gap-4">
                            <div class="w-10 h-10 rounded bg-cyan-500/10 flex items-center justify-center text-cyan-400"><i class="fas fa-file-alt"></i></div>
                            <div>
                                <p class="text-sm font-bold">AI Strategy Ebook.pdf</p>
                                <p class="text-[10px] text-gray-500">By: User_99 | GH-Accra</p>
                            </div>
                        </div>
                        <div class="flex items-center gap-6">
                            <span class="badge-pending">PENDING</span>
                            <div class="flex gap-2">
                                <button class="w-8 h-8 rounded bg-green-500/20 text-green-500 hover:bg-green-500 hover:text-white transition"><i class="fas fa-check text-[10px]"></i></button>
                                <button class="w-8 h-8 rounded bg-red-500/20 text-red-500 hover:bg-red-500 hover:text-white transition"><i class="fas fa-times text-[10px]"></i></button>
                            </div>
                        </div>
                    </div>

                    <div class="submission-row">
                        <div class="flex items-center gap-4">
                            <div class="w-10 h-10 rounded bg-purple-500/10 flex items-center justify-center text-purple-400"><i class="fas fa-link"></i></div>
                            <div>
                                <p class="text-sm font-bold">Firebase Login Component</p>
                                <p class="text-[10px] text-gray-500">Repo: debeatzgh1.github.io/blogs/</p>
                            </div>
                        </div>
                        <div class="flex items-center gap-6">
                            <span class="badge-pending">REVIEWING</span>
                            <div class="flex gap-2">
                                <button class="w-8 h-8 rounded bg-green-500/20 text-green-500 hover:bg-green-500 hover:text-white transition"><i class="fas fa-check text-[10px]"></i></button>
                                <button class="w-8 h-8 rounded bg-red-500/20 text-red-500 hover:bg-red-500 hover:text-white transition"><i class="fas fa-times text-[10px]"></i></button>
                            </div>
                        </div>
                    </div>

                    <div class="submission-row">
                        <div class="flex items-center gap-4">
                            <div class="w-10 h-10 rounded bg-orange-500/10 flex items-center justify-center text-orange-400"><i class="fas fa-image"></i></div>
                            <div>
                                <p class="text-sm font-bold">Logo Branding Pack.zip</p>
                                <p class="text-[10px] text-gray-500">Digital Design Hobby Entry</p>
                            </div>
                        </div>
                        <div class="flex items-center gap-6">
                            <span class="badge-pending">PENDING</span>
                            <div class="flex gap-2">
                                <button class="w-8 h-8 rounded bg-green-500/20 text-green-500 hover:bg-green-500 hover:text-white transition"><i class="fas fa-check text-[10px]"></i></button>
                                <button class="w-8 h-8 rounded bg-red-500/20 text-red-500 hover:bg-red-500 hover:text-white transition"><i class="fas fa-times text-[10px]"></i></button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="space-y-8">
                <div class="bg-white/5 border border-white/5 rounded-2xl p-6">
                    <h4 class="text-xs font-bold text-gray-500 uppercase tracking-widest mb-6">Network Broadcast</h4>
                    <textarea class="w-full h-24 bg-black/40 border border-white/10 rounded-xl p-4 text-xs outline-none focus:border-red-500 transition mb-4" placeholder="Send a global task to all collaborators..."></textarea>
                    <button class="w-full bg-red-500 text-white font-bold py-3 rounded-xl text-xs uppercase tracking-widest hover:bg-red-600 transition">Deploy Task</button>
                </div>

                <div class="bg-white/5 border border-white/5 rounded-2xl p-6">
                    <h4 class="text-xs font-bold text-gray-500 uppercase tracking-widest mb-6">Google Node Status</h4>
                    <div class="space-y-4">
                        <div class="flex justify-between items-center text-xs">
                            <span class="text-gray-400">Search Engine Index</span>
                            <span class="text-green-500 font-bold">LIVE</span>
                        </div>
                        <div class="flex justify-between items-center text-xs">
                            <span class="text-gray-400">Map Discovery</span>
                            <span class="text-green-500 font-bold">ACTIVE</span>
                        </div>
                        <div class="flex justify-between items-center text-xs">
                            <span class="text-gray-400">Affiliate Monetization</span>
                            <span class="text-yellow-500 font-bold">SYNCING</span>
                        </div>
                    </div>
                </div>

                <div class="space-y-3">
                    <a href="https://forms.gle/Pm5PK45qN5KGELbt7" target="_blank" class="block w-full text-center p-3 bg-white/5 rounded-xl border border-white/10 text-[10px] font-bold text-gray-500 hover:text-red-400 transition">MANAGE SIGN-INS</a>
                    <a href="https://docs.google.com/forms/d/e/1FAIpQLSdipVP7tU1hjTjECfWUdnhzWN-PROdQp19ng25EUDJk5-8JzA/viewform" target="_blank" class="block w-full text-center p-3 bg-white/5 rounded-xl border border-white/10 text-[10px] font-bold text-gray-500 hover:text-red-400 transition">VIEW ENQUIRIES</a>
                </div>
            </div>

        </div>
    </main>

</body>
</html>
