# Parthiban25-portfolio
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Parthiban S — Full Stack Developer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Outfit:wght@300;400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

:root {
  --bg:      #060609;
  --bg2:     #0d0d14;
  --bg3:     #13131e;
  --surface: #1a1a28;
  --border:  rgba(255,255,255,0.07);
  --accent:  #00f5c4;
  --accent2: #7b5cff;
  --text:    #e8e8f0;
  --muted:   #6b6b8a;
  --dim:     #3a3a5a;
  --mono:    'JetBrains Mono', monospace;
}

html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  color: var(--text);
  font-family: 'Outfit', sans-serif;
  overflow-x: hidden;
  cursor: none;
}

/* Noise overlay */
body::before {
  content: '';
  position: fixed; inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.03'/%3E%3C/svg%3E");
  pointer-events: none;
  z-index: 1000;
}

/* Custom cursor */
#cur { position:fixed; width:10px; height:10px; background:var(--accent); border-radius:50%; pointer-events:none; z-index:9999; transform:translate(-50%,-50%); mix-blend-mode:difference; transition:width .15s,height .15s; }
#cur-ring { position:fixed; width:38px; height:38px; border:1px solid rgba(0,245,196,.35); border-radius:50%; pointer-events:none; z-index:9998; transform:translate(-50%,-50%); transition:width .25s,height .25s; }

/* ── NAV ── */
nav {
  position:fixed; top:0; left:0; right:0; z-index:500;
  padding:1.3rem 6%;
  display:flex; align-items:center; justify-content:space-between;
  background:rgba(6,6,9,.8);
  backdrop-filter:blur(24px);
  border-bottom:1px solid var(--border);
}
.logo { font-family:'Bebas Neue',sans-serif; font-size:1.5rem; letter-spacing:3px; color:var(--text); }
.logo em { color:var(--accent); font-style:normal; }
.nav-links { display:flex; gap:2.4rem; list-style:none; }
.nav-links a {
  color:var(--muted); text-decoration:none;
  font-size:.8rem; font-weight:500; letter-spacing:1.8px; text-transform:uppercase;
  transition:color .2s; position:relative;
}
.nav-links a::after { content:''; position:absolute; bottom:-4px; left:0; right:0; height:1px; background:var(--accent); transform:scaleX(0); transition:transform .25s; }
.nav-links a:hover { color:var(--text); }
.nav-links a:hover::after { transform:scaleX(1); }
.nav-cta { font-family:var(--mono); font-size:.76rem; padding:.5rem 1.3rem; border:1px solid var(--accent); color:var(--accent); text-decoration:none; letter-spacing:1px; transition:background .2s,color .2s; }
.nav-cta:hover { background:var(--accent); color:var(--bg); }

/* ── HERO ── */
#hero {
  min-height:100vh;
  display:flex; align-items:center;
  padding:130px 6% 90px;
  position:relative; overflow:hidden;
}
#hero::before {
  content:'';
  position:absolute; inset:0;
  background-image:
    linear-gradient(rgba(0,245,196,.035) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0,245,196,.035) 1px, transparent 1px);
  background-size:65px 65px;
  animation:gridShift 25s linear infinite;
}
@keyframes gridShift { to { background-position:65px 65px; } }

.orb { position:absolute; border-radius:50%; filter:blur(90px); pointer-events:none; }
.orb1 { width:550px; height:550px; background:rgba(123,92,255,.11); top:-120px; right:-80px; animation:floatOrb 9s ease-in-out infinite; }
.orb2 { width:380px; height:380px; background:rgba(0,245,196,.07); bottom:-60px; left:5%; animation:floatOrb 13s ease-in-out infinite reverse; }
@keyframes floatOrb { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-50px)} }

.hero-inner { position:relative; z-index:2; max-width:780px; }

.hero-tag {
  display:inline-flex; align-items:center; gap:.6rem;
  font-family:var(--mono); font-size:.75rem; color:var(--accent);
  letter-spacing:2.5px; text-transform:uppercase; margin-bottom:1.6rem;
  opacity:0; animation:up .6s .2s forwards;
}
.hero-tag::before { content:''; width:28px; height:1px; background:var(--accent); }

