<!doctype html>
<html lang="en" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Alpha0x - Privacy-First Agent AI</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&amp;family=JetBrains+Mono:wght@400;600&amp;family=Inter:wght@300;400;500;600&amp;display=swap" rel="stylesheet">
  <style>
    body {
      box-sizing: border-box;
    }
    
    .font-display {
      font-family: 'Orbitron', sans-serif;
    }
    
    .font-mono {
      font-family: 'JetBrains Mono', monospace;
    }
    
    .font-body {
      font-family: 'Inter', sans-serif;
    }
    
    @keyframes shimmer {
      0% { background-position: -200% 0; }
      100% { background-position: 200% 0; }
    }
    
    .shimmer-text {
      background: linear-gradient(90deg, #ffffff 0%, #60a5fa 25%, #ffffff 50%, #60a5fa 75%, #ffffff 100%);
      background-size: 200% auto;
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      animation: shimmer 3s linear infinite;
    }
    
    @keyframes slide-up {
      from {
        opacity: 0;
        transform: translateY(40px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    
    .stagger-animation {
      animation: slide-up 0.8s ease-out forwards;
      opacity: 0;
    }
    
    .stagger-1 { animation-delay: 0.1s; }
    .stagger-2 { animation-delay: 0.2s; }
    .stagger-3 { animation-delay: 0.3s; }
    .stagger-4 { animation-delay: 0.4s; }
    .stagger-5 { animation-delay: 0.5s; }
    
    @keyframes electric-icon-pulse {
      0%, 100% { 
        filter: drop-shadow(0 0 8px rgba(59, 130, 246, 0.4));
      }
      50% { 
        filter: drop-shadow(0 0 20px rgba(96, 165, 250, 0.8)) drop-shadow(0 0 10px rgba(59, 130, 246, 0.6));
      }
    }
    
    .electric-icon {
      animation: electric-icon-pulse 2.5s ease-in-out infinite;
    }
    
    .group:hover .electric-icon {
      animation: electric-icon-pulse 1.5s ease-in-out infinite;
      filter: drop-shadow(0 0 15px rgba(59, 130, 246, 0.7));
    }
    
    @keyframes typewriter {
      from {
        width: 0;
      }
      to {
        width: 100%;
      }
    }
    
    .terminal-line {
      overflow: hidden;
      white-space: nowrap;
      animation: typewriter 0.03s steps(1000, end) forwards;
    }
    
    @keyframes grid-drift {
      0% { transform: translateY(0px) translateX(0px); }
      100% { transform: translateY(-100px) translateX(0px); }
    }
    
    @keyframes glitch-horizontal {
      0%, 19%, 21%, 23%, 25%, 54%, 56%, 100% {
        text-shadow: -2px 0 #ff00ff, 2px 0 #00ffff;
      }
      20%, 24%, 55% {
        text-shadow: 2px 0 #ff00ff, -2px 0 #00ffff;
      }
    }
    
    @keyframes glitch-skew {
      0% { transform: skew(0deg); }
      10% { transform: skew(10deg); }
      20% { transform: skew(-5deg); }
      30% { transform: skew(0deg); }
      100% { transform: skew(0deg); }
    }
    
    @keyframes neon-flare {
      0%, 100% { filter: drop-shadow(0 0 10px rgba(0, 255, 255, 0.6)) drop-shadow(0 0 20px rgba(255, 0, 255, 0.3)); }
      50% { filter: drop-shadow(0 0 20px rgba(0, 255, 255, 0.9)) drop-shadow(0 0 40px rgba(255, 0, 255, 0.6)); }
    }
    
    @keyframes pulse-neon {
      0%, 100% { filter: drop-shadow(0 0 5px rgba(0, 255, 255, 0.5)); }
      50% { filter: drop-shadow(0 0 30px rgba(0, 255, 255, 1)) drop-shadow(0 0 50px rgba(255, 0, 255, 0.8)); }
    }
    
    .cyberpunk-grid {
      position: absolute;
      inset: 0;
      background-image: 
        linear-gradient(rgba(0, 255, 255, 0.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(0, 255, 255, 0.03) 1px, transparent 1px);
      background-size: 50px 50px;
      animation: grid-drift 8s linear infinite;
    }
    
    .cyberpunk-grid::before {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(
        180deg,
        rgba(0, 255, 255, 0) 0%,
        rgba(0, 255, 255, 0.1) 50%,
        rgba(0, 255, 255, 0) 100%
      );
      animation: grid-drift 12s linear infinite reverse;
    }
    
    .hero-glitch {
      position: relative;
      animation: glitch-horizontal 4s infinite;
    }
    
    .hero-glitch::before {
      content: attr(data-text);
      position: absolute;
      left: 0;
      top: 0;
      z-index: -1;
      color: #ff00ff;
      opacity: 0.8;
      animation: glitch-skew 2s infinite;
    }
    
    .hero-glitch::after {
      content: attr(data-text);
      position: absolute;
      left: 0;
      top: 0;
      z-index: -2;
      color: #00ffff;
      opacity: 0.6;
      animation: glitch-skew 2s infinite reverse;
    }
    
    .neon-glow {
      animation: pulse-neon 3s ease-in-out infinite;
    }
    
    @keyframes flicker {
      0% { opacity: 0; }
      10% { opacity: 0; }
      15% { opacity: 1; }
      20% { opacity: 0.8; }
      25% { opacity: 1; }
      30% { opacity: 0.7; }
      35% { opacity: 1; }
      40% { opacity: 0.9; }
      45% { opacity: 1; }
      100% { opacity: 1; }
    }
    
    .speech-bubble-line {
      display: block;
      animation: flicker 2s ease-in-out 3s infinite;
      opacity: 0;
    }
    
    .speech-bubble-line:first-child {
      animation-delay: 3s;
    }
    
    .speech-bubble-line:last-child {
      animation-delay: 5.1s;
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full font-body">
  <div id="app-wrapper" class="w-full h-full overflow-auto"><!-- Background -->
   <div class="fixed inset-0 w-full h-full -z-10 bg-cover bg-center" style="background-image: url('https://imgur.com/7571Pes.png'); background-attachment: fixed;"></div>
   <div class="fixed inset-0 w-full h-full -z-10 bg-black/85"></div><!-- Main Content -->
   <div class="relative min-h-full"><!-- Navigation -->
    <nav class="flex items-center justify-between px-6 md:px-12 py-6">
     <div class="flex items-center gap-4"><img src="https://imgur.com/mJ6Vdvr.png" alt="Alpha0x Logo" class="h-10 w-auto electric-icon" loading="lazy" onerror="console.error('Logo failed:', this.src);">
      <div class="hidden md:flex bg-gradient-to-br from-cyan-500/20 to-blue-500/20 border border-cyan-400/50 rounded-lg px-3 py-2 backdrop-blur-sm shadow-lg shadow-cyan-500/20">
       <div class="text-white font-mono text-xs leading-tight">
        <div class="speech-bubble-line">
         <span class="text-cyan-400">&gt;</span> <span class="text-green-400">Hi!</span> I'm <span class="text-cyan-400">Claw0x</span>
        </div>
        <div class="speech-bubble-line">
         <span class="text-cyan-400">&gt;</span> Your <span class="text-green-400">agent</span> <span class="text-cyan-400">AI</span>
        </div>
       </div>
      </div>
     </div>
     <div class="hidden md:flex items-center gap-8 text-gray-400 text-sm"><a href="#about" class="hover:text-blue-400 transition-colors">About</a> <a href="#features" class="hover:text-blue-400 transition-colors">Features</a> <a href="#roadmap" class="hover:text-blue-400 transition-colors">Roadmap</a> <a href="#faq" class="hover:text-blue-400 transition-colors">FAQ</a> <a href="#connect" class="hover:text-blue-400 transition-colors">Community</a>
     </div>
    </nav><!-- Hero Section -->
    <section id="about" class="px-6 md:px-12 py-16 md:py-24 relative overflow-hidden">
     <div class="absolute inset-0 overflow-hidden pointer-events-none">
      <div class="cyberpunk-grid"></div>
      <div class="absolute inset-0 bg-gradient-to-b from-cyan-500/5 via-transparent to-purple-500/5"></div>
      <div class="absolute top-1/4 left-1/4 w-96 h-96 bg-cyan-500/10 rounded-full blur-3xl animate-pulse" style="animation-duration: 4s;"></div>
      <div class="absolute bottom-1/4 right-1/4 w-96 h-96 bg-purple-500/10 rounded-full blur-3xl animate-pulse" style="animation-delay: 2s; animation-duration: 4s;"></div>
      <div class="absolute top-1/2 right-1/3 w-64 h-64 border border-cyan-400/20 rounded-lg rotate-45 animate-pulse" style="animation-duration: 6s;"></div>
     </div>
     <div class="text-center max-w-5xl mx-auto relative z-10">
      <h1 id="hero-title" class="font-display font-black text-5xl md:text-6xl lg:text-7xl text-white mb-4 leading-tight stagger-animation stagger-1 tracking-tight neon-glow hero-glitch" data-text="CLAW0X">CLAW0X</h1>
      <p class="stagger-animation stagger-2 text-3xl md:text-5xl lg:text-6xl tracking-widest mb-2"><span class="shimmer-text font-display font-black">CLAW0X</span></p>
      <p class="text-cyan-400 font-mono text-sm md:text-base tracking-widest mb-8 stagger-animation stagger-3">POWERED BY ALPHA0X</p>
      <p id="hero-subtitle" class="font-mono text-gray-300 font-medium text-lg md:text-xl leading-relaxed mb-8 stagger-animation stagger-3 max-w-3xl mx-auto">Meet Claw0x, the official mascot of Alpha0x, a digital guardian forged at the intersection of privacy-first technology and Agent AI. Alpha0x integrates these innovations to deliver autonomous monitoring and market intelligence directly within DApps. It tracks target wallets, detects new launches, analyzes volume and trends, and evaluates market sentiment—all while ensuring transactions and signals remain fully encrypted and confidential.</p>
     </div>
    </section><!-- Key Features Section -->
    <section id="features" class="px-6 md:px-12 py-16 md:py-24">
     <div class="max-w-6xl mx-auto">
      <div class="text-center mb-20">
       <h2 class="font-display font-bold text-3xl md:text-4xl mb-4"><span class="shimmer-text">Key Features</span></h2>
       <p class="text-gray-400 text-lg">Powerful capabilities for privacy-first AI</p>
      </div>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8"><!-- Feature 1 -->
       <div class="group stagger-animation stagger-1">
        <div class="relative h-full p-8 border-l-4 border-blue-500 hover:border-l-8 transition-all duration-300 bg-gradient-to-br from-blue-500/5 to-cyan-500/5 hover:from-blue-500/15 hover:to-cyan-500/15 pl-6 rounded-lg overflow-hidden">
         <div class="absolute left-0 top-0 w-1 h-0 bg-gradient-to-b from-blue-400 to-transparent group-hover:h-full transition-all duration-500"></div>
         <div class="relative z-10 flex flex-col h-full">
          <div class="w-10 h-10 rounded-full border-2 border-blue-400 flex items-center justify-center text-blue-300 font-display font-bold text-sm mb-4 group-hover:bg-blue-500/30 group-hover:border-blue-300 group-hover:scale-110 transition-all duration-300 shadow-lg shadow-blue-500/20">
           01
          </div>
          <h3 id="feature-1-title" class="font-display font-bold text-xl text-white mb-3 group-hover:text-blue-200 transition-colors duration-300">Zero-Knowledge Proofs</h3>
          <p class="text-gray-400 text-sm leading-relaxed flex-grow group-hover:text-gray-300 transition-colors duration-300">Agents verify events without revealing private data. Advanced cryptographic protocols ensure complete confidentiality.</p>
         </div>
        </div>
       </div><!-- Feature 2 -->
       <div class="group stagger-animation stagger-2">
        <div class="relative h-full p-8 border-l-4 border-cyan-500 hover:border-l-8 transition-all duration-300 bg-gradient-to-br from-cyan-500/5 to-teal-500/5 hover:from-cyan-500/15 hover:to-teal-500/15 pl-6 rounded-lg overflow-hidden">
         <div class="absolute left-0 top-0 w-1 h-0 bg-gradient-to-b from-cyan-400 to-transparent group-hover:h-full transition-all duration-500"></div>
         <div class="relative z-10 flex flex-col h-full">
          <div class="w-10 h-10 rounded-full border-2 border-cyan-400 flex items-center justify-center text-cyan-300 font-display font-bold text-sm mb-4 group-hover:bg-cyan-500/30 group-hover:border-cyan-300 group-hover:scale-110 transition-all duration-300 shadow-lg shadow-cyan-500/20">
           02
          </div>
          <h3 id="feature-2-title" class="font-display font-bold text-xl text-white mb-3 group-hover:text-cyan-200 transition-colors duration-300">Encrypted Workflows</h3>
          <p class="text-gray-400 text-sm leading-relaxed flex-grow group-hover:text-gray-300 transition-colors duration-300">End-to-end encryption for all transactions and communications. Military-grade security protects every interaction.</p>
         </div>
        </div>
       </div><!-- Feature 3 -->
       <div class="group stagger-animation stagger-3">
        <div class="relative h-full p-8 border-l-4 border-purple-500 hover:border-l-8 transition-all duration-300 bg-gradient-to-br from-purple-500/5 to-pink-500/5 hover:from-purple-500/15 hover:to-pink-500/15 pl-6 rounded-lg overflow-hidden">
         <div class="absolute left-0 top-0 w-1 h-0 bg-gradient-to-b from-purple-400 to-transparent group-hover:h-full transition-all duration-500"></div>
         <div class="relative z-10 flex flex-col h-full">
          <div class="w-10 h-10 rounded-full border-2 border-purple-400 flex items-center justify-center text-purple-300 font-display font-bold text-sm mb-4 group-hover:bg-purple-500/30 group-hover:border-purple-300 group-hover:scale-110 transition-all duration-300 shadow-lg shadow-purple-500/20">
           03
          </div>
          <h3 id="feature-3-title" class="font-display font-bold text-xl text-white mb-3 group-hover:text-purple-200 transition-colors duration-300">Decentralized Execution</h3>
          <p class="text-gray-400 text-sm leading-relaxed flex-grow group-hover:text-gray-300 transition-colors duration-300">Agents operate autonomously inside DApps with no central authority. True decentralization meets intelligent automation.</p>
         </div>
        </div>
       </div><!-- Feature 4 -->
       <div class="group stagger-animation stagger-4">
        <div class="relative h-full p-8 border-l-4 border-indigo-500 hover:border-l-8 transition-all duration-300 bg-gradient-to-br from-indigo-500/5 to-blue-500/5 hover:from-indigo-500/15 hover:to-blue-500/15 pl-6 rounded-lg overflow-hidden">
         <div class="absolute left-0 top-0 w-1 h-0 bg-gradient-to-b from-indigo-400 to-transparent group-hover:h-full transition-all duration-500"></div>
         <div class="relative z-10 flex flex-col h-full">
          <div class="w-10 h-10 rounded-full border-2 border-indigo-400 flex items-center justify-center text-indigo-300 font-display font-bold text-sm mb-4 group-hover:bg-indigo-500/30 group-hover:border-indigo-300 group-hover:scale-110 transition-all duration-300 shadow-lg shadow-indigo-500/20">
           04
          </div>
          <h3 id="feature-4-title" class="font-display font-bold text-xl text-white mb-3 group-hover:text-indigo-200 transition-colors duration-300">Confidential Insights</h3>
          <p class="text-gray-400 text-sm leading-relaxed flex-grow group-hover:text-gray-300 transition-colors duration-300">Market intelligence stays hidden from competitors. Access real-time data without exposing your strategies.</p>
         </div>
        </div>
       </div><!-- Feature 5 -->
       <div class="group stagger-animation stagger-5">
        <div class="relative h-full p-8 border-l-4 border-green-500 hover:border-l-8 transition-all duration-300 bg-gradient-to-br from-green-500/5 to-emerald-500/5 hover:from-green-500/15 hover:to-emerald-500/15 pl-6 rounded-lg overflow-hidden">
         <div class="absolute left-0 top-0 w-1 h-0 bg-gradient-to-b from-green-400 to-transparent group-hover:h-full transition-all duration-500"></div>
         <div class="relative z-10 flex flex-col h-full">
          <div class="w-10 h-10 rounded-full border-2 border-green-400 flex items-center justify-center text-green-300 font-display font-bold text-sm mb-4 group-hover:bg-green-500/30 group-hover:border-green-300 group-hover:scale-110 transition-all duration-300 shadow-lg shadow-green-500/20">
           05
          </div>
          <h3 id="feature-5-title" class="font-display font-bold text-xl text-white mb-3 group-hover:text-green-200 transition-colors duration-300">Adaptive Security</h3>
          <p class="text-gray-400 text-sm leading-relaxed flex-grow group-hover:text-gray-300 transition-colors duration-300">AI continuously evolves to counter emerging threats. Dynamic defense mechanisms adapt in real-time.</p>
         </div>
        </div>
       </div>
      </div>
     </div>
    </section><!-- Roadmap Section -->
    <section id="roadmap" class="px-6 md:px-12 py-16 md:py-24">
     <div class="max-w-5xl mx-auto">
      <div class="text-center mb-20">
       <h2 class="font-display font-bold text-3xl md:text-4xl mb-4"><span class="shimmer-text">Roadmap &amp; FAQs</span></h2>
       <p class="text-gray-400 text-lg">Our development path and answers to common questions</p>
      </div>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-12"><!-- Roadmap -->
       <div>
        <h3 class="font-display font-bold text-2xl text-white mb-8">Development Timeline</h3>
        <div class="space-y-6"><!-- Phase 1 -->
         <div class="relative pl-8 border-l-2 border-blue-500 stagger-animation stagger-1">
          <div class="absolute -left-3 top-0 w-6 h-6 rounded-full bg-blue-500 border-4 border-black"></div>
          <div>
           <h4 class="font-display font-bold text-lg text-white mb-2">Phase 1: Community Gathering</h4>
           <p class="text-gray-400 text-sm mb-3">Launch community gathering and social media presence. Build foundation for ecosystem engagement and brand awareness across crypto communities.</p>
           <div class="flex flex-wrap gap-2"><span class="text-xs bg-blue-500/20 border border-blue-400/50 text-blue-300 px-3 py-1 rounded-full">Social Media</span> <span class="text-xs bg-blue-500/20 border border-blue-400/50 text-blue-300 px-3 py-1 rounded-full">Community</span> <span class="text-xs bg-blue-500/20 border border-blue-400/50 text-blue-300 px-3 py-1 rounded-full">Engagement</span>
           </div>
          </div>
         </div><!-- Phase 2 -->
         <div class="relative pl-8 border-l-2 border-cyan-500 stagger-animation stagger-2">
          <div class="absolute -left-3 top-0 w-6 h-6 rounded-full bg-cyan-500 border-4 border-black"></div>
          <div>
           <h4 class="font-display font-bold text-lg text-white mb-2">Phase 2: Token Launch &amp; Growth</h4>
           <p class="text-gray-400 text-sm mb-3">Launch official Alpha0x token. Initiate community growth and marketing campaigns. Begin Claw0x character development and integration into ecosystem.</p>
           <div class="flex flex-wrap gap-2"><span class="text-xs bg-cyan-500/20 border border-cyan-400/50 text-cyan-300 px-3 py-1 rounded-full">Token Launch</span> <span class="text-xs bg-cyan-500/20 border border-cyan-400/50 text-cyan-300 px-3 py-1 rounded-full">Community Growth</span> <span class="text-xs bg-cyan-500/20 border border-cyan-400/50 text-cyan-300 px-3 py-1 rounded-full">Claw0x Dev</span>
           </div>
          </div>
         </div><!-- Phase 3 -->
         <div class="relative pl-8 border-l-2 border-purple-500 stagger-animation stagger-3">
          <div class="absolute -left-3 top-0 w-6 h-6 rounded-full bg-purple-500 border-4 border-black"></div>
          <div>
           <h4 class="font-display font-bold text-lg text-white mb-2">Phase 3: Optimization</h4>
           <p class="text-gray-400 text-sm mb-3">Deploy advanced sentiment analysis. Implement adaptive AI models. Launch community beta program for early adopters.</p>
           <div class="flex flex-wrap gap-2"><span class="text-xs bg-purple-500/20 border border-purple-400/50 text-purple-300 px-3 py-1 rounded-full">Sentiment AI</span> <span class="text-xs bg-purple-500/20 border border-purple-400/50 text-purple-300 px-3 py-1 rounded-full">Model Training</span> <span class="text-xs bg-purple-500/20 border border-purple-400/50 text-purple-300 px-3 py-1 rounded-full">Beta Program</span>
           </div>
          </div>
         </div><!-- Phase 4 -->
         <div class="relative pl-8 border-l-2 border-indigo-500 stagger-animation stagger-4">
          <div class="absolute -left-3 top-0 w-6 h-6 rounded-full bg-indigo-500 border-4 border-black"></div>
          <div>
           <h4 class="font-display font-bold text-lg text-white mb-2">Phase 4: Official Release &amp; Development</h4>
           <p class="text-gray-400 text-sm mb-3">Official release of Privacy + Agent AI Technology with continued development. DApps can integrate autonomous agents with privacy guarantees while we iterate on new features and capabilities.</p>
           <div class="flex flex-wrap gap-2"><span class="text-xs bg-indigo-500/20 border border-indigo-400/50 text-indigo-300 px-3 py-1 rounded-full">Official Release</span> <span class="text-xs bg-indigo-500/20 border border-indigo-400/50 text-indigo-300 px-3 py-1 rounded-full">DApp Integration</span> <span class="text-xs bg-indigo-500/20 border border-indigo-400/50 text-indigo-300 px-3 py-1 rounded-full">Continuous Development</span>
           </div>
          </div>
         </div><!-- Phase 5 -->
         <div class="relative pl-8 border-l-2 border-green-500 stagger-animation stagger-5">
          <div class="absolute -left-3 top-0 w-6 h-6 rounded-full bg-green-500 border-4 border-black"></div>
          <div>
           <h4 class="font-display font-bold text-lg text-white mb-2">Phase 5: Updates</h4>
           <p class="text-gray-400 text-sm mb-3">Continuous improvements and expansion. New capabilities, multi-chain support, and ecosystem partnerships.</p>
           <div class="flex flex-wrap gap-2"><span class="text-xs bg-green-500/20 border border-green-400/50 text-green-300 px-3 py-1 rounded-full">New Features</span> <span class="text-xs bg-green-500/20 border border-green-400/50 text-green-300 px-3 py-1 rounded-full">Multi-Chain</span> <span class="text-xs bg-green-500/20 border border-green-400/50 text-green-300 px-3 py-1 rounded-full">Partnerships</span>
           </div>
          </div>
         </div>
        </div>
       </div><!-- FAQ -->
       <div id="faq">
        <h3 class="font-display font-bold text-2xl text-white mb-8">Frequently Asked Questions</h3>
        <div class="space-y-4 flex flex-col">
         <details class="group border border-gray-700/50 rounded-lg p-4 hover:border-blue-400/50 transition-all cursor-pointer stagger-animation stagger-1"><summary class="font-semibold text-white flex justify-between items-center"> What is Claw0x? <span class="text-blue-400 group-open:rotate-180 transition-transform">▼</span> </summary>
          <p class="text-gray-400 text-sm mt-3 leading-relaxed">Claw0x is powered by Alpha0x privacy-first AI infrastructure that integrates autonomous agents with advanced cryptography to deliver market intelligence and wallet monitoring while keeping all transactions and user data fully encrypted and confidential.</p>
         </details>
         <details class="group border border-gray-700/50 rounded-lg p-4 hover:border-blue-400/50 transition-all cursor-pointer stagger-animation stagger-2"><summary class="font-semibold text-white flex justify-between items-center"> How does Privacy + Agent AI work? <span class="text-blue-400 group-open:rotate-180 transition-transform">▼</span> </summary>
          <p class="text-gray-400 text-sm mt-3 leading-relaxed">Your query gets encrypted and wrapped in zero-knowledge proofs. Autonomous agents analyze market data, wallet activity, and sentiment—all within encrypted environments. The agents verify insights cryptographically without ever accessing raw data. Results return to you encrypted and fully confidential. No third party sees your requests, strategies, or intelligence.</p>
         </details>
         <details class="group border border-gray-700/50 rounded-lg p-4 hover:border-blue-400/50 transition-all cursor-pointer stagger-animation stagger-3"><summary class="font-semibold text-white flex justify-between items-center"> When can I start using it? <span class="text-blue-400 group-open:rotate-180 transition-transform">▼</span> </summary>
          <p class="text-gray-400 text-sm mt-3 leading-relaxed">We're launching in phases throughout 2026. Foundation infrastructure launches in Q1, beta testing begins in Q3, and the public mainnet launches in Q4 with full feature support.</p>
         </details>
         <details class="group border border-gray-700/50 rounded-lg p-4 hover:border-blue-400/50 transition-all cursor-pointer stagger-animation stagger-4"><summary class="font-semibold text-white flex justify-between items-center"> What chains are supported? <span class="text-blue-400 group-open:rotate-180 transition-transform">▼</span> </summary>
          <p class="text-gray-400 text-sm mt-3 leading-relaxed">Solana first and expand to other major chains including Ethereum, Base, BNB Chain, Arbitrum, Optimism, Polygon, and more throughout 2026.</p>
         </details>
         <details class="group border border-gray-700/50 rounded-lg p-4 hover:border-blue-400/50 transition-all cursor-pointer stagger-animation stagger-5"><summary class="font-semibold text-white flex justify-between items-center"> Who's the team behind Alpha0x? <span class="text-blue-400 group-open:rotate-180 transition-transform">▼</span> </summary>
          <p class="text-gray-400 text-sm mt-3 leading-relaxed">A powerhouse team of experienced former LoopNetwork (Layer 1) and Layerium (Layer 2) administrators, united with global crypto community leaders and seasoned backend developers—driving innovation in Privacy + Agent AI.</p>
         </details>
        </div>
       </div>
      </div>
     </div>
    </section><!-- Community Section -->
    <section id="connect" class="px-6 md:px-12 py-16 md:py-24 relative">
     <div class="absolute inset-0 overflow-hidden pointer-events-none">
      <div class="absolute top-0 right-0 w-96 h-96 bg-gradient-to-bl from-cyan-500/10 via-transparent to-transparent rounded-full blur-3xl"></div>
      <div class="absolute bottom-0 left-0 w-96 h-96 bg-gradient-to-tr from-purple-500/10 via-transparent to-transparent rounded-full blur-3xl"></div>
     </div>
     <div class="max-w-6xl mx-auto relative z-10">
      <div class="text-center mb-20">
       <h2 class="font-display font-bold text-3xl md:text-4xl mb-4"><span class="shimmer-text">Join Our Community</span></h2>
       <p class="text-gray-400 text-lg">Be part of the Alpha0x revolution</p>
      </div>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6"><!-- Twitter --> <a href="https://twitter.com/projectalpha0x" target="_blank" rel="noopener noreferrer" class="group stagger-animation stagger-1 relative">
        <div class="absolute inset-0 bg-gradient-to-r from-blue-500/0 via-blue-500/10 to-blue-500/0 rounded-xl opacity-0 group-hover:opacity-100 transition-opacity duration-300 blur-xl"></div>
        <div class="relative h-full p-8 rounded-xl border border-blue-500/30 bg-gradient-to-br from-blue-950/40 to-black/60 hover:border-blue-400/60 transition-all duration-300 overflow-hidden">
         <div class="absolute top-0 right-0 w-32 h-32 bg-blue-500/5 rounded-full blur-2xl group-hover:bg-blue-500/15 transition-all duration-300"></div>
         <div class="relative flex flex-col items-center gap-6">
          <div class="w-20 h-20 rounded-full bg-gradient-to-br from-blue-500/30 to-blue-600/10 flex items-center justify-center border border-blue-400/50 group-hover:border-blue-300 group-hover:from-blue-500/50 transition-all duration-300 shadow-lg shadow-blue-500/20 group-hover:shadow-blue-500/40">
           <svg class="w-10 h-10 text-blue-300 group-hover:text-blue-200 transition-colors electric-icon" fill="currentColor" viewbox="0 0 24 24"><path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417a9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.17-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z" />
           </svg>
          </div>
          <div class="text-center">
           <h3 class="font-display font-bold text-xl text-white mb-2 group-hover:text-blue-200 transition-colors">Twitter</h3>
           <p class="text-gray-400 text-sm leading-relaxed group-hover:text-gray-300 transition-colors">Real-time updates, announcements &amp; community conversations</p>
          </div>
          <div class="pt-2 text-blue-400 group-hover:text-blue-300 transition-colors text-sm font-semibold flex items-center gap-2">
           Follow →
          </div>
         </div>
        </div></a> <!-- Telegram --> <a href="https://t.me/projectalpha0x" target="_blank" rel="noopener noreferrer" class="group stagger-animation stagger-2 relative">
        <div class="absolute inset-0 bg-gradient-to-r from-cyan-500/0 via-cyan-500/10 to-cyan-500/0 rounded-xl opacity-0 group-hover:opacity-100 transition-opacity duration-300 blur-xl"></div>
        <div class="relative h-full p-8 rounded-xl border border-cyan-500/30 bg-gradient-to-br from-cyan-950/40 to-black/60 hover:border-cyan-400/60 transition-all duration-300 overflow-hidden">
         <div class="absolute top-0 right-0 w-32 h-32 bg-cyan-500/5 rounded-full blur-2xl group-hover:bg-cyan-500/15 transition-all duration-300"></div>
         <div class="relative flex flex-col items-center gap-6">
          <div class="w-20 h-20 rounded-full bg-gradient-to-br from-cyan-500/30 to-cyan-600/10 flex items-center justify-center border border-cyan-400/50 group-hover:border-cyan-300 group-hover:from-cyan-500/50 transition-all duration-300 shadow-lg shadow-cyan-500/20 group-hover:shadow-cyan-500/40">
           <svg class="w-10 h-10 text-cyan-300 group-hover:text-cyan-200 transition-colors electric-icon" fill="currentColor" viewbox="0 0 24 24"><path d="M11.944 0A12 12 0 0 0 0 12a12 12 0 0 0 12 12 12 12 0 0 0 12-12A12 12 0 0 0 12 0a11.955 11.955 0 0 0-.056 0zm4.962 7.224c.1-.002.321.023.465.14a.506.506 0 0 1 .171.325c.016.093.036.306.02.472-.18 1.898-.962 6.502-1.36 8.627-.168.9-.499 1.201-.82 1.23-.696.065-1.225-.46-1.9-.902-1.056-.693-1.653-1.124-2.678-1.8-1.185-.78-.417-1.21.258-1.91.177-.184 3.247-2.977 3.307-3.23.007-.032.014-.15-.056-.212s-.174-.041-.249-.024c-.106.024-1.793 1.14-5.061 3.345-.48.33-.913.485-1.313.474-.431-.008-1.252-.241-1.865-.44-.752-.245-1.349-.374-1.297-.789.027-.15.321-.455.875-.71 3.4-1.604 5.666-2.66 6.798-3.172.92-.403 1.757-.588 2.455-.588z" />
           </svg>
          </div>
          <div class="text-center">
           <h3 class="font-display font-bold text-xl text-white mb-2 group-hover:text-cyan-200 transition-colors">Telegram</h3>
           <p class="text-gray-400 text-sm leading-relaxed group-hover:text-gray-300 transition-colors">Chat directly with the team &amp; community members</p>
          </div>
          <div class="pt-2 text-cyan-400 group-hover:text-cyan-300 transition-colors text-sm font-semibold flex items-center gap-2">
           Join →
          </div>
         </div>
        </div></a> <!-- Discord --> <a href="https://discord.gg/GxfN5MwynB" target="_blank" rel="noopener noreferrer" class="group stagger-animation stagger-3 relative">
        <div class="absolute inset-0 bg-gradient-to-r from-purple-500/0 via-purple-500/10 to-purple-500/0 rounded-xl opacity-0 group-hover:opacity-100 transition-opacity duration-300 blur-xl"></div>
        <div class="relative h-full p-8 rounded-xl border border-purple-500/30 bg-gradient-to-br from-purple-950/40 to-black/60 hover:border-purple-400/60 transition-all duration-300 overflow-hidden">
         <div class="absolute top-0 right-0 w-32 h-32 bg-purple-500/5 rounded-full blur-2xl group-hover:bg-purple-500/15 transition-all duration-300"></div>
         <div class="relative flex flex-col items-center gap-6">
          <div class="w-20 h-20 rounded-full bg-gradient-to-br from-purple-500/30 to-purple-600/10 flex items-center justify-center border border-purple-400/50 group-hover:border-purple-300 group-hover:from-purple-500/50 transition-all duration-300 shadow-lg shadow-purple-500/20 group-hover:shadow-purple-500/40">
           <svg class="w-10 h-10 text-purple-300 group-hover:text-purple-200 transition-colors electric-icon" fill="currentColor" viewbox="0 0 24 24"><path d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515a.074.074 0 0 0-.079.037c-.211.375-.444.86-.607 1.244a18.27 18.27 0 0 0-5.487 0c-.163-.384-.396-.869-.609-1.244a.077.077 0 0 0-.079-.036a19.736 19.736 0 0 0-4.885 1.515a.07.07 0 0 0-.032.028C.533 9.046-.32 13.58.099 18.057a.082.082 0 0 0 .031.056a19.9 19.9 0 0 0 5.993 3.03a.078.078 0 0 0 .084-.028c.462-.63.873-1.295 1.226-1.994a.076.076 0 0 0-.041-.106a13.107 13.107 0 0 1-1.872-.892a.077.077 0 0 1-.008-.128c.126-.095.252-.195.372-.298a.074.074 0 0 1 .076-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .075.009c.12.103.246.203.373.298a.077.077 0 0 1-.007.128c-.598.35-1.222.646-1.872.892a.077.077 0 0 0-.041.107c.359.699.77 1.364 1.225 1.994a.076.076 0 0 0 .084.028a19.839 19.839 0 0 0 6.002-3.03a.077.077 0 0 0 .032-.054c.5-4.786-.838-8.895-3.549-12.562a.06.06 0 0 0-.031-.029zM8.02 15.33c-1.183 0-2.157-1.085-2.157-2.419c0-1.334.968-2.419 2.157-2.419c1.196 0 2.178 1.096 2.157 2.42c0 1.333-.96 2.418-2.157 2.418zm7.975 0c-1.183 0-2.157-1.085-2.157-2.419c0-1.334.968-2.419 2.157-2.419c1.196 0 2.178 1.096 2.157 2.42c0 1.333-.96 2.418-2.157 2.418z" />
           </svg>
          </div>
          <div class="text-center">
           <h3 class="font-display font-bold text-xl text-white mb-2 group-hover:text-purple-200 transition-colors">Discord</h3>
           <p class="text-gray-400 text-sm leading-relaxed group-hover:text-gray-300 transition-colors">Voice channels, discussion forums &amp; exclusive events</p>
          </div>
          <div class="pt-2 text-purple-400 group-hover:text-purple-300 transition-colors text-sm font-semibold flex items-center gap-2">
           Connect →
          </div>
         </div>
        </div></a>
      </div>
     </div>
    </section><!-- Footer -->
    <footer class="px-6 md:px-12 py-12 border-t border-gray-800">
     <div class="max-w-6xl mx-auto">
      <div class="text-center text-white text-sm">
       © 2026 Alpha0x. Privacy-First AI Infrastructure.
      </div>
     </div>
    </footer>
   </div>
  </div>
  <script>
    const defaultConfig = {
      hero_title: "CLAW0X",
      hero_subtitle: "Meet Claw0x, the official mascot of Alpha0x, a digital guardian forged at the intersection of privacy-first technology and Agent AI. Alpha0x integrates these innovations to deliver autonomous monitoring and market intelligence directly within DApps. It tracks target wallets, detects new launches, analyzes volume and trends, and evaluates market sentiment—all while ensuring transactions and signals remain fully encrypted and confidential.",
      feature_1_title: "Zero-Knowledge Proofs",
      feature_2_title: "Encrypted Workflows",
      feature_3_title: "Decentralized Execution",
      feature_4_title: "Confidential Insights",
      feature_5_title: "Adaptive Security"
    };
    
    let config = { ...defaultConfig };
    
    async function onConfigChange(cfg) {
      config = { ...defaultConfig, ...cfg };
      
      const heroTitle = document.getElementById('hero-title');
      const titleText = config.hero_title || defaultConfig.hero_title;
      heroTitle.innerHTML = `<span class="shimmer-text">${titleText}</span>`;
      
      document.getElementById('hero-subtitle').textContent = config.hero_subtitle || defaultConfig.hero_subtitle;
      document.getElementById('feature-1-title').textContent = config.feature_1_title || defaultConfig.feature_1_title;
      document.getElementById('feature-2-title').textContent = config.feature_2_title || defaultConfig.feature_2_title;
      document.getElementById('feature-3-title').textContent = config.feature_3_title || defaultConfig.feature_3_title;
      document.getElementById('feature-4-title').textContent = config.feature_4_title || defaultConfig.feature_4_title;
      document.getElementById('feature-5-title').textContent = config.feature_5_title || defaultConfig.feature_5_title;
    }
    
    function mapToCapabilities(cfg) {
      return {
        recolorables: [],
        borderables: [],
        fontEditable: undefined,
        fontSizeable: undefined
      };
    }
    
    function mapToEditPanelValues(cfg) {
      return new Map([
        ["hero_title", cfg.hero_title || defaultConfig.hero_title],
        ["hero_subtitle", cfg.hero_subtitle || defaultConfig.hero_subtitle],
        ["feature_1_title", cfg.feature_1_title || defaultConfig.feature_1_title],
        ["feature_2_title", cfg.feature_2_title || defaultConfig.feature_2_title],
        ["feature_3_title", cfg.feature_3_title || defaultConfig.feature_3_title],
        ["feature_4_title", cfg.feature_4_title || defaultConfig.feature_4_title],
        ["feature_5_title", cfg.feature_5_title || defaultConfig.feature_5_title]
      ]);
    }
    
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities,
        mapToEditPanelValues
      });
    }
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9cbb1ae1131fda84',t:'MTc3MDcyMTI0OS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
