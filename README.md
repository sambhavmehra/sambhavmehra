<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sambhav Mehra — Cyber Security Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600;700;900&family=Share+Tech+Mono&family=Rajdhani:wght@300;400;600;700&display=swap" rel="stylesheet">
<style>
:root {
  --bg: #020408;
  --surface: rgba(5,15,25,0.9);
  --green: #00ff88;
  --cyan: #00e5ff;
  --red: #ff2d55;
  --purple: #bf5fff;
  --yellow: #ffe600;
  --orange: #ff6b2b;
  --white: #e8f4fd;
  --muted: #3a5068;
  --border: rgba(0,229,255,0.15);
  --glow-g: 0 0 20px rgba(0,255,136,0.4), 0 0 60px rgba(0,255,136,0.1);
  --glow-c: 0 0 20px rgba(0,229,255,0.4), 0 0 60px rgba(0,229,255,0.1);
  --glow-r: 0 0 20px rgba(255,45,85,0.4), 0 0 60px rgba(255,45,85,0.1);
}

*, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }

html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  color: var(--white);
  font-family: 'Share Tech Mono', monospace;
  overflow-x: hidden;
  cursor: none;
}

/* CUSTOM CURSOR */
.cursor {
  width: 16px; height: 16px;
  border: 1.5px solid var(--cyan);
  border-radius: 50%;
  position: fixed;
  pointer-events: none;
  z-index: 99999;
  transition: transform 0.1s, background 0.2s;
  mix-blend-mode: difference;
}
.cursor-dot {
  width: 4px; height: 4px;
  background: var(--cyan);
  border-radius: 50%;
  position: fixed;
  pointer-events: none;
  z-index: 99999;
  transform: translate(-50%,-50%);
}
body:hover .cursor { background: rgba(0,229,255,0.1); }

/* MATRIX CANVAS */
#matrix {
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  z-index: 0;
  opacity: 0.07;
}

/* NOISE OVERLAY */
body::after {
  content: '';
  position: fixed;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.4'/%3E%3C/svg%3E");
  opacity: 0.03;
  pointer-events: none;
  z-index: 1;
}

/* SCANLINES */
body::before {
  content: '';
  position: fixed;
  inset: 0;
  background: repeating-linear-gradient(0deg, transparent, transparent 3px, rgba(0,229,255,0.012) 3px, rgba(0,229,255,0.012) 4px);
  pointer-events: none;
  z-index: 2;
}

.page {
  position: relative;
  z-index: 10;
  max-width: 960px;
  margin: 0 auto;
  padding: 0 24px 80px;
}

/* ═══════════════════ HERO ═══════════════════ */
.hero {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 60px 20px;
  position: relative;
}

.hero-bg-ring {
  position: absolute;
  width: 600px; height: 600px;
  border: 1px solid rgba(0,229,255,0.06);
  border-radius: 50%;
  top: 50%; left: 50%;
  transform: translate(-50%, -50%);
  animation: ringRotate 20s linear infinite;
}
.hero-bg-ring::before {
  content: '';
  position: absolute;
  width: 4px; height: 4px;
  background: var(--cyan);
  border-radius: 50%;
  top: -2px; left: 50%;
  box-shadow: var(--glow-c);
}
.hero-bg-ring:nth-child(2) {
  width: 800px; height: 800px;
  border-color: rgba(0,255,136,0.04);
  animation-duration: 30s;
  animation-direction: reverse;
}
.hero-bg-ring:nth-child(2)::before { background: var(--green); top: auto; bottom: -2px; box-shadow: var(--glow-g); }
.hero-bg-ring:nth-child(3) {
  width: 400px; height: 400px;
  border-color: rgba(255,45,85,0.05);
  animation-duration: 15s;
}
.hero-bg-ring:nth-child(3)::before { background: var(--red); box-shadow: var(--glow-r); left: -2px; top: 50%; }

@keyframes ringRotate {
  from { transform: translate(-50%,-50%) rotate(0deg); }
  to { transform: translate(-50%,-50%) rotate(360deg); }
}

.status-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 6px 16px;
  border: 1px solid rgba(0,255,136,0.3);
  border-radius: 20px;
  font-size: 10px;
  color: var(--green);
  letter-spacing: 0.2em;
  text-transform: uppercase;
  margin-bottom: 32px;
  background: rgba(0,255,136,0.05);
}
.status-dot {
  width: 6px; height: 6px;
  background: var(--green);
  border-radius: 50%;
  animation: pulse 2s infinite;
}
@keyframes pulse {
  0%,100% { box-shadow: 0 0 0 0 rgba(0,255,136,0.4); }
  50% { box-shadow: 0 0 0 6px rgba(0,255,136,0); }
}