.hero-name {
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(5rem,11vw,10rem);
  line-height:.88; letter-spacing:3px;
  margin-bottom:.5rem;
  opacity:0; animation:up .7s .35s forwards;
}
.hero-name .ghost { -webkit-text-stroke:1px rgba(255,255,255,.2); color:transparent; }

.hero-role {
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(1.4rem,3vw,2.5rem);
  color:var(--accent); letter-spacing:4px;
  margin-bottom:1.8rem;
  opacity:0; animation:up .7s .5s forwards;
}

.hero-desc {
  font-size:1rem; font-weight:300; color:var(--muted);
  max-width:500px; line-height:1.85; margin-bottom:2.5rem;
  opacity:0; animation:up .7s .65s forwards;
}

.hero-btns {
  display:flex; gap:1rem; flex-wrap:wrap;
  opacity:0; animation:up .7s .8s forwards;
}
.btn-p {
  background:var(--accent); color:var(--bg); font-weight:600; font-size:.87rem;
  padding:.85rem 2rem; text-decoration:none; letter-spacing:.5px;
  clip-path:polygon(0 0,calc(100% - 12px) 0,100% 12px,100% 100%,0 100%);
  transition:transform .2s,box-shadow .2s;
}
.btn-p:hover { transform:translateY(-2px); box-shadow:0 8px 32px rgba(0,245,196,.28); }
.btn-s {
  border:1px solid var(--dim); color:var(--text); font-size:.87rem;
  padding:.85rem 2rem; text-decoration:none; letter-spacing:.5px;
  clip-path:polygon(0 0,calc(100% - 12px) 0,100% 12px,100% 100%,0 100%);
  transition:border-color .2s,color .2s;
}
.btn-s:hover { border-color:var(--accent); color:var(--accent); }

/* Floating code card */
.hero-code {
  position:absolute; right:6%; top:50%; transform:translateY(-50%);
  background:var(--bg3); border:1px solid var(--border);
  padding:1.6rem 2rem;
  font-family:var(--mono); font-size:.76rem; line-height:2; color:var(--muted);
  opacity:0; animation:fromRight .8s 1s forwards;
  max-width:330px;
}
.hero-code::before { content:''; position:absolute; top:0; left:0; right:0; height:2px; background:linear-gradient(90deg,var(--accent),var(--accent2)); }
.dots { display:flex; gap:6px; margin-bottom:1rem; }
.dots span { width:10px; height:10px; border-radius:50%; background:var(--dim); }
.dots span:nth-child(1){background:#ff5f57} .dots span:nth-child(2){background:#febc2e} .dots span:nth-child(3){background:#28c840}
.kw{color:var(--accent2)} .fn{color:var(--accent)} .str{color:#ff9f7c} .cm{color:var(--dim)}

/* Scroll hint */
.scroll-hint {
  position:absolute; bottom:2.5rem; left:50%; transform:translateX(-50%);
  display:flex; flex-direction:column; align-items:center; gap:.5rem;
  font-family:var(--mono); font-size:.67rem; color:var(--dim); letter-spacing:2px;
  opacity:0; animation:up .5s 1.4s forwards;
}
.s-line { width:1px; height:48px; background:linear-gradient(var(--accent),transparent); animation:sLine 1.6s ease-in-out infinite; }
@keyframes sLine {
  0%{transform:scaleY(0);transform-origin:top} 50%{transform:scaleY(1);transform-origin:top}
  51%{transform:scaleY(1);transform-origin:bottom} 100%{transform:scaleY(0);transform-origin:bottom}
}

/* ── SHARED ── */
section { padding:100px 6%; position:relative; }
.s-label { font-family:var(--mono); font-size:.72rem; color:var(--accent); letter-spacing:3px; text-transform:uppercase; margin-bottom:.7rem; }
.s-title { font-family:'Bebas Neue',sans-serif; font-size:clamp(2.5rem,5vw,4rem); letter-spacing:2px; line-height:1; margin-bottom:3rem; }
.s-title span { color:var(--accent); }
.divider { width:100%; height:1px; background:linear-gradient(90deg,transparent,var(--dim),transparent); }

/* ── ABOUT ── */
#about { background:var(--bg2); }
.about-grid { display:grid; grid-template-columns:1fr 1fr; gap:5rem; align-items:center; }
.about-text p { color:var(--muted); font-weight:300; line-height:1.9; margin-bottom:1rem; }
.about-text p strong { color:var(--text); font-weight:500; }
.stat-grid { display:grid; grid-template-columns:1fr 1fr; gap:1px; border:1px solid var(--border); overflow:hidden; }
.stat-box { background:var(--bg3); padding:2rem 1.8rem; transition:background .3s; position:relative; }
.stat-box:hover { background:var(--surface); }
.stat-box::after { content:''; position:absolute; inset:0; border:1px solid var(--border); pointer-events:none; }
.stat-n { font-family:'Bebas Neue',sans-serif; font-size:3.2rem; color:var(--accent); line-height:1; display:block; }
.stat-l { font-size:.75rem; font-weight:500; color:var(--muted); letter-spacing:1.5px; text-transform:uppercase; margin-top:.3rem; display:block; }

/* ── SKILLS ── */
#skills { background:var(--bg); }
.skills-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(250px,1fr)); gap:1px; border:1px solid var(--border); overflow:hidden; }
.sk-cat { background:var(--bg3); padding:2rem; transition:background .3s; position:relative; }
.sk-cat::before { content:''; position:absolute; top:0; left:0; right:0; height:2px; background:linear-gradient(90deg,var(--accent),transparent); transform:scaleX(0); transition:transform .4s; }
.sk-cat:hover { background:var(--surface); }
.sk-cat:hover::before { transform:scaleX(1); }
.sk-label { font-family:var(--mono); font-size:.7rem; color:var(--accent); letter-spacing:2px; text-transform:uppercase; margin-bottom:1.2rem; display:flex; align-items:center; gap:.5rem; }
.sk-label::before { content:''; width:18px; height:1px; background:var(--accent); }
.tags { display:flex; flex-wrap:wrap; gap:.45rem; }
.tag { font-family:var(--mono); font-size:.72rem; padding:.28rem .65rem; border:1px solid var(--dim); color:var(--muted); letter-spacing:.5px; transition:border-color .2s,color .2s; cursor:default; }
.tag:hover { border-color:var(--accent); color:var(--accent); }

