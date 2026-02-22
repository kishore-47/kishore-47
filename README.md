<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Kishore Anand — GitHub Profile</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;500;600;700&family=Space+Grotesk:wght@300;400;500;600;700&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #060810;
    --surface: #0d1117;
    --surface2: #111827;
    --surface3: #1a2234;
    --border: #1f2937;
    --border2: #2d3748;
    --text: #e2e8f0;
    --muted: #6b7280;
    --muted2: #9ca3af;
    --accent: #38bdf8;
    --accent2: #818cf8;
    --accent3: #34d399;
    --glow: rgba(56,189,248,0.15);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Space Grotesk', sans-serif;
    overflow-x: hidden;
    cursor: none;
  }

  /* CUSTOM CURSOR */
  .cursor {
    width: 10px; height: 10px;
    background: var(--accent);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9999;
    transition: transform 0.1s ease;
    box-shadow: 0 0 12px var(--accent);
  }
  .cursor-ring {
    width: 36px; height: 36px;
    border: 1px solid rgba(56,189,248,0.4);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9998;
    transition: all 0.15s ease;
  }

  /* GRID BACKGROUND */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image:
      linear-gradient(rgba(56,189,248,0.025) 1px, transparent 1px),
      linear-gradient(90deg, rgba(56,189,248,0.025) 1px, transparent 1px);
    background-size: 60px 60px;
    pointer-events: none;
    z-index: 0;
  }

  /* NOISE OVERLAY */
  body::after {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 1;
    opacity: 0.4;
  }

  .page { position: relative; z-index: 2; max-width: 900px; margin: 0 auto; padding: 0 24px 80px; }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column;
    justify-content: center; align-items: center;
    text-align: center;
    position: relative;
    padding: 60px 0;
  }

  .hero-glow {
    position: absolute;
    width: 600px; height: 600px;
    background: radial-gradient(circle, rgba(56,189,248,0.06) 0%, transparent 70%);
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    pointer-events: none;
    animation: pulse-glow 4s ease-in-out infinite;
  }

  @keyframes pulse-glow {
    0%, 100% { opacity: 0.6; transform: translate(-50%,-50%) scale(1); }
    50% { opacity: 1; transform: translate(-50%,-50%) scale(1.1); }
  }

  .hero-tag {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    font-weight: 500;
    letter-spacing: 4px;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 24px;
    opacity: 0;
    animation: fade-up 0.8s ease 0.2s forwards;
  }

  .hero-name {
    font-family: 'JetBrains Mono', monospace;
    font-size: clamp(52px, 10vw, 96px);
    font-weight: 700;
    letter-spacing: -3px;
    line-height: 1;
    background: linear-gradient(135deg, #f9fafb 0%, #94a3b8 50%, #38bdf8 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    opacity: 0;
    animation: fade-up 0.8s ease 0.4s forwards;
    margin-bottom: 16px;
  }

  .hero-sub {
    font-size: 13px;
    font-weight: 400;
    letter-spacing: 3px;
    color: var(--muted);
    text-transform: uppercase;
    opacity: 0;
    animation: fade-up 0.8s ease 0.6s forwards;
    margin-bottom: 48px;
  }

  .hero-sub span {
    color: var(--border2);
    margin: 0 12px;
  }

  .terminal-line {
    font-family: 'JetBrains Mono', monospace;
    font-size: 13px;
    color: var(--muted);
    opacity: 0;
    animation: fade-up 0.8s ease 0.8s forwards;
  }

  .terminal-line .prompt { color: var(--accent); }
  .terminal-line .cmd { color: var(--text); }
  .terminal-cursor {
    display: inline-block;
    width: 8px; height: 14px;
    background: var(--accent);
    vertical-align: middle;
    animation: blink 1s steps(1) infinite;
  }
  @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0; } }

  .scroll-hint {
    position: absolute;
    bottom: 32px;
    display: flex; flex-direction: column; align-items: center; gap: 8px;
    opacity: 0;
    animation: fade-up 1s ease 1.5s forwards;
  }
  .scroll-hint span {
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    letter-spacing: 3px;
    color: var(--muted);
    text-transform: uppercase;
  }
  .scroll-arrow {
    width: 20px; height: 20px;
    border-right: 1px solid var(--muted);
    border-bottom: 1px solid var(--muted);
    transform: rotate(45deg);
    animation: scroll-bounce 1.5s ease infinite;
  }
  @keyframes scroll-bounce {
    0%, 100% { transform: rotate(45deg) translateY(0); opacity: 0.4; }
    50% { transform: rotate(45deg) translateY(6px); opacity: 1; }
  }

  @keyframes fade-up {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ── SECTION LAYOUT ── */
  .section { margin-bottom: 80px; }

  .section-header {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 40px;
    opacity: 0;
    transform: translateY(20px);
    transition: all 0.6s ease;
  }
  .section-header.visible { opacity: 1; transform: none; }

  .section-num {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 2px;
  }
  .section-title {
    font-family: 'JetBrains Mono', monospace;
    font-size: 13px;
    font-weight: 600;
    letter-spacing: 4px;
    text-transform: uppercase;
    color: var(--text);
  }
  .section-line {
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border2), transparent);
  }

  /* ── ABOUT CARD ── */
  .about-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 2px;
    padding: 0;
    overflow: hidden;
    opacity: 0;
    transform: translateY(20px);
    transition: all 0.6s ease 0.1s;
    position: relative;
  }
  .about-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--accent), transparent);
  }
  .about-card.visible { opacity: 1; transform: none; }

  .card-topbar {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 14px 20px;
    border-bottom: 1px solid var(--border);
    background: var(--surface2);
  }
  .dot { width: 10px; height: 10px; border-radius: 50%; }
  .dot.red { background: #ff5f57; }
  .dot.yellow { background: #ffbd2e; }
  .dot.green { background: #28c840; }
  .card-filename {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--muted);
    margin-left: 8px;
    letter-spacing: 1px;
  }

  .code-block {
    padding: 28px 32px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 13px;
    line-height: 2;
  }

  .code-row { display: flex; align-items: baseline; gap: 0; }
  .ln { color: var(--border2); min-width: 32px; font-size: 11px; user-select: none; }
  .key { color: #818cf8; }
  .colon { color: var(--muted2); }
  .str { color: #34d399; }
  .arr { color: var(--accent); }
  .punc { color: var(--muted2); }
  .comment { color: var(--border2); font-style: italic; }

  /* ── STATS ── */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
    opacity: 0;
    transform: translateY(20px);
    transition: all 0.6s ease;
  }
  .stats-row.visible { opacity: 1; transform: none; }

  .stat-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 2px;
    padding: 28px 24px;
    text-align: center;
    position: relative;
    overflow: hidden;
    transition: border-color 0.3s ease, transform 0.3s ease;
    cursor: default;
  }
  .stat-card::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    transform: scaleX(0);
    transition: transform 0.3s ease;
  }
  .stat-card:hover { border-color: var(--border2); transform: translateY(-4px); }
  .stat-card:hover::after { transform: scaleX(1); }

  .stat-num {
    font-family: 'JetBrains Mono', monospace;
    font-size: 36px;
    font-weight: 700;
    background: linear-gradient(135deg, var(--text), var(--accent));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    display: block;
    margin-bottom: 6px;
  }
  .stat-label {
    font-size: 10px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--muted);
    font-weight: 500;
  }

  /* ── TECH GRID ── */
  .tech-grid {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 12px;
    opacity: 0;
    transform: translateY(20px);
    transition: all 0.6s ease;
  }
  .tech-grid.visible { opacity: 1; transform: none; }

  .tech-item {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 2px;
    padding: 20px 12px 16px;
    display: flex; flex-direction: column;
    align-items: center; gap: 10px;
    transition: all 0.3s ease;
    cursor: default;
    position: relative;
    overflow: hidden;
  }
  .tech-item::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, var(--glow), transparent);
    opacity: 0;
    transition: opacity 0.3s ease;
  }
  .tech-item:hover { border-color: var(--border2); transform: translateY(-4px); box-shadow: 0 12px 32px rgba(0,0,0,0.4); }
  .tech-item:hover::before { opacity: 1; }

  .tech-icon { font-size: 28px; line-height: 1; }
  .tech-name {
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    color: var(--muted);
    letter-spacing: 1px;
    text-align: center;
  }

  /* ── SKILLS ── */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
    opacity: 0;
    transform: translateY(20px);
    transition: all 0.6s ease;
  }
  .skills-grid.visible { opacity: 1; transform: none; }

  .skill-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 2px;
    padding: 28px 24px;
    transition: border-color 0.3s ease;
  }
  .skill-card:hover { border-color: var(--border2); }

  .skill-title {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 20px;
    padding-bottom: 14px;
    border-bottom: 1px solid var(--border);
  }
  .skill-title.net { color: var(--accent); }
  .skill-title.code { color: var(--accent2); }
  .skill-title.data { color: var(--accent3); }

  .skill-item {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 7px 0;
    font-size: 12px;
    color: var(--muted2);
    font-family: 'JetBrains Mono', monospace;
    border-bottom: 1px solid rgba(31,41,55,0.5);
    transition: color 0.2s ease;
  }
  .skill-item:last-child { border-bottom: none; }
  .skill-item:hover { color: var(--text); }
  .skill-dot { width: 4px; height: 4px; border-radius: 50%; flex-shrink: 0; }
  .skill-dot.net { background: var(--accent); }
  .skill-dot.code { background: var(--accent2); }
  .skill-dot.data { background: var(--accent3); }

  /* ── CONTACT ── */
  .connect-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 12px;
    opacity: 0;
    transform: translateY(20px);
    transition: all 0.6s ease;
  }
  .connect-grid.visible { opacity: 1; transform: none; }

  .connect-link {
    display: flex;
    align-items: center;
    gap: 16px;
    padding: 20px 24px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 2px;
    text-decoration: none;
    color: var(--muted2);
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    letter-spacing: 1px;
    transition: all 0.3s ease;
    position: relative;
    overflow: hidden;
  }
  .connect-link::before {
    content: '';
    position: absolute;
    left: 0; top: 0; bottom: 0;
    width: 2px;
    transform: scaleY(0);
    transition: transform 0.3s ease;
  }
  .connect-link.gmail::before { background: #EA4335; }
  .connect-link.linkedin::before { background: #0A66C2; }
  .connect-link.leetcode::before { background: #FFA116; }
  .connect-link.github::before { background: #ffffff; }
  .connect-link.instagram::before { background: #E4405F; }

  .connect-link:hover { border-color: var(--border2); color: var(--text); transform: translateX(4px); }
  .connect-link:hover::before { transform: scaleY(1); }

  .connect-icon { font-size: 20px; }
  .connect-info { display: flex; flex-direction: column; gap: 2px; }
  .connect-platform { font-size: 10px; letter-spacing: 3px; text-transform: uppercase; color: var(--muted); }
  .connect-handle { font-size: 12px; color: inherit; }

  /* ── FOOTER ── */
  .footer {
    text-align: center;
    padding: 60px 0 20px;
    border-top: 1px solid var(--border);
    opacity: 0;
    transform: translateY(20px);
    transition: all 0.6s ease;
  }
  .footer.visible { opacity: 1; transform: none; }
  .footer-quote {
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--muted);
    letter-spacing: 2px;
    margin-bottom: 24px;
  }
  .footer-quote em { color: var(--muted2); font-style: normal; }
  .footer-views {
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--border2);
  }

  /* ANIMATIONS */
  @keyframes counter { from { opacity: 0; } to { opacity: 1; } }

  /* SCROLLBAR */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--border2); border-radius: 2px; }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursor-ring"></div>

<div class="page">

  <!-- ══ HERO ══ -->
  <section class="hero">
    <div class="hero-glow"></div>
    <div class="hero-tag">github.com / kishore-47</div>
    <h1 class="hero-name">KISHORE<br/>ANAND</h1>
    <p class="hero-sub">
      Network Engineer <span>·</span> Developer <span>·</span> Problem Solver
    </p>
    <div class="terminal-line">
      <span class="prompt">~/kishore-47 </span>
      <span class="cmd">$ ./initialize --mode full-stack --focus networking</span>
      <span class="terminal-cursor"></span>
    </div>
    <div class="scroll-hint">
      <span>scroll</span>
      <div class="scroll-arrow"></div>
    </div>
  </section>

  <!-- ══ ABOUT ══ -->
  <section class="section">
    <div class="section-header">
      <span class="section-num">01</span>
      <span class="section-title">About</span>
      <div class="section-line"></div>
    </div>

    <div class="about-card">
      <div class="card-topbar">
        <div class="dot red"></div>
        <div class="dot yellow"></div>
        <div class="dot green"></div>
        <span class="card-filename">profile.json</span>
      </div>
      <div class="code-block">
        <div class="code-row"><span class="ln">1</span><span class="punc">{</span></div>
        <div class="code-row"><span class="ln">2</span>&nbsp;&nbsp;<span class="key">"name"</span><span class="colon">:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="str">"Kishore Anand"</span><span class="punc">,</span></div>
        <div class="code-row"><span class="ln">3</span>&nbsp;&nbsp;<span class="key">"role"</span><span class="colon">:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="str">"Aspiring Network Engineer &amp; Developer"</span><span class="punc">,</span></div>
        <div class="code-row"><span class="ln">4</span>&nbsp;&nbsp;<span class="key">"location"</span><span class="colon">:&nbsp;&nbsp;</span><span class="str">"India"</span><span class="punc">,</span></div>
        <div class="code-row"><span class="ln">5</span>&nbsp;&nbsp;<span class="key">"focus"</span><span class="colon">:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="arr">[</span> <span class="str">"Networking"</span><span class="punc">,</span> <span class="str">"Full Stack"</span><span class="punc">,</span> <span class="str">"DSA"</span><span class="punc">,</span> <span class="str">"Data Analysis"</span> <span class="arr">]</span><span class="punc">,</span></div>
        <div class="code-row"><span class="ln">6</span>&nbsp;&nbsp;<span class="key">"languages"</span><span class="colon">: </span><span class="arr">[</span> <span class="str">"C"</span><span class="punc">,</span> <span class="str">"Java"</span><span class="punc">,</span> <span class="str">"Python"</span><span class="punc">,</span> <span class="str">"SQL"</span> <span class="arr">]</span><span class="punc">,</span></div>
        <div class="code-row"><span class="ln">7</span>&nbsp;&nbsp;<span class="key">"practice"</span><span class="colon">:  </span><span class="str">"LeetCode — daily, no off days"</span><span class="punc">,</span></div>
        <div class="code-row"><span class="ln">8</span>&nbsp;&nbsp;<span class="key">"contact"</span><span class="colon">:&nbsp;&nbsp;&nbsp;</span><span class="str">"mannai.kishore7@gmail.com"</span><span class="punc">,</span></div>
        <div class="code-row"><span class="ln">9</span>&nbsp;&nbsp;<span class="key">"motto"</span><span class="colon">:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="str">"Consistency beats talent."</span></div>
        <div class="code-row"><span class="ln">10</span><span class="punc">}</span></div>
      </div>
    </div>
  </section>

  <!-- ══ STATS ══ -->
  <section class="section">
    <div class="section-header">
      <span class="section-num">02</span>
      <span class="section-title">At a Glance</span>
      <div class="section-line"></div>
    </div>
    <div class="stats-row">
      <div class="stat-card">
        <span class="stat-num" data-count="4">0</span>
        <span class="stat-label">Languages</span>
      </div>
      <div class="stat-card">
        <span class="stat-num" data-count="365">0</span>
        <span class="stat-label">Days / Year Grinding</span>
      </div>
      <div class="stat-card">
        <span class="stat-num" data-count="6">0</span>
        <span class="stat-label">Domains Explored</span>
      </div>
    </div>
  </section>

  <!-- ══ STACK ══ -->
  <section class="section">
    <div class="section-header">
      <span class="section-num">03</span>
      <span class="section-title">Tech Stack</span>
      <div class="section-line"></div>
    </div>
    <div class="tech-grid">
      <div class="tech-item"><div class="tech-icon">⚙️</div><div class="tech-name">C</div></div>
      <div class="tech-item"><div class="tech-icon">☕</div><div class="tech-name">Java</div></div>
      <div class="tech-item"><div class="tech-icon">🐍</div><div class="tech-name">Python</div></div>
      <div class="tech-item"><div class="tech-icon">🌐</div><div class="tech-name">HTML5</div></div>
      <div class="tech-item"><div class="tech-icon">🎨</div><div class="tech-name">CSS3</div></div>
      <div class="tech-item"><div class="tech-icon">💚</div><div class="tech-name">Node.js</div></div>
      <div class="tech-item"><div class="tech-icon">🚂</div><div class="tech-name">Express</div></div>
      <div class="tech-item"><div class="tech-icon">🗃️</div><div class="tech-name">SQLite</div></div>
      <div class="tech-item"><div class="tech-icon">🔧</div><div class="tech-name">Git</div></div>
      <div class="tech-item"><div class="tech-icon">🐧</div><div class="tech-name">Linux</div></div>
      <div class="tech-item"><div class="tech-icon">💻</div><div class="tech-name">VS Code</div></div>
      <div class="tech-item"><div class="tech-icon">📊</div><div class="tech-name">Power BI</div></div>
      <div class="tech-item"><div class="tech-icon">🎯</div><div class="tech-name">Figma</div></div>
      <div class="tech-item"><div class="tech-icon">🔵</div><div class="tech-name">Cisco</div></div>
    </div>
  </section>

  <!-- ══ SKILLS ══ -->
  <section class="section">
    <div class="section-header">
      <span class="section-num">04</span>
      <span class="section-title">Domain Knowledge</span>
      <div class="section-line"></div>
    </div>
    <div class="skills-grid">
      <div class="skill-card">
        <div class="skill-title net">[ Networking ]</div>
        <div class="skill-item"><div class="skill-dot net"></div>OSI &amp; TCP/IP Models</div>
        <div class="skill-item"><div class="skill-dot net"></div>Subnetting &amp; CIDR</div>
        <div class="skill-item"><div class="skill-dot net"></div>Routing &amp; Switching</div>
        <div class="skill-item"><div class="skill-dot net"></div>VLANs &amp; Trunking</div>
        <div class="skill-item"><div class="skill-dot net"></div>DNS · DHCP · HTTP/S</div>
        <div class="skill-item"><div class="skill-dot net"></div>Packet Tracer Labs</div>
        <div class="skill-item"><div class="skill-dot net"></div>Network Troubleshooting</div>
      </div>
      <div class="skill-card">
        <div class="skill-title code">[ Programming ]</div>
        <div class="skill-item"><div class="skill-dot code"></div>Data Structures</div>
        <div class="skill-item"><div class="skill-dot code"></div>Algorithms &amp; Complexity</div>
        <div class="skill-item"><div class="skill-dot code"></div>OOP Principles</div>
        <div class="skill-item"><div class="skill-dot code"></div>REST API Design</div>
        <div class="skill-item"><div class="skill-dot code"></div>Full Stack (MERN-lite)</div>
        <div class="skill-item"><div class="skill-dot code"></div>LeetCode Problem Solving</div>
        <div class="skill-item"><div class="skill-dot code"></div>Version Control · Git</div>
      </div>
      <div class="skill-card">
        <div class="skill-title data">[ Data ]</div>
        <div class="skill-item"><div class="skill-dot data"></div>Python (Pandas, NumPy)</div>
        <div class="skill-item"><div class="skill-dot data"></div>SQL Queries &amp; Joins</div>
        <div class="skill-item"><div class="skill-dot data"></div>Excel &amp; PivotTables</div>
        <div class="skill-item"><div class="skill-dot data"></div>Power BI Dashboards</div>
        <div class="skill-item"><div class="skill-dot data"></div>Data Visualization</div>
        <div class="skill-item"><div class="skill-dot data"></div>Analytical Reporting</div>
        <div class="skill-item"><div class="skill-dot data"></div>KPI Tracking</div>
      </div>
    </div>
  </section>

  <!-- ══ CONNECT ══ -->
  <section class="section">
    <div class="section-header">
      <span class="section-num">05</span>
      <span class="section-title">Connect</span>
      <div class="section-line"></div>
    </div>
    <div class="connect-grid">
      <a href="mailto:mannai.kishore7@gmail.com" class="connect-link gmail">
        <span class="connect-icon">📧</span>
        <div class="connect-info">
          <span class="connect-platform">Email</span>
          <span class="connect-handle">mannai.kishore7@gmail.com</span>
        </div>
      </a>
      <a href="https://www.linkedin.com/in/kishoreanand47" class="connect-link linkedin" target="_blank">
        <span class="connect-icon">💼</span>
        <div class="connect-info">
          <span class="connect-platform">LinkedIn</span>
          <span class="connect-handle">kishoreanand47</span>
        </div>
      </a>
      <a href="https://leetcode.com/u/Kishore-47/" class="connect-link leetcode" target="_blank">
        <span class="connect-icon">🔥</span>
        <div class="connect-info">
          <span class="connect-platform">LeetCode</span>
          <span class="connect-handle">@Kishore-47</span>
        </div>
      </a>
      <a href="https://github.com/kishore-47" class="connect-link github" target="_blank">
        <span class="connect-icon">🐙</span>
        <div class="connect-info">
          <span class="connect-platform">GitHub</span>
          <span class="connect-handle">@kishore-47</span>
        </div>
      </a>
      <a href="https://instagram.com/_kishore_47__" class="connect-link instagram" target="_blank">
        <span class="connect-icon">📸</span>
        <div class="connect-info">
          <span class="connect-platform">Instagram</span>
          <span class="connect-handle">_kishore_47__</span>
        </div>
      </a>
    </div>
  </section>

  <!-- ══ FOOTER ══ -->
  <footer class="footer">
    <p class="footer-quote"><em>"</em> The expert in anything was once a beginner. <em>"</em></p>
    <p class="footer-views">consistency · discipline · growth</p>
  </footer>

</div>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursor-ring');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.left = mx - 5 + 'px';
    cursor.style.top = my - 5 + 'px';
  });
  function animateRing() {
    rx += (mx - rx - 18) * 0.15;
    ry += (my - ry - 18) * 0.15;
    ring.style.left = rx + 'px';
    ring.style.top = ry + 'px';
    requestAnimationFrame(animateRing);
  }
  animateRing();

  // Scroll reveal
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) e.target.classList.add('visible');
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.section-header, .about-card, .stats-row, .tech-grid, .skills-grid, .connect-grid, .footer').forEach(el => observer.observe(el));

  // Counter animation
  const counters = document.querySelectorAll('[data-count]');
  const counterObserver = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        const el = e.target;
        const target = parseInt(el.dataset.count);
        const suffix = target === 365 ? '' : '';
        let current = 0;
        const step = Math.ceil(target / 40);
        const timer = setInterval(() => {
          current = Math.min(current + step, target);
          el.textContent = current + (target === 365 ? '' : '');
          if (current >= target) clearInterval(timer);
        }, 30);
        counterObserver.unobserve(el);
      }
    });
  }, { threshold: 0.5 });
  counters.forEach(c => counterObserver.observe(c));
</script>
</body>
</html>