.hero-name {
  font-family: 'Orbitron', monospace;
  font-size: clamp(36px, 8vw, 80px);
  font-weight: 900;
  letter-spacing: 0.05em;
  line-height: 1;
  margin-bottom: 8px;
  position: relative;
}

.hero-name .line1 { color: var(--white); }
.hero-name .line2 {
  background: linear-gradient(90deg, var(--cyan), var(--green), var(--cyan));
  background-size: 200%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: shimmer 3s linear infinite;
}
@keyframes shimmer {
  from { background-position: 0% 50%; }
  to { background-position: 200% 50%; }
}

.glitch {
  position: relative;
}
.glitch::before, .glitch::after {
  content: attr(data-text);
  position: absolute;
  top: 0; left: 0;
  width: 100%;
}
.glitch::before {
  color: var(--red);
  animation: glitch1 3.5s infinite;
  clip-path: polygon(0 0, 100% 0, 100% 35%, 0 35%);
}
.glitch::after {
  color: var(--cyan);
  animation: glitch2 3.5s infinite;
  clip-path: polygon(0 65%, 100% 65%, 100% 100%, 0 100%);
}
@keyframes glitch1 {
  0%,90%,100% { transform: none; opacity: 0; }
  92% { transform: translate(-3px, 2px); opacity: 0.8; }
  94% { transform: translate(3px, -2px); opacity: 0.8; }
  96% { transform: translate(-2px, 0); opacity: 0.8; }
}
@keyframes glitch2 {
  0%,90%,100% { transform: none; opacity: 0; }
  91% { transform: translate(3px, -1px); opacity: 0.8; }
  93% { transform: translate(-3px, 2px); opacity: 0.8; }
  95% { transform: translate(2px, 1px); opacity: 0.8; }
}

.hero-title {
  font-family: 'Rajdhani', sans-serif;
  font-size: clamp(12px, 2vw, 16px);
  font-weight: 300;
  color: var(--cyan);
  letter-spacing: 0.4em;
  text-transform: uppercase;
  margin: 20px 0 12px;
}

.hero-sub {
  font-size: 11px;
  color: var(--muted);
  letter-spacing: 0.1em;
  margin-bottom: 40px;
}

.hero-links {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
  justify-content: center;
}

.hero-link {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 10px 22px;
  border-radius: 4px;
  font-size: 11px;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  text-decoration: none;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}
.hero-link::before {
  content: '';
  position: absolute;
  inset: 0;
  background: currentColor;
  opacity: 0;
  transition: opacity 0.3s;
}
.hero-link:hover::before { opacity: 0.1; }
.hero-link:hover { transform: translateY(-2px); }

.hero-link.primary {
  border: 1px solid var(--cyan);
  color: var(--cyan);
  box-shadow: 0 0 20px rgba(0,229,255,0.15);
}
.hero-link.primary:hover { box-shadow: var(--glow-c); }
.hero-link.secondary {
  border: 1px solid var(--green);
  color: var(--green);
}
.hero-link.secondary:hover { box-shadow: var(--glow-g); }
.hero-link.danger {
  border: 1px solid var(--red);
  color: var(--red);
}
.hero-link.danger:hover { box-shadow: var(--glow-r); }
.hero-link.gold {
  border: 1px solid var(--yellow);
  color: var(--yellow);
}
.hero-link.gold:hover { box-shadow: 0 0 20px rgba(255,230,0,0.3); }

.scroll-hint {
  position: absolute;
  bottom: 30px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  color: var(--muted);
  font-size: 9px;
  letter-spacing: 0.2em;
  text-transform: uppercase;
}
.scroll-arrow {
  width: 20px; height: 30px;
  border: 1px solid var(--muted);
  border-radius: 10px;
  position: relative;
}
.scroll-arrow::after {
  content: '';
  width: 4px; height: 4px;
  background: var(--cyan);
  border-radius: 50%;
  position: absolute;
  top: 6px; left: 50%;
  transform: translateX(-50%);
  animation: scrollDown 1.5s infinite;
}
@keyframes scrollDown {
  0% { top: 6px; opacity: 1; }
  100% { top: 18px; opacity: 0; }
}

/* ═══════════════════ SECTION HEADERS ═══════════════════ */
.sec {
  margin: 80px 0 0;
  animation: fadeUp 0.7s ease both;
}
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

.sec-label {
  display: flex;
  align-items: center;
  gap: 16px;
  margin-bottom: 32px;
}
.sec-num {
  font-family: 'Orbitron', monospace;
  font-size: 10px;
  color: var(--cyan);
  letter-spacing: 0.2em;
  opacity: 0.6;
}
.sec-title {
  font-family: 'Orbitron', monospace;
  font-size: clamp(16px, 3vw, 22px);
  font-weight: 700;
  color: var(--white);
  letter-spacing: 0.1em;
}
.sec-line {
  flex: 1;
  height: 1px;
  background: linear-gradient(90deg, var(--border), transparent);
}
.sec-icon {
  font-size: 18px;
  margin-right: 8px;
}

