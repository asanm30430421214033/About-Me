# About-Me
Portfolio 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Naveen K — Portfolio</title>
  <link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg: #080c10;
      --surface: #0d1117;
      --border: #1e2a38;
      --accent: #00d4ff;
      --accent2: #7c3aed;
      --green: #39d353;
      --text: #e6edf3;
      --muted: #7d8590;
      --card: #0d1117;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'Syne', sans-serif;
      overflow-x: hidden;
      cursor: none;
    }

    /* Custom cursor */
    .cursor {
      width: 12px; height: 12px;
      background: var(--accent);
      border-radius: 50%;
      position: fixed;
      top: 0; left: 0;
      pointer-events: none;
      z-index: 9999;
      transform: translate(-50%, -50%);
      transition: transform 0.05s, width 0.2s, height 0.2s, background 0.2s;
      mix-blend-mode: screen;
    }
    .cursor-ring {
      width: 36px; height: 36px;
      border: 1.5px solid var(--accent);
      border-radius: 50%;
      position: fixed;
      top: 0; left: 0;
      pointer-events: none;
      z-index: 9998;
      transform: translate(-50%, -50%);
      transition: all 0.12s ease;
      opacity: 0.5;
    }

    /* ── NAV ── */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 1.2rem 3rem;
      background: rgba(8,12,16,0.85);
      backdrop-filter: blur(18px);
      border-bottom: 1px solid var(--border);
    }
    .nav-logo {
      font-family: 'Space Mono', monospace;
      font-size: 1rem;
      color: var(--accent);
      letter-spacing: 0.05em;
    }
    .nav-links {
      display: flex;
      gap: 2.2rem;
      list-style: none;
    }
    .nav-links a {
      color: var(--muted);
      text-decoration: none;
      font-size: 0.85rem;
      font-weight: 600;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      transition: color 0.2s;
      position: relative;
    }
    .nav-links a::after {
      content: '';
      position: absolute;
      bottom: -3px; left: 0;
      width: 0; height: 1px;
      background: var(--accent);
      transition: width 0.3s;
    }
    .nav-links a:hover { color: var(--accent); }
    .nav-links a:hover::after { width: 100%; }

    /* ── HERO ── */
    #hero {
      min-height: 100vh;
      display: flex;
      align-items: center;
      padding: 0 3rem;
      position: relative;
      overflow: hidden;
    }
    .grid-bg {
      position: absolute;
      inset: 0;
      background-image:
        linear-gradient(rgba(0,212,255,0.04) 1px, transparent 1px),
        linear-gradient(90deg, rgba(0,212,255,0.04) 1px, transparent 1px);
      background-size: 50px 50px;
      animation: gridPulse 8s ease-in-out infinite;
    }
    @keyframes gridPulse {
      0%,100% { opacity: 0.5; }
      50% { opacity: 1; }
    }
    .glow-blob {
      position: absolute;
      width: 500px; height: 500px;
      background: radial-gradient(circle, rgba(0,212,255,0.08) 0%, transparent 70%);
      right: -100px; top: 50%;
      transform: translateY(-50%);
      animation: blobFloat 6s ease-in-out infinite;
    }
    .glow-blob2 {
      position: absolute;
      width: 300px; height: 300px;
      background: radial-gradient(circle, rgba(124,58,237,0.1) 0%, transparent 70%);
      left: 100px; bottom: 100px;
      animation: blobFloat 8s ease-in-out infinite reverse;
    }
    @keyframes blobFloat {
      0%,100% { transform: translateY(-50%) scale(1); }
      50% { transform: translateY(-55%) scale(1.08); }
    }
    .hero-content {
      position: relative;
      z-index: 1;
      max-width: 700px;
    }
    .hero-tag {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      background: rgba(0,212,255,0.08);
      border: 1px solid rgba(0,212,255,0.25);
      color: var(--accent);
      font-family: 'Space Mono', monospace;
      font-size: 0.75rem;
      padding: 0.35rem 0.9rem;
      border-radius: 100px;
      margin-bottom: 2rem;
      letter-spacing: 0.1em;
    }
    .hero-tag .dot {
      width: 6px; height: 6px;
      background: var(--green);
      border-radius: 50%;
      animation: blink 1.5s ease-in-out infinite;
    }
    @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0.3} }
    .hero-name {
      font-size: clamp(3.5rem, 8vw, 6.5rem);
      font-weight: 800;
      line-height: 0.95;
      margin-bottom: 1rem;
      letter-spacing: -0.03em;
    }
    .hero-name .line1 { display: block; color: var(--text); }
    .hero-name .line2 {
      display: block;
      background: linear-gradient(135deg, var(--accent), var(--accent2));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }
    .hero-desc {
      font-size: 1.1rem;
      color: var(--muted);
      line-height: 1.7;
      margin-bottom: 2.5rem;
      max-width: 540px;
    }
    .hero-cta {
      display: flex;
      gap: 1rem;
      flex-wrap: wrap;
    }
    .btn-primary {
      background: var(--accent);
      color: #000;
      font-family: 'Space Mono', monospace;
      font-size: 0.8rem;
      font-weight: 700;
      letter-spacing: 0.08em;
      padding: 0.85rem 2rem;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      text-decoration: none;
      text-transform: uppercase;
      transition: transform 0.2s, box-shadow 0.2s;
      display: inline-block;
    }
    .btn-primary:hover {
      transform: translateY(-2px);
      box-shadow: 0 8px 30px rgba(0,212,255,0.3);
    }
    .btn-secondary {
      background: transparent;
      color: var(--text);
      font-family: 'Space Mono', monospace;
      font-size: 0.8rem;
      font-weight: 700;
      letter-spacing: 0.08em;
      padding: 0.85rem 2rem;
      border: 1px solid var(--border);
      border-radius: 4px;
      cursor: pointer;
      text-decoration: none;
      text-transform: uppercase;
      transition: border-color 0.2s, color 0.2s;
      display: inline-block;
    }
    .btn-secondary:hover {
      border-color: var(--accent);
      color: var(--accent);
    }
    .scroll-hint {
      position: absolute;
      bottom: 2.5rem;
      left: 50%;
      transform: translateX(-50%);
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 0.5rem;
      color: var(--muted);
      font-family: 'Space Mono', monospace;
      font-size: 0.65rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
    }
    .scroll-arrow {
      width: 1px;
      height: 40px;
      background: linear-gradient(to bottom, var(--muted), transparent);
      animation: scrollDrop 1.5s ease-in-out infinite;
    }
    @keyframes scrollDrop { 0%{opacity:0;transform:scaleY(0);transform-origin:top} 50%{opacity:1;transform:scaleY(1)} 100%{opacity:0;transform:translateY(20px)} }

    /* ── SECTION BASE ── */
    section { padding: 6rem 3rem; }
    .section-header {
      display: flex;
      align-items: center;
      gap: 1rem;
      margin-bottom: 3.5rem;
    }
    .section-num {
      font-family: 'Space Mono', monospace;
      font-size: 0.75rem;
      color: var(--accent);
      letter-spacing: 0.1em;
    }
    .section-title {
      font-size: 2.2rem;
      font-weight: 800;
      letter-spacing: -0.02em;
    }
    .section-line {
      flex: 1;
      height: 1px;
      background: linear-gradient(to right, var(--border), transparent);
    }

    /* ── SKILLS ── */
    #skills { background: var(--surface); }
    .skills-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
      gap: 1rem;
    }
    .skill-pill {
      background: var(--bg);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 1rem 1.2rem;
      display: flex;
      align-items: center;
      gap: 0.75rem;
      transition: border-color 0.25s, transform 0.25s, box-shadow 0.25s;
      animation: fadeUp 0.5s ease both;
    }
    .skill-pill:hover {
      border-color: var(--accent);
      transform: translateY(-3px);
      box-shadow: 0 6px 20px rgba(0,212,255,0.08);
    }
    .skill-icon {
      font-size: 1.3rem;
      flex-shrink: 0;
    }
    .skill-name {
      font-size: 0.85rem;
      font-weight: 600;
      color: var(--text);
    }
    .skill-category {
      font-size: 0.65rem;
      color: var(--muted);
      font-family: 'Space Mono', monospace;
    }

    /* ── EXPERIENCE ── */
    .exp-card {
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 2rem 2.5rem;
      background: var(--surface);
      position: relative;
      overflow: hidden;
      transition: border-color 0.3s;
    }
    .exp-card::before {
      content: '';
      position: absolute;
      left: 0; top: 0; bottom: 0;
      width: 3px;
      background: linear-gradient(to bottom, var(--accent), var(--accent2));
    }
    .exp-card:hover { border-color: rgba(0,212,255,0.3); }
    .exp-top {
      display: flex;
      align-items: flex-start;
      justify-content: space-between;
      margin-bottom: 0.75rem;
      flex-wrap: wrap;
      gap: 0.5rem;
    }
    .exp-role {
      font-size: 1.25rem;
      font-weight: 700;
    }
    .exp-period {
      font-family: 'Space Mono', monospace;
      font-size: 0.75rem;
      color: var(--accent);
      background: rgba(0,212,255,0.08);
      border: 1px solid rgba(0,212,255,0.2);
      padding: 0.3rem 0.8rem;
      border-radius: 100px;
    }
    .exp-company {
      font-size: 0.9rem;
      color: var(--muted);
      margin-bottom: 1.5rem;
      font-family: 'Space Mono', monospace;
    }
    .exp-bullets {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 0.6rem;
    }
    .exp-bullets li {
      display: flex;
      gap: 0.75rem;
      font-size: 0.9rem;
      color: #b0bec5;
      line-height: 1.6;
    }
    .exp-bullets li::before {
      content: '→';
      color: var(--accent);
      flex-shrink: 0;
      margin-top: 1px;
    }

    /* ── PROJECTS ── */
    .projects-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
      gap: 1.5rem;
    }
    .project-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 1.75rem;
      transition: transform 0.25s, border-color 0.25s, box-shadow 0.25s;
      position: relative;
      overflow: hidden;
    }
    .project-card::after {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(135deg, rgba(0,212,255,0.03) 0%, transparent 60%);
      opacity: 0;
      transition: opacity 0.3s;
    }
    .project-card:hover {
      transform: translateY(-5px);
      border-color: rgba(0,212,255,0.25);
      box-shadow: 0 16px 40px rgba(0,0,0,0.4);
    }
    .project-card:hover::after { opacity: 1; }
    .project-top {
      display: flex;
      align-items: flex-start;
      justify-content: space-between;
      margin-bottom: 1rem;
    }
    .project-icon {
      width: 44px; height: 44px;
      background: rgba(0,212,255,0.08);
      border: 1px solid rgba(0,212,255,0.2);
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.3rem;
    }
    .project-num {
      font-family: 'Space Mono', monospace;
      font-size: 0.65rem;
      color: var(--muted);
      letter-spacing: 0.1em;
    }
    .project-title {
      font-size: 1.1rem;
      font-weight: 700;
      margin-bottom: 0.6rem;
      line-height: 1.3;
    }
    .project-desc {
      font-size: 0.85rem;
      color: var(--muted);
      line-height: 1.65;
      margin-bottom: 1.25rem;
    }
    .project-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 0.4rem;
    }
    .tag {
      font-family: 'Space Mono', monospace;
      font-size: 0.65rem;
      color: var(--accent);
      background: rgba(0,212,255,0.06);
      border: 1px solid rgba(0,212,255,0.15);
      padding: 0.25rem 0.6rem;
      border-radius: 4px;
      letter-spacing: 0.05em;
    }

    /* ── EDUCATION ── */
    #education { background: var(--surface); }
    .edu-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      gap: 1.5rem;
    }
    .edu-card {
      background: var(--bg);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 2rem;
      transition: border-color 0.3s;
      position: relative;
    }
    .edu-card:hover { border-color: rgba(124,58,237,0.4); }
    .edu-degree {
      font-size: 1.1rem;
      font-weight: 700;
      margin-bottom: 0.4rem;
    }
    .edu-school {
      font-size: 0.85rem;
      color: var(--muted);
      margin-bottom: 1rem;
      line-height: 1.5;
    }
    .edu-meta {
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 0.5rem;
    }
    .edu-year {
      font-family: 'Space Mono', monospace;
      font-size: 0.72rem;
      color: var(--muted);
      border: 1px solid var(--border);
      padding: 0.25rem 0.7rem;
      border-radius: 100px;
    }
    .edu-cgpa {
      font-family: 'Space Mono', monospace;
      font-size: 0.75rem;
      color: var(--green);
      background: rgba(57,211,83,0.06);
      border: 1px solid rgba(57,211,83,0.2);
      padding: 0.25rem 0.7rem;
      border-radius: 100px;
    }

    /* ── CERTIFICATIONS ── */
    .cert-list {
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }
    .cert-item {
      display: flex;
      align-items: center;
      gap: 1.5rem;
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 10px;
      padding: 1.25rem 1.75rem;
      transition: border-color 0.25s;
    }
    .cert-item:hover { border-color: rgba(0,212,255,0.3); }
    .cert-badge {
      width: 42px; height: 42px;
      border-radius: 10px;
      background: linear-gradient(135deg, rgba(0,212,255,0.12), rgba(124,58,237,0.12));
      border: 1px solid rgba(0,212,255,0.2);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.2rem;
      flex-shrink: 0;
    }
    .cert-name {
      font-size: 0.95rem;
      font-weight: 600;
      flex: 1;
    }
    .cert-issuer {
      font-family: 'Space Mono', monospace;
      font-size: 0.7rem;
      color: var(--muted);
    }

    /* ── CONTACT ── */
    #contact {
      background: var(--surface);
      text-align: center;
    }
    .contact-inner {
      max-width: 560px;
      margin: 0 auto;
    }
    .contact-headline {
      font-size: clamp(2rem, 5vw, 3.2rem);
      font-weight: 800;
      line-height: 1.1;
      margin-bottom: 1rem;
      letter-spacing: -0.03em;
    }
    .contact-sub {
      color: var(--muted);
      font-size: 1rem;
      line-height: 1.7;
      margin-bottom: 2.5rem;
    }
    .contact-links {
      display: flex;
      justify-content: center;
      gap: 1rem;
      flex-wrap: wrap;
      margin-bottom: 2.5rem;
    }
    .contact-link {
      display: flex;
      align-items: center;
      gap: 0.6rem;
      background: var(--bg);
      border: 1px solid var(--border);
      color: var(--text);
      text-decoration: none;
      padding: 0.75rem 1.4rem;
      border-radius: 8px;
      font-size: 0.85rem;
      font-weight: 600;
      transition: border-color 0.2s, color 0.2s, transform 0.2s;
    }
    .contact-link:hover {
      border-color: var(--accent);
      color: var(--accent);
      transform: translateY(-2px);
    }

    /* ── FOOTER ── */
    footer {
      padding: 2rem 3rem;
      border-top: 1px solid var(--border);
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 1rem;
    }
    .footer-copy {
      font-family: 'Space Mono', monospace;
      font-size: 0.72rem;
      color: var(--muted);
    }
    .footer-stack {
      font-family: 'Space Mono', monospace;
      font-size: 0.7rem;
      color: var(--muted);
    }
    .footer-stack span { color: var(--accent); }

    /* ── ANIMATIONS ── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    .reveal {
      opacity: 0;
      transform: translateY(30px);
      transition: opacity 0.6s ease, transform 0.6s ease;
    }
    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* ── RESPONSIVE ── */
    @media (max-width: 768px) {
      nav { padding: 1rem 1.5rem; }
      .nav-links { gap: 1.2rem; }
      section { padding: 4rem 1.5rem; }
      #hero { padding: 0 1.5rem; }
      .hero-name { font-size: clamp(2.8rem, 12vw, 4.5rem); }
      footer { padding: 1.5rem; }
    }
  </style>