/* ── PROJECTS ── */
#projects { background:var(--bg2); }
.proj-grid { display:grid; grid-template-columns:1fr 1fr; gap:1px; }
.proj-card {
  background:var(--bg3); padding:2.5rem;
  position:relative; overflow:hidden;
  border:1px solid var(--border);
  transition:background .3s;
}
.proj-card:hover { background:var(--surface); }
.proj-card::before {
  content:''; position:absolute; top:0; left:0; right:0; height:1px;
  background:linear-gradient(90deg,var(--accent2),var(--accent));
  transform:scaleX(0); transform-origin:left; transition:transform .5s;
}
.proj-card:hover::before { transform:scaleX(1); }
.proj-card.wide { grid-column:1/-1; }
.proj-card.wide .proj-inner { display:grid; grid-template-columns:1fr 1fr; gap:3rem; align-items:start; }
.p-num { font-family:var(--mono); font-size:.68rem; color:var(--dim); letter-spacing:2px; margin-bottom:.8rem; }
.p-type { font-family:var(--mono); font-size:.68rem; color:var(--accent); letter-spacing:2px; text-transform:uppercase; margin-bottom:.6rem; }
.p-name { font-family:'Bebas Neue',sans-serif; font-size:1.9rem; letter-spacing:1px; margin-bottom:1rem; line-height:1.1; }
.p-desc { font-size:.9rem; color:var(--muted); font-weight:300; line-height:1.8; margin-bottom:1.4rem; }
.p-bullets { list-style:none; margin-bottom:1.4rem; }
.p-bullets li { font-size:.86rem; color:var(--muted); padding:.32rem 0 .32rem 1.1rem; position:relative; font-weight:300; border-bottom:1px solid rgba(255,255,255,.04); }
.p-bullets li::before { content:'→'; position:absolute; left:0; color:var(--accent); font-size:.72rem; top:.38rem; }
.p-stack { display:flex; flex-wrap:wrap; gap:.4rem; margin-top:1rem; }
.badge { font-family:var(--mono); font-size:.67rem; padding:.22rem .6rem; background:rgba(0,245,196,.06); border:1px solid rgba(0,245,196,.18); color:var(--accent); letter-spacing:.5px; }