/* ═══════════════════ ABOUT ═══════════════════ */
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}
@media(max-width:600px) { .about-grid { grid-template-columns: 1fr; } }

.terminal-window {
  background: rgba(5,12,20,0.95);
  border: 1px solid var(--border);
  border-radius: 10px;
  overflow: hidden;
  position: relative;
}
.terminal-window::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(0,229,255,0.03) 0%, transparent 50%);
  pointer-events: none;
}
.tw-bar {
  background: rgba(0,229,255,0.05);
  padding: 10px 16px;
  display: flex;
  align-items: center;
  gap: 7px;
  border-bottom: 1px solid var(--border);
}
.tw-dot { width: 10px; height: 10px; border-radius: 50%; }
.tw-dot.r { background: #ff5f57; }
.tw-dot.y { background: #febc2e; }
.tw-dot.g { background: #28c840; }
.tw-title { color: var(--muted); font-size: 10px; margin-left: 6px; letter-spacing: 0.1em; }
.tw-body { padding: 20px; font-size: 11px; line-height: 2.2; }
.tw-body .k { color: var(--cyan); }
.tw-body .v { color: var(--yellow); }
.tw-body .s { color: var(--green); }
.tw-body .c { color: var(--muted); }
.blink-cursor {
  display: inline-block;
  width: 8px; height: 13px;
  background: var(--green);
  vertical-align: middle;
  margin-left: 2px;
  animation: blink 1s step-end infinite;
}
@keyframes blink { 50% { opacity: 0; } }

.stat-items {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}
.stat-item {
  background: rgba(5,12,20,0.95);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 18px;
  text-align: center;
  position: relative;
  overflow: hidden;
  transition: all 0.3s;
}
.stat-item::after {
  content: '';
  position: absolute;
  bottom: 0; left: 0; right: 0;
  height: 2px;
  background: currentColor;
  opacity: 0;
  transition: opacity 0.3s;
}
.stat-item:hover { transform: translateY(-4px); }
.stat-item:hover::after { opacity: 1; }
.stat-item.cyan { color: var(--cyan); }
.stat-item.green { color: var(--green); }
.stat-item.red { color: var(--red); }
.stat-item.purple { color: var(--purple); }
.stat-item:hover.cyan { box-shadow: 0 8px 30px rgba(0,229,255,0.15); border-color: rgba(0,229,255,0.3); }
.stat-item:hover.green { box-shadow: 0 8px 30px rgba(0,255,136,0.15); border-color: rgba(0,255,136,0.3); }
.stat-item:hover.red { box-shadow: 0 8px 30px rgba(255,45,85,0.15); border-color: rgba(255,45,85,0.3); }
.stat-item:hover.purple { box-shadow: 0 8px 30px rgba(191,95,255,0.15); border-color: rgba(191,95,255,0.3); }
.stat-num {
  font-family: 'Orbitron', monospace;
  font-size: 32px;
  font-weight: 900;
  display: block;
  line-height: 1;
  margin-bottom: 6px;
}
.stat-lbl { font-size: 9px; color: var(--muted); letter-spacing: 0.15em; text-transform: uppercase; }

/* ═══════════════════ SKILLS ═══════════════════ */
.skills-container {
  display: grid;
  grid-template-columns: repeat(3,1fr);
  gap: 16px;
}
@media(max-width:650px){ .skills-container { grid-template-columns: 1fr; } }

.skill-panel {
  background: rgba(5,12,20,0.95);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 24px;
  position: relative;
  overflow: hidden;
  transition: all 0.35s cubic-bezier(0.4,0,0.2,1);
}
.skill-panel::before {
  content: '';
  position: absolute;
  top: -50%; left: -50%;
  width: 200%; height: 200%;
  background: conic-gradient(from 0deg, transparent 0%, var(--accent-color) 5%, transparent 10%);
  opacity: 0;
  transition: opacity 0.4s;
  animation: radarSpin 3s linear infinite;
}
@keyframes radarSpin { to { transform: rotate(360deg); } }
.skill-panel:hover::before { opacity: 0.04; }
.skill-panel::after {
  content: '';
  position: absolute;
  inset: 1px;
  border-radius: 9px;
  background: rgba(5,12,20,0.98);
}

.skill-panel:hover { transform: translateY(-6px); }
.skill-panel.red { --accent-color: var(--red); border-top: 2px solid var(--red); }
.skill-panel.blue { --accent-color: var(--cyan); border-top: 2px solid var(--cyan); }
.skill-panel.green { --accent-color: var(--green); border-top: 2px solid var(--green); }
.skill-panel.red:hover { box-shadow: 0 20px 60px rgba(255,45,85,0.2); }
.skill-panel.blue:hover { box-shadow: 0 20px 60px rgba(0,229,255,0.2); }
.skill-panel.green:hover { box-shadow: 0 20px 60px rgba(0,255,136,0.2); }

.sp-inner { position: relative; z-index: 1; }
.sp-title {
  font-family: 'Orbitron', monospace;
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  margin-bottom: 18px;
  display: flex;
  align-items: center;
  gap: 8px;
}
.sp-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 7px;
}
.sp-tag {
  font-size: 10px;
  padding: 4px 10px;
  border-radius: 3px;
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(255,255,255,0.08);
  color: rgba(255,255,255,0.6);
  transition: all 0.2s;
  cursor: default;
}
.skill-panel:hover .sp-tag { border-color: rgba(255,255,255,0.15); color: rgba(255,255,255,0.85); }

/* ═══════════════════ PROJECTS ═══════════════════ */
.project-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}
@media(max-width:600px){ .project-grid { grid-template-columns: 1fr; } }

.proj-card {
  background: rgba(5,12,20,0.95);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 26px;
  position: relative;
  overflow: hidden;
  transition: all 0.35s cubic-bezier(0.4,0,0.2,1);
  cursor: default;
}
.proj-card::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(0,229,255,0.05) 0%, transparent 60%);
  opacity: 0;
  transition: opacity 0.3s;
}
.proj-card:hover { transform: translateY(-6px); border-color: rgba(0,229,255,0.25); box-shadow: 0 20px 60px rgba(0,229,255,0.1); }
.proj-card:hover::before { opacity: 1; }

