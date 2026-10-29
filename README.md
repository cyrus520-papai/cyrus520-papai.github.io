<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Achroma | Movies, Games & Video</title>
    <meta
      name="description"
      content="Achroma has a movie library with YouTube trailers embedded inside the site, plus real games and a browser section."
    />
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap"
      rel="stylesheet"
    />
    <style>
      :root {
        --bg: #070b12;
        --bg-2: #0d1420;
        --panel: rgba(17, 24, 39, 0.82);
        --panel-strong: rgba(12, 18, 29, 0.92);
        --line: rgba(148, 163, 184, 0.14);
        --text: #edf2ff;
        --text-soft: #dfe7ff;
        --muted: #9aa9bd;
        --primary: #7c3aed;
        --primary-2: #8b5cf6;
        --accent: #22d3ee;
        --success: #34d399;
        --gold: #fbbf24;
        --shadow: 0 30px 80px rgba(2, 6, 23, 0.7);
        --container: 1220px;
      }

      * { box-sizing: border-box; }
      html { scroll-behavior: smooth; }
      body {
        margin: 0;
        font-family: "Inter", sans-serif;
        background:
          radial-gradient(circle at top left, rgba(124,58,237,0.18), transparent 25%),
          radial-gradient(circle at top right, rgba(34,211,238,0.12), transparent 24%),
          linear-gradient(180deg, #050a11 0%, #0a1120 52%, #0b1020 100%);
        color: var(--text);
        line-height: 1.6;
      }

      a { color: inherit; text-decoration: none; }
      img { display: block; max-width: 100%; }
      button, input { font: inherit; }

      .container {
        width: min(var(--container), calc(100% - 28px));
        margin: 0 auto;
      }

      .section {
        padding: 90px 0;
      }

      .eyebrow {
        display: inline-flex;
        align-items: center;
        gap: 12px;
        padding: 8px 14px;
        border-radius: 999px;
        background: rgba(124,58,237,0.12);
        border: 1px solid rgba(168,85,247,0.2);
        color: #d9c4ff;
        font-size: 11px;
        letter-spacing: 0.14em;
        font-weight: 700;
        text-transform: uppercase;
      }

      .eyebrow::before {
        content: "";
        width: 8px;
        height: 8px;
        border-radius: 50%;
        background: linear-gradient(135deg, #8b5cf6, #22d3ee);
        box-shadow: 0 0 16px rgba(124,58,237,0.9);
      }

      .btn {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        gap: 10px;
        padding: 15px 24px;
        border-radius: 14px;
        border: 1px solid transparent;
        font-weight: 700;
        cursor: pointer;
        transition: 0.25s ease;
        text-decoration: none;
      }

      .btn-primary {
        background: linear-gradient(135deg, var(--primary), var(--primary-2));
        color: white;
        box-shadow: 0 18px 35px rgba(124,58,237,0.35);
      }

      .btn-primary:hover {
        transform: translateY(-2px);
        box-shadow: 0 26px 45px rgba(124,58,237,0.4);
      }

      .btn-secondary {
        background: rgba(148,163,184,0.06);
        border-color: rgba(148,163,184,0.18);
        color: var(--text);
      }

      .btn-secondary:hover {
        background: rgba(148,163,184,0.12);
      }

      .header {
        position: sticky;
        top: 0;
        z-index: 50;
        backdrop-filter: blur(18px);
        background: rgba(6,11,18,0.56);
        border-bottom: 1px solid rgba(255,255,255,0.04);
      }

      .nav {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 18px 0;
      }

      .brand {
        display: inline-flex;
        align-items: center;
        gap: 12px;
        font-size: 1.48rem;
        font-weight: 800;
        letter-spacing: -0.04em;
      }

      .brand-mark {
        width: 32px;
        height: 32px;
        border-radius: 10px;
        background: linear-gradient(135deg, var(--primary), var(--accent));
        box-shadow: 0 0 24px rgba(124,58,237,0.7);
        position: relative;
      }

      .brand-mark::before {
        content: "";
        position: absolute;
        inset: 6px;
        border-radius: 7px;
        background: rgba(7,11,18,0.88);
      }

      .nav-links {
        display: flex;
        align-items: center;
        gap: 26px;
        color: var(--text-soft);
        font-size: 0.95rem;
      }

      .nav-links a:hover { color: var(--text); }

      .nav-actions {
        display: flex;
        align-items: center;
        gap: 14px;
      }

      .search {
        width: 42px;
        height: 42px;
        display: grid;
        place-items: center;
        border-radius: 12px;
        background: rgba(148,163,184,0.06);
        border: 1px solid var(--line);
        color: var(--text-soft);
      }

      .ham {
        display: none;
        width: 40px;
        height: 40px;
        border-radius: 12px;
        border: 1px solid var(--line);
        background: rgba(148,163,184,0.06);
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 5px;
        cursor: pointer;
      }

      .ham span {
        width: 18px;
        height: 2px;
        background: white;
        border-radius: 2px;
      }

      .hero {
        padding-top: 34px;
        padding-bottom: 20px;
      }

      .hero-box {
        position: relative;
        min-height: 660px;
        border-radius: 30px;
        overflow: hidden;
        border: 1px solid rgba(255,255,255,0.08);
        background:
          linear-gradient(90deg, rgba(4,7,13,0.96) 0%, rgba(4,7,13,0.72) 38%, rgba(4,7,13,0.22) 100%),
          url("https://images.unsplash.com/photo-1517604931442-7e0c8ed2963c?auto=format&fit=crop&w=1600&q=80") center/cover no-repeat;
        box-shadow: var(--shadow);
      }

      .hero-content {
        position: relative;
        z-index: 2;
        width: min(620px, calc(100% - 60px));
        padding: 62px 50px 50px;
      }

      .hero-meta {
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        gap: 14px;
        margin-bottom: 18px;
      }

      .meta-pill {
        display: inline-flex;
        align-items: center;
        gap: 8px;
        padding: 8px 12px;
        border-radius: 999px;
        border: 1px solid rgba(255,255,255,0.1);
        background: rgba(255,255,255,0.06);
        color: #e8efff;
        font-size: 0.76rem;
        font-weight: 600;
      }

      .hero-content h1 {
        font-size: clamp(3rem, 6vw, 6rem);
        line-height: 0.92;
        letter-spacing: -0.08em;
        margin: 0 0 18px;
      }

      .hero-content p {
        max-width: 560px;
        color: rgba(237,242,255,0.8);
        font-size: 1.08rem;
        margin-bottom: 28px;
      }

      .hero-actions {
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        gap: 16px;
        margin-bottom: 30px;
      }

      .hero-stats {
        display: flex;
        flex-wrap: wrap;
        gap: 24px;
      }

      .stat-box {
        min-width: 120px;
      }

      .stat-box .label {
        display: block;
        color: rgba(237,242,255,0.66);
        font-size: 0.8rem;
        margin-bottom: 6px;
      }

      .stat-box strong {
        font-size: 1.8rem;
        letter-spacing: -0.06em;
      }

      .hero-side-panel {
        position: absolute;
        right: 26px;
        bottom: 26px;
        width: min(320px, calc(100% - 40px));
        padding: 18px 16px;
        border-radius: 20px;
        background: rgba(15,23,42,0.84);
        border: 1px solid rgba(255,255,255,0.08);
        backdrop-filter: blur(12px);
        box-shadow: var(--shadow);
      }

      .hero-side-panel .row {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 8px;
        font-size: 0.75rem;
        letter-spacing: 0.12em;
        text-transform: uppercase;
        color: var(--text-soft);
      }

      .movie-title {
        font-size: 1.6rem;
        font-weight: 800;
        letter-spacing: -0.05em;
        margin-bottom: 10px;
      }

      .tags {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
      }

      .tag {
        padding: 6px 10px;
        border-radius: 999px;
        font-size: 0.72rem;
        font-weight: 600;
        border: 1px solid rgba(168,85,247,0.18);
        background: rgba(124,58,237,0.12);
        color: #d9c4ff;
      }

      .section-head {
        display: flex;
        justify-content: space-between;
        align-items: end;
        gap: 20px;
        margin-bottom: 28px;
      }

      .section-head h2 {
        margin: 14px 0 0;
        font-size: clamp(2.1rem, 3vw, 3.5rem);
        line-height: 1;
        letter-spacing: -0.06em;
      }

      .section-head p {
        color: var(--muted);
        max-width: 560px;
        margin: 0;
      }

      .chip-row {
        display: flex;
        flex-wrap: wrap;
        gap: 10px;
      }

      .chip {
        padding: 9px 14px;
        border-radius: 999px;
        background: rgba(148,163,184,0.04);
        border: 1px solid var(--line);
        color: var(--text-soft);
        font-size: 0.8rem;
        font-weight: 600;
      }

      .chip.active {
        background: linear-gradient(135deg, rgba(124,58,237,0.18), rgba(34,211,238,0.12));
        color: white;
        border-color: rgba(168,85,247,0.28);
      }

      .video-player-shell {
        background: rgba(15,23,42,0.7);
        border: 1px solid var(--line);
        border-radius: 28px;
        overflow: hidden;
        margin-bottom: 24px;
        box-shadow: var(--shadow);
      }

      .video-wrap {
        position: relative;
        width: 100%;
        padding-top: 56.25%;
      }

      .video-wrap iframe {
        position: absolute;
        inset: 0;
        width: 100%;
        height: 100%;
        border: 0;
      }

      .video-meta {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 12px;
        padding: 16px 18px 20px;
      }

      .video-meta h3 {
        margin: 0;
        font-size: 1.5rem;
        letter-spacing: -0.04em;
      }

      .video-meta span {
        color: var(--muted);
      }

      .media-grid {
        display: grid;
        grid-template-columns: repeat(5, minmax(0, 1fr));
        gap: 18px;
      }

      .card {
        position: relative;
        overflow: hidden;
        border-radius: 20px;
        border: 1px solid var(--line);
        background: rgba(15,23,42,0.7);
        transition: transform 0.25s ease, box-shadow 0.25s ease;
        cursor: pointer;
      }

      .card:hover {
        transform: translateY(-4px);
        box-shadow: 0 26px 50px rgba(0,0,0,0.25);
      }

      .poster {
        position: relative;
        aspect-ratio: 3 / 4.5;
        overflow: hidden;
      }

      .poster img {
        width: 100%;
        height: 100%;
        object-fit: cover;
      }

      .poster::after {
        content: "";
        position: absolute;
        inset: 0;
        background: linear-gradient(180deg, rgba(10,12,20,0.04), rgba(10,12,20,0.82));
      }

      .card-content {
        position: absolute;
        inset: auto 0 0 0;
        z-index: 1;
        padding: 18px 16px 16px;
      }

      .rating-row {
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-bottom: 8px;
      }

      .rating {
        display: inline-flex;
        align-items: center;
        gap: 6px;
        color: #fef3c7;
        font-size: 0.8rem;
      }

      .rating::before {
        content: "★";
        color: var(--gold);
      }

      .duration {
        color: rgba(237,242,255,0.72);
        font-size: 0.75rem;
      }

      .card-title {
        margin: 0;
        font-size: 1.08rem;
        letter-spacing: -0.04em;
        font-weight: 700;
      }

      .sub {
        margin-top: 5px;
        color: rgba(237,242,255,0.76);
        font-size: 0.76rem;
      }

      .feature-panel {
        background: rgba(15, 23, 42, 0.7);
        border: 1px solid var(--line);
        border-radius: 28px;
        overflow: hidden;
      }

      .feature-panel.large {
        display: grid;
        grid-template-columns: 1.25fr 0.75fr;
      }

      .feature-image {
        min-height: 330px;
        background:
          linear-gradient(135deg, rgba(10,12,20,0.18), rgba(10,12,20,0.78)),
          url("https://images.unsplash.com/photo-1524985069026-dd778a71c7b4?auto=format&fit=crop&w=1200&q=80") center/cover no-repeat;
      }

      .feature-copy {
        padding: 28px 26px;
      }

      .feature-copy h3 {
        margin: 18px 0 12px;
        font-size: clamp(2rem, 2.9vw, 3rem);
        letter-spacing: -0.06em;
        line-height: 1;
      }

      .feature-copy p {
        color: var(--muted);
        margin: 0 0 18px;
      }

      .mini-list {
        list-style: none;
        margin: 0 0 22px;
        padding: 0;
      }

      .mini-list li {
        display: flex;
        align-items: center;
        gap: 10px;
        color: var(--text-soft);
        margin-bottom: 10px;
      }

      .mini-list li::before {
        content: "✓";
        width: 22px;
        height: 22px;
        display: inline-grid;
        place-items: center;
        border-radius: 50%;
        background: rgba(52,211,153,0.12);
        border: 1px solid rgba(52,211,153,0.2);
        color: var(--success);
        font-weight: 900;
      }

      .games-grid {
        display: grid;
        grid-template-columns: repeat(4, minmax(0,1fr));
        gap: 18px;
      }

      .game-card {
        background: rgba(15, 23, 42, 0.72);
        border: 1px solid var(--line);
        border-radius: 22px;
        overflow: hidden;
      }

      .game-card .img {
        height: 180px;
        background-size: cover;
        background-position: center;
      }

      .game-card .content {
        padding: 16px;
      }

      .game-card h3 {
        margin: 0 0 8px;
        font-size: 1.14rem;
      }

      .game-card p {
        margin: 0 0 12px;
        color: var(--muted);
        font-size: 0.85rem;
      }

      .game-card .tiny {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 12px;
        margin-bottom: 12px;
      }

      .badge {
        display: inline-flex;
        align-items: center;
        gap: 6px;
        padding: 6px 10px;
        border-radius: 999px;
        background: rgba(124,58,237,0.12);
        border: 1px solid rgba(168,85,247,0.18);
        color: #d9c4ff;
        font-size: 0.72rem;
        font-weight: 700;
      }

      .browser-shell {
        background: rgba(15,23,42,0.74);
        border: 1px solid var(--line);
        border-radius: 28px;
        overflow: hidden;
        box-shadow: var(--shadow);
      }

      .browser-topbar {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 16px;
        padding: 14px 18px;
        background: rgba(17,24,39,0.9);
        border-bottom: 1px solid var(--line);
      }

      .browser-controls {
        display: flex;
        align-items: center;
        gap: 8px;
      }

      .browser-dot {
        width: 12px;
        height: 12px;
        border-radius: 50%;
      }

      .browser-dot:nth-child(1) { background: #f87171; }
      .browser-dot:nth-child(2) { background: #fbbf24; }
      .browser-dot:nth-child(3) { background: #4ade80; }

      .browser-address {
        flex: 1;
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 10px 14px;
        border-radius: 12px;
        background: rgba(148,163,184,0.04);
        border: 1px solid var(--line);
        color: var(--text-soft);
        font-size: 0.82rem;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
      }

      .browser-actions {
        display: flex;
        flex-wrap: wrap;
        gap: 10px;
        padding: 18px;
        border-bottom: 1px solid var(--line);
        background: rgba(12,18,29,0.7);
      }

      .browser-btn {
        padding: 10px 14px;
        border-radius: 12px;
        background: rgba(148,163,184,0.04);
        border: 1px solid var(--line);
        color: var(--text-soft);
        font-weight: 600;
        cursor: pointer;
      }

      .browser-pane {
        padding: 20px;
      }

      .browser-placeholder {
        display: grid;
        place-items: center;
        min-height: 360px;
        border-radius: 18px;
        border: 1px dashed rgba(148,163,184,0.18);
        background: rgba(148,163,184,0.02);
        padding: 24px;
        color: var(--muted);
        text-align: center;
      }

      .cta-box {
        background: linear-gradient(135deg, rgba(124,58,237,0.12), rgba(34,211,238,0.08));
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 30px;
        padding: 34px 28px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 20px;
      }

      .cta-box h3 {
        margin: 14px 0 10px;
        font-size: clamp(2rem, 3vw, 3rem);
        line-height: 1;
        letter-spacing: -0.06em;
      }

      .cta-box p {
        margin: 0;
        color: var(--muted);
      }

      .footer {
        padding: 22px 0 60px;
      }

      .footer-inner {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 20px;
        padding-top: 28px;
        border-top: 1px solid rgba(148,163,184,0.08);
        color: var(--muted);
      }

      .footer-links {
        display: flex;
        flex-wrap: wrap;
        gap: 18px;
      }

      @media (max-width: 1100px) {
        .media-grid { grid-template-columns: repeat(3, minmax(0,1fr)); }
        .games-grid { grid-template-columns: repeat(2, minmax(0,1fr)); }
        .feature-panel.large { grid-template-columns: 1fr; }
      }

      @media (max-width: 980px) {
        .nav-links {
          position: absolute;
          top: calc(100% + 10px);
          left: 14px;
          right: 14px;
          background: rgba(15,23,42,0.96);
          border: 1px solid var(--line);
          border-radius: 18px;
          padding: 18px;
          display: none;
          flex-direction: column;
          align-items: flex-start;
          gap: 16px;
          box-shadow: var(--shadow);
        }

        .nav-links.open { display: flex; }
        .ham { display: flex; }
        .nav-actions .btn { display: none; }
        .hero-side-panel {
          position: static;
          width: auto;
          margin: 18px 20px 20px;
        }
        .hero-box { min-height: auto; }
      }

      @media (max-width: 720px) {
        .media-grid { grid-template-columns: repeat(2, minmax(0,1fr)); }
        .games-grid { grid-template-columns: 1fr; }
        .section-head {
          flex-direction: column;
          align-items: flex-start;
        }
        .hero-content {
          width: calc(100% - 30px);
          padding: 38px 18px 18px;
        }
        .hero-actions { flex-direction: column; align-items: stretch; }
        .hero-actions .btn {
          width: 100%;
        }
        .cta-box {
          flex-direction: column;
          align-items: flex-start;
        }
        .footer-inner {
          flex-direction: column;
          align-items: flex-start;
        }
      }

      @media (max-width: 500px) {
        .media-grid { grid-template-columns: 1fr; }
        .hero-meta { flex-wrap: wrap; }
      }
    </style>
  </head>
  <body>
    <header class="header">
      <div class="container nav">
        <a href="#top" class="brand" aria-label="Achroma home">
          <span class="brand-mark" aria-hidden="true"></span>
          Achroma
        </a>

        <nav class="nav-links" id="navLinks">
          <a href="#home">Home</a>
          <a href="#movies">Movies</a>
          <a href="#games">Games</a>
          <a href="#browser">Browser</a>
        </nav>

        <div class="nav-actions">
          <span class="search" aria-label="Search">⌕</span>
          <a href="#browser" class="btn btn-secondary">Open Browser</a>
          <button class="ham" id="menuBtn" aria-label="Toggle menu">
            <span></span>
            <span></span>
            <span></span>
          </button>
        </div>
      </div>
    </header>

    <main id="top">
      <section id="home" class="section hero">
        <div class="container">
          <div class="hero-box">
            <div class="hero-content">
              <div class="hero-meta">
                <span class="meta-pill">Movies</span>
                <span class="meta-pill">Games</span>
                <span class="meta-pill">Browser</span>
              </div>

              <h1>Watch. Play. Browse.</h1>

              <p>
                Achroma gives you embedded YouTube trailers in the app, real game storefronts, and browser launchers for trustworthy entertainment sites.
              </p>

              <div class="hero-actions">
                <a href="#movies" class="btn btn-primary">▶ Watch Movies</a>
                <a href="#games" class="btn btn-secondary">🎮 Explore Games</a>
              </div>

              <div class="hero-stats">
                <div class="stat-box">
                  <span class="label">Movies</span>
                  <strong>120+</strong>
                </div>
                <div class="stat-box">
                  <span class="label">Games</span>
                  <strong>90+</strong>
                </div>
                <div class="stat-box">
                  <span class="label">Sites</span>
                  <strong>18</strong>
                </div>
              </div>
            </div>

            <div class="hero-side-panel">
              <div class="row">
                <span>Featured</span>
                <span>2026</span>
              </div>
              <div class="movie-title">Skyline Nights</div>
              <div class="tags">
                <span class="tag">Epic</span>
                <span class="tag">Sci‑Fi</span>
                <span class="tag">Official</span>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section id="movies" class="section">
        <div class="container">
          <div class="section-head">
            <div>
              <span class="eyebrow">Movies</span>
              <h2>Watch trailers in the website.</h2>
            </div>
            <div class="chip-row">
              <span class="chip active">All</span>
              <span class="chip">Action</span>
              <span class="chip">Sci‑Fi</span>
              <span class="chip">Drama</span>
              <span class="chip">Epic</span>
            </div>
          </div>

          <div class="video-player-shell">
            <div class="video-wrap">
              <iframe
                id="mainVideo"
                src="https://www.youtube.com/embed/Way9Dexny3w?autoplay=0&rel=0"
                title="Featured movie trailer"
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
                allowfullscreen>
              </iframe>
            </div>

            <div class="video-meta">
              <h3 id="mainVideoTitle">Dune: Part Two</h3>
              <span id="mainVideoType">Official trailer</span>
            </div>
          </div>

          <div id="movieGrid" class="media-grid"></div>
        </div>
      </section>

      <section id="games" class="section">
        <div class="container">
          <div class="section-head">
            <div>
              <span class="eyebrow">Games</span>
              <h2>Real games from official stores.</h2>
            </div>
            <p>Official store links to Steam, Epic, Minecraft, and other trusted publishers.</p>
          </div>

          <div id="gameGrid" class="games-grid"></div>
        </div>
      </section>

      <section id="browser" class="section">
        <div class="container">
          <div class="section-head">
            <div>
              <span class="eyebrow">Browser</span>
              <h2>Open official websites directly.</h2>
            </div>
            <p>This is a browser launcher for trusted sites, not a pirated media host.</p>
          </div>

          <div class="browser-shell">
            <div class="browser-topbar">
              <div class="browser-controls">
                <span class="browser-dot"></span>
                <span class="browser-dot"></span>
                <span class="browser-dot"></span>
              </div>

              <div class="browser-address" id="browserAddress">https://store.steampowered.com</div>
            </div>

            <div class="browser-actions">
              <button class="browser-btn" data-url="https://www.imdb.com/">IMDb</button>
              <button class="browser-btn" data-url="https://www.rottentomatoes.com/">Rotten Tomatoes</button>
              <button class="browser-btn" data-url="https://store.steampowered.com/">Steam</button>
              <button class="browser-btn" data-url="https://store.epicgames.com/en-US/">Epic Games</button>
              <button class="browser-btn" data-url="https://www.netflix.com/">Netflix</button>
              <button class="browser-btn" data-url="https://www.disneyplus.com/">Disney+</button>
              <button class="browser-btn" data-url="https://www.minecraft.net/">Minecraft</button>
            </div>

            <div class="browser-pane">
              <div class="browser-placeholder">
                <div>
                  <h3 style="margin:0 0 10px; font-size:1.8rem; letter-spacing:-0.04em;">Launch an official website</h3>
                  <p style="margin:0; max-width:520px; color:var(--muted);">
                    Choose a trusted site above to open it in a new tab.
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section class="section">
        <div class="container">
          <div class="feature-panel large">
            <div class="feature-image"></div>
            <div class="feature-copy">
              <span class="eyebrow">Why Achroma</span>
              <h3>Real entertainment, properly linked.</h3>
              <p>
                Achroma is built around official sources: YouTube trailers, trusted game stores, and browser links to real entertainment platforms.
              </p>

              <ul class="mini-list">
                <li>Embedded YouTube trailers</li>
                <li>Official game storefronts</li>
                <li>Trusted browser launchers</li>
              </ul>

              <a href="#browser" class="btn btn-primary">Open Browser</a>
            </div>
          </div>
        </div>
      </section>

      <section class="section">
        <div class="container">
          <div class="cta-box">
            <div>
              <span class="eyebrow">Official sources</span>
              <h3>Play real games. Watch trailers inside the site.</h3>
              <p>No tab breaks for the main movie experience.</p>
            </div>

            <div style="display:flex; gap:12px; flex-wrap:wrap;">
              <a href="#movies" class="btn btn-primary">Watch Movies</a>
              <a href="#games" class="btn btn-secondary">View Games</a>
            </div>
          </div>
        </div>
      </section>
    </main>

    <footer class="footer">
      <div class="container footer-inner">
        <div class="brand">
          <span class="brand-mark" aria-hidden="true"></span>
          Achroma
        </div>

        <div class="footer-links">
          <a href="#movies">Movies</a>
          <a href="#games">Games</a>
          <a href="#browser">Browser</a>
        </div>
      </div>
    </footer>

    <script>
      const movieData = [
        { title: "Dune: Part Two", subtitle: "Sci‑Fi / Epic", rating: "8.6", meta: "Trailer", image: "https://images.unsplash.com/photo-1513106580091-1d82408b8cd6?auto=format&fit=crop&w=800&q=80", embed: "https://www.youtube.com/embed/Way9Dexny3w?autoplay=0&rel=0" },
        { title: "The Batman", subtitle: "Action / Crime", rating: "8.5", meta: "Trailer", image: "https://images.unsplash.com/photo-1504384308090-c894fdcc538d?auto=format&fit=crop&w=800&q=80", embed: "https://www.youtube.com/embed/mqqft2x_Aa4?autoplay=0&rel=0" },
        { title: "Oppenheimer", subtitle: "Drama / Biography", rating: "8.6", meta: "Trailer", image: "https://images.unsplash.com/photo-1497032628192-86f99bcd76bc?auto=format&fit=crop&w=800&q=80", embed: "https://www.youtube.com/embed/uYPbbksJxIg?autoplay=0&rel=0" },
        { title: "Interstellar", subtitle: "Sci‑Fi / Adventure", rating: "8.7", meta: "Trailer", image: "https://images.unsplash.com/photo-1517602302552-471fe67acf66?auto=format&fit=crop&w=800&q=80", embed: "https://www.youtube.com/embed/zSWdZVtXT7E?autoplay=0&rel=0" },
        { title: "Blade Runner 2049", subtitle: "Sci‑Fi / Mystery", rating: "8.0", meta: "Trailer", image: "https://images.unsplash.com/photo-1517604931442-7e0c8ed2963c?auto=format&fit=crop&w=800&q=80", embed: "https://www.youtube.com/embed/gCcx85zbxz4?autoplay=0&rel=0" },
        { title: "Inception", subtitle: "Sci‑Fi / Thriller", rating: "8.8", meta: "Trailer", image: "https://images.unsplash.com/photo-1516280440614-37939bbacd81?auto=format&fit=crop&w=800&q=80", embed: "https://www.youtube.com/embed/YoHD9XEInc0?autoplay=0&rel=0" },
        { title: "Top Gun: Maverick", subtitle: "Action / Drama", rating: "8.3", meta: "Trailer", image: "https://images.unsplash.com/photo-1527631746610-bca00a040d60?auto=format&fit=crop&w=800&q=80", embed: "https://www.youtube.com/embed/qSqVVswa420?autoplay=0&rel=0" },
        { title: "The Dark Knight", subtitle: "Action / Crime", rating: "9.0", meta: "Trailer", image: "https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?auto=format&fit=crop&w=800&q=80", embed: "https://www.youtube.com/embed/EXeTwQWrcwY?autoplay=0&rel=0" },
        { title: "Arrival", subtitle: "Sci‑Fi / Drama", rating: "7.9", meta: "Trailer", image: "https://images.unsplash.com/photo-1522869635100-9f4c5e86aa37?auto=format&fit=crop&w=800&q=80", embed: "https://www.youtube.com/embed/tFMo3UJ4B4g?autoplay=0&rel=0" },
        { title: "Mad Max: Fury Road", subtitle: "Action / Adventure", rating: "8.1", meta: "Trailer", image: "https://images.unsplash.com/photo-1478720568477-152d9b164e26?auto=format&fit=crop&w=800&q=80", embed: "https://www.youtube.com/embed/hEJnMQG9ev8?autoplay=0&rel=0" },
        { title: "Gladiator", subtitle: "Action / Drama", rating: "8.5", meta: "Trailer", image: "https://images.unsplash.com/photo-1497032628192-86f99bcd76bc?auto=format&fit=crop&w=800&q=80", embed: "https://www.youtube.com/embed/owK1qxDselE?autoplay=0&rel=0" },
        { title: "No Time to Die", subtitle: "Action / Spy", rating: "7.3", meta: "Trailer", image: "https://images.unsplash.com/photo-1516979187457-637abb4f9353?auto=format&fit=crop&w=800&q=80", embed: "https://www.youtube.com/embed/NG4yxDtvA3Q?autoplay=0&rel=0" }
      ];

      const gameData = [
        { title: "Counter-Strike 2", subtitle: "FPS / Competitive", rating: "9.0", meta: "Steam", image: "https://images.unsplash.com/photo-1542751371-adc38448a05e?auto=format&fit=crop&w=800&q=80", link: "https://store.steampowered.com/app/730/CounterStrike_2/" },
        { title: "Helldivers 2", subtitle: "Co-op / Shooter", rating: "9.4", meta: "Steam", image: "https://images.unsplash.com/photo-1511512578047-dfb367046420?auto=format&fit=crop&w=800&q=80", link: "https://store.steampowered.com/app/553850/HELLDIVERS_2/" },
        { title: "Apex Legends", subtitle: "Battle Royale", rating: "8.9", meta: "EA / Steam", image: "https://images.unsplash.com/photo-1551107696-a4b0c5a0d9a2?auto=format&fit=crop&w=800&q=80", link: "https://store.steampowered.com/app/1172470/Apex_Legends/" },
        { title: "Rocket League", subtitle: "Sports / Arcade", rating: "8.7", meta: "Steam", image: "https://images.unsplash.com/photo-1545239351-1141bd82e8a6?auto=format&fit=crop&w=800&q=80", link: "https://store.steampowered.com/app/252950/Rocket_League/" },
        { title: "Dead by Daylight", subtitle: "Survival / Horror", rating: "8.4", meta: "Steam", image: "https://images.unsplash.com/photo-1560253023-3ec5d5029598?auto=format&fit=crop&w=800&q=80", link: "https://store.steampowered.com/app/381210/Dead_by_Daylight/" },
        { title: "Minecraft", subtitle: "Sandbox / Survival", rating: "9.1", meta: "Official Store", image: "https://images.unsplash.com/photo-1528819622761-6bcf9d2d1f25?auto=format&fit=crop&w=800&q=80", link: "https://www.minecraft.net/" },
        { title: "Valorant", subtitle: "Tactical Shooter", rating: "8.8", meta: "Official Store", image: "https://images.unsplash.com/photo-1509198397868-475647b2a1e5?auto=format&fit=crop&w=800&q=80", link: "https://playvalorant.com/" },
        { title: "Fortnite", subtitle: "Battle Royale", rating: "8.6", meta: "Epic Games", image: "https://images.unsplash.com/photo-1534423861386-85a16f5d13fd?auto=format&fit=crop&w=800&q=80", link: "https://store.epicgames.com/en-US/p/fortnite" },
        { title: "League of Legends", subtitle: "MOBA / Strategy", rating: "8.9", meta: "Official Site", image: "https://images.unsplash.com/photo-1511884642898-4c92249e20b6?auto=format&fit=crop&w=800&q=80", link: "https://www.leagueoflegends.com/" },
        { title: "Baldur's Gate 3", subtitle: "RPG / Story Rich", rating: "9.3", meta: "Steam", image: "https://images.unsplash.com/photo-1493711662062-fa541adb3fc8?auto=format&fit=crop&w=800&q=80", link: "https://store.steampowered.com/app/1086940/Baldurs_Gate_3/" },
        { title: "God of War", subtitle: "Action / Adventure", rating: "9.2", meta: "Steam / PlayStation", image: "https://images.unsplash.com/photo-1517457373958-b7bdd4587205?auto=format&fit=crop&w=800&q=80", link: "https://store.steampowered.com/app/1593500/God_of_War/" },
        { title: "The Witcher 3", subtitle: "RPG / Adventure", rating: "9.1", meta: "Steam", image: "https://images.unsplash.com/photo-1522202176988-66273c2fd55f?auto=format&fit=crop&w=800&q=80", link: "https://store.steampowered.com/app/292030/The_Witcher_3_Wild_Hunt/" }
      ];

      const mainVideo = document.getElementById("mainVideo");
      const mainVideoTitle = document.getElementById("mainVideoTitle");
      const mainVideoType = document.getElementById("mainVideoType");

      const movieGrid = document.getElementById("movieGrid");
      movieGrid.innerHTML = movieData.map(item => `
        <div class="card" data-video="${item.embed}" data-title="${item.title}" data-type="${item.subtitle}">
          <div class="poster">
            <img src="${item.image}" alt="${item.title}" />
          </div>
          <div class="card-content">
            <div class="rating-row">
              <span class="rating">${item.rating}</span>
              <span class="duration">${item.meta}</span>
            </div>
            <h3 class="card-title">${item.title}</h3>
            <div class="sub">${item.subtitle}</div>
          </div>
        </div>
      `).join("");

      document.querySelectorAll(".card").forEach(card => {
        card.addEventListener("click", () => {
          const src = card.getAttribute("data-video");
          const title = card.getAttribute("data-title");
          const type = card.getAttribute("data-type");
          mainVideo.src = src + "&autoplay=1&rel=0";
          mainVideoTitle.textContent = title;
          mainVideoType.textContent = type;
        });
      });

      const gameGrid = document.getElementById("gameGrid");
      gameGrid.innerHTML = gameData.map(item => `
        <a class="game-card" href="${item.link}" target="_blank" rel="noreferrer">
          <div class="img" style="background-image:url('${item.image}')"></div>
          <div class="content">
            <div class="tiny">
              <span class="badge">${item.meta}</span>
              <span class="duration">${item.rating}</span>
            </div>
            <h3>${item.title}</h3>
            <p>${item.subtitle}</p>
            <span class="btn btn-secondary" style="width: 100%;">Open Store</span>
          </div>
        </a>
      `).join("");

      const browserAddress = document.getElementById("browserAddress");
      document.querySelectorAll(".browser-btn").forEach(button => {
        button.addEventListener("click", () => {
          const url = button.dataset.url;
          browserAddress.textContent = url;
          window.open(url, "_blank", "noopener,noreferrer");
        });
      });

      const menuBtn = document.getElementById("menuBtn");
      const navLinks = document.getElementById("navLinks");
      menuBtn.addEventListener("click", () => navLinks.classList.toggle("open"));
      navLinks.querySelectorAll("a").forEach(link => {
        link.addEventListener("click", () => navLinks.classList.remove("open"));
      });
    </script>
  </body>
</html>
