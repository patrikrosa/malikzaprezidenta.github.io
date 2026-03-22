<!DOCTYPE html>
<html lang="sk">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>PhDr. Branislav Malík, CSc. – Prezident 2029</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=DM+Sans:wght@300;400;500;700&display=swap" rel="stylesheet">
<!-- Lenis smooth scroll -->
<script src="https://cdn.jsdelivr.net/npm/@studio-freight/lenis@1.0.42/dist/lenis.min.js"></script>
<!-- GSAP + ScrollTrigger -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js"></script>
<style>
:root {
  --gold: #D4AF37;
  --gold-light: #f0cc5a;
  --gold-dim: rgba(212,175,55,0.15);
  --dark: #06090f;
  --dark2: #0d1420;
  --dark3: #111827;
  --text: #e8eaf0;
  --muted: rgba(232,234,240,0.55);
  --radius: 20px;
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: auto; }

body {
  font-family: 'DM Sans', sans-serif;
  background: var(--dark);
  color: var(--text);
  overflow-x: hidden;
}

/* ─── NOISE TEXTURE ─── */
body::before {
  content: '';
  position: fixed; inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='1'/%3E%3C/svg%3E");
  opacity: 0.028;
  pointer-events: none;
  z-index: 9000;
}

/* ─── CURSOR ─── */
.cursor {
  position: fixed;
  width: 14px; height: 14px;
  background: var(--gold);
  border-radius: 50%;
  pointer-events: none;
  z-index: 9999;
  transform: translate(-50%,-50%);
  transition: width .2s, height .2s, opacity .2s;
  mix-blend-mode: normal;
  box-shadow:
    0 0 8px 3px rgba(212,175,55,0.9),
    0 0 20px 6px rgba(212,175,55,0.45),
    0 0 40px 10px rgba(212,175,55,0.15);
}
.cursor-ring {
  position: fixed;
  width: 36px; height: 36px;
  border: 1.5px solid rgba(212,175,55,0.5);
  border-radius: 50%;
  pointer-events: none;
  z-index: 9998;
  transform: translate(-50%,-50%);
  transition: transform .12s ease, width .2s, height .2s;
}

/* ─── NAVBAR ─── */
header {
  position: fixed; top: 0; left: 0; right: 0;
  z-index: 1000;
  padding: 0 40px;
  transition: background .4s;
}
header.scrolled {
  background: rgba(6,9,15,0.85);
  backdrop-filter: blur(20px);
  border-bottom: 1px solid rgba(212,175,55,0.08);
}
nav {
  max-width: 1200px;
  margin: auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 22px 0;
}
.nav-logo {
  font-family: 'Playfair Display', serif;
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--gold);
  letter-spacing: 0.04em;
  text-decoration: none;
}
.nav-links { display: flex; gap: 36px; list-style: none; }
.nav-links a {
  color: rgba(232,234,240,0.75);
  text-decoration: none;
  font-size: 0.9rem;
  font-weight: 500;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  transition: color .2s;
}
.nav-links a:hover { color: var(--gold); }
.nav-links a {
  position: relative;
}
.nav-links a::after {
  content: '';
  position: absolute;
  bottom: -4px; left: 0;
  width: 0; height: 1px;
  background: var(--gold);
  transition: width .3s ease;
}
.nav-links a:hover::after { width: 100%; }

/* ─── HERO ─── */
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  position: relative;
  text-align: center;
  overflow: hidden;
  padding: 90px 24px 120px;
}

/* Animated mesh background */
.hero-bg {
  position: absolute; inset: 0;
  background:
    radial-gradient(ellipse 80% 60% at 20% 30%, rgba(212,175,55,0.09), transparent 60%),
    radial-gradient(ellipse 60% 80% at 80% 70%, rgba(212,175,55,0.06), transparent 60%),
    linear-gradient(160deg, #0d1420 0%, #06090f 100%);
  animation: meshShift 16s ease-in-out infinite alternate;
}
@keyframes meshShift {
  0%   { background-position: 0% 50%; }
  100% { background-position: 100% 50%; }
}

/* Floating orbs */
.orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  pointer-events: none;
  animation: orbFloat linear infinite;
}
.orb1 {
  width: 500px; height: 500px;
  background: radial-gradient(circle, rgba(212,175,55,0.12), transparent 70%);
  top: -100px; left: -150px;
  animation-duration: 22s;
  animation-direction: alternate;
}
.orb2 {
  width: 400px; height: 400px;
  background: radial-gradient(circle, rgba(240,204,90,0.08), transparent 70%);
  bottom: -80px; right: -100px;
  animation-duration: 18s;
  animation-direction: alternate-reverse;
}
@keyframes orbFloat {
  0%   { transform: translate(0,0) scale(1); }
  50%  { transform: translate(40px,-30px) scale(1.08); }
  100% { transform: translate(-20px,20px) scale(0.95); }
}

/* Diagonal lines decoration */
.hero-lines {
  position: absolute; inset: 0;
  overflow: hidden;
  opacity: 0.04;
}
.hero-lines::before,
.hero-lines::after {
  content: '';
  position: absolute;
  width: 2px; height: 200%;
  background: var(--gold);
  top: -50%;
}
.hero-lines::before { left: 20%; transform: rotate(12deg); }
.hero-lines::after  { right: 20%; transform: rotate(-12deg); }

.hero-inner {
  position: relative; z-index: 2;
  max-width: 860px;
}
.hero-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 28px;
  opacity: 0;
  animation: fadeUp .8s .2s forwards;
}
.hero-eyebrow::before,
.hero-eyebrow::after {
  content: '';
  display: block;
  width: 32px; height: 1px;
  background: var(--gold);
  opacity: 0.5;
}
.hero h1 {
  font-family: 'Playfair Display', serif;
  font-size: clamp(2.8rem, 6vw, 5rem);
  font-weight: 900;
  line-height: 1.05;
  background: linear-gradient(135deg, #fff 0%, var(--gold-light) 50%, var(--gold) 100%);
  -webkit-background-clip: text;
  color: transparent;
  margin-bottom: 24px;
  opacity: 0;
  animation: fadeUp .9s .4s forwards;
}
.hero-sub {
  font-size: 1.15rem;
  color: var(--muted);
  max-width: 600px;
  margin: 0 auto 44px;
  line-height: 1.7;
  font-weight: 300;
  opacity: 0;
  animation: fadeUp .9s .6s forwards;
}
.hero-ctas {
  display: flex;
  gap: 16px;
  justify-content: center;
  flex-wrap: wrap;
  opacity: 0;
  animation: fadeUp .9s .8s forwards;
}
.btn-primary {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 16px 32px;
  border-radius: 999px;
  background: linear-gradient(90deg, var(--gold), var(--gold-light));
  color: #07080b;
  font-weight: 700;
  font-size: 0.95rem;
  text-decoration: none;
  transition: transform .25s, box-shadow .25s;
  box-shadow: 0 8px 40px rgba(212,175,55,0.25);
}
.btn-primary:hover {
  transform: translateY(-3px);
  box-shadow: 0 18px 50px rgba(212,175,55,0.38);
}
.btn-ghost {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 16px 32px;
  border-radius: 999px;
  border: 1px solid rgba(212,175,55,0.35);
  color: var(--gold);
  font-weight: 600;
  font-size: 0.95rem;
  text-decoration: none;
  transition: background .25s, border-color .25s;
  background: transparent;
}
.btn-ghost:hover {
  background: rgba(212,175,55,0.08);
  border-color: var(--gold);
}

/* Stats bar */
.stats-bar {
  display: flex;
  gap: 60px;
  z-index: 2;
  opacity: 0;
  animation: fadeUp .9s 1.1s forwards;
  margin-top: 56px;
  padding-bottom: 8px;
}
.stat-item { text-align: center; }
.stat-num {
  font-family: 'Playfair Display', serif;
  font-size: 2rem;
  font-weight: 700;
  color: var(--gold);
  line-height: 1;
}
.stat-label {
  font-size: 0.75rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--muted);
  margin-top: 6px;
}
.stat-divider {
  width: 1px;
  background: rgba(212,175,55,0.2);
  align-self: stretch;
}

/* Scroll indicator */
.scroll-hint {
  position: absolute;
  bottom: 28px;
  right: 44px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 6px;
  font-size: 0.7rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--muted);
  z-index: 2;
  opacity: 0;
  animation: fadeIn 1s 1.4s forwards;
}
@media (max-width: 900px) { .scroll-hint { display: none; } }
.scroll-line {
  width: 1px; height: 44px;
  background: linear-gradient(to bottom, var(--gold), transparent);
  animation: scrollPulse 2s ease-in-out infinite;
}
@keyframes scrollPulse {
  0%,100% { transform: scaleY(1); opacity: 1; }
  50%      { transform: scaleY(0.6); opacity: 0.4; }
}

/* ─── SECTION BASE ─── */
.section {
  max-width: 1200px;
  margin: 0 auto;
  padding: 100px 24px;
}
.section-tag {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-size: 0.72rem;
  font-weight: 700;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 20px;
}
.section-tag::before {
  content: '';
  display: block;
  width: 24px; height: 1px;
  background: var(--gold);
}
.section-title {
  font-family: 'Playfair Display', serif;
  font-size: clamp(2rem, 4vw, 3rem);
  font-weight: 700;
  line-height: 1.1;
  margin-bottom: 16px;
}
.section-title em {
  font-style: normal;
  background: linear-gradient(90deg, var(--gold), var(--gold-light));
  -webkit-background-clip: text;
  color: transparent;
}
.section-lead {
  font-size: 1.05rem;
  color: var(--muted);
  max-width: 560px;
  line-height: 1.75;
  font-weight: 300;
  margin-bottom: 60px;
}

/* ─── DIVIDER ─── */
.gold-divider {
  width: 100%;
  height: 1px;
  background: linear-gradient(to right, transparent, rgba(212,175,55,0.25), transparent);
  margin: 0 24px;
}

/* ─── PROGRAM ─── */
#program { background: linear-gradient(180deg, var(--dark) 0%, var(--dark2) 100%); }
.program-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2px;
  background: rgba(212,175,55,0.08);
  border-radius: var(--radius);
  overflow: hidden;
  border: 1px solid rgba(212,175,55,0.12);
}
.program-card {
  background: var(--dark2);
  padding: 44px 36px;
  transition: background .3s;
  position: relative;
  overflow: hidden;
}
.program-card::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--gold), var(--gold-light));
  transform: scaleX(0);
  transform-origin: left;
  transition: transform .4s ease;
}
.program-card:hover { background: var(--dark3); }
.program-card:hover::before { transform: scaleX(1); }
.mag-card { transition: transform .15s ease, background .3s; will-change: transform; }
.cursor.enlarged { width: 48px; height: 48px; opacity: 0.15; }
.cursor-ring.enlarged { width: 60px; height: 60px; border-color: rgba(212,175,55,0.8); }
.program-icon {
  font-size: 2rem;
  margin-bottom: 20px;
  display: block;
}
.program-card h3 {
  font-family: 'Playfair Display', serif;
  font-size: 1.35rem;
  margin-bottom: 12px;
  color: #fff;
}
.program-card p {
  color: var(--muted);
  font-size: 0.95rem;
  line-height: 1.7;
  font-weight: 300;
}
.program-num {
  position: absolute;
  top: 20px; right: 24px;
  font-size: 3.5rem;
  font-family: 'Playfair Display', serif;
  font-weight: 900;
  color: rgba(212,175,55,0.05);
  line-height: 1;
  pointer-events: none;
}

/* ─── ENERGY / QUOTE ─── */
.energy-section {
  position: relative;
  overflow: hidden;
  padding: 0;
}
.energy-wrap {
  max-width: 1200px;
  margin: 0 auto;
  padding: 120px 24px;
  position: relative;
  z-index: 2;
  text-align: center;
}
.energy-bg-glow {
  position: absolute; inset: 0;
  background: radial-gradient(ellipse 70% 80% at 50% 50%, rgba(212,175,55,0.08), transparent 70%);
  pointer-events: none;
  animation: energyPulse 8s ease-in-out infinite;
}
@keyframes energyPulse {
  0%,100% { opacity: .6; transform: scale(1); }
  50%      { opacity: 1; transform: scale(1.05); }
}
.energy-quote {
  font-family: 'Playfair Display', serif;
  font-size: clamp(1.6rem, 3.5vw, 2.6rem);
  font-weight: 700;
  line-height: 1.35;
  max-width: 820px;
  margin: 0 auto 32px;
}
.energy-quote span {
  background: linear-gradient(90deg, var(--gold), var(--gold-light));
  -webkit-background-clip: text;
  color: transparent;
}
.energy-quote em {
  font-style: italic;
  color: rgba(232,234,240,0.65);
}

/* ─── ABOUT ─── */
.about-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: center;
}
@media (max-width: 760px) {
  .about-layout { grid-template-columns: 1fr; gap: 40px; }
}
.about-visual {
  position: relative;
}
.about-portrait {
  width: 100%;
  aspect-ratio: 3/4;
  background: linear-gradient(135deg, var(--dark3) 0%, #1a2236 100%);
  border-radius: var(--radius);
  border: 1px solid rgba(212,175,55,0.15);
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  position: relative;
}
.about-portrait::after {
  content: '';
  position: absolute; inset: 0;
  background: linear-gradient(to top, rgba(212,175,55,0.1), transparent 50%);
}
.portrait-placeholder {
  font-size: 6rem;
  opacity: 0.25;
}
.about-badge {
  position: absolute;
  bottom: -20px; right: -20px;
  background: linear-gradient(135deg, var(--gold), var(--gold-light));
  color: #07080b;
  border-radius: 14px;
  padding: 18px 24px;
  font-weight: 800;
  font-size: 0.85rem;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  box-shadow: 0 12px 40px rgba(212,175,55,0.3);
  text-align: center;
}
.about-badge span { display: block; font-size: 1.6rem; font-family: 'Playfair Display', serif; }
.about-text p {
  color: var(--muted);
  font-size: 1.05rem;
  line-height: 1.8;
  font-weight: 300;
  margin-bottom: 20px;
}
.about-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-top: 36px;
}
.tag {
  padding: 8px 18px;
  border-radius: 999px;
  border: 1px solid rgba(212,175,55,0.25);
  font-size: 0.8rem;
  font-weight: 500;
  color: var(--gold);
  background: rgba(212,175,55,0.05);
  letter-spacing: 0.04em;
}

/* ─── SUPPORT ─── */
.support-section {
  background: linear-gradient(135deg, var(--dark2), var(--dark3));
  border-top: 1px solid rgba(212,175,55,0.08);
  border-bottom: 1px solid rgba(212,175,55,0.08);
}
.support-inner {
  max-width: 1200px;
  margin: 0 auto;
  padding: 100px 24px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: center;
}
@media (max-width: 760px) {
  .support-inner { grid-template-columns: 1fr; gap: 40px; }
}
.support-counter-box {
  background: rgba(212,175,55,0.04);
  border: 1px solid rgba(212,175,55,0.15);
  border-radius: var(--radius);
  padding: 50px 40px;
  text-align: center;
}
.counter-num {
  font-family: 'Playfair Display', serif;
  font-size: 4rem;
  font-weight: 900;
  color: var(--gold);
  line-height: 1;
  margin-bottom: 10px;
  display: block;
}
.counter-label {
  font-size: 0.85rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--muted);
  margin-bottom: 36px;
}
.progress-bar {
  width: 100%;
  height: 4px;
  background: rgba(255,255,255,0.06);
  border-radius: 2px;
  overflow: hidden;
  margin-bottom: 10px;
}
.progress-fill {
  height: 100%;
  background: linear-gradient(90deg, var(--gold), var(--gold-light));
  border-radius: 2px;
  width: 0%;
  transition: width 1.5s cubic-bezier(.16,1,.3,1);
}
.progress-label {
  display: flex;
  justify-content: space-between;
  font-size: 0.75rem;
  color: var(--muted);
  margin-bottom: 32px;
}

/* ─── TIMELINE ─── */
.timeline {
  position: relative;
  padding-left: 32px;
}
.timeline::before {
  content: '';
  position: absolute;
  left: 0; top: 8px; bottom: 8px;
  width: 1px;
  background: linear-gradient(to bottom, var(--gold), rgba(212,175,55,0.1));
}
.timeline-item {
  position: relative;
  margin-bottom: 36px;
}
.timeline-item::before {
  content: '';
  position: absolute;
  left: -36px; top: 8px;
  width: 9px; height: 9px;
  border-radius: 50%;
  background: var(--gold);
  box-shadow: 0 0 12px rgba(212,175,55,0.5);
}
.timeline-year {
  font-size: 0.72rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 4px;
}
.timeline-item h4 {
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 4px;
}
.timeline-item p {
  font-size: 0.88rem;
  color: var(--muted);
  line-height: 1.6;
  font-weight: 300;
}

/* ─── FOOTER ─── */
footer {
  text-align: center;
  padding: 52px 24px;
  border-top: 1px solid rgba(212,175,55,0.08);
}
.footer-logo {
  font-family: 'Playfair Display', serif;
  font-size: 1.5rem;
  color: var(--gold);
  margin-bottom: 16px;
}
.footer-copy {
  font-size: 0.8rem;
  color: var(--muted);
}