/* ── ACHIEVEMENTS ── */
#achievements { background:var(--bg); }
.timeline { position:relative; padding-left:2.5rem; margin-top:1rem; }
.timeline::before { content:''; position:absolute; left:0; top:0; bottom:0; width:1px; background:linear-gradient(var(--accent),var(--accent2),transparent); }
.t-item { position:relative; padding-bottom:2.8rem; }
.t-item:last-child { padding-bottom:0; }
.t-item::before { content:''; position:absolute; left:-2.5rem; top:.4rem; width:9px; height:9px; border-radius:50%; background:var(--accent); box-shadow:0 0 0 3px rgba(0,245,196,.15); }
.t-date { font-family:var(--mono); font-size:.7rem; color:var(--accent); letter-spacing:2px; margin-bottom:.35rem; }
.t-title { font-size:.98rem; font-weight:600; margin-bottom:.25rem; }
.t-sub { font-size:.87rem; color:var(--muted); font-weight:300; }

/* ── EDUCATION ── */
#education { background:var(--bg2); }
.edu-list { border:1px solid var(--border); overflow:hidden; margin-top:1rem; }
.edu-row {
  background:var(--bg3); padding:2rem 2.5rem;
  display:grid; grid-template-columns:1fr auto; align-items:center; gap:2rem;
  border-bottom:1px solid var(--border); transition:background .3s;
}
.edu-row:last-child { border-bottom:none; }
.edu-row:hover { background:var(--surface); }
.edu-deg { font-family:var(--mono); font-size:.7rem; color:var(--accent); letter-spacing:2px; text-transform:uppercase; margin-bottom:.4rem; }
.edu-inst { font-size:1.02rem; font-weight:600; margin-bottom:.2rem; }
.edu-det { font-size:.87rem; color:var(--muted); font-weight:300; }
.edu-yr { font-family:'Bebas Neue',sans-serif; font-size:1.5rem; color:var(--dim); letter-spacing:2px; white-space:nowrap; }

/* ── CONTACT ── */
#contact { background:var(--bg); text-align:center; padding:130px 6%; }
.c-big {
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(3rem,9vw,8rem);
  letter-spacing:3px; line-height:.9; margin-bottom:1.5rem;
}
.c-big span { color:var(--accent); }
.c-sub { font-size:1rem; color:var(--muted); font-weight:300; max-width:480px; margin:0 auto 2.5rem; line-height:1.85; }
.c-links { display:flex; align-items:center; justify-content:center; flex-wrap:wrap; gap:.8rem; }
.c-link {
  display:flex; align-items:center; gap:.55rem;
  font-family:var(--mono); font-size:.78rem; color:var(--muted);
  text-decoration:none; padding:.65rem 1.3rem;
  border:1px solid var(--dim); letter-spacing:1px;
  transition:border-color .2s,color .2s;
}
.c-link:hover { border-color:var(--accent); color:var(--accent); }
.c-link svg { width:15px; height:15px; stroke:currentColor; fill:none; stroke-width:1.5; flex-shrink:0; }

/* ── FOOTER ── */
footer { background:var(--bg2); border-top:1px solid var(--border); padding:2rem 6%; display:flex; align-items:center; justify-content:space-between; flex-wrap:wrap; gap:1rem; }
.f-logo { font-family:'Bebas Neue',sans-serif; font-size:1.3rem; letter-spacing:2px; }
.f-logo em { color:var(--accent); font-style:normal; }
footer p { font-family:var(--mono); font-size:.68rem; color:var(--dim); letter-spacing:1px; }

/* ── ANIMATIONS ── */
@keyframes up { from{opacity:0;transform:translateY(26px)} to{opacity:1;transform:translateY(0)} }
@keyframes fromRight { from{opacity:0;transform:translate(30px,-50%)} to{opacity:1;transform:translate(0,-50%)} }

