<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>GitHub Profile Preview</title>
<link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@300;400;500;600&family=JetBrains+Mono:wght@300;400;700&display=swap" rel="stylesheet"/>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0d1117;
    --bg2: #161b22;
    --border: #21262d;
    --green: #00ff88;
    --green-dim: #00cc6a;
    --text: #c9d1d9;
    --muted: #8b949e;
    --code-bg: #010409;
  }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Fira Code', monospace;
    min-height: 100vh;
    padding: 0;
    overflow-x: hidden;
  }

  /* HEADER WAVE */
  .header-wave {
    width: 100%;
    background: linear-gradient(180deg, #0a0a0a 0%, #001a0e 50%, #0d1117 100%);
    padding: 48px 24px 40px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .header-wave::before {
    content: '';
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse 80% 60% at 50% 0%, rgba(0,255,136,0.12) 0%, transparent 70%),
      repeating-linear-gradient(90deg, transparent, transparent 80px, rgba(0,255,136,0.03) 80px, rgba(0,255,136,0.03) 81px),
      repeating-linear-gradient(0deg, transparent, transparent 80px, rgba(0,255,136,0.03) 80px, rgba(0,255,136,0.03) 81px);
  }
  .header-wave::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 40px;
    background: linear-gradient(to bottom, transparent, var(--bg));
  }
  .header-name {
    font-family: 'JetBrains Mono', monospace;
    font-size: clamp(36px, 6vw, 64px);
    font-weight: 700;
    color: var(--green);
    letter-spacing: -1px;
    position: relative;
    text-shadow: 0 0 40px rgba(0,255,136,0.4), 0 0 80px rgba(0,255,136,0.15);
    animation: flicker 4s infinite;
  }
  @keyframes flicker {
    0%,95%,100% { opacity: 1; }
    96% { opacity: 0.85; }
    97% { opacity: 1; }
    98% { opacity: 0.9; }
  }
  .header-sub {
    color: var(--muted);
    font-size: 15px;
    margin-top: 8px;
    letter-spacing: 2px;
    text-transform: uppercase;
    position: relative;
  }

  /* TYPING */
  .typing-wrapper {
    text-align: center;
    padding: 24px 16px 8px;
  }
  .typing-text {
    font-size: 17px;
    color: var(--green);
    display: inline-block;
  }
  .typing-cursor {
    animation: blink 1s infinite;
    color: var(--green);
  }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

  /* DIVIDER */
  .divider {
    border: none;
    border-top: 1px solid var(--border);
    margin: 28px auto;
    max-width: 800px;
    position: relative;
  }
  .divider::before {
    content: '// ';
    position: absolute;
    left: 50%;
    top: -10px;
    transform: translateX(-50%);
    background: var(--bg);
    padding: 0 12px;
    color: var(--green);
    font-size: 12px;
  }

  /* CONTAINER */
  .container {
    max-width: 860px;
    margin: 0 auto;
    padding: 0 24px 60px;
  }

  /* CODE BLOCK */
  .code-block {
    background: var(--code-bg);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 24px 28px;
    margin: 24px 0;
    position: relative;
    overflow: hidden;
    animation: slideUp 0.6s ease both;
  }
  .code-block::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--green), transparent);
  }
  .code-dots {
    display: flex;
    gap: 6px;
    margin-bottom: 16px;
  }
  .dot { width: 12px; height: 12px; border-radius: 50%; }
  .dot-r { background: #ff5f57; }
  .dot-y { background: #febc2e; }
  .dot-g { background: #28c840; }
  .code-content {
    font-family: 'Fira Code', monospace;
    font-size: 13.5px;
    line-height: 1.8;
    white-space: pre;
  }
  .kw  { color: #ff7b72; }
  .fn  { color: #d2a8ff; }
  .str { color: #a5d6ff; }
  .cmt { color: #484f58; font-style: italic; }
  .grn { color: var(--green); }
  .num { color: #f0883e; }
  .wh  { color: var(--text); }

  /* SECTION TITLES */
  .section-title {
    text-align: center;
    margin: 40px 0 24px;
    font-size: 20px;
    color: var(--green);
    letter-spacing: 1px;
  }
  .section-title span { color: var(--muted); font-size: 14px; display: block; margin-top: 4px; }

  /* TECH GRID */
  .tech-category {
    margin: 20px 0;
  }
  .tech-label {
    font-size: 12px;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 2px;
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .tech-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }
  .tech-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }
  .pill {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 6px 14px;
    border-radius: 6px;
    font-size: 12.5px;
    font-weight: 500;
    border: 1px solid;
    transition: all 0.2s;
    cursor: default;
    animation: fadeIn 0.4s ease both;
  }
  .pill:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 16px rgba(0,255,136,0.2);
  }
  .pill-ai   { color: #00ff88; border-color: #00ff8840; background: #00ff8808; }
  .pill-web  { color: #61dafb; border-color: #61dafb40; background: #61dafb08; }
  .pill-dev  { color: #f0883e; border-color: #f0883e40; background: #f0883e08; }
  .pill-dot  { width: 7px; height: 7px; border-radius: 50%; background: currentColor; box-shadow: 0 0 6px currentColor; }

  /* STATS GRID */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 16px;
    margin: 24px 0;
  }
  .stat-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 20px;
    text-align: center;
    position: relative;
    overflow: hidden;
    transition: all 0.3s;
    animation: slideUp 0.5s ease both;
  }
  .stat-card:hover {
    border-color: var(--green);
    box-shadow: 0 0 24px rgba(0,255,136,0.1);
    transform: translateY(-2px);
  }
  .stat-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: var(--green);
    transform: scaleX(0);
    transition: transform 0.3s;
  }
  .stat-card:hover::before { transform: scaleX(1); }
  .stat-number {
    font-size: 32px;
    font-weight: 700;
    color: var(--green);
    text-shadow: 0 0 20px rgba(0,255,136,0.4);
    font-family: 'JetBrains Mono', monospace;
  }
  .stat-label { color: var(--muted); font-size: 12px; margin-top: 4px; letter-spacing: 1px; }

  /* STREAK BAR */
  .streak-section {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 24px;
    margin: 16px 0;
  }
  .streak-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 16px; }
  .streak-title { color: var(--green); font-size: 14px; }
  .streak-count { font-size: 28px; font-weight: 700; color: var(--green); font-family: 'JetBrains Mono'; }
  .bar-track { height: 6px; background: var(--border); border-radius: 3px; overflow: hidden; }
  .bar-fill { height: 100%; border-radius: 3px; background: linear-gradient(90deg, var(--green-dim), var(--green)); animation: grow 1.2s ease both; }
  @keyframes grow { from { width: 0 } }

  /* CONTRIB GRID */
  .contrib-grid {
    display: grid;
    grid-template-columns: repeat(52, 1fr);
    gap: 2px;
    margin: 16px 0;
    overflow: hidden;
  }
  .contrib-cell {
    aspect-ratio: 1;
    border-radius: 2px;
    animation: cellPop 0.05s ease both;
  }
  .c0 { background: var(--border); }
  .c1 { background: #0e4429; }
  .c2 { background: #006d32; }
  .c3 { background: #26a641; }
  .c4 { background: #39d353; }

  /* CONNECT */
  .connect-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    justify-content: center;
    margin: 24px 0;
  }
  .badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 8px 18px;
    border-radius: 6px;
    font-size: 13px;
    font-weight: 600;
    text-decoration: none;
    color: white;
    transition: all 0.2s;
    letter-spacing: 0.5px;
  }
  .badge:hover { transform: translateY(-2px); filter: brightness(1.2); box-shadow: 0 4px 20px rgba(0,0,0,0.4); }
  .badge-li   { background: #0A66C2; }
  .badge-tw   { background: #1DA1F2; }
  .badge-port { background: #00cc6a; color: #000; }
  .badge-mail { background: #EA4335; }

  /* VISITORS */
  .visitors {
    text-align: center;
    margin-top: 16px;
    font-size: 12px;
    color: var(--muted);
    letter-spacing: 2px;
  }
  .visitors strong { color: var(--green); }

  /* FOOTER WAVE */
  .footer-wave {
    width: 100%;
    height: 80px;
    background: linear-gradient(180deg, var(--bg) 0%, #001a0e 50%, #0a0a0a 100%);
    margin-top: 40px;
    position: relative;
    overflow: hidden;
  }
  .footer-wave::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(ellipse 80% 150% at 50% 100%, rgba(0,255,136,0.1) 0%, transparent 70%);
  }

  @keyframes slideUp { from { opacity:0; transform:translateY(20px) } to { opacity:1; transform:translateY(0) } }
  @keyframes fadeIn  { from { opacity:0 } to { opacity:1 } }

  /* SCANLINE EFFECT */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0,0,0,0.05) 2px, rgba(0,0,0,0.05) 4px);
    pointer-events: none;
    z-index: 999;
  }
</style>
</head>
<body>

<!-- HEADER -->
<div class="header-wave">
  <div class="header-name" id="headerName">Muhammad Umar Farooq</div>
  <div class="header-sub">AI Engineer &nbsp;|&nbsp; Web Developer</div>
</div>

<!-- TYPING -->
<div class="typing-wrapper">
  <span class="typing-text" id="typingEl"></span><span class="typing-cursor">█</span>
</div>

<div class="container">
  <hr class="divider"/>

  <!-- CODE BLOCK -->
  <div class="code-block">
    <div class="code-dots">
      <div class="dot dot-r"></div><div class="dot dot-y"></div><div class="dot dot-g"></div>
    </div>
    <div class="code-content"><span class="kw">class</span> <span class="fn">AIEngineer</span><span class="wh">:</span>
  <span class="kw">def</span> <span class="fn">__init__</span><span class="wh">(</span><span class="grn">self</span><span class="wh">):</span>
    <span class="grn">self</span><span class="wh">.name</span>       <span class="wh">=</span> <span class="str">"YOUR_NAME"</span>
    <span class="grn">self</span><span class="wh">.username</span>   <span class="wh">=</span> <span class="str">"@YOUR_USERNAME"</span>
    <span class="grn">self</span><span class="wh">.role</span>       <span class="wh">=</span> <span class="wh">[</span><span class="str">"AI Engineer"</span><span class="wh">,</span> <span class="str">"Full-Stack Developer"</span><span class="wh">]</span>
    <span class="grn">self</span><span class="wh">.languages</span>  <span class="wh">=</span> <span class="wh">[</span><span class="str">"Python"</span><span class="wh">,</span> <span class="str">"JavaScript"</span><span class="wh">,</span> <span class="str">"TypeScript"</span><span class="wh">,</span> <span class="str">"SQL"</span><span class="wh">]</span>
    <span class="grn">self</span><span class="wh">.interests</span>  <span class="wh">=</span> <span class="wh">[</span><span class="str">"LLMs"</span><span class="wh">,</span> <span class="str">"MLOps"</span><span class="wh">,</span> <span class="str">"System Design"</span><span class="wh">,</span> <span class="str">"Open Source"</span><span class="wh">]</span>
    <span class="grn">self</span><span class="wh">.currently</span>  <span class="wh">=</span> <span class="str">"Building something the world hasn't seen yet 🚀"</span>

  <span class="kw">def</span> <span class="fn">say_hi</span><span class="wh">(</span><span class="grn">self</span><span class="wh">):</span>
    <span class="fn">print</span><span class="wh">(</span><span class="str">f"Hey! I'm </span><span class="wh">{</span><span class="grn">self</span><span class="wh">.name}.</span> <span class="str">Let's build something extraordinary."</span><span class="wh">)</span>

<span class="wh">me</span> <span class="wh">=</span> <span class="fn">AIEngineer</span><span class="wh">()</span>
<span class="wh">me</span><span class="wh">.</span><span class="fn">say_hi</span><span class="wh">()</span>
<span class="cmt">## → Hey! I'm YOUR_NAME. Let's build something extraordinary.</span></div>
  </div>

  <hr class="divider"/>

  <!-- TECH STACK -->
  <div class="section-title">⚡ Tech Arsenal</div>

  <div class="tech-category">
    <div class="tech-label">🤖 AI / Machine Learning</div>
    <div class="tech-pills">
      <span class="pill pill-ai"><span class="pill-dot"></span>Python</span>
      <span class="pill pill-ai"><span class="pill-dot"></span>TensorFlow</span>
      <span class="pill pill-ai"><span class="pill-dot"></span>PyTorch</span>
      <span class="pill pill-ai"><span class="pill-dot"></span>scikit-learn</span>
      <span class="pill pill-ai"><span class="pill-dot"></span>LangChain</span>
      <span class="pill pill-ai"><span class="pill-dot"></span>OpenCV</span>
      <span class="pill pill-ai"><span class="pill-dot"></span>Jupyter</span>
    </div>
  </div>

  <div class="tech-category">
    <div class="tech-label">🌐 Web Development</div>
    <div class="tech-pills">
      <span class="pill pill-web"><span class="pill-dot"></span>JavaScript</span>
      <span class="pill pill-web"><span class="pill-dot"></span>TypeScript</span>
      <span class="pill pill-web"><span class="pill-dot"></span>React</span>
      <span class="pill pill-web"><span class="pill-dot"></span>Next.js</span>
      <span class="pill pill-web"><span class="pill-dot"></span>Node.js</span>
      <span class="pill pill-web"><span class="pill-dot"></span>FastAPI</span>
    </div>
  </div>

  <div class="tech-category">
    <div class="tech-label">🛠 DevOps &amp; Tools</div>
    <div class="tech-pills">
      <span class="pill pill-dev"><span class="pill-dot"></span>Docker</span>
      <span class="pill pill-dev"><span class="pill-dot"></span>Git</span>
      <span class="pill pill-dev"><span class="pill-dot"></span>Linux</span>
      <span class="pill pill-dev"><span class="pill-dot"></span>PostgreSQL</span>
      <span class="pill pill-dev"><span class="pill-dot"></span>MongoDB</span>
      <span class="pill pill-dev"><span class="pill-dot"></span>Redis</span>
    </div>
  </div>

  <hr class="divider"/>

  <!-- STATS -->
  <div class="section-title">📊 GitHub Stats</div>

  <div class="stats-grid">
    <div class="stat-card">
      <div class="stat-number">142</div>
      <div class="stat-label">REPOSITORIES</div>
    </div>
    <div class="stat-card">
      <div class="stat-number">3.2k</div>
      <div class="stat-label">CONTRIBUTIONS</div>
    </div>
    <div class="stat-card">
      <div class="stat-number">847</div>
      <div class="stat-label">STARS EARNED</div>
    </div>
    <div class="stat-card">
      <div class="stat-number">94</div>
      <div class="stat-label">PULL REQUESTS</div>
    </div>
  </div>

  <!-- STREAK -->
  <div class="streak-section">
    <div class="streak-header">
      <div class="streak-title">🔥 Current Streak</div>
      <div class="streak-count">47 days</div>
    </div>
    <div class="bar-track"><div class="bar-fill" style="width:78%"></div></div>
    <div style="display:flex;justify-content:space-between;margin-top:8px;font-size:11px;color:var(--muted);">
      <span>Longest: 112 days</span><span>Total: 1,840 days</span>
    </div>
  </div>

  <hr class="divider"/>

  <!-- CONTRIBUTION GRAPH -->
  <div class="section-title">🐍 Contribution Graph</div>
  <div class="contrib-grid" id="contribGrid"></div>

  <hr class="divider"/>

  <!-- CONNECT -->
  <div class="section-title">📡 Connect</div>
  <div class="connect-grid">
    <a class="badge badge-li" href="www.linkedin.com/in/muhammadumar-farooq">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="white"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2" fill="white"/></svg>
      LinkedIn
    </a>
    <a class="badge badge-tw" href="#">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="white"><path d="M23 3a10.9 10.9 0 01-3.14 1.53 4.48 4.48 0 00-7.86 3v1A10.66 10.66 0 013 4s-4 9 5 13a11.64 11.64 0 01-7 2c9 5 20 0 20-11.5a4.5 4.5 0 00-.08-.83A7.72 7.72 0 0023 3z"/></svg>
      Twitter
    </a>
    <a class="badge badge-port" href="https://umar045-portfolio.netlify.app/">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="black"><path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"/></svg>
      Portfolio
    </a>
    <a class="badge badge-mail" href="mumarfarooqkhan45@gmail.com">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
      Email
    </a>
  </div>

  <div class="visitors">PROFILE VIEWS &nbsp;·&nbsp; <strong>∞</strong></div>
</div>

<!-- FOOTER -->
<div class="footer-wave"></div>

<script>
// TYPING ANIMATION
const lines = [
  "Building intelligent systems 🤖",
  "Crafting seamless web experiences 🌐",
  "Training models that actually work 🧠",
  "Turning coffee into code ☕"
];
let li = 0, ci = 0, deleting = false;
const el = document.getElementById('typingEl');
function type() {
  const line = lines[li];
  if (!deleting) {
    el.textContent = line.slice(0, ++ci);
    if (ci === line.length) { deleting = true; setTimeout(type, 1800); return; }
  } else {
    el.textContent = line.slice(0, --ci);
    if (ci === 0) { deleting = false; li = (li + 1) % lines.length; }
  }
  setTimeout(type, deleting ? 40 : 70);
}
type();

// CONTRIBUTION GRID
const grid = document.getElementById('contribGrid');
const weights = [0,0,0,0,1,1,2,2,3,4];
for (let i = 0; i < 52 * 7; i++) {
  const cell = document.createElement('div');
  const w = weights[Math.floor(Math.random() * weights.length)];
  cell.className = `contrib-cell c${w}`;
  cell.style.animationDelay = `${i * 2}ms`;
  grid.appendChild(cell);
}
</script>
</body>
</html>
