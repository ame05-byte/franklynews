<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Frankly</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&family=Libre+Franklin:wght@400;500;600;700;800;900&family=Cormorant+Garamond:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
  *,*::before,*::after{margin:0;padding:0;box-sizing:border-box}
 
  :root {
    --bg: #F5F0E8;
    --bg-card: #F5F0E8;
    --bg-card-alt: #EDE8DD;
    --text: #1A1A1A;
    --text-muted: #6B6560;
    --red: #CC2A1E;
    --black: #111;
    --divider: #D4CFC5;
    --nav-bg: #F5F0E8;
  }
 
  html { font-size: 16px; }
 
  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Cormorant Garamond', Georgia, serif;
    -webkit-font-smoothing: antialiased;
    min-height: 100vh;
    overflow-x: hidden;
  }
 
  /* ── HEADER ── */
  .header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 16px 20px;
    position: sticky;
    top: 0;
    z-index: 100;
    background: var(--bg);
    border-bottom: 1px solid var(--divider);
  }
 
  .logo {
    font-family: 'Playfair Display', serif;
    font-weight: 900;
    font-size: 1.65rem;
    letter-spacing: -0.02em;
    color: var(--text);
    display: flex;
    align-items: baseline;
    gap: 0;
    cursor: default;
    user-select: none;
  }
 
  .logo-h {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    background: var(--red);
    color: #fff;
    width: 32px;
    height: 38px;
    font-size: 2rem;
    font-weight: 900;
    line-height: 1;
    margin-right: 2px;
    position: relative;
    top: 2px;
  }
 
  .logo-rest {
    font-family: 'Libre Franklin', sans-serif;
    font-weight: 800;
    font-size: 1.1rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
  }
 
  .header-actions {
    display: flex;
    align-items: center;
    gap: 18px;
  }
 
  .icon-btn {
    background: none;
    border: none;
    cursor: pointer;
    padding: 6px;
    color: var(--text);
    transition: opacity 0.2s;
  }
  .icon-btn:hover { opacity: 0.6; }
  .icon-btn svg { display: block; }
 
  /* ── DATE BAR ── */
  .date-bar {
    text-align: center;
    padding: 10px 20px;
    font-family: 'Libre Franklin', sans-serif;
    font-size: 0.72rem;
    font-weight: 600;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--text-muted);
    border-bottom: 1px solid var(--divider);
  }
 
  /* ── BREAKING BANNER ── */
  .breaking-banner {
    background: var(--red);
    color: #fff;
    padding: 10px 20px;
    display: flex;
    align-items: center;
    gap: 12px;
    overflow: hidden;
  }
  .breaking-label {
    font-family: 'Libre Franklin', sans-serif;
    font-weight: 900;
    font-size: 0.7rem;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    white-space: nowrap;
    padding: 3px 10px;
    background: #fff;
    color: var(--red);
    border-radius: 2px;
    flex-shrink: 0;
  }
  .breaking-marquee {
    overflow: hidden;
    flex: 1;
  }
  .breaking-text {
    font-family: 'Libre Franklin', sans-serif;
    font-weight: 600;
    font-size: 0.82rem;
    white-space: nowrap;
    display: inline-block;
    animation: scroll-text 25s linear infinite;
  }
  @keyframes scroll-text {
    0% { transform: translateX(100%); }
    100% { transform: translateX(-100%); }
  }
 
  /* ── CATEGORY NAV ── */
  .cat-nav {
    display: flex;
    align-items: stretch;
    border-bottom: 3px solid var(--black);
    overflow-x: auto;
    scrollbar-width: none;
    -ms-overflow-style: none;
    background: var(--nav-bg);
  }
  .cat-nav::-webkit-scrollbar { display: none; }
 
  .cat-tab {
    font-family: 'Libre Franklin', sans-serif;
    font-weight: 800;
    font-size: 0.78rem;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    padding: 12px 20px;
    white-space: nowrap;
    cursor: pointer;
    border: none;
    background: transparent;
    color: var(--text);
    position: relative;
    transition: background 0.2s, color 0.2s;
    border-right: 1px solid var(--divider);
  }
 
  .cat-tab:first-child { background: var(--bg-card); }
 
  .cat-tab.active { color: var(--red); }
 
  .cat-tab.active::after {
    content: '';
    position: absolute;
    bottom: -3px;
    left: 0;
    right: 0;
    height: 3px;
    background: var(--red);
  }
 
  .cat-tab:hover { background: rgba(0,0,0,0.03); }
 
  .cat-tab .frankly {
    font-style: italic;
    font-weight: 700;
    color: var(--red);
    letter-spacing: 0.01em;
    font-family: 'Libre Franklin', sans-serif;
  }
 
  /* ── NEWS LIST ── */
  .news-list {
    max-width: 720px;
    margin: 0 auto;
    padding: 0;
  }
 
  /* ── NEWS CARD ── */
  .news-card {
    display: flex;
    align-items: flex-start;
    gap: 18px;
    padding: 28px 20px;
    border-bottom: 1px solid var(--divider);
    cursor: pointer;
    transition: background 0.25s;
    opacity: 0;
    transform: translateY(16px);
    animation: cardIn 0.5s ease forwards;
  }
 
  .news-card:nth-child(1) { animation-delay: 0.08s; }
  .news-card:nth-child(2) { animation-delay: 0.16s; }
  .news-card:nth-child(3) { animation-delay: 0.24s; }
  .news-card:nth-child(4) { animation-delay: 0.32s; }
  .news-card:nth-child(5) { animation-delay: 0.40s; }
  .news-card:nth-child(6) { animation-delay: 0.48s; }
  .news-card:nth-child(7) { animation-delay: 0.56s; }
  .news-card:nth-child(8) { animation-delay: 0.64s; }
 
  @keyframes cardIn {
    to { opacity: 1; transform: translateY(0); }
  }
 
  .news-card:hover { background: rgba(0,0,0,0.02); }
  .news-card:nth-child(even) { background: var(--bg-card-alt); }
  .news-card:nth-child(even):hover { background: #E8E3D8; }
 
  .card-thumb {
    width: 100px;
    height: 100px;
    min-width: 100px;
    border-radius: 10px;
    overflow: hidden;
    background: #ddd;
    display: flex;
    align-items: center;
    justify-content: center;
  }
 
  .card-thumb .thumb-placeholder {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
 
  .card-body { flex: 1; min-width: 0; }
 
  .card-tag {
    display: inline-block;
    font-family: 'Libre Franklin', sans-serif;
    font-weight: 800;
    font-size: 0.6rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--red);
    margin-bottom: 6px;
  }
 
  .card-headline {
    font-family: 'Playfair Display', serif;
    font-weight: 700;
    font-size: 1.3rem;
    line-height: 1.3;
    color: var(--text);
    margin-bottom: 14px;
    letter-spacing: -0.01em;
  }
 
  .card-meta {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    gap: 16px;
  }
 
  .card-source {
    font-family: 'Libre Franklin', sans-serif;
    font-weight: 700;
    font-size: 0.68rem;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: var(--text-muted);
  }
 
  .card-time {
    font-family: 'Libre Franklin', sans-serif;
    font-weight: 700;
    font-size: 0.72rem;
    color: var(--red);
    letter-spacing: 0.02em;
  }
 
  /* ── SECTION DIVIDERS ── */
  .section-bar {
    background: var(--black);
    height: 6px;
    width: 100%;
  }
 
  /* ── FOOTER ── */
  .footer {
    text-align: center;
    padding: 32px 20px;
    font-family: 'Libre Franklin', sans-serif;
    font-size: 0.7rem;
    font-weight: 600;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--text-muted);
    border-top: 3px solid var(--black);
    margin-top: 20px;
  }
 
  /* ── RESPONSIVE ── */
  @media (max-width: 480px) {
    .card-headline { font-size: 1.1rem; }
    .card-thumb { width: 80px; height: 80px; min-width: 80px; }
    .news-card { gap: 14px; padding: 22px 16px; }
    .logo-rest { font-size: 0.95rem; }
  }
 
  /* ── SUBTLE GRAIN ── */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    pointer-events: none;
    opacity: 0.025;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
    background-repeat: repeat;
    background-size: 200px 200px;
    z-index: 9999;
  }
 
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--divider); border-radius: 3px; }
</style>
</head>
<body>
 