/* ─── ANIMATIONS ─── */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(28px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes fadeIn {
  from { opacity: 0; }
  to   { opacity: 1; }
}
.fade {
  opacity: 0;
  transform: translateY(32px);
  transition: opacity .75s ease, transform .75s ease;
}
.fade.show {
  opacity: 1;
  transform: translateY(0);
}
.fade-delay-1 { transition-delay: .1s; }
.fade-delay-2 { transition-delay: .2s; }
.fade-delay-3 { transition-delay: .3s; }

/* ══════════════════════════════════
   RESPONSIVE — všetky obrazovky
══════════════════════════════════ */

/* Hide custom cursor on touch devices */
@media (hover: none) {
  .cursor, .cursor-ring { display: none; }
  #introCursor { display: none; }
}

/* ── WIDE SCREENS (1400px+) ── */
@media (min-width: 1400px) {
  .section { padding: 120px 40px; }
  .hero h1 { font-size: 5.5rem; }
  .about-layout { gap: 100px; }
  .hof-grid { gap: 28px; }
}

/* ── LARGE DESKTOP (1200px–1400px) ── */
@media (max-width: 1400px) {
  .support-inner { gap: 60px; }
}

/* ── TABLET LANDSCAPE (900px–1200px) ── */
@media (max-width: 1100px) {
  .about-layout { gap: 48px; }
  .hof-grid { gap: 14px; }
  .hof-card { padding: 28px 18px; }
  .support-inner { gap: 48px; }
  header { padding: 0 24px; }
}

/* ── TABLET PORTRAIT (600px–900px) ── */
@media (max-width: 900px) {
  /* Nav */
  header { padding: 0 20px; }
  nav { padding: 16px 0; }
  .nav-links { gap: 20px; }
  .nav-links a { font-size: 0.78rem; }

  /* Hero */
  .hero { padding: 80px 20px 80px; min-height: 100svh; }
  .hero h1 { font-size: clamp(2.2rem, 7vw, 3.4rem); }
  .hero-sub { font-size: 1rem; }
  .stats-bar { gap: 28px; margin-top: 40px; }
  .stat-num { font-size: 1.6rem; }
  .stat-label { font-size: 0.65rem; }

  /* Sections */
  .section { padding: 72px 20px; }
  .section-title { font-size: clamp(1.6rem, 4vw, 2.4rem); }

  /* About */
  .about-layout { grid-template-columns: 1fr; gap: 36px; }
  .about-visual { max-width: 340px; margin: 0 auto; }
  .about-badge { bottom: -14px; right: -10px; padding: 12px 16px; font-size: 0.75rem; }
  .about-badge span { font-size: 1.2rem; }

  /* Support */
  .support-inner { grid-template-columns: 1fr; gap: 40px; padding: 72px 20px; }

  /* Hall of fame */
  .hof-grid { grid-template-columns: 1fr; gap: 14px; max-width: 480px; margin-left: auto; margin-right: auto; }

  /* Quiz */
  .quiz-options { grid-template-columns: 1fr; }
  .quiz-wrap { padding: 28px 20px; }

  /* Fuzometer */
  .fuzometer-wrap { padding: 32px 20px; }

  /* Program grid */
  .program-grid { grid-template-columns: 1fr; }

  /* Energy */
  .energy-wrap { padding: 72px 20px; }
  .energy-quote { font-size: clamp(1.2rem, 3.5vw, 1.8rem); }

  /* Intro */
  .intro-tagline { font-size: clamp(1rem, 3.5vw, 1.5rem); margin-top: 36px; }
  .intro-mustache { width: min(320px, 72vw); }
  .intro-enter-btn { padding: 12px 30px; font-size: 0.85rem; }
  .intro-skip { bottom: 20px; right: 20px; }
}

/* ── MOBILE (max 600px) ── */
@media (max-width: 600px) {
  /* Nav — hide links, show only logo + one CTA */
  .nav-links li:not(:last-child) { display: none; }
  .nav-links { gap: 0; }
  .nav-links li:last-child a {
    background: rgba(212,175,55,0.1);
    border: 1px solid rgba(212,175,55,0.25);
    padding: 7px 16px;
    border-radius: 999px;
    font-size: 0.75rem;
  }

  /* Hero */
  .hero { padding: 100px 16px 110px; }
  .hero h1 { font-size: clamp(1.9rem, 9vw, 2.8rem); line-height: 1.08; }
  .hero-eyebrow { font-size: 0.65rem; gap: 6px; margin-bottom: 18px; }
  .hero-eyebrow::before, .hero-eyebrow::after { width: 20px; }
  .hero-sub { font-size: 0.92rem; margin-bottom: 32px; }
  .hero-ctas { flex-direction: column; align-items: center; gap: 12px; }
  .btn-primary, .btn-ghost { width: 100%; max-width: 280px; justify-content: center; padding: 14px 24px; }
  .stats-bar {
    gap: 16px;
    margin-top: 36px;
    justify-content: center;
  }
  .stat-divider { display: none; }
  .stat-item { padding: 0 12px; border-right: 1px solid rgba(212,175,55,0.2); }
  .stat-item:last-child { border-right: none; }
  .stat-num { font-size: 1.4rem; }
  .stat-label { font-size: 0.6rem; letter-spacing: 0.06em; }

  /* Hero inner needs padding for stats */
  .hero-inner { width: 100%; }

  /* Sections */
  .section { padding: 56px 16px; }
  .section-title { font-size: clamp(1.5rem, 6vw, 2rem); }
  .section-lead { font-size: 0.95rem; }

  /* Program cards */
  .program-grid { gap: 0; border-radius: 16px; }
  .program-card { padding: 32px 24px; }

  /* About */
  .about-visual { max-width: 280px; }
  .about-badge { bottom: -10px; right: -6px; padding: 10px 14px; }

  /* Support */
  .support-inner { padding: 56px 16px; gap: 36px; }
  .support-counter-box { padding: 36px 24px; }
  .counter-num { font-size: 3rem; }

  /* Timeline */
  .timeline { padding-left: 24px; }
  .timeline-item::before { left: -28px; }

  /* Hall of fame */
  .hof-grid { max-width: 100%; }
  .hof-card { padding: 24px 18px; }
  .hof-emoji { font-size: 2.2rem; }

  /* Fuzometer */
  .fuzometer-wrap { padding: 28px 16px; }
  .fuzometer-title { font-size: 1.2rem; }
  .fuz-star { font-size: 1.7rem; }
  .fuzometer-labels { font-size: 0.58rem; }

  /* Quiz */
  .quiz-wrap { padding: 24px 16px; }
  .quiz-header { gap: 12px; }
  .quiz-icon { font-size: 1.8rem; }
  .quiz-title { font-size: 1.1rem; }

  /* Energy */
  .energy-wrap { padding: 56px 16px; }

  /* Footer */
  footer { padding: 40px 16px; }

  /* Intro */
  .intro-mustache { width: min(260px, 78vw); }
  .intro-tagline { font-size: clamp(0.95rem, 4vw, 1.3rem); margin-top: 28px; max-width: 90vw; }
  .intro-year { font-size: 0.62rem; letter-spacing: 0.35em; }
  .intro-subline { font-size: 0.65rem; letter-spacing: 0.18em; margin-top: 14px; }
  .intro-enter-btn { margin-top: 28px; padding: 12px 28px; font-size: 0.82rem; }
  .intro-skip { font-size: 0.6rem; padding: 6px 14px; bottom: 16px; right: 14px; }
}

/* ── VERY SMALL (max 380px) ── */
@media (max-width: 380px) {
  .hero h1 { font-size: 1.75rem; }
  .hero-eyebrow { display: none; }
  .stats-bar { gap: 0; }
  .stat-item { padding: 0 8px; }
  .intro-mustache { width: 88vw; }
  .intro-tagline { font-size: 0.88rem; }
  .nav-links li:last-child { display: none; }
}

/* ── TALL MOBILE (svh units for better iPhone support) ── */
@supports (height: 100svh) {
  .hero { min-height: 100svh; }
}

/* ── LANDSCAPE MOBILE ── */
@media (max-width: 900px) and (orientation: landscape) {
  .hero { min-height: 100vw; padding-top: 70px; padding-bottom: 80px; }
  .stats-bar { bottom: 12px; }
  .intro-stage { flex-direction: row; gap: 32px; flex-wrap: wrap; justify-content: center; }
  .intro-mustache { width: min(220px, 35vw); }
  .intro-tagline { margin-top: 0; font-size: 1rem; max-width: 45vw; }
  #intro .bar-top, #intro .bar-bot { height: 6vh; }
}
#intro {
  position: fixed; inset: 0;
  z-index: 99999;
  background: #000;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

/* Gold aura cursor inside intro */
#introCursor {
  position: fixed;
  pointer-events: none;
  z-index: 100010;
  transform: translate(-50%, -50%);
}
#introCursor .ic-dot {
  width: 8px; height: 8px;
  background: #f0cc5a;
  border-radius: 50%;
  position: absolute;
  top: 50%; left: 50%;
  transform: translate(-50%,-50%);
  box-shadow: 0 0 8px 2px rgba(212,175,55,0.9);
}
#introCursor .ic-ring {
  width: 36px; height: 36px;
  border: 1.5px solid rgba(212,175,55,0.55);
  border-radius: 50%;
  position: absolute;
  top: 50%; left: 50%;
  transform: translate(-50%,-50%);
  animation: icRingPulse 2s ease-in-out infinite;
}
#introCursor .ic-aura {
  width: 80px; height: 80px;
  background: radial-gradient(circle, rgba(212,175,55,0.18) 0%, transparent 70%);
  border-radius: 50%;
  position: absolute;
  top: 50%; left: 50%;
  transform: translate(-50%,-50%);
  animation: icRingPulse 2s ease-in-out infinite reverse;
}
@keyframes icRingPulse {
  0%,100% { opacity: 0.5; transform: translate(-50%,-50%) scale(1); }
  50%      { opacity: 1;   transform: translate(-50%,-50%) scale(1.15); }
}
#intro .bar-top,
#intro .bar-bot {
  position: absolute; left: 0; right: 0;
  height: 11vh;
  background: #000;
  z-index: 10;
  transition: height 1.1s cubic-bezier(.76,0,.24,1);
}
#intro .bar-top { top: 0; }
#intro .bar-bot { bottom: 0; }
#intro.bars-open .bar-top,
#intro.bars-open .bar-bot { height: 0; }
#introCanvas {
  position: absolute; inset: 0;
  width: 100%; height: 100%;
}
#intro::after {
  content: '';
  position: absolute; inset: 0;
  background: repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0,0,0,0.15) 2px, rgba(0,0,0,0.15) 4px);
  pointer-events: none;
  z-index: 11;
  opacity: 0.35;
}
.intro-stage {
  position: relative; z-index: 12;
  text-align: center;
  display: flex; flex-direction: column;
  align-items: center; justify-content: center;
}
.intro-mustache {
  width: min(420px, 76vw);
  opacity: 0;
  transform: scale(0.4) rotate(-8deg);
  filter: drop-shadow(0 0 0px rgba(212,175,55,0));
}
.intro-mustache.show {
  animation: mustacheDrop 1.1s cubic-bezier(.16,1,.3,1) forwards;
}
@keyframes mustacheDrop {
  0%   { opacity:0; transform:scale(0.3) rotate(-12deg) translateY(-80px); filter:drop-shadow(0 0 0px rgba(212,175,55,0)); }
  55%  { opacity:1; transform:scale(1.1) rotate(4deg) translateY(0); filter:drop-shadow(0 0 100px rgba(212,175,55,1)); }
  100% { opacity:1; transform:scale(1) rotate(0deg); filter:drop-shadow(0 0 50px rgba(212,175,55,0.55)); }
}
.intro-mustache.pulse {
  animation: mustachePulse 1.8s ease-in-out infinite;
}
@keyframes mustachePulse {
  0%,100% { filter:drop-shadow(0 0 30px rgba(212,175,55,0.4)); }
  50%      { filter:drop-shadow(0 0 100px rgba(212,175,55,1)) drop-shadow(0 0 200px rgba(212,175,55,0.35)); }
}
.intro-year {
  margin-top: 12px;
  font-family: 'DM Sans', sans-serif;
  font-size: 0.72rem;
  letter-spacing: 0.55em;
  text-transform: uppercase;
  color: rgba(212,175,55,0.55);
  opacity: 0;
  transition: opacity .7s .3s;
}
.intro-tagline {
  margin-top: 52px;
  font-family: 'Playfair Display', serif;
  font-size: clamp(1.15rem, 2.8vw, 1.9rem);
  font-weight: 900;
  color: #fff;
  letter-spacing: 0.03em;
  line-height: 1.25;
  max-width: 580px;
  min-height: 3em;
}
.intro-tagline em {
  font-style: normal;
  background: linear-gradient(90deg,#D4AF37,#f0cc5a);
  -webkit-background-clip: text;
  color: transparent;
}
.intro-tagline .word {
  display: inline-block;
  opacity: 0;
  transform: translateY(18px);
  transition: opacity .38s ease, transform .38s ease;
}
.intro-tagline .word.show { opacity:1; transform:translateY(0); }
.intro-subline {
  margin-top: 22px;
  font-family: 'DM Sans', sans-serif;
  font-size: 0.72rem;
  letter-spacing: 0.28em;
  text-transform: uppercase;
  color: rgba(212,175,55,0.45);
  opacity: 0;
  transition: opacity .8s;
}
.intro-enter-btn {
  margin-top: 40px;
  padding: 14px 40px;
  border-radius: 999px;
  background: linear-gradient(90deg,#D4AF37,#f0cc5a);
  color: #06090f;
  font-family: 'DM Sans', sans-serif;
  font-weight: 800;
  font-size: 0.95rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  border: none;
  cursor: pointer;
  opacity: 0;
  transform: translateY(14px);
  transition: opacity .5s, transform .5s, box-shadow .25s;
  box-shadow: 0 8px 40px rgba(212,175,55,0.3);
}
.intro-enter-btn:hover {
  box-shadow: 0 16px 60px rgba(212,175,55,0.55);
  transform: translateY(-2px) !important;
}
.intro-skip {
  position: absolute;
  bottom: 32px; right: 36px;
  z-index: 20;
  font-family: 'DM Sans', sans-serif;
  font-size: 0.68rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.25);
  cursor: pointer;
  border: 1px solid rgba(255,255,255,0.1);
  padding: 7px 16px;
  border-radius: 999px;
  transition: color .2s, border-color .2s;
  opacity: 0;
  animation: fadeIn 1s 1.2s forwards;
  background: none;
}
.intro-skip:hover { color:rgba(255,255,255,0.7); border-color:rgba(255,255,255,0.3); }
.intro-progress {
  position: absolute;
  bottom: 0; left: 0;
  height: 2px;
  background: linear-gradient(90deg, transparent, var(--gold), var(--gold-light));
  width: 0%;
  z-index: 20;
}
#intro.exit {
  animation: introExit .85s cubic-bezier(.76,0,.24,1) forwards;
  pointer-events: none;
}
@keyframes introExit {
  0%   { opacity:1; transform:scale(1); }
  35%  { opacity:1; transform:scale(1.04); }
  100% { opacity:0; transform:scale(1.1); }
}
body.intro-active { overflow: hidden; }