.proj-card:nth-child(2)::before { background: linear-gradient(135deg, rgba(0,255,136,0.05) 0%, transparent 60%); }
.proj-card:nth-child(2):hover { border-color: rgba(0,255,136,0.25); box-shadow: 0 20px 60px rgba(0,255,136,0.1); }
.proj-card:nth-child(3)::before { background: linear-gradient(135deg, rgba(255,45,85,0.05) 0%, transparent 60%); }
.proj-card:nth-child(3):hover { border-color: rgba(255,45,85,0.25); box-shadow: 0 20px 60px rgba(255,45,85,0.1); }
.proj-card:nth-child(4)::before { background: linear-gradient(135deg, rgba(191,95,255,0.05) 0%, transparent 60%); }
.proj-card:nth-child(4):hover { border-color: rgba(191,95,255,0.25); box-shadow: 0 20px 60px rgba(191,95,255,0.1); }

.proj-num {
  font-family: 'Orbitron', monospace;
  font-size: 9px;
  color: var(--muted);
  letter-spacing: 0.2em;
  margin-bottom: 12px;
}
.proj-icon { font-size: 26px; margin-bottom: 12px; display: block; }
.proj-name {
  font-family: 'Orbitron', monospace;
  font-size: 13px;
  font-weight: 700;
  color: var(--white);
  margin-bottom: 8px;
  line-height: 1.3;
}
.proj-stack {
  font-size: 9px;
  color: var(--cyan);
  letter-spacing: 0.1em;
  margin-bottom: 14px;
  opacity: 0.8;
}
.proj-desc {
  font-size: 11px;
  color: rgba(200,220,240,0.55);
  line-height: 1.8;
}
.proj-corner {
  position: absolute;
  bottom: 16px; right: 16px;
  font-size: 20px;
  opacity: 0.08;
  transition: opacity 0.3s;
}
.proj-card:hover .proj-corner { opacity: 0.15; }

/* ═══════════════════ CERTIFICATIONS ═══════════════════ */
.cert-list { display: flex; flex-direction: column; gap: 10px; }
.cert-row {
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 16px 20px;
  background: rgba(5,12,20,0.95);
  border: 1px solid var(--border);
  border-radius: 8px;
  transition: all 0.25s;
  position: relative;
  overflow: hidden;
}
.cert-row::before {
  content: '';
  position: absolute;
  left: 0; top: 0; bottom: 0;
  width: 0;
  background: linear-gradient(90deg, rgba(0,229,255,0.08), transparent);
  transition: width 0.3s;
}
.cert-row:hover { border-color: rgba(0,229,255,0.2); transform: translateX(6px); }
.cert-row:hover::before { width: 100%; }
.cert-ico { font-size: 20px; flex-shrink: 0; }
.cert-info { flex: 1; }
.cert-name { font-size: 12px; color: var(--white); margin-bottom: 3px; }
.cert-issuer { font-size: 10px; color: var(--muted); }
.cert-badge {
  font-size: 9px;
  padding: 3px 10px;
  border-radius: 20px;
  border: 1px solid rgba(0,255,136,0.3);
  color: var(--green);
  letter-spacing: 0.1em;
  text-transform: uppercase;
  white-space: nowrap;
}