<!-- HEADER -->
<header class="header">
  <div class="logo">
    <span class="logo-h">F</span><span class="logo-rest">rankly</span>
  </div>
  <div class="header-actions">
    <button class="icon-btn" aria-label="Search">
      <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
    </button>
    <button class="icon-btn" aria-label="Menu">
      <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round"><line x1="3" y1="6" x2="21" y2="6"/><line x1="3" y1="12" x2="21" y2="12"/><line x1="3" y1="18" x2="21" y2="18"/></svg>
    </button>
  </div>
</header>
 
<!-- DATE BAR -->
<div class="date-bar">Thursday, April 3, 2026</div>
 
<!-- BREAKING BANNER -->
<div class="breaking-banner">
  <span class="breaking-label">LIVE</span>
  <div class="breaking-marquee">
    <span class="breaking-text">Artemis II crew approaching the Moon — first humans beyond Earth orbit since 1972 &nbsp;&bull;&nbsp; U.S. employers add 178,000 jobs in March &nbsp;&bull;&nbsp; Trump proposes record $1.5 trillion defense budget &nbsp;&bull;&nbsp; Iran claims it shot down U.S. fighter jet</span>
  </div>
</div>
 
<!-- CATEGORY NAV -->
<nav class="cat-nav" id="catNav">
  <button class="cat-tab active" data-cat="new"><span class="frankly">frankly</span>NEW</button>
  <button class="cat-tab" data-cat="us">U.S</button>
  <button class="cat-tab" data-cat="world">WORLD</button>
  <button class="cat-tab" data-cat="tech">TECH</button>
  <button class="cat-tab" data-cat="science">SCIENCE</button>
  <button class="cat-tab" data-cat="business">BUSINESS</button>