.reveal { opacity:0; transform:translateY(28px); transition:opacity .7s ease,transform .7s ease; }
.reveal.visible { opacity:1; transform:none; }

/* ── RESPONSIVE ── */
@media(max-width:900px){
  .nav-links{display:none}
  .hero-code{display:none}
  .about-grid{grid-template-columns:1fr;gap:3rem}
  .proj-grid{grid-template-columns:1fr}
  .proj-card.wide .proj-inner{grid-template-columns:1fr;gap:1.5rem}
  .hero-name{font-size:clamp(3.5rem,16vw,6rem)}
}
</style>
</head>
<body>

<div id="cur"></div>
<div id="cur-ring"></div>

<!-- NAV -->
<nav>
  <div class="logo">P<em>.</em>S</div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#achievements">Achievements</a></li>
    <li><a href="#education">Education</a></li>
  </ul>
  <a href="#contact" class="nav-cta">Hire Me</a>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="orb orb1"></div>
  <div class="orb orb2"></div>

  <div class="hero-inner">
    <div class="hero-tag">Full Stack Developer · MERN · Python</div>
    <h1 class="hero-name">PARTHI<br><span class="ghost">BAN S</span></h1>
    <p class="hero-role">Building Scalable Web Apps</p>
    <p class="hero-desc">
      Final-year ECE student from Chennai. I build full stack applications
      using MERN &amp; Python — clean code, secure backends, and experiences
      that actually ship.
    </p>
    <div class="hero-btns">
      <a href="#projects" class="btn-p">View Projects</a>
      <a href="#contact" class="btn-s">Get In Touch</a>
    </div>
  </div>

  <div class="hero-code">
    <div class="dots"><span></span><span></span><span></span></div>
    <div><span class="cm">// developer.config.js</span></div>
    <div>&nbsp;</div>
    <div><span class="kw">const</span> parthiban = {</div>
    <div>&nbsp;&nbsp;role: <span class="str">"Full Stack Dev"</span>,</div>
    <div>&nbsp;&nbsp;stack: [<span class="str">"MERN"</span>, <span class="str">"Flask"</span>],</div>
    <div>&nbsp;&nbsp;loves: <span class="str">"Clean Code"</span>,</div>
    <div>&nbsp;&nbsp;status: <span class="str">"Open to Work ✓"</span>,</div>
    <div>&nbsp;&nbsp;location: <span class="str">"Chennai, IN"</span></div>
    <div>};</div>
    <div>&nbsp;</div>
    <div><span class="fn">export default</span> parthiban;</div>
  </div>

  <div class="scroll-hint">
    <div class="s-line"></div>
    SCROLL
  </div>
</section>

<div class="divider"></div>

<!-- ABOUT -->
<section id="about">
  <div class="s-label">01 — About</div>
  <h2 class="s-title">Who I <span>Am</span></h2>
  <div class="about-grid">
    <div class="about-text reveal">
      <p>I'm <strong>Parthiban S</strong>, a final-year Electronics &amp; Communication
      Engineering student at Agni College of Technology, Chennai, graduating in 2026.</p>
      <p>I've channelled my engineering foundation into <strong>full stack development</strong> —
      building real, production-quality applications from scratch. My stack of choice is
      <strong>MERN</strong> for dynamic web apps and <strong>Flask + MySQL</strong> for
      structured backend systems.</p>
      <p>I care about <strong>clean architecture, RESTful design, and secure authentication</strong>.
      Outside of code, I've organized inter-college tech events, won paper presentation
      competitions, and volunteered for community service.</p>
    </div>
    <div class="reveal">
      <div class="stat-grid">
        <div class="stat-box">
          <span class="stat-n">3+</span>
          <span class="stat-l">Projects Built</span>
        </div>
        <div class="stat-box">
          <span class="stat-n">7.0</span>
          <span class="stat-l">CGPA</span>
        </div>
        <div class="stat-box">
          <span class="stat-n">5+</span>
          <span class="stat-l">Certifications</span>
        </div>
        <div class="stat-box">
          <span class="stat-n">2026</span>
          <span class="stat-l">Graduating</span>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- SKILLS -->
