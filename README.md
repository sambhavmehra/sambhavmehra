<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sambhav Mehra — GitHub Profile</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;600;700&family=Syne:wght@400;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #060a0f;
    --surface: #0d1117;
    --surface2: #111827;
    --border: #1e2d3d;
    --green: #00ff88;
    --cyan: #00d4ff;
    --red: #ff4757;
    --yellow: #ffd32a;
    --text: #c9d1d9;
    --muted: #6e7681;
    --white: #f0f6fc;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Scanline effect */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0,255,136,0.015) 2px, rgba(0,255,136,0.015) 4px);
    pointer-events: none;
    z-index: 1000;
  }

  .container {
    max-width: 900px;
    margin: 0 auto;
    padding: 40px 24px;
  }

  /* Hero */
  .hero {
    text-align: center;
    padding: 60px 20px 40px;
    position: relative;
  }

  .ascii-name {
    font-size: clamp(7px, 1.4vw, 13px);
    line-height: 1.2;
    color: var(--green);
    letter-spacing: 0.05em;
    text-shadow: 0 0 20px rgba(0,255,136,0.5);
    animation: flicker 6s infinite;
    white-space: pre;
    display: inline-block;
  }

  @keyframes flicker {
    0%,95%,100% { opacity: 1; }
    96% { opacity: 0.8; }
    97% { opacity: 1; }
    98% { opacity: 0.6; }
    99% { opacity: 1; }
  }

  .hero-role {
    font-family: 'Syne', sans-serif;
    font-size: 13px;
    font-weight: 400;
    color: var(--cyan);
    letter-spacing: 0.3em;
    text-transform: uppercase;
    margin: 20px 0 8px;
  }

  .hero-sub {
    font-size: 11px;
    color: var(--muted);
    margin-bottom: 28px;
  }

  .badges {
    display: flex;
    gap: 10px;
    justify-content: center;
    flex-wrap: wrap;
  }

  .badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 6px 14px;
    border: 1px solid var(--border);
    border-radius: 4px;
    font-size: 11px;
    text-decoration: none;
    color: var(--text);
    transition: all 0.2s ease;
    background: var(--surface2);
  }

  .badge:hover { border-color: var(--green); color: var(--green); transform: translateY(-2px); box-shadow: 0 4px 15px rgba(0,255,136,0.15); }
  .badge.red:hover { border-color: var(--red); color: var(--red); box-shadow: 0 4px 15px rgba(255,71,87,0.15); }
  .badge.cyan:hover { border-color: var(--cyan); color: var(--cyan); box-shadow: 0 4px 15px rgba(0,212,255,0.15); }
  .badge.yellow:hover { border-color: var(--yellow); color: var(--yellow); box-shadow: 0 4px 15px rgba(255,211,42,0.15); }

  /* Section */
  .section {
    margin: 48px 0;
    animation: fadeUp 0.6s ease both;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .section:nth-child(2) { animation-delay: 0.1s; }
  .section:nth-child(3) { animation-delay: 0.2s; }
  .section:nth-child(4) { animation-delay: 0.3s; }
  .section:nth-child(5) { animation-delay: 0.4s; }

  .section-header {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 20px;
  }

  .section-header .prompt {
    color: var(--green);
    font-size: 13px;
  }

  .section-header .cmd {
    color: var(--cyan);
    font-size: 13px;
  }

  .divider {
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
    margin: 8px 0 24px;
  }

  /* Whoami box */
  .code-block {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 20px 24px;
    font-size: 12px;
    line-height: 2;
    position: relative;
    overflow: hidden;
  }

  .code-block::before {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    width: 3px;
    background: var(--green);
    border-radius: 3px 0 0 3px;
  }

  .yaml-key { color: var(--cyan); }
  .yaml-val { color: var(--yellow); }
  .yaml-str { color: var(--green); }

  /* Skills grid */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
  }

  @media (max-width: 600px) { .skills-grid { grid-template-columns: 1fr; } }

  .skill-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 20px;
    transition: all 0.25s ease;
    position: relative;
    overflow: hidden;
  }

  .skill-card:hover { transform: translateY(-4px); }

  .skill-card.red { border-top: 2px solid var(--red); }
  .skill-card.red:hover { box-shadow: 0 8px 30px rgba(255,71,87,0.15); }
  .skill-card.blue { border-top: 2px solid var(--cyan); }
  .skill-card.blue:hover { box-shadow: 0 8px 30px rgba(0,212,255,0.15); }
  .skill-card.green { border-top: 2px solid var(--green); }
  .skill-card.green:hover { box-shadow: 0 8px 30px rgba(0,255,136,0.15); }

  .skill-title {
    font-family: 'Syne', sans-serif;
    font-size: 12px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.15em;
    margin-bottom: 14px;
    display: flex;
    align-items: center;
    gap: 6px;
  }

  .skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }

  .tag {
    font-size: 10px;
    padding: 3px 8px;
    border-radius: 3px;
    background: rgba(255,255,255,0.05);
    border: 1px solid var(--border);
    color: var(--text);
  }

  /* Projects */
  .project-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 22px 24px;
    margin-bottom: 14px;
    transition: all 0.25s ease;
    cursor: default;
    position: relative;
    overflow: hidden;
  }

  .project-card::after {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(0,255,136,0.03) 0%, transparent 60%);
    opacity: 0;
    transition: opacity 0.3s;
  }

  .project-card:hover { border-color: rgba(0,255,136,0.3); transform: translateX(4px); }
  .project-card:hover::after { opacity: 1; }

  .project-name {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    color: var(--white);
    font-size: 15px;
    margin-bottom: 6px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .project-stack {
    font-size: 10px;
    color: var(--cyan);
    margin-bottom: 10px;
    letter-spacing: 0.05em;
  }

  .project-desc {
    font-size: 11px;
    color: var(--muted);
    line-height: 1.7;
  }

  /* Certs table */
  .cert-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 12px;
  }

  .cert-table th {
    text-align: left;
    padding: 10px 16px;
    color: var(--muted);
    font-weight: 400;
    font-size: 10px;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    border-bottom: 1px solid var(--border);
  }

  .cert-table td {
    padding: 12px 16px;
    border-bottom: 1px solid rgba(30,45,61,0.5);
  }

  .cert-table tr:hover td { background: rgba(255,255,255,0.02); }

  .cert-name { color: var(--white); }
  .cert-issuer { color: var(--muted); }
  .cert-status { color: var(--green); }

  /* Achievements */
  .achievement {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 14px 20px;
    margin-bottom: 10px;
    font-size: 12px;
    display: flex;
    align-items: center;
    gap: 12px;
    transition: border-color 0.2s;
  }

  .achievement:hover { border-color: var(--yellow); }
  .achievement .ach-icon { font-size: 18px; }
  .achievement .ach-tag { color: var(--green); margin-right: 8px; }

  /* Stats */
  .stats-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }

  @media(max-width:500px) { .stats-grid { grid-template-columns: 1fr; } }

  .stat-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 20px;
    text-align: center;
  }

  .stat-number {
    font-family: 'Syne', sans-serif;
    font-size: 36px;
    font-weight: 800;
    color: var(--green);
    text-shadow: 0 0 20px rgba(0,255,136,0.4);
    display: block;
  }

  .stat-label {
    font-size: 10px;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 0.15em;
    margin-top: 4px;
  }

  /* Footer */
  .footer {
    text-align: center;
    padding: 40px 20px;
    border-top: 1px solid var(--border);
    margin-top: 60px;
  }

  .contact-line {
    font-size: 12px;
    color: var(--muted);
    margin-bottom: 16px;
    display: flex;
    gap: 20px;
    justify-content: center;
    flex-wrap: wrap;
  }

  .contact-line a { color: var(--text); text-decoration: none; }
  .contact-line a:hover { color: var(--green); }

  .quote {
    font-size: 12px;
    color: var(--muted);
    font-style: italic;
    margin: 16px 0;
  }

  .quote span { color: var(--green); }

  .cursor {
    display: inline-block;
    width: 8px;
    height: 14px;
    background: var(--green);
    vertical-align: middle;
    margin-left: 2px;
    animation: blink 1s step-end infinite;
  }

  @keyframes blink {
    0%,100% { opacity: 1; }
    50% { opacity: 0; }
  }

  /* Terminal dots */
  .terminal-bar {
    background: #1a2332;
    border: 1px solid var(--border);
    border-bottom: none;
    border-radius: 8px 8px 0 0;
    padding: 8px 16px;
    display: flex;
    align-items: center;
    gap: 6px;
  }

  .dot { width: 10px; height: 10px; border-radius: 50%; }
  .dot.r { background: #ff5f57; }
  .dot.y { background: #febc2e; }
  .dot.g { background: #28c840; }
  .t-title { color: var(--muted); font-size: 10px; margin-left: 8px; }

  .terminal-body {
    background: var(--surface);
    border: 1px solid var(--border);
    border-top: none;
    border-radius: 0 0 8px 8px;
    padding: 20px 24px;
  }

</style>
</head>
<body>

<div class="container">

  <!-- HERO -->
  <div class="hero">
    <div class="ascii-name">███████╗ █████╗ ███╗   ███╗██████╗ ██╗  ██╗ █████╗ ██╗   ██╗
██╔════╝██╔══██╗████╗ ████║██╔══██╗██║  ██║██╔══██╗██║   ██║
███████╗███████║██╔████╔██║██████╔╝███████║███████║██║   ██║
╚════██║██╔══██║██║╚██╔╝██║██╔══██╗██╔══██║██╔══██║╚██╗ ██╔╝
███████║██║  ██║██║ ╚═╝ ██║██████╔╝██║  ██║██║  ██║ ╚████╔╝ 
╚══════╝╚═╝  ╚═╝╚═╝     ╚═╝╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═╝  ╚═══╝</div>
    <div class="hero-role">Cybersecurity Engineer · SOC Analyst · Ethical Hacker</div>
    <div class="hero-sub">B.Tech CSE – Cyber Security @ SISTec, Bhopal &nbsp;|&nbsp; CGPA: 7.13</div>
    <div class="badges">
      <a class="badge cyan" href="#">⚡ LinkedIn</a>
      <a class="badge red" href="#">📸 Instagram</a>
      <a class="badge" href="#">🐙 GitHub</a>
      <a class="badge yellow" href="#">☕ Buy Me Coffee</a>
    </div>
  </div>

  <!-- ABOUT -->
  <div class="section">
    <div class="section-header">
      <span class="prompt">$</span>
      <span class="cmd">cat about.txt</span>
    </div>
    <div class="divider"></div>
    <div class="terminal-bar">
      <div class="dot r"></div><div class="dot y"></div><div class="dot g"></div>
      <span class="t-title">bash — sambhav@kali:~$</span>
    </div>
    <div class="terminal-body">
      <div class="code-block" style="border:none;background:transparent;padding:0">
        <div><span class="yaml-key">name      </span>: <span class="yaml-str">Sambhav Mehra</span></div>
        <div><span class="yaml-key">role      </span>: <span class="yaml-str">Cybersecurity Enthusiast & Developer</span></div>
        <div><span class="yaml-key">location  </span>: <span class="yaml-str">Bhopal, Madhya Pradesh, India</span></div>
        <div><span class="yaml-key">focus     </span>: <span class="yaml-val">Threat Analysis · Vulnerability Assessment · SOC Ops</span></div>
        <div><span class="yaml-key">mission   </span>: <span class="yaml-str">Protect digital assets & strengthen org security</span></div>
        <div><span class="yaml-key">status    </span>: <span style="color:var(--green)">Open to Opportunities ✅</span></div>
        <div style="margin-top:8px;color:var(--muted)">█<span class="cursor"></span></div>
      </div>
    </div>
  </div>

  <!-- SKILLS -->
  <div class="section">
    <div class="section-header">
      <span class="prompt">$</span>
      <span class="cmd">ls -la skills/</span>
    </div>
    <div class="divider"></div>
    <div class="skills-grid">
      <div class="skill-card red">
        <div class="skill-title" style="color:var(--red)">🔴 Offensive Security</div>
        <div class="skill-tags">
          <span class="tag">Ethical Hacking</span>
          <span class="tag">OWASP TOP 10</span>
          <span class="tag">Metasploit</span>
          <span class="tag">BurpSuite</span>
          <span class="tag">Nmap</span>
          <span class="tag">Cryptography</span>
        </div>
      </div>
      <div class="skill-card blue">
        <div class="skill-title" style="color:var(--cyan)">🔵 SOC & Blue Team</div>
        <div class="skill-tags">
          <span class="tag">MS Sentinel</span>
          <span class="tag">KQL</span>
          <span class="tag">Log Analysis</span>
          <span class="tag">Wireshark</span>
          <span class="tag">Networking</span>
          <span class="tag">SIEM/IDS</span>
        </div>
      </div>
      <div class="skill-card green">
        <div class="skill-title" style="color:var(--green)">🟢 Development</div>
        <div class="skill-tags">
          <span class="tag">Python</span>
          <span class="tag">C++</span>
          <span class="tag">JavaScript</span>
          <span class="tag">React</span>
          <span class="tag">HTML/CSS</span>
          <span class="tag">scikit-learn</span>
        </div>
      </div>
    </div>
  </div>

  <!-- PROJECTS -->
  <div class="section">
    <div class="section-header">
      <span class="prompt">$</span>
      <span class="cmd">cat projects.json</span>
    </div>
    <div class="divider"></div>

    <div class="project-card">
      <div class="project-name">🛡️ SOAR SOC Assistant</div>
      <div class="project-stack">> Stack: Python (Flask) · React · Agentic AI · ML</div>
      <div class="project-desc">Real-time SOAR platform for SOC teams — AI-powered incident analysis, automated response, threat auto-blocking, virtual chatbot assistant, and AI report generation.</div>
    </div>

    <div class="project-card">
      <div class="project-name">🏥 Secure Electronic Health Records</div>
      <div class="project-stack">> Stack: Python · MetaMask · Ganache (Blockchain) · HTML/CSS/JS</div>
      <div class="project-desc">Blockchain-based patient data management ensuring full privacy, integrity, and decentralized controlled access to sensitive medical records.</div>
    </div>

    <div class="project-card">
      <div class="project-name">🤖 SHARVA — Cybersecurity AI Chatbot</div>
      <div class="project-stack">> Stack: Python · Groq API</div>
      <div class="project-desc">Linux-based advanced AI assistant with dual-mode: general purpose everyday tasks and specialized cybersecurity mode for security professionals.</div>
    </div>

    <div class="project-card">
      <div class="project-name">📡 SIEM + IDS Integration</div>
      <div class="project-stack">> Stack: Python · Streamlit · ML</div>
      <div class="project-desc">Real-time IDS & SIEM system — monitors network traffic, detects threats via rule-based & ML techniques, auto-blocks malicious IPs, and centralizes logging.</div>
    </div>
  </div>

  <!-- CERTIFICATIONS -->
  <div class="section">
    <div class="section-header">
      <span class="prompt">$</span>
      <span class="cmd">cat certifications.txt</span>
    </div>
    <div class="divider"></div>
    <div style="background:var(--surface);border:1px solid var(--border);border-radius:8px;overflow:hidden">
      <table class="cert-table">
        <thead>
          <tr>
            <th>Certification</th>
            <th>Issuer</th>
            <th>Status</th>
          </tr>
        </thead>
        <tbody>
          <tr><td class="cert-name">🎯 Certified Ethical Hacker (CEH)</td><td class="cert-issuer">Skill India</td><td class="cert-status">✅ Certified</td></tr>
          <tr><td class="cert-name">🌐 CCNA</td><td class="cert-issuer">Cisco Networking Academy</td><td class="cert-status">✅ Certified</td></tr>
          <tr><td class="cert-name">🔐 Practical Cyber Security</td><td class="cert-issuer">NPTEL | IIT Kanpur</td><td class="cert-status">✅ Completed</td></tr>
          <tr><td class="cert-name">💻 Python Essentials</td><td class="cert-issuer">Cisco Networking Academy</td><td class="cert-status">✅ Completed</td></tr>
          <tr><td class="cert-name">⚔️ Ethical Hacking Training</td><td class="cert-issuer">Hacker Academy</td><td class="cert-status">✅ Completed</td></tr>
        </tbody>
      </table>
    </div>
  </div>

  <!-- ACHIEVEMENTS -->
  <div class="section">
    <div class="section-header">
      <span class="prompt">$</span>
      <span class="cmd">sudo cat achievements.log</span>
    </div>
    <div class="divider"></div>
    <div class="achievement">
      <span class="ach-icon">🥇</span>
      <div><span class="ach-tag">[SUCCESS]</span> 1st Place — "Crack the Hack" CTF Event <span style="color:var(--muted)">(College Level)</span></div>
    </div>
    <div class="achievement">
      <span class="ach-icon">🎖️</span>
      <div><span class="ach-tag">[SUCCESS]</span> NCC 'A' Certificate — National Cadet Corps (Army Wing)</div>
    </div>
    <div class="achievement">
      <span class="ach-icon">🎪</span>
      <div><span class="ach-tag">[SUCCESS]</span> Coordinated multiple techno-cultural events at college level</div>
    </div>
  </div>

  <!-- STATS -->
  <div class="section">
    <div class="section-header">
      <span class="prompt">$</span>
      <span class="cmd">git stats --user=sambhavmehra</span>
    </div>
    <div class="divider"></div>
    <div class="stats-grid">
      <div class="stat-card">
        <span class="stat-number">4+</span>
        <span class="stat-label">Security Projects</span>
      </div>
      <div class="stat-card">
        <span class="stat-number">5</span>
        <span class="stat-label">Certifications</span>
      </div>
      <div class="stat-card">
        <span class="stat-number">#1</span>
        <span class="stat-label">CTF Champion</span>
      </div>
      <div class="stat-card">
        <span class="stat-number">∞</span>
        <span class="stat-label">Learning Mode</span>
      </div>
    </div>
    <div style="text-align:center;margin-top:20px;font-size:11px;color:var(--muted)">
      📊 Live stats powered by <span style="color:var(--cyan)">github-readme-stats · nirzak-streak-stats</span>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <div class="contact-line">
      <a href="mailto:sambhavvmehra07@gmail.com">📧 sambhavvmehra07@gmail.com</a>
      <span>📱 +91 9993016789</span>
      <span>📍 Bhopal, MP, India</span>
    </div>
    <div class="quote">"Security is not a product, but a process." — <span>Bruce Schneier</span></div>
    <div style="font-size:11px;color:var(--muted);margin-top:16px">
      ⚡ Actively learning · Building · Breaking · Securing ⚡
    </div>
  </div>

</div>

</body>
</html>
