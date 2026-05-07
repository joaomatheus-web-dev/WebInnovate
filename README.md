<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Web Innovate — Solução que gera resultados.</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
<style>
  :root {
    --violet: #7B5CF6;
    --violet-light: #A78BFA;
    --violet-dark: #5B3FD4;
    --blue: #3B82F6;
    --blue-light: #60A5FA;
    --blue-mid: #4F6EF7;
    --indigo: #6366F1;
    --gradient: linear-gradient(135deg, #7B5CF6 0%, #4F6EF7 50%, #3B82F6 100%);
    --gradient-soft: linear-gradient(135deg, #EDE9FE 0%, #DBEAFE 100%);
    --bg: #06060F;
    --bg2: #0D0D1F;
    --surface: #12122A;
    --surface2: #1A1A35;
    --text: #F0EEFF;
    --text-muted: #8884B8;
    --border: rgba(123,92,246,0.2);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--bg);
    color: var(--text);
    overflow-x: hidden;
  }

  /* ── NOISE OVERLAY ── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 1000;
    opacity: 0.5;
  }

  /* ── NAV ── */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 900;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 1.2rem 4rem;
    background: rgba(6,6,15,0.7);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
    transition: all 0.3s;
  }

  .nav-logo {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 1.4rem;
    background: var(--gradient);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    letter-spacing: -0.5px;
  }

  .nav-links { display: flex; gap: 2.5rem; list-style: none; }
  .nav-links a {
    color: var(--text-muted);
    text-decoration: none;
    font-size: 0.9rem;
    font-weight: 500;
    transition: color 0.3s;
    letter-spacing: 0.3px;
  }
  .nav-links a:hover { color: var(--violet-light); }

  .nav-cta {
    background: var(--gradient);
    color: #fff;
    border: none;
    padding: 0.65rem 1.6rem;
    border-radius: 50px;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.9rem;
    font-weight: 500;
    cursor: pointer;
    transition: opacity 0.3s, transform 0.3s;
  }
  .nav-cta:hover { opacity: 0.85; transform: translateY(-1px); }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    text-align: center;
    padding: 8rem 2rem 5rem;
    position: relative;
  }

  .hero-orb {
    position: absolute;
    border-radius: 50%;
    filter: blur(90px);
    pointer-events: none;
    animation: float 8s ease-in-out infinite;
  }
  .orb1 {
    width: 500px; height: 500px;
    background: radial-gradient(circle, rgba(123,92,246,0.35) 0%, transparent 70%);
    top: 5%; left: -10%;
    animation-delay: 0s;
  }
  .orb2 {
    width: 400px; height: 400px;
    background: radial-gradient(circle, rgba(59,130,246,0.3) 0%, transparent 70%);
    top: 20%; right: -5%;
    animation-delay: -3s;
  }
  .orb3 {
    width: 300px; height: 300px;
    background: radial-gradient(circle, rgba(99,102,241,0.25) 0%, transparent 70%);
    bottom: 10%; left: 30%;
    animation-delay: -5s;
  }

  @keyframes float {
    0%, 100% { transform: translateY(0) scale(1); }
    50% { transform: translateY(-30px) scale(1.05); }
  }

  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    background: rgba(123,92,246,0.15);
    border: 1px solid rgba(123,92,246,0.3);
    border-radius: 50px;
    padding: 0.4rem 1.1rem;
    font-size: 0.8rem;
    color: var(--violet-light);
    margin-bottom: 2rem;
    animation: fadeUp 0.8s 0.2s both;
  }

  .hero-badge::before {
    content: '';
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--violet-light);
    animation: pulse 2s infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(1.4); }
  }

  .hero h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(3rem, 7vw, 6rem);
    font-weight: 800;
    line-height: 1.05;
    letter-spacing: -2px;
    margin-bottom: 1.5rem;
    animation: fadeUp 0.8s 0.4s both;
  }

  .hero h1 .gradient-text {
    background: var(--gradient);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .hero p {
    font-size: 1.2rem;
    color: var(--text-muted);
    max-width: 550px;
    line-height: 1.7;
    margin-bottom: 2.5rem;
    font-weight: 300;
    animation: fadeUp 0.8s 0.6s both;
  }

  .hero-buttons {
    display: flex;
    gap: 1rem;
    animation: fadeUp 0.8s 0.8s both;
  }

  .btn-primary {
    background: var(--gradient);
    color: #fff;
    border: none;
    padding: 0.9rem 2.2rem;
    border-radius: 50px;
    font-family: 'DM Sans', sans-serif;
    font-size: 1rem;
    font-weight: 500;
    cursor: pointer;
    transition: transform 0.3s, box-shadow 0.3s;
    text-decoration: none;
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
  }
  .btn-primary:hover {
    transform: translateY(-3px);
    box-shadow: 0 20px 50px rgba(123,92,246,0.4);
  }

  .btn-ghost {
    background: transparent;
    color: var(--text);
    border: 1px solid var(--border);
    padding: 0.9rem 2.2rem;
    border-radius: 50px;
    font-family: 'DM Sans', sans-serif;
    font-size: 1rem;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.3s;
    text-decoration: none;
  }
  .btn-ghost:hover {
    border-color: var(--violet-light);
    color: var(--violet-light);
    transform: translateY(-3px);
  }

  /* ── STATS ── */
  .stats-bar {
    display: flex;
    justify-content: center;
    gap: 4rem;
    padding: 2rem;
    animation: fadeUp 0.8s 1s both;
  }

  .stat { text-align: center; }
  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 2rem;
    font-weight: 800;
    background: var(--gradient);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .stat-label {
    font-size: 0.8rem;
    color: var(--text-muted);
    margin-top: 0.2rem;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ── SECTION BASE ── */
  section { padding: 7rem 4rem; }

  .section-label {
    font-size: 0.8rem;
    font-weight: 600;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--violet-light);
    margin-bottom: 1rem;
  }

  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2rem, 4vw, 3rem);
    font-weight: 800;
    line-height: 1.1;
    letter-spacing: -1px;
    margin-bottom: 1.2rem;
  }

  .section-desc {
    color: var(--text-muted);
    font-size: 1.05rem;
    line-height: 1.7;
    max-width: 520px;
    font-weight: 300;
  }

  /* ── SERVICES ── */
  .services { background: var(--bg2); }

  .services-header {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    margin-bottom: 4rem;
    flex-wrap: wrap;
    gap: 2rem;
  }

  .services-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
  }

  .service-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 20px;
    padding: 2.2rem;
    transition: all 0.4s;
    position: relative;
    overflow: hidden;
  }
  .service-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: var(--gradient);
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.4s;
  }
  .service-card:hover::before { transform: scaleX(1); }
  .service-card:hover {
    background: var(--surface2);
    transform: translateY(-5px);
    border-color: rgba(123,92,246,0.4);
    box-shadow: 0 20px 50px rgba(123,92,246,0.15);
  }

  .service-icon {
    width: 50px; height: 50px;
    border-radius: 14px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 1.5rem;
    font-size: 1.4rem;
    background: rgba(123,92,246,0.15);
  }

  .service-card h3 {
    font-family: 'Syne', sans-serif;
    font-size: 1.15rem;
    font-weight: 700;
    margin-bottom: 0.8rem;
  }
  .service-card p {
    color: var(--text-muted);
    font-size: 0.9rem;
    line-height: 1.7;
  }

  /* ── PORTFOLIO / DEMOS ── */
  .portfolio { background: var(--bg); }

  .portfolio-header {
    text-align: center;
    margin-bottom: 4rem;
  }

  .demo-tabs {
    display: flex;
    justify-content: center;
    gap: 1rem;
    margin-bottom: 3rem;
    flex-wrap: wrap;
  }

  .demo-tab {
    background: var(--surface);
    border: 1px solid var(--border);
    color: var(--text-muted);
    padding: 0.6rem 1.5rem;
    border-radius: 50px;
    cursor: pointer;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.9rem;
    transition: all 0.3s;
  }
  .demo-tab.active, .demo-tab:hover {
    background: var(--gradient);
    border-color: transparent;
    color: #fff;
  }

  /* BROWSER MOCKUP */
  .browser-mockup {
    max-width: 1000px;
    margin: 0 auto;
    border-radius: 16px;
    overflow: hidden;
    border: 1px solid var(--border);
    box-shadow: 0 40px 100px rgba(0,0,0,0.6), 0 0 0 1px rgba(255,255,255,0.05);
    animation: fadeUp 0.5s ease both;
  }

  .browser-bar {
    background: var(--surface2);
    padding: 0.9rem 1.2rem;
    display: flex;
    align-items: center;
    gap: 1rem;
    border-bottom: 1px solid var(--border);
  }

  .browser-dots { display: flex; gap: 6px; }
  .browser-dots span {
    width: 12px; height: 12px;
    border-radius: 50%;
  }
  .dot-r { background: #FF5F57; }
  .dot-y { background: #FFBC2E; }
  .dot-g { background: #28C840; }

  .browser-url {
    flex: 1;
    background: rgba(255,255,255,0.06);
    border-radius: 8px;
    padding: 0.35rem 1rem;
    font-size: 0.8rem;
    color: var(--text-muted);
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }

  .browser-url::before {
    content: '🔒';
    font-size: 0.7rem;
  }

  .demo-content { display: none; }
  .demo-content.active { display: block; }

  /* ── DEMO 1: LOJA VIRTUAL ── */
  .demo-store {
    background: #FAFAFA;
    color: #1a1a1a;
    font-family: 'DM Sans', sans-serif;
    min-height: 500px;
  }

  .store-nav {
    background: #fff;
    padding: 1rem 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: 1px solid #eee;
    position: sticky;
    top: 0;
  }
  .store-logo { font-weight: 800; font-size: 1.2rem; color: #7B5CF6; }
  .store-nav-links { display: flex; gap: 1.5rem; font-size: 0.85rem; color: #555; }
  .store-cart {
    background: #7B5CF6;
    color: #fff;
    border: none;
    padding: 0.4rem 1rem;
    border-radius: 20px;
    font-size: 0.8rem;
    cursor: pointer;
  }

  .store-hero {
    background: linear-gradient(135deg, #7B5CF6, #3B82F6);
    color: white;
    padding: 3rem 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .store-hero-text h2 { font-size: 1.8rem; font-weight: 800; margin-bottom: 0.5rem; }
  .store-hero-text p { opacity: 0.85; font-size: 0.9rem; margin-bottom: 1rem; }
  .store-hero-btn {
    background: #fff;
    color: #7B5CF6;
    border: none;
    padding: 0.6rem 1.5rem;
    border-radius: 20px;
    font-weight: 600;
    cursor: pointer;
    font-size: 0.85rem;
  }
  .store-hero-img { font-size: 5rem; }

  .store-products { padding: 2rem; }
  .store-products h3 { font-weight: 700; margin-bottom: 1.5rem; color: #1a1a1a; }
  .products-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 1rem; }
  .product-card {
    background: #fff;
    border-radius: 12px;
    overflow: hidden;
    border: 1px solid #eee;
    transition: all 0.3s;
    cursor: pointer;
  }
  .product-card:hover { transform: translateY(-3px); box-shadow: 0 10px 30px rgba(0,0,0,0.1); }
  .product-img {
    height: 100px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2.5rem;
  }
  .product-info { padding: 0.75rem; }
  .product-name { font-size: 0.8rem; font-weight: 600; color: #1a1a1a; margin-bottom: 0.25rem; }
  .product-price { font-size: 0.85rem; font-weight: 700; color: #7B5CF6; }
  .product-add {
    width: 100%;
    background: #7B5CF6;
    color: #fff;
    border: none;
    padding: 0.4rem;
    font-size: 0.75rem;
    cursor: pointer;
    border-radius: 6px;
    margin-top: 0.5rem;
  }

  /* ── DEMO 2: RESTAURANTE ── */
  .demo-restaurant {
    background: #1C1008;
    color: #F5E6D0;
    font-family: 'DM Sans', sans-serif;
    min-height: 500px;
  }
  .rest-header {
    background: linear-gradient(180deg, #2A1810 0%, #1C1008 100%);
    padding: 2.5rem 2rem 1.5rem;
    text-align: center;
    border-bottom: 1px solid #3D2510;
  }
  .rest-logo { font-size: 1.8rem; font-weight: 800; color: #F59E0B; letter-spacing: -0.5px; }
  .rest-logo span { color: #EF4444; }
  .rest-tagline { font-size: 0.8rem; color: #B07D50; margin-top: 0.3rem; letter-spacing: 2px; text-transform: uppercase; }
  .rest-cats { display: flex; gap: 0.8rem; justify-content: center; padding: 1rem; overflow-x: auto; }
  .rest-cat {
    background: rgba(245,158,11,0.1);
    border: 1px solid rgba(245,158,11,0.3);
    color: #F59E0B;
    padding: 0.4rem 1rem;
    border-radius: 20px;
    font-size: 0.8rem;
    cursor: pointer;
    white-space: nowrap;
  }
  .rest-cat.active { background: #F59E0B; color: #1C1008; font-weight: 700; }

  .rest-menu { padding: 1.5rem; display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }
  .menu-item {
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,255,255,0.08);
    border-radius: 12px;
    padding: 1rem;
    display: flex;
    gap: 0.8rem;
    cursor: pointer;
    transition: all 0.3s;
  }
  .menu-item:hover { background: rgba(245,158,11,0.08); border-color: rgba(245,158,11,0.3); }
  .menu-emoji { font-size: 2.2rem; flex-shrink: 0; }
  .menu-info { flex: 1; }
  .menu-name { font-weight: 600; font-size: 0.9rem; color: #F5E6D0; }
  .menu-desc { font-size: 0.75rem; color: #B07D50; margin-top: 0.2rem; line-height: 1.4; }
  .menu-price { font-size: 0.95rem; font-weight: 700; color: #F59E0B; margin-top: 0.5rem; }
  .menu-add-btn {
    background: #F59E0B;
    color: #1C1008;
    border: none;
    width: 28px; height: 28px;
    border-radius: 50%;
    font-size: 1.1rem;
    cursor: pointer;
    flex-shrink: 0;
    align-self: flex-end;
    font-weight: 700;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  /* ── DEMO 3: DOUTOR ── */
  .demo-doctor {
    background: #F8FAFF;
    color: #1a2540;
    font-family: 'DM Sans', sans-serif;
    min-height: 500px;
  }
  .doc-header {
    background: linear-gradient(135deg, #1E3A8A 0%, #3B82F6 100%);
    padding: 1rem 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    color: white;
  }
  .doc-clinic { font-weight: 700; font-size: 1rem; }
  .doc-header-links { display: flex; gap: 1.5rem; font-size: 0.8rem; opacity: 0.85; }

  .doc-profile {
    padding: 2.5rem;
    display: flex;
    gap: 2rem;
    align-items: flex-start;
    background: #fff;
    border-bottom: 1px solid #E5EAF5;
  }
  .doc-avatar {
    width: 100px; height: 100px;
    border-radius: 50%;
    background: linear-gradient(135deg, #1E3A8A, #3B82F6);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 3rem;
    flex-shrink: 0;
    border: 4px solid #EFF6FF;
  }
  .doc-info { flex: 1; }
  .doc-name { font-size: 1.5rem; font-weight: 800; color: #1E3A8A; }
  .doc-specialty { color: #3B82F6; font-size: 0.9rem; font-weight: 600; margin-top: 0.25rem; }
  .doc-badges { display: flex; gap: 0.5rem; margin-top: 0.8rem; flex-wrap: wrap; }
  .doc-badge {
    background: #EFF6FF;
    color: #1E3A8A;
    font-size: 0.75rem;
    padding: 0.3rem 0.8rem;
    border-radius: 20px;
    font-weight: 500;
  }
  .doc-rating { display: flex; align-items: center; gap: 0.4rem; margin-top: 0.8rem; font-size: 0.85rem; color: #555; }
  .stars { color: #F59E0B; }
  .doc-cta {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    flex-shrink: 0;
  }
  .doc-btn-primary {
    background: #3B82F6;
    color: #fff;
    border: none;
    padding: 0.65rem 1.4rem;
    border-radius: 10px;
    cursor: pointer;
    font-weight: 600;
    font-size: 0.85rem;
    white-space: nowrap;
  }
  .doc-btn-ghost {
    background: #EFF6FF;
    color: #3B82F6;
    border: none;
    padding: 0.65rem 1.4rem;
    border-radius: 10px;
    cursor: pointer;
    font-weight: 600;
    font-size: 0.85rem;
  }

  .doc-body { display: grid; grid-template-columns: 1fr 1fr; padding: 1.5rem 2.5rem; gap: 2rem; }
  .doc-about h4, .doc-schedule h4 { font-size: 0.95rem; font-weight: 700; color: #1E3A8A; margin-bottom: 0.8rem; border-bottom: 2px solid #EFF6FF; padding-bottom: 0.5rem; }
  .doc-about p { font-size: 0.82rem; color: #555; line-height: 1.6; }
  .schedule-slot {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0.5rem 0;
    border-bottom: 1px solid #F0F4FF;
    font-size: 0.82rem;
  }
  .slot-day { color: #1E3A8A; font-weight: 600; }
  .slot-time { color: #555; }
  .slot-avail {
    background: #DCFCE7;
    color: #15803D;
    font-size: 0.7rem;
    padding: 0.2rem 0.5rem;
    border-radius: 10px;
    font-weight: 600;
  }
  .slot-busy {
    background: #FEE2E2;
    color: #DC2626;
    font-size: 0.7rem;
    padding: 0.2rem 0.5rem;
    border-radius: 10px;
    font-weight: 600;
  }

  /* ── PROCESS ── */
  .process { background: var(--bg2); }
  .process-header { text-align: center; margin-bottom: 4rem; }
  .process-steps {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 2rem;
    max-width: 1000px;
    margin: 0 auto;
    position: relative;
  }
  .process-steps::before {
    content: '';
    position: absolute;
    top: 28px;
    left: 15%;
    right: 15%;
    height: 1px;
    background: var(--gradient);
    opacity: 0.4;
  }

  .process-step { text-align: center; }
  .step-num {
    width: 56px; height: 56px;
    background: var(--surface);
    border: 2px solid var(--violet);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Syne', sans-serif;
    font-size: 1.1rem;
    font-weight: 800;
    background: var(--gradient);
    margin: 0 auto 1.2rem;
    color: #fff;
    box-shadow: 0 0 30px rgba(123,92,246,0.3);
  }
  .step-title {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    margin-bottom: 0.5rem;
  }
  .step-desc { font-size: 0.85rem; color: var(--text-muted); line-height: 1.6; }

  /* ── TESTIMONIALS ── */
  .testimonials { background: var(--bg); }
  .testimonials-header { text-align: center; margin-bottom: 3rem; }
  .testimonials-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
    max-width: 1100px;
    margin: 0 auto;
  }
  .testimonial-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 20px;
    padding: 2rem;
    transition: all 0.3s;
  }
  .testimonial-card:hover {
    border-color: rgba(123,92,246,0.4);
    transform: translateY(-4px);
  }
  .test-stars { color: #F59E0B; font-size: 0.9rem; margin-bottom: 1rem; }
  .test-text { font-size: 0.9rem; color: var(--text-muted); line-height: 1.7; margin-bottom: 1.5rem; font-style: italic; }
  .test-author { display: flex; align-items: center; gap: 0.8rem; }
  .test-avatar {
    width: 40px; height: 40px;
    border-radius: 50%;
    background: var(--gradient);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.2rem;
  }
  .test-name { font-weight: 600; font-size: 0.9rem; }
  .test-role { font-size: 0.75rem; color: var(--text-muted); }

  /* ── CTA ── */
  .cta-section {
    background: var(--bg);
    padding: 5rem 4rem;
    text-align: center;
  }
  .cta-card {
    background: var(--gradient);
    border-radius: 30px;
    padding: 5rem 3rem;
    max-width: 900px;
    margin: 0 auto;
    position: relative;
    overflow: hidden;
  }
  .cta-card::before {
    content: '';
    position: absolute;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: radial-gradient(circle at center, rgba(255,255,255,0.15), transparent 60%);
    pointer-events: none;
  }
  .cta-card h2 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2rem, 4vw, 3rem);
    font-weight: 800;
    color: #fff;
    margin-bottom: 1rem;
    line-height: 1.1;
    letter-spacing: -1px;
  }
  .cta-card p { color: rgba(255,255,255,0.8); font-size: 1.05rem; margin-bottom: 2rem; }
  .cta-buttons { display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap; }
  .btn-white {
    background: #fff;
    color: #7B5CF6;
    border: none;
    padding: 0.9rem 2.2rem;
    border-radius: 50px;
    font-family: 'DM Sans', sans-serif;
    font-size: 1rem;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.3s;
  }
  .btn-white:hover { transform: translateY(-3px); box-shadow: 0 15px 40px rgba(0,0,0,0.2); }
  .btn-outline-white {
    background: transparent;
    color: #fff;
    border: 2px solid rgba(255,255,255,0.5);
    padding: 0.9rem 2.2rem;
    border-radius: 50px;
    font-family: 'DM Sans', sans-serif;
    font-size: 1rem;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.3s;
  }
  .btn-outline-white:hover { border-color: #fff; background: rgba(255,255,255,0.1); }

  /* ── FOOTER ── */
  footer {
    background: var(--bg2);
    border-top: 1px solid var(--border);
    padding: 4rem 4rem 2rem;
  }
  .footer-grid {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: 3rem;
    margin-bottom: 3rem;
  }
  .footer-brand-desc { color: var(--text-muted); font-size: 0.9rem; margin-top: 0.8rem; line-height: 1.7; }
  .footer-social { display: flex; gap: 0.8rem; margin-top: 1.5rem; }
  .social-btn {
    width: 38px; height: 38px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1rem;
    cursor: pointer;
    transition: all 0.3s;
    text-decoration: none;
  }
  .social-btn:hover { background: var(--violet); border-color: var(--violet); }

  .footer-col h4 {
    font-family: 'Syne', sans-serif;
    font-size: 0.85rem;
    font-weight: 700;
    margin-bottom: 1.2rem;
    color: var(--text);
    letter-spacing: 0.5px;
  }
  .footer-col ul { list-style: none; }
  .footer-col li { margin-bottom: 0.7rem; }
  .footer-col a { color: var(--text-muted); text-decoration: none; font-size: 0.88rem; transition: color 0.3s; }
  .footer-col a:hover { color: var(--violet-light); }

  .footer-bottom {
    border-top: 1px solid var(--border);
    padding-top: 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: var(--text-muted);
    font-size: 0.82rem;
  }

  /* ── SCROLL REVEAL ── */
  .reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* ── SECURITY ── */
  .security { background: var(--bg2); }

  .security-header { margin-bottom: 4rem; }

  .security-layout {
    display: grid;
    grid-template-columns: 1fr 1.5fr;
    gap: 5rem;
    align-items: center;
    margin-bottom: 4rem;
  }

  /* Shield animation */
  .security-visual {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .shield-wrap {
    position: relative;
    width: 280px;
    height: 280px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .shield-ring {
    position: absolute;
    border-radius: 50%;
    border: 1px solid rgba(123,92,246,0.25);
    animation: spinRing 12s linear infinite;
  }
  .r1 { width: 100%; height: 100%; animation-duration: 20s; }
  .r2 { width: 73%; height: 73%; animation-duration: 14s; animation-direction: reverse; border-color: rgba(59,130,246,0.3); }
  .r3 { width: 46%; height: 46%; animation-duration: 9s; border-color: rgba(99,102,241,0.35); }

  @keyframes spinRing {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
  }

  .shield-core {
    position: relative;
    z-index: 2;
    background: var(--surface);
    border: 2px solid rgba(123,92,246,0.5);
    border-radius: 50%;
    width: 110px;
    height: 110px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 0.2rem;
    box-shadow: 0 0 50px rgba(123,92,246,0.25), 0 0 100px rgba(123,92,246,0.1);
  }

  .shield-icon { font-size: 2.2rem; }
  .shield-label { font-size: 0.65rem; font-weight: 700; color: var(--violet-light); letter-spacing: 1px; text-transform: uppercase; }

  .shield-dot {
    position: absolute;
    width: 36px;
    height: 36px;
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1rem;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) rotate(var(--a)) translateY(-130px) rotate(calc(-1 * var(--a)));
    box-shadow: 0 4px 15px rgba(0,0,0,0.3);
    animation: floatDot 4s ease-in-out infinite;
    animation-delay: calc(var(--a) / 60deg * 0.5s);
  }

  @keyframes floatDot {
    0%, 100% { box-shadow: 0 4px 15px rgba(0,0,0,0.3); }
    50% { box-shadow: 0 4px 20px rgba(123,92,246,0.4); border-color: rgba(123,92,246,0.5); }
  }

  /* Features list */
  .security-features {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
  }

  .sec-feature {
    display: flex;
    gap: 1rem;
    align-items: flex-start;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 1.3rem;
    transition: all 0.3s;
  }
  .sec-feature:hover {
    border-color: rgba(123,92,246,0.4);
    background: var(--surface2);
    transform: translateY(-3px);
    box-shadow: 0 10px 30px rgba(123,92,246,0.1);
  }

  .sec-feat-icon {
    font-size: 1.5rem;
    flex-shrink: 0;
    width: 42px;
    height: 42px;
    background: rgba(123,92,246,0.12);
    border-radius: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .sec-feature h4 {
    font-family: 'Syne', sans-serif;
    font-size: 0.88rem;
    font-weight: 700;
    margin-bottom: 0.35rem;
    color: var(--text);
  }
  .sec-feature p {
    font-size: 0.8rem;
    color: var(--text-muted);
    line-height: 1.6;
  }

  /* Badges bar */
  .security-badges {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 1rem;
    padding-top: 1rem;
    border-top: 1px solid var(--border);
  }

  .sec-badge {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 50px;
    padding: 0.5rem 1.2rem;
    font-size: 0.82rem;
    color: var(--text-muted);
    font-weight: 500;
    transition: all 0.3s;
  }
  .sec-badge:hover {
    border-color: rgba(123,92,246,0.5);
    color: var(--violet-light);
    background: rgba(123,92,246,0.08);
  }
  .sec-badge-icon { font-size: 0.85rem; }

  /* ── RESPONSIVE ── */
  @media (max-width: 900px) {
    nav { padding: 1rem 2rem; }
    .nav-links, .nav-cta { display: none; }
    section { padding: 5rem 1.5rem; }
    .services-grid { grid-template-columns: 1fr; }
    .process-steps { grid-template-columns: 1fr 1fr; }
    .process-steps::before { display: none; }
    .testimonials-grid { grid-template-columns: 1fr; }
    .security-layout { grid-template-columns: 1fr; }
    .shield-wrap { width: 200px; height: 200px; }
    .security-features { grid-template-columns: 1fr; }
    .footer-grid { grid-template-columns: 1fr 1fr; }
    .products-grid { grid-template-columns: 1fr 1fr; }
    .rest-menu { grid-template-columns: 1fr; }
    .doc-profile { flex-direction: column; }
    .doc-body { grid-template-columns: 1fr; }
    .stats-bar { gap: 2rem; flex-wrap: wrap; }
    .services-header { flex-direction: column; align-items: flex-start; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">WebInnovate</div>
  <ul class="nav-links">
    <li><a href="#servicos">Serviços</a></li>
    <li><a href="#portfolio">Portfólio</a></li>
    <li><a href="#seguranca">Segurança</a></li>
    <li><a href="#processo">Processo</a></li>
    <li><a href="#depoimentos">Depoimentos</a></li>
  </ul>
  <button class="nav-cta" onclick="document.querySelector('.cta-section').scrollIntoView({behavior:'smooth'})">Falar com especialista</button>
</nav>

<!-- HERO -->
<section class="hero" id="inicio">
  <div class="hero-orb orb1"></div>
  <div class="hero-orb orb2"></div>
  <div class="hero-orb orb3"></div>

  <div class="hero-badge">✦ Aplicações web de alta performance</div>

  <h1>
    Soluções digitais que<br>
    <span class="gradient-text">geram resultados.</span>
  </h1>

  <p>Criamos aplicações web modernas, rápidas e escaláveis para empresas que querem crescer no ambiente digital.</p>

  <div class="hero-buttons">
    <a href="#portfolio" class="btn-primary">Ver projetos ↓</a>
    <a href="#servicos" class="btn-ghost">Nossos serviços</a>
  </div>

  <div class="stats-bar">
    <div class="stat">
      <div class="stat-num">+150</div>
      <div class="stat-label">Projetos entregues</div>
    </div>
    <div class="stat">
      <div class="stat-num">98%</div>
      <div class="stat-label">Clientes satisfeitos</div>
    </div>
    <div class="stat">
      <div class="stat-num">8 anos</div>
      <div class="stat-label">De experiência</div>
    </div>
  </div>
</section>

<!-- SERVIÇOS -->
<section class="services" id="servicos">
  <div class="services-header reveal">
    <div>
      <div class="section-label">O que fazemos</div>
      <h2 class="section-title">Soluções completas<br>para o seu negócio</h2>
    </div>
    <p class="section-desc">Da ideia ao lançamento, cuidamos de cada etapa do desenvolvimento da sua aplicação web.</p>
  </div>

  <div class="services-grid">
    <div class="service-card reveal">
      <div class="service-icon">🎨</div>
      <h3>Design UI/UX</h3>
      <p>Interfaces bonitas e intuitivas que encantam os usuários e aumentam as conversões do seu negócio.</p>
    </div>
    <div class="service-card reveal" style="transition-delay:0.1s">
      <div class="service-icon">⚡</div>
      <h3>Desenvolvimento Web</h3>
      <p>Aplicações rápidas, responsivas e escaláveis com as tecnologias mais modernas do mercado.</p>
    </div>
    <div class="service-card reveal" style="transition-delay:0.2s">
      <div class="service-icon">🛒</div>
      <h3>E-commerce</h3>
      <p>Lojas virtuais completas, integradas com os principais meios de pagamento e ERP do mercado.</p>
    </div>
    <div class="service-card reveal" style="transition-delay:0.3s">
      <div class="service-icon">🔒</div>
      <h3>Segurança Digital</h3>
      <p>Proteção avançada para suas aplicações com criptografia, autenticação segura e monitoramento contínuo contra ameaças.</p>
    </div>
    <div class="service-card reveal" style="transition-delay:0.4s">
      <div class="service-icon">☁️</div>
      <h3>Cloud & Infraestrutura</h3>
      <p>Arquitetura em nuvem robusta e escalável para suportar o crescimento da sua operação.</p>
    </div>
    <div class="service-card reveal" style="transition-delay:0.5s">
      <div class="service-icon">📊</div>
      <h3>Analytics & SEO</h3>
      <p>Monitoramento de dados e otimização para que seu site seja encontrado por mais pessoas.</p>
    </div>
  </div>
</section>

<!-- PORTFÓLIO -->
<section class="portfolio" id="portfolio">
  <div class="portfolio-header reveal">
    <div class="section-label">Portfólio</div>
    <h2 class="section-title">Demonstrações reais<br>de projetos nossos</h2>
    <p style="color:var(--text-muted);margin-top:0.8rem;font-size:1rem;">Navegue pelos projetos abaixo e veja como transformamos ideias em experiências digitais.</p>
  </div>

  <div class="demo-tabs reveal">
    <button class="demo-tab active" onclick="switchDemo('store', this)">🛒 Loja Virtual</button>
    <button class="demo-tab" onclick="switchDemo('restaurant', this)">🍽️ Cardápio Digital</button>
    <button class="demo-tab" onclick="switchDemo('doctor', this)">🩺 Perfil Médico</button>
  </div>

  <div class="browser-mockup reveal">
    <div class="browser-bar">
      <div class="browser-dots">
        <span class="dot-r"></span>
        <span class="dot-y"></span>
        <span class="dot-g"></span>
      </div>
      <div class="browser-url" id="demo-url">webinnovate.com.br/demo/loja</div>
    </div>

    <!-- DEMO: LOJA -->
    <div class="demo-content active" id="demo-store">
      <div class="demo-store">
        <nav class="store-nav">
          <div class="store-logo">NOVA SHOP</div>
          <div class="store-nav-links">
            <span>Início</span><span>Produtos</span><span>Promoções</span>
          </div>
          <button class="store-cart">🛒 Carrinho (2)</button>
        </nav>
        <div class="store-hero">
          <div class="store-hero-text">
            <h2>Moda que<br>inspira você</h2>
            <p>Coleção verão 2025 com até 40% de desconto</p>
            <button class="store-hero-btn">Ver coleção →</button>
          </div>
          <div class="store-hero-img">👗</div>
        </div>
        <div class="store-products">
          <h3>Produtos em destaque</h3>
          <div class="products-grid">
            <div class="product-card">
              <div class="product-img" style="background:#FEF3C7">👟</div>
              <div class="product-info">
                <div class="product-name">Tênis Urban Pro</div>
                <div class="product-price">R$ 299,90</div>
                <button class="product-add">Adicionar ao carrinho</button>
              </div>
            </div>
            <div class="product-card">
              <div class="product-img" style="background:#EDE9FE">👗</div>
              <div class="product-info">
                <div class="product-name">Vestido Leve Rosa</div>
                <div class="product-price">R$ 189,90</div>
                <button class="product-add">Adicionar ao carrinho</button>
              </div>
            </div>
            <div class="product-card">
              <div class="product-img" style="background:#DCFCE7">🧢</div>
              <div class="product-info">
                <div class="product-name">Boné Street Style</div>
                <div class="product-price">R$ 79,90</div>
                <button class="product-add">Adicionar ao carrinho</button>
              </div>
            </div>
            <div class="product-card">
              <div class="product-img" style="background:#FEE2E2">👜</div>
              <div class="product-info">
                <div class="product-name">Bolsa Couro Italia</div>
                <div class="product-price">R$ 449,90</div>
                <button class="product-add">Adicionar ao carrinho</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- DEMO: RESTAURANTE -->
    <div class="demo-content" id="demo-restaurant">
      <div class="demo-restaurant">
        <div class="rest-header">
          <div class="rest-logo">Bella<span>Vista</span> 🍕</div>
          <div class="rest-tagline">Sabor italiano na sua mesa</div>
        </div>
        <div class="rest-cats">
          <div class="rest-cat active">🍕 Pizzas</div>
          <div class="rest-cat">🍝 Massas</div>
          <div class="rest-cat">🥗 Entradas</div>
          <div class="rest-cat">🍰 Sobremesas</div>
          <div class="rest-cat">🍷 Bebidas</div>
        </div>
        <div class="rest-menu">
          <div class="menu-item">
            <div class="menu-emoji">🍕</div>
            <div class="menu-info">
              <div class="menu-name">Margherita Clássica</div>
              <div class="menu-desc">Molho de tomate, mozzarella fresca e manjericão</div>
              <div class="menu-price">R$ 52,90</div>
            </div>
            <button class="menu-add-btn">+</button>
          </div>
          <div class="menu-item">
            <div class="menu-emoji">🍕</div>
            <div class="menu-info">
              <div class="menu-name">Quatro Queijos</div>
              <div class="menu-desc">Mozzarella, gorgonzola, parmesão e provolone</div>
              <div class="menu-price">R$ 64,90</div>
            </div>
            <button class="menu-add-btn">+</button>
          </div>
          <div class="menu-item">
            <div class="menu-emoji">🍕</div>
            <div class="menu-info">
              <div class="menu-name">Pepperoni Picante</div>
              <div class="menu-desc">Pepperoni importado, pimenta calabresa e orégano</div>
              <div class="menu-price">R$ 68,90</div>
            </div>
            <button class="menu-add-btn">+</button>
          </div>
          <div class="menu-item">
            <div class="menu-emoji">🍕</div>
            <div class="menu-info">
              <div class="menu-name">Portuguesa Premium</div>
              <div class="menu-desc">Presunto, ovo, cebola, azeitona e catupiry</div>
              <div class="menu-price">R$ 61,90</div>
            </div>
            <button class="menu-add-btn">+</button>
          </div>
        </div>
      </div>
    </div>

    <!-- DEMO: DOUTOR -->
    <div class="demo-content" id="demo-doctor">
      <div class="demo-doctor">
        <div class="doc-header">
          <div class="doc-clinic">🏥 ClínicaMed — Saúde & Bem-Estar</div>
          <div class="doc-header-links">
            <span>Especialistas</span>
            <span>Exames</span>
            <span>Contato</span>
          </div>
        </div>
        <div class="doc-profile">
          <div class="doc-avatar">👨‍⚕️</div>
          <div class="doc-info">
            <div class="doc-name">Dr. Ricardo Alves</div>
            <div class="doc-specialty">Cardiologista Intervencionista — CRM 123456/SP</div>
            <div class="doc-badges">
              <span class="doc-badge">❤️ Cardiologia</span>
              <span class="doc-badge">🎓 USP — Especialização</span>
              <span class="doc-badge">15+ anos</span>
            </div>
            <div class="doc-rating">
              <span class="stars">★★★★★</span> 4.9 (312 avaliações)
            </div>
          </div>
          <div class="doc-cta">
            <button class="doc-btn-primary">📅 Agendar consulta</button>
            <button class="doc-btn-ghost">💬 Mensagem</button>
          </div>
        </div>
        <div class="doc-body">
          <div class="doc-about">
            <h4>Sobre o Especialista</h4>
            <p>O Dr. Ricardo Alves possui mais de 15 anos de experiência em cardiologia clínica e intervencionista. Formado pela Universidade de São Paulo, com residência médica no Hospital das Clínicas e fellowship em hemodinâmica nos Estados Unidos.</p>
            <br>
            <p>Especialista em cateterismo cardíaco, angioplastia coronariana e implante de stents. Atua também na prevenção de doenças cardiovasculares e no tratamento da hipertensão arterial e insuficiência cardíaca.</p>
          </div>
          <div class="doc-schedule">
            <h4>Agenda da Semana</h4>
            <div class="schedule-slot">
              <span class="slot-day">Segunda-feira</span>
              <span class="slot-time">08h – 12h</span>
              <span class="slot-avail">Disponível</span>
            </div>
            <div class="schedule-slot">
              <span class="slot-day">Terça-feira</span>
              <span class="slot-time">14h – 18h</span>
              <span class="slot-avail">Disponível</span>
            </div>
            <div class="schedule-slot">
              <span class="slot-day">Quarta-feira</span>
              <span class="slot-time">08h – 17h</span>
              <span class="slot-busy">Lotado</span>
            </div>
            <div class="schedule-slot">
              <span class="slot-day">Quinta-feira</span>
              <span class="slot-time">14h – 18h</span>
              <span class="slot-avail">Disponível</span>
            </div>
            <div class="schedule-slot">
              <span class="slot-day">Sexta-feira</span>
              <span class="slot-time">08h – 12h</span>
              <span class="slot-avail">Disponível</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- SEGURANÇA -->
<section class="security" id="seguranca">
  <div class="security-header reveal">
    <div class="section-label">Segurança</div>
    <h2 class="section-title">Sua aplicação protegida<br><span class="gradient-text">em cada camada</span></h2>
    <p class="section-desc">Segurança não é um recurso opcional — é a base de tudo que construímos. Cada projeto entregue segue os mais altos padrões de proteção do mercado.</p>
  </div>

  <div class="security-layout reveal">
    <div class="security-visual">
      <div class="shield-wrap">
        <div class="shield-ring r1"></div>
        <div class="shield-ring r2"></div>
        <div class="shield-ring r3"></div>
        <div class="shield-core">
          <span class="shield-icon">🛡️</span>
          <span class="shield-label">Protegido</span>
        </div>
        <div class="shield-dot" style="--a:0deg">🔒</div>
        <div class="shield-dot" style="--a:60deg">🔐</div>
        <div class="shield-dot" style="--a:120deg">🛡️</div>
        <div class="shield-dot" style="--a:180deg">🔑</div>
        <div class="shield-dot" style="--a:240deg">🕵️</div>
        <div class="shield-dot" style="--a:300deg">✅</div>
      </div>
    </div>

    <div class="security-features">
      <div class="sec-feature">
        <div class="sec-feat-icon">🔒</div>
        <div>
          <h4>Criptografia de ponta a ponta</h4>
          <p>Todos os dados trafegam via HTTPS/TLS 1.3. Informações sensíveis armazenadas com AES-256, garantindo privacidade total.</p>
        </div>
      </div>
      <div class="sec-feature">
        <div class="sec-feat-icon">🛡️</div>
        <div>
          <h4>Proteção contra ataques (WAF)</h4>
          <p>Firewall de aplicação web que bloqueia SQL Injection, XSS, CSRF e outros vetores de ataque antes que cheguem ao servidor.</p>
        </div>
      </div>
      <div class="sec-feature">
        <div class="sec-feat-icon">🔐</div>
        <div>
          <h4>Autenticação Multifator</h4>
          <p>Implementamos OAuth 2.0, JWT e MFA para garantir que apenas usuários autorizados acessem sistemas críticos.</p>
        </div>
      </div>
      <div class="sec-feature">
        <div class="sec-feat-icon">🕵️</div>
        <div>
          <h4>Monitoramento 24/7</h4>
          <p>Alertas em tempo real, logs auditáveis e varredura contínua de vulnerabilidades com relatórios mensais de segurança.</p>
        </div>
      </div>
      <div class="sec-feature">
        <div class="sec-feat-icon">📋</div>
        <div>
          <h4>Conformidade LGPD</h4>
          <p>Todas as aplicações seguem a Lei Geral de Proteção de Dados, com gestão de consentimento e políticas de privacidade integradas.</p>
        </div>
      </div>
      <div class="sec-feature">
        <div class="sec-feat-icon">☁️</div>
        <div>
          <h4>Backups automatizados</h4>
          <p>Rotinas de backup diárias com retenção de 30 dias e planos de recuperação de desastres testados e documentados.</p>
        </div>
      </div>
    </div>
  </div>

  <div class="security-badges reveal">
    <div class="sec-badge"><span class="sec-badge-icon">✅</span><span>OWASP Top 10</span></div>
    <div class="sec-badge"><span class="sec-badge-icon">✅</span><span>LGPD Compliant</span></div>
    <div class="sec-badge"><span class="sec-badge-icon">✅</span><span>SSL/TLS 1.3</span></div>
    <div class="sec-badge"><span class="sec-badge-icon">✅</span><span>ISO 27001 Guidelines</span></div>
    <div class="sec-badge"><span class="sec-badge-icon">✅</span><span>Pentest anual</span></div>
  </div>
</section>

<!-- PROCESSO -->
<section class="process" id="processo">
  <div class="process-header reveal">
    <div class="section-label">Como trabalhamos</div>
    <h2 class="section-title">Do briefing ao lançamento</h2>
    <p style="color:var(--text-muted);margin-top:0.8rem;font-size:1rem;max-width:500px;margin-left:auto;margin-right:auto;">Nosso processo garante qualidade em cada etapa e entregas no prazo combinado.</p>
  </div>
  <div class="process-steps">
    <div class="process-step reveal">
      <div class="step-num">01</div>
      <div class="step-title">Descoberta</div>
      <div class="step-desc">Entendemos seu negócio, objetivos e público-alvo para criar a solução ideal.</div>
    </div>
    <div class="process-step reveal" style="transition-delay:0.15s">
      <div class="step-num">02</div>
      <div class="step-title">Design</div>
      <div class="step-desc">Criamos protótipos visuais e validamos a experiência antes de codar.</div>
    </div>
    <div class="process-step reveal" style="transition-delay:0.3s">
      <div class="step-num">03</div>
      <div class="step-title">Desenvolvimento</div>
      <div class="step-desc">Programação ágil com sprints semanais e entregas contínuas para revisão.</div>
    </div>
    <div class="process-step reveal" style="transition-delay:0.45s">
      <div class="step-num">04</div>
      <div class="step-title">Lançamento</div>
      <div class="step-desc">Deploy com suporte, monitoramento e treinamento da sua equipe.</div>
    </div>
  </div>
</section>

<!-- DEPOIMENTOS -->
<section class="testimonials" id="depoimentos">
  <div class="testimonials-header reveal">
    <div class="section-label">Depoimentos</div>
    <h2 class="section-title">O que nossos clientes dizem</h2>
  </div>
  <div class="testimonials-grid">
    <div class="testimonial-card reveal">
      <div class="test-stars">★★★★★</div>
      <div class="test-text">"A Web Innovate transformou completamente nosso e-commerce. As vendas cresceram 180% no primeiro trimestre após o lançamento. Equipe incrível!"</div>
      <div class="test-author">
        <div class="test-avatar">👩</div>
        <div>
          <div class="test-name">Ana Carvalho</div>
          <div class="test-role">CEO, Boutique Moderna</div>
        </div>
      </div>
    </div>
    <div class="testimonial-card reveal" style="transition-delay:0.1s">
      <div class="test-stars">★★★★★</div>
      <div class="test-text">"Profissionalismo e qualidade em cada detalhe. Nosso sistema de agendamento médico ficou exatamente como imaginávamos — rápido e simples."</div>
      <div class="test-author">
        <div class="test-avatar">👨‍⚕️</div>
        <div>
          <div class="test-name">Dr. Marcos Lima</div>
          <div class="test-role">Diretor, ClínicaMed</div>
        </div>
      </div>
    </div>
    <div class="testimonial-card reveal" style="transition-delay:0.2s">
      <div class="test-stars">★★★★★</div>
      <div class="test-text">"O cardápio digital deles revolucionou nosso atendimento. Pedidos online aumentaram 300% e os clientes adoram a experiência. Superou todas as expectativas!"</div>
      <div class="test-author">
        <div class="test-avatar">👨‍🍳</div>
        <div>
          <div class="test-name">Carlo Rizzo</div>
          <div class="test-role">Proprietário, BellaVista</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CTA -->
<div class="cta-section">
  <div class="cta-card reveal">
    <h2>Pronto para transformar<br>sua presença digital?</h2>
    <p>Fale com nossos especialistas e receba um orçamento gratuito em até 24 horas.</p>
    <div class="cta-buttons">
      <button class="btn-white">Solicitar orçamento grátis</button>
      <button class="btn-outline-white">Ver mais projetos</button>
    </div>
  </div>
</div>

<!-- FOOTER -->
<footer>
  <div class="footer-grid">
    <div>
      <div class="nav-logo" style="font-family:'Syne',sans-serif;font-weight:800;font-size:1.3rem;background:linear-gradient(135deg,#7B5CF6,#3B82F6);-webkit-background-clip:text;-webkit-text-fill-color:transparent">WebInnovate</div>
      <p class="footer-brand-desc">Soluções web que geram resultados reais para empresas que querem crescer no ambiente digital.</p>
      <div class="footer-social">
        <a class="social-btn" href="#">💼</a>
        <a class="social-btn" href="#">📸</a>
        <a class="social-btn" href="#">🐦</a>
        <a class="social-btn" href="#">▶️</a>
      </div>
    </div>
    <div class="footer-col">
      <h4>Serviços</h4>
      <ul>
        <li><a href="#">Design UI/UX</a></li>
        <li><a href="#">Desenvolvimento Web</a></li>
        <li><a href="#">E-commerce</a></li>
        <li><a href="#">Apps Mobile</a></li>
        <li><a href="#">Cloud</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Empresa</h4>
      <ul>
        <li><a href="#">Sobre nós</a></li>
        <li><a href="#">Portfólio</a></li>
        <li><a href="#">Blog</a></li>
        <li><a href="#">Carreiras</a></li>
        <li><a href="#">Parceiros</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Contato</h4>
      <ul>
        <li><a href="#">📧 contato@webinnovate.com.br</a></li>
        <li><a href="#">📞 (11) 9 9999-0000</a></li>
        <li><a href="#">📍 São Paulo, SP</a></li>
        <li><a href="#">💬 WhatsApp</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <span>© 2025 WebInnovate. Todos os direitos reservados.</span>
    <span style="color:var(--text-muted)">Feito com 💜 em São Paulo</span>
  </div>
</footer>

<script>
  // DEMO TABS
  const demoUrls = {
    store: 'webinnovate.com.br/demo/loja',
    restaurant: 'webinnovate.com.br/demo/cardapio',
    doctor: 'webinnovate.com.br/demo/medico'
  };

  function switchDemo(id, btn) {
    document.querySelectorAll('.demo-content').forEach(d => d.classList.remove('active'));
    document.querySelectorAll('.demo-tab').forEach(t => t.classList.remove('active'));
    document.getElementById('demo-' + id).classList.add('active');
    btn.classList.add('active');
    document.getElementById('demo-url').textContent = demoUrls[id];
  }

  // SCROLL REVEAL
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('visible');
        observer.unobserve(e.target);
      }
    });
  }, { threshold: 0.1 });
  reveals.forEach(r => observer.observe(r));

  // NAV SCROLL EFFECT
  window.addEventListener('scroll', () => {
    const nav = document.querySelector('nav');
    if (window.scrollY > 50) {
      nav.style.background = 'rgba(6,6,15,0.95)';
    } else {
      nav.style.background = 'rgba(6,6,15,0.7)';
    }
  });

  // COUNTER ANIMATION
  function animateCounter(el, target, suffix = '') {
    let start = 0;
    const duration = 1500;
    const step = target / (duration / 16);
    const timer = setInterval(() => {
      start += step;
      if (start >= target) {
        start = target;
        clearInterval(timer);
      }
      el.textContent = Math.round(start) + suffix;
    }, 16);
  }

  const statsObs = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        const nums = e.target.querySelectorAll('.stat-num');
        nums[0] && animateCounter(nums[0], 150, '+');
        nums[1] && animateCounter(nums[1], 98, '%');
        statsObs.unobserve(e.target);
      }
    });
  }, { threshold: 0.5 });

  const statsBar = document.querySelector('.stats-bar');
  if (statsBar) statsObs.observe(statsBar);
</script>
</body>
</html>