<section id="skills">
  <div class="s-label">02 — Skills</div>
  <h2 class="s-title">Tech <span>Stack</span></h2>
  <div class="skills-grid">
    <div class="sk-cat reveal">
      <div class="sk-label">Languages</div>
      <div class="tags">
        <span class="tag">JavaScript</span><span class="tag">Python</span>
        <span class="tag">Java</span><span class="tag">C</span>
      </div>
    </div>
    <div class="sk-cat reveal">
      <div class="sk-label">Frontend</div>
      <div class="tags">
        <span class="tag">React.js</span><span class="tag">HTML5</span>
        <span class="tag">CSS3</span><span class="tag">Figma</span>
      </div>
    </div>
    <div class="sk-cat reveal">
      <div class="sk-label">UI / UX Design</div>
      <div class="tags">
        <span class="tag">Figma</span><span class="tag">Wireframing</span>
        <span class="tag">Prototyping</span><span class="tag">User Research</span>
        <span class="tag">Design Systems</span>
      </div>
    </div>
    <div class="sk-cat reveal">
      <div class="sk-label">Backend</div>
      <div class="tags">
        <span class="tag">Node.js</span><span class="tag">Express.js</span>
        <span class="tag">Flask</span><span class="tag">REST APIs</span>
      </div>
    </div>
    <div class="sk-cat reveal">
      <div class="sk-label">Database</div>
      <div class="tags">
        <span class="tag">MongoDB</span><span class="tag">MySQL</span>
      </div>
    </div>
    <div class="sk-cat reveal">
      <div class="sk-label">Core Concepts</div>
      <div class="tags">
        <span class="tag">DSA</span><span class="tag">OOP</span>
        <span class="tag">DBMS</span><span class="tag">JWT Auth</span>
        <span class="tag">REST Architecture</span>
      </div>
    </div>
    <div class="sk-cat reveal">
      <div class="sk-label">Tools</div>
      <div class="tags">
        <span class="tag">Git</span><span class="tag">GitHub</span>
        <span class="tag">Postman</span><span class="tag">VS Code</span>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- PROJECTS -->
<section id="projects">
  <div class="s-label">03 — Projects</div>
  <h2 class="s-title">What I've <span>Built</span></h2>
  <div class="proj-grid">

    <!-- Featured -->
    <div class="proj-card wide reveal">
      <div class="proj-inner">
        <div>
          <div class="p-num">Project 01 · 2025</div>
          <div class="p-type">MERN Stack · Full Stack</div>
          <h3 class="p-name">Task Management<br>Application</h3>
          <p class="p-desc">A scalable, full-featured task management platform engineered from the ground up with clean RESTful architecture, JWT-secured authentication, and a responsive React frontend.</p>
          <div class="p-stack">
            <span class="badge">MongoDB</span>
            <span class="badge">Express.js</span>
            <span class="badge">React.js</span>
            <span class="badge">Node.js</span>
            <span class="badge">JWT Auth</span>
          </div>
        </div>
        <div>
          <ul class="p-bullets">
            <li>Engineered RESTful APIs supporting full CRUD for 100+ simulated users</li>
            <li>Integrated JWT-based authentication with secured backend route protection</li>
            <li>Architected scalable MongoDB data models for efficient querying</li>
            <li>Enhanced API efficiency and improved frontend responsiveness across devices</li>
          </ul>
        </div>
      </div>
    </div>

    <!-- Project 2 -->
    <div class="proj-card reveal">
      <div class="p-num">Project 02 · 2025</div>
      <div class="p-type">Python Flask · Backend API</div>
      <h3 class="p-name">Student Management System</h3>
      <p class="p-desc">A robust REST API for structured student record management, built with Flask and MySQL with centralized error handling and full input validation.</p>
      <ul class="p-bullets">
        <li>Designed CRUD endpoints with input validation &amp; error handling</li>
        <li>Configured MySQL schema for reliable relational data storage</li>
        <li>Validated performance and stability using Postman test suites</li>
      </ul>
      <div class="p-stack">
        <span class="badge">Python</span>
        <span class="badge">Flask</span>
        <span class="badge">MySQL</span>
        <span class="badge">Postman</span>
      </div>
    </div>

    <!-- Project 3 -->
    <div class="proj-card reveal">
      <div class="p-num">Project 03 · 2024</div>
      <div class="p-type">Embedded Systems · Arduino</div>
      <h3 class="p-name">Smart Irrigation System</h3>
      <p class="p-desc">An automated irrigation controller using Arduino and soil moisture sensors, applying threshold-based logic to conserve water and minimize manual intervention.</p>
      <ul class="p-bullets">
        <li>Sensor-driven relay control for automated water pump operation</li>
        <li>Threshold logic to optimize water usage and minimize wastage</li>
        <li>Suitable for gardens, farms, and greenhouse environments</li>
      </ul>
      <div class="p-stack">
        <span class="badge">Arduino</span>
        <span class="badge">C</span>
        <span class="badge">Sensor Interfacing</span>
      </div>
    </div>

  </div>
