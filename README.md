<!DOCTYPE html>
<html lang="sk">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Naše Hospoda — Karloveská, Bratislava</title>

  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400;1,700&family=DM+Sans:wght@300;400;500&family=Libre+Baskerville:ital@1&display=swap" rel="stylesheet" />

  <style>
    :root {
      --cream: #f5f0e8;
      --warm-white: #faf7f2;
      --amber: #c8872a;
      --amber-light: #e8a84a;
      --dark: #1a1208;
      --dark-mid: #2d2010;
      --wood: #6b3e1c;
      --foam: #f0e8d0;
      --gold: #d4a843;
      --ink: #2c1e0a;
      --muted: #8a7560;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    html { scroll-behavior: smooth; }

    body {
      background: var(--cream);
      color: var(--ink);
      font-family: 'DM Sans', sans-serif;
      font-weight: 300;
      overflow-x: hidden;
    }

    /* ── NAV ─────────────────────────────────────── */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 20px 48px;
      background: transparent;
      transition: background 0.4s, backdrop-filter 0.4s;
    }
    nav.scrolled {
      background: rgba(26,18,8,0.92);
      backdrop-filter: blur(12px);
    }
    .nav-logo {
      font-family: 'Playfair Display', serif;
      font-size: 1.3rem;
      font-weight: 700;
      color: var(--cream);
      letter-spacing: 0.04em;
      text-decoration: none;
    }
    .nav-logo span { color: var(--amber-light); font-style: italic; }
    .nav-links {
      display: flex;
      gap: 36px;
      list-style: none;
    }
    .nav-links a {
      color: rgba(245,240,232,0.75);
      text-decoration: none;
      font-size: 0.82rem;
      font-weight: 400;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      transition: color 0.2s;
    }
    .nav-links a:hover { color: var(--amber-light); }

    /* ── HERO ────────────────────────────────────── */
    .hero {
      position: relative;
      height: 100vh;
      min-height: 680px;
      display: flex;
      align-items: flex-end;
      justify-content: flex-start;
      overflow: hidden;
      background: var(--dark);
    }

    /* Atmospheric layered background */
    .hero-bg {
      position: absolute;
      inset: 0;
      background:
        radial-gradient(ellipse 60% 80% at 70% 40%, rgba(200,135,42,0.18) 0%, transparent 60%),
        radial-gradient(ellipse 40% 60% at 20% 70%, rgba(107,62,28,0.35) 0%, transparent 55%),
        linear-gradient(165deg, #1a1208 0%, #2d2010 40%, #1a1208 100%);
    }

    /* Beer bubbles SVG pattern overlay */
    .hero-texture {
      position: absolute;
      inset: 0;
      opacity: 0.035;
      background-image:
        radial-gradient(circle 1px at 15% 25%, #d4a843 1px, transparent 0),
        radial-gradient(circle 1.5px at 45% 55%, #d4a843 1px, transparent 0),
        radial-gradient(circle 1px at 75% 35%, #d4a843 1px, transparent 0),
        radial-gradient(circle 2px at 30% 75%, #d4a843 1px, transparent 0),
        radial-gradient(circle 1px at 60% 15%, #d4a843 1px, transparent 0),
        radial-gradient(circle 1.5px at 85% 65%, #d4a843 1px, transparent 0),
        radial-gradient(circle 1px at 10% 50%, #d4a843 1px, transparent 0),
        radial-gradient(circle 2px at 50% 85%, #d4a843 1px, transparent 0);
      background-size: 120px 120px;
    }

    /* Decorative hop garland line */
    .hero-line {
      position: absolute;
      top: 0;
      right: 0;
      width: 2px;
      height: 100%;
      background: linear-gradient(to bottom, transparent, var(--amber) 30%, var(--amber) 70%, transparent);
      opacity: 0.4;
    }
    .hero-line::after {
      content: '';
      position: absolute;
      top: 30%;
      left: 50%;
      transform: translateX(-50%);
      width: 12px;
      height: 40%;
      border-left: 1px solid var(--amber);
      border-right: 1px solid var(--amber);
      opacity: 0.3;
    }

    /* Big decorative beer glass silhouette */
    .hero-glass {
      position: absolute;
      right: 8%;
      top: 50%;
      transform: translateY(-50%);
      width: 260px;
      height: 340px;
      opacity: 0.07;
    }
    .glass-body {
      position: absolute;
      bottom: 0;
      left: 50%;
      transform: translateX(-50%);
      width: 130px;
      height: 260px;
      background: linear-gradient(to bottom, var(--amber-light) 0%, var(--amber) 100%);
      clip-path: polygon(10% 0%, 90% 0%, 100% 100%, 0% 100%);
      border-radius: 0 0 8px 8px;
    }
    .glass-foam {
      position: absolute;
      top: 0;
      left: 50%;
      transform: translateX(-50%);
      width: 145px;
      height: 70px;
      background: var(--foam);
      border-radius: 50% 50% 0 0;
      left: calc(50% - 72px);
    }
    .glass-handle {
      position: absolute;
      right: 42px;
      top: 110px;
      width: 45px;
      height: 90px;
      border: 14px solid var(--amber);
      border-radius: 0 30px 30px 0;
      border-left: none;
    }

    .hero-content {
      position: relative;
      z-index: 2;
      padding: 0 72px 80px;
      max-width: 650px;
    }

    .hero-eyebrow {
      display: inline-block;
      font-size: 0.72rem;
      letter-spacing: 0.28em;
      text-transform: uppercase;
      color: var(--amber-light);
      font-weight: 400;
      margin-bottom: 24px;
      opacity: 0;
      animation: fadeUp 0.7s 0.2s ease forwards;
    }

    .hero-title {
      font-family: 'Playfair Display', serif;
      font-size: clamp(3.2rem, 6vw, 5.5rem);
      line-height: 1.02;
      font-weight: 900;
      color: var(--cream);
      margin-bottom: 8px;
      opacity: 0;
      animation: fadeUp 0.7s 0.4s ease forwards;
    }
    .hero-title em {
      font-style: italic;
      color: var(--amber-light);
      display: block;
    }

    .hero-subtitle {
      font-family: 'Libre Baskerville', serif;
      font-style: italic;
      color: rgba(245,240,232,0.5);
      font-size: 1rem;
      margin-bottom: 40px;
      letter-spacing: 0.03em;
      opacity: 0;
      animation: fadeUp 0.7s 0.55s ease forwards;
    }

    .hero-tagline {
      font-size: 0.95rem;
      color: rgba(245,240,232,0.7);
      line-height: 1.7;
      max-width: 420px;
      margin-bottom: 48px;
      font-weight: 300;
      opacity: 0;
      animation: fadeUp 0.7s 0.7s ease forwards;
    }

    .hero-cta {
      display: flex;
      gap: 18px;
      flex-wrap: wrap;
      opacity: 0;
      animation: fadeUp 0.7s 0.85s ease forwards;
    }

    .btn-primary {
      display: inline-block;
      padding: 14px 36px;
      background: var(--amber);
      color: var(--dark);
      font-size: 0.78rem;
      font-weight: 500;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      text-decoration: none;
      border: 2px solid var(--amber);
      transition: background 0.25s, color 0.25s, transform 0.2s;
    }
    .btn-primary:hover {
      background: transparent;
      color: var(--amber-light);
      border-color: var(--amber-light);
      transform: translateY(-2px);
    }

    .btn-ghost {
      display: inline-block;
      padding: 14px 36px;
      background: transparent;
      color: rgba(245,240,232,0.75);
      font-size: 0.78rem;
      font-weight: 400;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      text-decoration: none;
      border: 1px solid rgba(245,240,232,0.25);
      transition: border-color 0.25s, color 0.25s, transform 0.2s;
    }
    .btn-ghost:hover {
      border-color: var(--amber-light);
      color: var(--amber-light);
      transform: translateY(-2px);
    }

    /* Scroll indicator */
    .scroll-hint {
      position: absolute;
      bottom: 32px;
      right: 72px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 8px;
      opacity: 0;
      animation: fadeUp 0.7s 1.1s ease forwards;
    }
    .scroll-hint span {
      font-size: 0.65rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--muted);
      writing-mode: vertical-rl;
    }
    .scroll-hint::after {
      content: '';
      width: 1px;
      height: 60px;
      background: linear-gradient(to bottom, var(--amber), transparent);
    }

    /* ── STRIP ───────────────────────────────────── */
    .strip {
      background: var(--amber);
      color: var(--dark);
      padding: 16px 48px;
      display: flex;
      gap: 48px;
      align-items: center;
      justify-content: center;
      flex-wrap: wrap;
      font-size: 0.72rem;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      font-weight: 500;
    }
    .strip-item {
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .strip-dot {
      width: 4px; height: 4px;
      background: var(--dark);
      border-radius: 50%;
      opacity: 0.4;
    }

    /* ── ABOUT ───────────────────────────────────── */
    .about {
      padding: 110px 72px;
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 80px;
      align-items: center;
      background: var(--warm-white);
      position: relative;
    }
    .about::before {
      content: '"';
      position: absolute;
      top: 40px;
      left: 60px;
      font-family: 'Playfair Display', serif;
      font-size: 18rem;
      color: rgba(200,135,42,0.06);
      line-height: 1;
      pointer-events: none;
    }

    .section-label {
      font-size: 0.68rem;
      letter-spacing: 0.3em;
      text-transform: uppercase;
      color: var(--amber);
      font-weight: 500;
      margin-bottom: 20px;
    }

    .section-title {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2rem, 3.5vw, 3rem);
      line-height: 1.15;
      color: var(--ink);
      margin-bottom: 28px;
    }
    .section-title em {
      font-style: italic;
      color: var(--amber);
    }

    .about-body p {
      color: var(--muted);
      line-height: 1.85;
      font-size: 0.95rem;
      margin-bottom: 18px;
    }

    .stat-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 2px;
      margin-top: 8px;
    }
    .stat {
      background: var(--dark);
      padding: 28px 24px;
      position: relative;
    }
    .stat:nth-child(even) { background: var(--dark-mid); }
    .stat-num {
      font-family: 'Playfair Display', serif;
      font-size: 2.8rem;
      font-weight: 900;
      color: var(--amber-light);
      line-height: 1;
      margin-bottom: 6px;
    }
    .stat-label {
      font-size: 0.7rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: rgba(245,240,232,0.45);
    }
    .stat-accent {
      position: absolute;
      top: 0; left: 0;
      width: 3px; height: 100%;
      background: var(--amber);
      opacity: 0;
      transition: opacity 0.3s;
    }
    .stat:hover .stat-accent { opacity: 1; }

    /* ── BEER ────────────────────────────────────── */
    .beer-section {
      background: var(--dark);
      padding: 100px 72px;
      position: relative;
      overflow: hidden;
    }
    .beer-section::after {
      content: '';
      position: absolute;
      bottom: 0; left: 0; right: 0;
      height: 3px;
      background: linear-gradient(90deg, transparent, var(--amber), transparent);
    }

    .beer-header {
      text-align: center;
      margin-bottom: 70px;
    }
    .beer-header .section-title {
      color: var(--cream);
    }
    .beer-header p {
      color: var(--muted);
      max-width: 500px;
      margin: 0 auto;
      font-size: 0.9rem;
      line-height: 1.75;
    }

    .beer-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 2px;
    }

    .beer-card {
      background: rgba(245,240,232,0.03);
      border: 1px solid rgba(245,240,232,0.06);
      padding: 44px 36px;
      position: relative;
      transition: background 0.3s;
      overflow: hidden;
      cursor: default;
    }
    .beer-card:hover {
      background: rgba(200,135,42,0.08);
    }
    .beer-card::before {
      content: '';
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 2px;
      background: linear-gradient(90deg, var(--amber), var(--amber-light));
      transform: scaleX(0);
      transform-origin: left;
      transition: transform 0.4s ease;
    }
    .beer-card:hover::before { transform: scaleX(1); }

    .beer-icon {
      font-size: 1.8rem;
      margin-bottom: 20px;
      display: block;
    }
    .beer-name {
      font-family: 'Playfair Display', serif;
      font-size: 1.3rem;
      font-weight: 700;
      color: var(--cream);
      margin-bottom: 10px;
    }
    .beer-style {
      font-size: 0.7rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--amber);
      margin-bottom: 16px;
      display: block;
    }
    .beer-desc {
      color: rgba(245,240,232,0.45);
      font-size: 0.88rem;
      line-height: 1.7;
    }
    .beer-abv {
      position: absolute;
      top: 44px;
      right: 36px;
      font-family: 'Playfair Display', serif;
      font-size: 1.4rem;
      font-weight: 700;
      color: rgba(212,168,67,0.25);
    }

    /* ── MENU ────────────────────────────────────── */
    .menu-section {
      padding: 110px 72px;
      background: var(--cream);
    }

    .menu-header {
      display: flex;
      align-items: flex-end;
      justify-content: space-between;
      margin-bottom: 64px;
      flex-wrap: wrap;
      gap: 24px;
    }

    .menu-tabs {
      display: flex;
      gap: 0;
      border-bottom: 1px solid rgba(107,62,28,0.2);
      flex-wrap: wrap;
    }
    .tab {
      padding: 10px 28px 14px;
      font-size: 0.75rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--muted);
      cursor: pointer;
      border-bottom: 2px solid transparent;
      margin-bottom: -1px;
      transition: color 0.2s, border-color 0.2s;
      user-select: none;
      font-weight: 400;
    }
    .tab:hover { color: var(--amber); }
    .tab.active {
      color: var(--amber);
      border-bottom-color: var(--amber);
      font-weight: 500;
    }

    .menu-panel { display: none; }
    .menu-panel.active { display: block; }

    .menu-list {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 2px;
    }

    .menu-item {
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
      padding: 20px 24px;
      background: var(--warm-white);
      gap: 24px;
      transition: background 0.2s;
      border-left: 2px solid transparent;
      transition: all 0.2s;
    }
    .menu-item:hover {
      background: #f0ead8;
      border-left-color: var(--amber);
    }
    .menu-item-info { flex: 1; }
    .menu-item-name {
      font-family: 'Playfair Display', serif;
      font-size: 1rem;
      font-weight: 400;
      color: var(--ink);
      margin-bottom: 5px;
    }
    .menu-item-desc {
      font-size: 0.8rem;
      color: var(--muted);
      line-height: 1.55;
    }
    .menu-item-price {
      font-family: 'Playfair Display', serif;
      font-size: 1.05rem;
      color: var(--amber);
      font-weight: 700;
      white-space: nowrap;
    }

    /* ── GALLERY ─────────────────────────────────── */
    .gallery-section {
      background: var(--dark-mid);
      padding: 100px 0;
      text-align: center;
    }
    .gallery-section .section-title { color: var(--cream); margin-bottom: 60px; }
    .gallery-section .section-label { color: var(--amber); }

    .gallery-grid {
      display: grid;
      grid-template-columns: 2fr 1fr 1fr;
      grid-template-rows: 220px 220px;
      gap: 4px;
      padding: 0 4px;
    }
    .gallery-cell {
      background: rgba(245,240,232,0.05);
      overflow: hidden;
      position: relative;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .gallery-cell.tall { grid-row: span 2; }

    /* Illustrated scene stand-ins */
    .scene {
      width: 100%;
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 4rem;
      position: relative;
    }
    .scene-1 { background: linear-gradient(135deg, #2d2010, #1a1208); }
    .scene-2 { background: linear-gradient(135deg, #3a2615, #2d1e0a); }
    .scene-3 { background: linear-gradient(135deg, #1f1508, #2d2010); }
    .scene-4 { background: linear-gradient(135deg, #2a1c0e, #1a1208); }
    .scene-5 { background: linear-gradient(135deg, #351e0a, #2d2010); }

    .scene-label {
      position: absolute;
      bottom: 16px; left: 16px;
      font-size: 0.68rem;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: rgba(245,240,232,0.45);
    }

    /* ── INFO ────────────────────────────────────── */
    .info-section {
      background: var(--dark);
      padding: 100px 72px;
      display: grid;
      grid-template-columns: 1.2fr 1fr;
      gap: 80px;
      position: relative;
    }
    .info-section::before {
      content: '';
      position: absolute;
      top: 0; left: 72px; right: 72px;
      height: 1px;
      background: linear-gradient(90deg, transparent, rgba(212,168,67,0.3), transparent);
    }

    .info-block .section-label { color: var(--amber); }
    .info-block .section-title { color: var(--cream); font-size: 2rem; }

    .hours-list {
      list-style: none;
      margin-top: 28px;
    }
    .hours-list li {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 14px 0;
      border-bottom: 1px solid rgba(245,240,232,0.06);
      font-size: 0.9rem;
    }
    .hours-list .day { color: rgba(245,240,232,0.5); }
    .hours-list .time { color: var(--cream); }
    .hours-list .closed { color: var(--muted); }
    .hours-list li.today .day { color: var(--amber-light); }
    .hours-list li.today .time { color: var(--amber-light); font-weight: 500; }

    .contact-info {
      margin-top: 36px;
    }
    .contact-item {
      display: flex;
      gap: 18px;
      align-items: flex-start;
      margin-bottom: 24px;
    }
    .contact-icon {
      width: 40px;
      height: 40px;
      border: 1px solid rgba(212,168,67,0.3);
      display: flex;
      align-items: center;
      justify-content: center;
      flex-shrink: 0;
      font-size: 1rem;
    }
    .contact-text {
      color: rgba(245,240,232,0.6);
      font-size: 0.9rem;
      line-height: 1.6;
    }
    .contact-text a {
      color: rgba(245,240,232,0.6);
      text-decoration: none;
      transition: color 0.2s;
    }
    .contact-text a:hover { color: var(--amber-light); }

    .map-placeholder {
      background: rgba(255,255,255,0.03);
      border: 1px solid rgba(212,168,67,0.15);
      height: 240px;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      gap: 12px;
      margin-top: 28px;
      cursor: pointer;
      transition: background 0.3s;
      text-decoration: none;
    }
    .map-placeholder:hover { background: rgba(200,135,42,0.08); }
    .map-placeholder .pin { font-size: 2rem; }
    .map-placeholder span {
      font-size: 0.72rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--amber);
    }

    /* ── FOOTER ─────────────────────────────────── */
    footer {
      background: #0f0a04;
      padding: 48px 72px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 24px;
      border-top: 1px solid rgba(212,168,67,0.1);
    }
    .footer-logo {
      font-family: 'Playfair Display', serif;
      font-size: 1.4rem;
      font-weight: 700;
      color: var(--cream);
      letter-spacing: 0.04em;
    }
    .footer-logo span { color: var(--amber); }
    .footer-copy {
      font-size: 0.75rem;
      color: var(--muted);
      letter-spacing: 0.08em;
    }
    .footer-staropramen {
      font-size: 0.7rem;
      color: rgba(138,117,96,0.55);
      letter-spacing: 0.1em;
    }

    /* ── DIVIDER ORNAMENT ────────────────────────── */
    .ornament {
      text-align: center;
      padding: 0;
      color: var(--amber);
      font-size: 1.2rem;
      opacity: 0.4;
      letter-spacing: 0.6em;
      line-height: 1;
    }

    /* ── ANIMATIONS ──────────────────────────────── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(22px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    .reveal {
      opacity: 0;
      transform: translateY(28px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }
    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }
    .reveal-delay-1 { transition-delay: 0.1s; }
    .reveal-delay-2 { transition-delay: 0.22s; }
    .reveal-delay-3 { transition-delay: 0.34s; }
    .reveal-delay-4 { transition-delay: 0.46s; }

    /* ── RESPONSIVE ──────────────────────────────── */
    @media (max-width: 900px) {
      nav { padding: 16px 24px; }
      .nav-links { gap: 20px; }
      .hero-content { padding: 0 28px 64px; }
      .about { grid-template-columns: 1fr; padding: 72px 28px; gap: 48px; }
      .beer-section { padding: 72px 28px; }
      .beer-grid { grid-template-columns: 1fr; gap: 2px; }
      .menu-section { padding: 72px 28px; }
      .menu-list { grid-template-columns: 1fr; }
      .gallery-grid { grid-template-columns: 1fr 1fr; grid-template-rows: 160px 160px 160px; }
      .gallery-cell.tall { grid-row: span 1; }
      .info-section { grid-template-columns: 1fr; padding: 72px 28px; }
      footer { padding: 36px 28px; }
      .menu-header { flex-direction: column; align-items: flex-start; }
    }
    @media (max-width: 600px) {
      .nav-links { display: none; }
      .hero-title { font-size: 2.6rem; }
      .hero-glass { display: none; }
      .strip { padding: 14px 24px; gap: 20px; font-size: 0.65rem; }
      .beer-grid { grid-template-columns: 1fr; }
      .gallery-grid { grid-template-columns: 1fr; }
      .gallery-cell.tall { grid-row: span 1; }
    }
  </style>
</head>
<body>

  <!-- NAV -->
  <nav id="navbar">
    <a class="nav-logo" href="#">Naše <span>Hospoda</span></a>
    <ul class="nav-links">
      <li><a href="#o-nas">O nás</a></li>
      <li><a href="#pivo">Pivo</a></li>
      <li><a href="#jedlo">Jedlo</a></li>
      <li><a href="#kontakt">Kontakt</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <section class="hero">
    <div class="hero-bg"></div>
    <div class="hero-texture"></div>
    <div class="hero-line"></div>
    <div class="hero-glass">
      <div class="glass-foam"></div>
      <div class="glass-body"></div>
      <div class="glass-handle"></div>
    </div>

    <div class="hero-content">
      <span class="hero-eyebrow">Karloveská · Bratislava</span>
      <h1 class="hero-title">
        Naše<br><em>Hospoda</em>
      </h1>
      <p class="hero-subtitle">Pivárska tradícia. Moderný duch.</p>
      <p class="hero-tagline">Moderný gastronomický koncept pod pivnou vlajkou Staropramen. Čerstvé pivo z tanku, domáca kuchyňa a priateľská obsluha — všetko na jednom mieste v Karlovej Vsi.</p>
      <div class="hero-cta">
        <a href="#jedlo" class="btn-primary">Pozri jedálny lístok</a>
        <a href="#kontakt" class="btn-ghost">Nájdi nás</a>
      </div>
    </div>

    <div class="scroll-hint">
      <span>Scrolluj</span>
    </div>
  </section>

  <!-- INFO STRIP -->
  <div class="strip">
    <div class="strip-item">🍺 Staropramen z tanku</div>
    <div class="strip-dot"></div>
    <div class="strip-item">🍔 Domáca kuchyňa</div>
    <div class="strip-dot"></div>
    <div class="strip-item">📍 Segnerova 3/A, Bratislava</div>
    <div class="strip-dot"></div>
    <div class="strip-item">⏰ Po–Ne 11:00 – 22:00</div>
  </div>

  <!-- ABOUT -->
  <section class="about" id="o-nas">
    <div class="about-body">
      <div class="section-label reveal">O nás</div>
      <h2 class="section-title reveal reveal-delay-1">Hospoda s <em>charakterom</em></h2>
      <p class="reveal reveal-delay-2">Naše Hospoda Karloveská je miestom, kde sa stretáva autentická hospodská atmosféra s moderným gastronomickým konceptom. Sme súčasťou rodinky Staropramen — pivovaru s takmer 160-ročnou históriou.</p>
      <p class="reveal reveal-delay-3">Ponúkame nepasterizované pivo priamo z chladiaceho tanku, domácky varené jedlá plné chutí a obsluhu, ktorá sa o vás postará tak, ako má. Jednoducho: naša hospoda, vaša pohoda.</p>
    </div>

    <div class="stat-grid reveal reveal-delay-2">
      <div class="stat">
        <div class="stat-accent"></div>
        <div class="stat-num">4.6</div>
        <div class="stat-label">Google hodnotenie</div>
      </div>
      <div class="stat">
        <div class="stat-accent"></div>
        <div class="stat-num">500+</div>
        <div class="stat-label">Recenzií</div>
      </div>
      <div class="stat">
        <div class="stat-accent"></div>
        <div class="stat-num">5</div>
        <div class="stat-label">Druhov piva z tanku</div>
      </div>
      <div class="stat">
        <div class="stat-accent"></div>
        <div class="stat-num">€10</div>
        <div class="stat-label">Od za denné menu</div>
      </div>
    </div>
  </section>

  <!-- BEER -->
  <section class="beer-section" id="pivo">
    <div class="beer-header reveal">
      <div class="section-label" style="color: var(--amber); margin-bottom: 16px;">Pivo</div>
      <h2 class="section-title" style="color: var(--cream); font-size: 2.6rem;">Naše <em style="color: var(--amber-light);">pivné špeciály</em></h2>
      <p style="color: var(--muted); margin-top: 16px; line-height: 1.75; font-size: 0.9rem;">Čerstvé, nepasterizované pivo priamo z nerezového tanku. Tak, ako to má byť.</p>
    </div>

    <div class="beer-grid">
      <div class="beer-card reveal reveal-delay-1">
        <div class="beer-abv">10°</div>
        <span class="beer-icon">🍺</span>
        <div class="beer-name">Staropramen Svetlý</div>
        <span class="beer-style">Nepasterizovaný · Czech Lager</span>
        <p class="beer-desc">Klasický svetlý ležiak s jemnou chmeľovou horkosťou. Čerstvý priamo z tanku — nedostanete ho kdekoľvek.</p>
      </div>
      <div class="beer-card reveal reveal-delay-2">
        <div class="beer-abv">12°</div>
        <span class="beer-icon">🌾</span>
        <div class="beer-name">Nefiltrovaný 12</div>
        <span class="beer-style">Weizen · Kvasnicové</span>
        <p class="beer-desc">Plné telo, kvasnicová vôňa, jemne zakalený. Hosťom odporúčaný obľúbenec — podávame v 2L súpravách.</p>
      </div>
      <div class="beer-card reveal reveal-delay-3">
        <div class="beer-abv">11°</div>
        <span class="beer-icon">⚫</span>
        <div class="beer-name">Černá Barbora</div>
        <span class="beer-style">Tmavý ležiak</span>
        <p class="beer-desc">Tmavý, zamatovo hladký ležiak s tónmi karamelu a pečeného sladu. Ideálny k pivárenským jedlám.</p>
      </div>
      <div class="beer-card reveal reveal-delay-1">
        <div class="beer-abv">12°</div>
        <span class="beer-icon">🌿</span>
        <div class="beer-name">Extrachmelená 12</div>
        <span class="beer-style">Špeciálny ležiak</span>
        <p class="beer-desc">Pre milovníkov intenzívnej chmeľovej vône a horkosti. Limitovaný špeciál pre skutočných pivových nadšencov.</p>
      </div>
      <div class="beer-card reveal reveal-delay-2">
        <div class="beer-abv">10°</div>
        <span class="beer-icon">✨</span>
        <div class="beer-name">Špecial zo Špiľky</div>
        <span class="beer-style">Špiľkové · Tradičné</span>
        <p class="beer-desc">Pivo točené tradičnou špiľkovou metódou. Jemné, kremovité čapovanie s hodvábnou penou.</p>
      </div>
      <div class="beer-card reveal reveal-delay-3">
        <div class="beer-abv">0%</div>
        <span class="beer-icon">🍋</span>
        <div class="beer-name">Staropramen Grep Radler</div>
        <span class="beer-style">Nealko · Citrus</span>
        <p class="beer-desc">Osviežujúci nealko radler s grapefruitom. Zadarmo pri objednávke nad 15€ — len tak, od nás.</p>
      </div>
    </div>
  </section>

  <!-- MENU -->
  <section class="menu-section" id="jedlo">
    <div class="menu-header">
      <div>
        <div class="section-label reveal">Jedálny lístok</div>
        <h2 class="section-title reveal reveal-delay-1">Skvelá domáca <em>kuchyňa</em></h2>
      </div>
      <div class="menu-tabs reveal">
        <div class="tab active" onclick="switchTab('burgers', this)">Burgre</div>
        <div class="tab" onclick="switchTab('mains', this)">Hlavné jedlá</div>
        <div class="tab" onclick="switchTab('salads', this)">Šaláty</div>
        <div class="tab" onclick="switchTab('pub', this)">K pivu</div>
      </div>
    </div>

    <div id="burgers" class="menu-panel active">
      <div class="menu-list">
        <div class="menu-item">
          <div class="menu-item-info">
            <div class="menu-item-name">Classic Burger</div>
            <div class="menu-item-desc">Mleté hovädzie mäso, cheddar, zelenina, domáca tatárska omáčka, BBQ, 150g zemiakové lupene</div>
          </div>
          <div class="menu-item-price">12.90€</div>
        </div>
        <div class="menu-item">
          <div class="menu-item-info">
            <div class="menu-item-name">Chilli Burger</div>
            <div class="menu-item-desc">Mleté hovädzie s chilli, cheddar, zelenina, sweet chilli, BBQ, cibuľové krúžky</div>
          </div>
          <div class="menu-item-price">12.90€</div>
        </div>
        <div class="menu-item">
          <div class="menu-item-info">
            <div class="menu-item-name">Chicken Bacon Burger</div>
            <div class="menu-item-desc">Kuracie prsia, cheddar, slanina, slaninová majonéza, kyslá uhorka, paradajka, BBQ, 150g hranolky</div>
          </div>
          <div class="menu-item-price">13.90€</div>
        </div>
        <div class="menu-item">
          <div class="menu-item-info">
            <div class="menu-item-name">Pulled Pork Burger</div>
            <div class="menu-item-desc">Trhané bravčové pečené 8 hodín, niva, karamelizovaná cibuľa, slanina, volské oko, BBQ majonéza</div>
          </div>
          <div class="menu-item-price">14.90€</div>
        </div>
      </div>
    </div>

    <div id="mains" class="menu-panel">
      <div class="menu-list">
        <div class="menu-item">
          <div class="menu-item-info">
            <div class="menu-item-name">Vyprážaný hermelín</div>
            <div class="menu-item-desc">Vyprážaný hermelín s hranolkami a tatárskou omáčkou</div>
          </div>
          <div class="menu-item-price">9.90€</div>
        </div>
        <div class="menu-item">
          <div class="menu-item-info">
            <div class="menu-item-name">Pečený pstruh</div>
            <div class="menu-item-desc">S tymiánom a citrónom, varené zemiaky, kôprový dresing</div>
          </div>
          <div class="menu-item-price">11.90€</div>
        </div>
        <div class="menu-item">
          <div class="menu-item-info">
            <div class="menu-item-name">Bravčová roláda</div>
            <div class="menu-item-desc">Plnená šunkou, syrom a olivami, prírodná omáčka, štuchané zemiaky</div>
          </div>
          <div class="menu-item-price">11.90€</div>
        </div>
        <div class="menu-item">
          <div class="menu-item-info">
            <div class="menu-item-name">Fusilli s kuracím mäsom</div>
            <div class="menu-item-desc">Nivová omáčka so šampiňónmi a kuraciou fileou</div>
          </div>
          <div class="menu-item-price">9.90€</div>
        </div>
      </div>
    </div>

    <div id="salads" class="menu-panel">
      <div class="menu-list">
        <div class="menu-item">
          <div class="menu-item-info">
            <div class="menu-item-name">Kurací šalát s parmezánom</div>
            <div class="menu-item-desc">Mix listových šalátov, mrkva, cherry paradajky, medovo-horčicový dresing, grilované kuracie kúsky</div>
          </div>
          <div class="menu-item-price">9.90€</div>
        </div>
        <div class="menu-item">
          <div class="menu-item-info">
            <div class="menu-item-name">Šalát s kozím syrom</div>
            <div class="menu-item-desc">Ľadový šalát, rukola, polníček, medovo-horčicový dresing, hrozno, orechy</div>
          </div>
          <div class="menu-item-price">10.90€</div>
        </div>
        <div class="menu-item">
          <div class="menu-item-info">
            <div class="menu-item-name">Fresh šalát s enciánom</div>
            <div class="menu-item-desc">Mix listových šalátov, sezónna zelenina, olivový olej, grilovaný enciány</div>
          </div>
          <div class="menu-item-price">9.90€</div>
        </div>
      </div>
    </div>

    <div id="pub" class="menu-panel">
      <div class="menu-list">
        <div class="menu-item">
          <div class="menu-item-info">
            <div class="menu-item-name">Držková polievka</div>
            <div class="menu-item-desc">Poctivá držková s chlebom, 0,40 l</div>
          </div>
          <div class="menu-item-price">4.90€</div>
        </div>
        <div class="menu-item">
          <div class="menu-item-info">
            <div class="menu-item-name">Hovädzí vývar</div>
            <div class="menu-item-desc">S rezancami a zeleninou, domáci vývar, 0,40 l</div>
          </div>
          <div class="menu-item-price">3.90€</div>
        </div>
        <div class="menu-item">
          <div class="menu-item-info">
            <div class="menu-item-name">Vyprážaný syrový krúžok</div>
            <div class="menu-item-desc">Výber syrov, domáca tatárska omáčka</div>
          </div>
          <div class="menu-item-price">7.90€</div>
        </div>
        <div class="menu-item">
          <div class="menu-item-info">
            <div class="menu-item-name">Pivársky tanier</div>
            <div class="menu-item-desc">Výber údenín, nakladaný syr, domáci chlieb, horčica</div>
          </div>
          <div class="menu-item-price">10.90€</div>
        </div>
      </div>
    </div>
  </section>

  <!-- VISUAL BREAK -->
  <section class="gallery-section">
    <div class="section-label" style="margin-bottom: 12px;" >Atmosféra</div>
    <h2 class="section-title">Vitajte <em style="color: var(--amber-light);">u nás</em></h2>

    <div class="gallery-grid">
      <div class="gallery-cell tall">
        <div class="scene scene-1">
          <div style="text-align:center;">
            <div style="font-size: 5rem;">🍺</div>
            <div style="font-family:'Playfair Display',serif; font-size:1.6rem; color: var(--amber-light); margin-top:12px;">Pivo z tanku</div>
            <div style="font-size:0.75rem; letter-spacing:0.15em; color: var(--muted); margin-top:8px; text-transform:uppercase;">Nepasterizované</div>
          </div>
        </div>
        <div class="scene-label">Výčap</div>
      </div>
      <div class="gallery-cell">
        <div class="scene scene-2">🥩</div>
        <div class="scene-label">Gril</div>
      </div>
      <div class="gallery-cell">
        <div class="scene scene-3">🌿</div>
        <div class="scene-label">Záhrada</div>
      </div>
      <div class="gallery-cell">
        <div class="scene scene-4">🍔</div>
        <div class="scene-label">Burgre</div>
      </div>
      <div class="gallery-cell">
        <div class="scene scene-5">⚽</div>
        <div class="scene-label">Sport bar</div>
      </div>
    </div>
  </section>

  <!-- CONTACT / INFO -->
  <section class="info-section" id="kontakt">
    <div class="info-block">
      <div class="section-label reveal">Otváracie hodiny</div>
      <h2 class="section-title reveal reveal-delay-1">Kedy nás<br><em>nájdete</em></h2>

      <ul class="hours-list reveal reveal-delay-2">
        <li><span class="day">Pondelok</span><span class="time">11:00 – 22:00</span></li>
        <li><span class="day">Utorok</span><span class="time">11:00 – 22:00</span></li>
        <li><span class="day">Streda</span><span class="time">11:00 – 22:00</span></li>
        <li><span class="day">Štvrtok</span><span class="time">11:00 – 23:00</span></li>
        <li class="today"><span class="day">Piatok ★</span><span class="time">11:00 – 23:00</span></li>
        <li><span class="day">Sobota</span><span class="time">12:00 – 23:00</span></li>
        <li><span class="day">Nedeľa</span><span class="time">12:00 – 21:00</span></li>
      </ul>

      <p style="margin-top: 20px; font-size: 0.78rem; color: var(--muted); font-style: italic;">Denné menu podávame od 11:00 do 14:00, alebo do vypredania.</p>
    </div>

    <div class="info-block">
      <div class="section-label reveal">Kontakt</div>
      <h2 class="section-title reveal reveal-delay-1">Ako nás<br><em>kontaktovať</em></h2>

      <div class="contact-info reveal reveal-delay-2">
        <div class="contact-item">
          <div class="contact-icon">📍</div>
          <div class="contact-text">
            Segnerova 3/A<br>
            841 02 Bratislava – Karlova Ves<br>
            Slovenská republika
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">📞</div>
          <div class="contact-text">
            <a href="tel:+421220794094">+421 2 / 207 940 94</a>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">✉️</div>
          <div class="contact-text">
            <a href="mailto:info@nasehospoda-karloveska.sk">info@nasehospoda-karloveska.sk</a>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">🚗</div>
          <div class="contact-text">
            Dostupné električkou č. 4, 9, 12<br>
            Zastávka: Molecova
          </div>
        </div>
      </div>

      <a href="https://maps.app.goo.gl/pYxZV2Yf9r2RewLp6" target="_blank" class="map-placeholder reveal reveal-delay-3">
        <div class="pin">📍</div>
        <span>Zobraziť na mape</span>
      </a>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="footer-logo">Naše <span>Hospoda</span></div>
    <div class="footer-copy">© 2026 Naše Hospoda Karloveská · Bratislava</div>
    <div class="footer-staropramen">Powered by Staropramen ® · Pite zodpovedne</div>
  </footer>

  <script>
    // Nav scroll effect
    const navbar = document.getElementById('navbar');
    window.addEventListener('scroll', () => {
      navbar.classList.toggle('scrolled', window.scrollY > 60);
    });

    // Scroll reveal
    const reveals = document.querySelectorAll('.reveal');
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(e => {
        if (e.isIntersecting) {
          e.target.classList.add('visible');
          observer.unobserve(e.target);
        }
      });
    }, { threshold: 0.12 });
    reveals.forEach(el => observer.observe(el));

    // Menu tabs
    function switchTab(id, el) {
      document.querySelectorAll('.menu-panel').forEach(p => p.classList.remove('active'));
      document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
      document.getElementById(id).classList.add('active');
      el.classList.add('active');
    }
  </script>
</body>
</html>