</nav>
 
<!-- NEWS LIST -->
<main class="news-list" id="newsList"></main>
 
<!-- FOOTER -->
<footer class="footer">
  &copy; 2026 Frankly News &nbsp;&bull;&nbsp; All rights reserved
</footer>
 
<script>
  const articles = [
    {
      headline: "Artemis II Crew on Course for the Moon in First Crewed Deep Space Mission Since Apollo",
      tag: "SCIENCE",
      source: "FRANKLY",
      time: "2 hrs ago",
      bg: "#0B1D3A",
      icon: `<svg width="44" height="44" viewBox="0 0 44 44" fill="none"><circle cx="22" cy="22" r="16" fill="#1E3A5F"/><circle cx="22" cy="22" r="10" fill="#C0C8D4" opacity="0.9"/><circle cx="18" cy="19" r="3" fill="#A0AAB8" opacity="0.5"/><circle cx="26" cy="24" r="2" fill="#A0AAB8" opacity="0.4"/><circle cx="22" cy="16" r="1.5" fill="#A0AAB8" opacity="0.3"/></svg>`
    },
    {
      headline: "Trump Proposes Record $1.5 Trillion Defense Budget as Military Spending Reaches WWII Levels",
      tag: "U.S. POLITICS",
      source: "FRANKLY",
      time: "3 hrs ago",
      bg: "#1A1A2E",
      icon: `<svg width="40" height="40" viewBox="0 0 40 40"><rect x="8" y="16" width="24" height="16" rx="2" fill="#333952"/><polygon points="20,6 12,16 28,16" fill="#4A5580"/><rect x="18" y="20" width="4" height="8" fill="#6B7DB3" opacity="0.7"/></svg>`
    },
    {
      headline: "U.S. Economy Adds 178,000 Jobs in March as Unemployment Dips to 4.3%",
      tag: "BUSINESS",
      source: "FRANKLY",
      time: "5 hrs ago",
      bg: "#1B5E3B",
      icon: `<svg width="40" height="40" viewBox="0 0 40 40"><rect x="6" y="26" width="6" height="10" fill="#4CAF80"/><rect x="14" y="20" width="6" height="16" fill="#3D9E6E"/><rect x="22" y="14" width="6" height="22" fill="#2E8B5A"/><rect x="30" y="8" width="6" height="28" fill="#1F7A48"/></svg>`
    },
    {
      headline: "Jury Finds Meta and YouTube Liable for Harming Youth Through Addictive Platform Design",
      tag: "TECH",
      source: "FRANKLY",
      time: "6 hrs ago",
      bg: "#CC2A1E",
      icon: `<svg width="36" height="36" viewBox="0 0 36 36"><rect x="4" y="4" width="28" height="28" rx="6" fill="#E8453A"/><rect x="10" y="14" width="16" height="2" rx="1" fill="#fff"/><rect x="10" y="20" width="16" height="2" rx="1" fill="#fff"/><circle cx="13" cy="10" r="2" fill="#fff" opacity="0.6"/></svg>`
    },
    {
      headline: "Iran Claims It Shot Down U.S. Fighter Jet as Gulf Tensions Escalate",
      tag: "WORLD",
      source: "FRANKLY",
      time: "4 hrs ago",
      bg: "#3A1A0A",
      icon: `<svg width="40" height="40" viewBox="0 0 40 40"><circle cx="20" cy="20" r="16" fill="#5C2D0E"/><path d="M12 20 L20 12 L28 20 L20 28 Z" fill="#D4871C" opacity="0.8"/><circle cx="20" cy="20" r="4" fill="#E8A840"/></svg>`
    },
    {
      headline: "Trump Fires Attorney General Pam Bondi, Names Former Defense Lawyer as Replacement",
      tag: "U.S. POLITICS",
      source: "FRANKLY",
      time: "8 hrs ago",
      bg: "#2A2040",
      icon: `<svg width="36" height="36" viewBox="0 0 36 36"><rect x="6" y="8" width="24" height="20" rx="3" fill="#4A3B6B"/><path d="M10 14h16M10 18h12M10 22h8" stroke="#8B7EC8" stroke-width="1.5" stroke-linecap="round"/></svg>`
    },
    {
      headline: "COVID Variant BA.3.2 'Cicada' Detected in 23 Countries and Half of U.S. States",
      tag: "HEALTH",
      source: "FRANKLY",
      time: "7 hrs ago",
      bg: "#0E4D40",
      icon: `<svg width="36" height="36" viewBox="0 0 36 36"><circle cx="18" cy="18" r="12" fill="#1A6B58"/><circle cx="18" cy="18" r="6" fill="#2AAA8A" opacity="0.7"/><circle cx="18" cy="18" r="2" fill="#5DDFC0"/><line x1="18" y1="6" x2="18" y2="12" stroke="#2AAA8A" stroke-width="1.5"/><line x1="18" y1="24" x2="18" y2="30" stroke="#2AAA8A" stroke-width="1.5"/><line x1="6" y1="18" x2="12" y2="18" stroke="#2AAA8A" stroke-width="1.5"/><line x1="24" y1="18" x2="30" y2="18" stroke="#2AAA8A" stroke-width="1.5"/></svg>`
    },
    {
      headline: "Pentagon Fires Army Chief of Staff in Latest Military Leadership Shakeup",
      tag: "DEFENSE",
      source: "FRANKLY",
      time: "10 hrs ago",
      bg: "#2C2C2C",
      icon: `<svg width="36" height="36" viewBox="0 0 36 36"><polygon points="18,4 22,14 33,14 24,21 27,32 18,25 9,32 12,21 3,14 14,14" fill="#555" opacity="0.8"/></svg>`
    }
  ];
 
  function renderArticles() {
    const list = document.getElementById('newsList');
    list.innerHTML = '';
    articles.forEach((a, i) => {
      const showBar = i === 3 || i === 6;
      let html = '';
      if (showBar) html += `<div class="section-bar"></div>`;
      html += `
        <article class="news-card">
          <div class="card-thumb">
            <div class="thumb-placeholder" style="background:${a.bg}">
              ${a.icon}
            </div>
          </div>
          <div class="card-body">
            <span class="card-tag">${a.tag}</span>
            <h2 class="card-headline">${a.headline}</h2>
            <div class="card-meta">
              <span class="card-source">${a.source}</span>
              <span class="card-time">${a.time}</span>
            </div>
          </div>
        </article>
      `;
      list.insertAdjacentHTML('beforeend', html);
    });
  }
 
  document.getElementById('catNav').addEventListener('click', (e) => {
    const tab = e.target.closest('.cat-tab');
    if (!tab) return;
    document.querySelectorAll('.cat-tab').forEach(t => t.classList.remove('active'));
    tab.classList.add('active');
    document.querySelectorAll('.news-card').forEach(c => {
      c.style.animation = 'none';
      c.offsetHeight;
      c.style.animation = '';
    });
  });
 
  renderArticles();
</script>
</body>
</html>
 