/* ══════════════════════════════════
   LIGHT MODE
══════════════════════════════════ */
body.light {
  --dark:  #f5f0e8;
  --dark2: #ede6d6;
  --dark3: #e4dcc8;
  --text:  #1a1208;
  --muted: rgba(30,18,8,0.55);
  background: var(--dark);
  color: var(--text);
}
body.light header.scrolled { background:rgba(245,240,232,0.9); border-bottom-color:rgba(212,175,55,0.2); }
body.light .nav-logo { color:#8B6914; }
body.light .nav-links a { color:rgba(30,18,8,0.65); }
body.light .nav-links a:hover { color:#8B6914; }
body.light .hero-bg { background: radial-gradient(ellipse 80% 60% at 20% 30%,rgba(212,175,55,0.14),transparent 60%), radial-gradient(ellipse 60% 80% at 80% 70%,rgba(212,175,55,0.1),transparent 60%), linear-gradient(160deg,#ede6d6 0%,#f5f0e8 100%); }
body.light .program-card { background:#f0e9d8; }
body.light .program-card:hover { background:#e8dfca; }
body.light .news-card { background:rgba(0,0,0,0.02); border-color:rgba(212,175,55,0.2); }
body.light .news-card:hover { background:rgba(212,175,55,0.06); }
body.light .support-section { background:linear-gradient(135deg,#ede6d6,#e4dcc8); }
body.light .support-counter-box { background:rgba(212,175,55,0.08); }
body.light .contact-form-inner { background:rgba(0,0,0,0.02); border-color:rgba(212,175,55,0.2); }
body.light .form-group input,
body.light .form-group textarea,
body.light .form-group select { background:rgba(255,255,255,0.8); border-color:rgba(212,175,55,0.25); color:var(--text); }
body.light .about-portrait { background:linear-gradient(135deg,#e4dcc8,#d9d0bc); }
body.light .quote-card { background:rgba(0,0,0,0.03); border-color:rgba(212,175,55,0.2); }
body.light .comp-table-wrap { border-color:rgba(212,175,55,0.2); }
body.light .comp-table thead tr { background:rgba(212,175,55,0.1); }
body.light .comp-table tbody tr:hover td { background:rgba(212,175,55,0.05); }
body.light .comp-table td, body.light .comp-table th { border-color:rgba(0,0,0,0.07); }
body.light .gold-divider { background:linear-gradient(to right,transparent,rgba(139,105,20,0.2),transparent); }
body.light .map-svg-wrap { background:rgba(0,0,0,0.02); border-radius:12px; }
body.light #liquidCanvas { opacity:0.15; }
body.light .sk-region { fill:rgba(139,105,20,0.08); stroke:rgba(139,105,20,0.3); }
body.light .sk-region:hover { fill:rgba(139,105,20,0.25); }
body.light footer { background:#ede6d6; }
body.light .timeline::before { background:linear-gradient(to bottom,#8B6914,rgba(139,105,20,0.1)); }
body.light .timeline-item::before { background:#8B6914; }
body.light .section-title em { background:linear-gradient(90deg,#8B6914,#b8930a); -webkit-background-clip:text; color:transparent; }
body.light .news-tag { background:rgba(139,105,20,0.1); }
body.light .tag { border-color:rgba(139,105,20,0.3); color:#8B6914; background:rgba(139,105,20,0.05); }
body.light .orb1 { background:radial-gradient(circle,rgba(139,105,20,0.1),transparent 70%); }
body.light .orb2 { background:radial-gradient(circle,rgba(139,105,20,0.07),transparent 70%); }
body.light .about-badge { box-shadow:0 12px 40px rgba(139,105,20,0.25); }
body.light .map-bar-track { background:rgba(0,0,0,0.08); }
body.light .progress-bar { background:rgba(0,0,0,0.08); }

/* Smooth theme transition on all elements */
*, *::before, *::after {
  transition-property: background-color, border-color, color, box-shadow, opacity;
  transition-duration: 0.35s;
  transition-timing-function: ease;
}
.cursor,.cursor-ring,#introCursor,canvas,.fade,.sd-reveal,.sd-left,.sd-right,.sd-scale,
.mag-card,input[type=range]::-webkit-slider-thumb,svg *,#morphBlob,
.orb,.hero-bg,.hero-lines,#particleCanvas,#liquidCanvas { transition-duration:0s !important; }

/* ── THEME TOGGLE BUTTON ── */
.theme-toggle { background:none; border:none; cursor:pointer; padding:0; outline:none; flex-shrink:0; }
.tt-track {
  width:58px; height:28px;
  background:rgba(255,255,255,0.08);
  border:1.5px solid rgba(212,175,55,0.3);
  border-radius:999px; position:relative;
  display:flex; align-items:center;
  padding:0 4px; justify-content:space-between;
}
body.light .tt-track { background:rgba(212,175,55,0.18); border-color:rgba(139,105,20,0.45); }
.tt-sun,.tt-moon { font-size:13px; line-height:1; pointer-events:none; z-index:0; }
.tt-thumb {
  position:absolute;
  width:20px; height:20px; border-radius:50%;
  background:linear-gradient(135deg,var(--gold),var(--gold-light));
  top:50%; transform:translateY(-50%);
  left:4px;
  transition:left .38s cubic-bezier(.34,1.56,.64,1) !important;
  box-shadow:0 2px 8px rgba(212,175,55,0.45);
  z-index:1;
}
body.light .tt-thumb { left:calc(100% - 24px); }

/* ── SUN BURST OVERLAY ── */
#sunBurst {
  position:fixed; inset:0;
  pointer-events:none; z-index:99998;
  overflow:hidden; display:none;
}
#sunBurst.active { display:block; }
#sunRayEl {
  position:absolute;
  border-radius:50%;
  background:radial-gradient(circle,#fffde7 0%,#f0cc5a 35%,rgba(240,204,90,0) 70%);
  transform:scale(0);
  pointer-events:none;
}

/* ── QUOTES GRID ── */
.quotes-grid { display:grid; grid-template-columns:repeat(3,1fr); gap:20px; }
@media (max-width:900px) { .quotes-grid { grid-template-columns:1fr 1fr; } }
@media (max-width:560px) { .quotes-grid { grid-template-columns:1fr; } }
.quote-card {
  background:rgba(255,255,255,0.02);
  border:1px solid rgba(212,175,55,0.12);
  border-radius:var(--radius); padding:32px 28px;
  position:relative; overflow:hidden;
}
.quote-card::before {
  content:''; position:absolute; top:0;left:0;right:0;height:2px;
  background:linear-gradient(90deg,var(--gold),var(--gold-light));
  transform:scaleX(0); transform-origin:left;
  transition:transform .4s ease !important;
}
.quote-card:hover::before { transform:scaleX(1); }
.quote-num {
  font-family:'Playfair Display',serif; font-size:3.5rem; font-weight:900;
  color:rgba(212,175,55,0.06); line-height:1;
  position:absolute; top:10px; right:14px; pointer-events:none;
}
.quote-icon { font-size:1.8rem; margin-bottom:14px; display:block; }
.quote-card p { font-size:0.94rem; color:var(--muted); line-height:1.72; font-weight:300; }
.quote-card p strong { color:var(--text); font-weight:600; }

/* ── COMPARISON TABLE ── */
.comp-table-wrap { border:1px solid rgba(212,175,55,0.15); border-radius:var(--radius); overflow:hidden; }
.comp-table { width:100%; border-collapse:collapse; font-size:0.9rem; }
.comp-table thead tr { background:rgba(212,175,55,0.06); border-bottom:1px solid rgba(212,175,55,0.14); }
.comp-table th { padding:20px 24px; text-align:center; font-weight:700; font-size:0.8rem; letter-spacing:0.06em; text-transform:uppercase; }
.comp-table th.comp-criteria { text-align:left; color:var(--muted); width:50%; }
.comp-table th.comp-us { color:var(--gold); }
.comp-table th.comp-them { color:var(--muted); }
.comp-table tbody tr { border-bottom:1px solid rgba(212,175,55,0.07); }
.comp-table tbody tr:last-child { border-bottom:none; }
.comp-table tbody tr:hover td { background:rgba(212,175,55,0.04) !important; }
.comp-table td { padding:15px 24px; }
.comp-table td.comp-yes,.comp-table td.comp-no { text-align:center; }
.comp-head-inner { display:flex; align-items:center; justify-content:center; gap:10px; }
.comp-avatar { font-size:1.5rem; }
.comp-avatar-gray { filter:grayscale(1) opacity(0.45); }
.comp-badge { display:inline-flex; align-items:center; padding:5px 14px; border-radius:999px; font-size:0.78rem; font-weight:700; letter-spacing:0.04em; white-space:nowrap; }
.comp-badge-yes { background:rgba(34,197,94,0.12); color:#4ade80; border:1px solid rgba(34,197,94,0.25); }
.comp-badge-no  { background:rgba(239,68,68,0.08); color:#f87171; border:1px solid rgba(239,68,68,0.18); }
body.light .comp-badge-yes { background:rgba(34,197,94,0.1); color:#15803d; border-color:rgba(34,197,94,0.3); }
body.light .comp-badge-no  { background:rgba(239,68,68,0.07); color:#b91c1c; border-color:rgba(239,68,68,0.2); }
@media (max-width:600px) { .comp-table th,.comp-table td { padding:11px 10px; font-size:0.74rem; } .comp-badge { padding:4px 9px; font-size:0.68rem; } }

/* ── COUNTDOWN ── */
.countdown-grid {
  display: flex; align-items: center;
  justify-content: center; gap: 8px;
  flex-wrap: wrap;
}
.cd-item { text-align: center; min-width: 100px; }
.cd-num {
  font-family: 'Playfair Display', serif;
  font-size: clamp(2.8rem, 7vw, 5rem);
  font-weight: 900;
  color: var(--gold);
  line-height: 1;
  display: block;
  background: linear-gradient(135deg,#fff,var(--gold-light),var(--gold));
  -webkit-background-clip: text; color: transparent;
  text-shadow: none;
  letter-spacing: -0.02em;
}
.cd-label {
  font-size: 0.68rem; letter-spacing: 0.2em;
  text-transform: uppercase; color: var(--muted);
  margin-top: 8px;
}
.cd-sep {
  font-family: 'Playfair Display', serif;
  font-size: clamp(2rem, 5vw, 3.5rem);
  color: rgba(212,175,55,0.3);
  line-height: 1; padding-bottom: 20px;
  font-weight: 900;
}
@media (max-width: 480px) {
  .cd-item { min-width: 70px; }
  .cd-sep { font-size: 1.8rem; }
}

/* ── NEWS ── */
.news-grid {
  display: grid;
  grid-template-columns: repeat(3,1fr);
  gap: 20px; margin-top: 0;
}
@media (max-width: 900px) { .news-grid { grid-template-columns: 1fr; } }
@media (min-width: 600px) and (max-width: 900px) { .news-grid { grid-template-columns: 1fr 1fr; } }
.news-card {
  background: rgba(255,255,255,0.02);
  border: 1px solid rgba(212,175,55,0.1);
  border-radius: var(--radius); padding: 32px 28px;
  display: flex; flex-direction: column; gap: 10px;
  cursor: pointer;
  transition: border-color .25s, background .25s, transform .15s;
  position: relative; overflow: hidden;
}
.news-card::before {
  content: ''; position: absolute;
  top: 0; left: 0; right: 0; height: 2px;
  background: linear-gradient(90deg, var(--gold), var(--gold-light));
  transform: scaleX(0); transform-origin: left;
  transition: transform .4s ease;
}
.news-card:hover { border-color: rgba(212,175,55,0.3); background: rgba(212,175,55,0.04); }
.news-card:hover::before { transform: scaleX(1); }
.news-tag {
  display: inline-block; padding: 4px 12px;
  border-radius: 999px; font-size: 0.68rem;
  font-weight: 700; letter-spacing: 0.12em;
  text-transform: uppercase;
  background: rgba(212,175,55,0.12);
  color: var(--gold); width: fit-content;
}
.news-tag--media { background: rgba(96,165,250,0.1); color: #60a5fa; }
.news-tag--event { background: rgba(52,211,153,0.1); color: #34d399; }
.news-date { font-size: 0.75rem; color: var(--muted); }
.news-card h3 {
  font-family: 'Playfair Display', serif;
  font-size: 1.05rem; font-weight: 700;
  line-height: 1.35; color: var(--text);
  flex: 1;
}
.news-card p { font-size: 0.88rem; color: var(--muted); line-height: 1.65; font-weight: 300; }
.news-read { font-size: 0.78rem; color: var(--gold); font-weight: 600; margin-top: 4px; letter-spacing: 0.04em; }

/* ── MAP ── */
.map-layout {
  display: grid; grid-template-columns: 1.6fr 1fr;
  gap: 48px; align-items: center; margin-top: 48px;
}
@media (max-width: 800px) { .map-layout { grid-template-columns: 1fr; gap: 28px; } }
.map-svg-wrap { position: relative; }
#slovakiaMap { width: 100%; border-radius: 12px; }
.sk-region {
  fill: rgba(212,175,55,0.08);
  stroke: rgba(212,175,55,0.25); stroke-width: 1.5;
  cursor: pointer;
  transition: fill .25s, filter .25s;
}
.sk-region:hover { fill: rgba(212,175,55,0.35); filter: drop-shadow(0 0 8px rgba(212,175,55,0.5)); }
.sk-region.active { fill: rgba(212,175,55,0.28); }
.map-tooltip {
  position: absolute; pointer-events: none;
  background: rgba(13,20,32,0.95);
  border: 1px solid rgba(212,175,55,0.3);
  border-radius: 10px; padding: 10px 16px;
  font-size: 0.82rem; color: var(--text);
  backdrop-filter: blur(8px);
  opacity: 0; transition: opacity .15s;
  white-space: nowrap; z-index: 10;
}
.map-tooltip strong { color: var(--gold); display: block; font-size: 0.9rem; }
.map-legend-title {
  font-size: 0.75rem; letter-spacing: 0.14em;
  text-transform: uppercase; color: var(--gold);
  margin-bottom: 20px; font-weight: 700;
}
.map-bars { display: flex; flex-direction: column; gap: 12px; }
.map-bar-row { display: flex; flex-direction: column; gap: 4px; }
.map-bar-label {
  display: flex; justify-content: space-between;
  font-size: 0.78rem; color: var(--text);
}
.map-bar-label span { color: var(--gold); font-weight: 700; }
.map-bar-track {
  height: 4px; background: rgba(255,255,255,0.06);
  border-radius: 2px; overflow: hidden;
}
.map-bar-fill {
  height: 100%;
  background: linear-gradient(90deg,var(--gold),var(--gold-light));
  border-radius: 2px; width: 0%;
  transition: width 1.2s cubic-bezier(.16,1,.3,1);
}

/* ── CONTACT ── */
.contact-layout {
  display: grid; grid-template-columns: 1fr 1.2fr;
  gap: 72px; align-items: start;
}
@media (max-width: 800px) { .contact-layout { grid-template-columns: 1fr; gap: 40px; } }
.contact-info-items { display: flex; flex-direction: column; gap: 20px; }
.ci-item {
  display: flex; align-items: flex-start; gap: 16px;
}
.ci-icon {
  font-size: 1.3rem; margin-top: 2px;
  width: 40px; height: 40px;
  background: rgba(212,175,55,0.08);
  border: 1px solid rgba(212,175,55,0.15);
  border-radius: 10px;
  display: flex; align-items: center; justify-content: center;
  flex-shrink: 0;
}
.ci-label { font-size: 0.72rem; letter-spacing: 0.12em; text-transform: uppercase; color: var(--muted); margin-bottom: 2px; }
.ci-val { font-size: 0.95rem; color: var(--text); font-weight: 500; }
.contact-form-wrap {}
.contact-form-inner {
  background: rgba(255,255,255,0.02);
  border: 1px solid rgba(212,175,55,0.12);
  border-radius: var(--radius); padding: 36px;
}
.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
@media (max-width: 500px) { .form-row { grid-template-columns: 1fr; } }
.form-group { display: flex; flex-direction: column; gap: 7px; margin-bottom: 16px; }
.form-group label {
  font-size: 0.73rem; font-weight: 600;
  letter-spacing: 0.1em; text-transform: uppercase;
  color: var(--muted);
}
.form-group input,
.form-group textarea,
.form-group select {
  background: rgba(255,255,255,0.04);
  border: 1px solid rgba(212,175,55,0.15);
  border-radius: 10px; padding: 12px 16px;
  color: var(--text); font-family: 'DM Sans', sans-serif;
  font-size: 0.92rem; outline: none;
  transition: border-color .2s, background .2s;
  width: 100%;
}
.form-group input:focus,
.form-group textarea:focus,
.form-group select:focus {
  border-color: var(--gold);
  background: rgba(212,175,55,0.05);
}
.form-group textarea { resize: vertical; min-height: 100px; }
.form-select-wrap { position: relative; }
.form-group select { appearance: none; cursor: pointer; }
.form-select-wrap::after {
  content: '▾'; position: absolute;
  right: 14px; top: 50%; transform: translateY(-50%);
  color: var(--gold); pointer-events: none; font-size: 1rem;
}
.form-group select option { background: var(--dark2); color: var(--text); }
.form-success {
  display: none; margin-top: 14px;
  padding: 12px 16px; border-radius: 10px;
  background: rgba(34,197,94,0.1);
  border: 1px solid rgba(34,197,94,0.25);
  color: #4ade80; font-size: 0.88rem;
}
══════════════════════════════════ */
#morphBlob {
  position: absolute;
  inset: -20%;
  width: 140%; height: 140%;
  opacity: 0.12;
  filter: blur(1px);
  animation: blobSpin 25s linear infinite;
  pointer-events: none;
  z-index: 0;
}
@keyframes blobSpin {
  from { transform: rotate(0deg) scale(1); }
  33%  { transform: rotate(120deg) scale(1.08); }
  66%  { transform: rotate(240deg) scale(0.95); }
  to   { transform: rotate(360deg) scale(1); }
}

/* ══════════════════════════════════
   FEATURE 3 — SCROLL-DRIVEN REVEALS
══════════════════════════════════ */
.sd-reveal {
  opacity: 0;
  clip-path: inset(0 0 100% 0);
  transition: opacity .6s ease, clip-path .85s cubic-bezier(.16,1,.3,1);
}
.sd-reveal.visible { opacity: 1; clip-path: inset(0 0 0% 0); }
.sd-left {
  opacity: 0; transform: translateX(-52px);
  transition: opacity .7s ease, transform .9s cubic-bezier(.16,1,.3,1);
}
.sd-left.visible { opacity: 1; transform: translateX(0); }
.sd-right {
  opacity: 0; transform: translateX(52px);
  transition: opacity .7s ease, transform .9s cubic-bezier(.16,1,.3,1);
}
.sd-right.visible { opacity: 1; transform: translateX(0); }
.sd-scale {
  opacity: 0; transform: scale(0.86);
  transition: opacity .6s ease, transform .8s cubic-bezier(.16,1,.3,1);
}
.sd-scale.visible { opacity: 1; transform: scale(1); }
[data-delay="1"] { transition-delay: .1s !important; }
[data-delay="2"] { transition-delay: .2s !important; }
[data-delay="3"] { transition-delay: .3s !important; }
[data-delay="4"] { transition-delay: .4s !important; }

/* ══════════════════════════════════
   FEATURE 4 — WIPE TEXT REVEAL
══════════════════════════════════ */
.wipe-wrap {
  display: inline-block;
  position: relative;
  overflow: hidden;
}
.wipe-wrap .wt { opacity: 0; display: inline; }
.wipe-wrap::after {
  content: '';
  position: absolute;
  inset: -2px;
  background: var(--gold);
  transform: scaleX(0);
  transform-origin: left;
}
.wipe-wrap.wipe-go::after {
  animation: wipeBar .9s cubic-bezier(.76,0,.24,1) forwards;
}
.wipe-wrap.wipe-go .wt {
  animation: wipeShow .9s ease forwards;
}
@keyframes wipeBar {
  0%   { transform: scaleX(0); transform-origin: left; }
  45%  { transform: scaleX(1); transform-origin: left; }
  46%  { transform: scaleX(1); transform-origin: right; }
  100% { transform: scaleX(0); transform-origin: right; }
}
@keyframes wipeShow {
  0%,44% { opacity: 0; }
  45%    { opacity: 1; }
  100%   { opacity: 1; }
}

/* ══════════════════════════════════
   FEATURE 5 — LIQUID REACTIVE BG
══════════════════════════════════ */
#liquidCanvas {
  position: fixed; inset: 0;
  pointer-events: none;
  z-index: 0;
  opacity: 1;
}

/* ══════════════════════════════════
   FEATURE 6 — FÚZY CUSTOMIZER
══════════════════════════════════ */
.customizer-wrap {
  background: rgba(212,175,55,0.03);
  border: 1px solid rgba(212,175,55,0.15);
  border-radius: var(--radius);
  padding: 40px;
  margin-top: 48px;
}
.customizer-title {
  font-family: 'Playfair Display', serif;
  font-size: 1.3rem; font-weight: 700;
  color: var(--gold); margin-bottom: 6px;
}
.customizer-sub { font-size: 0.85rem; color: var(--muted); margin-bottom: 28px; }
.customizer-layout {
  display: grid; grid-template-columns: 1fr 1.4fr;
  gap: 36px; align-items: start;
}
@media (max-width: 700px) { .customizer-layout { grid-template-columns: 1fr; } }
.customizer-preview {
  background: rgba(255,255,255,0.02);
  border: 1px solid rgba(212,175,55,0.1);
  border-radius: 16px; padding: 28px;
  display: flex; flex-direction: column;
  align-items: center; gap: 12px;
  position: sticky; top: 100px;
}
.cust-svg-wrap { width: 200px; height: 90px; }
#custMustacheSvg { width: 100%; height: 100%; overflow: visible; }
.cust-name-preview {
  font-family: 'Playfair Display', serif;
  font-size: 0.9rem; color: var(--gold);
  text-align: center; letter-spacing: 0.04em;
}
.customizer-controls { display: flex; flex-direction: column; gap: 18px; }
.ctrl-row { display: flex; flex-direction: column; gap: 6px; }
.ctrl-label {
  font-size: 0.75rem; font-weight: 600;
  letter-spacing: 0.1em; text-transform: uppercase;
  color: var(--text); display: flex; justify-content: space-between;
}
.ctrl-label span { color: var(--gold); font-weight: 700; }
input[type=range] {
  -webkit-appearance: none; width: 100%;
  height: 4px; border-radius: 2px;
  background: rgba(255,255,255,0.08); outline: none; cursor: pointer;
}
input[type=range]::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 18px; height: 18px; border-radius: 50%;
  background: linear-gradient(135deg,var(--gold),var(--gold-light));
  box-shadow: 0 0 10px rgba(212,175,55,0.6);
  cursor: pointer; transition: transform .15s;
}
input[type=range]::-webkit-slider-thumb:hover { transform: scale(1.25); }
.color-swatches { display: flex; gap: 10px; flex-wrap: wrap; margin-top: 2px; }
.swatch {
  width: 26px; height: 26px; border-radius: 50%;
  cursor: pointer; border: 2px solid transparent;
  transition: transform .15s, border-color .15s; flex-shrink: 0;
}
.swatch.active { border-color: white; transform: scale(1.18); }
.swatch:hover { transform: scale(1.1); }
.style-btns { display: flex; gap: 8px; flex-wrap: wrap; margin-top: 2px; }
.style-btn {
  padding: 6px 14px; border-radius: 999px;
  border: 1px solid rgba(212,175,55,0.22);
  background: transparent; color: var(--muted);
  font-size: 0.76rem; font-family: 'DM Sans', sans-serif;
  cursor: pointer; transition: all .2s;
}
.style-btn.active, .style-btn:hover {
  background: rgba(212,175,55,0.1);
  border-color: var(--gold); color: var(--gold);
}
.save-look-btn {
  margin-top: 4px; padding: 12px 28px;
  border-radius: 999px;
  background: linear-gradient(90deg,var(--gold),var(--gold-light));
  color: #06090f; font-weight: 800; font-size: 0.88rem;
  border: none; cursor: pointer;
  font-family: 'DM Sans', sans-serif;
  transition: box-shadow .2s, transform .2s;
  letter-spacing: 0.06em; width: 100%;
}
.save-look-btn:hover {
  box-shadow: 0 8px 30px rgba(212,175,55,0.45);
  transform: translateY(-2px);
}

/* ─── FLOATING MOUSTACHES ─── */
.moustache-float {
  position: absolute;
  font-size: 1.8rem;
  color: var(--gold);
  opacity: 0.2;
  animation: floatMustache 6s ease-in-out infinite;
  pointer-events: none;
  font-family: serif;
  letter-spacing: -4px;
  filter: blur(0.5px);
}
@keyframes floatMustache {
  0%,100% { transform: translateY(0) rotate(-5deg); opacity: 0.15; }
  50%      { transform: translateY(-18px) rotate(5deg); opacity: 0.3; }
}

/* ─── EYE TRACKING ─── */
#avatarBox { cursor: none; }

/* ─── FÚZO-METER ─── */
.fuzometer-wrap {
  background: rgba(212,175,55,0.04);
  border: 1px solid rgba(212,175,55,0.18);
  border-radius: var(--radius);
  padding: 44px 40px;
  text-align: center;
  margin-bottom: 40px;
  position: relative;
  overflow: hidden;
}
.fuzometer-wrap::before {
  content: '🥸';
  position: absolute;
  font-size: 8rem;
  right: -10px; top: -10px;
  opacity: 0.05;
  pointer-events: none;
}
.fuzometer-title {
  font-family: 'Playfair Display', serif;
  font-size: 1.6rem;
  color: var(--gold);
  font-weight: 900;
  letter-spacing: 0.1em;
  margin-bottom: 8px;
}
.fuzometer-sub {
  color: var(--muted);
  font-size: 0.9rem;
  margin-bottom: 28px;
}
.fuzometer-bar-wrap {
  max-width: 500px;
  margin: 0 auto 24px;
}
.fuzometer-bar-wrap > div:first-child {
  /* the fill bar */
}
.fuzometer-fill {
  height: 16px;
  background: linear-gradient(90deg, #555, var(--gold), var(--gold-light));
  border-radius: 8px;
  width: 0%;
  transition: width 1s cubic-bezier(.16,1,.3,1);
  box-shadow: 0 0 20px rgba(212,175,55,0.4);
  margin-bottom: 8px;
  position: relative;
}
.fuzometer-fill::after {
  content: '';
  position: absolute;
  right: -2px; top: -4px;
  width: 24px; height: 24px;
  background: var(--gold-light);
  border-radius: 50%;
  box-shadow: 0 0 12px rgba(240,204,90,0.8);
}
.fuzometer-labels {
  display: flex;
  justify-content: space-between;
  font-size: 0.65rem;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: var(--muted);
  margin-top: 12px;
}
.fuz-stars {
  display: flex;
  justify-content: center;
  gap: 12px;
  margin: 20px 0 16px;
}
.fuz-star {
  font-size: 2rem;
  cursor: pointer;
  transition: transform .2s, filter .2s;
  filter: grayscale(1) opacity(0.4);
}
.fuz-star.active { filter: grayscale(0) drop-shadow(0 0 8px rgba(212,175,55,0.8)); }
.fuz-star:hover { transform: scale(1.3) rotate(-10deg); filter: grayscale(0); }
.fuz-verdict {
  font-family: 'Playfair Display', serif;
  font-size: 1.15rem;
  color: var(--gold);
  min-height: 1.5em;
  transition: all .3s;
}

/* ─── QUIZ ─── */
.quiz-wrap {
  background: rgba(255,255,255,0.02);
  border: 1px solid rgba(212,175,55,0.12);
  border-radius: var(--radius);
  padding: 40px;
  margin-bottom: 40px;
}
.quiz-header {
  display: flex;
  align-items: center;
  gap: 20px;
  margin-bottom: 32px;
}
.quiz-icon { font-size: 2.5rem; }
.quiz-title {
  font-family: 'Playfair Display', serif;
  font-size: 1.4rem;
  font-weight: 700;
}
.quiz-sub { color: var(--muted); font-size: 0.88rem; margin-top: 4px; }
.quiz-question-text {
  font-size: 1.05rem;
  margin-bottom: 20px;
  line-height: 1.6;
}
.quiz-question-num {
  font-size: 0.72rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 10px;
}
.quiz-options {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  margin-bottom: 20px;
}
@media (max-width: 600px) { .quiz-options { grid-template-columns: 1fr; } }
.quiz-opt {
  padding: 14px 20px;
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(212,175,55,0.15);
  border-radius: 12px;
  color: var(--text);
  font-size: 0.9rem;
  cursor: pointer;
  transition: all .2s;
  text-align: left;
  font-family: 'DM Sans', sans-serif;
}
.quiz-opt:hover { background: rgba(212,175,55,0.08); border-color: var(--gold); }
.quiz-opt.correct { background: rgba(34,197,94,0.12); border-color: #22c55e; color: #4ade80; }
.quiz-opt.wrong   { background: rgba(239,68,68,0.1); border-color: #ef4444; color: #f87171; }
.quiz-opt:disabled { cursor: default; }
.quiz-feedback {
  padding: 14px 20px;
  border-radius: 12px;
  font-size: 0.9rem;
  margin-bottom: 16px;
  line-height: 1.6;
  display: none;
}
.quiz-feedback.show { display: block; }
.quiz-feedback.good { background: rgba(34,197,94,0.08); border: 1px solid rgba(34,197,94,0.3); color: #86efac; }
.quiz-feedback.bad  { background: rgba(239,68,68,0.08); border: 1px solid rgba(239,68,68,0.2); color: #fca5a5; }
.quiz-next-btn {
  padding: 11px 24px;
  border-radius: 999px;
  background: linear-gradient(90deg,var(--gold),var(--gold-light));
  color: #07080b;
  font-weight: 700;
  font-size: 0.9rem;
  border: none;
  cursor: pointer;
  display: none;
}
.quiz-next-btn.show { display: inline-block; }
.quiz-score {
  text-align: center;
  padding: 40px;
}
.quiz-score-num {
  font-family: 'Playfair Display', serif;
  font-size: 3.5rem;
  color: var(--gold);
  font-weight: 900;
}
.quiz-score-msg {
  font-size: 1.1rem;
  color: var(--muted);
  margin-top: 12px;
  line-height: 1.6;
}

/* ─── HALL OF FAME ─── */
.hof-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  margin-top: 40px;
}
@media (max-width: 700px) { .hof-grid { grid-template-columns: 1fr; } }
.hof-card {
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(212,175,55,0.1);
  border-radius: var(--radius);
  padding: 36px 24px;
  text-align: center;
  position: relative;
  overflow: hidden;
  transition: transform .15s ease;
}
.hof-highlight {
  background: rgba(212,175,55,0.06);
  border-color: rgba(212,175,55,0.35);
  box-shadow: 0 0 40px rgba(212,175,55,0.08);
}
.hof-crown {
  position: absolute;
  top: 12px; right: 16px;
  font-size: 1.4rem;
  animation: crownBounce 2s ease-in-out infinite;
}
@keyframes crownBounce {
  0%,100% { transform: translateY(0) rotate(-5deg); }
  50%      { transform: translateY(-5px) rotate(5deg); }
}
.hof-emoji { font-size: 3rem; margin-bottom: 12px; }
.hof-name {
  font-family: 'Playfair Display', serif;
  font-size: 1.05rem;
  font-weight: 700;
  margin-bottom: 10px;
}
.hof-fuz {
  font-size: 0.75rem;
  letter-spacing: 0.05em;
  color: var(--gold);
  margin-bottom: 12px;
  font-family: monospace;
}
.hof-quote {
  font-size: 0.82rem;
  color: var(--muted);
  font-style: italic;
  line-height: 1.5;
}

/* ─── CONFETTI CANVAS ─── */
#confettiCanvas {
  position: fixed; inset: 0;
  pointer-events: none;
  z-index: 9990;
  display: none;
}

/* ══════════════════════════════════════════════════════
   FEATURE 4 — LENIS: body overflow for smooth scroll
══════════════════════════════════════════════════════ */
html.lenis { height: auto; }
.lenis.lenis-smooth { scroll-behavior: auto; }
.lenis.lenis-smooth [data-lenis-prevent] { overscroll-behavior: contain; }

/* ══════════════════════════════════════════════════════
   FEATURE 6 — GLASSMORPHISM CARDS 2.0
   (applied to program-card and news-card)
══════════════════════════════════════════════════════ */
.glass-card {
  background: rgba(255,255,255,0.03) !important;
  backdrop-filter: blur(20px) saturate(160%) !important;
  -webkit-backdrop-filter: blur(20px) saturate(160%) !important;
  border: 1px solid rgba(255,255,255,0.07) !important;
  position: relative;
  overflow: hidden;
}
.glass-card::after {
  content: '';
  position: absolute; inset: 0;
  background: radial-gradient(600px circle at var(--mx,50%) var(--my,50%),
    rgba(212,175,55,0.07), transparent 40%);
  opacity: 0;
  transition: opacity .35s;
  pointer-events: none;
  z-index: 0;
}
.glass-card:hover::after { opacity: 1; }
.glass-card > * { position: relative; z-index: 1; }
body.light .glass-card {
  background: rgba(255,255,255,0.45) !important;
  border: 1px solid rgba(212,175,55,0.15) !important;
  backdrop-filter: blur(24px) saturate(180%) !important;
}

/* ══════════════════════════════════════════════════════
   FEATURE 7 — KINETIC TYPOGRAPHY
══════════════════════════════════════════════════════ */
.kinetic-wrap {
  display: inline-flex;
  align-items: center;
  position: relative;
  overflow: hidden;
  vertical-align: middle;
  height: 1.7em;
  min-width: 240px;
  margin-bottom: -0.2em;
}
.kinetic-word {
  display: block;
  position: absolute;
  top: 0; left: 0;
  width: 100%;
  text-align: inherit;
  white-space: nowrap;
  font-size: inherit;
  font-weight: 700;
  letter-spacing: 0.02em;
  background: linear-gradient(90deg,#fff 0%,var(--gold-light) 50%,var(--gold) 100%);
  -webkit-background-clip: text;
  color: transparent;
  opacity: 0;
  line-height: 1.7;
  transform: translateY(110%);
}
.kinetic-word.active {
  animation: kineticIn .65s cubic-bezier(.16,1,.3,1) forwards;
}
.kinetic-word.leaving {
  animation: kineticOut .5s cubic-bezier(.76,0,.24,1) forwards;
}
@keyframes kineticIn {
  from { transform: translateY(110%); opacity: 0; }
  to   { transform: translateY(0);    opacity: 1; }
}
@keyframes kineticOut {
  from { transform: translateY(0);     opacity: 1; }
  to   { transform: translateY(-110%); opacity: 0; }
}

/* ══════════════════════════════════════════════════════
   FEATURE 11 — APPLE-STYLE SCROLL STORY
══════════════════════════════════════════════════════ */
#story {
  background: var(--dark);
  position: relative;
}
.story-sticky-outer {
  /* tall enough for all scenes to pin through */
  height: 600vh;
  position: relative;
}
.story-sticky {
  position: sticky;
  top: 0;
  height: 100vh;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
}
/* Dark cinematic overlay gradient */
.story-sticky::before {
  content: '';
  position: absolute; inset: 0;
  background: radial-gradient(ellipse 80% 80% at 50% 50%,
    transparent 40%, var(--dark) 100%);
  z-index: 2; pointer-events: none;
}
.story-bg-layer {
  position: absolute; inset: 0;
  background: var(--dark);
  transition: background 0.8s ease;
  z-index: 0;
}
/* Background blobs that transform per scene */
.story-blob {
  position: absolute;
  border-radius: 50%;
  filter: blur(100px);
  pointer-events: none;
  opacity: 0;
  transition: none;
  z-index: 1;
}
#sb1 { width:600px;height:600px; background:radial-gradient(circle,rgba(212,175,55,0.18),transparent 70%); top:-100px;left:-100px; }
#sb2 { width:500px;height:500px; background:radial-gradient(circle,rgba(99,102,241,0.15),transparent 70%); top:50%;right:-100px; transform:translateY(-50%); }
#sb3 { width:700px;height:400px; background:radial-gradient(circle,rgba(16,185,129,0.12),transparent 70%); bottom:-100px;left:50%;transform:translateX(-50%); }
#sb4 { width:500px;height:500px; background:radial-gradient(circle,rgba(239,68,68,0.1),transparent 70%); top:0;right:0; }

.story-content {
  position: relative;
  z-index: 10;
  text-align: center;
  max-width: 900px;
  padding: 0 24px;
  pointer-events: none;
}
.story-scene {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  pointer-events: none;
  z-index: 10;
}
.story-scene.active { pointer-events: auto; }

.story-eyebrow {
  font-size: 0.72rem;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 24px;
  opacity: 0;
}
.story-headline {
  font-family: 'Playfair Display', serif;
  font-size: clamp(2.4rem, 6vw, 5.5rem);
  font-weight: 900;
  line-height: 1.02;
  margin-bottom: 28px;
  opacity: 0;
}
.story-headline em {
  font-style: normal;
  background: linear-gradient(90deg,var(--gold),var(--gold-light));
  -webkit-background-clip: text; color: transparent;
}
.story-body {
  font-size: clamp(1rem, 2vw, 1.25rem);
  color: var(--muted);
  line-height: 1.7;
  font-weight: 300;
  max-width: 640px;
  margin: 0 auto 36px;
  opacity: 0;
}
.story-stat {
  display: inline-flex;
  align-items: baseline;
  gap: 6px;
  margin: 0 20px;
  opacity: 0;
}
.story-stat-num {
  font-family: 'Playfair Display', serif;
  font-size: clamp(2.5rem, 5vw, 4rem);
  font-weight: 900;
  color: var(--gold);
  line-height: 1;
}
.story-stat-label {
  font-size: 0.78rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--muted);
}
.story-stats-row {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 8px 0;
  opacity: 0;
  border-top: 1px solid rgba(212,175,55,0.12);
  padding-top: 28px;
  margin-top: 16px;
}
.story-stat-divider { width:1px; background:rgba(212,175,55,0.2); align-self:stretch; margin: 0 16px; }

/* Scene progress dots */
.story-dots {
  position: absolute;
  bottom: 40px; left: 50%;
  transform: translateX(-50%);
  display: flex; gap: 10px;
  z-index: 20;
}
.story-dot {
  width: 6px; height: 6px;
  border-radius: 50%;
  background: rgba(212,175,55,0.25);
  transition: background .3s, transform .3s;
}
.story-dot.active {
  background: var(--gold);
  transform: scale(1.4);
}
/* Scroll hint inside story */
.story-scroll-hint {
  position: absolute;
  bottom: 44px; right: 48px;
  z-index: 20;
  display: flex; flex-direction: column;
  align-items: center; gap: 6px;
  font-size: 0.65rem; letter-spacing: 0.18em;
  text-transform: uppercase; color: var(--muted);
}
.story-scroll-line {
  width: 1px; height: 36px;
  background: linear-gradient(to bottom,var(--gold),transparent);
  animation: scrollPulse 2s ease-in-out infinite;
}

/* ══════════════════════════════════════════════════════
   FEATURE 13 — PARALLAX DEPTH
══════════════════════════════════════════════════════ */
.parallax-deep   { will-change: transform; }
.parallax-mid    { will-change: transform; }
.parallax-slow   { will-change: transform; }

/* ══════════════════════════════════════════════════════
   FEATURE 16 — LIVE SUPPORT TICKER
══════════════════════════════════════════════════════ */
.live-ticker {
  position: fixed;
  bottom: 24px; left: 24px;
  z-index: 9000;
  pointer-events: none;
}
.live-toast {
  background: rgba(13,20,32,0.92);
  backdrop-filter: blur(16px);
  border: 1px solid rgba(212,175,55,0.2);
  border-radius: 12px;
  padding: 12px 18px;
  display: flex; align-items: center; gap: 12px;
  font-size: 0.82rem; color: var(--text);
  transform: translateX(-120%);
  transition: transform .5s cubic-bezier(.16,1,.3,1);
  max-width: 280px;
  box-shadow: 0 8px 32px rgba(0,0,0,0.4);
}
.live-toast.show { transform: translateX(0); }
body.light .live-toast {
  background: rgba(245,240,232,0.95);
  border-color: rgba(139,105,20,0.25);
  color: var(--text);
}
.lt-avatar {
  width: 32px; height: 32px; border-radius: 50%;
  background: linear-gradient(135deg,var(--gold),var(--gold-light));
  display: flex; align-items: center; justify-content: center;
  font-size: 0.9rem; flex-shrink: 0;
}
.lt-text strong { display: block; font-weight: 600; font-size: 0.82rem; }
.lt-text span { color: var(--muted); font-size: 0.74rem; }
.lt-pulse {
  width: 8px; height: 8px; border-radius: 50%;
  background: #22c55e;
  animation: ltPulse 2s ease-in-out infinite;
  flex-shrink: 0; margin-left: auto;
}
@keyframes ltPulse {
  0%,100% { box-shadow: 0 0 0 0 rgba(34,197,94,0.5); }
  50%      { box-shadow: 0 0 0 6px rgba(34,197,94,0); }
}
@media (max-width:600px) { .live-ticker { bottom:16px; left:12px; } .live-toast { max-width:240px; } }
</style>
</head>
<body>

<div id="sunBurst"><div id="sunRayEl"></div></div>
<!-- LIVE TICKER -->
<div class="live-ticker"><div class="live-toast" id="liveToast"><div class="lt-avatar" id="ltAvatar">👤</div><div class="lt-text"><strong id="ltName">Ján K.</strong><span id="ltCity">Bratislava sa práve pridal</span></div><div class="lt-pulse"></div></div></div>
<canvas id="liquidCanvas"></canvas>
<canvas id="confettiCanvas"></canvas>

<!-- ══ CINEMATIC INTRO ══ -->
<div id="intro">
  <div id="introCursor">
    <div class="ic-aura"></div>
    <div class="ic-ring"></div>
    <div class="ic-dot"></div>
  </div>
  <canvas id="introCanvas"></canvas>
  <div class="bar-top"></div>
  <div class="bar-bot"></div>

  <div class="intro-stage">
    <!-- Big gold mustache SVG -->
    <div style="position:relative; display:inline-block;">
      <svg id="introMustache" class="intro-mustache" viewBox="0 0 500 200" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <radialGradient id="mg" cx="50%" cy="50%" r="50%">
            <stop offset="0%" stop-color="#f0cc5a"/>
            <stop offset="60%" stop-color="#D4AF37"/>
            <stop offset="100%" stop-color="#8B6914"/>
          </radialGradient>
          <filter id="glow">
            <feGaussianBlur stdDeviation="4" result="blur"/>
            <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
          </filter>
        </defs>
        <!-- Left wing -->
        <path d="M250 110 Q210 60 140 50 Q80 42 30 80 Q10 95 20 115 Q35 135 70 125 Q110 112 160 108 Q200 105 250 110 Z"
              fill="url(#mg)" filter="url(#glow)"/>
        <!-- Left curl up -->
        <path d="M30 80 Q15 65 25 50 Q38 38 55 55 Q40 62 35 75 Z"
              fill="#c9a227"/>
        <!-- Right wing -->
        <path d="M250 110 Q290 60 360 50 Q420 42 470 80 Q490 95 480 115 Q465 135 430 125 Q390 112 340 108 Q300 105 250 110 Z"
              fill="url(#mg)" filter="url(#glow)"/>
        <!-- Right curl up -->
        <path d="M470 80 Q485 65 475 50 Q462 38 445 55 Q460 62 465 75 Z"
              fill="#c9a227"/>
        <!-- Center dip highlight -->
        <ellipse cx="250" cy="115" rx="30" ry="8" fill="#f5d55a" opacity="0.6"/>
        <!-- Shine -->
        <path d="M100 72 Q160 58 220 68" stroke="rgba(255,255,255,0.25)" stroke-width="4" fill="none" stroke-linecap="round"/>
        <path d="M280 68 Q340 58 400 72" stroke="rgba(255,255,255,0.25)" stroke-width="4" fill="none" stroke-linecap="round"/>
      </svg>
    </div>

    <div class="intro-year" id="introYear">Prezidentská kampaň · 2029</div>

    <div class="intro-tagline" id="introTagline"></div>
    <div class="intro-subline" id="introSubline">Slovensko si zaslúži fúzy na najvyššom poste</div>

    <button class="intro-enter-btn" id="introEnterBtn" onclick="exitIntro()">
      Vstúpiť na stránku →
    </button>
  </div>

  <div class="intro-progress" id="introProgress"></div>
  <button class="intro-skip" onclick="exitIntro()">Preskočiť</button>
</div>

<!-- Custom cursor -->
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- NAV -->
<header id="header">
  <nav>
    <a href="#" class="nav-logo">Malík 2029</a>
    <ul class="nav-links">
      <li><a href="#program">Program</a></li>
      <li><a href="#novinky">Novinky</a></li>
      <li><a href="#about">O mne</a></li>
      <li><a href="#kontakt">Kontakt</a></li>
    </ul>
    <button class="theme-toggle" id="themeToggle" onclick="toggleTheme()" aria-label="Prepnúť tému">
      <div class="tt-track">
        <div class="tt-sun">☀️</div>
        <div class="tt-moon">🌙</div>
        <div class="tt-thumb" id="ttThumb"></div>
      </div>
    </button>
  </nav>
</header>

<!-- HERO -->
<section class="hero">
  <canvas id="particleCanvas" style="position:absolute;inset:0;width:100%;height:100%;pointer-events:none;z-index:1;opacity:0.5;"></canvas>
  <!-- FEATURE 2: Morphing blob -->
  <svg id="morphBlob" viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg" style="position:absolute;inset:-20%;width:140%;height:140%;pointer-events:none;z-index:0;">
    <defs>
      <radialGradient id="blobGrad" cx="50%" cy="50%" r="50%">
        <stop offset="0%" stop-color="#D4AF37" stop-opacity="1"/>
        <stop offset="100%" stop-color="#D4AF37" stop-opacity="0"/>
      </radialGradient>
    </defs>
    <path id="blobPath" fill="url(#blobGrad)">
      <animate attributeName="d" dur="12s" repeatCount="indefinite"
        values="
          M49.2,-57.8C63.3,-46.6,74.1,-30.3,76.4,-13C78.8,4.3,72.7,22.7,62,37.8C51.3,52.9,36,64.7,18.8,70.3C1.5,75.9,-17.7,75.3,-34.2,68.1C-50.7,60.9,-64.5,47.1,-71.2,30.4C-77.9,13.6,-77.5,-6.2,-70.5,-22.7C-63.6,-39.3,-50.1,-52.7,-35.2,-63.6C-20.2,-74.5,-3.8,-82.9,11.9,-81.6C27.6,-80.3,35.1,-69.1,49.2,-57.8Z;
          M43.7,-52.8C57.2,-41.4,69,-27.3,73.3,-10.7C77.6,5.9,74.5,25,65.4,40.5C56.3,55.9,41.2,67.7,24.6,72.5C8,77.2,-10.1,74.8,-25.9,67.4C-41.7,60,-55.1,47.5,-64.1,31.8C-73.1,16.1,-77.8,-2,-74.4,-18.5C-71,-35,-59.5,-49.9,-45.4,-61.2C-31.3,-72.5,-14.6,-80.2,1,-81.4C16.6,-82.6,30.2,-64.2,43.7,-52.8Z;
          M55.6,-64.3C70.7,-52.5,80.4,-33.6,82.1,-14.3C83.8,5,77.5,24.7,67.1,41.2C56.7,57.7,42.2,71,25.8,76.5C9.4,82.1,-8.8,79.9,-25.8,73.4C-42.8,67,-58.5,56.3,-68.1,41.8C-77.7,27.3,-81.1,9,-77.9,-7.5C-74.6,-24,-64.6,-38.7,-52,-50.8C-39.4,-62.9,-24.2,-72.5,-6.9,-75.8C10.4,-79.1,40.5,-76.2,55.6,-64.3Z;
          M49.2,-57.8C63.3,-46.6,74.1,-30.3,76.4,-13C78.8,4.3,72.7,22.7,62,37.8C51.3,52.9,36,64.7,18.8,70.3C1.5,75.9,-17.7,75.3,-34.2,68.1C-50.7,60.9,-64.5,47.1,-71.2,30.4C-77.9,13.6,-77.5,-6.2,-70.5,-22.7C-63.6,-39.3,-50.1,-52.7,-35.2,-63.6C-20.2,-74.5,-3.8,-82.9,11.9,-81.6C27.6,-80.3,35.1,-69.1,49.2,-57.8Z
        "/>
    </path>
  </svg>
  <div class="hero-bg"></div>
  <div class="orb orb1 parallax-deep"></div>
  <div class="orb orb2 parallax-mid"></div>
  <div class="hero-lines"></div>

  <div class="hero-inner" id="heroParallax">
    <div class="hero-eyebrow">Prezidentská kampaň 2029</div>
    <h1 id="heroTitle"><span class="wipe-wrap"><span class="wt">PhDr. Branislav<br>Malík, CSc.</span></span></h1>
    <p class="hero-sub">Budúcnosť, ktorá má štýl a pevné hodnoty.<br>Slovensko si zaslúži vodcu s <span class="kinetic-wrap" id="kineticWrap"><span class="kinetic-word active" id="kw0">víziou.</span><span class="kinetic-word" id="kw1">odvahou.</span><span class="kinetic-word" id="kw2">múdrosťou.</span><span class="kinetic-word" id="kw3">charakterom.</span><span class="kinetic-word" id="kw4">fúzmi.</span></span></p>
    <div class="hero-ctas">
      <a href="#support" class="btn-primary">
        <span>Podporiť kandidatúru</span>
        <span>→</span>
      </a>
      <a href="#program" class="btn-ghost">Zobraziť program</a>
    </div>
  </div>

  <div class="stats-bar">
    <div class="stat-item">
      <div class="stat-num" id="heroCount">312 847</div>
      <div class="stat-label">Podporovateľov</div>
    </div>
    <div class="stat-divider"></div>
    <div class="stat-item">
      <div class="stat-num">3</div>
      <div class="stat-label">Kľúčové piliere</div>
    </div>
    <div class="stat-divider"></div>
    <div class="stat-item">
      <div class="stat-num">2029</div>
      <div class="stat-label">Voľby</div>
    </div>
  </div>

  <div class="scroll-hint">
    <div class="scroll-line"></div>
    <span>Scroll</span>
  </div>
</section>

<div class="gold-divider"></div>

<!-- ENERGY QUOTE -->
<div class="energy-section">
  <div class="energy-bg-glow"></div>
  <div class="energy-wrap">
    <p class="section-tag">Vízia</p>
    <p class="energy-quote fade">
      Slovensko potrebuje <span>NOVÝ IMPULZ</span> —<br>
      <em>modernú energiu, ktorá spája technológie,<br>kreativitu a odvahu posunúť krajinu dopredu.</em>
    </p>
  </div>
</div>

<div class="gold-divider"></div>

<!-- ══ APPLE SCROLL STORY ══ -->
<section id="story">
  <div class="story-sticky-outer" id="storyOuter">
    <div class="story-sticky" id="storySticky">
      <!-- Background layer -->
      <div class="story-bg-layer" id="storyBg"></div>
      <!-- Animated blobs -->
      <div class="story-blob" id="sb1"></div>
      <div class="story-blob" id="sb2"></div>
      <div class="story-blob" id="sb3"></div>
      <div class="story-blob" id="sb4"></div>

      <!-- SCENE 1 — Intro -->
      <div class="story-scene" id="scene1">
        <div class="story-content">
          <div class="story-eyebrow" id="s1ey">Príbeh kandidáta</div>
          <h2 class="story-headline" id="s1h">Jeden muž.<br>Jedna <em>vízia</em>.</h2>
          <p class="story-body" id="s1b">Nie politická kariéra. Nie stranícka nominácia. Len hlboké presvedčenie, že Slovensko si zaslúži lepšie.</p>
        </div>
      </div>

      <!-- SCENE 2 — Academia -->
      <div class="story-scene" id="scene2">
        <div class="story-content">
          <div class="story-eyebrow" id="s2ey">Akademik</div>
          <h2 class="story-headline" id="s2h">20 rokov<br>na <em>katedre</em>.</h2>
          <p class="story-body" id="s2b">Filozofia nie je len teória — je to spôsob myslenia. A myslenie formuje rozhodnutia. PhDr. Malík, CSc. vie, ako premeniť idey na činy.</p>
          <div class="story-stats-row" id="s2stats">
            <div class="story-stat"><div class="story-stat-num">20+</div><div class="story-stat-label">Rokov pedagógie</div></div>
            <div class="story-stat-divider"></div>
            <div class="story-stat"><div class="story-stat-num">47</div><div class="story-stat-label">Publikácií</div></div>
            <div class="story-stat-divider"></div>
            <div class="story-stat"><div class="story-stat-num">2</div><div class="story-stat-label">Vedecké tituly</div></div>
          </div>
        </div>
      </div>

      <!-- SCENE 3 — Values -->
      <div class="story-scene" id="scene3">
        <div class="story-content">
          <div class="story-eyebrow" id="s3ey">Hodnoty</div>
          <h2 class="story-headline" id="s3h">Transparentnosť<br>nie je <em>slogan</em>.</h2>
          <p class="story-body" id="s3b">Keď hovorí o konci politiky "našich ľudí" — hovorí to človek, ktorý nikdy nebol súčasťou tejto hry. To je rozdiel, ktorý sa nedá kúpiť.</p>
        </div>
      </div>

      <!-- SCENE 4 — Future -->
      <div class="story-scene" id="scene4">
        <div class="story-content">
          <div class="story-eyebrow" id="s4ey">Budúcnosť</div>
          <h2 class="story-headline" id="s4h">Slovensko <em>2029</em>.<br>Tvoja voľba.</h2>
          <p class="story-body" id="s4b">Každé štyri roky dostaneme šancu. Tentokrát je táto šanca iná — pretože kandidát je iný. Autentický. Odvážny. So srdcom na správnom mieste.</p>
          <div style="opacity:0" id="s4cta">
            <a href="#support" class="btn-primary" style="pointer-events:auto;">Pridať sa k hnutiu →</a>
          </div>
        </div>
      </div>

      <!-- Progress dots -->
      <div class="story-dots" id="storyDots">
        <div class="story-dot active" data-scene="0"></div>
        <div class="story-dot" data-scene="1"></div>
        <div class="story-dot" data-scene="2"></div>
        <div class="story-dot" data-scene="3"></div>
      </div>
      <div class="story-scroll-hint" id="storyScrollHint">
        <div class="story-scroll-line"></div>
        <span>Scroll</span>
      </div>
    </div>
  </div>
</section>

<div class="gold-divider"></div>

<!-- PROGRAM -->
<div id="program" style="background: linear-gradient(180deg, var(--dark2) 0%, var(--dark) 100%);">
  <div class="section">
    <p class="section-tag fade sd-left">Program</p>
    <h2 class="section-title fade sd-reveal">Tri piliere <em>zmeny</em></h2>
    <p class="section-lead fade sd-left" data-delay="1">Konkrétne kroky, merateľné ciele a odvaha ich presadiť. Nie sľuby — činy.</p>

    <div class="program-grid">
      <div class="program-card fade fade-delay-1 mag-card glass-card">
        <span class="program-icon">📚</span>
        <div class="program-num">01</div>
        <h3>Vzdelávanie</h3>
        <p>Digitálne školy, moderné učebné metódy a investície do učiteľov. Vzdelaná generácia je základ prosperujúceho Slovenska.</p>
      </div>
      <div class="program-card fade fade-delay-2 mag-card glass-card">
        <span class="program-icon">💼</span>
        <div class="program-num">02</div>
        <h3>Ekonomika</h3>
        <p>Podpora mladých podnikateľov, znižovanie byrokracie a pritiahnutie moderných investícií. Silná ekonomika pre všetkých.</p>
      </div>
      <div class="program-card fade fade-delay-3 mag-card glass-card">
        <span class="program-icon">🌍</span>
        <div class="program-num">03</div>
        <h3>Spoločnosť</h3>
        <p>Jednota, stabilita a dlhodobá vízia. Krajina, kde sa ľudia cítia bezpečne a hrdí na svoju identitu.</p>
      </div>
    </div>
  </div>
</div>

<div class="gold-divider"></div>

<!-- ABOUT -->
<div id="about">
  <div class="section">
    <div class="about-layout">
      <div class="about-visual fade">
        <div class="about-portrait" id="avatarBox">
          <!-- Animated SVG avatar with iconic mustache -->
          <svg id="filosofSvg" viewBox="0 0 300 380" xmlns="http://www.w3.org/2000/svg" style="width:80%;max-width:260px;position:relative;z-index:2;">
            <!-- Head -->
            <ellipse cx="150" cy="160" rx="90" ry="105" fill="#1e2a3a" stroke="rgba(212,175,55,0.3)" stroke-width="1.5"/>
            <!-- Hair -->
            <ellipse cx="150" cy="70" rx="90" ry="42" fill="#0d1420"/>
            <path d="M60 100 Q50 60 80 45 Q110 30 150 28 Q190 30 220 45 Q250 60 240 100" fill="#0d1420"/>
            <!-- Ear left -->
            <ellipse cx="60" cy="165" rx="14" ry="18" fill="#1e2a3a" stroke="rgba(212,175,55,0.2)" stroke-width="1"/>
            <!-- Ear right -->
            <ellipse cx="240" cy="165" rx="14" ry="18" fill="#1e2a3a" stroke="rgba(212,175,55,0.2)" stroke-width="1"/>
            <!-- Eyes whites -->
            <ellipse cx="115" cy="150" rx="18" ry="14" fill="white"/>
            <ellipse cx="185" cy="150" rx="18" ry="14" fill="white"/>
            <!-- Pupils (will be animated) -->
            <circle id="pupilL" cx="115" cy="152" r="8" fill="#0d1420"/>
            <circle id="pupilR" cx="185" cy="152" r="8" fill="#0d1420"/>
            <!-- Eye shine -->
            <circle cx="119" cy="148" r="3" fill="white" opacity="0.8"/>
            <circle cx="189" cy="148" r="3" fill="white" opacity="0.8"/>
            <!-- Eyebrows -->
            <path d="M97 132 Q115 126 133 132" stroke="#8a7060" stroke-width="3" fill="none" stroke-linecap="round"/>
            <path d="M167 132 Q185 126 203 132" stroke="#8a7060" stroke-width="3" fill="none" stroke-linecap="round"/>
            <!-- Nose -->
            <path d="M145 165 Q138 185 148 192 Q152 194 155 192 Q165 186 158 165" fill="#162030" stroke="rgba(212,175,55,0.15)" stroke-width="1"/>
            <!-- THE ICONIC MUSTACHE 🥸 -->
            <g id="mustacheGroup">
              <!-- Left side -->
              <path d="M105 208 Q118 200 140 205 Q150 207 150 210" fill="#4a3520" stroke="#6b4c2a" stroke-width="0.5"/>
              <path d="M105 208 Q100 215 108 220 Q120 225 140 212 Q150 209 150 210" fill="#5c4030"/>
              <!-- Right side -->
              <path d="M195 208 Q182 200 160 205 Q150 207 150 210" fill="#4a3520" stroke="#6b4c2a" stroke-width="0.5"/>
              <path d="M195 208 Q200 215 192 220 Q180 225 160 212 Q150 209 150 210" fill="#5c4030"/>
              <!-- Mustache shine -->
              <path d="M115 208 Q130 204 148 207" stroke="rgba(255,255,255,0.12)" stroke-width="1.5" fill="none" stroke-linecap="round"/>
              <path d="M185 208 Q170 204 152 207" stroke="rgba(255,255,255,0.12)" stroke-width="1.5" fill="none" stroke-linecap="round"/>
            </g>
            <!-- Smile -->
            <path d="M130 230 Q150 244 170 230" stroke="#8a6040" stroke-width="2" fill="none" stroke-linecap="round"/>
            <!-- Collar / suit -->
            <path d="M60 280 Q80 260 110 265 L150 310 L190 265 Q220 260 240 280 L240 380 L60 380 Z" fill="#0d1420" stroke="rgba(212,175,55,0.2)" stroke-width="1"/>
            <!-- Tie -->
            <path d="M150 280 L142 300 L150 340 L158 300 Z" fill="#D4AF37" opacity="0.8"/>
            <!-- Glasses frames -->
            <circle cx="115" cy="150" r="22" fill="none" stroke="rgba(212,175,55,0.6)" stroke-width="2"/>
            <circle cx="185" cy="150" r="22" fill="none" stroke="rgba(212,175,55,0.6)" stroke-width="2"/>
            <line x1="137" y1="150" x2="163" y2="150" stroke="rgba(212,175,55,0.6)" stroke-width="2"/>
            <line x1="60" y1="148" x2="93" y2="150" stroke="rgba(212,175,55,0.5)" stroke-width="2"/>
            <line x1="207" y1="150" x2="240" y2="148" stroke="rgba(212,175,55,0.5)" stroke-width="2"/>
          </svg>
          <!-- Floating mustache particles -->
          <div class="moustache-float" style="top:10%;left:5%">~</div>
          <div class="moustache-float" style="top:20%;right:8%;animation-delay:1s">~</div>
          <div class="moustache-float" style="bottom:25%;left:8%;animation-delay:2s">~</div>
        </div>
        <div class="about-badge">
          <span>PhDr.</span>
          CSc.
        </div>
      </div>
      <div class="about-text">
        <p class="section-tag fade sd-left">O kandidátovi</p>
        <h2 class="section-title fade sd-reveal">Skúsenosť,<br><em>odbornosť, vízia</em></h2>
        <p class="fade">PhDr. Branislav Malík, CSc. predstavuje kombináciu hlbokých skúseností a moderného pohľadu na spoločnosť. Celý život zasvätil verejnému životu a akademickej práci.</p>
        <p class="fade">Je pripravený viesť Slovensko do modernej budúcnosti — s pokorou, odvahou a jasnou stratégiou.</p>
        <div class="about-tags fade">
          <span class="tag">Akademik</span>
          <span class="tag">Verejná správa</span>
          <span class="tag">Medzinárodné vzťahy</span>
          <span class="tag">Inovácie</span>
        </div>
      </div>
    </div>
  </div>
</div>

<div class="gold-divider"></div>

<!-- COUNTDOWN -->
<div id="volby" style="background:var(--dark2);">
  <div class="section" style="text-align:center;padding-top:80px;padding-bottom:80px;">
    <p class="section-tag fade" style="justify-content:center;">Voľby 2029</p>
    <h2 class="section-title fade" style="margin-bottom:40px;">Čas do <em>rozhodovania</em></h2>
    <div class="countdown-grid fade">
      <div class="cd-item"><div class="cd-num" id="cdDays">000</div><div class="cd-label">Dní</div></div>
      <div class="cd-sep">:</div>
      <div class="cd-item"><div class="cd-num" id="cdHours">00</div><div class="cd-label">Hodín</div></div>
      <div class="cd-sep">:</div>
      <div class="cd-item"><div class="cd-num" id="cdMins">00</div><div class="cd-label">Minút</div></div>
      <div class="cd-sep">:</div>
      <div class="cd-item"><div class="cd-num" id="cdSecs">00</div><div class="cd-label">Sekúnd</div></div>
    </div>
    <p class="fade" style="color:var(--muted);font-size:0.85rem;margin-top:24px;letter-spacing:0.1em;">DO PREZIDENTSKÝCH VOLIEB · APRÍL 2029</p>
  </div>
</div>

<div class="gold-divider"></div>

<!-- NEWS / PRESS -->
<div id="novinky" style="background:linear-gradient(180deg,var(--dark) 0%,var(--dark2) 100%);">
  <div class="section">
    <p class="section-tag fade sd-left">Médiá</p>
    <h2 class="section-title fade sd-reveal">Najnovšie <em>správy</em></h2>
    <p class="section-lead fade">Sledujte priebeh kampane, vyjadrenia kandidáta a mediálne pokrytie.</p>
    <div class="news-grid">
      <article class="news-card fade mag-card glass-card" data-delay="1">
        <div class="news-tag">Prejav</div>
        <div class="news-date">15. marca 2026</div>
        <h3>Malík predstavil detailný plán vzdelávacej reformy</h3>
        <p>Na konferencii v Bratislave kandidát predložil konkrétne kroky digitalizácie slovenských škôl s rozpočtom 2 mld. €.</p>
        <div class="news-read">Čítať viac →</div>
      </article>
      <article class="news-card fade mag-card glass-card" data-delay="2">
        <div class="news-tag news-tag--media">Rozhovor</div>
        <div class="news-date">8. marca 2026</div>
        <h3>Rozhovor pre Denník N: „Filozofia nie je luxus, je to základ"</h3>
        <p>Kandidát hovoril o prepojení akademického myslenia s reálnou politikou a o potrebe dlhodobého uvažovania.</p>
        <div class="news-read">Čítať viac →</div>
      </article>
      <article class="news-card fade mag-card glass-card" data-delay="3">
        <div class="news-tag news-tag--event">Udalosť</div>
        <div class="news-date">1. marca 2026</div>
        <h3>Kampaň štartuje v 8 regiónoch Slovenska súčasne</h3>
        <p>Tím Malík 2029 spustil koordinovanú kampaň naprieč celou krajinou s viac ako 200 dobrovoľníkmi.</p>
        <div class="news-read">Čítať viac →</div>
      </article>
    </div>
    <div style="text-align:center;margin-top:40px;" class="fade">
      <a href="#" class="btn-ghost">Všetky správy</a>
    </div>
  </div>
</div>

<div class="gold-divider"></div>

<!-- SUPPORT MAP -->
<div id="mapa" style="background:var(--dark2);">
  <div class="section">
    <p class="section-tag fade sd-left">Podpora</p>
    <h2 class="section-title fade sd-reveal">Slovensko <em>za Malíka</em></h2>
    <p class="section-lead fade">Podpora rastie vo všetkých krajoch. Každý region má svoju silu.</p>
    <div class="map-layout fade">
      <div class="map-svg-wrap">
        <svg id="slovakiaMap" viewBox="0 0 800 420" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <filter id="mapGlow"><feGaussianBlur stdDeviation="4" result="b"/><feMerge><feMergeNode in="b"/><feMergeNode in="SourceGraphic"/></feMerge></filter>
          </defs>

          <!-- Bratislavský -->
          <path class="sk-region" data-region="Bratislavský" data-pct="87" d="M 1.7,289.9 28.4,258.2 53.5,237.0 75.3,247.6 98.7,262.4 112.1,296.3 92.0,325.9 61.9,349.2 28.4,364.0 11.7,353.4 1.7,332.3 1.7,289.9 Z"/>
          <text x="47.3" y="300.5" font-size="11" fill="rgba(212,175,55,0.85)" text-anchor="middle" font-family="DM Sans,sans-serif" font-weight="700" pointer-events="none">BA</text>

          <!-- Trnavský -->
          <path class="sk-region" data-region="Trnavský" data-pct="74" d="M 75.3,247.6 98.7,220.1 128.8,205.3 170.6,198.9 212.4,211.6 242.5,237.0 254.2,268.8 232.5,304.8 195.7,332.3 162.2,347.1 120.4,342.9 92.0,325.9 112.1,296.3 98.7,262.4 75.3,247.6 Z"/>
          <text x="151.4" y="269.9" font-size="11" fill="rgba(212,175,55,0.85)" text-anchor="middle" font-family="DM Sans,sans-serif" font-weight="700" pointer-events="none">TT</text>

          <!-- Trenčiansky -->
          <path class="sk-region" data-region="Trenčiansky" data-pct="68" d="M 128.8,131.2 162.2,110.1 195.7,99.5 237.5,110.1 270.9,131.2 296.0,163.0 299.4,205.3 279.3,241.3 254.2,268.8 242.5,237.0 212.4,211.6 170.6,198.9 145.5,173.5 132.1,152.4 128.8,131.2 Z"/>
          <text x="210.4" y="171.0" font-size="11" fill="rgba(212,175,55,0.85)" text-anchor="middle" font-family="DM Sans,sans-serif" font-weight="700" pointer-events="none">TN</text>

          <!-- Nitriansky -->
          <path class="sk-region" data-region="Nitriansky" data-pct="71" d="M 92.0,325.9 120.4,342.9 162.2,347.1 195.7,332.3 232.5,304.8 254.2,268.8 279.3,241.3 299.4,268.8 321.1,304.8 337.8,342.9 326.1,374.6 287.7,395.8 237.5,402.1 195.7,395.8 153.9,385.2 120.4,368.3 92.0,353.4 61.9,349.2 92.0,325.9 Z"/>
          <text x="203.3" y="338.4" font-size="11" fill="rgba(212,175,55,0.85)" text-anchor="middle" font-family="DM Sans,sans-serif" font-weight="700" pointer-events="none">NR</text>

          <!-- Žilinský -->
          <path class="sk-region" data-region="Žilinský" data-pct="79" d="M 237.5,110.1 279.3,93.1 321.1,78.3 362.9,78.3 404.7,88.9 438.2,105.8 463.3,131.2 471.6,173.5 446.6,211.6 404.7,232.8 362.9,241.3 329.5,237.0 299.4,205.3 296.0,163.0 270.9,131.2 237.5,110.1 Z"/>
          <text x="351.6" y="149.5" font-size="11" fill="rgba(212,175,55,0.85)" text-anchor="middle" font-family="DM Sans,sans-serif" font-weight="700" pointer-events="none">ZA</text>

          <!-- Banskobystrický -->
          <path class="sk-region" data-region="Banskobystrický" data-pct="65" d="M 299.4,268.8 329.5,237.0 362.9,241.3 404.7,232.8 446.6,211.6 471.6,173.5 496.7,190.5 530.2,220.1 555.3,254.0 560.3,296.3 538.5,332.3 496.7,364.0 446.6,385.2 396.4,393.7 346.2,389.4 304.4,381.0 262.6,368.3 229.1,353.4 195.7,332.3 232.5,304.8 254.2,268.8 279.3,241.3 299.4,268.8 Z"/>
          <text x="379.9" y="291.7" font-size="11" fill="rgba(212,175,55,0.85)" text-anchor="middle" font-family="DM Sans,sans-serif" font-weight="700" pointer-events="none">BB</text>

          <!-- Prešovský -->
          <path class="sk-region" data-region="Prešovský" data-pct="62" d="M 471.6,14.8 513.4,8.5 555.3,14.8 597.1,36.0 638.9,50.8 680.7,72.0 714.1,93.1 739.2,120.6 747.6,163.0 722.5,198.9 680.7,226.5 630.5,241.3 580.3,254.0 538.5,254.0 496.7,237.0 463.3,211.6 446.6,173.5 454.9,131.2 459.9,88.9 463.3,46.6 471.6,14.8 Z"/>
          <text x="574.6" y="126.3" font-size="11" fill="rgba(212,175,55,0.85)" text-anchor="middle" font-family="DM Sans,sans-serif" font-weight="700" pointer-events="none">PO</text>

          <!-- Košický -->
          <path class="sk-region" data-region="Košický" data-pct="69" d="M 538.5,254.0 580.3,254.0 630.5,241.3 680.7,226.5 722.5,198.9 747.6,163.0 764.3,190.5 781.0,226.5 789.4,268.8 777.7,311.1 747.6,342.9 705.8,368.3 660.6,385.2 610.5,393.7 560.3,389.4 521.8,374.6 488.4,359.8 471.6,332.3 480.0,296.3 496.7,262.4 496.7,237.0 538.5,254.0 Z"/>
          <text x="626.9" y="287.8" font-size="11" fill="rgba(212,175,55,0.85)" text-anchor="middle" font-family="DM Sans,sans-serif" font-weight="700" pointer-events="none">KE</text>
        </svg>
        <div class="map-tooltip" id="mapTooltip"></div>
      </div>
      <div class="map-legend">
        <div class="map-legend-title">Podpora podľa krajov</div>
        <div class="map-bars" id="mapBars"></div>
      </div>
    </div>
  </div>
</div>

<div class="gold-divider"></div>

<!-- CONTACT / VOLUNTEER -->
<div id="kontakt" style="background:linear-gradient(180deg,var(--dark2) 0%,var(--dark) 100%);">
  <div class="section">
    <div class="contact-layout">
      <div class="sd-left fade">
        <p class="section-tag">Zapoj sa</p>
        <h2 class="section-title" style="margin-bottom:16px;">Staň sa <em>súčasťou</em><br>tímu</h2>
        <p style="color:var(--muted);line-height:1.75;font-size:1rem;font-weight:300;margin-bottom:32px;">Hľadáme dobrovoľníkov, koordinátorov a mediálnych partnerov v každom regióne Slovenska. Tvoja pomoc je pre nás dôležitá.</p>
        <div class="contact-info-items">
          <div class="ci-item"><div class="ci-icon">📧</div><div><div class="ci-label">Email</div><div class="ci-val">kampan@malik2029.sk</div></div></div>
          <div class="ci-item"><div class="ci-icon">📞</div><div><div class="ci-label">Telefón</div><div class="ci-val">+421 900 2029 SK</div></div></div>
          <div class="ci-item"><div class="ci-icon">📍</div><div><div class="ci-label">Sídlo kampane</div><div class="ci-val">Šoltésovej 4, Bratislava</div></div></div>
        </div>
      </div>
      <div class="contact-form-wrap sd-right fade">
        <div class="contact-form-inner">
          <h3 style="font-family:'Playfair Display',serif;font-size:1.2rem;margin-bottom:20px;color:var(--gold);">Napíšte nám</h3>
          <div class="form-row">
            <div class="form-group"><label>Meno</label><input type="text" placeholder="Ján Novák" id="fName"></div>
            <div class="form-group"><label>Email</label><input type="email" placeholder="jan@email.sk" id="fEmail"></div>
          </div>
          <div class="form-group">
            <label>Záujem</label>
            <div class="form-select-wrap">
              <select id="fRole">
                <option>Dobrovoľník v teréne</option>
                <option>Koordinátor regiónu</option>
                <option>Mediálny partner</option>
                <option>Finančná podpora</option>
                <option>Iné</option>
              </select>
            </div>
          </div>
          <div class="form-group"><label>Správa</label><textarea placeholder="Napíšte nám..." rows="4" id="fMsg"></textarea></div>
          <button class="btn-primary" style="width:100%;justify-content:center;border:none;cursor:pointer;" onclick="submitForm()">Odoslať správu →</button>
          <div class="form-success" id="formSuccess">✅ Správa odoslaná! Ozveme sa do 48 hodín.</div>
        </div>
      </div>
    </div>
  </div>
</div>

<div class="gold-divider"></div>

<!-- QUOTES / PREČO MALÍK -->
<div id="preco" style="background:var(--dark);">
  <div class="section">
    <p class="section-tag fade sd-left">Prečo Malík?</p>
    <h2 class="section-title fade sd-reveal" style="margin-bottom:48px;">Päť dôvodov, prečo <em>práve on</em></h2>
    <div class="quotes-grid">
      <div class="quote-card fade mag-card glass-card" data-delay="1">
        <div class="quote-num">01</div>
        <div class="quote-icon">🥸</div>
        <p>Nerobím politiku <strong>popod fúzy</strong> — môžete u mňa očakávať absolútnu transparentnosť a autenticitu.</p>
      </div>
      <div class="quote-card fade mag-card glass-card" data-delay="2">
        <div class="quote-num">02</div>
        <div class="quote-icon">🌲</div>
        <p>Na Slovensku mi záleží — presadím aktívnu <strong>ochranu lesov a vôd</strong>. Ekologický dlh nesmú splácať naše deti.</p>
      </div>
      <div class="quote-card fade mag-card glass-card" data-delay="3">
        <div class="quote-num">03</div>
        <div class="quote-icon">⚖️</div>
        <p>Koniec politiky <strong>"našich ľudí"</strong> — Prezidentský palác nemôže byť tichým svedkom rozoberania štátu.</p>
      </div>
      <div class="quote-card fade mag-card glass-card" data-delay="1">
        <div class="quote-num">04</div>
        <div class="quote-icon">📚</div>
        <p>Budem <strong>hlasom učiteľov a študentov</strong>, aby školstvo dostalo zdroje a pozornosť, ktoré si zaslúži.</p>
      </div>
      <div class="quote-card fade mag-card glass-card" data-delay="2">
        <div class="quote-num">05</div>
        <div class="quote-icon">🏥</div>
        <p>Budem vyvíjať tlak aby <strong>lekári a sestry mali dôstojné podmienky</strong>. Pacient nie je číslo — je ľudská bytosť.</p>
      </div>
    </div>
  </div>
</div>

<div class="gold-divider"></div>

<!-- COMPARISON TABLE -->
<div id="porovnanie" style="background:var(--dark2);">
  <div class="section">
    <p class="section-tag fade sd-left">Porovnanie</p>
    <h2 class="section-title fade sd-reveal" style="margin-bottom:12px;">Fakty <em>hovorí samy</em></h2>
    <p class="section-lead fade">Objektívne kritériá. Žiadna politika. Len fakty.</p>
    <div class="comp-table-wrap fade">
      <table class="comp-table">
        <thead>
          <tr>
            <th class="comp-criteria">Kritérium</th>
            <th class="comp-us">
              <div class="comp-head-inner">
                <span class="comp-avatar">🥸</span>
                <span>Malík</span>
              </div>
            </th>
            <th class="comp-them">
              <div class="comp-head-inner">
                <span class="comp-avatar comp-avatar-gray">👤</span>
                <span>Kandidát X</span>
              </div>
            </th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Profesor na Univerzite Komenského</td>
            <td class="comp-yes"><span class="comp-badge comp-badge-yes">✓ Áno</span></td>
            <td class="comp-no"><span class="comp-badge comp-badge-no">✗ Nie</span></td>
          </tr>
          <tr>
            <td>Akademický titul (PhDr., CSc.)</td>
            <td class="comp-yes"><span class="comp-badge comp-badge-yes">✓ Áno</span></td>
            <td class="comp-no"><span class="comp-badge comp-badge-no">✗ Nie</span></td>
          </tr>
          <tr>
            <td>Verejný program s konkrétnymi bodmi</td>
            <td class="comp-yes"><span class="comp-badge comp-badge-yes">✓ Áno</span></td>
            <td class="comp-no"><span class="comp-badge comp-badge-no">✗ Nie</span></td>
          </tr>
          <tr>
            <td>Transparentné financovanie kampane</td>
            <td class="comp-yes"><span class="comp-badge comp-badge-yes">✓ Áno</span></td>
            <td class="comp-no"><span class="comp-badge comp-badge-no">✗ Neuvedené</span></td>
          </tr>
          <tr>
            <td>Záväzok ochrany životného prostredia</td>
            <td class="comp-yes"><span class="comp-badge comp-badge-yes">✓ Áno</span></td>
            <td class="comp-no"><span class="comp-badge comp-badge-no">✗ Nie</span></td>
          </tr>
          <tr>
            <td>Skúsenosť v pedagogike</td>
            <td class="comp-yes"><span class="comp-badge comp-badge-yes">✓ 20+ rokov</span></td>
            <td class="comp-no"><span class="comp-badge comp-badge-no">✗ Nie</span></td>
          </tr>
          <tr>
            <td>Ikonické fúzy</td>
            <td class="comp-yes"><span class="comp-badge comp-badge-yes">✓ Legendárne</span></td>
            <td class="comp-no"><span class="comp-badge comp-badge-no">✗ Žiadne</span></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</div>

<div class="gold-divider"></div>

<!-- SUPPORT -->
  <div class="support-inner">
    <div>
      <p class="section-tag fade">Podpora</p>
      <h2 class="section-title fade">Pridajte sa<br>k <em>hnutiu</em></h2>
      <p class="section-lead fade" style="margin-bottom:0">Každý hlas sa počíta. Spoločne môžeme zmeniť smer krajiny.</p>

      <div class="timeline" style="margin-top:48px">
        <div class="timeline-item fade">
          <div class="timeline-year">Fáza 1 — Jar 2027</div>
          <h4>Zber podpisov</h4>
          <p>Spustenie oficálnej kampane a zberu nominačných podpisov.</p>
        </div>
        <div class="timeline-item fade fade-delay-1">
          <div class="timeline-year">Fáza 2 — Jeseň 2028</div>
          <h4>Národná kampaň</h4>
          <p>Debaty, stretnutia s občanmi a prezentácia programu po celom Slovensku.</p>
        </div>
        <div class="timeline-item fade fade-delay-2">
          <div class="timeline-year">Fáza 3 — 2029</div>
          <h4>Voľby prezidenta</h4>
          <p>Rozhodujúci moment pre budúcnosť Slovenska.</p>
        </div>
      </div>
    </div>

    <div class="fade">
      <div class="support-counter-box">
        <span class="counter-num" id="voteCount">312 847</span>
        <div class="counter-label">podporovateľov po celom Slovensku</div>
        <div class="progress-bar">
          <div class="progress-fill" id="progressFill"></div>
        </div>
        <div class="progress-label">
          <span>0</span>
          <span>a stále rastie ↑</span>
        </div>
        <button onclick="addVote()" class="btn-primary" style="width:100%;justify-content:center;border:none;cursor:pointer;font-size:1rem;" id="voteBtn">
          🥸 Podporiť fúzy!
        </button>
      </div>
    </div>
  </div>
</div>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">Malík 2029</div>
  <p class="footer-copy">© 2029 Malík kampaň · Všetky práva vyhradené</p>
</footer>

<script>
// ══════════════════════════════════
// CINEMATIC INTRO
// ══════════════════════════════════
(function() {
  document.body.classList.add('intro-active');

  const intro      = document.getElementById('intro');
  const mustache   = document.getElementById('introMustache');
  const yearEl     = document.getElementById('introYear');
  const taglineEl  = document.getElementById('introTagline');
  const sublineEl  = document.getElementById('introSubline');
  const enterBtn   = document.getElementById('introEnterBtn');
  const progress   = document.getElementById('introProgress');
  const iCanvas    = document.getElementById('introCanvas');
  const ictx       = iCanvas.getContext('2d');

  // Gold aura cursor tracking
  const introCursor = document.getElementById('introCursor');
  let icx = window.innerWidth/2, icy = window.innerHeight/2;
  let icrx = icx, icry = icy;
  document.addEventListener('mousemove', e => { icx = e.clientX; icy = e.clientY; });
  (function trackIC() {
    if (!introCursor) return;
    icrx += (icx - icrx) * 0.13;
    icry += (icy - icry) * 0.13;
    introCursor.style.left = icrx + 'px';
    introCursor.style.top  = icry + 'px';
    requestAnimationFrame(trackIC);
  })();

  // Resize intro canvas
  function resizeIC() { iCanvas.width = window.innerWidth; iCanvas.height = window.innerHeight; }
  resizeIC(); window.addEventListener('resize', resizeIC);

  // Floating gold particles on intro bg
  const iParticles = Array.from({length:60}, () => ({
    x: Math.random() * iCanvas.width,
    y: Math.random() * iCanvas.height,
    r: Math.random() * 1.4 + 0.3,
    vx: (Math.random()-.5)*.3,
    vy: -(Math.random()*.4+.1),
    a: Math.random()*.5+.1
  }));
  function animIC() {
    if (!intro.parentNode) return;
    ictx.clearRect(0,0,iCanvas.width,iCanvas.height);
    iParticles.forEach(p => {
      p.x+=p.vx; p.y+=p.vy;
      if(p.y<-4){p.y=iCanvas.height+4;p.x=Math.random()*iCanvas.width;}
      ictx.beginPath();
      ictx.arc(p.x,p.y,p.r,0,Math.PI*2);
      ictx.fillStyle=`rgba(212,175,55,${p.a})`;
      ictx.fill();
    });
    // Draw connecting lines
    for(let i=0;i<iParticles.length;i++)
      for(let j=i+1;j<iParticles.length;j++){
        const dx=iParticles[i].x-iParticles[j].x, dy=iParticles[i].y-iParticles[j].y;
        const d=Math.sqrt(dx*dx+dy*dy);
        if(d<90){ictx.beginPath();ictx.moveTo(iParticles[i].x,iParticles[i].y);ictx.lineTo(iParticles[j].x,iParticles[j].y);ictx.strokeStyle=`rgba(212,175,55,${.07*(1-d/90)})`;ictx.lineWidth=.5;ictx.stroke();}
      }
    requestAnimationFrame(animIC);
  }
  animIC();

  // Sequence
  const taglineText = 'Fúzy, ktoré menia Slovensko.';
  const taglineWords = taglineText.split(' ');

  let seq = [
    // t=0: open letterbox
    [0,    ()=> intro.classList.add('bars-open')],
    // t=400: drop mustache
    [400,  ()=> { mustache.classList.add('show'); yearEl.style.opacity='1'; }],
    // t=1400: mustache starts pulsing
    [1500, ()=> mustache.classList.add('pulse')],
    // t=1800: tagline words appear one by one
    [1800, ()=> {
      taglineEl.innerHTML = taglineWords.map(w=>`<span class="word">${w === 'menia' || w === 'Slovensko.' ? `<em>${w}</em>` : w}</span>`).join(' ');
      const words = taglineEl.querySelectorAll('.word');
      words.forEach((w,i) => setTimeout(()=>w.classList.add('show'), i*140));
    }],
    // t=2800: subline
    [2900, ()=> sublineEl.style.opacity='1'],
    // t=3400: enter button
    [3400, ()=> {
      enterBtn.style.opacity='1';
      enterBtn.style.transform='translateY(0)';
    }],
    // progress bar (5s total)
  ];

  seq.forEach(([t, fn]) => setTimeout(fn, t));

  // Progress bar animation
  setTimeout(()=>{
    progress.style.transition = 'width 4.8s linear';
    progress.style.width = '100%';
  }, 200);

  // Auto-exit after 8s if they haven't clicked
  let autoTimer = setTimeout(()=>exitIntro(), 8200);

  window._introAutoTimer = autoTimer;
})();

function exitIntro() {
  clearTimeout(window._introAutoTimer);
  const intro = document.getElementById('intro');
  const ic = document.getElementById('introCursor');
  if (!intro) return;
  if (ic) ic.remove();
  intro.classList.add('exit');
  setTimeout(()=>{ intro.remove(); document.body.classList.remove('intro-active'); }, 850);
}

// ══════════════════════════════════
// THEME TOGGLE — Sun/Moon animation
// ══════════════════════════════════
let isLight = false;

function toggleTheme() {
  const btn = document.getElementById('themeToggle');
  const rect = btn.getBoundingClientRect();
  const ox = rect.left + rect.width / 2;
  const oy = rect.top  + rect.height / 2;

  const burst = document.getElementById('sunBurst');
  const ray   = document.getElementById('sunRayEl');
  const maxR  = Math.sqrt(window.innerWidth**2 + window.innerHeight**2) * 2;

  burst.classList.add('active');
  ray.style.cssText = `
    left:${ox}px; top:${oy}px;
    width:20px; height:20px;
    margin-left:-10px; margin-top:-10px;
    transform:scale(0);
    transition:none;
  `;

  // Force reflow
  ray.getBoundingClientRect();

  if (!isLight) {
    // Going LIGHT — golden sun explosion
    ray.style.background = 'radial-gradient(circle,#fffde7 0%,#f0cc5a 30%,rgba(240,204,90,0.4) 60%,transparent 70%)';
    ray.style.transition = `transform 0.65s cubic-bezier(.16,1,.3,1), opacity 0.3s ease 0.5s`;
    ray.style.transform  = `scale(${maxR / 10})`;
    ray.style.opacity    = '1';

    setTimeout(() => {
      document.body.classList.add('light');
      isLight = true;
    }, 300);

    setTimeout(() => {
      ray.style.opacity = '0';
      setTimeout(() => { burst.classList.remove('active'); ray.style.transform='scale(0)'; ray.style.opacity='1'; }, 320);
    }, 520);

  } else {
    // Going DARK — moon silver sweep
    ray.style.background = 'radial-gradient(circle,#1a2040 0%,#0a0f1e 40%,rgba(10,15,30,0.5) 65%,transparent 70%)';
    ray.style.transition = `transform 0.65s cubic-bezier(.16,1,.3,1), opacity 0.3s ease 0.5s`;
    ray.style.transform  = `scale(${maxR / 10})`;
    ray.style.opacity    = '1';

    setTimeout(() => {
      document.body.classList.remove('light');
      isLight = false;
    }, 300);

    setTimeout(() => {
      ray.style.opacity = '0';
      setTimeout(() => { burst.classList.remove('active'); ray.style.transform='scale(0)'; ray.style.opacity='1'; }, 320);
    }, 520);
  }
}


// ══════════════════════════════════════════════════════
// FEATURE 4 — LENIS SMOOTH SCROLL
// ══════════════════════════════════════════════════════
let lenis;
if (typeof Lenis !== 'undefined') {
  lenis = new Lenis({
    duration: 1.3,
    easing: t => Math.min(1, 1.001 - Math.pow(2, -10 * t)),
    smoothWheel: true,
    touchMultiplier: 1.5,
  });
  function rafLenis(time) { lenis.raf(time); requestAnimationFrame(rafLenis); }
  requestAnimationFrame(rafLenis);
  // Connect GSAP ScrollTrigger to Lenis
  if (typeof ScrollTrigger !== 'undefined') {
    lenis.on('scroll', ScrollTrigger.update);
  }
}

// ══════════════════════════════════════════════════════
// FEATURE 5 — GSAP ScrollTrigger (section reveals)
// ══════════════════════════════════════════════════════
if (typeof gsap !== 'undefined' && typeof ScrollTrigger !== 'undefined') {
  gsap.registerPlugin(ScrollTrigger);

  // Section titles stagger in
  gsap.utils.toArray('.section-title').forEach(el => {
    gsap.fromTo(el,
      { y: 60, opacity: 0 },
      { y: 0, opacity: 1, duration: 1, ease: 'power3.out',
        scrollTrigger: { trigger: el, start: 'top 85%', toggleActions: 'play none none none' }
      }
    );
  });

  // Section tags slide in from left
  gsap.utils.toArray('.section-tag').forEach(el => {
    gsap.fromTo(el,
      { x: -40, opacity: 0 },
      { x: 0, opacity: 1, duration: 0.7, ease: 'power2.out',
        scrollTrigger: { trigger: el, start: 'top 88%' }
      }
    );
  });

  // Counter numbers count up
  gsap.utils.toArray('.cd-num').forEach(el => {
    const final = el.textContent;
    scrollTrigger: ScrollTrigger.create({
      trigger: el, start: 'top 80%',
      once: true,
      onEnter: () => {
        const num = parseInt(final);
        if (!isNaN(num)) gsap.fromTo(el,
          { textContent: 0 },
          { textContent: num, duration: 2, ease: 'power2.out', snap: { textContent: 1 },
            onUpdate() { el.textContent = String(Math.round(this.targets()[0].textContent)).padStart(final.length, '0'); }
          }
        );
      }
    });
  });
}

// ══════════════════════════════════════════════════════
// FEATURE 6 — GLASSMORPHISM MOUSE GLOW
// ══════════════════════════════════════════════════════
document.querySelectorAll('.glass-card').forEach(card => {
  card.addEventListener('mousemove', e => {
    const rect = card.getBoundingClientRect();
    const x = ((e.clientX - rect.left) / rect.width * 100).toFixed(1) + '%';
    const y = ((e.clientY - rect.top) / rect.height * 100).toFixed(1) + '%';
    card.style.setProperty('--mx', x);
    card.style.setProperty('--my', y);
  });
});

// ══════════════════════════════════════════════════════
// FEATURE 7 — KINETIC TYPOGRAPHY
// ══════════════════════════════════════════════════════
(function() {
  const words = document.querySelectorAll('.kinetic-word');
  if (!words.length) return;
  let current = 0;
  function nextWord() {
    const cur = words[current];
    cur.classList.remove('active');
    cur.classList.add('leaving');
    setTimeout(() => cur.classList.remove('leaving'), 500);
    current = (current + 1) % words.length;
    words[current].classList.add('active');
  }
  setInterval(nextWord, 2200);
})();

// ══════════════════════════════════════════════════════
// FEATURE 11 — APPLE SCROLL STORY (GSAP ScrollTrigger)
// ══════════════════════════════════════════════════════
(function() {
  if (typeof gsap === 'undefined' || typeof ScrollTrigger === 'undefined') return;

  const outer  = document.getElementById('storyOuter');
  const sticky = document.getElementById('storySticky');
  if (!outer || !sticky) return;

  const scenes = [
    {
      id: 'scene1',
      blob: '#sb1', blobOpacity: 0.9,
      elems: ['s1ey','s1h','s1b'],
      bg: 'radial-gradient(ellipse 60% 60% at 20% 40%, rgba(212,175,55,0.06), transparent 70%)',
    },
    {
      id: 'scene2',
      blob: '#sb3', blobOpacity: 0.8,
      elems: ['s2ey','s2h','s2b','s2stats'],
      bg: 'radial-gradient(ellipse 70% 50% at 80% 60%, rgba(99,102,241,0.06), transparent 70%)',
    },
    {
      id: 'scene3',
      blob: '#sb4', blobOpacity: 0.7,
      elems: ['s3ey','s3h','s3b'],
      bg: 'radial-gradient(ellipse 60% 60% at 50% 30%, rgba(239,68,68,0.05), transparent 70%)',
    },
    {
      id: 'scene4',
      blob: '#sb2', blobOpacity: 0.8,
      elems: ['s4ey','s4h','s4b','s4cta'],
      bg: 'radial-gradient(ellipse 70% 70% at 50% 50%, rgba(16,185,129,0.06), transparent 70%)',
    }
  ];

  const dots = document.querySelectorAll('.story-dot');
  const scrollHint = document.getElementById('storyScrollHint');
  const allBlobs = ['#sb1','#sb2','#sb3','#sb4'];
  let activeScene = -1;

  function activateScene(idx) {
    if (activeScene === idx) return;
    const prev = activeScene;
    activeScene = idx;

    // Update dots
    dots.forEach((d,i) => d.classList.toggle('active', i === idx));

    // Hide all scenes
    scenes.forEach((s, i) => {
      const el = document.getElementById(s.id);
      if (!el) return;
      if (i !== idx) {
        gsap.to(el, { opacity: 0, duration: 0.35, ease: 'power2.in', onComplete: () => { el.classList.remove('active'); } });
      }
    });

    // Hide all blobs
    allBlobs.forEach(b => gsap.to(b, { opacity: 0, duration: 0.5 }));

    // Show current scene
    const sc = scenes[idx];
    const scEl = document.getElementById(sc.id);
    scEl.classList.add('active');

    // Animate background blob
    gsap.to(sc.blob, { opacity: sc.blobOpacity, duration: 1.2, ease: 'power2.out' });

    // Stagger in scene elements
    const elems = sc.elems.map(id => document.getElementById(id)).filter(Boolean);
    gsap.fromTo(scEl, { opacity: 0 }, { opacity: 1, duration: 0.5, ease: 'power2.out' });
    gsap.fromTo(elems,
      { y: 50, opacity: 0 },
      { y: 0, opacity: 1, duration: 0.9, ease: 'power3.out', stagger: 0.12, delay: 0.1 }
    );

    // Hide scroll hint after first scene
    if (scrollHint) gsap.to(scrollHint, { opacity: idx > 0 ? 0 : 1, duration: 0.4 });
  }

  // Build ScrollTrigger timeline
  const tl = gsap.timeline({
    scrollTrigger: {
      trigger: outer,
      start: 'top top',
      end: 'bottom bottom',
      scrub: false,
      onUpdate(self) {
        const progress = self.progress;
        const sceneIdx = Math.min(Math.floor(progress * scenes.length), scenes.length - 1);
        activateScene(sceneIdx);
      },
      pin: false,
    }
  });

  // Trigger first scene immediately when story enters viewport
  ScrollTrigger.create({
    trigger: outer,
    start: 'top 60%',
    once: true,
    onEnter: () => activateScene(0)
  });

})();

// ══════════════════════════════════════════════════════
// FEATURE 13 — MULTI-LAYER PARALLAX
// ══════════════════════════════════════════════════════
(function() {
  let scrollY = 0;
  window.addEventListener('scroll', () => { scrollY = window.scrollY; }, { passive: true });
  function updateParallax() {
    document.querySelectorAll('.parallax-deep').forEach(el => {
      el.style.transform = `translate(${scrollY*0.04}px, ${scrollY*0.06}px)`;
    });
    document.querySelectorAll('.parallax-mid').forEach(el => {
      el.style.transform = `translate(${-scrollY*0.02}px, ${scrollY*0.03}px)`;
    });
    document.querySelectorAll('.parallax-slow').forEach(el => {
      el.style.transform = `translateY(${scrollY*0.015}px)`;
    });
    requestAnimationFrame(updateParallax);
  }
  updateParallax();
})();

// ══════════════════════════════════════════════════════
// FEATURE 16 — LIVE SUPPORT TICKER
// ══════════════════════════════════════════════════════
(function() {
  const toast = document.getElementById('liveToast');
  const nameEl = document.getElementById('ltName');
  const cityEl = document.getElementById('ltCity');
  const avatarEl = document.getElementById('ltAvatar');
  if (!toast) return;

  const people = [
    {n:'Martin K.', c:'Žilina', a:'👨'},
    {n:'Jana M.', c:'Košice', a:'👩'},
    {n:'Peter S.', c:'Prešov', a:'🧑'},
    {n:'Lucia B.', c:'Banská Bystrica', a:'👩'},
    {n:'Tomáš N.', c:'Nitra', a:'👨'},
    {n:'Zuzana H.', c:'Trenčín', a:'👩'},
    {n:'Michal O.', c:'Trnava', a:'🧔'},
    {n:'Eva R.', c:'Poprad', a:'👩'},
    {n:'Rastislav F.', c:'Liptovský Mikuláš', a:'👨'},
    {n:'Katarína V.', c:'Bratislava', a:'👩'},
    {n:'Ondrej D.', c:'Piešťany', a:'🧑'},
    {n:'Monika T.', c:'Rožňava', a:'👩'},
  ];
  const actions = [
    'sa práve pridal/a k podpore',
    'zdieľal/a stránku',
    'podpísal/a petíciu',
    'sa zaregistroval/a ako dobrovoľník',
  ];

  let idx = Math.floor(Math.random() * people.length);

  function showNext() {
    const p = people[idx % people.length];
    const a = actions[Math.floor(Math.random() * actions.length)];
    idx++;
    nameEl.textContent = p.n;
    cityEl.textContent = p.c + ' ' + a;
    avatarEl.textContent = p.a;

    toast.classList.add('show');
    setTimeout(() => toast.classList.remove('show'), 3800);
  }

  // Start after 4 seconds, then every 7-12 seconds
  setTimeout(() => {
    showNext();
    setInterval(showNext, 7000 + Math.random() * 5000);
  }, 4000);
})();

// ─── CURSOR ───
const cursor = document.getElementById('cursor');
const ring = document.getElementById('cursorRing');
let mx = 0, my = 0, rx = 0, ry = 0;
document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
function animCursor() {
  rx += (mx - rx) * 0.12;
  ry += (my - ry) * 0.12;
  cursor.style.left = mx + 'px'; cursor.style.top  = my + 'px';
  ring.style.left   = rx + 'px'; ring.style.top    = ry + 'px';
  requestAnimationFrame(animCursor);
}
animCursor();
document.querySelectorAll('a, button, .mag-card, .fuz-star, .quiz-opt').forEach(el => {
  el.addEventListener('mouseenter', () => { cursor.classList.add('enlarged'); ring.classList.add('enlarged'); });
  el.addEventListener('mouseleave', () => { cursor.classList.remove('enlarged'); ring.classList.remove('enlarged'); });
});

// ─── EYE TRACKING (follows real mouse) ───
const pupilL = document.getElementById('pupilL');
const pupilR = document.getElementById('pupilR');
const avatarBox = document.getElementById('avatarBox');
document.addEventListener('mousemove', e => {
  if (!pupilL || !avatarBox) return;
  const rect = avatarBox.getBoundingClientRect();
  const ax = rect.left + rect.width * 0.38;  // left eye center
  const ay = rect.top  + rect.height * 0.40;
  const bx = rect.left + rect.width * 0.62;  // right eye center
  const by = ay;

  function movePupil(el, ex, ey, limit) {
    const dx = e.clientX - ex, dy = e.clientY - ey;
    const dist = Math.sqrt(dx*dx + dy*dy);
    const ratio = Math.min(limit / Math.max(dist,1), 1);
    return { x: dx * ratio, y: dy * ratio };
  }
  const pL = movePupil(pupilL, ax, ay, 6);
  const pR = movePupil(pupilR, bx, by, 6);
  const baseLx = rect.width > 0 ? 115 : 115;
  const baseRx = 185;
  const baseY  = 152;
  pupilL.setAttribute('cx', baseLx + pL.x);
  pupilL.setAttribute('cy', baseY  + pL.y);
  pupilR.setAttribute('cx', baseRx + pR.x);
  pupilR.setAttribute('cy', baseY  + pR.y);
});

// Mustache wiggle on hover
const mustache = document.getElementById('mustacheGroup');
if (mustache) {
  avatarBox && avatarBox.addEventListener('mouseenter', () => {
    mustache.style.transition = 'transform .15s';
    let t = 0;
    const wg = setInterval(() => {
      t++;
      mustache.style.transform = `rotate(${Math.sin(t*0.8)*4}deg) translateX(${Math.sin(t*0.6)*3}px)`;
      if (t > 20) { clearInterval(wg); mustache.style.transform = ''; }
    }, 40);
  });
}

// ─── PARTICLE CANVAS ───
const canvas = document.getElementById('particleCanvas');
const ctx = canvas.getContext('2d');
let W, H, particles = [];
function resizeCanvas() { W = canvas.width = canvas.offsetWidth; H = canvas.height = canvas.offsetHeight; }
resizeCanvas(); window.addEventListener('resize', resizeCanvas);
class Particle {
  constructor() { this.reset(); }
  reset() {
    this.x = Math.random() * W; this.y = Math.random() * H;
    this.r = Math.random() * 1.5 + 0.3;
    this.vx = (Math.random() - 0.5) * 0.25; this.vy = (Math.random() - 0.5) * 0.25 - 0.1;
    this.alpha = Math.random() * 0.6 + 0.1;
  }
  update() { this.x += this.vx; this.y += this.vy; if (this.y < -5 || this.x < -5 || this.x > W + 5) this.reset(); }
  draw() { ctx.beginPath(); ctx.arc(this.x, this.y, this.r, 0, Math.PI*2); ctx.fillStyle = `rgba(212,175,55,${this.alpha})`; ctx.fill(); }
}
for (let i = 0; i < 80; i++) particles.push(new Particle());
function drawLines() {
  for (let i = 0; i < particles.length; i++)
    for (let j = i+1; j < particles.length; j++) {
      const dx = particles[i].x-particles[j].x, dy = particles[i].y-particles[j].y;
      const d = Math.sqrt(dx*dx+dy*dy);
      if (d < 100) { ctx.beginPath(); ctx.moveTo(particles[i].x,particles[i].y); ctx.lineTo(particles[j].x,particles[j].y); ctx.strokeStyle=`rgba(212,175,55,${0.08*(1-d/100)})`; ctx.lineWidth=0.5; ctx.stroke(); }
    }
}
function animParticles() { ctx.clearRect(0,0,W,H); particles.forEach(p=>{p.update();p.draw();}); drawLines(); requestAnimationFrame(animParticles); }
animParticles();

// ─── HERO PARALLAX ───
const heroParallax = document.getElementById('heroParallax');
document.querySelector('.hero').addEventListener('mousemove', e => {
  const rect = e.currentTarget.getBoundingClientRect();
  const dx = (e.clientX - rect.left - rect.width/2) / (rect.width/2);
  const dy = (e.clientY - rect.top - rect.height/2) / (rect.height/2);
  heroParallax.style.transform = `translate(${dx*10}px,${dy*6}px)`;
});
document.querySelector('.hero').addEventListener('mouseleave', () => {
  heroParallax.style.transition='transform .6s ease'; heroParallax.style.transform='translate(0,0)';
  setTimeout(()=>heroParallax.style.transition='',600);
});

// ─── TEXT SCRAMBLE ───
class TextScramble {
  constructor(el) { this.el=el; this.chars='!<>-_\\/[]{}—=+*^?#ABCDEFGHIJKLMNOPQRSTUVWXYZ'; this.update=this.update.bind(this); }
  setText(t) {
    const old=this.el.innerText, len=Math.max(old.length,t.length);
    const p=new Promise(r=>this.resolve=r); this.queue=[];
    for(let i=0;i<len;i++){const s=Math.floor(Math.random()*20),e=s+Math.floor(Math.random()*20);this.queue.push({from:old[i]||'',to:t[i]||'',start:s,end:e});}
    cancelAnimationFrame(this.frameReq); this.frame=0; this.update(); return p;
  }
  update() {
    let out='',done=0;
    for(let i=0;i<this.queue.length;i++){let{from,to,start,end,char}=this.queue[i];
      if(this.frame>=end){done++;out+=to;}
      else if(this.frame>=start){if(!char||Math.random()<0.28){char=this.chars[Math.floor(Math.random()*this.chars.length)];this.queue[i].char=char;}out+=`<span style="color:var(--gold);opacity:0.6">${char}</span>`;}
      else out+=from;}
    this.el.innerHTML=out;
    if(done===this.queue.length)this.resolve();
    else{this.frameReq=requestAnimationFrame(this.update);this.frame++;}
  }
}
setTimeout(()=>{
  const t=document.getElementById('heroTitle'); if(!t)return;
  const fx=new TextScramble(t);
  t.style.backgroundClip='unset'; t.style.webkitBackgroundClip='unset'; t.style.color='white';
  fx.setText('PhDr. Branislav Malík, CSc.').then(()=>{
    t.innerHTML='PhDr. Branislav<br>Malík, CSc.'; t.style.color=''; t.style.backgroundClip=''; t.style.webkitBackgroundClip='';
  });
},500);

// ─── MAGNETIC CARDS ───
document.querySelectorAll('.mag-card').forEach(card=>{
  card.addEventListener('mousemove',e=>{
    const r=card.getBoundingClientRect(), cx=r.left+r.width/2, cy=r.top+r.height/2;
    const dx=(e.clientX-cx)/(r.width/2), dy=(e.clientY-cy)/(r.height/2);
    card.style.transform=`perspective(800px) rotateX(${-dy*6}deg) rotateY(${dx*6}deg) translateZ(8px)`;
  });
  card.addEventListener('mouseleave',()=>card.style.transform='perspective(800px) rotateX(0) rotateY(0) translateZ(0)');
});

// ─── NAVBAR ───
const header = document.getElementById('header');
window.addEventListener('scroll',()=>header.classList.toggle('scrolled',window.scrollY>60));

// ─── FADE OBSERVER ───
const observer=new IntersectionObserver(entries=>{entries.forEach(e=>{if(e.isIntersecting){e.target.classList.add('show');observer.unobserve(e.target);}});},{rootMargin:'0px 0px -10% 0px'});
document.querySelectorAll('.fade').forEach(el=>observer.observe(el));


// ── COUNTDOWN ──
(function() {
  const target = new Date('2029-04-15T08:00:00');
  function tick() {
    const diff = target - new Date();
    if (diff <= 0) return;
    const d = Math.floor(diff/86400000);
    const h = Math.floor((diff%86400000)/3600000);
    const m = Math.floor((diff%3600000)/60000);
    const s = Math.floor((diff%60000)/1000);
    const pad = (n,l=2) => String(n).padStart(l,'0');
    const dEl=document.getElementById('cdDays'), hEl=document.getElementById('cdHours');
    const mEl=document.getElementById('cdMins'),  sEl=document.getElementById('cdSecs');
    if(dEl) dEl.textContent=pad(d,3);
    if(hEl) hEl.textContent=pad(h);
    if(mEl) mEl.textContent=pad(m);
    if(sEl){ const ns=pad(s); if(sEl.textContent!==ns){sEl.textContent=ns; sEl.style.transform='scale(1.15)'; setTimeout(()=>sEl.style.transform='',120);} }
  }
  tick(); setInterval(tick,1000);
})();

// ── MAP ──
(function() {
  const regions = document.querySelectorAll('.sk-region');
  const tooltip = document.getElementById('mapTooltip');
  const barsEl  = document.getElementById('mapBars');
  if (!regions.length) return;
  const data=[{r:'Bratislavský',pct:87},{r:'Trnavský',pct:74},{r:'Trenčiansky',pct:68},{r:'Nitriansky',pct:71},{r:'Žilinský',pct:79},{r:'Banskobystrický',pct:65},{r:'Prešovský',pct:62},{r:'Košický',pct:69}];
  if(barsEl) barsEl.innerHTML=data.map(d=>`<div class="map-bar-row"><div class="map-bar-label">${d.r}<span>${d.pct}%</span></div><div class="map-bar-track"><div class="map-bar-fill" data-w="${d.pct}"></div></div></div>`).join('');
  const barObs=new IntersectionObserver(entries=>{if(entries[0].isIntersecting){document.querySelectorAll('.map-bar-fill').forEach((b,i)=>setTimeout(()=>b.style.width=b.dataset.w+'%',i*80));barObs.disconnect();}},{threshold:0.2});
  const ms=document.getElementById('mapa'); if(ms) barObs.observe(ms);
  regions.forEach(r=>{
    r.addEventListener('mouseenter',e=>{if(!tooltip)return; tooltip.innerHTML=`<strong>${r.dataset.region} kraj</strong>Podpora: ${r.dataset.pct}%`; tooltip.style.opacity='1';});
    r.addEventListener('mousemove',e=>{if(!tooltip)return; const rect=document.getElementById('slovakiaMap').getBoundingClientRect(); tooltip.style.left=(e.clientX-rect.left+14)+'px'; tooltip.style.top=(e.clientY-rect.top-10)+'px';});
    r.addEventListener('mouseleave',()=>{if(tooltip) tooltip.style.opacity='0';});
    r.addEventListener('click',()=>{regions.forEach(x=>x.classList.remove('active')); r.classList.add('active');});
  });
})();

// ── CONTACT ──
function submitForm() {
  const name=document.getElementById('fName')?.value.trim();
  const email=document.getElementById('fEmail')?.value.trim();
  if(!name||!email){
    const btn=document.querySelector('[onclick="submitForm()"]');
    btn.textContent='⚠️ Vyplňte meno a email'; btn.style.background='rgba(239,68,68,0.8)';
    setTimeout(()=>{btn.textContent='Odoslať správu →';btn.style.background='';},2000); return;
  }
  const success=document.getElementById('formSuccess');
  if(success) success.style.display='block';
  const btn=document.querySelector('[onclick="submitForm()"]');
  btn.textContent='✅ Odoslané!'; btn.style.background='linear-gradient(90deg,#22c55e,#4ade80)';
  setTimeout(()=>{btn.textContent='Odoslať správu →'; btn.style.background='';
    ['fName','fEmail','fMsg'].forEach(id=>{const el=document.getElementById(id);if(el)el.value='';});
    setTimeout(()=>{if(success)success.style.display='none';},3000);},2500);
}

let votes = 312847;
function updateUI() {
  document.getElementById('voteCount').textContent = votes.toLocaleString('sk-SK');
  document.getElementById('heroCount').textContent = votes.toLocaleString('sk-SK');
  document.getElementById('progressFill').style.width = '70%';
}
updateUI();
new IntersectionObserver(entries=>{if(entries[0].isIntersecting){updateUI();}},{threshold:0.3}).observe(document.getElementById('progressFill').parentElement);

function addVote() {
  votes++; updateUI();
  launchConfetti('mustache');
  const btn = document.getElementById('voteBtn');
  if (!btn) return;
  btn.textContent = '🥸 Ďakujeme! Fúzy víťazia!';
  btn.style.background = 'linear-gradient(90deg,#22c55e,#4ade80)';
  setTimeout(()=>{ btn.innerHTML='🥸 Podporiť fúzy!'; btn.style.background=''; }, 2500);
}
</script>
</body>
</html>
