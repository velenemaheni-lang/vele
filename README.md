<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Vele Nemaheni · E-learning Portfolio</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=Inter:wght@300;400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  /* ── Tokens ──────────────────────────────────────────────────────────────── */
  :root {
    --ink:        #0F1C2E;
    --teal:       #0D9488;
    --teal-dim:   #134E4A;
    --teal-light: #CCFBF1;
    --gold:       #F59E0B;
    --gold-light: #FEF3C7;
    --slate:      #64748B;
    --mist:       #F1F5F9;
    --white:      #FFFFFF;
    --rule:       #E2E8F0;
    --radius:     10px;
  }

  /* ── Reset ───────────────────────────────────────────────────────────────── */
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }
  body {
    font-family: 'Inter', sans-serif;
    background: var(--white);
    color: var(--ink);
    line-height: 1.6;
    overflow-x: hidden;
  }
  img { display: block; max-width: 100%; }
  a { color: inherit; text-decoration: none; }

  /* ── Nav ─────────────────────────────────────────────────────────────────── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 0 5vw;
    height: 60px;
    background: rgba(15,28,46,0.95);
    backdrop-filter: blur(8px);
    border-bottom: 1px solid rgba(255,255,255,0.07);
  }
  .nav-logo {
    font-family: 'DM Serif Display', serif;
    font-size: 1.1rem;
    color: var(--white);
    letter-spacing: 0.02em;
  }
  .nav-logo span { color: var(--teal); }
  .nav-links { display: flex; gap: 2rem; }
  .nav-links a {
    font-size: 0.82rem;
    font-weight: 500;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.6);
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--teal); }

  /* ── Hero ────────────────────────────────────────────────────────────────── */
  .hero {
    min-height: 100vh;
    background: var(--ink);
    display: grid;
    grid-template-columns: 1fr 1fr;
    align-items: center;
    padding: 100px 5vw 60px;
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute;
    top: -120px; right: -120px;
    width: 500px; height: 500px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(13,148,136,0.18) 0%, transparent 70%);
    pointer-events: none;
  }
  .hero::after {
    content: '';
    position: absolute;
    bottom: -80px; left: 30%;
    width: 360px; height: 360px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(245,158,11,0.08) 0%, transparent 70%);
    pointer-events: none;
  }
  .hero-text { position: relative; z-index: 2; }
  .hero-eyebrow {
    display: inline-flex; align-items: center; gap: 8px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.75rem;
    color: var(--teal);
    letter-spacing: 0.12em;
    text-transform: uppercase;
    margin-bottom: 1.2rem;
  }
  .hero-eyebrow::before {
    content: '';
    display: block;
    width: 28px; height: 2px;
    background: var(--teal);
  }
  .hero h1 {
    font-family: 'DM Serif Display', serif;
    font-size: clamp(2.6rem, 5vw, 4rem);
    line-height: 1.1;
    color: var(--white);
    margin-bottom: 1.4rem;
  }
  .hero h1 em {
    font-style: italic;
    color: var(--teal);
  }
  .hero-bio {
    font-size: 1rem;
    color: rgba(255,255,255,0.62);
    max-width: 480px;
    line-height: 1.75;
    margin-bottom: 2rem;
  }
  .hero-actions { display: flex; gap: 1rem; flex-wrap: wrap; }
  .btn {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 0.7rem 1.5rem;
    border-radius: 6px;
    font-size: 0.875rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s;
    border: none;
  }
  .btn-primary {
    background: var(--teal);
    color: var(--white);
  }
  .btn-primary:hover { background: #0f766e; transform: translateY(-1px); }
  .btn-outline {
    background: transparent;
    color: rgba(255,255,255,0.75);
    border: 1.5px solid rgba(255,255,255,0.2);
  }
  .btn-outline:hover { border-color: var(--teal); color: var(--teal); }

  /* Hero right side stat cards */
  .hero-stats {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
    padding-left: 6vw;
    position: relative; z-index: 2;
  }
  .stat-card {
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,255,255,0.08);
    border-radius: var(--radius);
    padding: 1.4rem 1.2rem;
    transition: border-color 0.25s, transform 0.25s;
  }
  .stat-card:hover { border-color: var(--teal); transform: translateY(-3px); }
  .stat-card:nth-child(2) { margin-top: 2rem; }
  .stat-card:nth-child(4) { margin-top: 2rem; }
  .stat-num {
    font-family: 'DM Serif Display', serif;
    font-size: 2.4rem;
    color: var(--teal);
    line-height: 1;
    margin-bottom: 0.3rem;
  }
  .stat-label {
    font-size: 0.78rem;
    color: rgba(255,255,255,0.5);
    line-height: 1.4;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  /* ── Section shell ───────────────────────────────────────────────────────── */
  section { padding: 80px 5vw; }
  .section-eyebrow {
    display: inline-flex; align-items: center; gap: 8px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.72rem;
    color: var(--teal);
    letter-spacing: 0.14em;
    text-transform: uppercase;
    margin-bottom: 0.6rem;
  }
  .section-eyebrow::before {
    content: '';
    width: 20px; height: 2px;
    background: var(--teal);
    display: block;
  }
  .section-title {
    font-family: 'DM Serif Display', serif;
    font-size: clamp(1.8rem, 3vw, 2.4rem);
    color: var(--ink);
    margin-bottom: 0.5rem;
    line-height: 1.2;
  }
  .section-sub {
    font-size: 0.95rem;
    color: var(--slate);
    max-width: 560px;
    margin-bottom: 3rem;
    line-height: 1.7;
  }

  /* ── About ───────────────────────────────────────────────────────────────── */
  #about { background: var(--mist); }
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: start;
  }
  .about-text p {
    font-size: 0.97rem;
    color: #334155;
    line-height: 1.8;
    margin-bottom: 1rem;
  }
  .philosophy-card {
    background: var(--ink);
    border-radius: var(--radius);
    padding: 2rem;
    position: relative;
    overflow: hidden;
  }
  .philosophy-card::before {
    content: '"';
    font-family: 'DM Serif Display', serif;
    font-size: 8rem;
    color: var(--teal);
    opacity: 0.15;
    position: absolute;
    top: -1rem; left: 1rem;
    line-height: 1;
  }
  .philosophy-card blockquote {
    font-family: 'DM Serif Display', serif;
    font-size: 1.2rem;
    font-style: italic;
    color: var(--white);
    line-height: 1.6;
    position: relative; z-index: 1;
    margin-bottom: 1rem;
  }
  .philosophy-card cite {
    font-size: 0.78rem;
    color: var(--teal);
    font-style: normal;
    letter-spacing: 0.06em;
    text-transform: uppercase;
  }

  /* ── Skills ──────────────────────────────────────────────────────────────── */
  #skills { background: var(--white); }
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
    gap: 1.2rem;
  }
  .skill-card {
    border: 1.5px solid var(--rule);
    border-radius: var(--radius);
    padding: 1.4rem;
    transition: border-color 0.2s, box-shadow 0.2s;
  }
  .skill-card:hover {
    border-color: var(--teal);
    box-shadow: 0 4px 20px rgba(13,148,136,0.1);
  }
  .skill-icon {
    width: 38px; height: 38px;
    background: var(--teal-light);
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.1rem;
    margin-bottom: 0.8rem;
  }
  .skill-card h4 {
    font-size: 0.9rem;
    font-weight: 600;
    color: var(--ink);
    margin-bottom: 0.3rem;
  }
  .skill-card p {
    font-size: 0.78rem;
    color: var(--slate);
    line-height: 1.5;
  }

  /* ── Projects ────────────────────────────────────────────────────────────── */
  #projects { background: var(--mist); }
  .projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 1.5rem;
  }
  .project-card {
    background: var(--white);
    border-radius: var(--radius);
    overflow: hidden;
    border: 1px solid var(--rule);
    transition: transform 0.25s, box-shadow 0.25s;
    display: flex; flex-direction: column;
  }
  .project-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 12px 36px rgba(15,28,46,0.1);
  }
  .project-thumb {
    height: 160px;
    display: flex; align-items: center; justify-content: center;
    font-size: 3rem;
    position: relative;
    overflow: hidden;
  }
  .project-thumb.drc    { background: linear-gradient(135deg, #0F1C2E 0%, #134E4A 100%); }
  .project-thumb.blend  { background: linear-gradient(135deg, #1E3A5F 0%, #0D9488 100%); }
  .project-thumb.debate { background: linear-gradient(135deg, #451A03 0%, #92400E 100%); }
  .project-thumb.lms    { background: linear-gradient(135deg, #1E1B4B 0%, #4338CA 100%); }
  .project-thumb::after {
    content: '';
    position: absolute; inset: 0;
    background: rgba(0,0,0,0.15);
  }
  .project-thumb span { position: relative; z-index: 1; }
  .project-body { padding: 1.4rem; flex: 1; display: flex; flex-direction: column; }
  .project-tag {
    display: inline-block;
    font-size: 0.7rem;
    font-weight: 600;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: var(--teal);
    background: var(--teal-light);
    padding: 2px 8px;
    border-radius: 4px;
    margin-bottom: 0.7rem;
  }
  .project-body h3 {
    font-size: 1rem;
    font-weight: 600;
    color: var(--ink);
    margin-bottom: 0.5rem;
    line-height: 1.3;
  }
  .project-body p {
    font-size: 0.85rem;
    color: var(--slate);
    line-height: 1.6;
    flex: 1;
    margin-bottom: 1rem;
  }
  .project-meta {
    display: flex; gap: 0.6rem; flex-wrap: wrap;
  }
  .meta-pill {
    font-size: 0.72rem;
    color: var(--slate);
    background: var(--mist);
    border-radius: 4px;
    padding: 2px 7px;
  }

  /* ── Experience timeline ─────────────────────────────────────────────────── */
  #experience { background: var(--white); }
  .timeline { position: relative; padding-left: 2rem; }
  .timeline::before {
    content: '';
    position: absolute;
    left: 6px; top: 6px; bottom: 0;
    width: 2px;
    background: linear-gradient(to bottom, var(--teal), transparent);
  }
  .tl-item { position: relative; margin-bottom: 2.5rem; }
  .tl-dot {
    position: absolute;
    left: -2rem; top: 4px;
    width: 14px; height: 14px;
    border-radius: 50%;
    background: var(--teal);
    border: 2.5px solid var(--white);
    box-shadow: 0 0 0 2px var(--teal);
  }
  .tl-dot.gold { background: var(--gold); box-shadow: 0 0 0 2px var(--gold); }
  .tl-header {
    display: flex; align-items: baseline;
    justify-content: space-between;
    gap: 1rem;
    margin-bottom: 0.2rem;
    flex-wrap: wrap;
  }
  .tl-company {
    font-weight: 600;
    font-size: 1rem;
    color: var(--ink);
  }
  .tl-date {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.75rem;
    color: var(--teal);
    white-space: nowrap;
  }
  .tl-role {
    font-size: 0.88rem;
    color: var(--teal);
    font-style: italic;
    margin-bottom: 0.6rem;
  }
  .tl-bullets { list-style: none; }
  .tl-bullets li {
    font-size: 0.875rem;
    color: #334155;
    line-height: 1.6;
    padding-left: 1rem;
    position: relative;
    margin-bottom: 0.3rem;
  }
  .tl-bullets li::before {
    content: '›';
    position: absolute; left: 0;
    color: var(--teal);
    font-weight: 700;
  }

  /* ── Certifications ──────────────────────────────────────────────────────── */
  #certifications { background: var(--ink); }
  #certifications .section-title { color: var(--white); }
  #certifications .section-sub   { color: rgba(255,255,255,0.5); }
  #certifications .section-eyebrow { color: var(--teal); }
  .certs-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
    gap: 1rem;
  }
  .cert-card {
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,255,255,0.1);
    border-left: 3px solid var(--gold);
    border-radius: var(--radius);
    padding: 1.2rem 1.4rem;
    transition: background 0.2s, transform 0.2s;
  }
  .cert-card:hover { background: rgba(255,255,255,0.07); transform: translateY(-2px); }
  .cert-card h4 { font-size: 0.9rem; font-weight: 600; color: var(--white); margin-bottom: 0.2rem; }
  .cert-card p  { font-size: 0.78rem; color: rgba(255,255,255,0.45); }

  /* ── Education ───────────────────────────────────────────────────────────── */
  #education { background: var(--mist); }
  .edu-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 1.2rem;
  }
  .edu-card {
    background: var(--white);
    border-radius: var(--radius);
    padding: 1.6rem;
    border-top: 3px solid var(--teal);
    box-shadow: 0 2px 12px rgba(15,28,46,0.05);
  }
  .edu-card .year {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.75rem;
    color: var(--teal);
    margin-bottom: 0.4rem;
  }
  .edu-card h4 { font-size: 0.95rem; font-weight: 600; color: var(--ink); margin-bottom: 0.2rem; line-height: 1.3; }
  .edu-card p  { font-size: 0.82rem; color: var(--slate); }

  /* ── Contact ─────────────────────────────────────────────────────────────── */
  #contact {
    background: var(--ink);
    text-align: center;
    padding: 80px 5vw;
  }
  #contact .section-eyebrow { justify-content: center; }
  #contact .section-eyebrow::before { display: none; }
  #contact .section-title { color: var(--white); }
  #contact .section-sub { color: rgba(255,255,255,0.5); margin: 0 auto 2.5rem; }
  .contact-links {
    display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap;
  }
  .contact-pill {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 0.65rem 1.3rem;
    border-radius: 999px;
    font-size: 0.85rem;
    font-weight: 500;
    background: rgba(255,255,255,0.06);
    color: rgba(255,255,255,0.8);
    border: 1px solid rgba(255,255,255,0.12);
    transition: all 0.2s;
  }
  .contact-pill:hover { background: var(--teal); border-color: var(--teal); color: var(--white); }

  /* ── Footer ──────────────────────────────────────────────────────────────── */
  footer {
    background: #070F1A;
    text-align: center;
    padding: 1.2rem;
    font-size: 0.78rem;
    color: rgba(255,255,255,0.25);
  }
  footer span { color: var(--teal); }

  /* ── Scroll reveal ───────────────────────────────────────────────────────── */
  .reveal {
    opacity: 0;
    transform: translateY(22px);
    transition: opacity 0.55s ease, transform 0.55s ease;
  }
  .reveal.visible { opacity: 1; transform: none; }

  /* ── Responsive ──────────────────────────────────────────────────────────── */
  @media (max-width: 768px) {
    .hero { grid-template-columns: 1fr; padding-top: 80px; }
    .hero-stats { padding-left: 0; margin-top: 3rem; }
    .about-grid { grid-template-columns: 1fr; gap: 2rem; }
    .nav-links { display: none; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">Vele <span>Nemaheni</span></div>
  <div class="nav-links">
    <a href="#about">About</a>
    <a href="#projects">Projects</a>
    <a href="#experience">Experience</a>
    <a href="#certifications">Certifications</a>
    <a href="#contact">Contact</a>
  </div>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-text reveal">
    <div class="hero-eyebrow">E-learning Specialist &amp; Educational Consultant</div>
    <h1>Designing learning that <em>actually works.</em></h1>
    <p class="hero-bio">
      I build digital learning experiences that meet people where they are, from engineers in the DRC to English learners in Shanghai. Curriculum design, LMS architecture, and learner-centred pedagogy are my tools.
    </p>
    <div class="hero-actions">
      <a href="#projects" class="btn btn-primary">View Projects</a>
      <a href="#contact" class="btn btn-outline">Get in Touch</a>
    </div>
  </div>
  <div class="hero-stats reveal">
    <div class="stat-card">
      <div class="stat-num">6+</div>
      <div class="stat-label">Years teaching across 3 countries</div>
    </div>
    <div class="stat-card">
      <div class="stat-num">DRC</div>
      <div class="stat-label">Ongoing international programme since 2023</div>
    </div>
    <div class="stat-card">
      <div class="stat-num">4+</div>
      <div class="stat-label">LMS & e-learning platforms mastered</div>
    </div>
    <div class="stat-card">
      <div class="stat-num">ADDIE</div>
      <div class="stat-label">SAM · Blended · Remote · Adult learning</div>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="section-eyebrow">About</div>
  <h2 class="section-title">Pedagogy meets technology.</h2>
  <div class="about-grid">
    <div class="about-text reveal">
      <p>
        I'm Vele Nemaheni, an E-learning Specialist, Digital Educator, and Curriculum Developer based in South Africa. My work sits at the intersection of instructional design and educational technology, with a focus on making learning environments that are genuinely engaging rather than just functional.
      </p>
      <p>
        From designing blended courses at the University of Pretoria to running recurring 2-month intensive programmes for engineers in the Democratic Republic of Congo, I've built learning experiences for diverse audiences in high-pressure, cross-cultural contexts.
      </p>
      <p>
        I'm currently completing a BEd (Hons) in Computer Integrated Education, deepening the theoretical foundations behind the practical work I do every day.
      </p>
    </div>
    <div class="philosophy-card reveal">
      <blockquote>
        "The best learning design is invisible. Learners are too busy thinking to notice the scaffolding."
      </blockquote>
      <cite>Vele's design philosophy</cite>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="section-eyebrow">Skills</div>
  <h2 class="section-title">What I bring to the table.</h2>
  <p class="section-sub">A toolkit built across real classrooms, digital platforms, and international programmes.</p>
  <div class="skills-grid reveal">
    <div class="skill-card">
      <div class="skill-icon">🏗️</div>
      <h4>Instructional Design</h4>
      <p>ADDIE & SAM methodologies. Curriculum architecture from needs analysis to evaluation.</p>
    </div>
    <div class="skill-card">
      <div class="skill-icon">🖥️</div>
      <h4>LMS Management</h4>
      <p>Moodle, Google Classroom, Seesaw. Course builds, user management, analytics.</p>
    </div>
    <div class="skill-card">
      <div class="skill-icon">🎨</div>
      <h4>E-learning Tools</h4>
      <p>Articulate 360, Canva, Spark by Cengage. Interactive content and visual design.</p>
    </div>
    <div class="skill-card">
      <div class="skill-icon">🌍</div>
      <h4>Blended & Remote Delivery</h4>
      <p>Facilitation across time zones and cultures. Engagement strategies for distributed learners.</p>
    </div>
    <div class="skill-card">
      <div class="skill-icon">📊</div>
      <h4>Learning Analytics</h4>
      <p>Performance tracking, assessment design, and data-informed course iteration.</p>
    </div>
    <div class="skill-card">
      <div class="skill-icon">🧠</div>
      <h4>Adult Learning</h4>
      <p>Andragogy principles applied to professional and vocational learning contexts.</p>
    </div>
    <div class="skill-card">
      <div class="skill-icon">📝</div>
      <h4>Content Development</h4>
      <p>Lesson plans, assessments, and materials aligned to CAPS and international standards.</p>
    </div>
    <div class="skill-card">
      <div class="skill-icon">🤝</div>
      <h4>Project Coordination</h4>
      <p>Stakeholder collaboration, vendor negotiation, community programme management.</p>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="section-eyebrow">Projects</div>
  <h2 class="section-title">Selected work.</h2>
  <p class="section-sub">Real programmes, real learners, real outcomes. Each project below represents a distinct instructional design challenge.</p>
  <div class="projects-grid reveal">

    <div class="project-card">
      <div class="project-thumb drc"><span>🌍</span></div>
      <div class="project-body">
        <span class="project-tag">International Programme</span>
        <h3>DRC Engineering Language Programme</h3>
        <p>Recurring 2-month intensive English for Professional Purposes programme for engineers in the Democratic Republic of Congo. Running since 2023, designed around real workplace communication needs in technical environments.</p>
        <div class="project-meta">
          <span class="meta-pill">ESP Design</span>
          <span class="meta-pill">Remote Delivery</span>
          <span class="meta-pill">NGL Resources</span>
          <span class="meta-pill">Since 2023</span>
        </div>
      </div>
    </div>

    <div class="project-card">
      <div class="project-thumb blend"><span>💻</span></div>
      <div class="project-body">
        <span class="project-tag">Blended Learning</span>
        <h3>Digital-First EFL at Education First</h3>
        <p>Four years delivering fully digital English instruction to international learners in Shanghai. Introduced student-centred learning strategies and led co-curricular enrichment including a school-wide debate club.</p>
        <div class="project-meta">
          <span class="meta-pill">Digital Environment</span>
          <span class="meta-pill">Learner-Centred</span>
          <span class="meta-pill">Co-curricular</span>
          <span class="meta-pill">2018–2022</span>
        </div>
      </div>
    </div>

    <div class="project-card">
      <div class="project-thumb debate"><span>🎤</span></div>
      <div class="project-body">
        <span class="project-tag">Engagement Design</span>
        <h3>Holiday Learning Festivals</h3>
        <p>Designed and organised holiday learning festivals to convert traditionally low-engagement periods into structured, enriching learning experiences. Boosted learner participation and created a sense of community beyond the classroom.</p>
        <div class="project-meta">
          <span class="meta-pill">Event Design</span>
          <span class="meta-pill">Community Building</span>
          <span class="meta-pill">Engagement</span>
        </div>
      </div>
    </div>

    <div class="project-card">
      <div class="project-thumb lms"><span>⚙️</span></div>
      <div class="project-body">
        <span class="project-tag">LMS & Technology</span>
        <h3>Integrated Digital Learning at UoP</h3>
        <p>Ongoing integration of digital tools into adult learning programmes at the University of Pretoria, including LMS setup, performance tracking, and remote engagement strategies for diverse learner cohorts.</p>
        <div class="project-meta">
          <span class="meta-pill">Moodle</span>
          <span class="meta-pill">Seesaw</span>
          <span class="meta-pill">Analytics</span>
          <span class="meta-pill">2023–Present</span>
        </div>
      </div>
    </div>

  </div>
</section>

<!-- EXPERIENCE -->
<section id="experience">
  <div class="section-eyebrow">Experience</div>
  <h2 class="section-title">Career timeline.</h2>
  <p class="section-sub">A path built across classrooms, platforms, and continents.</p>
  <div class="timeline reveal">

    <div class="tl-item">
      <div class="tl-dot"></div>
      <div class="tl-header">
        <span class="tl-company">University of Pretoria</span>
        <span class="tl-date">Jul 2023 – Present</span>
      </div>
      <div class="tl-role">EFL Lecturer</div>
      <ul class="tl-bullets">
        <li>Designs and delivers English lessons to adult learners using National Geographic Learning resources.</li>
        <li>Leads recurring 2-month intensive instructional programmes for engineers in the DRC since 2023.</li>
        <li>Integrates digital tools to enhance remote learning engagement and performance tracking.</li>
      </ul>
    </div>

    <div class="tl-item">
      <div class="tl-dot"></div>
      <div class="tl-header">
        <span class="tl-company">Education First, Shanghai</span>
        <span class="tl-date">Aug 2018 – Aug 2022</span>
      </div>
      <div class="tl-role">English Teacher</div>
      <ul class="tl-bullets">
        <li>Delivered English instruction to international learners in a fully digital environment.</li>
        <li>Introduced and implemented student-centred learning strategies across all year groups.</li>
        <li>Led school debate club and organised holiday learning festivals to boost participation.</li>
      </ul>
    </div>

    <div class="tl-item">
      <div class="tl-dot gold"></div>
      <div class="tl-header">
        <span class="tl-company">Futures Academy</span>
        <span class="tl-date">Apr – May 2023</span>
      </div>
      <div class="tl-role">Intern Teacher</div>
      <ul class="tl-bullets">
        <li>Supported CAPS-based lesson planning and classroom instruction.</li>
        <li>Prepared assessments aligned with national learning standards.</li>
      </ul>
    </div>

    <div class="tl-item">
      <div class="tl-dot gold"></div>
      <div class="tl-header">
        <span class="tl-company">Hillsong Africa Foundation</span>
        <span class="tl-date">Jan – Dec 2017</span>
      </div>
      <div class="tl-role">Administration Intern</div>
      <ul class="tl-bullets">
        <li>Led community projects and negotiated vendor contracts.</li>
        <li>Supported organisational development through data analysis and stakeholder collaboration.</li>
      </ul>
    </div>

  </div>
</section>

<!-- CERTIFICATIONS -->
<section id="certifications">
  <div class="section-eyebrow">Credentials</div>
  <h2 class="section-title">Certifications.</h2>
  <p class="section-sub">Formally recognised qualifications underpinning the practical work.</p>
  <div class="certs-grid reveal">
    <div class="cert-card">
      <h4>TEFL Certificate</h4>
      <p>Teaching English as a Foreign Language</p>
    </div>
    <div class="cert-card">
      <h4>TKT Young Learners</h4>
      <p>Cambridge Assessment English</p>
    </div>
    <div class="cert-card">
      <h4>TKT Modules 1 &amp; 2</h4>
      <p>Cambridge Assessment English</p>
    </div>
    <div class="cert-card">
      <h4>SACE Teaching Licence</h4>
      <p>South African Council for Educators</p>
    </div>
  </div>
</section>

<!-- EDUCATION -->
<section id="education">
  <div class="section-eyebrow">Education</div>
  <h2 class="section-title">Academic foundation.</h2>
  <p class="section-sub">Theory that informs and sharpens practice.</p>
  <div class="edu-grid reveal">
    <div class="edu-card">
      <div class="year">In Progress</div>
      <h4>BEd (Hons) Computer Integrated Education</h4>
      <p>University of Pretoria</p>
    </div>
    <div class="edu-card">
      <div class="year">2023</div>
      <h4>Postgraduate Certificate in Education</h4>
      <p>Two Oceans Graduate Institute</p>
    </div>
    <div class="edu-card">
      <div class="year">2018</div>
      <h4>BA in Politics</h4>
      <p>University of Johannesburg</p>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="section-eyebrow">Contact</div>
  <h2 class="section-title">Let's work together.</h2>
  <p class="section-sub">Open to e-learning design projects, instructional consulting, and teaching roles. Based in South Africa and available internationally.</p>
  <div class="contact-links">
    <a href="mailto:velenemaheni@gmail.com" class="contact-pill">✉ velenemaheni@gmail.com</a>
    <a href="tel:+27817361666" class="contact-pill">✆ +27 81 736 1666</a>
    <a href="https://linkedin.com/in/velenemaheni" target="_blank" class="contact-pill">in linkedin.com/in/velenemaheni</a>
  </div>
</section>

<footer>
  &copy; 2026 <span>Vele Nemaheni</span> · E-learning Specialist · Built with purpose.
</footer>

<script>
  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.classList.add('visible'); io.unobserve(e.target); }
    });
  }, { threshold: 0.12 });
  reveals.forEach(r => io.observe(r));

  // Stagger children of grids
  document.querySelectorAll('.skills-grid, .projects-grid, .certs-grid, .edu-grid').forEach(grid => {
    Array.from(grid.children).forEach((child, i) => {
      child.style.transitionDelay = `${i * 0.07}s`;
    });
  });
</script>
</body>
</html>