</section>

<div class="divider"></div>

<!-- ACHIEVEMENTS -->
<section id="achievements">
  <div class="s-label">04 — Achievements</div>
  <h2 class="s-title">Milestones &amp; <span>Certs</span></h2>
  <div class="timeline">
    <div class="t-item reveal">
      <div class="t-date">2023</div>
      <div class="t-title">🏆 First Prize — Paper Presentation</div>
      <div class="t-sub">Jerusalem College of Engineering</div>
    </div>
    <div class="t-item reveal">
      <div class="t-date">2024</div>
      <div class="t-title">Organized Inter-College Technical Symposium</div>
      <div class="t-sub">Agni College of Technology, Chennai</div>
    </div>
    <div class="t-item reveal">
      <div class="t-date">2024</div>
      <div class="t-title">Network Security &amp; Communication Management</div>
      <div class="t-sub">Great Learning — Certification Completed</div>
    </div>
    <div class="t-item reveal">
      <div class="t-date">2024</div>
      <div class="t-title">Business English &amp; Design Thinking</div>
      <div class="t-sub">Infosys Springboard — Certification Completed</div>
    </div>
    <div class="t-item reveal">
      <div class="t-date">2025</div>
      <div class="t-title">Volunteered — Blood Donation &amp; Social Service Events</div>
      <div class="t-sub">Community Service, Chennai</div>
    </div>
    <div class="t-item reveal">
      <div class="t-date">2025</div>
      <div class="t-title">🎓 UI/UX Design — Course Completed</div>
      <div class="t-sub">Novitech, Chennai &nbsp;·&nbsp; Figma · Wireframing · Prototyping · Design Systems</div>
    </div>
    <div class="t-item reveal">
      <div class="t-date">2025</div>
      <div class="t-title">🎓 MERN Stack Development — Course Completed</div>
      <div class="t-sub">Novitech, Chennai &nbsp;·&nbsp; MongoDB · Express.js · React.js · Node.js</div>
    </div>
    <div class="t-item reveal">
      <div class="t-date">2025</div>
      <div class="t-title">🎓 Python Full Stack — Course Completed</div>
      <div class="t-sub">QSpider, Chennai &nbsp;·&nbsp; Python · Django/Flask · HTML · CSS · MySQL</div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- EDUCATION -->
<section id="education">
  <div class="s-label">05 — Education</div>
  <h2 class="s-title">Academic <span>Journey</span></h2>
  <div class="edu-list reveal">
    <div class="edu-row">
      <div>
        <div class="edu-deg">B.E. — Electronics &amp; Communication Engineering</div>
        <div class="edu-inst">Agni College of Technology, Chennai</div>
        <div class="edu-det">CGPA: 7.0 (till 7th Semester)</div>
      </div>
      <div class="edu-yr">2022–26</div>
    </div>
    <div class="edu-row">
      <div>
        <div class="edu-deg">Higher Secondary Certificate (Class XII)</div>
        <div class="edu-inst">St. George Matriculation Hr. Sec. School, Chennai</div>
        <div class="edu-det">Percentage: 63%</div>
      </div>
      <div class="edu-yr">2021–22</div>
    </div>
    <div class="edu-row">
      <div>
        <div class="edu-deg">Secondary School Leaving Certificate (Class X)</div>
        <div class="edu-inst">St. George Matriculation Hr. Sec. School, Chennai</div>
        <div class="edu-det">Percentage: 60%</div>
      </div>
      <div class="edu-yr">2019–20</div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- CONTACT -->
