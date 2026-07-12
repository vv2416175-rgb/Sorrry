<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>For My Love</title>
  
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  
  <!-- Google Fonts: Playfair Display & Inter (as fallback for Satoshi) -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&family=Playfair+Display:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">
  
  <!-- FontAwesome CDN for premium minimalist icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  
  <!-- GSAP Core for cinematic animations -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
  
  <!-- Canvas Confetti for the Grand Finale explosion -->
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

  <script>
    // Tailwind Config for custom luxury color palette
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            midnight: '#09090B',
            darkzinc: '#18181B',
            rosepink: '#FF5F8F',
            warmred: '#FF4D6D',
            gold: '#FFD166',
            mutedgray: '#D4D4D8',
          },
          fontFamily: {
            serif: ['"Playfair Display"', 'serif'],
            sans: ['Inter', 'sans-serif'],
          }
        }
      }
    }
  </script>

  <style>
    /* Premium Aurora Background Gradient Layer 1 */
    @keyframes aurora {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }
    .aurora-bg {
      background: linear-gradient(-45deg, #09090B, #18181B, #1f0d14, #0b1a24, #09090B);
      background-size: 400% 400%;
      animation: aurora 25s ease infinite;
    }

    /* Glassmorphism Design */
    .glass-card {
      background: rgba(24, 24, 27, 0.45);
      backdrop-filter: blur(16px);
      -webkit-backdrop-filter: blur(16px);
      border: 1px solid rgba(255, 255, 255, 0.08);
      box-shadow: 0 12px 40px 0 rgba(0, 0, 0, 0.5);
    }

    /* Subdued Pulsing Hearts */
    @keyframes heartPulse {
      0%, 100% { transform: scale(1); filter: drop-shadow(0 0 10px rgba(255, 95, 143, 0.4)); }
      50% { transform: scale(1.08); filter: drop-shadow(0 0 25px rgba(255, 77, 109, 0.8)); }
    }
    .pulse-heart {
      animation: heartPulse 3s ease-in-out infinite;
    }

    /* Audio Visualizer Indicator Animation */
    @keyframes eq-bar {
      0%, 100% { height: 4px; }
      50% { height: 16px; }
    }
    .eq-bar-1 { animation: eq-bar 0.8s ease infinite; }
    .eq-bar-2 { animation: eq-bar 1.2s ease infinite 0.2s; }
    .eq-bar-3 { animation: eq-bar 0.9s ease infinite 0.4s; }

    /* Custom Scrollbar for premium feel */
    ::-webkit-scrollbar {
      width: 6px;
    }
    ::-webkit-scrollbar-track {
      background: #09090B;
    }
    ::-webkit-scrollbar-thumb {
      background: rgba(255, 95, 143, 0.3);
      border-radius: 3px;
    }
    ::-webkit-scrollbar-thumb:hover {
      background: rgba(255, 95, 143, 0.6);
    }
  </style>
</head>
<body class="aurora-bg text-white font-sans min-h-screen flex flex-col justify-between overflow-x-hidden selection:bg-rosepink/30 selection:text-white">

  <!-- Interactive Background Canvas (Layer 2, 3 & 4) -->
  <canvas id="bg-canvas" class="fixed inset-0 w-full h-full pointer-events-none z-0"></canvas>

  <!-- Glowing Fixed Progress Bar -->
  <div class="fixed top-0 left-0 w-full h-1.5 z-50 bg-white/5">
    <div id="progress-indicator" class="h-full w-[14.28%] bg-gradient-to-r from-rosepink to-warmred shadow-[0_0_12px_rgba(255,77,109,0.7)] transition-all duration-700 ease-out"></div>
  </div>

  <!-- Global Header (Logo & Procedural Soundtrack Control) -->
  <header class="relative z-10 w-full max-w-7xl mx-auto px-6 py-5 flex justify-between items-center">
    <div class="font-serif tracking-widest text-sm opacity-60 uppercase">For You Always</div>
    
    <!-- Music Button Controls -->
    <button onclick="toggleMusic()" id="music-btn" class="flex items-center gap-2 px-4 py-2 rounded-full glass-card hover:bg-white/10 transition-all duration-300 border border-white/10 group focus:outline-none">
      <div id="eq-container" class="hidden flex items-end gap-0.5 h-4 w-4">
        <span class="eq-bar-1 w-[2px] bg-rosepink rounded-full"></span>
        <span class="eq-bar-2 w-[2px] bg-rosepink rounded-full"></span>
        <span class="eq-bar-3 w-[2px] bg-rosepink rounded-full"></span>
      </div>
      <i id="mute-icon" class="fa-solid fa-music text-xs text-rosepink/80 group-hover:scale-110 transition-transform"></i>
      <span id="music-text" class="text-xs font-medium tracking-wide uppercase">Play Soft Music</span>
    </button>
  </header>

  <!-- Interactive 7-Step Journey Container -->
  <main class="relative z-10 flex-grow flex items-center justify-center px-4 py-12 max-w-4xl mx-auto w-full">
    
    <!-- STEP 1: WELCOME -->
    <div id="step-1" class="step-container w-full">
      <div class="glass-card rounded-3xl p-8 md:p-12 text-center max-w-xl mx-auto transform transition-all duration-500 hover:border-white/15">
        <div class="pulse-heart text-6xl md:text-7xl mb-8 select-none">❤️</div>
        <h1 class="font-serif text-4xl md:text-5xl font-medium tracking-wide mb-6 leading-tight">Hey My Love...</h1>
        <p class="text-mutedgray text-base md:text-lg font-light leading-relaxed mb-8 max-w-md mx-auto">
          Before you leave this page, I just want you to give me a few minutes. I made something straight from my heart.
        </p>
        <button onclick="nextStep(2)" class="px-8 py-4 rounded-full bg-gradient-to-r from-rosepink to-warmred text-white text-sm font-semibold uppercase tracking-wider shadow-[0_4px_20px_rgba(255,95,143,0.3)] hover:shadow-[0_4px_30px_rgba(255,95,143,0.65)] hover:scale-[1.05] active:scale-[0.98] transition-all duration-300">
          Continue ❤️
        </button>
      </div>
    </div>

    <!-- STEP 2: THE APOLOGY -->
    <div id="step-2" class="step-container w-full hidden opacity-0">
      <div class="glass-card rounded-3xl p-8 md:p-12 text-center max-w-2xl mx-auto">
        <div class="text-6xl text-warmred/90 mb-6 drop-shadow-[0_0_15px_rgba(255,77,109,0.3)]">💔</div>
        <h2 class="font-serif text-3xl md:text-4xl font-semibold mb-6">I'm Truly Sorry</h2>
        <div class="space-y-4 text-mutedgray text-sm md:text-base font-light leading-relaxed max-w-lg mx-auto">
          <p class="stagger-txt">I know I hurt you.</p>
          <p class="stagger-txt">Maybe my words... Maybe my actions... Maybe both.</p>
          <p class="stagger-txt text-rosepink/90 font-medium">Whatever happened, I regret every single moment that caused tears in your eyes.</p>
          <p class="stagger-txt italic">If I could go back in time, I would change everything.</p>
        </div>
        <button onclick="nextStep(3)" class="mt-8 px-8 py-4 rounded-full bg-transparent border border-white/20 text-white text-sm font-semibold uppercase tracking-wider hover:bg-white/5 hover:border-rosepink/50 hover:scale-[1.05] active:scale-[0.98] transition-all duration-300">
          I Need To Tell You More
        </button>
      </div>
    </div>

    <!-- STEP 3: WHAT I REALIZED (Bento Grid) -->
    <div id="step-3" class="step-container w-full hidden opacity-0">
      <div class="text-center max-w-3xl mx-auto">
        <h2 class="font-serif text-3xl md:text-4xl font-semibold mb-8">I Finally Understood</h2>
        
        <!-- Bento Grid Layout -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-left mb-8">
          <!-- Card 1 -->
          <div class="glass-card rounded-2xl p-6 hover:border-rosepink/40 hover:translate-y-[-2px] transition-all duration-300">
            <div class="text-rosepink text-xl mb-3"><i class="fa-regular fa-face-smile"></i></div>
            <h3 class="text-white font-serif text-lg font-medium mb-2">Your Smile</h3>
            <p class="text-mutedgray text-sm font-light leading-relaxed">I never realized how much your smile meant until I became the reason it disappeared.</p>
          </div>
          <!-- Card 2 -->
          <div class="glass-card rounded-2xl p-6 hover:border-gold/40 hover:translate-y-[-2px] transition-all duration-300">
            <div class="text-gold text-xl mb-3"><i class="fa-solid fa-shield-halved"></i></div>
            <h3 class="text-white font-serif text-lg font-medium mb-2">Your Trust</h3>
            <p class="text-mutedgray text-sm font-light leading-relaxed">Trust is fragile. I understand now how difficult it is to rebuild, and I am willing to work for it.</p>
          </div>
          <!-- Card 3 -->
          <div class="glass-card rounded-2xl p-6 hover:border-rosepink/40 hover:translate-y-[-2px] transition-all duration-300">
            <div class="text-rosepink text-xl mb-3"><i class="fa-regular fa-heart"></i></div>
            <h3 class="text-white font-serif text-lg font-medium mb-2">Your Love</h3>
            <p class="text-mutedgray text-sm font-light leading-relaxed">You loved me with your whole heart. I should have valued it much more than I showed.</p>
          </div>
          <!-- Card 4 -->
          <div class="glass-card rounded-2xl p-6 hover:border-warmred/40 hover:translate-y-[-2px] transition-all duration-300">
            <div class="text-warmred text-xl mb-3"><i class="fa-solid fa-wand-magic-sparkles"></i></div>
            <h3 class="text-white font-serif text-lg font-medium mb-2">My Mistake</h3>
            <p class="text-mutedgray text-sm font-light leading-relaxed">I wasn't perfect. But I promise to learn, grow, and become the partner you deserve.</p>
          </div>
        </div>

        <button onclick="nextStep(4)" class="px-8 py-4 rounded-full bg-gradient-to-r from-rosepink to-warmred text-white text-sm font-semibold uppercase tracking-wider shadow-[0_4px_20px_rgba(255,95,143,0.3)] hover:scale-[1.05] active:scale-[0.98] transition-all duration-300">
          There's Something I Want You To Remember
        </button>
      </div>
    </div>

    <!-- STEP 4: OUR BEAUTIFUL MEMORIES -->
    <div id="step-4" class="step-container w-full hidden opacity-0">
      <div class="text-center max-w-xl mx-auto">
        <h2 class="font-serif text-3xl md:text-4xl font-semibold mb-8">Our Beautiful Memories</h2>
        
        <!-- Interactive 3D Polaroid Frame -->
        <div id="polaroid" class="polaroid-card bg-[#F4F4F5] p-4 pb-8 rounded shadow-[0_20px_50px_rgba(0,0,0,0.6)] text-black max-w-sm mx-auto mb-8 transform transition-transform duration-300 ease-out cursor-pointer select-none">
          <div class="relative w-full aspect-square bg-[#E4E4E7] overflow-hidden rounded-sm flex flex-col items-center justify-center">
            <!-- Vector Illustration of Starry Skies & Sunset for visual elegance -->
            <svg class="absolute inset-0 w-full h-full object-cover" viewBox="0 0 400 400" fill="none" xmlns="http://www.w3.org/2000/svg">
              <rect width="400" height="400" fill="url(#paint0_linear)"/>
              <circle cx="200" cy="220" r="100" fill="url(#paint1_radial)" opacity="0.8"/>
              <path d="M-50 400C100 320 180 340 450 400Z" fill="#131316"/>
              <path d="M-20 400C120 350 220 370 420 400Z" fill="#201F25" opacity="0.8"/>
              <circle cx="120" cy="110" r="1.5" fill="white"/>
              <circle cx="280" cy="90" r="2" fill="#FFE082"/>
              <circle cx="200" cy="70" r="1.2" fill="white"/>
              <path d="M190 280C190 274.477 194.477 270 200 270C205.523 270 210 274.477 210 280V320H190V280Z" fill="#0A0A0C" opacity="0.9"/>
              <path d="M196 285C197 282 203 282 204 285L200 310Z" fill="#FF4D6D"/>
              <defs>
                <linearGradient id="paint0_linear" x1="200" y1="0" x2="200" y2="400" gradientUnits="userSpaceOnUse">
                  <stop stop-color="#0F1026"/>
                  <stop offset="0.6" stop-color="#3D152F"/>
                  <stop offset="1" stop-color="#FF5F8F"/>
                </linearGradient>
                <radialGradient id="paint1_radial" cx="0" cy="0" r="1" gradientUnits="userSpaceOnUse" gradientTransform="translate(200 220) rotate(90) scale(100)">
                  <stop stop-color="#FFD166"/>
                  <stop offset="1" stop-color="#FFD166" stop-opacity="0"/>
                </radialGradient>
              </defs>
            </svg>
            <span class="absolute text-white/50 text-xs font-light tracking-wide uppercase">Insert Your Favorite Photo Here</span>
          </div>
          <p class="font-serif italic text-lg mt-5 text-zinc-800">Our happiest memory ❤️</p>
        </div>

        <div class="space-y-4 max-w-md mx-auto mb-8">
          <p class="text-mutedgray text-base font-light">Every memory with you is my favorite chapter.</p>
          <p class="text-rosepink font-serif italic text-lg">I don't want our story to end here.</p>
        </div>

        <button onclick="nextStep(5)" class="px-8 py-4 rounded-full bg-transparent border border-white/20 text-white text-sm font-semibold uppercase tracking-wider hover:bg-white/5 hover:border-rosepink/50 hover:scale-[1.05] active:scale-[0.98] transition-all duration-300">
          One More Thing
        </button>
      </div>
    </div>

    <!-- STEP 5: MY PROMISE -->
    <div id="step-5" class="step-container w-full hidden opacity-0">
      <div class="text-center max-w-3xl mx-auto">
        <div class="text-5xl text-rosepink/90 mb-4 drop-shadow-[0_0_15px_rgba(255,95,143,0.3)]">🤝</div>
        <h2 class="font-serif text-3xl md:text-4xl font-semibold mb-8">If You Give Me Another Chance...</h2>

        <!-- Promise Row Grids -->
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 max-w-2xl mx-auto mb-8 text-left">
          <div class="glass-card rounded-2xl p-5 flex items-center gap-4 hover:border-rosepink/30 transition-all duration-300">
            <span class="text-2xl text-rosepink"><i class="fa-regular fa-comments"></i></span>
            <div>
              <p class="font-medium text-white text-sm">I'll listen more</p>
              <p class="text-mutedgray text-xs">To your words, and your silences.</p>
            </div>
          </div>
          <div class="glass-card rounded-2xl p-5 flex items-center gap-4 hover:border-rosepink/30 transition-all duration-300">
            <span class="text-2xl text-gold"><i class="fa-regular fa-heart"></i></span>
            <div>
              <p class="font-medium text-white text-sm">I'll understand you better</p>
              <p class="text-mutedgray text-xs">Putting your feelings before mine.</p>
            </div>
          </div>
          <div class="glass-card rounded-2xl p-5 flex items-center gap-4 hover:border-rosepink/30 transition-all duration-300">
            <span class="text-2xl text-warmred"><i class="fa-solid fa-check-double"></i></span>
            <div>
              <p class="font-medium text-white text-sm">I'll never stop choosing you</p>
              <p class="text-mutedgray text-xs">Through storm and calm, every day.</p>
            </div>
          </div>
          <div class="glass-card rounded-2xl p-5 flex items-center gap-4 hover:border-rosepink/30 transition-all duration-300">
            <span class="text-2xl text-rosepink"><i class="fa-solid fa-sparkles"></i></span>
            <div>
              <p class="font-medium text-white text-sm">I'll love you even more</p>
              <p class="text-mutedgray text-xs">Than I did yesterday, always.</p>
            </div>
          </div>
        </div>

        <button onclick="nextStep(6)" class="px-8 py-4 rounded-full bg-gradient-to-r from-rosepink to-warmred text-white text-sm font-semibold uppercase tracking-wider shadow-[0_4px_20px_rgba(255,95,143,0.3)] hover:scale-[1.05] active:scale-[0.98] transition-all duration-300">
          My Final Words
        </button>
      </div>
    </div>

    <!-- STEP 6: HEARTFELT LETTER -->
    <div id="step-6" class="step-container w-full hidden opacity-0">
      <div class="glass-card rounded-3xl p-8 md:p-12 max-w-xl mx-auto border border-white/10 relative overflow-hidden">
        <div class="absolute -top-10 -right-10 w-32 h-32 bg-rosepink/10 rounded-full filter blur-xl"></div>
        <div class="font-serif text-lg text-rosepink italic mb-4">My Love,</div>
        
        <!-- Elegant sequential typed elements -->
        <div id="letter-content" class="space-y-4 text-mutedgray text-sm md:text-base font-light leading-relaxed mb-8 text-left">
          <p class="letter-line opacity-0">I'm not asking you to forget everything.</p>
          <p class="letter-line opacity-0">I'm only asking for a chance to make tomorrow better than yesterday.</p>
          <p class="letter-line opacity-0">I know apologies don't erase pain. But I hope my actions can slowly heal it.</p>
          <p class="letter-line opacity-0">You mean more to me than words can explain.</p>
          <p class="letter-line opacity-0 font-medium text-white">If I could choose again, I'd still choose you. Every single time.</p>
        </div>

        <div class="text-center">
          <button onclick="nextStep(7)" class="px-8 py-4 rounded-full bg-transparent border border-white/20 text-white text-sm font-semibold uppercase tracking-wider hover:bg-white/5 hover:border-rosepink/50 hover:scale-[1.05] active:scale-[0.98] transition-all duration-300">
            Final Surprise ❤️
          </button>
        </div>
      </div>
    </div>

    <!-- STEP 7: FINAL PROPOSAL -->
    <div id="step-7" class="step-container w-full hidden opacity-0">
      <div class="glass-card rounded-3xl p-8 md:p-12 text-center max-w-xl mx-auto">
        <div class="pulse-heart text-7xl md:text-8xl mb-8 select-none">❤️</div>
        <h2 class="font-serif text-3xl md:text-4xl font-semibold mb-6">Can We Start Again?</h2>
        <div class="space-y-4 text-mutedgray text-sm md:text-base font-light leading-relaxed max-w-md mx-auto mb-10">
          <p>I don't expect everything to become perfect overnight.</p>
          <p>I simply hope we can take one small step toward us again.</p>
          <p class="text-warmred/90 font-medium">Because losing you is the biggest fear I've ever known.</p>
        </div>

        <!-- Heart glowing action button -->
        <button id="forgive-btn" onclick="startGrandFinale()" class="px-10 py-5 rounded-full bg-gradient-to-r from-rosepink via-warmred to-rosepink bg-[length:200%_auto] text-white text-base font-bold uppercase tracking-widest shadow-[0_0_30px_rgba(255,77,109,0.5)] hover:shadow-[0_0_50px_rgba(255,77,109,0.9)] hover:scale-[1.08] active:scale-[0.96] transition-all duration-300 animate-[pulse_2s_infinite]">
          ❤️ Forgive Me ❤️
        </button>
      </div>
    </div>

    <!-- GRAND FINALE PAGE (Hidden initially) -->
    <div id="grand-finale" class="w-full hidden opacity-0 text-center">
      <div class="max-w-xl mx-auto space-y-8 py-10">
        <!-- Floating Infinite Heartbeat -->
        <div class="relative inline-block select-none scale-[1.3] mb-6">
          <div class="pulse-heart text-8xl">💖</div>
          <div class="absolute inset-0 bg-rosepink/20 rounded-full filter blur-xl scale-125 pointer-events-none"></div>
        </div>

        <h1 class="font-serif text-4xl md:text-6xl font-bold tracking-wide text-white drop-shadow-[0_0_30px_rgba(255,95,143,0.8)]">
          I Love You Forever ❤️
        </h1>
        
        <div class="space-y-4 text-mutedgray text-base md:text-lg font-light leading-relaxed">
          <p class="finale-text opacity-0">Thank you for reading everything.</p>
          <p class="finale-text opacity-0 text-rosepink font-medium">No matter what happens,</p>
          <p class="finale-text opacity-0 italic">You'll always have a special place in my heart.</p>
        </div>

        <div class="w-24 h-[1px] bg-white/20 mx-auto my-6"></div>

        <div class="finale-text opacity-0 flex justify-center items-center gap-2 text-xs uppercase tracking-widest text-white/40">
          <span class="inline-block w-2 h-2 rounded-full bg-green-500 animate-pulse"></span>
          Connected Forever
        </div>
      </div>
    </div>

  </main>

  <!-- Global Footer -->
  <footer class="relative z-10 w-full text-center py-6 text-white/30 text-xs tracking-wider select-none">
    Made with love, sincere regret, and hope.
  </footer>

  <script>
    // --- CANVAS VISUAL ENGINE (Bokeh, Floating Hearts, Shooting Stars) ---
    const canvas = document.getElementById('bg-canvas');
    const ctx = canvas.getContext('2d');
    
    let particles = [];
    let shootingStars = [];
    let width = (canvas.width = window.innerWidth);
    let height = (canvas.height = window.innerHeight);

    window.addEventListener('resize', () => {
      width = canvas.width = window.innerWidth;
      height = canvas.height = window.innerHeight;
    });

    // Particle Classes
    class FloatingParticle {
      constructor() {
        this.reset();
        this.y = Math.random() * height;
      }
      reset() {
        this.x = Math.random() * width;
        this.y = height + 50;
        this.size = Math.random() * 14 + 6;
        this.speedY = -(Math.random() * 0.4 + 0.2);
        this.speedX = Math.sin(Math.random() * 5) * 0.2;
        this.opacity = Math.random() * 0.35 + 0.15;
        this.type = Math.random() > 0.4 ? 'bokeh' : 'heart';
        this.color = Math.random() > 0.5 ? '#FF5F8F' : '#FFFFFF';
        this.rot = Math.random() * 360;
        this.rotSpeed = (Math.random() - 0.5) * 0.5;
      }
      update() {
        this.y += this.speedY;
        this.x += this.speedX;
        this.rot += this.rotSpeed;
        if (this.y < -50) this.reset();
      }
      draw() {
        ctx.save();
        ctx.globalAlpha = this.opacity;
        ctx.translate(this.x, this.y);
        
        if (this.type === 'bokeh') {
          // Large blurred bokeh light
          ctx.beginPath();
          ctx.arc(0, 0, this.size * 2, 0, Math.PI * 2);
          ctx.fillStyle = this.color;
          ctx.shadowBlur = 15;
          ctx.shadowColor = this.color;
          ctx.fill();
        } else {
          // Soft heart vector draw
          ctx.rotate((this.rot * Math.PI) / 180);
          ctx.beginPath();
          const d = this.size;
          ctx.moveTo(0, d / 4);
          ctx.quadraticCurveTo(0, 0, d / 2, 0);
          ctx.quadraticCurveTo(d, 0, d, d / 4);
          ctx.quadraticCurveTo(d, (d * 3) / 4, d / 2, d);
          ctx.quadraticCurveTo(0, (d * 3) / 4, 0, d / 4);
          ctx.fillStyle = this.color;
          ctx.shadowBlur = 10;
          ctx.shadowColor = this.color;
          ctx.fill();
        }
        ctx.restore();
      }
    }

    class ShootingStar {
      constructor() {
        this.reset();
      }
      reset() {
        this.x = Math.random() * width * 0.7;
        this.y = Math.random() * height * 0.3;
        this.length = Math.random() * 80 + 50;
        this.speed = Math.random() * 6 + 4;
        this.opacity = 1;
        this.angle = Math.PI / 4; // Diagonal downwards
      }
      update() {
        this.x += Math.cos(this.angle) * this.speed;
        this.y += Math.sin(this.angle) * this.speed;
        this.opacity -= 0.015;
        if (this.opacity <= 0) {
          this.reset();
          return false;
        }
        return true;
      }
      draw() {
        ctx.save();
        ctx.strokeStyle = `rgba(255, 209, 102, ${this.opacity})`;
        ctx.lineWidth = 1.5;
        ctx.beginPath();
        ctx.moveTo(this.x, this.y);
        ctx.lineTo(this.x - Math.cos(this.angle) * this.length, this.y - Math.sin(this.angle) * this.length);
        ctx.shadowBlur = 10;
        ctx.shadowColor = '#FFD166';
        ctx.stroke();
        ctx.restore();
      }
    }

    // Initialize 40 ambient floating particles
    for (let i = 0; i < 40; i++) {
      particles.push(new FloatingParticle());
    }

    // Occasional shooting star execution (8-12 seconds)
    function spawnStar() {
      shootingStars.push(new ShootingStar());
      setTimeout(spawnStar, Math.random() * 4000 + 8000);
    }
    setTimeout(spawnStar, 3000);

    // Canvas Loop
    function render() {
      ctx.clearRect(0, 0, width, height);
      
      particles.forEach((p) => {
        p.update();
        p.draw();
      });

      shootingStars = shootingStars.filter((star) => {
        const alive = star.update();
        if (alive) star.draw();
        return alive;
      });

      requestAnimationFrame(render);
    }
    render();


    // --- 3D POLAROID TILT ENGINE ---
    const polaroid = document.getElementById('polaroid');
    if(polaroid) {
      polaroid.addEventListener('mousemove', (e) => {
        const rect = polaroid.getBoundingClientRect();
        const x = e.clientX - rect.left - rect.width / 2;
        const y = e.clientY - rect.top - rect.height / 2;
        
        // 3D rotation limits based on coordinates
        const rotX = -y / 10;
        const rotY = x / 10;
        
        gsap.to(polaroid, {
          rotateX: rotX,
          rotateY: rotY,
          transformPerspective: 1000,
          ease: 'power2.out',
          duration: 0.3
        });
      });

      polaroid.addEventListener('mouseleave', () => {
        gsap.to(polaroid, {
          rotateX: 0,
          rotateY: 0,
          transformPerspective: 1000,
          ease: 'power2.out',
          duration: 0.6
        });
      });
    }


    // --- PROGRESSIVE STEP CONTROLLER ---
    let currentStep = 1;
    const totalSteps = 7;

    function updateProgress(step) {
      const percentage = (step / totalSteps) * 100;
      const progressIndicator = document.getElementById('progress-indicator');
      if (progressIndicator) {
        progressIndicator.style.width = `${percentage}%`;
      }
    }

    function nextStep(step) {
      const activeDiv = document.getElementById(`step-${currentStep}`);
      const nextDiv = document.getElementById(`step-${step}`);
      
      if (!activeDiv || !nextDiv) return;

      // Handle music triggers on active click events
      if (currentStep === 1 && !isPlaying) {
        // Start synthesized track safely upon user interaction
        toggleMusic();
      }

      // GSAP Transitions: Outward zoom and fade transition out
      gsap.to(activeDiv, {
        opacity: 0,
        scale: 0.95,
        duration: 0.5,
        ease: 'power2.inOut',
        onComplete: () => {
          activeDiv.classList.add('hidden');
          nextDiv.classList.remove('hidden');
          
          // GSAP Transitions: Inward zoom and fade transition in
          gsap.fromTo(nextDiv, 
            { opacity: 0, scale: 1.05 },
            { opacity: 1, scale: 1, duration: 0.6, ease: 'power2.out' }
          );

          // Custom step activation trigger sequences
          if (step === 2) {
            gsap.fromTo('.stagger-txt', 
              { opacity: 0, y: 15 },
              { opacity: 1, y: 0, stagger: 0.25, duration: 0.6, ease: 'power2.out' }
            );
          } else if (step === 6) {
            gsap.fromTo('.letter-line', 
              { opacity: 0, y: 10 },
              { opacity: 1, y: 0, stagger: 1.5, duration: 1.0, ease: 'power2.out' }
            );
          }

          currentStep = step;
          updateProgress(currentStep);
        }
      });
    }


    // --- WEB AUDIO API PROCEDURAL MUSIC ENGINE ---
    let audioCtx = null;
    let delayNode = null;
    let musicInterval = null;
    let isPlaying = false;
    let activeOscillators = [];

    function initAudio() {
      if (audioCtx) return;
      audioCtx = new (window.AudioContext || window.webkitAudioContext)();
      
      // Delay system creates beautiful ambient echo effects
      delayNode = audioCtx.createDelay(5.0);
      const feedback = audioCtx.createGain();
      const delayFilter = audioCtx.createBiquadFilter();
      
      delayNode.delayTime.value = 0.6;
      feedback.gain.value = 0.35;
      delayFilter.frequency.value = 800; // Limits harsh high notes in loop echo
      
      delayNode.connect(feedback);
      feedback.connect(delayFilter);
      delayFilter.connect(delayNode);
      delayNode.connect(audioCtx.destination);
    }

    // Play individual soft synth keys imitating an ambient Rhodes electric piano
    function playSoftNote(freq, startTime, duration) {
      if (!audioCtx) return;
      
      const osc = audioCtx.createOscillator();
      const gain = audioCtx.createGain();
      const filter = audioCtx.createBiquadFilter();
      
      osc.type = 'triangle'; // Smooth base sound waves
      osc.frequency.setValueAtTime(freq, startTime);
      
      filter.type = 'lowpass';
      filter.frequency.setValueAtTime(200, startTime);
      filter.frequency.exponentialRampToValueAtTime(1000, startTime + 0.15);
      filter.frequency.exponentialRampToValueAtTime(250, startTime + duration);
      
      gain.gain.setValueAtTime(0, startTime);
      gain.gain.linearRampToValueAtTime(0.12, startTime + 0.1); // Gradual smooth key attack
      gain.gain.exponentialRampToValueAtTime(0.001, startTime + duration); // Emotional ringing delay
      
      osc.connect(filter);
      filter.connect(gain);
      gain.connect(audioCtx.destination);
      if (delayNode) {
        gain.connect(delayNode);
      }
      
      osc.start(startTime);
      osc.stop(startTime + duration + 1.0);
      activeOscillators.push(osc);
    }

    // Procedural Romantic ambient chord progressions (Frequencies in Hertz)
    const chords = [
      // Fmaj7
      [87.31, 130.81, 220.00, 329.63, 392.00], 
      // Cmaj7
      [130.81, 196.00, 246.94, 329.63, 493.88],
      // Am9
      [110.00, 164.81, 261.63, 329.63, 493.88],
      // G6/E
      [82.41, 146.83, 196.00, 293.66, 392.00]
    ];
    let currentChordIndex = 0;

    function playLoopStep() {
      const chord = chords[currentChordIndex];
      const now = audioCtx.currentTime;
      
      // Gently arpeggiate notes in chord list
      chord.forEach((freq, idx) => {
        const noteDelay = idx * 0.35 + (Math.random() * 0.05); // Organic acoustic latency
        playSoftNote(freq, now + noteDelay, 4.5);
      });

      currentChordIndex = (currentChordIndex + 1) % chords.length;
    }

    function toggleMusic() {
      initAudio();

      if (!isPlaying) {
        // Handle browser autoplay policy restrictions
        if (audioCtx.state === 'suspended') {
          audioCtx.resume();
        }
        
        // Immediately trigger and queue subsequent sequences
        playLoopStep();
        musicInterval = setInterval(playLoopStep, 5000);
        
        isPlaying = true;
        document.getElementById('music-text').textContent = "Mute Music";
        document.getElementById('eq-container').classList.remove('hidden');
        document.getElementById('mute-icon').classList.add('hidden');
      } else {
        clearInterval(musicInterval);
        isPlaying = false;
        document.getElementById('music-text').textContent = "Play Soft Music";
        document.getElementById('eq-container').classList.add('hidden');
        document.getElementById('mute-icon').classList.remove('hidden');
      }
    }


    // --- GRAND FINALE TRIGGER ---
    function startGrandFinale() {
      const finalProposalDiv = document.getElementById('step-7');
      const grandFinaleDiv = document.getElementById('grand-finale');
      const progressContainer = document.getElementById('progress-indicator').parentNode;
      
      if (!finalProposalDiv || !grandFinaleDiv) return;

      // Clean transition away from current interactive container
      gsap.to(finalProposalDiv, {
        opacity: 0,
        scale: 0.9,
        duration: 0.8,
        ease: 'power3.inOut',
        onComplete: () => {
          finalProposalDiv.classList.add('hidden');
          grandFinaleDiv.classList.remove('hidden');
          
          // Gently obscure fixed utility visuals to maximize immersive scope
          if(progressContainer) progressContainer.classList.add('hidden');

          // Darken canvas/aurora parameters slightly to isolate visual highlights
          gsap.to('.aurora-bg', {
            background: '#040406',
            duration: 2.0
          });

          // Music swells (gains a bit of volume and density)
          if (audioCtx && isPlaying) {
            // Trigger rapid beautiful high note flutters as a musical climax
            const finalHarmonies = [523.25, 587.33, 659.25, 783.99, 987.77];
            const now = audioCtx.currentTime;
            finalHarmonies.forEach((freq, idx) => {
              playSoftNote(freq, now + (idx * 0.25), 6.0);
            });
          }

          // Trigger Confetti explosion: Deep warm pink / gold colors
          const end = Date.now() + (3 * 1000);
          const colors = ['#FF5F8F', '#FF4D6D', '#FFD166', '#FFFFFF'];

          (function frame() {
            confetti({
              particleCount: 3,
              angle: 60,
              spread: 55,
              origin: { x: 0 },
              colors: colors
            });
            confetti({
              particleCount: 3,
              angle: 120,
              spread: 55,
              origin: { x: 1 },
              colors: colors
            });

            if (Date.now() < end) {
              requestAnimationFrame(frame);
            }
          }());

          // Increment custom screen canvas particle density for heart swirls
          for (let i = 0; i < 60; i++) {
            const extraPart = new FloatingParticle();
            extraPart.speedY = -(Math.random() * 2 + 1); // Swifter upward ascent speed
            extraPart.opacity = Math.random() * 0.6 + 0.3; // Brighter presence
            particles.push(extraPart);
          }

          // GSAP Reveal Sequence for Final Emotional Frame Elements
          gsap.fromTo(grandFinaleDiv,
            { opacity: 0, scale: 1.1 },
            { opacity: 1, scale: 1, duration: 2.0, ease: 'power4.out' }
          );

          gsap.fromTo('.finale-text',
            { opacity: 0, y: 20 },
            { opacity: 1, y: 0, stagger: 1.0, duration: 1.5, ease: 'power3.out', delay: 1.0 }
          );
        }
      });
    }
  </script>
</body>
</html>
