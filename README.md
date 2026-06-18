# Theprohoopers5
<!DOCTYPE html>
<html lang="pt">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>PRO HOOPS</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Anton&family=Bebas+Neue&family=Oswald:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500;700&display=swap" rel="stylesheet">
<style>
  :root{
    --black: #0a0a0b;
    --charcoal: #161618;
    --steel: #2b2c30;
    --ash: #6b6c70;
    --smoke: #a8a9ad;
    --paper: #ededee;
    --line-orange: #ff5a1f;
    --line-orange-dim: #ff5a1f33;
  }

  *{margin:0;padding:0;box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--black);
    color:var(--paper);
    font-family:'Oswald', sans-serif;
    overflow-x:hidden;
  }

  ::selection{ background:var(--line-orange); color:#0a0a0b; }

  /* Reduced motion respect */
  @media (prefers-reduced-motion: reduce){
    *{animation-duration:0.01ms !important; animation-iteration-count:1 !important; transition-duration:0.01ms !important; scroll-behavior:auto !important;}
  }

  a{color:inherit; text-decoration:none;}
  button{font-family:inherit;}

  :focus-visible{
    outline:2px solid var(--line-orange);
    outline-offset:3px;
  }

  /* ============ SHARED ============ */
  .court-texture{
    position:absolute; inset:0;
    background-image:
      linear-gradient(var(--steel) 1px, transparent 1px),
      linear-gradient(90deg, var(--steel) 1px, transparent 1px);
    background-size: 64px 64px;
    opacity:0.18;
    pointer-events:none;
  }

  .eyebrow{
    font-family:'JetBrains Mono', monospace;
    font-size:0.72rem;
    letter-spacing:0.28em;
    text-transform:uppercase;
    color:var(--line-orange);
    display:flex;
    align-items:center;
    gap:10px;
  }
  .eyebrow::before{
    content:'';
    width:18px; height:2px;
    background:var(--line-orange);
  }

  .display-xl{
    font-family:'Anton', sans-serif;
    text-transform:uppercase;
    line-height:0.92;
    letter-spacing:0.01em;
  }

  .nav{
    position:fixed; top:0; left:0; right:0;
    z-index:200;
    display:flex;
    align-items:center;
    justify-content:space-between;
    padding:26px 5vw;
    mix-blend-mode:normal;
  }
  .logo{
    font-family:'Anton', sans-serif;
    font-size:1.3rem;
    letter-spacing:0.02em;
    text-transform:uppercase;
    display:flex;
    align-items:baseline;
    gap:2px;
  }
  .logo .o-ball{
    display:inline-block;
    width:0.62em; height:0.62em;
    border-radius:50%;
    background:
      radial-gradient(circle at 32% 28%, #ff8a4f, var(--line-orange) 60%, #b33e10 100%);
    position:relative;
    margin:0 1px;
    box-shadow: inset -2px -2px 4px rgba(0,0,0,0.45);
  }
  .logo .o-ball::before, .logo .o-ball::after{
    content:'';
    position:absolute;
    background:#0a0a0b;
  }
  .logo .o-ball::before{ left:48%; top:0; width:8%; height:100%; }
  .logo .o-ball::after{ top:48%; left:0; width:100%; height:8%; }

  .navlinks{
    display:flex;
    gap:34px;
    font-family:'JetBrains Mono', monospace;
    font-size:0.74rem;
    letter-spacing:0.12em;
    text-transform:uppercase;
  }
  .navlinks a{
    position:relative;
    padding-bottom:6px;
    color:var(--smoke);
    transition:color 0.25s ease;
  }
  .navlinks a:hover, .navlinks a:focus-visible{ color:var(--paper); }
  .navlinks a::after{
    content:'';
    position:absolute; left:0; bottom:0;
    width:0; height:1px;
    background:var(--line-orange);
    transition:width 0.3s ease;
  }
  .navlinks a:hover::after{ width:100%; }

  @media (max-width:780px){
    .navlinks{ display:none; }
  }

  /* ============ HERO ============ */
  .hero{
    position:relative;
    min-height:100vh;
    display:flex;
    align-items:center;
    overflow:hidden;
    background:
      radial-gradient(circle at 78% 38%, rgba(255,90,31,0.10), transparent 55%),
      linear-gradient(180deg, #0d0d0e 0%, #0a0a0b 70%);
  }

  .hero-scoreboard-glow{
    position:absolute;
    top:-20%; right:-10%;
    width:60vw; height:60vw;
    background:radial-gradient(circle, rgba(255,90,31,0.14), transparent 65%);
    filter:blur(10px);
    pointer-events:none;
  }

  .hero-inner{
    position:relative;
    z-index:2;
    width:100%;
    max-width:1400px;
    margin:0 auto;
    padding:0 5vw;
    display:grid;
    grid-template-columns:1.1fr 0.9fr;
    align-items:center;
    gap:40px;
  }

  .hero-copy{ padding-top:60px; }
  .hero-copy .eyebrow{ margin-bottom:22px; opacity:0; animation:riseIn 0.7s 0.15s forwards ease-out; }
  .hero-title{
    font-size:clamp(3.6rem, 9vw, 8.2rem);
    color:var(--paper);
    opacity:0;
    animation:riseIn 0.8s 0.3s forwards ease-out;
  }
  .hero-title span{
    display:block;
    -webkit-text-stroke:2px var(--paper);
    color:transparent;
  }
  .hero-sub{
    margin-top:26px;
    max-width:440px;
    color:var(--smoke);
    font-weight:300;
    font-size:1.05rem;
    line-height:1.6;
    opacity:0;
    animation:riseIn 0.8s 0.5s forwards ease-out;
  }
  .hero-cta-row{
    margin-top:38px;
    display:flex;
    gap:16px;
    align-items:center;
    opacity:0;
    animation:riseIn 0.8s 0.65s forwards ease-out;
  }
  .btn-primary{
    background:var(--line-orange);
    color:#0a0a0b;
    font-family:'JetBrains Mono', monospace;
    font-weight:700;
    font-size:0.82rem;
    letter-spacing:0.1em;
    text-transform:uppercase;
    padding:16px 30px;
    border:none;
    border-radius:2px;
    cursor:pointer;
    transition:transform 0.25s ease, box-shadow 0.25s ease;
    box-shadow:0 0 0 0 rgba(255,90,31,0.5);
  }
  .btn-primary:hover{
    transform:translateY(-2px);
    box-shadow:0 10px 24px -8px rgba(255,90,31,0.55);
  }
  .btn-ghost{
    color:var(--paper);
    font-family:'JetBrains Mono', monospace;
    font-size:0.78rem;
    letter-spacing:0.1em;
    text-transform:uppercase;
    border-bottom:1px solid var(--steel);
    padding-bottom:4px;
    transition:border-color 0.25s ease, color 0.25s ease;
  }
  .btn-ghost:hover{ border-color:var(--paper); }

  @keyframes riseIn{
    from{ opacity:0; transform:translateY(22px); }
    to{ opacity:1; transform:translateY(0); }
  }

  /* Floating player card */
  .player-card-zone{
    position:relative;
    height:640px;
    display:flex;
    align-items:center;
    justify-content:center;
  }
  .player-card{
    position:relative;
    width:340px;
    border-radius:6px;
    background:linear-gradient(165deg, #1c1c1f, #0e0e10 70%);
    border:1px solid var(--steel);
    padding:26px 26px 30px;
    box-shadow:0 40px 70px -30px rgba(0,0,0,0.8);
    animation:floatCard 6s ease-in-out infinite, cardIn 0.9s 0.4s backwards;
  }
  @keyframes cardIn{
    from{ opacity:0; transform:translateY(40px) rotate(3deg); }
    to{ opacity:1; transform:translateY(0) rotate(0deg); }
  }
  @keyframes floatCard{
    0%,100%{ transform:translateY(0) rotate(-1.2deg); }
    50%{ transform:translateY(-18px) rotate(1deg); }
  }
  .player-card .card-top{
    display:flex;
    justify-content:space-between;
    align-items:flex-start;
    font-family:'JetBrains Mono', monospace;
    font-size:0.68rem;
    letter-spacing:0.1em;
    color:var(--ash);
    text-transform:uppercase;
  }
  .player-card .ovr{
    font-family:'Anton', sans-serif;
    font-size:2.2rem;
    color:var(--line-orange);
    line-height:1;
  }
  .player-figure{
    width:100%;
    height:300px;
    margin:6px 0 4px;
  }
  .player-card .pname{
    font-family:'Anton', sans-serif;
    font-size:1.5rem;
    text-transform:uppercase;
    letter-spacing:0.01em;
    color:var(--paper);
  }
  .player-card .ppos{
    font-family:'JetBrains Mono', monospace;
    font-size:0.7rem;
    color:var(--smoke);
    letter-spacing:0.12em;
    margin-top:2px;
  }
  .stat-row{
    display:flex;
    justify-content:space-between;
    margin-top:18px;
    padding-top:16px;
    border-top:1px solid var(--steel);
  }
  .stat{
    text-align:center;
  }
  .stat .num{
    font-family:'Anton', sans-serif;
    font-size:1.15rem;
    color:var(--paper);
  }
  .stat .lab{
    font-family:'JetBrains Mono', monospace;
    font-size:0.6rem;
    color:var(--ash);
    letter-spacing:0.1em;
    margin-top:2px;
  }

  .court-floor-line{
    position:absolute;
    bottom:0; left:0; right:0;
    height:1px;
    background:linear-gradient(90deg, transparent, var(--steel), transparent);
  }

  .scroll-cue{
    position:absolute;
    bottom:34px; left:5vw;
    font-family:'JetBrains Mono', monospace;
    font-size:0.66rem;
    letter-spacing:0.18em;
    text-transform:uppercase;
    color:var(--ash);
    display:flex;
    align-items:center;
    gap:10px;
  }
  .scroll-cue .stick{
    width:1px; height:30px;
    background:var(--ash);
    position:relative;
    overflow:hidden;
  }
  .scroll-cue .stick::after{
    content:'';
    position:absolute; top:0; left:0;
    width:100%; height:40%;
    background:var(--line-orange);
    animation:scrollDrip 1.8s ease-in-out infinite;
  }
  @keyframes scrollDrip{
    0%{ top:-40%; }
    100%{ top:100%; }
  }

  @media (max-width: 900px){
    .hero-inner{ grid-template-columns:1fr; }
    .player-card-zone{ height:420px; margin-top:20px; }
    .player-card{ width:280px; }
    .hero-copy{ padding-top:120px; }
  }

  /* ============ FEATURES (Page 2) ============ */
  .features{
    position:relative;
    background:var(--black);
  }
  .feat-block{
    position:relative;
    min-height:92vh;
    display:flex;
    align-items:center;
    overflow:hidden;
    border-top:1px solid var(--steel);
  }
  .feat-arena-bg{
    position:absolute; inset:0;
    background:
      radial-gradient(ellipse 80% 60% at 50% 0%, rgba(255,180,90,0.16), transparent 60%),
      radial-gradient(ellipse 60% 50% at 20% 100%, rgba(255,90,31,0.08), transparent 70%),
      linear-gradient(180deg, #0a0a0b, #141416);
  }
  .feat-arena-bg .beam{
    position:absolute;
    top:-10%;
    width:140px;
    height:160%;
    background:linear-gradient(180deg, rgba(255,225,180,0.16), transparent 75%);
    transform:rotate(14deg);
    filter:blur(6px);
  }
  .feat-arena-bg .beam.b1{ left:8%; }
  .feat-arena-bg .beam.b2{ left:28%; transform:rotate(8deg); opacity:0.7;}
  .feat-arena-bg .beam.b3{ left:68%; transform:rotate(-10deg); opacity:0.5;}

  .feat-content{
    position:relative;
    z-index:2;
    width:100%;
    max-width:1300px;
    margin:0 auto;
    padding:0 5vw;
    display:grid;
    grid-template-columns:0.85fr 1.15fr;
    gap:60px;
    align-items:center;
  }
  .feat-block.reverse .feat-content{
    grid-template-columns:1.15fr 0.85fr;
  }
  .feat-block.reverse .feat-text{ order:2; }
  .feat-block.reverse .feat-visual{ order:1; }

  .feat-num{
    font-family:'JetBrains Mono', monospace;
    font-size:0.74rem;
    color:var(--line-orange);
    letter-spacing:0.2em;
  }
  .feat-title{
    margin-top:18px;
    font-size:clamp(2.4rem, 5vw, 4.2rem);
    color:var(--paper);
  }
  .feat-desc{
    margin-top:22px;
    max-width:420px;
    color:var(--smoke);
    font-weight:300;
    line-height:1.7;
    font-size:1.02rem;
  }
  .feat-btn{
    margin-top:32px;
    display:inline-flex;
    align-items:center;
    gap:14px;
    background:transparent;
    border:1px solid var(--steel);
    color:var(--paper);
    font-family:'JetBrains Mono', monospace;
    font-size:0.8rem;
    letter-spacing:0.1em;
    text-transform:uppercase;
    padding:16px 26px;
    cursor:pointer;
    transition:all 0.3s ease;
    border-radius:2px;
  }
  .feat-btn:hover{
    border-color:var(--line-orange);
    background:var(--line-orange-dim);
    gap:20px;
  }
  .feat-btn .arrow{ transition:transform 0.3s ease; }
  .feat-btn:hover .arrow{ transform:translateX(4px); }

  /* Visual: arena lights illustration */
  .arena-visual{
    position:relative;
    height:420px;
    border:1px solid var(--steel);
    border-radius:6px;
    overflow:hidden;
    background:linear-gradient(180deg, #111113, #0a0a0b);
  }
  .arena-visual svg{ width:100%; height:100%; display:block; }

  /* Visual: gameplay action card */
  .action-visual{
    position:relative;
    height:420px;
    border:1px solid var(--steel);
    border-radius:6px;
    overflow:hidden;
    background:linear-gradient(160deg, #15151a, #0a0a0b);
    display:flex;
    align-items:center;
    justify-content:center;
  }
  .action-visual svg{ width:78%; height:78%; }

  .hud-corner{
    position:absolute;
    font-family:'JetBrains Mono', monospace;
    font-size:0.62rem;
    letter-spacing:0.1em;
    color:var(--ash);
    text-transform:uppercase;
  }
  .hud-corner.tl{ top:14px; left:16px; }
  .hud-corner.br{ bottom:14px; right:16px; }

  @media (max-width:900px){
    .feat-content, .feat-block.reverse .feat-content{
      grid-template-columns:1fr;
    }
    .feat-block.reverse .feat-text, .feat-block.reverse .feat-visual{ order:initial; }
    .feat-block{ padding:80px 0; min-height:auto; }
  }

  /* ============ GAME MODES (Page 3) ============ */
  .modes{
    position:relative;
    background:#0a0a0b;
    padding:140px 5vw 120px;
    border-top:1px solid var(--steel);
    overflow:hidden;
  }
  .modes-aerial{
    position:absolute; inset:0;
    opacity:0.5;
  }
  .modes-aerial svg{ width:100%; height:100%; }

  .modes-head{
    position:relative;
    z-index:2;
    max-width:1300px;
    margin:0 auto 70px;
  }
  .modes-head .display-xl{
    font-size:clamp(2.6rem, 6vw, 5rem);
    color:var(--paper);
    margin-top:18px;
  }

  .modes-grid{
    position:relative;
    z-index:2;
    max-width:1300px;
    margin:0 auto;
    display:grid;
    grid-template-columns:repeat(3, 1fr);
    gap:26px;
  }
  .mode-card{
    position:relative;
    border:1px solid var(--steel);
    border-radius:6px;
    overflow:hidden;
    min-height:480px;
    display:flex;
    flex-direction:column;
    justify-content:flex-end;
    padding:30px;
    background:linear-gradient(180deg, #131315, #0a0a0b);
    transition:border-color 0.3s ease, transform 0.3s ease;
  }
  .mode-card:hover{
    border-color:var(--ash);
    transform:translateY(-6px);
  }
  .mode-visual{
    position:absolute;
    inset:0;
    z-index:0;
  }
  .mode-visual svg{ width:100%; height:100%; }
  .mode-fade{
    position:absolute;
    inset:0;
    background:linear-gradient(180deg, rgba(10,10,11,0.05) 30%, rgba(10,10,11,0.96) 88%);
    z-index:1;
  }
  .mode-body{ position:relative; z-index:2; }
  .mode-tag{
    font-family:'JetBrains Mono', monospace;
    font-size:0.68rem;
    letter-spacing:0.18em;
    text-transform:uppercase;
    color:var(--line-orange);
  }
  .mode-name{
    font-family:'Anton', sans-serif;
    font-size:2.1rem;
    text-transform:uppercase;
    color:var(--paper);
    margin-top:10px;
    line-height:1;
  }
  .mode-desc{
    margin-top:12px;
    color:var(--smoke);
    font-weight:300;
    font-size:0.92rem;
    line-height:1.55;
  }

  @media (max-width:980px){
    .modes-grid{ grid-template-columns:1fr; }
    .mode-card{ min-height:400px; }
  }

  /* ============ REVIEWS / COMMUNITY (Page 4) ============ */
  .community{
    position:relative;
    background:#0a0a0b;
    padding:140px 5vw 0;
    border-top:1px solid var(--steel);
  }
  .community-head{
    max-width:1300px;
    margin:0 auto 60px;
  }
  .community-head .display-xl{
    font-size:clamp(2.4rem, 5.5vw, 4.6rem);
    color:var(--paper);
    margin-top:18px;
  }

  .reviews-row{
    max-width:1300px;
    margin:0 auto;
    display:grid;
    grid-template-columns:repeat(3, 1fr);
    gap:24px;
  }
  .review-card{
    border:1px solid var(--steel);
    border-radius:6px;
    padding:30px;
    background:#111113;
  }
  .review-stars{
    color:var(--line-orange);
    font-family:'JetBrains Mono', monospace;
    letter-spacing:2px;
    font-size:0.9rem;
  }
  .review-quote{
    margin-top:16px;
    color:var(--paper);
    font-weight:300;
    line-height:1.65;
    font-size:1rem;
  }
  .review-author{
    margin-top:20px;
    display:flex;
    align-items:center;
    gap:12px;
    font-family:'JetBrains Mono', monospace;
    font-size:0.72rem;
    color:var(--ash);
    letter-spacing:0.06em;
  }
  .review-author .dot{
    width:8px; height:8px;
    border-radius:50%;
    background:var(--line-orange);
  }

  @media (max-width:980px){
    .reviews-row{ grid-template-columns:1fr; }
  }

  /* Footer */
  .footer{
    margin-top:120px;
    border-top:1px solid var(--steel);
    background:#080809;
  }
  .footer-inner{
    max-width:1300px;
    margin:0 auto;
    padding:80px 5vw 50px;
    display:grid;
    grid-template-columns:1.2fr 1fr;
    gap:60px;
  }
  .footer-cta .eyebrow{ margin-bottom:20px; }
  .footer-cta h3{
    font-family:'Anton', sans-serif;
    font-size:clamp(2rem, 4vw, 3rem);
    text-transform:uppercase;
    color:var(--paper);
    line-height:1.05;
  }
  .footer-cta p{
    margin-top:18px;
    max-width:420px;
    color:var(--smoke);
    font-weight:300;
    line-height:1.6;
  }
  .footer-form{
    margin-top:30px;
    display:flex;
    gap:12px;
    max-width:440px;
  }
  .footer-form input{
    flex:1;
    background:transparent;
    border:1px solid var(--steel);
    color:var(--paper);
    padding:14px 16px;
    font-family:'Oswald', sans-serif;
    font-size:0.92rem;
    border-radius:2px;
  }
  .footer-form input::placeholder{ color:var(--ash); }
  .footer-form input:focus{ border-color:var(--line-orange); outline:none; }

  .footer-social{
    display:flex;
    flex-direction:column;
    justify-content:center;
  }
  .social-list{
    display:flex;
    gap:34px;
  }
  .social-item{
    display:flex;
    flex-direction:column;
    align-items:center;
    gap:12px;
  }
  .social-icon{
    width:54px; height:54px;
    border:1px solid var(--steel);
    border-radius:50%;
    display:flex;
    align-items:center;
    justify-content:center;
    color:var(--smoke);
    transition:all 0.3s ease;
  }
  .social-item:hover .social-icon{
    border-color:var(--line-orange);
    color:var(--line-orange);
    transform:translateY(-4px);
  }
  .social-icon svg{ width:22px; height:22px; }
  .social-handle{
    font-family:'JetBrains Mono', monospace;
    font-size:0.7rem;
    color:var(--ash);
    letter-spacing:0.04em;
  }

  .footer-bottom{
    max-width:1300px;
    margin:0 auto;
    padding:26px 5vw 30px;
    border-top:1px solid var(--steel);
    display:flex;
    justify-content:space-between;
    align-items:center;
    font-family:'JetBrains Mono', monospace;
    font-size:0.68rem;
    color:var(--ash);
    letter-spacing:0.06em;
    text-transform:uppercase;
  }

  @media (max-width:780px){
    .footer-inner{ grid-template-columns:1fr; }
    .footer-bottom{ flex-direction:column; gap:10px; text-align:center; }
  }

  /* scroll-reveal helper */
  .reveal{
    opacity:0;
    transform:translateY(30px);
    transition:opacity 0.8s ease, transform 0.8s ease;
  }
  .reveal.in{
    opacity:1;
    transform:translateY(0);
  }
</style>
</head>
<body>

<nav class="nav">
  <div class="logo"><span>PR</span><span class="o-ball"></span><span>HOOPS</span></div>
  <div class="navlinks">
    <a href="#features">Features</a>
    <a href="#modes">Modes</a>
    <a href="#community">Community</a>
  </div>
</nav>

<!-- ===================== PAGE 1 — HOMEPAGE ===================== -->
<section class="hero" id="home">
  <div class="hero-scoreboard-glow"></div>
  <div class="court-texture"></div>

  <!-- background dunking figure, drawn as SVG silhouette to avoid stock-photo licensing issues -->
  <svg style="position:absolute; right:-6%; top:0; height:100%; width:62%; opacity:0.9; z-index:1;" viewBox="0 0 600 800" preserveAspectRatio="xMidYMax slice" xmlns="http://www.w3.org/2000/svg">
    <defs>
      <linearGradient id="silhouetteFade" x1="0" y1="0" x2="0" y2="1">
        <stop offset="0%" stop-color="#1a1a1d"/>
        <stop offset="100%" stop-color="#0a0a0b"/>
      </linearGradient>
      <radialGradient id="hoopGlow" cx="50%" cy="50%" r="50%">
        <stop offset="0%" stop-color="#ff5a1f" stop-opacity="0.55"/>
        <stop offset="100%" stop-color="#ff5a1f" stop-opacity="0"/>
      </radialGradient>
    </defs>
    <circle cx="430" cy="160" r="160" fill="url(#hoopGlow)"/>
    <!-- hoop -->
    <rect x="370" y="120" width="120" height="80" fill="none" stroke="#3a3a3e" stroke-width="3"/>
    <ellipse cx="430" cy="205" rx="55" ry="10" fill="none" stroke="#ff5a1f" stroke-width="4"/>
    <!-- dunking figure (stylized, non-representational silhouette) -->
    <g fill="url(#silhouetteFade)">
      <path d="M250 760 
        L260 600 
        Q255 560 280 520
        L300 430
        Q305 380 350 340
        L400 260
        Q410 235 440 220
        L470 195
        Q480 188 490 195
        L500 215
        Q505 230 490 245
        L450 280
        Q430 300 415 330
        L390 410
        Q380 450 395 480
        L430 540
        Q445 570 440 610
        L450 760
        Z"/>
      <!-- raised arm to hoop -->
      <path d="M470 195 Q500 170 430 215 Q455 200 470 195Z"/>
      <path d="M345 345 Q310 360 290 410 Q270 460 290 520 Q300 480 320 440 Q335 400 345 345Z"/>
    </g>
  </svg>

  <div class="hero-inner">
    <div class="hero-copy">
      <div class="eyebrow">Season 01 — Tip-off</div>
      <h1 class="hero-title display-xl">Own<br><span>The Paint</span></h1>
      <p class="hero-sub">Build your roster, run your system, and take it to the rim. Pro Hoops puts real basketball IQ into every possession — no two games play the same.</p>
      <div class="hero-cta-row">
        <button class="btn-primary">Play Now</button>
        <a href="#features" class="btn-ghost">Watch Gameplay</a>
      </div>
    </div>

    <div class="player-card-zone">
      <div class="player-card">
        <div class="card-top">
          <span>Starting five</span>
          <span class="ovr">96</span>
        </div>
        <svg class="player-figure" viewBox="0 0 300 300" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <linearGradient id="cardFig" x1="0" y1="0" x2="0" y2="1">
              <stop offset="0%" stop-color="#3a3a3e"/>
              <stop offset="100%" stop-color="#17171a"/>
            </linearGradient>
          </defs>
          <ellipse cx="150" cy="270" rx="90" ry="14" fill="#000" opacity="0.4"/>
          <g fill="url(#cardFig)">
            <circle cx="150" cy="55" r="26"/>
            <path d="M115 90 Q150 78 185 90 L195 150 Q198 175 180 185 L185 250 L165 250 L158 190 L142 190 L135 250 L115 250 L120 185 Q102 175 105 150 Z"/>
            <path d="M115 95 Q85 110 75 150 Q70 170 85 175 Q90 150 100 130 Q105 110 115 95Z"/>
            <path d="M185 95 Q210 100 222 130 L235 110 Q225 95 200 90 Z"/>
          </g>
          <circle cx="240" cy="100" r="13" fill="#ff5a1f"/>
          <path d="M240 87 L240 113 M227 100 L253 100" stroke="#0a0a0b" stroke-width="1.4"/>
        </svg>
        <div class="pname">M. Carter</div>
        <div class="ppos">Shooting Guard · #23</div>
        <div class="stat-row">
          <div class="stat"><div class="num">92</div><div class="lab">SPD</div></div>
          <div class="stat"><div class="num">88</div><div class="lab">3PT</div></div>
          <div class="stat"><div class="num">95</div><div class="lab">DNK</div></div>
          <div class="stat"><div class="num">90</div><div class="lab">DEF</div></div>
        </div>
      </div>
    </div>
  </div>

  <div class="scroll-cue"><span class="stick"></span>Scroll</div>
  <div class="court-floor-line"></div>
</section>

<!-- ===================== PAGE 2 — FEATURES ===================== -->
<section class="features" id="features">

  <div class="feat-block">
    <div class="feat-arena-bg">
      <div class="beam b1"></div>
      <div class="beam b2"></div>
      <div class="beam b3"></div>
    </div>
    <div class="feat-content">
      <div class="feat-text">
        <div class="feat-num">FEATURE — ARENA</div>
        <h2 class="feat-title display-xl">Lights.<br>Crowd.<br>Noise.</h2>
        <p class="feat-desc">Every arena is built from the ground up — dynamic crowd reactions, blinding tunnel lights, and a sound system that gets louder the closer the game.</p>
      </div>
      <div class="feat-visual">
        <div class="arena-visual">
          <span class="hud-corner tl">Arena_04 / Night</span>
          <span class="hud-corner br">Capacity 18,422</span>
          <svg viewBox="0 0 600 420" xmlns="http://www.w3.org/2000/svg">
            <defs>
              <radialGradient id="arenaLight" cx="50%" cy="0%" r="80%">
                <stop offset="0%" stop-color="#ffdcb0" stop-opacity="0.7"/>
                <stop offset="100%" stop-color="#ffdcb0" stop-opacity="0"/>
              </radialGradient>
              <linearGradient id="floorGrad" x1="0" y1="0" x2="0" y2="1">
                <stop offset="0%" stop-color="#2a1b12"/>
                <stop offset="100%" stop-color="#160d08"/>
              </linearGradient>
            </defs>
            <rect width="600" height="420" fill="#0c0c0e"/>
            <rect width="600" height="420" fill="url(#arenaLight)"/>
            <!-- light rigs -->
            <g stroke="#4a4a4e" stroke-width="2">
              <line x1="60" y1="0" x2="60" y2="60"/>
              <line x1="200" y1="0" x2="200" y2="40"/>
              <line x1="400" y1="0" x2="400" y2="40"/>
              <line x1="540" y1="0" x2="540" y2="60"/>
            </g>
            <g fill="#ffd9a3">
              <circle cx="60" cy="62" r="7"/>
              <circle cx="200" cy="42" r="7"/>
              <circle cx="400" cy="42" r="7"/>
              <circle cx="540" cy="62" r="7"/>
            </g>
            <!-- court floor -->
            <polygon points="120,420 480,420 380,260 220,260" fill="url(#floorGrad)"/>
            <polygon points="120,420 480,420 380,260 220,260" fill="none" stroke="#ff5a1f" stroke-width="1.5" opacity="0.5"/>
            <!-- crowd dots -->
            <g fill="#3a3a3e">
              <circle cx="40" cy="220" r="3"/><circle cx="60" cy="225" r="3"/><circle cx="80" cy="218" r="3"/>
              <circle cx="100" cy="228" r="3"/><circle cx="120" cy="216" r="3"/><circle cx="500" cy="220" r="3"/>
              <circle cx="520" cy="226" r="3"/><circle cx="540" cy="218" r="3"/><circle cx="560" cy="222" r="3"/>
            </g>
          </svg>
        </div>
      </div>
    </div>
  </div>

  <div class="feat-block reverse">
    <div class="feat-arena-bg" style="background:linear-gradient(180deg,#0a0a0b,#121214);"></div>
    <div class="feat-content">
      <div class="feat-text">
        <div class="feat-num">FEATURE — GAMEPLAY</div>
        <h2 class="feat-title display-xl">Every Move<br>Counts</h2>
        <p class="feat-desc">Crossovers, step-backs, contested fades — full animation control puts every play in your hands. React to the defense, not a script.</p>
        <button class="feat-btn">Play Gameplay Demo <span class="arrow">→</span></button>
      </div>
      <div class="feat-visual">
        <div class="action-visual">
          <svg viewBox="0 0 300 320" xmlns="http://www.w3.org/2000/svg">
            <defs>
              <linearGradient id="actFig" x1="0" y1="0" x2="0" y2="1">
                <stop offset="0%" stop-color="#4a4a4e"/>
                <stop offset="100%" stop-color="#19191c"/>
              </linearGradient>
            </defs>
            <ellipse cx="150" cy="305" rx="100" ry="10" fill="#000" opacity="0.35"/>
            <g fill="url(#actFig)">
              <circle cx="160" cy="50" r="24"/>
              <path d="M125 82 Q160 70 195 82 L210 150 Q150 175 95 150 L125 82Z"/>
              <path d="M195 85 Q235 70 260 30 L245 18 Q220 50 190 65Z"/>
              <path d="M125 88 Q90 110 70 160 Q90 165 100 150 Q108 120 125 88Z"/>
              <path d="M150 150 Q140 200 165 240 Q175 260 160 300 L145 300 Q150 260 140 235 Q120 195 130 150Z"/>
              <path d="M150 150 Q160 200 135 240 Q125 260 140 300 L155 300 Q150 260 160 235 Q180 195 170 150Z"/>
            </g>
            <circle cx="262" cy="20" r="14" fill="#ff5a1f"/>
            <path d="M262 6 L262 34 M248 20 L276 20" stroke="#0a0a0b" stroke-width="1.5"/>
          </svg>
        </div>
      </div>
    </div>
  </div>

</section>

<!-- ===================== PAGE 3 — GAME MODES ===================== -->
<section class="modes" id="modes">
  <div class="modes-aerial">
    <svg viewBox="0 0 1400 700" preserveAspectRatio="xMidYMid slice" xmlns="http://www.w3.org/2000/svg">
      <defs>
        <linearGradient id="aerialFloor" x1="0" y1="0" x2="1" y2="1">
          <stop offset="0%" stop-color="#1c1208"/>
          <stop offset="100%" stop-color="#0a0a0b"/>
        </linearGradient>
      </defs>
      <rect width="1400" height="700" fill="#0a0a0b"/>
      <rect x="200" y="60" width="1000" height="580" fill="url(#aerialFloor)" stroke="#ff5a1f" stroke-width="1.5" opacity="0.7"/>
      <line x1="700" y1="60" x2="700" y2="640" stroke="#ff5a1f" stroke-width="1.2" opacity="0.5"/>
      <circle cx="700" cy="350" r="90" fill="none" stroke="#ff5a1f" stroke-width="1.2" opacity="0.5"/>
      <rect x="200" y="280" width="60" height="140" fill="none" stroke="#ff5a1f" stroke-width="1" opacity="0.4"/>
      <rect x="1140" y="280" width="60" height="140" fill="none" stroke="#ff5a1f" stroke-width="1" opacity="0.4"/>
    </svg>
  </div>

  <div class="modes-head">
    <div class="eyebrow">Choose your court</div>
    <h2 class="display-xl">Three Ways<br>To Play</h2>
  </div>

  <div class="modes-grid">

    <div class="mode-card">
      <div class="mode-visual">
        <svg viewBox="0 0 400 480" xmlns="http://www.w3.org/2000/svg">
          <defs><linearGradient id="seasonFig" x1="0" y1="0" x2="0" y2="1"><stop offset="0%" stop-color="#3a3a3e"/><stop offset="100%" stop-color="#15151a"/></linearGradient></defs>
          <rect width="400" height="480" fill="#0c0c0e"/>
          <g fill="url(#seasonFig)">
            <circle cx="130" cy="120" r="20"/>
            <path d="M105 148 Q130 138 155 148 L165 230 L95 230Z"/>
            <circle cx="220" cy="100" r="22"/>
            <path d="M195 130 Q220 120 245 130 L255 220 L185 220Z"/>
            <circle cx="300" cy="135" r="18"/>
            <path d="M278 160 Q300 152 322 160 L330 235 L270 235Z"/>
          </g>
        </svg>
      </div>
      <div class="mode-fade"></div>
      <div class="mode-body">
        <div class="mode-tag">Mode 01</div>
        <div class="mode-name">Season</div>
        <p class="mode-desc">Run a full franchise — draft, trade, and grind through 82 games with a roster that grows with you.</p>
      </div>
    </div>

    <div class="mode-card">
      <div class="mode-visual">
        <svg viewBox="0 0 400 480" xmlns="http://www.w3.org/2000/svg">
          <defs><linearGradient id="tourFig" x1="0" y1="0" x2="0" y2="1"><stop offset="0%" stop-color="#4a4a4e"/><stop offset="100%" stop-color="#15151a"/></linearGradient></defs>
          <rect width="400" height="480" fill="#0c0c0e"/>
          <line x1="200" y1="60" x2="200" y2="420" stroke="#ff5a1f" stroke-width="1" opacity="0.4"/>
          <g fill="url(#tourFig)">
            <circle cx="120" cy="160" r="22"/>
            <path d="M95 188 Q120 178 145 188 L155 270 Q120 285 90 270Z"/>
            <path d="M145 195 Q175 185 190 160 L178 148 Q160 170 140 180Z"/>
            <circle cx="290" cy="160" r="22"/>
            <path d="M265 188 Q290 178 315 188 L325 270 Q290 285 260 270Z"/>
            <path d="M265 195 Q235 185 220 160 L232 148 Q250 170 270 180Z"/>
          </g>
        </svg>
      </div>
      <div class="mode-fade"></div>
      <div class="mode-body">
        <div class="mode-tag">Mode 02</div>
        <div class="mode-name">Tournament</div>
        <p class="mode-desc">Single elimination, 1v1. No bench, no excuses — just you, your defender, and the next bracket.</p>
      </div>
    </div>

    <div class="mode-card">
      <div class="mode-visual">
        <svg viewBox="0 0 400 480" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <radialGradient id="ballGrad" cx="35%" cy="30%" r="65%">
              <stop offset="0%" stop-color="#ff8a4f"/>
              <stop offset="55%" stop-color="#e8590f"/>
              <stop offset="100%" stop-color="#8a3208"/>
            </radialGradient>
          </defs>
          <rect width="400" height="480" fill="#0c0c0e"/>
          <ellipse cx="200" cy="430" rx="90" ry="12" fill="#000" opacity="0.4"/>
          <circle cx="200" cy="330" r="80" fill="url(#ballGrad)"/>
          <path d="M200 250 L200 410 M120 330 L280 330" stroke="#1a0a02" stroke-width="3"/>
          <path d="M140 270 Q170 310 140 390" fill="none" stroke="#1a0a02" stroke-width="3"/>
          <path d="M260 270 Q230 310 260 390" fill="none" stroke="#1a0a02" stroke-width="3"/>
        </svg>
      </div>
      <div class="mode-fade"></div>
      <div class="mode-body">
        <div class="mode-tag">Mode 03</div>
        <div class="mode-name">Quick Match</div>
        <p class="mode-desc">Drop in, pick a team, and play. One quarter, full intensity — perfect for a fast run between classes.</p>
      </div>
    </div>

  </div>
</section>

<!-- ===================== PAGE 4 — REVIEWS & COMMUNITY ===================== -->
<section class="community" id="community">
  <div class="community-head">
    <div class="eyebrow">From the community</div>
    <h2 class="display-xl">Players Are<br>Talking</h2>
  </div>

  <div class="reviews-row">
    <div class="review-card">
      <div class="review-stars">★★★★★</div>
      <p class="review-quote">The gameplay feels actually responsive — crossovers connect the way you'd expect, not on a delay.</p>
      <div class="review-author"><span class="dot"></span>@courtside_dre</div>
    </div>
    <div class="review-card">
      <div class="review-stars">★★★★★</div>
      <p class="review-quote">Season mode is the deepest I've played. Trade logic actually makes sense for once.</p>
      <div class="review-author"><span class="dot"></span>@hoopsdaily</div>
    </div>
    <div class="review-card">
      <div class="review-stars">★★★★☆</div>
      <p class="review-quote">Tournament mode 1v1s are brutal in the best way. My go-to for a 10-minute session.</p>
      <div class="review-author"><span class="dot"></span>@rim_runner</div>
    </div>
  </div>

  <footer class="footer">
    <div class="footer-inner">
      <div class="footer-cta">
        <div class="eyebrow">Get in touch</div>
        <h3>Contact Us</h3>
        <p>Questions, feedback, or just want to talk hoops? Drop your email and we'll get back to you.</p>
        <form class="footer-form" onsubmit="return false;">
          <input type="email" placeholder="your@email.com" aria-label="Email address" required>
          <button class="btn-primary" type="submit">Send</button>
        </form>
      </div>
      <div class="footer-social">
        <div class="social-list">
          <a class="social-item" href="#" aria-label="Instagram">
            <span class="social-icon">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6"><rect x="3" y="3" width="18" height="18" rx="5"/><circle cx="12" cy="12" r="4"/><circle cx="17.5" cy="6.5" r="1"/></svg>
            </span>
            <span class="social-handle">@Pro-hoops</span>
          </a>
          <a class="social-item" href="#" aria-label="Facebook">
            <span class="social-icon">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6"><path d="M16 8h-2a3 3 0 0 0-3 3v2H9v3h2v6h3v-6h2.5l.5-3H14v-1.5a1 1 0 0 1 1-1H16z"/></svg>
            </span>
            <span class="social-handle">@Pro-hoops</span>
          </a>
          <a class="social-item" href="#" aria-label="Gmail">
            <span class="social-icon">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6"><rect x="3" y="5" width="18" height="14" rx="2"/><path d="M3 7l9 6 9-6"/></svg>
            </span>
            <span class="social-handle">@Pro-hoops</span>
          </a>
        </div>
      </div>
    </div>
    <div class="footer-bottom">
      <span>© 2026 Pro Hoops. All rights reserved.</span>
      <span>Made for the love of the game</span>
    </div>
  </footer>
</section>

<script>
  // scroll-reveal for feature/mode/review blocks
  const revealTargets = document.querySelectorAll('.feat-text, .feat-visual, .mode-card, .review-card, .modes-head, .community-head');
  revealTargets.forEach(el => el.classList.add('reveal'));

  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if(entry.isIntersecting){
        entry.target.classList.add('in');
      }
    });
  }, { threshold: 0.15 });

  revealTargets.forEach(el => observer.observe(el));
</script>

</body>
</html>