</head>
<body>

  <div class="cursor" id="cursor"></div>
  <div class="cursor-ring" id="cursorRing"></div>

  <!-- NAV -->
  <nav>
    <div class="nav-logo">NK<span style="color:var(--muted)">_dev</span></div>
    <ul class="nav-links">
      <li><a href="#skills">Skills</a></li>
      <li><a href="#experience">Experience</a></li>
      <li><a href="#projects">Projects</a></li>
      <li><a href="#education">Education</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <section id="hero">
    <div class="grid-bg"></div>
    <div class="glow-blob"></div>
    <div class="glow-blob2"></div>
    <div class="hero-content">
      <div class="hero-tag">
        <span class="dot"></span>
        Open to Opportunities · Chennai
      </div>
      <h1 class="hero-name">
        <span class="line1">Naveen</span>
        <span class="line2">K.</span>
      </h1>
      <p class="hero-desc">
        Full Stack Python Developer & MCA Candidate. I build web applications, REST APIs, and AI-powered systems — currently seeking fresher IT roles at MNCs.
      </p>
      <div class="hero-cta">
        <a href="#projects" class="btn-primary">View Projects</a>
        <a href="#contact" class="btn-secondary">Get In Touch</a>
      </div>
    </div>
    <div class="scroll-hint">
      <span>Scroll</span>
      <div class="scroll-arrow"></div>
    </div>
  </section>

  <!-- SKILLS -->
  <section id="skills">
    <div class="section-header">
      <span class="section-num">01</span>
      <h2 class="section-title">Technical Skills</h2>
      <div class="section-line"></div>
    </div>
    <div class="skills-grid" id="skillsGrid"></div>
  </section>

  <!-- EXPERIENCE -->
  <section id="experience">
    <div class="section-header">
      <span class="section-num">02</span>
      <h2 class="section-title">Experience</h2>
      <div class="section-line"></div>
    </div>
    <div class="exp-card reveal">
      <div class="exp-top">
        <div>
          <div class="exp-role">Full Stack Python Developer Intern</div>
          <div class="exp-company">📍 Vcodez — Sholinganallur, Chennai</div>
        </div>
        <span class="exp-period">Mar 2025 – Jun 2025</span>
      </div>
      <ul class="exp-bullets">
        <li>Developed web applications using Python, Django, React.js, SQL, HTML, CSS, and JavaScript.</li>
        <li>Built and integrated REST APIs connecting Django backend with React frontend.</li>
        <li>Identified and fixed bugs to improve application stability and performance.</li>
        <li>Collaborated on UI validation and user experience improvements across projects.</li>
      </ul>
    </div>
  </section>

  <!-- PROJECTS -->
  <section id="projects">
    <div class="section-header">
      <span class="section-num">03</span>
      <h2 class="section-title">Projects</h2>
      <di
