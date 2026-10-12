
<html lang="pt-BR" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SAMS | Exoesqueletos e Próteses Biônicas - Reflexo Muscular Artificial</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        sci: {
                            950: '#020617',
                            900: '#090d16',
                            800: '#111827',
                            700: '#1f2937',
                            cyan: '#06b6d4',
                            emerald: '#10b981',
                            amber: '#f59e0b',
                            rose: '#f43f5e',
                            purple: '#8b5cf6'
                        }
                    }
                }
            }
        }
    </script>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500;700&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; }
        .font-mono { font-family: 'JetBrains Mono', monospace; }
        .glass-panel {
            background: rgba(15, 23, 42, 0.75);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(6, 182, 212, 0.2);
        }
        .glow-cyan {
            box-shadow: 0 0 25px rgba(6, 182, 212, 0.25);
        }
        .glow-amber {
            box-shadow: 0 0 25px rgba(245, 158, 11, 0.3);
        }
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #020617;
        }
        ::-webkit-scrollbar-thumb {
            background: #1e293b;
            border-radius: 3px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #06b6d4;
        }
    </style>
</head>
<body class="bg-sci-950 text-slate-100 min-h-screen flex flex-col overflow-x-hidden">

    <!-- Header / Navbar -->
    <header class="glass-panel border-b border-cyan-500/20 px-6 py-4 flex flex-wrap items-center justify-between gap-4 sticky top-0 z-50">
        <div class="flex items-center space-x-3">
            <div class="relative flex items-center justify-center w-10 h-10 rounded-xl bg-cyan-950 border border-cyan-500/50 glow-cyan">
                <svg class="w-6 h-6 text-cyan-400 animate-pulse" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"/>
                </svg>
            </div>
            <div>
                <h1 class="text-lg font-bold tracking-wider text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 to-emerald-400">SAMS MEDICAL EXOSKELETON</h1>
                <p class="text-xs text-slate-400 font-mono">Reflexo Muscular Artificial & Fluido Magnetorreológico</p>
            </div>
        </div>

        <!-- System Status Pills -->
        <div class="flex items-center gap-3 text-xs font-mono flex-wrap">
            <div class="flex items-center gap-2 px-3 py-1.5 rounded-full bg-slate-900 border border-slate-700">
                <span id="sams-status-dot" class="w-2.5 h-2.5 rounded-full bg-emerald-500 animate-ping"></span>
                <span>SAMS Reflexo: <strong id="sams-status-text" class="text-emerald-400">ATIVO (1.2 ms)</strong></span>
            </div>
            <div class="flex items-center gap-2 px-3 py-1.5 rounded-full bg-slate-900 border border-slate-700">
                <span class="w-2.5 h-2.5 rounded-full bg-cyan-500"></span>
                <span>Fluido MR: <strong id="fluid-state-badge" class="text-cyan-400">FLUIDO / ADAPTATIVO</strong></span>
            </div>
            <div class="flex items-center gap-2 px-3 py-1.5 rounded-full bg-slate-900 border border-slate-700">
                <span class="w-2.5 h-2.5 rounded-full bg-purple-500"></span>
                <span>Piezoelétricos: <strong class="text-purple-400">100% ESCUTA</strong></span>
            </div>
        </div>
    </header>

    <!-- Main Workspace -->
    <main class="flex-1 grid grid-cols-1 lg:grid-cols-12 gap-6 p-6 max-w-[1700px] mx-auto w-full">
        
        <!-- Left Sidebar: Controls & Scenarios -->
        <section class="lg:col-span-3 flex flex-col gap-6">
            
            <!-- Scenario Selection -->
            <div class="glass-panel rounded-2xl p-5 shadow-xl">
                <h2 class="text-sm font-semibold tracking-wide text-cyan-400 uppercase mb-4 flex items-center gap-2">
                    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"/></svg>
                    Cenários de Teste Biônico
                </h2>
                <div class="space-y-3">
                    <button onclick="setScenario('walk')" id="scen-walk" class="w-full text-left p-3 rounded-xl border border-cyan-500/40 bg-cyan-500/10 transition-all hover:bg-cyan-500/20 flex items-center justify-between group">
                        <div>
                            <div class="font-semibold text-sm text-cyan-300">Caminhada Regular</div>
                            <div class="text-xs text-slate-400">Passos fluidos em piso plano</div>
                        </div>
                        <span class="w-2 h-2 rounded-full bg-cyan-400"></span>
                    </button>
                    <button onclick="setScenario('terrain')" id="scen-terrain" class="w-full text-left p-3 rounded-xl border border-slate-700 bg-slate-900/60 transition-all hover:border-amber-500/40 flex items-center justify-between group">
                        <div>
                            <div class="font-semibold text-sm text-slate-200 group-hover:text-amber-300">Terreno Irregular / Buraco</div>
                            <div class="text-xs text-slate-400">Desnível e risco de torção</div>
                        </div>
                        <span class="w-2 h-2 rounded-full bg-slate-600" id="dot-terrain"></span>
                    </button>
                    <button onclick="setScenario('stumble')" id="scen-stumble" class="w-full text-left p-3 rounded-xl border border-slate-700 bg-slate-900/60 transition-all hover:border-rose-500/40 flex items-center justify-between group">
                        <div>
                            <div class="font-semibold text-sm text-slate-200 group-hover:text-rose-300">Tropelho / Impacto Súbito</div>
                            <div class="text-xs text-slate-400">Choque externo de alta energia</div>
                        </div>
                        <span class="w-2 h-2 rounded-full bg-slate-600" id="dot-stumble"></span>
                    </button>
                </div>
            </div>

            <!-- SAMS Reflex Calibration Unit -->
            <div class="glass-panel rounded-2xl p-5 shadow-xl border-cyan-500/30">
                <div class="flex items-center justify-between mb-4">
                    <h2 class="text-sm font-semibold tracking-wide text-cyan-400 uppercase flex items-center gap-2">
                        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6V4m0 2a2 2 0 100 4m0-4a2 2 0 110 4m-6 8a2 2 0 100-4m0 4a2 2 0 110-4m0 4v2m0-6V4m6 6v10m6-2a2 2 0 100-4m0 4a2 2 0 110-4m0 4v2m0-6V4"/></svg>
                        Parâmetros SAMS
                    </h2>
                    <span id="sams-badge" class="px-2.5 py-0.5 rounded text-xs font-mono font-bold bg-cyan-500/20 text-cyan-300 border border-cyan-500/40">ATIVO</span>
                </div>
                
                <div class="space-y-4">
                    <div class="flex items-center justify-between bg-slate-900/80 p-3 rounded-xl border border-slate-800">
                        <div>
                            <div class="text-xs font-medium text-slate-300">Reflexo Muscular Artificial</div>
                            <div class="text-[10px] text-slate-400 font-mono">Endurecimento em ms</div>
                        </div>
                        <label class="relative inline-flex items-center cursor-pointer">
                            <input type="checkbox" id="samsToggle" checked onchange="toggleSAMS()" class="sr-only peer">
                            <div class="w-11 h-6 bg-slate-700 peer-focus:outline-none rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-cyan-500"></div>
                        </label>
                    </div>

                    <div>
                        <div class="flex justify-between text-xs mb-1 font-mono">
                            <span class="text-slate-400">Intensidade do Campo Eletromagnético</span>
                            <span id="mag-val" class="text-cyan-400">85%</span>
                        </div>
                        <input type="range" id="magIntensity" min="20" max="100" value="85" oninput="updateMag(this.value)" class="w-full h-2 bg-slate-800 rounded-lg appearance-none cursor-pointer accent-cyan-400">
                    </div>

                    <div>
                        <div class="flex justify-between text-xs mb-1 font-mono">
                            <span class="text-slate-400">Sensibilidade Piezoelétrica</span>
                            <span class="text-purple-400">9.4 kHz</span>
                        </div>
                        <input type="range" min="1" max="10" value="8" class="w-full h-2 bg-slate-800 rounded-lg appearance-none cursor-pointer accent-purple-400">
                    </div>
                </div>
            </div>

            <!-- Action Triggers -->
            <div class="glass-panel rounded-2xl p-5 shadow-xl flex flex-col gap-3">
                <h2 class="text-sm font-semibold tracking-wide text-cyan-400 uppercase mb-1">Comandos de Emergência</h2>
                <button onclick="triggerForcedStumble()" class="w-full py-3 px-4 rounded-xl bg-gradient-to-r from-amber-600 to-rose-600 hover:from-amber-500 hover:to-rose-500 text-white font-semibold text-sm shadow-lg shadow-amber-900/30 transition-all flex items-center justify-center gap-2">
                    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"/></svg>
                    Simular Tropelho Imediato
                </button>
                <button onclick="recalibrateSuit()" class="w-full py-2.5 px-4 rounded-xl bg-slate-900 hover:bg-slate-800 border border-slate-700 text-slate-300 font-medium text-xs transition-all flex items-center justify-center gap-2">
                    <svg class="w-4 h-4 text-cyan-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15"/></svg>
                    Calibrar Sensores Piezoelétricos
                </button>
            </div>

        </section>

        <!-- Center: Canvas 2D Simulation Viewport -->
        <section class="lg:col-span-6 flex flex-col gap-6">
            <div class="glass-panel rounded-2xl p-4 shadow-2xl relative flex flex-col overflow-hidden border-cyan-500/30">
                
                <!-- Viewport Header HUD -->
                <div class="flex items-center justify-between pb-3 mb-3 border-b border-slate-800 text-xs font-mono">
                    <div class="flex items-center gap-2">
                        <span class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse"></span>
                        <span class="text-slate-300">EXOSQUELETO BIÔNICO - MONITOR DE REFLEXO SAMS</span>
                    </div>
                    <div class="flex items-center gap-4 text-slate-400">
                        <span>Tempo de Reação: <strong id="hud-reaction" class="text-emerald-400">1.2 ms</strong></span>
                        <span>Força Articular: <strong id="hud-force" class="text-cyan-400">450 N</strong></span>
                    </div>
                </div>

                <!-- Canvas Container -->
                <div class="relative w-full aspect-[4/3] bg-slate-950 rounded-xl overflow-hidden border border-slate-800 shadow-inner">
                    <canvas id="simCanvas" class="w-full h-full block"></canvas>
                    
                    <!-- HUD Instructions / Legend -->
                    <div class="absolute bottom-4 left-4 pointer-events-none bg-slate-900/80 backdrop-blur-md px-3 py-2 rounded-lg border border-cyan-500/30 text-[11px] font-mono text-cyan-300 space-y-1">
                        <div>🛡️ Esqueleto com atuadores piezoelétricos ativos</div>
                        <div>⚡ Fluido magnetorreológico endurece milissegundos antes do impacto</div>
                    </div>

                    <!-- Impact Warning Banner -->
                    <div id="impact-banner" class="absolute top-4 inset-x-4 pointer-events-none hidden transition-all duration-300">
                        <div class="bg-amber-950/90 border border-amber-500 text-amber-200 px-4 py-2 rounded-xl text-xs font-mono font-bold flex items-center justify-center gap-2 animate-bounce">
                            <svg class="w-4 h-4 text-amber-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"/></svg>
                            IMPACTO DETECTADO! SAMS ENDURECEU ARTICULAÇÕES EM 0.8ms! QUEDA PREVENIDA!
                        </div>
                    </div>
                </div>

                <!-- Quick Metrics Bar -->
                <div class="grid grid-cols-3 gap-3 mt-4 text-center font-mono">
                    <div class="bg-slate-900/60 p-2.5 rounded-xl border border-slate-800">
                        <div class="text-[10px] text-slate-400">Estabilidade Postural</div>
                        <div id="metric-stability" class="text-sm font-bold text-cyan-400">99.8%</div>
                    </div>
                    <div class="bg-slate-900/60 p-2.5 rounded-xl border border-slate-800">
                        <div class="text-[10px] text-slate-400">Viscosidade do Fluido MR</div>
                        <div id="metric-viscosity" class="text-sm font-bold text-emerald-400">Adaptativa (12 Pa·s)</div>
                    </div>
                    <div class="bg-slate-900/60 p-2.5 rounded-xl border border-slate-800">
                        <div class="text-[10px] text-slate-400">Proteção Óssea</div>
                        <div id="metric-protection" class="text-sm font-bold text-purple-400">100% Blindado</div>
                    </div>
                </div>

            </div>
        </section>

        <!-- Right Sidebar: Telemetry & AI Reflex Console -->
        <section class="lg:col-span-3 flex flex-col gap-6">
            
            <!-- Patient / User Biometrics -->
            <div class="glass-panel rounded-2xl p-5 shadow-xl">
                <h2 class="text-sm font-semibold tracking-wide text-cyan-400 uppercase mb-4 flex items-center gap-2">
                    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"/></svg>
                    Biometria do Paciente
                </h2>
                <div class="space-y-3 font-mono text-xs">
                    <div class="flex justify-between items-center bg-slate-900/80 p-2.5 rounded-xl border border-slate-800">
                        <span class="text-slate-400">Condição Motora</span>
                        <span class="text-rose-400 font-bold">Paralisia Parcial (T12)</span>
                    </div>
                    <div class="flex justify-between items-center bg-slate-900/80 p-2.5 rounded-xl border border-slate-800">
                        <span class="text-slate-400">Carga do Exoesqueleto</span>
                        <span class="text-cyan-400 font-bold">78% (Bateria Nuclear)</span>
                    </div>
                    <div class="flex justify-between items-center bg-slate-900/80 p-2.5 rounded-xl border border-slate-800">
                        <span class="text-slate-400">Atuadores Piezoelétricos</span>
                        <span class="text-emerald-400 font-bold">24 Ativos</span>
                    </div>
                    <div class="flex justify-between items-center bg-slate-900/80 p-2.5 rounded-xl border border-slate-800">
                        <span class="text-slate-400">Pressão nos Joelhos</span>
                        <span class="text-amber-400 font-bold">1.2 MPa</span>
                    </div>
                </div>
            </div>

            <!-- SAMS AI Reflex Telemetry Log -->
            <div class="glass-panel rounded-2xl p-5 shadow-xl flex flex-col flex-1 min-h-[260px]">
                <h2 class="text-sm font-semibold tracking-wide text-cyan-400 uppercase mb-3 flex items-center gap-2">
                    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 9l3 3-3 3m5 0h3M5 20h14a2 2 0 002-2V6a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"/></svg>
                    Console SAMS Neural
                </h2>
                <div id="ai-console" class="flex-1 bg-slate-950/80 rounded-xl p-3 border border-slate-900 font-mono text-[11px] text-slate-300 space-y-1.5 overflow-y-auto max-h-[220px]">
                    <div class="text-slate-500">[00:00:01] SAMS Exoesqueletos v5.2 inicializado.</div>
                    <div class="text-cyan-400">[00:00:03] Sensores piezoelétricos calibrados em 9.4 kHz.</div>
                    <div class="text-emerald-400">[00:00:05] Fluido magnetorreológico em estado líquido adaptativo.</div>
                </div>
            </div>

        </section>

    </main>

    <!-- Footer -->
    <footer class="text-center py-4 text-xs text-slate-500 border-t border-slate-900 font-mono">
        SAMS (Smart Active Micro-Vibration Suppression) &bull; Exoesqueletos & Próteses Biônicas Médicas v2.1
    </footer>

    <!-- JavaScript Simulation Engine -->
    <script>
        // --- Simulation State ---
        let state = {
            scenario: 'walk', // 'walk', 'terrain', 'stumble'
            samsActive: true,
            magIntensity: 85,
            time: 0,
            walkCycle: 0,
            stumbleTimer: 0,
            isStumbling: false,
            impactFlash: 0
        };

        // DOM Elements
        const canvas = document.getElementById('simCanvas');
        const ctx = canvas.getContext('2d');
        const samsToggleEl = document.getElementById('samsToggle');
        const samsBadgeEl = document.getElementById('sams-badge');
        const samsStatusTextEl = document.getElementById('sams-status-text');
        const fluidStateBadgeEl = document.getElementById('fluid-state-badge');
        const impactBannerEl = document.getElementById('impact-banner');
        const hudReactionEl = document.getElementById('hud-reaction');
        const metricStabilityEl = document.getElementById('metric-stability');
        const metricViscosityEl = document.getElementById('metric-viscosity');
        const aiConsole = document.getElementById('ai-console');

        // Audio Helper
        let audioCtx = null;
        function initAudio() {
            if (!audioCtx) audioCtx = new (window.AudioContext || window.webkitAudioContext)();
        }

        function playBeep(freq = 440, type = 'sine', duration = 0.1) {
            try {
                initAudio();
                if (!audioCtx) return;
                const osc = audioCtx.createOscillator();
                const gain = audioCtx.createGain();
                osc.type = type;
                osc.frequency.value = freq;
                gain.gain.setValueAtTime(0.04, audioCtx.currentTime);
                gain.gain.exponentialRampToValueAtTime(0.0001, audioCtx.currentTime + duration);
                osc.connect(gain);
                gain.connect(audioCtx.destination);
                osc.start();
                osc.stop(audioCtx.currentTime + duration);
            } catch (e) {}
        }

        // Resize Canvas
        function resizeCanvas() {
            const rect = canvas.getBoundingClientRect();
            canvas.width = rect.width * window.devicePixelRatio;
            canvas.height = rect.height * window.devicePixelRatio;
            ctx.setTransform(window.devicePixelRatio, 0, 0, window.devicePixelRatio, 0, 0);
        }

        window.addEventListener('resize', resizeCanvas);

        // Control Handlers
        function setScenario(scen) {
            state.scenario = scen;
            ['walk', 'terrain', 'stumble'].forEach(s => {
                const btn = document.getElementById(`scen-${s}`);
                if (s === scen) {
                    btn.className = "w-full text-left p-3 rounded-xl border border-cyan-500/40 bg-cyan-500/10 transition-all flex items-center justify-between group";
                } else {
                    btn.className = "w-full text-left p-3 rounded-xl border border-slate-700 bg-slate-900/60 transition-all hover:border-slate-500 flex items-center justify-between group";
                }
            });

            if (scen === 'stumble') {
                triggerForcedStumble();
            } else if (scen === 'terrain') {
                logAI("Cenário de Terreno Irregular ativado. SAMS ajustando viscosidade preventiva.");
                playBeep(550, 'triangle', 0.15);
            } else {
                logAI("Cenário de Caminhada Regular ativado. Ciclo biônico normal.");
                playBeep(440, 'sine', 0.1);
            }
        }

        function toggleSAMS() {
            state.samsActive = samsToggleEl.checked;
            if (state.samsActive) {
                samsBadgeEl.textContent = "ATIVO";
                samsBadgeEl.className = "px-2.5 py-0.5 rounded text-xs font-mono font-bold bg-cyan-500/20 text-cyan-300 border border-cyan-500/40";
                samsStatusTextEl.textContent = "ATIVO (1.2 ms)";
                logAI("SAMS reativado: Reflexo muscular artificial em prontidão.");
                playBeep(880, 'sine', 0.2);
            } else {
                samsBadgeEl.textContent = "DESLIGADO";
                samsBadgeEl.className = "px-2.5 py-0.5 rounded text-xs font-mono font-bold bg-rose-500/20 text-rose-300 border border-rose-500/40";
                samsStatusTextEl.textContent = "VULNERÁVEL";
                logAI("ALERTA: SAMS desativado! Risco iminente de queda em desníveis.");
                playBeep(220, 'sawtooth', 0.3);
            }
        }

        function updateMag(val) {
            state.magIntensity = parseInt(val);
            document.getElementById('mag-val').textContent = val + '%';
        }

        function triggerForcedStumble() {
            state.isStumbling = true;
            state.stumbleTimer = 60;
            state.impactFlash = 1.0;
            impactBannerEl.classList.remove('hidden');
            
            if (state.samsActive) {
                logAI("⚡ TROPEÇO DETECTADO! Atuadores piezoelétricos dispararam. Fluido MR cristalizado instantaneamente!");
                playBeep(1200, 'square', 0.25);
            } else {
                logAI("🚨 QUEDA IMINENTE! SAMS desativado — o paciente sofreu impacto sem amortecimento!");
                playBeep(150, 'sawtooth', 0.4);
            }

            setTimeout(() => {
                impactBannerEl.classList.add('hidden');
                state.isStumbling = false;
            }, 2500);
        }

        function recalibrateSuit() {
            logAI("🔄 Calibração dos sensores piezoelétricos concluída. Resposta de reflexo otimizada para 0.8ms.");
            playBeep(750, 'sine', 0.2);
        }

        function logAI(message) {
            const timeStr = new Date().toTimeString().split(' ')[0];
            const div = document.createElement('div');
            div.className = "text-slate-300";
            div.innerHTML = `<span class="text-slate-500">[${timeStr}]</span> ${message}`;
            aiConsole.appendChild(div);
            aiConsole.scrollTop = aiConsole.scrollHeight;
        }

        // --- Main Animation & Simulation Loop ---
        function updateSimulation() {
            state.time += 0.04;
            if (!state.isStumbling) {
                state.walkCycle += 0.05;
            }

            // Periodic automatic terrain/stumble events if in terrain mode
            if (state.scenario === 'terrain' && Math.floor(state.time * 10) % 250 === 0 && !state.isStumbling) {
                triggerForcedStumble();
            }

            drawCanvas();
            requestAnimationFrame(updateSimulation);
        }

        function drawCanvas() {
            const width = canvas.clientWidth;
            const height = canvas.clientHeight;
            
            ctx.clearRect(0, 0, width, height);

            // Draw background grid
            ctx.strokeStyle = 'rgba(6, 182, 212, 0.07)';
            ctx.lineWidth = 1;
            const gridSize = 45;
            for (let x = 0; x < width; x += gridSize) {
                ctx.beginPath(); ctx.moveTo(x, 0); ctx.lineTo(x, height); ctx.stroke();
            }
            for (let y = 0; y < height; y += gridSize) {
                ctx.beginPath(); ctx.moveTo(0, y); ctx.lineTo(width, y); ctx.stroke();
            }

            // Draw floor
            const floorY = height * 0.75;
            ctx.strokeStyle = '#06b6d4';
            ctx.lineWidth = 3;
            ctx.beginPath();
            ctx.moveTo(0, floorY);
            ctx.lineTo(width, floorY);
            ctx.stroke();

            // Draw uneven terrain obstacle if scenario is terrain or stumble
            if (state.scenario === 'terrain' || state.scenario === 'stumble') {
                ctx.fillStyle = 'rgba(245, 158, 11, 0.2)';
                ctx.strokeStyle = '#f59e0b';
                ctx.lineWidth = 2;
                ctx.beginPath();
                ctx.moveTo(width * 0.55, floorY);
                ctx.lineTo(width * 0.65, floorY - 20);
                ctx.lineTo(width * 0.75, floorY);
                ctx.closePath();
                ctx.fill();
                ctx.stroke();
            }

            // Human Exoskeleton Kinematics
            const centerX = width * 0.45;
            const centerY = floorY - 140;

            // Stumble offset
            let stumbleOffsetX = 0;
            let stumbleOffsetY = 0;
            let bodyTilt = 0;

            if (state.isStumbling) {
                if (state.samsActive) {
                    // SAMS instantly corrects posture
                    stumbleOffsetX = Math.sin(state.time * 20) * 4;
                    bodyTilt = 0.05;
                } else {
                    // Fall forward
                    stumbleOffsetX = 35 * Math.min(1, (60 - state.stumbleTimer) / 20);
                    bodyTilt = 0.45;
                }
            }

            const hipX = centerX + stumbleOffsetX;
            const hipY = centerY - 20;
            const shoulderX = hipX - (bodyTilt * 60);
            const shoulderY = hipY - 70;
            const headX = shoulderX;
            const headY = shoulderY - 30;

            // Walk cycle angles
            const legCycle = Math.sin(state.walkCycle);
            const kneeBend1 = Math.abs(legCycle) * 35;
            const kneeBend2 = Math.abs(Math.sin(state.walkCycle + Math.PI)) * 35;

            // --- Draw Exoskeleton Frame & Joints ---
            ctx.save();

            // Exoskeleton Torso & Spine
            ctx.strokeStyle = state.samsActive ? '#06b6d4' : '#f43f5e';
            ctx.lineWidth = 8;
            ctx.lineCap = 'round';
            ctx.beginPath();
            ctx.moveTo(shoulderX, shoulderY);
            ctx.lineTo(hipX, hipY);
            ctx.stroke();

            // Spine Piezo Nodes
            ctx.fillStyle = '#ffffff';
            for (let i = 0; i < 4; i++) {
                const py = shoulderY + (i * 18);
                ctx.beginPath();
                ctx.arc(shoulderX, py, 4, 0, Math.PI * 2);
                ctx.fill();
            }

            // Head
            ctx.strokeStyle = '#94a3b8';
            ctx.lineWidth = 3;
            ctx.beginPath();
            ctx.arc(headX, headY, 14, 0, Math.PI * 2);
            ctx.stroke();

            // Robotic Arms (Exoskeleton)
            const armSwing = Math.cos(state.walkCycle) * 25;
            ctx.strokeStyle = '#334155';
            ctx.lineWidth = 6;
            ctx.beginPath();
            ctx.moveTo(shoulderX, shoulderY + 10);
            ctx.lineTo(shoulderX + armSwing, shoulderY + 60);
            ctx.lineTo(shoulderX + armSwing + 10, shoulderY + 110);
            ctx.stroke();

            // Legs (Exoskeleton + Magnetorheological fluid joints)
            // Left Leg
            const foot1X = hipX - 30 + (legCycle * 25);
            const knee1X = hipX - 15 + (legCycle * 10);
            const knee1Y = hipY + 50 - (kneeBend1 * 0.5);

            ctx.strokeStyle = state.samsActive && state.isStumbling ? '#f59e0b' : '#334155';
            ctx.lineWidth = 7;
            ctx.beginPath();
            ctx.moveTo(hipX, hipY);
            ctx.lineTo(knee1X, knee1Y);
            ctx.lineTo(foot1X, floorY);
            ctx.stroke();

            // Right Leg
            const foot2X = hipX + 30 - (legCycle * 25);
            const knee2X = hipX + 15 - (legCycle * 10);
            const knee2Y = hipY + 50 - (kneeBend2 * 0.5);

            ctx.beginPath();
            ctx.moveTo(hipX, hipY);
            ctx.lineTo(knee2X, knee2Y);
            ctx.lineTo(foot2X, floorY);
            ctx.stroke();

            // Draw Magnetorheological Fluid Joints (Knees & Hips with glowing magnetic flux rings)
            [
                { x: knee1X, y: knee1Y },
                { x: knee2X, y: knee2Y },
                { x: hipX, y: hipY }
            ].forEach(joint => {
                // Joint casing
                ctx.fillStyle = '#0f172a';
                ctx.strokeStyle = state.samsActive && state.isStumbling ? '#f59e0b' : '#06b6d4';
                ctx.lineWidth = 3;
                ctx.beginPath();
                ctx.arc(joint.x, joint.y, 9, 0, Math.PI * 2);
                ctx.fill();
                ctx.stroke();

                // Magnetic fluid field pulse if active
                if (state.samsActive) {
                    const pulse = 14 + Math.sin(state.time * 8) * 3;
                    ctx.strokeStyle = state.isStumbling ? 'rgba(245, 158, 11, 0.8)' : 'rgba(6, 182, 212, 0.4)';
                    ctx.lineWidth = 1.5;
                    ctx.beginPath();
                    ctx.arc(joint.x, joint.y, pulse, 0, Math.PI * 2);
                    ctx.stroke();
                }
            });

            // Impact shockwave visual if stumbling
            if (state.isStumbling && state.impactFlash > 0) {
                state.impactFlash -= 0.03;
                ctx.strokeStyle = state.samsActive ? 'rgba(16, 185, 129, 0.8)' : 'rgba(244, 63, 94, 0.9)';
                ctx.lineWidth = 3;
                ctx.beginPath();
                ctx.arc(foot1X, floorY, (1.0 - state.impactFlash) * 50, 0, Math.PI * 2);
                ctx.stroke();
            }

            ctx.restore();

            // Update UI telemetry badges dynamically
            if (state.isStumbling && state.samsActive) {
                metricViscosity.textContent = "CRISTALIZADO (100 Pa·s)";
                metricViscosity.className = "text-sm font-bold text-amber-400";
                metricStability.textContent = "100% (Travado)";
                hudReactionEl.textContent = "0.8 ms";
            } else if (state.samsActive) {
                metricViscosity.textContent = "Adaptativo (12 Pa·s)";
                metricViscosity.className = "text-sm font-bold text-emerald-400";
                metricStability.textContent = "99.8%";
                hudReactionEl.textContent = "1.2 ms";
            } else {
                metricViscosity.textContent = "Inativo (Fluido Livre)";
                metricViscosity.className = "text-sm font-bold text-rose-400";
                metricStability.textContent = state.isStumbling ? "12.4% (Queda!)" : "85.2%";
                hudReactionEl.textContent = "OFF";
            }
        }

        // Initialize on load
        window.onload = function() {
            resizeCanvas();
            updateSimulation();
        };
    </script>
</body>
</html>
