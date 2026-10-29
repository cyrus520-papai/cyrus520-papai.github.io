<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Achroma | Movies & Shows</title>
    <meta
      name="description"
      content="Achroma brings together the best movies, series, and trending entertainment all in one immersive streaming experience."
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
        --panel: rgba(16, 23, 35, 0.88);
        --soft-panel: rgba(15, 23, 42, 0.7);
        --line: rgba(148, 163, 184, 0.12);
        --muted: #9aa9bd;
        --text: #edf2ff;
        --text-soft: #d6def1;
        --primary: #7c3aed;
        --primary-2: #8b5cf6;
        --accent: #22d3ee;
        --success: #34d399;
        --danger: #f87171;
        --gold: #fbbf24;
        --shadow: 0 30px 60px rgba(3, 7, 18, 0.6);
        --radius: 22px;
        --container: 1200px;
      }

      * {
        box-sizing: border-box;
      }

      html {
        scroll-behavior: smooth;
      }

      body {
        margin: 0;
        font-family: "Inter", sans-serif;
        background:
          radial-gradient(circle at top left, rgba(124, 58, 237, 0.18), transparent 28%),
          radial-gradient(circle at top right, rgba(34, 211, 238, 0.10), transparent 22%),
          linear-gradient(180deg, #060911 0%, #0b1220 100%);
        color: var(--text);
        line-height: 1.6;
      }

      a {
        color: inherit;
        text-decoration: none;
      }

      img {
        max-width: 100%;
        display: block;
      }

      button {
        font: inherit;
      }

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
        gap: 10px;
        padding: 8px 14px;
        border-radius: 999px;
        background: rgba(124, 58, 237, 0.12);
        border: 1px solid rgba(168, 85, 247, 0.2);
        color: #d9c4ff;
        font-size: 11px;
        font-weight: 700;
        letter-spacing: 0.14em;
        text-transform: uppercase;
      }

      .eyebrow::before {
        content: "";
        width: 8px;
        height: 8px;
        border-radius: 50%;
        background: linear-gradient(135deg, #8b5cf6, #22d3ee);
        box-shadow: 0 0 18px rgba(124, 58, 237, 0.8);
      }

      .btn {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        gap: 10px;
        padding: 15px 24px;
        border-radius: 14px;
        border: 1px solid transparent;
        cursor: pointer;
        font-weight: 700;
        transition: 0.25s ease;
      }

      .btn-primary {
        background: linear-gradient(135deg, var(--primary), var(--primary-2));
        color: white;
        box-shadow: 0 18px 35px rgba(124, 58, 237, 0.35);
      }

      .btn-primary:hover {
        transform: translateY(-2px);
        box-shadow: 0 26px 45px rgba(124, 58, 237, 0.4);
      }

      .btn-secondary {
        background: rgba(148, 163, 184, 0.07);
        border-color: var(--line);
        color: var(--text);
      }

      .btn-secondary:hover {
        background: rgba(148, 163, 184, 0.12);
      }

      .header {
        position: sticky;
        top: 0;
        z-index: 40;
        backdrop-filter: blur(18px);
        background: rgba(7, 11, 18, 0.54);
        border-bottom: 1px solid rgba(255,255,255,0.03);
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
        font-size: 1.5rem;
        font-weight: 800;
        letter-spacing: -0.05em;
      }

      .brand-mark {
        width: 32px;
        height: 32px;
        border-radius: 10px;
        background: linear-gradient(135deg, var(--primary), var(--accent));
        box-shadow: 0 0 24px rgba(124, 58, 237, 0.6);
        position: relative;
      }

      .brand-mark::before {
        content: "";
        position: absolute;
        inset: 6px;
        border-radius: 7px;
        background: rgba(7, 11, 18, 0.88);
      }

      .nav-links {
        display: flex;
        align-items: center;
        gap: 26px;
        color: var(--text-soft);
        font-size: 0.95rem;
      }

      .nav-links a:hover {
        color: var(--text);
      }

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
        background: rgba(148, 163, 184, 0.06);
        border: 1px solid var(--line);
      }

      .ham {
        display: none;
        width: 40px;
        height: 40px;
        border-radius: 12px;
        border: 1px solid var(--line);
        background: rgba(148, 163, 184, 0.06);
        align-items: center;
        justify-content: center;
        flex-direction: column;
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
        padding-top: 42px;
        padding-bottom: 20px;
      }

      .hero-box {
        position: relative;
        min-height: 650px;
        border-radius: 30px;
        overflow: hidden;
        border: 1px solid rgba(255,255,255,0.08);
        background:
          linear-gradient(90deg, rgba(5,7,13,0.94) 0%, rgba(5,7,13,0.65) 40%, rgba(5,7,13,0.2) 100%),
          url("https://images.unsplash.com/photo-1517604931442-7e0c8ed2963c?auto=format&fit=crop&w=1600&q=80") center/cover no-repeat;
        box-shadow: var(--shadow);
      }

      .hero-content {
        position: relative;
        z-index: 2;
        width: min(620px, calc(100% - 60px));
        padding: 64px 52px 56px;
      }

      .hero-meta {
        display: flex;
        align-items: center;
        gap: 18px;
        color: #dfe8ff;
        font-size: 0.82rem;
        margin-bottom: 18px;
      }

      .meta-pill {
        display: inline-flex;
        align-items: center;
        gap: 8px;
        padding: 8px 12px;
        border-radius: 999px;
        background: rgba(255,255,255,0.08);
        border: 1px solid rgba(255,255,255,0.1);
      }

      .hero-content h1 {
        font-size: clamp(2.9rem, 6vw, 6rem);
        line-height: 0.92;
        letter-spacing: -0.08em;
        margin: 0 0 18px;
      }

      .hero-content p {
        max-width: 560px;
        font-size: 1.08rem;
        color: rgba(237, 242, 255, 0.82);
        margin-bottom: 28px;
      }

      .hero-actions {
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        gap: 16px;
        margin-bottom: 32px;
      }

      .play-btn {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        gap: 12px;
        width: 52px;
        height: 52px;
        border-radius: 50%;
        background: rgba(255,255,255,0.12);
        border: 1px solid rgba(255,255,255,0.18);
        font-size: 1.1rem;
      }

      .hero-stats {
        display: flex;
        flex-wrap: wrap;
        gap: 22px;
      }

      .stat-box {
        min-width: 140px;
      }

      .stat-box .label {
        display: block;
        color: rgba(237,242,255,0.66);
        font-size: 0.8rem;
        margin-bottom: 4px;
      }

      .stat-box strong {
        font-size: 1.8rem;
        letter-spacing: -0.06em;
      }

      .hero-side-panel {
        position: absolute;
        right: 34px;
        bottom: 28px;
        width: min(310px, calc(100% - 44px));
        padding: 20px 18px;
        border-radius: 22px;
        background: rgba(15,23,42,0.82);
        border: 1px solid rgba(255,255,255,0.08);
        backdrop-filter: blur(12px);
        box-shadow: var(--shadow);
      }

      .hero-side-panel .row {
        display: flex;
        justify-content: space-between;
        align-items: center;
        color: var(--text-soft);
        font-size: 0.78rem;
        letter-spacing: 0.12em;
        text-transform: uppercase;
        margin-bottom: 8px;
      }

      .hero-side-panel .movie-title {
        font-size: 1.55rem;
        font-weight: 800;
        letter-spacing: -0.05em;
        margin-bottom: 10px;
      }

      .tags {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
        margin-top: 10px;
      }

      .tag {
        padding: 6px 10px;
        border-radius: 999px;
        background: rgba(124,58,237,0.12);
        color: #d9c4ff;
        border: 1px solid rgba(168,85,247,0.18);
        font-size: 0.75rem;
        font-weight: 600;
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
        border: 1px solid var(--line);
        background: rgba(148,163,184,0.04);
        color: var(--text-soft);
        font-size: 0.8rem;
        font-weight: 600;
      }

      .chip.active {
        background: linear-gradient(135deg, rgba(124,58,237,0.18), rgba(34,211,238,0.12));
        color: white;
        border-color: rgba(168,85,247,0.28);
      }

      .media-grid {
        display: grid;
        grid-template-columns: repeat(5, minmax(0, 1fr));
        gap: 18px;
      }

      .card {
        position: relative;
        border-radius: 20px;
        overflow: hidden;
        background: rgba(15, 23, 42, 0.62);
        border: 1px solid var(--line);
        transition: transform 0.25s ease, box-shadow 0.25s ease;
      }

      .card:hover {
        transform: translateY(-4px);
        box-shadow: 0 18px 40px rgba(15,23,42,0.35);
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
        background: linear-gradient(180deg, rgba(10,12,20,0.05), rgba(10,12,20,0.8));
      }

      .card-content {
        position: absolute;
        inset: auto 0 0 0;
        padding: 18px 16px 16px;
        z-index: 1;
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
        font-size: 0.8rem;
        color: #fef3c7;
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
        font-weight: 700;
        font-size: 1.08rem;
        letter-spacing: -0.04em;
        margin: 0;
      }

      .sub {
        color: rgba(237,242,255,0.7);
        font-size: 0.76rem;
        margin-top: 6px;
      }

      .continue-grid {
        display: grid;
        grid-template-columns: repeat(3, minmax(0, 1fr));
        gap: 18px;
      }

      .episode-card {
        display: flex;
        gap: 14px;
        align-items: center;
        background: rgba(15,23,42,0.7);
        border: 1px solid var(--line);
        border-radius: 18px;
        padding: 12px;
      }

      .episode-card .thumb {
        width: 120px;
        height: 90px;
        border-radius: 14px;
        overflow: hidden;
        flex-shrink: 0;
      }

      .episode-card .thumb img {
        width: 100%;
        height: 100%;
        object-fit: cover;
      }

      .episode-info {
        flex: 1;
      }

      .episode-top {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 10px;
        margin-bottom: 8px;
      }

      .episode-top strong {
        font-size: 1rem;
      }

      .progress {
        position: relative;
        width: 100%;
        height: 8px;
        border-radius: 999px;
        background: rgba(255,255,255,0.08);
        overflow: hidden;
      }

      .progress > span {
        position: absolute;
        inset: 0 auto 0 0;
        width: 70%;
        background: linear-gradient(90deg, var(--primary), var(--accent));
        border-radius: inherit;
      }

      .showcase {
        display: grid;
        grid-template-columns: 1.2fr 0.8fr;
        gap: 20px;
      }

      .feature-panel {
        background: rgba(15, 23, 42, 0.68);
        border: 1px solid var(--line);
        border-radius: 28px;
        overflow: hidden;
      }

      .feature-panel.large {
        display: grid;
        grid-template-columns: 1.2fr 0.8fr;
      }

      .feature-image {
        min-height: 330px;
        background:
          linear-gradient(135deg, rgba(10,12,20,0.2), rgba(10,12,20,0.72)),
          url("https://images.unsplash.com/photo-1524985069026-dd778a71c7b4?auto=format&fit=crop&w=1200&q=80") center/cover no-repeat;
      }

      .feature-copy {
        padding: 28px 26px;
      }

      .feature-copy h3 {
        font-size: clamp(2rem, 2.8vw, 3rem);
        line-height: 1;
        letter-spacing: -0.06em;
        margin: 18px 0 12px;
      }

      .feature-copy p {
        color: var(--muted);
        margin: 0 0 18px;
      }

      .mini-list {
        list-style: none;
        padding: 0;
        margin: 0 0 22px;
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
        background: rgba(52, 211, 153, 0.12);
        border: 1px solid rgba(52,211,153,0.22);
        color: var(--success);
        font-weight: 800;
      }

      .side-stack {
        display: grid;
        gap: 18px;
      }

      .side-box {
        background: rgba(15, 23, 42, 0.7);
        border: 1px solid var(--line);
        border-radius: 24px;
        padding: 20px;
      }

      .side-box h4 {
        margin: 0 0 12px;
        font-size: 1.15rem;
        letter-spacing: -0.04em;
      }

      .small-list {
        display: grid;
        gap: 12px;
      }

      .small-item {
        display: flex;
        align-items: center;
        gap: 12px;
        padding: 6px 0;
      }

      .small-item .dot {
        width: 12px;
        height: 12px;
        border-radius: 50%;
        background: linear-gradient(135deg, var(--primary), var(--accent));
        box-shadow: 0 0 18px rgba(124, 58, 237, 0.5);
      }

      .small-item strong {
        display: block;
        font-size: 0.98rem;
      }

      .small-item span {
        color: var(--muted);
        font-size: 0.76rem;
      }

      .cta-box {
        background: linear-gradient(135deg, rgba(124,58,237,0.12), rgba(34,211,238,0.08));
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 30px;
        padding: 34px 28px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 20px;
      }

      .cta-box h3 {
        font-size: clamp(2rem, 3vw, 3rem);
        line-height: 1;
        letter-spacing: -0.06em;
        margin: 14px 0 10px;
      }

      .cta-box p {
        color: var(--muted);
        margin: 0;
      }

      .footer {
        padding: 22px 0 60px;
      }

      .footer-inner {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 20px;
        border-top: 1px solid rgba(148,163,184,0.08);
        padding-top: 28px;
        color: var(--muted);
      }

      .footer-links {
        display: flex;
        flex-wrap: wrap;
        gap: 18px;
      }

      @media (max-width: 1100px) {
        .media-grid {
          grid-template-columns: repeat(3, minmax(0, 1fr));
        }

        .feature-panel.large {
          grid-template-columns: 1fr;
        }
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
          flex-direction: column;
          align-items: flex-start;
          gap: 16px;
          display: none;
          box-shadow: var(--shadow);
        }

        .nav-links.open {
          display: flex;
        }

        .ham {
          display: flex;
        }

        .nav-actions .btn {
          display: none;
        }

        .showcase,
        .continue-grid {
          grid-template-columns: 1fr;
        }

        .hero-side-panel {
          position: static;
          width: auto;
          margin: 18px 20px 20px;
        }

        .hero-box {
          min-height: auto;
        }
      }

      @media (max-width: 720px) {
        .media-grid {
          grid-template-columns: repeat(2, minmax(0, 1fr));
        }

        .section-head {
          flex-direction: column;
          align-items: flex-start;
        }

        .hero-content {
          width: calc(100% - 30px);
          padding: 38px 18px 18px;
        }

        .hero-actions {
          flex-direction: column;
          align-items: stretch;
        }

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
        .media-grid {
          grid-template-columns: 1fr;
        }

        .hero-meta {
          flex-wrap: wrap;
        }
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
          <a href="#shows">Shows</a>
          <a href="#trending">Trending</a>
          <a href="#my-list">My List</a>
        </nav>

        <div class="nav-actions">
          <span class="search" aria-label="Search">⌕</span>
          <a href="#contact" class="btn btn-secondary">Join Now</a>
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
                <span class="meta-pill">Sci-Fi</span>
                <span class="meta-pill">Drama</span>
                <span class="meta-pill">4K UHD</span>
              </div>

              <h1>The Last Horizon</h1>

              <p>
                After a signal from deep space reveals a hidden civilization, a grieving pilot
                and a rogue scientist must cross a fractured galaxy to stop the Earth from
                collapsing under the weight of its own history.
              </p>

              <div class="hero-actions">
                <a href="#" class="btn btn-primary">▶ Watch Trailer</a>
                <a href="#" class="btn btn-secondary">＋ My List</a>
              </div>

              <div class="hero-stats">
                <div class="stat-box">
                  <span class="label">IMDb</span>
                  <strong>8.9</strong>
                </div>
                <div class="stat-box">
                  <span class="label">Runtime</span>
                  <strong>2h 14m</strong>
                </div>
                <div class="stat-box">
                  <span class="label">Genre</span>
                  <strong>Sci-Fi</strong>
                </div>
              </div>
            </div>

            <div class="hero-side-panel">
              <div class="row">
                <span>New Release</span>
                <span>2026</span>
              </div>

              <div class="movie-title">The Last Horizon</div>

              <div class="tags">
                <span class="tag">Epic</span>
                <span class="tag">Adventure</span>
                <span class="tag">Mind-Bending</span>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section id="trending" class="section">
        <div class="container">
          <div class="section-head">
            <div>
              <span class="eyebrow">Trending</span>
              <h2>Movies & shows everyone’s watching.</h2>
            </div>
            <div class="chip-row">
              <span class="chip active">All</span>
              <span class="chip">Movies</span>
              <span class="chip">Shows</span>
              <span class="chip">New</span>
              <span class="chip">Top Rated</span>
            </div>
          </div>

          <div class="media-grid">
            <article class="card">
              <div class="poster">
                <img src="https://images.unsplash.com/photo-1513106580091-1d82408b8cd6?auto=format&fit=crop&w=800&q=80" alt="Movie poster" />
              </div>
              <div class="card-content">
                <div class="rating-row">
                  <span class="rating">8.7</span>
                  <span class="duration">2h 06m</span>
                </div>
                <h3 class="card-title">Midnight Echo</h3>
                <div class="sub">Action / Mystery</div>
              </div>
            </article>

            <article class="card">
              <div class="poster">
                <img src="https://images.unsplash.com/photo-1516280440614-37939bbacd81?auto=format&fit=crop&w=800&q=80" alt="Show poster" />
              </div>
              <div class="card-content">
                <div class="rating-row">
                  <span class="rating">9.1</span>
                  <span class="duration">8 Episodes</span>
                </div>
                <h3 class="card-title">Glass Harbor</h3>
                <div class="sub">Drama / Thriller</div>
              </div>
            </article>

            <article class="card">
              <div class="poster">
                <img src="https://images.unsplash.com/photo-1504384308090-c894fdcc538d?auto=format&fit=crop&w=800&q=80" alt="Movie poster" />
              </div>
              <div class="card-content">
                <div class="rating-row">
                  <span class="rating">8.4</span>
                  <span class="duration">1h 49m</span>
                </div>
                <h3 class="card-title">City of Ash</h3>
                <div class="sub">Crime / Neo-noir</div>
              </div>
            </article>

            <article class="card">
              <div class="poster">
                <img src="https://images.unsplash.com/photo-1522869635100-9f4c5e86aa37?auto=format&fit=crop&w=800&q=80" alt="Show poster" />
              </div>
              <div class="card-content">
                <div class="rating-row">
                  <span class="rating">9.3</span>
                  <span class="duration">10 Episodes</span>
                </div>
                <h3 class="card-title">Velvet Rune</h3>
                <div class="sub">Fantasy / Adventure</div>
              </div>
            </article>

            <article class="card">
              <div class="poster">
                <img src="https://images.unsplash.com/photo-1517602302552-471fe67acf66?auto=format&fit=crop&w=800&q=80" alt="Movie poster" />
              </div>
              <div class="card-content">
                <div class="rating-row">
                  <span class="rating">8.8</span>
                  <span class="duration">2h 29m</span>
                </div>
                <h3 class="card-title">Night Signal</h3>
                <div class="sub">Sci-Fi / Mystery</div>
              </div>
            </article>
          </div>
        </div>
      </section>

      <section id="movies" class="section">
        <div class="container">
          <div class="section-head">
            <div>
              <span class="eyebrow">Movies</span>
              <h2>New cinematic picks.</h2>
            </div>
            <p>
              Bold stories, immersive visuals, and unforgettable performances — all in one place.
            </p>
          </div>

          <div class="media-grid">
            <article class="card">
              <div class="poster">
                <img src="https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?auto=format&fit=crop&w=800&q=80" alt="Movie poster" />
              </div>
              <div class="card-content">
                <div class="rating-row">
                  <span class="rating">8.6</span>
                  <span class="duration">1h 58m</span>
                </div>
                <h3 class="card-title">Iron Tide</h3>
                <div class="sub">Action / Thriller</div>
              </div>
            </article>

            <article class="card">
              <div class="poster">
                <img src="https://images.unsplash.com/photo-1497032628192-86f99bcd76bc?auto=format&fit=crop&w=800&q=80" alt="Movie poster" />
              </div>
              <div class="card-content">
                <div class="rating-row">
                  <span class="rating">8.5</span>
                  <span class="duration">2h 12m</span>
                </div>
                <h3 class="card-title">Black Creek</h3>
                <div class="sub">Western / Drama</div>
              </div>
            </article>

            <article class="card">
              <div class="poster">
                <img src="https://images.unsplash.com/photo-1500530855697-b586d89ba3ee?auto=format&fit=crop&w=800&q=80" alt="Movie poster" />
              </div>
              <div class="card-content">
                <div class="rating-row">
                  <span class="rating">8.9</span>
                  <span class="duration">2h 23m</span>
                </div>
                <h3 class="card-title">Winter Phantasm</h3>
                <div class="sub">Drama / Romance</div>
              </div>
            </article>

            <article class="card">
              <div class="poster">
                <img src="https://images.unsplash.com/photo-1516979187457-637abb4f9353?auto=format&fit=crop&w=800&q=80" alt="Movie poster" />
              </div>
              <div class="card-content">
                <div class="rating-row">
                  <span class="rating">8.8</span>
                  <span class="duration">1h 46m</span>
                </div>
                <h3 class="card-title">Breakwater</h3>
                <div class="sub">Adventure</div>
              </div>
            </article>

            <article class="card">
              <div class="poster">
                <img src="https://images.unsplash.com/photo-1516035069371-29a1b244cc32?auto=format&fit=crop&w=800&q=80" alt="Movie poster" />
              </div>
              <div class="card-content">
                <div class="rating-row">
                  <span class="rating">8.7</span>
                  <span class="duration">2h 02m</span>
                </div>
                <h3 class="card-title">Dusk Parade</h3>
                <div class="sub">Crime / Action</div>
              </div>
            </article>
          </div>
        </div>
      </section>

      <section id="shows" class="section">
        <div class="container">
          <div class="section-head">
            <div>
              <span class="eyebrow">Shows</span>
              <h2>Binge-worthy series to dive into.</h2>
            </div>
            <p>
              Discover stories built for late-night marathons, world-building, and emotional payoff.
            </p>
          </div>

          <div class="media-grid">
            <article class="card">
              <div class="poster">
                <img src="https://images.unsplash.com/photo-1522202176988-66273c2fd55f?auto=format&fit=crop&w=800&q=80" alt="Show poster" />
              </div>
              <div class="card-content">
                <div class="rating-row">
                  <span class="rating">9.2</span>
                  <span class="duration">12 Episodes</span>
                </div>
                <h3 class="card-title">Northfall</h3>
                <div class="sub">Drama / Political</div>
              </div>
            </article>

            <article class="card">
              <div class="poster">
                <img src="https://images.unsplash.com/photo-1519345182560-3f2917c472ef?auto=format&fit=crop&w=800&q=80" alt="Show poster" />
              </div>
              <div class="card-content">
                <div class="rating-row">
                  <span class="rating">9.0</span>
                  <span class="duration">8 Episodes</span>
                </div>
                <h3 class="card-title">Tide Theory</h3>
                <div class="sub">Sci-Fi / Mystery</div>
              </div>
            </article>

            <article class="card">
              <div class="poster">
                <img src="https://images.unsplash.com/photo-1524504388940-b1c1722653e1?auto=format&fit=crop&w=800&q=80" alt="Show poster" />
              </div>
              <div class="card-content">
                <div class="rating-row">
                  <span class="rating">8.9</span>
                  <span class="duration">10 Episodes</span>
                </div>
                <h3 class="card-title">Fable House</h3>
                <div class="sub">Fantasy / Thriller</div>
              </div>
            </article>

            <article class="card">
              <div class="poster">
                <img src="https://images.unsplash.com/photo-1529156069898-49953e39b3ac?auto=format&fit=crop&w=800&q=80" alt="Show poster" />
              </div>
              <div class="card-content">
                <div class="rating-row">
                  <span class="rating">9.1</span>
                  <span class="duration">6 Episodes</span>
                </div>
                <h3 class="card-title">Circuit Bloom</h3>
                <div class="sub">Tech / Drama</div>
              </div>
            </article>

            <article class="card">
              <div class="poster">
                <img src="https://images.unsplash.com/photo-1415201364774-f6f0bb35f28f?auto=format&fit=crop&w=800&q=80" alt="Show poster" />
              </div>
              <div class="card-content">
                <div class="rating-row">
                  <span class="rating">8.7</span>
                  <span class="duration">7 Episodes</span>
                </div>
                <h3 class="card-title">The Hollowing</h3>
                <div class="sub">Suspense / Horror</div>
              </div>
            </article>
          </div>
        </div>
      </section>

      <section id="my-list" class="section">
        <div class="container">
          <div class="section-head">
            <div>
              <span class="eyebrow">Continue Watching</span>
              <h2>Pick up right where you left off.</h2>
            </div>
            <p>
              Your queue stays organized with hand-picked titles and progress tracked automatically.
            </p>
          </div>

          <div class="continue-grid">
            <article class="episode-card">
              <div class="thumb">
                <img src="https://images.unsplash.com/photo-1505259824754-80d4c6a858d4?auto=format&fit=crop&w=800&q=80" alt="episode thumbnail" />
              </div>
              <div class="episode-info">
                <div class="episode-top">
                  <strong>Echoes of Dawn</strong>
                  <span class="duration">42 min</span>
                </div>
                <div class="progress"><span></span></div>
              </div>
            </article>

            <article class="episode-card">
              <div class="thumb">
                <img src="https://images.unsplash.com/photo-1521295121783-8a321d551ad2?auto=format&fit=crop&w=800&q=80" alt="episode thumbnail" />
              </div>
              <div class="episode-info">
                <div class="episode-top">
                  <strong>Signal Break</strong>
                  <span class="duration">52 min</span>
                </div>
                <div class="progress"><span style="width: 68%;"></span></div>
              </div>
            </article>

            <article class="episode-card">
              <div class="thumb">
                <img src="https://images.unsplash.com/photo-1516280440614-37939bbacd81?auto=format&fit=crop&w=800&q=80" alt="episode thumbnail" />
              </div>
              <div class="episode-info">
                <div class="episode-top">
                  <strong>Glass Harbor</strong>
                  <span class="duration">48 min</span>
                </div>
                <div class="progress"><span style="width: 81%;"></span></div>
              </div>
            </article>
          </div>
        </div>
      </section>

      <section class="section">
        <div class="container">
          <div class="showcase">
            <div class="feature-panel large">
              <div class="feature-image"></div>
              <div class="feature-copy">
                <span class="eyebrow">Featured</span>
                <h3>Discover stories that live beyond the screen.</h3>
                <p>
                  Achroma curates premium entertainment with cinematic visuals, immersive stories,
                  and hand-selected titles for every mood.
                </p>

                <ul class="mini-list">
                  <li>Curated collections by genre</li>
                  <li>Fresh releases every week</li>
                  <li>Top-rated series and films</li>
                </ul>

                <a href="#contact" class="btn btn-primary">Explore Collection</a>
              </div>
            </div>

            <div class="side-stack">
              <div class="side-box">
                <h4>Popular this week</h4>
                <div class="small-list">
                  <div class="small-item">
                    <span class="dot"></span>
                    <div>
                      <strong>Red Horizon</strong>
                      <span>Thriller • 8.9</span>
                    </div>
                  </div>
                  <div class="small-item">
                    <span class="dot"></span>
                    <div>
                      <strong>Silent Orbit</strong>
                      <span>Sci‑Fi • 9.3</span>
                    </div>
                  </div>
                  <div class="small-item">
                    <span class="dot"></span>
                    <div>
                      <strong>Moonline</strong>
                      <span>Drama • 8.8</span>
                    </div>
                  </div>
                </div>
              </div>

              <div class="side-box">
                <h4>Top Genres</h4>
                <div class="chip-row">
                  <span class="chip active">Action</span>
                  <span class="chip">Drama</span>
                  <span class="chip">Sci-Fi</span>
                  <span class="chip">Mystery</span>
                  <span class="chip">Thriller</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section id="contact" class="section">
        <div class="container">
          <div class="cta-box">
            <div>
              <span class="eyebrow">Stay in the loop</span>
              <h3>Find your next obsession.</h3>
              <p>From epic movies to binge-worthy series, Achroma keeps the best stories front and center.</p>
            </div>

            <div style="display:flex; gap:12px; flex-wrap:wrap;">
              <a href="mailto:hello@achroma.tv" class="btn btn-primary">hello@achroma.tv</a>
              <a href="#" class="btn btn-secondary">Get updates</a>
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
          <a href="#shows">Shows</a>
          <a href="#trending">Trending</a>
          <a href="#contact">Contact</a>
        </div>
      </div>
    </footer>

    <script>
      const menuBtn = document.getElementById("menuBtn");
      const navLinks = document.getElementById("navLinks");

      menuBtn.addEventListener("click", () => {
        navLinks.classList.toggle("open");
      });

      navLinks.querySelectorAll("a").forEach(link => {
        link.addEventListener("click", () => navLinks.classList.remove("open"));
      });
    </script>
  </body>
</html>
