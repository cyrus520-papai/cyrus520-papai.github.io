<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>SocialStream</title>
    <style>
      :root {
        --bg: #070d18;
        --bg-2: #101a2b;
        --panel: #111b2b;
        --panel-2: #17263d;
        --panel-3: #1f2f46;
        --soft: #edf3ff;
        --muted: #aab8d1;
        --text: #f7f9ff;
        --gold: #f7c96a;
        --gold-2: #ef8d3d;
        --blue: #60a5fa;
        --purple: #8b5cf6;
        --green: #3ad49d;
        --red: #f87171;
        --shadow: rgba(0, 0, 0, 0.38);
      }

      * {
        box-sizing: border-box;
      }

      html, body {
        margin: 0;
        min-height: 100vh;
        font-family: Arial, Helvetica, sans-serif;
        background:
          radial-gradient(circle at top, rgba(96,165,250,0.12), transparent 26%),
          linear-gradient(180deg, var(--bg), var(--bg-2));
        color: var(--text);
      }

      body {
        display: grid;
        place-items: center;
      }

      button, input {
        font: inherit;
      }

      .app {
        width: min(1500px, 96vw);
        min-height: 92vh;
        display: grid;
        grid-template-rows: auto 1fr;
        background: rgba(8, 12, 20, 0.92);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 24px;
        overflow: hidden;
        box-shadow: 0 32px 70px var(--shadow);
      }

      .topbar {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 18px;
        padding: 18px 22px;
        background: rgba(15, 21, 31, 0.92);
        border-bottom: 1px solid rgba(255,255,255,0.08);
      }

      .brand-wrap {
        display: flex;
        align-items: center;
        gap: 12px;
      }

      .brand-mark {
        width: 38px;
        height: 38px;
        display: grid;
        place-items: center;
        background: linear-gradient(135deg, var(--gold), var(--gold-2));
        color: #111827;
        border-radius: 12px;
        font-weight: 900;
      }

      .brand-name {
        font-size: 1.15rem;
        font-weight: 800;
        letter-spacing: 0.08em;
        text-transform: uppercase;
      }

      .nav {
        display: flex;
        gap: 10px;
        flex-wrap: wrap;
      }

      .tab {
        border: 1px solid rgba(255,255,255,0.08);
        background: rgba(255,255,255,0.03);
        color: var(--muted);
        border-radius: 999px;
        padding: 8px 14px;
        cursor: pointer;
        transition: all 0.12s ease;
      }

      .tab:hover {
        border-color: rgba(255,255,255,0.16);
      }

      .tab.active {
        background: linear-gradient(135deg, rgba(96,165,250,0.2), rgba(139,92,246,0.15));
        border-color: rgba(96,165,250,0.42);
        color: var(--text);
      }

      .user-pill {
        background: rgba(255,255,255,0.04);
        border: 1px solid rgba(255,255,255,0.08);
        padding: 9px 12px;
        border-radius: 999px;
        color: var(--soft);
      }

      .main {
        display: grid;
        grid-template-columns: minmax(0, 1.75fr) minmax(300px, 0.94fr);
        min-height: 0;
      }

      .content {
        padding: 22px;
        background: linear-gradient(180deg, rgba(17,24,39,0.9), rgba(8,12,17,0.96));
      }

      .section {
        display: none;
        min-height: 760px;
      }

      .section.active {
        display: block;
      }

      .browser-panel {
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 20px;
        overflow: hidden;
      }

      .browser-top {
        display: flex;
        align-items: center;
        gap: 12px;
        padding: 12px 14px;
        background: rgba(255,255,255,0.03);
        border-bottom: 1px solid rgba(255,255,255,0.07);
      }

      .traffic {
        display: flex;
        gap: 8px;
      }

      .dot {
        width: 12px;
        height: 12px;
        border-radius: 50%;
      }

      .dot.red { background: #ef4444; }
      .dot.yellow { background: #fbbf24; }
      .dot.green { background: #34d399; }

      .address-bar {
        flex: 1;
        border-radius: 999px;
        padding: 9px 14px;
        border: 1px solid rgba(255,255,255,0.08);
        background: rgba(0,0,0,0.18);
        color: var(--muted);
      }

      .browser-body {
        display: grid;
        grid-template-columns: 180px 1fr;
        min-height: 760px;
      }

      .side-nav {
        background: rgba(255,255,255,0.015);
        border-right: 1px solid rgba(255,255,255,0.06);
        padding: 16px 12px;
      }

      .side-nav-item {
        display: block;
        text-decoration: none;
        border: 1px solid rgba(255,255,255,0.05);
        background: rgba(255,255,255,0.02);
        color: var(--muted);
        border-radius: 12px;
        padding: 10px 12px;
        margin-bottom: 10px;
      }

      .side-nav-item.active {
        background: rgba(96,165,250,0.12);
        border-color: rgba(96,165,250,0.35);
        color: var(--text);
      }

      .browser-page {
        padding: 18px;
      }

      .page-hero {
        min-height: 220px;
        border-radius: 18px;
        padding: 24px;
        display: flex;
        align-items: flex-end;
        background:
          linear-gradient(135deg, rgba(17,24,39,0.8), rgba(15,23,42,0.74)),
          url("https://images.unsplash.com/photo-1524985069026-dd778a71c7b4?auto=format&fit=crop&w=1400&q=80") center/cover no-repeat;
        border: 1px solid rgba(255,255,255,0.08);
      }

      .page-hero h2 {
        margin: 0;
        font-size: clamp(2rem, 3vw, 3.4rem);
        letter-spacing: -0.05em;
      }

      .site-grid {
        margin-top: 18px;
        display: grid;
        grid-template-columns: repeat(3, minmax(0, 1fr));
        gap: 16px;
      }

      .site-card {
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 16px;
        overflow: hidden;
      }

      .site-card .image {
        aspect-ratio: 16 / 9;
        background-size: cover;
        background-position: center;
      }

      .site-card .body {
        padding: 12px 12px 14px;
      }

      .site-card h4 {
        margin: 0 0 7px;
        font-size: 1rem;
      }

      .site-card p {
        margin: 0;
        color: var(--muted);
        font-size: 0.86rem;
      }

      .movie-layout {
        display: grid;
        gap: 18px;
      }

      .featured-banner {
        position: relative;
        height: 320px;
        border-radius: 22px;
        overflow: hidden;
        background:
          linear-gradient(90deg, rgba(0,0,0,0.72), rgba(0,0,0,0.18)),
          url("https://images.unsplash.com/photo-1536440136628-849c177e76a1?auto=format&fit=crop&w=1600&q=80") center/cover no-repeat;
        border: 1px solid rgba(255,255,255,0.08);
      }

      .featured-content {
        position: absolute;
        left: 28px;
        right: 28px;
        bottom: 24px;
      }

      .eyebrow {
        display: inline-block;
        background: rgba(255,255,255,0.08);
        border: 1px solid rgba(255,255,255,0.12);
        border-radius: 999px;
        padding: 7px 12px;
        font-size: 0.7rem;
        text-transform: uppercase;
        letter-spacing: 0.08em;
      }

      .featured-content h2 {
        margin: 14px 0 10px;
        font-size: clamp(2rem, 4vw, 4.2rem);
        line-height: 0.96;
        letter-spacing: -0.04em;
      }

      .meta-row {
        display: flex;
        gap: 14px;
        flex-wrap: wrap;
        color: var(--soft);
        font-size: 0.9rem;
      }

      .action-row {
        margin-top: 18px;
        display: flex;
        flex-wrap: wrap;
        gap: 12px;
      }

      .primary-btn, .secondary-btn, .tiny-btn {
        border: none;
        border-radius: 999px;
        padding: 11px 16px;
        font-weight: 800;
        cursor: pointer;
      }

      .primary-btn {
        background: linear-gradient(135deg, var(--gold), var(--gold-2));
        color: #111827;
      }

      .secondary-btn {
        background: rgba(255,255,255,0.08);
        border: 1px solid rgba(255,255,255,0.12);
        color: var(--text);
      }

      .rows {
        display: grid;
        gap: 16px;
      }

      .row-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
      }

      .row-header h3 {
        margin: 0;
        font-size: 0.95rem;
        text-transform: uppercase;
        letter-spacing: 0.08em;
        color: var(--soft);
      }

      .more {
        color: var(--gold);
        font-weight: 700;
      }

      .movie-cards {
        display: grid;
        grid-template-columns: repeat(4, minmax(0, 1fr));
        gap: 18px;
      }

      .movie-card {
        background: linear-gradient(180deg, rgba(22,33,50,0.9), rgba(10,15,25,0.95));
        border: 1px solid rgba(255,255,255,0.06);
        border-radius: 18px;
        overflow: hidden;
        cursor: pointer;
        transition: transform 0.15s ease, border-color 0.15s ease;
      }

      .movie-card:hover {
        transform: translateY(-2px);
        border-color: rgba(96,165,250,0.35);
      }

      .movie-poster {
        position: relative;
        aspect-ratio: 4 / 5.2;
        background-size: cover;
        background-position: center;
      }

      .movie-badge {
        position: absolute;
        top: 10px;
        left: 10px;
        background: rgba(12,18,29,0.78);
        border: 1px solid rgba(255,255,255,0.12);
        border-radius: 999px;
        padding: 6px 8px;
        font-size: 0.7rem;
        font-weight: 700;
      }

      .movie-info {
        padding: 12px;
      }

      .movie-info h4 {
        margin: 0 0 6px;
        font-size: 1rem;
      }

      .movie-info p {
        margin: 0;
        color: var(--muted);
        font-size: 0.82rem;
      }

      .player-card {
        background: rgba(0,0,0,0.22);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 20px;
        overflow: hidden;
      }

      .player-card video {
        display: block;
        width: 100%;
        height: 260px;
        object-fit: cover;
        background: #000;
      }

      .game-card {
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 20px;
        padding: 16px;
      }

      .game-top {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 12px;
        margin-bottom: 12px;
      }

      .game-top h3 {
        margin: 0;
        font-size: 0.95rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        color: var(--soft);
      }

      .score-badge {
        padding: 6px 10px;
        border-radius: 999px;
        background: rgba(247, 201, 106, 0.12);
        border: 1px solid rgba(247, 201, 106, 0.35);
        color: var(--gold);
        font-size: 0.75rem;
        font-weight: 700;
      }

      .mini-scene {
        position: relative;
        width: 100%;
        height: 320px;
        background:
          linear-gradient(180deg, rgba(96,165,250,0.12), rgba(0,0,0,0.2)),
          linear-gradient(180deg, #14263f 0%, #0f1725 36%, #111827 100%);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 18px;
        overflow: hidden;
      }

      .mini-scene::before {
        content: "";
        position: absolute;
        inset: 0;
        background:
          linear-gradient(transparent 0 76%, rgba(7,11,20,0.88) 76% 100%),
          linear-gradient(90deg, rgba(255,255,255,0.02) 0 5%, transparent 5% 100%);
        pointer-events: none;
      }

      .findable {
        position: absolute;
        width: 42px;
        height: 42px;
        transform: translate(-50%, -50%);
        border: none;
        background: transparent;
        padding: 0;
        cursor: pointer;
        user-select: none;
        transition: transform 0.12s ease, filter 0.12s ease;
      }

      .findable:hover {
        transform: translate(-50%, -50%) scale(1.08);
      }

      .findable.hidden {
        opacity: 0;
        pointer-events: none;
      }

      .findable .sprite {
        width: 100%;
        height: 100%;
        display: grid;
        place-items: center;
        border-radius: 12px;
        background: rgba(255,255,255,0.08);
        border: 2px solid rgba(255,255,255,0.18);
        box-shadow: 0 8px 16px rgba(0,0,0,0.25);
        font-size: 1.6rem;
      }

      .findable.found .sprite {
        background: rgba(58,212,157,0.18);
        border-color: rgba(58,212,157,0.9);
        box-shadow: 0 0 18px rgba(58,212,157,0.3);
      }

      .game-footer {
        margin-top: 12px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 12px;
      }

      .game-hint {
        color: var(--muted);
        font-size: 0.85rem;
      }

      .tiny-btn {
        background: rgba(255,255,255,0.06);
        border: 1px solid rgba(255,255,255,0.08);
        color: var(--text);
      }

      .tiny-btn.primary {
        background: linear-gradient(135deg, var(--gold), var(--gold-2));
        color: #111827;
        border: none;
      }

      .chat-panel {
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 20px;
        overflow: hidden;
      }

      .chat-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 14px 16px;
        border-bottom: 1px solid rgba(255,255,255,0.08);
      }

      .chat-header h3 {
        margin: 0;
        font-size: 0.9rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        color: var(--soft);
      }

      .online-pill {
        background: rgba(58,212,157,0.12);
        border: 1px solid rgba(58,212,157,0.38);
        color: var(--green);
        border-radius: 999px;
        padding: 6px 10px;
        font-size: 0.75rem;
        font-weight: 700;
      }

      .chat-box {
        display: flex;
        flex-direction: column;
        gap: 12px;
        min-height: 360px;
        padding: 16px;
        background: rgba(0,0,0,0.06);
      }

      .msg {
        max-width: 85%;
        padding: 10px 12px;
        border-radius: 14px;
        line-height: 1.35;
        font-size: 0.9rem;
      }

      .msg.self {
        align-self: flex-end;
        background: linear-gradient(135deg, rgba(96,165,250,0.34), rgba(139,92,246,0.25));
        border: 1px solid rgba(96,165,250,0.35);
      }

      .msg.other {
        align-self: flex-start;
        background: rgba(255,255,255,0.04);
        border: 1px solid rgba(255,255,255,0.06);
        color: var(--soft);
      }

      .composer {
        display: flex;
        gap: 10px;
        padding: 14px 16px 16px;
        border-top: 1px solid rgba(255,255,255,0.08);
        background: rgba(255,255,255,0.02);
      }

      .composer input {
        flex: 1;
        background: rgba(255,255,255,0.04);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 999px;
        color: var(--text);
        padding: 11px 14px;
      }

      .voice-panel {
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 20px;
        padding: 18px 16px;
      }

      .voice-head {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 16px;
      }

      .voice-head h3 {
        margin: 0;
        font-size: 0.94rem;
        text-transform: uppercase;
        letter-spacing: 0.08em;
        color: var(--soft);
      }

      .voice-users {
        display: grid;
        gap: 10px;
      }

      .voice-user {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 12px;
        padding: 10px 12px;
        border-radius: 14px;
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
      }

      .user-name {
        display: flex;
        align-items: center;
        gap: 10px;
      }

      .avatar {
        width: 30px;
        height: 30px;
        border-radius: 50%;
        display: grid;
        place-items: center;
        font-size: 0.74rem;
        font-weight: 800;
        color: #111827;
      }

      .avatar.a1 { background: linear-gradient(135deg, #60a5fa, #93c5fd); }
      .avatar.a2 { background: linear-gradient(135deg, #f9a8d4, #fca5a5); }
      .avatar.a3 { background: linear-gradient(135deg, #fbbf24, #f59e0b); }
      .avatar.a4 { background: linear-gradient(135deg, #4ade80, #34d399); }

      .status {
        width: 10px;
        height: 10px;
        border-radius: 50%;
        background: var(--green);
        box-shadow: 0 0 10px rgba(58,212,157,0.8);
      }

      .status.idle {
        background: #fbbf24;
      }

      .status.muted {
        background: var(--red);
      }

      .voice-actions {
        display: flex;
        gap: 8px;
        flex-wrap: wrap;
        margin-top: 16px;
      }

      .sidebar-stack {
        display: grid;
        gap: 18px;
        padding: 18px;
        background: linear-gradient(180deg, rgba(23,34,53,0.9), rgba(9,14,22,0.92));
        border-left: 1px solid rgba(255,255,255,0.08);
      }

      @media (max-width: 1100px) {
        .main {
          grid-template-columns: 1fr;
        }

        .sidebar-stack {
          border-left: none;
          border-top: 1px solid rgba(255,255,255,0.08);
        }
      }

      @media (max-width: 900px) {
        .browser-body {
          grid-template-columns: 1fr;
        }

        .side-nav {
          border-right: none;
          border-bottom: 1px solid rgba(255,255,255,0.06);
        }

        .movie-cards {
          grid-template-columns: repeat(2, minmax(0, 1fr));
        }
      }

      @media (max-width: 620px) {
        .topbar {
          flex-direction: column;
          align-items: flex-start;
        }

        .nav {
          width: 100%;
        }

        .movie-cards, .site-grid {
          grid-template-columns: 1fr;
        }
      }
    </style>
  </head>
  <body>
    <div class="app">
      <header class="topbar">
        <div class="brand-wrap">
          <div class="brand-mark">S</div>
          <div class="brand-name">SocialStream</div>
        </div>

        <nav class="nav" aria-label="main tabs">
          <button class="tab active" type="button" data-section="browser">Browser</button>
          <button class="tab" type="button" data-section="games">Games</button>
          <button class="tab" type="button" data-section="movies">Movies</button>
          <button class="tab" type="button" data-section="chat">Chat</button>
          <button class="tab" type="button" data-section="voice">Voice</button>
        </nav>

        <div class="user-pill">Guest User</div>
      </header>

      <div class="main">
        <main class="content">
          <section class="section active" id="browser">
            <div class="browser-panel">
              <div class="browser-top">
                <div class="traffic">
                  <div class="dot red"></div>
                  <div class="dot yellow"></div>
                  <div class="dot green"></div>
                </div>
                <div class="address-bar">socialstream.app/explore</div>
              </div>

              <div class="browser-body">
                <aside class="side-nav">
                  <a href="#" class="side-nav-item active">Explore</a>
                  <a href="#" class="side-nav-item">Live</a>
                  <a href="#" class="side-nav-item">Movies</a>
                  <a href="#" class="side-nav-item">Games</a>
                  <a href="#" class="side-nav-item">Friends</a>
                  <a href="#" class="side-nav-item">Saved</a>
                </aside>

                <div class="browser-page">
                  <div class="page-hero">
                    <h2>Discover the internet together.</h2>
                  </div>

                  <div class="site-grid">
                    <div class="site-card">
                      <div class="image" style="background-image:url('https://images.unsplash.com/photo-1517604931442-7e0c8ed2963c?auto=format&fit=crop&w=1200&q=80')"></div>
                      <div class="body">
                        <h4>Movie Night</h4>
                        <p>Watch premieres with your friends.</p>
                      </div>
                    </div>

                    <div class="site-card">
                      <div class="image" style="background-image:url('https://images.unsplash.com/photo-1493711662062-fa541adb3fc8?auto=format&fit=crop&w=1200&q=80')"></div>
                      <div class="body">
                        <h4>Arcade Lounge</h4>
                        <p>Play and compete in quick games.</p>
                      </div>
                    </div>

                    <div class="site-card">
                      <div class="image" style="background-image:url('https://images.unsplash.com/photo-1524985069026-dd778a71c7b4?auto=format&fit=crop&w=1200&q=80')"></div>
                      <div class="body">
                        <h4>Community Rooms</h4>
                        <p>Join public or private social spaces.</p>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </section>

          <section class="section" id="games">
            <div class="game-card">
              <div class="game-top">
                <h3>Mini Game</h3>
                <div class="score-badge" id="gameScore">0 / 6</div>
              </div>

              <div class="mini-scene" id="miniScene"></div>

              <div class="game-footer">
                <div class="game-hint" id="gameHint">Find the movie clues.</div>
                <button type="button" class="tiny-btn primary" id="gameRestart">Restart</button>
              </div>
            </div>
          </section>

          <section class="section" id="movies">
            <div class="movie-layout">
              <div class="featured-banner">
                <div class="featured-content">
                  <div class="eyebrow">Featured Premiere</div>
                  <h2 id="featuredTitle">Night Drift</h2>
                  <div class="meta-row">
                    <span>2026</span>
                    <span>Drama / Sci‑Fi</span>
                    <span>2h 12m</span>
                    <span>4.9/5</span>
                  </div>

                  <div class="action-row">
                    <button type="button" class="primary-btn" id="watchNowBtn">Watch Now</button>
                    <button type="button" class="secondary-btn">+ My List</button>
                  </div>
                </div>
              </div>

              <div class="rows">
                <div class="row-header">
                  <h3>Trending</h3>
                  <div class="more">View all</div>
                </div>

                <div class="movie-cards" id="movieCards"></div>
              </div>

              <div class="player-card">
                <video id="movieVideo" controls playsinline poster="https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?auto=format&fit=crop&w=1200&q=80">
                  <source src="https://interactive-examples.mdn.mozilla.net/media/cc0-videos/flower.mp4" type="video/mp4">
                </video>
              </div>
            </div>
          </section>

          <section class="section" id="chat">
            <div class="chat-panel">
              <div class="chat-header">
                <h3>Community Chat</h3>
                <div class="online-pill">24 online</div>
              </div>

              <div class="chat-box" id="chatBox">
                <div class="msg other">Hey everyone! Anyone watching the new movie tonight?</div>
                <div class="msg self">I’m in. Let’s do a group watch.</div>
                <div class="msg other">I’ve got the room ready. You can join anytime.</div>
                <div class="msg self">Perfect. I’ll bring snacks.</div>
              </div>

              <div class="composer">
                <input id="chatInput" type="text" placeholder="Type a message..." />
                <button id="sendMessage" type="button" class="primary-btn">Send</button>
              </div>
            </div>
          </section>

          <section class="section" id="voice">
            <div class="voice-panel">
              <div class="voice-head">
                <h3>Voice Chat</h3>
                <div class="online-pill">Live</div>
              </div>

              <div class="voice-users">
                <div class="voice-user">
                  <div class="user-name">
                    <div class="avatar a1">A</div>
                    <div>
                      <div>Alice</div>
                      <div style="font-size:0.75rem;color:var(--muted);">Hosting room</div>
                    </div>
                  </div>
                  <div class="status"></div>
                </div>

                <div class="voice-user">
                  <div class="user-name">
                    <div class="avatar a2">B</div>
                    <div>
                      <div>Ben</div>
                      <div style="font-size:0.75rem;color:var(--muted);">Talking</div>
                    </div>
                  </div>
                  <div class="status"></div>
                </div>

                <div class="voice-user">
                  <div class="user-name">
                    <div class="avatar a3">C</div>
                    <div>
                      <div>Chloe</div>
                      <div style="font-size:0.75rem;color:var(--muted);">Muted</div>
                    </div>
                  </div>
                  <div class="status muted"></div>
                </div>

                <div class="voice-user">
                  <div class="user-name">
                    <div class="avatar a4">D</div>
                    <div>
                      <div>Dan</div>
                      <div style="font-size:0.75rem;color:var(--muted);">Away</div>
                    </div>
                  </div>
                  <div class="status idle"></div>
                </div>
              </div>

              <div class="voice-actions">
                <button class="tiny-btn primary" type="button">Join Voice</button>
                <button class="tiny-btn" type="button">Mute</button>
                <button class="tiny-btn" type="button">Settings</button>
              </div>
            </div>
          </section>
        </main>

        <aside class="sidebar-stack">
          <div class="chat-panel">
            <div class="chat-header">
              <h3>Room Feed</h3>
              <div class="online-pill">Live</div>
            </div>

            <div class="chat-box" style="min-height:220px;">
              <div class="msg other">The new trailer dropped. Check it out.</div>
              <div class="msg self">I saw it. The visuals are amazing.</div>
              <div class="msg other">Anyone want to play a quick game after?</div>
              <div class="msg self">Absolutely.</div>
            </div>
          </div>

          <div class="voice-panel">
            <div class="voice-head">
              <h3>Voice Room</h3>
              <div class="online-pill">4 in call</div>
            </div>

            <div class="voice-users">
              <div class="voice-user">
                <div class="user-name">
                  <div class="avatar a1">A</div>
                  <div>Alice</div>
                </div>
                <div class="status"></div>
              </div>

              <div class="voice-user">
                <div class="user-name">
                  <div class="avatar a2">B</div>
                  <div>Ben</div>
                </div>
                <div class="status"></div>
              </div>

              <div class="voice-user">
                <div class="user-name">
                  <div class="avatar a3">C</div>
                  <div>Chloe</div>
                </div>
                <div class="status muted"></div>
              </div>
            </div>

            <div class="voice-actions">
              <button class="tiny-btn primary" type="button">Join</button>
              <button class="tiny-btn" type="button">Mute</button>
            </div>
          </div>
        </aside>
      </div>
    </div>

    <script>
      const tabs = document.querySelectorAll(".tab");
      const sections = document.querySelectorAll(".section");

      tabs.forEach((tab) => {
        tab.addEventListener("click", () => {
          tabs.forEach(btn => btn.classList.remove("active"));
          sections.forEach(sec => sec.classList.remove("active"));

          tab.classList.add("active");
          document.getElementById(tab.dataset.section).classList.add("active");
        });
      });

      const movies = [
        {
          title: "Night Drift",
          tag: "Movie",
          year: "2026",
          rating: "4.9",
          poster: "https://images.unsplash.com/photo-1517604931442-7e0c8ed2963c?auto=format&fit=crop&w=1000&q=80"
        },
        {
          title: "Skyline Echo",
          tag: "Series",
          year: "2025",
          rating: "4.8",
          poster: "https://images.unsplash.com/photo-1504384308090-c894fdcc538d?auto=format&fit=crop&w=1000&q=80"
        },
        {
          title: "Pixel Harbor",
          tag: "Movie",
          year: "2024",
          rating: "4.7",
          poster: "https://images.unsplash.com/photo-1513106580091-1d82408b8cd6?auto=format&fit=crop&w=1000&q=80"
        },
        {
          title: "Signal Zero",
          tag: "Series",
          year: "2026",
          rating: "4.9",
          poster: "https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?auto=format&fit=crop&w=1000&q=80"
        }
      ];

      const movieCards = document.getElementById("movieCards");
      const featuredTitle = document.getElementById("featuredTitle");
      const movieVideo = document.getElementById("movieVideo");
      const watchNowBtn = document.getElementById("watchNowBtn");

      function renderMovies() {
        movieCards.innerHTML = "";

        movies.forEach((movie) => {
          const card = document.createElement("div");
          card.className = "movie-card";

          card.innerHTML = `
            <div class="movie-poster" style="background-image:url('${movie.poster}')">
              <div class="movie-badge">${movie.tag}</div>
            </div>
            <div class="movie-info">
              <h4>${movie.title}</h4>
              <p>${movie.year} • ${movie.rating}/5</p>
            </div>
          `;

          card.addEventListener("click", () => {
            featuredTitle.textContent = movie.title;
            movieVideo.play();
          });

          movieCards.appendChild(card);
        });
      }

      renderMovies();

      watchNowBtn.addEventListener("click", () => {
        movieVideo.play();
      });

      const chatInput = document.getElementById("chatInput");
      const chatBox = document.getElementById("chatBox");
      const sendMessage = document.getElementById("sendMessage");

      sendMessage.addEventListener("click", () => {
        const value = chatInput.value.trim();
        if (!value) return;

        const msg = document.createElement("div");
        msg.className = "msg self";
        msg.textContent = value;
        chatBox.appendChild(msg);

        chatInput.value = "";

        const response = document.createElement("div");
        response.className = "msg other";
        response.textContent = "Sounds good! I’ll join the room.";
        chatBox.appendChild(response);

        chatBox.scrollTop = chatBox.scrollHeight;
      });

      chatInput.addEventListener("keydown", (event) => {
        if (event.key === "Enter") {
          sendMessage.click();
        }
      });

      class MiniGame {
        constructor() {
          this.scene = document.getElementById("miniScene");
          this.scoreEl = document.getElementById("gameScore");
          this.hintEl = document.getElementById("gameHint");
          this.restartBtn = document.getElementById("gameRestart");
          this.items = [];
          this.found = 0;
          this.sceneSize = { width: 0, height: 0 };
          this.setup();
        }

        setup() {
          this.bindEvents();
          this.resetSceneSize();
          this.start();
        }

        bindEvents() {
          this.restartBtn.addEventListener("click", () => this.start());
          window.addEventListener("resize", () => this.resetSceneSize());
        }

        resetSceneSize() {
          const rect = this.scene.getBoundingClientRect();
          this.sceneSize.width = rect.width;
          this.sceneSize.height = rect.height;
        }

        start() {
          this.scene.innerHTML = "";
          this.items = [];
          this.found = 0;
          this.hintEl.textContent = "Find the movie clues.";
          this.renderScore();

          const items = [
            { name: "Ticket", emoji: "🎟️" },
            { name: "Popcorn", emoji: "🍿" },
            { name: "Play", emoji: "▶️" },
            { name: "Camera", emoji: "🎥" },
            { name: "Reel", emoji: "🎞️" },
            { name: "Clapperboard", emoji: "🎬" }
          ];

          for (let i = 0; i < items.length; i++) {
            const item = items[i];
            let x = 0;
            let y = 0;
            let tries = 0;

            do {
              x = Math.random() * (this.sceneSize.width - 80) + 40;
              y = Math.random() * (this.sceneSize.height - 80) + 40;
              tries++;
            } while (
              tries < 250 &&
              this.items.some((existing) => {
                const dx = x - existing.x;
                const dy = y - existing.y;
                return Math.hypot(dx, dy) < 72;
              })
            );

            const data = { ...item, x, y, found: false };
            this.items.push(data);
            this.createItem(data);
          }
        }

        createItem(item) {
          const btn = document.createElement("button");
          btn.type = "button";
          btn.className = "findable";
          btn.style.left = `${item.x}px`;
          btn.style.top = `${item.y}px`;
          btn.setAttribute("aria-label", `Find ${item.name}`);

          const sprite = document.createElement("span");
          sprite.className = "sprite";
          sprite.textContent = item.emoji;

          btn.appendChild(sprite);
          btn.addEventListener("click", () => this.onFound(item, btn));
          this.scene.appendChild(btn);
        }

        onFound(item, element) {
          if (item.found) return;

          item.found = true;
          element.classList.add("found");
          element.classList.add("hidden");

          this.found += 1;
          this.renderScore();

          if (this.found === this.items.length) {
            this.hintEl.textContent = "You found them all!";
            this.showOverlay();
          } else {
            this.hintEl.textContent = `Nice! ${this.found} found so far.`;
          }
        }

        renderScore() {
          this.scoreEl.textContent = `${this.found} / ${this.items.length}`;
        }

        showOverlay() {
          const overlay = document.createElement("div");
          overlay.style.position = "absolute";
          overlay.style.inset = "0";
          overlay.style.display = "grid";
          overlay.style.placeItems = "center";
          overlay.style.background = "rgba(0,0,0,0.42)";
          overlay.style.backdropFilter = "blur(2px)";
          overlay.style.fontSize = "clamp(1.3rem, 2vw, 2rem)";
          overlay.style.fontWeight = "800";
          overlay.style.color = "#d1fae5";
          overlay.textContent = "You found all clues!";
          this.scene.appendChild(overlay);
        }
      }

      new MiniGame();
    </script>
  </body>
</html>