/* ═══════════════════ ACHIEVEMENTS ═══════════════════ */
.ach-grid {
  display: grid;
  grid-template-columns: repeat(3,1fr);
  gap: 14px;
}
@media(max-width:600px){ .ach-grid { grid-template-columns: 1fr; } }

.ach-card {
  background: rgba(5,12,20,0.95);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 24px 20px;
  text-align: center;
  position: relative;
  overflow: hidden;
  transition: all 0.3s;
}
.ach-card:hover { transform: translateY(-6px); }
.ach-card.gold:hover { box-shadow: 0 20px 60px rgba(255,230,0,0.15); border-color: rgba(255,230,0,0.3); }
.ach-card.silver:hover { box-shadow: 0 20px 60px rgba(200,220,240,0.1); border-color: rgba(200,220,240,0.2); }
.ach-card.bronze:hover { box-shadow: 0 20px 60px rgba(255,107,43,0.15); border-color: rgba(255,107,43,0.3); }

.ach-glow {
  position: absolute;
  width: 80px; height: 80px;
  border-radius: 50%;
  top: -20px; right: -20px;
  opacity: 0.15;
  filter: blur(20px);
}
.ach-card.gold .ach-glow { background: var(--yellow); }
.ach-card.silver .ach-glow { background: var(--white); }
.ach-card.bronze .ach-glow { background: var(--orange); }

.ach-icon-big { font-size: 36px; display: block; margin-bottom: 12px; }
.ach-title {
  font-family: 'Rajdhani', sans-serif;
  font-size: 13px;
  font-weight: 700;
  color: var(--white);
  margin-bottom: 6px;
  line-height: 1.3;
}
.ach-sub { font-size: 10px; color: var(--muted); }

/* ═══════════════════ GITHUB STATS ═══════════════════ */
.stats-section {
  background: rgba(5,12,20,0.95);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 32px;
  text-align: center;
  position: relative;
  overflow: hidden;
}
.stats-section::before {
  content: 'GITHUB STATS';
  position: absolute;
  top: 16px; right: 20px;
  font-size: 9px;
  color: var(--muted);
  letter-spacing: 0.2em;
}
.stats-imgs {
  display: flex;
  gap: 12px;
  justify-content: center;
  flex-wrap: wrap;
}
.stats-imgs img {
  border-radius: 6px;
  max-width: 100%;
  filter: brightness(0.9) saturate(1.2);
}

/* ═══════════════════ FOOTER ═══════════════════ */
.footer {
  margin-top: 80px;
  text-align: center;
  padding: 40px;
  border-top: 1px solid var(--border);
  position: relative;
}
.footer-glow {
  position: absolute;
  bottom: 0; left: 50%; transform: translateX(-50%);
  width: 300px; height: 100px;
  background: radial-gradient(ellipse, rgba(0,229,255,0.08) 0%, transparent 70%);
  pointer-events: none;
}
.footer-contacts {
  display: flex;
  gap: 24px;
  justify-content: center;
  flex-wrap: wrap;
  margin-bottom: 20px;
}
.footer-contact {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 11px;
  color: var(--muted);
  text-decoration: none;
  transition: color 0.2s;
}
.footer-contact:hover { color: var(--cyan); }
.footer-quote {
  font-size: 11px;
  color: var(--muted);
  font-style: italic;
  margin: 16px 0 10px;
}
.footer-quote span { color: var(--cyan); }
.footer-tagline {
  font-family: 'Orbitron', monospace;
  font-size: 10px;
  color: rgba(0,229,255,0.3);
  letter-spacing: 0.3em;
  text-transform: uppercase;
}
</style>
</head>
<body>

<canvas id="matrix"></canvas>
<div class="cursor" id="cursor"></div>
<div class="cursor-dot" id="cursorDot"></div>

