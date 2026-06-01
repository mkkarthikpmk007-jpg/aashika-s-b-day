<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Aashika Royal Chamber</title>
    <!-- Tailwind CSS for high-fidelity styling -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome for gorgeous modern icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Premium Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link
        href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&display=swap"
        rel="stylesheet">

    <style>
        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
        }

        .royal-font {
            font-family: 'Dancing Script', cursive;
        }

        /* Custom Premium Soft Pink Glows */
        .glass-card {
            background: rgba(255, 241, 242, 0.55);
            backdrop-filter: blur(14px);
            -webkit-backdrop-filter: blur(14px);
            border: 1px solid rgba(251, 113, 133, 0.3);
        }

        .glow-pink {
            box-shadow: 0 0 25px rgba(244, 63, 94, 0.4);
        }

        .glow-text-pink {
            text-shadow: 0 0 15px rgba(244, 63, 94, 0.6);
        }

        /* Custom scrollbar matching pink palette */
        ::-webkit-scrollbar {
            width: 6px;
        }

        ::-webkit-scrollbar-track {
            background: #ffe4e6;
        }

        ::-webkit-scrollbar-thumb {
            background: #fda4af;
            border-radius: 10px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: #f43f5e;
        }
    </style>
</head>

<body
    class="bg-rose-50 text-slate-800 min-h-screen flex flex-col justify-between overflow-x-hidden selection:bg-rose-200 selection:text-rose-900">

    <!-- Beautiful Ambient Pink Spheres Background Layer -->
    <div class="fixed inset-0 pointer-events-none z-0 overflow-hidden">
        <div class="absolute top-[-10%] left-[-10%] w-[50vw] h-[50vw] rounded-full bg-rose-200/50 blur-[120px]"></div>
        <div class="absolute bottom-[-10%] right-[-10%] w-[50vw] h-[50vw] rounded-full bg-pink-200/40 blur-[120px]">
        </div>
        <div class="absolute top-[40%] right-[20%] w-[30vw] h-[30vw] rounded-full bg-rose-100/60 blur-[100px]"></div>
    </div>

    <!-- CUSTOM NOTIFICATION BOX (Saves from using alert) -->
    <div id="toast-notif"
        class="fixed top-5 right-5 z-50 transform translate-x-[150%] transition-transform duration-300 ease-out flex items-center gap-3 bg-white border-l-4 border-rose-500 py-3 px-5 rounded-lg shadow-lg max-w-sm">
        <div class="text-rose-500 text-lg"><i id="toast-icon" class="fa-solid fa-circle-check"></i></div>
        <div>
            <h4 class="font-bold text-xs text-slate-800" id="toast-title">Notification</h4>
            <p class="text-[10px] text-slate-500" id="toast-msg">Process Completed Successfully</p>
        </div>
    </div>

    <!-- ================= PREMIUM ENTRANCE KEYGATE ================= -->
    <div id="entrance-gate" class="relative z-10 flex-grow flex flex-col items-center justify-center p-4">
        <div
            class="max-w-md w-full glass-card p-8 rounded-3xl text-center shadow-xl border border-rose-200 relative overflow-hidden">
            <!-- Crown accent icon decoration -->
            <div class="mb-4 text-rose-400 text-5xl drop-shadow-md"><i class="fa-solid fa-crown animate-bounce"></i>
            </div>
            <h1 class="royal-font text-5xl text-rose-600 mb-2 font-bold drop-shadow-sm">Aashika's Protocol</h1>
            <p class="text-[10px] tracking-widest text-rose-400 uppercase font-bold mb-8">SECURE ACCESS • HIGHNESS MODE
                ONLY</p>

            <!-- Premium Princess Scan Pad -->
            <div id="biometric-pad" onclick="triggerBiometricVerify()"
                class="relative w-44 h-44 mx-auto mb-8 border border-rose-300 rounded-3xl flex flex-col items-center justify-center bg-rose-50/70 hover:bg-rose-100/70 transition-all duration-300 cursor-pointer shadow-inner group">
                <!-- Glowing laser scanner line -->
                <div id="laser-bar"
                    class="absolute left-0 right-0 h-1 bg-gradient-to-r from-transparent via-rose-500 to-transparent shadow-[0_0_12px_#f43f5e] top-0 hidden">
                </div>

                <div id="scanner-wrapper" class="text-center p-4 transition-all duration-300 group-hover:scale-105">
                    <i id="fingerprint-icon" class="fa-solid fa-fingerprint text-5xl text-rose-400"></i>
                    <p id="biometric-label" class="text-[9px] mt-3 font-bold tracking-wider text-rose-500 uppercase">TAP
                        TO CONFIRM ID</p>
                </div>
            </div>

            <!-- Manual Pin Fallback -->
            <div class="space-y-3 max-w-xs mx-auto">
                <input type="password" id="access-pass" placeholder="SECRET KEYWORD OR NICKNAME"
                    class="w-full bg-white/80 border border-rose-200 focus:border-rose-400 text-rose-700 text-xs px-4 py-3 rounded-xl text-center focus:outline-none placeholder:text-rose-300 font-bold tracking-widest transition-all">
                <button onclick="checkAccessKey()"
                    class="w-full bg-rose-500 hover:bg-rose-600 active:scale-95 text-white text-xs font-bold py-3 rounded-xl tracking-wider shadow-md shadow-rose-200 transition-all">
                    UNLOCK ROYAL COMPARTMENT
                </button>
            </div>
            <p id="entrance-error" class="text-rose-600 text-[10px] mt-4 font-bold tracking-wider h-4 uppercase"></p>
        </div>
    </div>

    <!-- ================= MAIN CORE PINK DASHBOARD ================= -->
    <div id="royal-chamber-dashboard"
        class="hidden relative z-10 p-4 md:p-8 max-w-7xl mx-auto w-full space-y-6 flex-grow">

        <!-- PREMIUM DYNAMIC HEADER BAR -->
        <div
            class="glass-card p-6 rounded-3xl flex flex-col md:flex-row md:items-center justify-between gap-4 shadow-md text-center md:text-left relative overflow-hidden">
            <!-- Sparkles decorations -->
            <div class="absolute -top-6 -left-6 text-rose-300/20 text-7xl"><i
                    class="fa-solid fa-wand-magic-sparkles"></i></div>
            <div class="absolute -bottom-6 -right-6 text-rose-300/20 text-7xl"><i class="fa-solid fa-cake-candles"></i>
            </div>

            <div class="flex flex-col md:flex-row items-center gap-5 z-10 w-full justify-between">
                <div class="flex flex-col md:flex-row items-center gap-4">
                    <div
                        class="w-16 h-16 rounded-full border border-rose-300 bg-white shadow-sm flex items-center justify-center text-rose-500 text-3xl animate-spin-slow">
                        <i class="fa-solid fa-gift"></i>
                    </div>
                    <div>
                        <!-- BOLD BIRTHDAY INSCRIPTION FONT -->
                        <h2
                            class="royal-font text-5xl md:text-6xl text-rose-600 font-extrabold tracking-wide drop-shadow-sm glow-text-pink select-text">
                            Happy Birthday Aashika! 🎉🌸
                        </h2>
                        <p class="text-[10px] tracking-widest text-rose-400 font-black uppercase mt-1">THE QUEEN OF
                            EXTRAVAGANT SANDA PROTOCOLS</p>
                    </div>
                </div>

                <div class="flex flex-wrap items-center justify-center gap-3 text-[10px] font-bold z-10">
                    <span
                        class="bg-emerald-100 text-emerald-800 px-3 py-1.5 rounded-full border border-emerald-200 flex items-center gap-1"><span
                            class="w-1.5 h-1.5 rounded-full bg-emerald-500 animate-ping"></span> BIRTHDAY LIVE:
                        YES</span>
                    <span class="bg-rose-100 text-rose-800 px-3 py-1.5 rounded-full border border-rose-200">HIERARCHY:
                        ROYAL HIGHNESS (AASHIKA)</span>
                </div>
            </div>
        </div>

        <!-- TWO MAIN CONTAINER GRID SYSTEM -->
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">

            <!-- COLUMN 1: QUOTES & COMPLIMENTS, AFFINITY INDEX -->
            <div class="space-y-6">
                <!-- 1. PREMIUM DYNAMIC QUOTES CORNER -->
                <div
                    class="glass-card p-6 rounded-3xl shadow-sm relative overflow-hidden flex flex-col justify-between min-h-[340px]">
                    <div>
                        <div class="flex items-center justify-between mb-4">
                            <span
                                class="text-[10px] bg-rose-200/50 text-rose-600 px-2.5 py-1 rounded-full font-black tracking-widest uppercase">Mood
                                Wisdom Box</span>
                            <span class="text-rose-300 text-2xl animate-pulse"><i
                                    class="fa-solid fa-quote-right"></i></span>
                        </div>

                        <!-- Blockquote element with fade animation -->
                        <div class="my-4 transition-all duration-300" id="quote-wrapper">
                            <p class="text-slate-700 font-semibold text-lg md:text-xl leading-relaxed mb-3"
                                id="quote-text">
                                "En sister kitta secret sonna,