<section id="contact">
  <div class="s-label" style="display:inline-block;margin-bottom:1rem">06 — Contact</div>
  <div class="c-big reveal">LET'S <span>BUILD</span><br>TOGETHER.</div>
  <p class="c-sub reveal">Open to full stack developer roles, internships, and freelance
  projects. I reply fast — let's talk.</p>
  <div class="c-links reveal">
    <a href="mailto:parthibansuresh2546@gmail.com" class="c-link">
      <svg viewBox="0 0 24 24"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
      parthibansuresh2546@gmail.com
    </a>
    <a href="tel:+919345700236" class="c-link">
      <svg viewBox="0 0 24 24"><path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07A19.5 19.5 0 013.07 9.8 19.79 19.79 0 01.22 1.22 2 2 0 012.22 0h3a2 2 0 012 1.72 12.84 12.84 0 00.7 2.81 2 2 0 01-.45 2.11L6.09 7.91a16 16 0 006 6l1.27-1.27a2 2 0 012.11-.45 12.84 12.84 0 002.81.7A2 2 0 0122 14.92z"/></svg>
      +91 93457 00236
    </a>
    <a href="https://linkedin.com/in/parthiban-suresh-446974267" target="_blank" class="c-link">
      <svg viewBox="0 0 24 24"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6z"/><rect x="2" y="9" width="4" height="12"/><circle cx="4" cy="4" r="2"/></svg>
      LinkedIn
    </a>
    <a href="https://github.com/parthiban25-upc" target="_blank" class="c-link">
      <svg viewBox="0 0 24 24"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 00-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0020 4.77 5.07 5.07 0 0019.91 1S18.73.65 16 2.48a13.38 13.38 0 00-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 005 4.77a5.44 5.44 0 00-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 009 18.13V22"/></svg>
      GitHub
    </a>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="f-logo">P<em>.</em>S</div>
  <p>© 2025 Parthiban S &nbsp;·&nbsp; Chennai, Tamil Nadu</p>
  <p>Built with passion &amp; clean code</p>
</footer>

<script>
// ── Custom Cursor
const cur = document.getElementById('cur');
const ring = document.getElementById('cur-ring');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove', e => { mx=e.clientX; my=e.clientY; });
(function tick(){
  cur.style.left=mx+'px'; cur.style.top=my+'px';
  rx+=(mx-rx)*0.11; ry+=(my-ry)*0.11;
  ring.style.left=rx+'px'; ring.style.top=ry+'px';
  requestAnimationFrame(tick);
})();
document.querySelectorAll('a,button,.sk-cat,.proj-card,.stat-box,.tag').forEach(el=>{
  el.addEventListener('mouseenter',()=>{ cur.style.width='18px'; cur.style.height='18px'; ring.style.width='56px'; ring.style.height='56px'; });
  el.addEventListener('mouseleave',()=>{ cur.style.width='10px'; cur.style.height='10px'; ring.style.width='38px'; ring.style.height='38px'; });
});

// ── Scroll Reveal
const obs = new IntersectionObserver(entries=>{
  entries.forEach(e=>{ if(e.isIntersecting){ e.target.classList.add('visible'); obs.unobserve(e.target); } });
}, { threshold:0.1 });
document.querySelectorAll('.reveal').forEach((el,i)=>{
  el.style.transitionDelay=(i%4)*0.08+'s';
  obs.observe(el);
});

// ── Active nav link highlight
const sections = document.querySelectorAll('section[id]');
window.addEventListener('scroll',()=>{
  let cur='';
  sections.forEach(s=>{ if(window.scrollY>=s.offsetTop-120) cur=s.id; });
  document.querySelectorAll('.nav-links a').forEach(a=>{
    a.style.color = a.getAttribute('href')==='#'+cur ? 'var(--text)' : '';
  });
});
</script>
</body>
</html>