<div class="page">

  <!-- ══ HERO ══ -->
  <section class="hero">
    <div class="hero-bg-ring"></div>
    <div class="hero-bg-ring"></div>
    <div class="hero-bg-ring"></div>

    <div class="status-badge">
      <div class="status-dot"></div>
      Available for Opportunities
    </div>

    <div class="hero-name">
      <div class="line1 glitch" data-text="SAMBHAV">SAMBHAV</div>
      <div class="line2">MEHRA</div>
    </div>

    <div class="hero-title">Cybersecurity Engineer &nbsp;·&nbsp; SOC Analyst &nbsp;·&nbsp; Ethical Hacker</div>
    <div class="hero-sub">B.Tech CSE – Cyber Security &nbsp;|&nbsp; SISTec Bhopal &nbsp;|&nbsp; CGPA: 7.13</div>

    <div class="hero-links">
      <a href="https://linkedin.com/in/sambhav-mehra-484427359" class="hero-link primary">⚡ LinkedIn</a>
      <a href="https://github.com/sambhavmehra" class="hero-link secondary">🐙 GitHub</a>
      <a href="https://instagram.com/sambhavv__7__" class="hero-link danger">📸 Instagram</a>
      <a href="https://buymeacoffee.com/sambhavv" class="hero-link gold">☕ Buy Me Coffee</a>
    </div>

    <div class="scroll-hint">
      <div class="scroll-arrow"></div>
      SCROLL
    </div>
  </section>

  <!-- ══ ABOUT ══ -->
  <section class="sec">
    <div class="sec-label">
      <span class="sec-num">01</span>
      <span class="sec-title"><span class="sec-icon">▸</span>WHOAMI</span>
      <div class="sec-line"></div>
    </div>
    <div class="about-grid">
      <div class="terminal-window">
        <div class="tw-bar">
          <div class="tw-dot r"></div><div class="tw-dot y"></div><div class="tw-dot g"></div>
          <span class="tw-title">bash — sambhav@kali:~$</span>
        </div>
        <div class="tw-body">
          <div><span class="c">// init profile</span></div>
          <div><span class="k">const</span> <span style="color:var(--purple)">sambhav</span> = {</div>
          <div>&nbsp; <span class="k">name</span>: <span class="v">"Sambhav Mehra"</span>,</div>
          <div>&nbsp; <span class="k">role</span>: <span class="v">"Cyber Security Eng."</span>,</div>
          <div>&nbsp; <span class="k">base</span>: <span class="v">"Bhopal, MP, India"</span>,</div>
          <div>&nbsp; <span class="k">focus</span>: [<span class="s">"SOC"</span>, <span class="s">"VAPT"</span>, <span class="s">"ML"</span>],</div>
          <div>&nbsp; <span class="k">status</span>: <span class="s">"open_to_work ✅"</span>,</div>
          <div>}</div>
          <div style="margin-top:6px"><span class="c">$ </span><span class="s">_</span><span class="blink-cursor"></span></div>
        </div>
      </div>
      <div class="stat-items">
        <div class="stat-item cyan">
          <span class="stat-num">4+</span>
          <span class="stat-lbl">Security Projects</span>
        </div>
        <div class="stat-item green">
          <span class="stat-num">5</span>
          <span class="stat-lbl">Certifications</span>
        </div>
        <div class="stat-item red">
          <span class="stat-num">#1</span>
          <span class="stat-lbl">CTF Champion</span>
        </div>
        <div class="stat-item purple">
          <span class="stat-num">∞</span>
          <span class="stat-lbl">Learning Mode</span>
        </div>
      </div>
    </div>
  </section>

  <!-- ══ SKILLS ══ -->
  <section class="sec">
    <div class="sec-label">
      <span class="sec-num">02</span>
      <span class="sec-title"><span class="sec-icon">▸</span>SKILL SET</span>
      <div class="sec-line"></div>
    </div>
    <div class="skills-container">
      <div class="skill-panel red">
        <div class="sp-inner">
          <div class="sp-title" style="color:var(--red)">🔴 Offensive Sec</div>
          <div class="sp-tags">
            <span class="sp-tag">Ethical Hacking</span>
            <span class="sp-tag">OWASP TOP 10</span>
            <span class="sp-tag">Metasploit</span>
            <span class="sp-tag">BurpSuite</span>
            <span class="sp-tag">Nmap</span>
            <span class="sp-tag">Cryptography</span>
            <span class="sp-tag">VAPT</span>
          </div>
        </div>
      </div>
      <div class="skill-panel blue">
        <div class="sp-inner">
          <div class="sp-title" style="color:var(--cyan)">🔵 SOC / Blue Team</div>
          <div class="sp-tags">
            <span class="sp-tag">MS Sentinel</span>
            <span class="sp-tag">KQL</span>
            <span class="sp-tag">Log Analysis</span>
            <span class="sp-tag">Wireshark</span>
            <span class="sp-tag">Networking</span>
            <span class="sp-tag">SIEM / IDS</span>
            <span class="sp-tag">SOAR</span>
          </div>
        </div>
      </div>
      <div class="skill-panel green">
        <div class="sp-inner">
          <div class="sp-title" style="color:var(--green)">🟢 Dev & Tools</div>
          <div class="sp-tags">
            <span class="sp-tag">Python</span>
            <span class="sp-tag">C++</span>
            <span class="sp-tag">JavaScript</span>
            <span class="sp-tag">React</span>
            <span class="sp-tag">scikit-learn</span>
            <span class="sp-tag">Git / GitHub</span>
            <span class="sp-tag">Linux</span>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ══ PROJECTS ══ -->
  <section class="sec">
    <div class="sec-label">
      <span class="sec-num">03</span>
      <span class="sec-title"><span class="sec-icon">▸</span>PROJECTS</span>
      <div class="sec-line"></div>
    </div>
    <div class="project-grid">
      <div class="proj-card">
        <div class="proj-num">PROJECT_01 // SOAR</div>
        <span class="proj-icon">🛡️</span>
        <div class="proj-name">SOAR SOC Assistant</div>
        <div class="proj-stack">> Python (Flask) · React · Agentic AI · ML</div>
        <div class="proj-desc">Real-time SOAR platform for SOC teams — AI-powered incident analysis, automated response, threat auto-blocking, virtual chatbot & AI report generation.</div>
        <span class="proj-corner">🛡</span>
      </div>
      <div class="proj-card">
        <div class="proj-num">PROJECT_02 // BLOCKCHAIN</div>
        <span class="proj-icon">🏥</span>
        <div class="proj-name">Secure Electronic Health Records</div>
        <div class="proj-stack">> Python · MetaMask · Ganache · HTML/CSS/JS</div>
        <div class="proj-desc">Blockchain-based patient data management ensuring privacy, integrity, and decentralized controlled access to sensitive medical records.</div>
        <span class="proj-corner">⛓</span>
      </div>
      <div class="proj-card">
        <div class="proj-num">PROJECT_03 // AI CHATBOT</div>
        <span class="proj-icon">🤖</span>
        <div class="proj-name">SHARVA — Cyber AI Chatbot</div>
        <div class="proj-stack">> Python · Groq API</div>
        <div class="proj-desc">Linux-based advanced AI assistant with dual-mode: general purpose everyday tasks and specialized cybersecurity mode for security professionals.</div>
        <span class="proj-corner">🤖</span>
      </div>
      <div class="proj-card">
        <div class="proj-num">PROJECT_04 // SIEM+IDS</div>
        <span class="proj-icon">📡</span>
        <div class="proj-name">SIEM + IDS Integration</div>
        <div class="proj-stack">> Python · Streamlit · ML</div>
        <div class="proj-desc">Real-time IDS & SIEM system — monitors traffic, detects threats via ML & rule-based techniques, auto-blocks malicious IPs and centralizes logging.</div>
        <span class="proj-corner">📡</span>
      </div>
    </div>
  </section>

  <!-- ══ CERTIFICATIONS ══ -->
  <section class="sec">
    <div class="sec-label">
      <span class="sec-num">04</span>
      <span class="sec-title"><span class="sec-icon">▸</span>CERTIFICATIONS</span>
      <div class="sec-line"></div>
    </div>
    <div class="cert-list">
      <div class="cert-row">
        <span class="cert-ico">🎯</span>
        <div class="cert-info">
          <div class="cert-name">Certified Ethical Hacker (CEH)</div>
          <div class="cert-issuer">Skill India</div>
        </div>
        <span class="cert-badge">✅ Certified</span>
      </div>
      <div class="cert-row">
        <span class="cert-ico">🌐</span>
        <div class="cert-info">
          <div class="cert-name">CCNA — Cisco Certified Network Associate</div>
          <div class="cert-issuer">Cisco Networking Academy</div>
        </div>
        <span class="cert-badge">✅ Certified</span>
      </div>
      <div class="cert-row">
        <span class="cert-ico">🔐</span>
        <div class="cert-info">
          <div class="cert-name">Practical Cyber Security for Practitioners</div>
          <div class="cert-issuer">NPTEL | IIT Kanpur</div>
        </div>
        <span class="cert-badge">✅ Completed</span>
      </div>
      <div class="cert-row">
        <span class="cert-ico">💻</span>
        <div class="cert-info">
          <div class="cert-name">Python Essentials</div>
          <div class="cert-issuer">Cisco Networking Academy</div>
        </div>
        <span class="cert-badge">✅ Completed</span>
      </div>
      <div class="cert-row">
        <span class="cert-ico">⚔️</span>
        <div class="cert-info">
          <div class="cert-name">Ethical Hacking Training</div>
          <div class="cert-issuer">Hacker Academy</div>
        </div>
        <span class="cert-badge">✅ Completed</span>
      </div>
    </div>
  </section>

  <!-- ══ ACHIEVEMENTS ══ -->
  <section class="sec">
    <div class="sec-label">
      <span class="sec-num">05</span>
      <span class="sec-title"><span class="sec-icon">▸</span>ACHIEVEMENTS</span>
      <div class="sec-line"></div>
    </div>
    <div class="ach-grid">
      <div class="ach-card gold">
        <div class="ach-glow"></div>
        <span class="ach-icon-big">🥇</span>
        <div class="ach-title">1st Place — CTF Event</div>
        <div class="ach-sub">"Crack the Hack" — College Level</div>
      </div>
      <div class="ach-card silver">
        <div class="ach-glow"></div>
        <span class="ach-icon-big">🎖️</span>
        <div class="ach-title">NCC 'A' Certificate</div>
        <div class="ach-sub">National Cadet Corps — Army Wing</div>
      </div>
      <div class="ach-card bronze">
        <div class="ach-glow"></div>
        <span class="ach-icon-big">🎪</span>
        <div class="ach-title">Event Coordinator</div>
        <div class="ach-sub">Techno-Cultural Events — College Level</div>
      </div>
    </div>
  </section>

  <!-- ══ GITHUB STATS ══ -->
  <section class="sec">
    <div class="sec-label">
      <span class="sec-num">06</span>
      <span class="sec-title"><span class="sec-icon">▸</span>GITHUB STATS</span>
      <div class="sec-line"></div>
    </div>
    <div class="stats-section">
      <div class="stats-imgs">
        <img src="https://github-readme-stats.vercel.app/api?username=sambhavmehra&theme=tokyonight&hide_border=true&show_icons=true&bg_color=050c14&title_color=00e5ff&icon_color=00ff88&text_color=c9d1d9" alt="GitHub Stats">
        <img src="https://nirzak-streak-stats.vercel.app/?user=sambhavmehra&theme=tokyonight&hide_border=true&background=050c14&ring=00e5ff&fire=ff2d55&currStreakLabel=00ff88" alt="Streak Stats">
        <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=sambhavmehra&theme=tokyonight&hide_border=true&layout=compact&bg_color=050c14&title_color=00e5ff&text_color=c9d1d9" alt="Top Languages">
      </div>
    </div>
  </section>

  <!-- ══ FOOTER ══ -->
  <footer class="footer">
    <div class="footer-glow"></div>
    <div class="footer-contacts">
      <a href="mailto:sambhavvmehra07@gmail.com" class="footer-contact">📧 sambhavvmehra07@gmail.com</a>
      <span class="footer-contact">📱 +91 9993016789</span>
      <span class="footer-contact">📍 Bhopal, MP, India</span>
    </div>
    <div class="footer-quote">"Security is not a product, but a process." — <span>Bruce Schneier</span></div>
    <div class="footer-tagline">⚡ &nbsp; Building · Breaking · Securing &nbsp; ⚡</div>
  </footer>