adhu secret-ah irukkum...
Aana family ellarum already therinjiruppanga! 🤣"
                            </p>
                            <p class="text-[10px] tracking-wider text-rose-500 font-bold uppercase" id="quote-author">~
                                Sibling Command Center</p>
                        </div>
                    </div>

                    <button onclick="generateNewQuote()"
                        class="w-full bg-rose-500 hover:bg-rose-600 active:scale-95 text-white font-bold py-3 rounded-xl text-xs transition-all tracking-wider shadow-sm flex items-center justify-center gap-2 mt-4">
                        <i class="fa-solid fa-shuffle"></i> SHUFFLE TANGLISH KADI JOKE & ROASTS
                    </button>
                </div>

                <!-- 2. SIBLING BOND LEVEL CONTROLLER -->
                <div class="glass-card p-6 rounded-3xl shadow-sm space-y-4">
                    <h3 class="text-xs font-black tracking-widest text-slate-700 uppercase flex items-center gap-2">
                        <i class="fa-solid fa-heart-pulse text-rose-500 text-sm animate-pulse"></i> Sibling Affinity
                        Index
                    </h3>

                    <div class="space-y-2">
                        <div class="flex justify-between text-xs font-bold">
                            <span class="text-slate-600">Bond Level with Bro</span>
                            <span class="text-rose-500" id="affinity-percent">50%</span>
                        </div>
                        <div class="w-full bg-rose-100 rounded-full h-3 border border-rose-200 overflow-hidden">
                            <div id="affinity-progress-bar"
                                class="bg-gradient-to-r from-pink-400 to-rose-500 h-full rounded-full transition-all duration-500"
                                style="width: 50%;"></div>
                        </div>
                        <p class="text-[9px] text-slate-400 font-semibold uppercase text-center" id="affinity-status">
                            Status: Standard Peaceful Co-existence</p>
                    </div>

                    <!-- Dynamic Controls to alter bond meter -->
                    <div class="grid grid-cols-2 gap-2 pt-2">
                        <button onclick="adjustAffinity(15)"
                            class="bg-white hover:bg-rose-100 text-rose-600 border border-rose-200 text-[10px] font-black py-2.5 rounded-lg uppercase tracking-wider transition-all">Buy
                            Chocolate (+15)</button>
                        <button onclick="adjustAffinity(-15)"
                            class="bg-white hover:bg-rose-50 text-slate-600 border border-rose-100 text-[10px] font-black py-2.5 rounded-lg uppercase tracking-wider transition-all">Steal
                            Remote (-15)</button>
                    </div>
                </div>
            </div>

            <!-- COLUMN 2: FAVORS & SECRETS, FEEDBACK -->
            <div class="space-y-6">

                <!-- 1. PINK SHADE BRIBE NEGOTIATOR (UPGRADED ITEMS) -->
                <div class="glass-card p-6 rounded-3xl shadow-sm">
                    <h3
                        class="text-xs font-black tracking-widest text-slate-700 uppercase mb-4 flex items-center gap-2">
                        <i class="fa-solid fa-handshake text-rose-500"></i> Royal Favor Negotiation Panel
                    </h3>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
                        <div>
                            <label class="text-[9px] text-slate-500 font-bold uppercase tracking-wider block mb-1">Favor
                                Requested from Bro</label>
                            <select id="negotiate-favor"
                                class="w-full bg-white border border-rose-200 rounded-xl p-3 text-xs text-rose-600 font-bold focus:outline-none focus:border-rose-400">
                                <option value="biryani">Buy me delicious Chicken Biryani 🍗</option>
                                <option value="chores">Complete my cleaning chore segment 🧹</option>
                                <option value="excuse">Lie to Mother to protect my cover 🤫</option>
                                <option value="academic">Complete my heavy college assignment 📝</option>
                                <option value="hoodie">Lend me your favorite branded hoodie 🧥</option>
                                <option value="chauffeur">Instant driver drop service to friend's home 🚗</option>
                                <option value="recharge">Recharge my high speed data pack instantly 📱</option>
                            </select>
                        </div>
                        <div>
                            <label
                                class="text-[9px] text-slate-500 font-bold uppercase tracking-wider block mb-1">Aashika's
                                Counter-Offering Asset</label>
                            <select id="negotiate-bribe"
                                class="w-full bg-white border border-rose-200 rounded-xl p-3 text-xs text-rose-600 font-bold focus:outline-none focus:border-rose-400">
                                <option value="maggi">Will cook spicy Maggi noodles 🍜</option>
                                <option value="secret">Won't expose your hidden minor secrets 🤐</option>
                                <option value="thanks">Will offer a genuine 'Aww, thanks bro!' 💖</option>
                                <option value="tea">Will prepare an excellent warm cup of tea ☕</option>
                                <option value="praise">Will praise you nicely in front of your friends 😂</option>
                                <option value="dishes">Will do the dining room dishes for 3 days 🍽️</option>
                            </select>
                        </div>
                    </div>

                    <button onclick="evaluateSISTERBargain()"
                        class="w-full bg-gradient-to-r from-rose-400 to-rose-500 hover:from-rose-500 hover:to-rose-600 text-white py-3 rounded-xl text-xs font-black tracking-widest shadow-md transition-all cursor-pointer">
                        RUN BARGAIN SUITABILITY ALGORITHM
                    </button>

                    <div id="bargain-result-box"
                        class="mt-4 p-4 bg-white/75 rounded-2xl border border-dashed border-rose-300 text-center text-xs hidden">
                        <span id="bargain-result-text" class="font-bold uppercase tracking-wider"></span>
                    </div>
                </div>

                <!-- 2. CHRONO SECRET ENCRYPTED LOCKER (SECURE TO COUNTDOWN FOREVER/UNTIL MILESTONE) -->
                <div class="glass-card p-6 rounded-3xl shadow-sm relative overflow-hidden">
                    <h3
                        class="text-xs font-black tracking-widest text-slate-700 uppercase mb-2 flex items-center gap-2">
                        <i class="fa-solid fa-box-archive text-rose-500"></i> The Aashika Special Locker
                    </h3>
                    <p class="text-[9px] text-rose-400/80 mb-4 uppercase tracking-widest font-black">Securely encrypted
                        timeline capsule</p>

                    <div class="bg-white/80 border border-rose-100 p-5 rounded-2xl text-center">
                        <!-- Dynamic Clock Elements -->
                        <div class="text-xl md:text-3xl font-black text-rose-600 tracking-wider mb-3 flex items-center justify-center gap-1 sm:gap-2"
                            id="capsule-chrono-clock">
                            <span>00</span><span class="text-rose-400 text-xs">d</span> :
                            <span>00</span><span class="text-rose-400 text-xs">h</span> :
                            <span>00</span><span class="text-rose-400 text-xs">m</span> :
                            <span>00</span><span class="text-rose-400 text-xs">s</span>
                        </div>
                        <div
                            class="text-[9px] text-amber-500 font-bold uppercase tracking-wider flex items-center justify-center gap-1">
                            <i class="fa-solid fa-circle-exclamation"></i> DECRYPT LOCK ONLY ON NEXT BIG MILESTONE
                            CELEBRATION!
                        </div>

                        <!-- Hidden Premium Content -->
                        <div id="hidden-greetings-board"
                            class="hidden mt-4 pt-4 border-t border-rose-200 text-xs text-slate-700 p-4 rounded-xl text-left bg-rose-50/50">
                            <p class="royal-font text-3xl text-rose-600 font-bold text-center mb-2">Unlocked Premium
                                Access! 🎉</p>
                            <p class="leading-relaxed text-xs text-slate-600">To the world's most annoying yet wonderful
                                sister—Happy Birthday! You deserve a premium slice of joy today. Ennoda core sister
                                application layout successful! Claim your premium actual physical gift straight from
                                your bro! 🎁💖</p>
                        </div>
                    </div>
                </div>

                <!-- 3. EMAIL FEEDBACK & MESSAGE REGISTRY (NEW) -->
                <div class="glass-card p-6 rounded-3xl shadow-sm space-y-4">
                    <div class="flex items-center justify-between">
                        <h3 class="text-xs font-black tracking-widest text-slate-700 uppercase flex items-center gap-2">
                            <i class="fa-solid fa-envelope text-rose-500"></i> Feedback & Sibling Message Registry 💌
                        </h3>
                        <span
                            class="text-[9px] bg-rose-200 text-rose-700 font-bold px-2 py-0.5 rounded-full border border-rose-300">Mail
                            Connection</span>
                    </div>

                    <!-- Feedback Form configured directly for mkkarthikpmk007@gmail.com -->
                    <form id="sibling-feedback-form" onsubmit="handleFeedbackSubmission(event)" class="space-y-3">
                        <div>
                            <label class="text-[8px] text-slate-400 font-black tracking-wider uppercase block mb-1">Your
                                Name / Highness Nickname</label>
                            <input type="text" name="name" id="feedback-name" required placeholder="Who is writing?"
                                value="Aashika 👑"
                                class="w-full bg-white border border-rose-200 focus:border-rose-400 text-xs text-rose-700 px-3 py-2.5 rounded-xl focus:outline-none placeholder:text-rose-300 font-bold">
                        </div>
                        <div>
                            <label class="text-[8px] text-slate-400 font-black tracking-wider uppercase block mb-1">Your
                                Feedback / Birthday Demands 🎁</label>
                            <textarea name="message" id="feedback-message" rows="3" required
                                placeholder="Type whatever you want, it will route directly to karthik's inbox!"
                                class="w-full bg-white border border-rose-200 focus:border-rose-400 text-xs text-rose-700 px-3 py-2.5 rounded-xl focus:outline-none placeholder:text-rose-300 font-semibold resize-none"></textarea>
                        </div>

                        <button type="submit"
                            class="w-full bg-rose-500 hover:bg-rose-600 active:scale-95 text-white text-xs font-bold py-2.5 rounded-xl transition-all tracking-wider uppercase cursor-pointer flex items-center justify-center gap-2">
                            <i class="fa-solid fa-paper-plane animate-pulse"></i> Transmit Message to Bro's Mail
                        </button>
                    </form>
                </div>

            </div>
        </div>
    </div>

    <!-- ================= DYNAMIC FOOTER ================= -->
    <footer
        class="relative z-10 w-full p-4 bg-rose-100/60 border-t border-rose-200/50 text-center text-[10px] text-rose-500/70 tracking-widest uppercase font-bold">
        Programmed & Handcrafted with absolute sisterly protection frameworks • India Node
    </footer>

    <!-- ================= CLIENT SIDE JS ENGREEMENT ================= -->
    <script>
        // Array of custom curated Sister Tanglish Kadi jokes & quotes
        const customQuotes = [
            
            { text: "Kadi Joke: Oru thabaal petti mela yen kal vachaanga? Enna athu 'Post Office' aahm! 📬 Sirippula vaitheriyuthu! 😂", author: "Extreme Kadi Board" },
            { text: "Kadi Joke: Airplane-la yen pathu peru ninutu poranga? Enna athu 'Air-bus' aahm! 🚌✈️ Ahaha, kadi joke speed run! 🔥", author: "Local Kadi King" },
            { text: "Kadi Joke: Oru thabaal petti mela yen kal vachaanga? Enna athu 'Post Office' aahm! 📬 Sirippula vaitheriyuthu! 😂", author: "Extreme Kadi Board" },
            { text: "Aashika special: Normal humans sleep at night. My sister? Dynamic scrolling on Instagram reels at 3 AM! 📱👽 Go to sleep alien!", author: "The Sibling Intelligence" },
            { text: "If irritating your brother was an Olympic sport, Aashika would definitely win Gold, Silver and Platinum medals at the same time! 🥇🏆", author: "Olympic Sibling Guild" },
            { text: "Kadi Joke: Singam yen kancha thosai sapaduthu? Yen na athuku 'Suda' theriyaathu! 🦁🔥 Hahaha kadi-oda extreme level!", author: "Silly Lion Council" },
            { text: "Enna thaan sandai potalum, unna mathiri oru thangaமான sister-ah adikka kooda manasu varaathu (Chocolates kudutha mattum)! 🍫💖", author: "The Sweet Bargain Section" },
            { text: "Kadi Joke: Kadal yen blue color-la iruku? Enna athula thaan 'Blue-berry' iruku! 🫐🌊 Enna oru puthsali-thanam! 😂", author: "Blue Ocean Research Group" },
            { text: "Kadi Joke: Oru bike accident-la yen head-ku adi padala? Enna helmet thalaiku 'safe-guard' ahm! 🏍️ Sila kadi joke sirippa varathu, azhugaiya thaan varum! 😭", author: "Dynamic Helmet Association" },
            { text: "Sister definition: Sanda podumpothu Rowdy 😈, appa kitta maatikumpothu innocent baby 😇, bro kitta treat ketkumpothu ultimate software diplomat! 🤷‍♂️🎀", author: "International Sibling Standards" },
            { text: "Ennoda standard secret documents thirudan (Aashika): 'Unnoda phone password sollu, naan summa thaan paapen' nu solra ulagathin muga mukkiya poi! 📱🤥", author: "Bro Security Agency" }
        ];

        // Sibling Affinity Index tracking
        let affinityLevel = parseInt(localStorage.getItem('aashika_sibling_affinity')) || 50;

        window.onload = function () {
            updateAffinityDisplay();
        };

        // --- CUSTOM TOAST FUNCTION ---
        function triggerCustomToast(title, message, iconType = "success") {
            const toast = document.getElementById('toast-notif');
            const tTitle = document.getElementById('toast-title');
            const tMsg = document.getElementById('toast-msg');
            const tIcon = document.getElementById('toast-icon');

            tTitle.innerText = title;
            tMsg.innerText = message;

            if (iconType === "success") {
                tIcon.className = "fa-solid fa-circle-check text-emerald-500";
                toast.style.borderLeftColor = "#10b981";
            } else if (iconType === "danger") {
                tIcon.className = "fa-solid fa-triangle-exclamation text-rose-500";
                toast.style.borderLeftColor = "#f43f5e";
            } else {
                tIcon.className = "fa-solid fa-info text-rose-500";
                toast.style.borderLeftColor = "#f43f5e";
            }

            toast.style.transform = "translateX(0)";
            setTimeout(() => {
                toast.style.transform = "translateX(150%)";
            }, 3500);
        }

        // --- 1. BIOMETRIC KEY LOCK LOGIC ---
        function triggerBiometricVerify() {
            const bar = document.getElementById('laser-bar');
            const label = document.getElementById('biometric-label');
            const icon = document.getElementById('fingerprint-icon');

            bar.classList.remove('hidden');
            bar.classList.add('animate-bounce');
            label.innerText = "AUTHENTICATING ROYAL BIOMETRICS...";
            label.className = "text-[9px] mt-3 font-bold tracking-wider text-rose-600 uppercase animate-pulse";
            icon.className = "fa-solid fa-fingerprint text-rose-500 animate-pulse";

            setTimeout(() => {
                bar.classList.add('hidden');
                bar.classList.remove('animate-bounce');
                label.innerText = "AASHIKA REGISTER CONFIRMED!";
                label.className = "text-[9px] mt-3 font-bold tracking-wider text-emerald-500 uppercase";
                icon.className = "fa-solid fa-circle-check text-emerald-500";
                document.getElementById('access-pass').value = "AASHIKA";

                triggerCustomToast("Biometrics Pass", "Aashika ID successfully mapped by system sensor!", "success");
            }, 2200);
        }

        function checkAccessKey() {
            const pass = document.getElementById('access-pass').value.trim().toUpperCase();
            const gateError = document.getElementById('entrance-error');

            if (pass === "AASHIKA" || pass === "SISTER" || pass === "QUEEN") {
                document.getElementById('entrance-gate').classList.add('hidden');
                document.getElementById('royal-chamber-dashboard').classList.remove('hidden');
                triggerCustomToast("Access Granted", "Welcome back, Your Royal Highness!", "success");
                startCapsuleTimer();
            } else {
                gateError.innerText = "❌ CORRUPT PASSKEY: RETRY SECURITY MAPPING SEGMENT!";
                setTimeout(() => { gateError.innerText = ""; }, 3000);
            }
        }

        // --- 2. RANDOM QUOTE ENGINE (TANGLISH KADI) ---
        function generateNewQuote() {
            const textEl = document.getElementById('quote-text');
            const authorEl = document.getElementById('quote-author');
            const wrapper = document.getElementById('quote-wrapper');

            wrapper.classList.add('opacity-0');

            setTimeout(() => {
                const random = customQuotes[Math.floor(Math.random() * customQuotes.length)];
                textEl.innerText = `"${random.text}"`;
                authorEl.innerText = `~ ${random.author}`;
                wrapper.classList.remove('opacity-0');
                triggerCustomToast("Shuffled Quote", "New Tanglish perspective loaded! 😂", "info");
            }, 300);
        }

        // --- 3. SIBLING AFFINITY PROGRESS LOGIC ---
        function adjustAffinity(value) {
            affinityLevel += value;
            if (affinityLevel > 100) affinityLevel = 100;
            if (affinityLevel < 0) affinityLevel = 0;

            localStorage.setItem('aashika_sibling_affinity', affinityLevel);
            updateAffinityDisplay();
        }

        function updateAffinityDisplay() {
            const bar = document.getElementById('affinity-progress-bar');
            const text = document.getElementById('affinity-percent');
            const status = document.getElementById('affinity-status');

            bar.style.width = affinityLevel + "%";
            text.innerText = affinityLevel + "%";

            if (affinityLevel >= 80) {
                status.innerText = "Status: Absolute Royal Sibling Friendship Champion 💖";
                status.className = "text-[9px] text-rose-600 font-bold uppercase text-center animate-pulse";
            } else if (affinityLevel >= 40) {
                status.innerText = "Status: Standard Peaceful Co-existence ✨";
                status.className = "text-[9px] text-slate-500 font-semibold uppercase text-center";
            } else {
                status.innerText = "Status: Active Sanda Phase! Immediate Maggi bribe recommended 🌋";
                status.className = "text-[9px] text-amber-600 font-bold uppercase text-center";
            }
        }

        // --- 4. BRIBE NEGOTIATOR ENGINE (UPGRADED) ---
        function evaluateSISTERBargain() {
            const favor = document.getElementById('negotiate-favor').value;
            const bribe = document.getElementById('negotiate-bribe').value;
            const box = document.getElementById('bargain-result-box');
            const text = document.getElementById('bargain-result-text');

            box.classList.remove('hidden');

            if (bribe === 'thanks') {
                text.innerText = "❌ Deal Denied: Sibling server says 'Thank you podhumu na treat thara mudiyathu!' Error 404.";
                text.className = "font-bold text-rose-500 tracking-wider";
            } else if (bribe === 'secret' || (favor === 'biryani' && bribe === 'tea') || bribe === 'dishes') {
                text.innerText = "🤝 Deal Approved: Highly profitable sibling contract active! Proceed with exchange.";
                text.className = "font-bold text-emerald-600 tracking-wider";
            } else {
                text.innerText = "⏳ Counter-Demand: Brother requests dynamic execution allowance. Add extra chocolate chip cookies!";
                text.className = "font-bold text-amber-500 tracking-wider";
            }
        }

        // --- 5. TIMER CAPSULE UNLOCK COUNTDOWN (DO NOT AUTO-OPEN IN 2 DAYS) ---
        function startCapsuleTimer() {
            // Hardcoded safe target date set long into the future (e.g. October 25, 2026 or next Birthday event)
            // This prevents it from opening automatically in 2 days. You can change this date as needed!
            const eventTarget = new Date("October 25, 2026 00:00:00").getTime();

            function runCycle() {
                const now = new Date().getTime();
                const diff = eventTarget - now;

                const days = Math.floor(diff / (1000 * 60 * 60 * 24));
                const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
                const seconds = Math.floor((diff % (1000 * 60)) / 1000);

                const element = document.getElementById('capsule-chrono-clock');

                if (diff < 0) {
                    clearInterval(intervalInstance);
                    element.innerText = "ACCESS REVEALED!";
                    document.getElementById('hidden-greetings-board').classList.remove('hidden');
                } else {
                    element.innerHTML = `
                        <span>${days.toString().padStart(2, '0')}</span><span class="text-rose-400 text-xs">d</span> : 
                        <span>${hours.toString().padStart(2, '0')}</span><span class="text-rose-400 text-xs">h</span> : 
                        <span>${minutes.toString().padStart(2, '0')}</span><span class="text-rose-400 text-xs">m</span> : 
                        <span>${seconds.toString().padStart(2, '0')}</span><span class="text-rose-400 text-xs">s</span>
                    `;
                }
            }

            runCycle();
            const intervalInstance = setInterval(runCycle, 1000);
        }

        // --- 6. EMAIL REGISTRY & FEEDBACK HANDLER (Directing to Bro's custom Mailbox) ---
        function handleFeedbackSubmission(event) {
            event.preventDefault();
            const name = document.getElementById('feedback-name').value;
            const msg = document.getElementById('feedback-message').value;

            triggerCustomToast("Transmitting", "Aashika's letter is being prepared... 📬", "info");

            // Format dynamic direct mailto system to mkkarthikpmk007@gmail.com
            setTimeout(() => {
                triggerCustomToast("Opening Mail Client", "Demands logged! Sending dispatch to Karthik... ✉️", "success");

                const mailtoLink = `mailto:mkkarthikpmk007@gmail.com?subject=${encodeURIComponent("Aashika's Birthday Demand Box 👑")}&body=${encodeURIComponent("Hi Karthik,\n\nI have submitted a response to your system feedback console:\n\nSender: " + name + "\nMessage: " + msg + "\n\nRegards,\nAashika Protocol System Client")}`;

                // Triggers user's native device mail app to send instantly to your mail ID
                window.location.href = mailtoLink;
            }, 1200);
        }
    </script>
</body>

</html><img width="920" height="451" alt="image" src="https://github.com/user-attachments/assets/3418b813-ccd5-4e57-94b0-6f543b9abe5b" />