</div>

<script>
// ─── CUSTOM CURSOR ───
const cursor = document.getElementById('cursor');
const dot = document.getElementById('cursorDot');
let mx = 0, my = 0, cx = 0, cy = 0;
document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; dot.style.left = mx + 'px'; dot.style.top = my + 'px'; });
function animCursor() {
  cx += (mx - cx) * 0.12;
  cy += (my - cy) * 0.12;
  cursor.style.left = (cx - 8) + 'px';
  cursor.style.top = (cy - 8) + 'px';
  requestAnimationFrame(animCursor);
}
animCursor();
document.querySelectorAll('a, button, .proj-card, .skill-panel, .cert-row, .ach-card, .stat-item').forEach(el => {
  el.addEventListener('mouseenter', () => cursor.style.transform = 'scale(2)');
  el.addEventListener('mouseleave', () => cursor.style.transform = 'scale(1)');
});

// ─── MATRIX RAIN ───
const canvas = document.getElementById('matrix');
const ctx = canvas.getContext('2d');
function resizeCanvas() { canvas.width = window.innerWidth; canvas.height = window.innerHeight; }
resizeCanvas();
window.addEventListener('resize', resizeCanvas);

const chars = 'アイウエオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワヲン01アイ0110ヲン'.split('');
const fontSize = 14;
let columns = Math.floor(canvas.width / fontSize);
let drops = Array(columns).fill(1);

function drawMatrix() {
  ctx.fillStyle = 'rgba(2,4,8,0.05)';
  ctx.fillRect(0, 0, canvas.width, canvas.height);
  ctx.font = fontSize + 'px monospace';
  drops.forEach((y, i) => {
    const char = chars[Math.floor(Math.random() * chars.length)];
    const brightness = Math.random();
    if (brightness > 0.98) {
      ctx.fillStyle = '#ffffff';
    } else if (brightness > 0.9) {
      ctx.fillStyle = '#00ff88';
    } else {
      ctx.fillStyle = 'rgba(0,180,80,0.6)';
    }
    ctx.fillText(char, i * fontSize, y * fontSize);
    if (y * fontSize > canvas.height && Math.random() > 0.975) drops[i] = 0;
    drops[i]++;
  });
}
setInterval(drawMatrix, 50);

// ─── SCROLL REVEAL ───
const observer = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.style.animationPlayState = 'running';
      e.target.style.opacity = '1';
    }
  });
}, { threshold: 0.1 });

document.querySelectorAll('.sec').forEach((el, i) => {
  el.style.animationDelay = `${i * 0.05}s`;
  observer.observe(el);
});

// ─── TYPEWRITER EFFECT ───
function typewrite(el, text, speed = 60) {
  el.textContent = '';
  let i = 0;
  const timer = setInterval(() => {
    if (i < text.length) { el.textContent += text[i++]; }
    else clearInterval(timer);
  }, speed);
}
</script>
</body>
</html>
