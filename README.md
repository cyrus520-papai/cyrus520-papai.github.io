<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>CinemaWorld Pro</title>
    <style>
      :root {
        --bg: #070b14;
        --bg-2: #101827;
        --panel: #111827;
        --panel-2: #172235;
        --panel-3: #1d2a3c;
        --soft: #e8edf7;
        --muted: #aab7ce;
        --text: #f7f9fc;
        --gold: #f7c96a;
        --gold-2: #ef8f3e;
        --blue: #63a4ff;
        --purple: #7c5fff;
        --green: #3ad49d;
        --danger: #fb7185;
        --shadow: rgba(0, 0, 0, 0.4);
      }

      * {
        box-sizing: border-box;
      }

      html, body {
        margin: 0;
        min-height: 100vh;
        font-family: Arial, Helvetica, sans-serif;
        background:
          radial-gradient(circle at top, rgba(99, 164, 255, 0.12), transparent 30%),
          linear-gradient(180deg, var(--bg), var(--bg-2));
        color: var(--text);
      }

      body {
        display: grid;
        place-items: center;
      }

      button {
        font: inherit;
      }

      .app {
        width: min(1420px, 96vw);
        min-height: 92vh;
        background: rgba(8, 12, 20, 0.9);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 28px;
        overflow: hidden;
        box-shadow: 0 30px 70px var(--shadow);
      }

      .topbar {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 20px;
        padding: 18px 22px;
        background: rgba(17, 24, 39, 0.82);
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
        border-radius: 12px;
        font-weight: 900;
        color: #111827;
        background: linear-gradient(135deg, var(--gold), var(--gold-2));
      }

      .brand {
        font-size: 1.2rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        font-weight: 800;
      }

      .nav {
        display: flex;
        align-items: center;
        gap: 10px;
        flex-wrap: wrap;
      }

      .nav-chip {
        background: rgba(255,255,255,0.04);
        border: 1px solid rgba(255,255,255,0.08);
        color: var(--muted);
        padding: 8px 14px;
        border-radius: 999px;
        cursor: pointer;
        transition: all 0.12s ease;
      }

      .nav-chip.active {
        color: var(--text);
        background: linear-gradient(135deg, rgba(99,164,255,0.24), rgba(124,95,255,0.2));
        border-color: rgba(99,164,255,0.5);
      }

      .nav-chip:hover {
        border-color: rgba(255,255,255,0.16);
      }

      .user-pill {
        padding: 10px 14px;
        border-radius: 999px;
        background: rgba(255,255,255,0.04);
        border: 1px solid rgba(255,255,255,0.08);
        color: var(--soft);
      }

      .main {
        display: grid;
        grid-template-columns: minmax(0, 1.8fr) minmax(360px, 0.9fr);
        min-height: calc(92vh - 76px);
      }

      .content {
        padding: 20px;
        background: linear-gradient(180deg, rgba(17,24,39,0.9), rgba(7,11,18,0.95));
      }

      .hero {
        position: relative;
        height: 430px;
        border-radius: 28px;
        overflow: hidden;
        border: 1px solid rgba(255,255,255,0.08);
        background:
          linear-gradient(90deg, rgba(0,0,0,0.72), rgba(0,0,0,0.12)),
          url("https://images.unsplash.com/photo-1517604931442-7e0c8ed2963c?auto=format&fit=crop&w=1600&q=80") center/cover no-repeat;
      }

      .hero-glow {
        position: absolute;
        inset: 0;
        background: linear-gradient(180deg, rgba(0,0,0,0.15), rgba(0,0,0,0.55));
      }

      .hero-inner {
        position: absolute;
        left: 30px;
        right: 30px;
        bottom: 28px;
        z-index: 1;
      }

      .eyebrow {
        display: inline-block;
        border-radius: 999px;
        background: rgba(255,255,255,0.08);
        border: 1px solid rgba(255,255,255,0.12);
        color: var(--soft);
        font-size: 0.74rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        padding: 8px 12px;
      }

      .hero h1 {
        margin: 18px 0 10px;
        font-size: clamp(2.4rem, 5vw, 4.6rem);
        letter-spacing: -0.05em;
        line-height: 0.96;
      }

      .meta-row {
        display: flex;
        gap: 14px;
        flex-wrap: wrap;
        color: var(--soft);
        font-size: 0.9rem;
        margin-bottom: 20px;
      }

      .hero-actions {
        display: flex;
        gap: 12px;
        flex-wrap: wrap;
      }

      .btn {
        border: none;
        border-radius: 999px;
        padding: 12px 18px;
        font-weight: 800;
        cursor: pointer;
        transition: transform 0.12s ease, filter 0.12s ease;
      }

      .btn:hover {
        transform: translateY(-1px);
        filter: brightness(1.04);
      }

      .btn.primary {
        background: linear-gradient(135deg, var(--gold), var(--gold-2));
        color: #111827;
      }

      .btn.secondary {
        background: rgba(255,255,255,0.08);
        color: var(--text);
        border: 1px solid rgba(255,255,255,0.12);
      }

      .section {
        margin-top: 26px;
      }

      .section-head {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 14px;
      }

      .section-head h2 {
        margin: 0;
        font-size: 1.08rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        color: var(--soft);
      }

      .more {
        color: var(--gold);
        font-weight: 700;
        font-size: 0.9rem;
      }

      .cards {
        display: grid;
        grid-template-columns: repeat(4, minmax(0, 1fr));
        gap: 18px;
      }

      .card {
        border: 1px solid rgba(255,255,255,0.06);
        background: linear-gradient(180deg, rgba(22,33,50,0.9), rgba(10,15,25,0.95));
        border-radius: 20px;
        overflow: hidden;
        cursor: pointer;
        transition: transform 0.15s ease, border-color 0.15s ease;
      }

      .card:hover {
        transform: translateY(-2px);
        border-color: rgba(99,164,255,0.45);
      }

      .poster {
        position: relative;
        aspect-ratio: 4 / 5.3;
        background-size: cover;
        background-position: center;
      }

      .poster-badge {
        position: absolute;
        top: 10px;
        left: 10px;
        border-radius: 999px;
        background: rgba(12, 18, 29, 0.7);
        border: 1px solid rgba(255,255,255,0.12);
        color: var(--soft);
        font-size: 0.7rem;
        font-weight: 700;
        padding: 6px 8px;
      }

      .card-body {
        padding: 12px 12px 14px;
      }

      .card-title {
        font-size: 1rem;
        font-weight: 800;
        margin: 0 0 6px;
      }

      .card-meta {
        color: var(--muted);
        font-size: 0.82rem;
      }

      .sidebar {
        background: linear-gradient(180deg, rgba(23,34,53,0.9), rgba(10,15,25,0.95));
        border-left: 1px solid rgba(255,255,255,0.08);
        padding: 18px 18px 16px;
      }

      .player-panel {
        background: rgba(0,0,0,0.25);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 22px;
        overflow: hidden;
      }

      video {
        width: 100%;
        display: block;
        height: 260px;
        background: #000;
        object-fit: cover;
      }

      .mini-panel {
        margin-top: 18px;
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 20px;
        overflow: hidden;
      }

      .mini-head {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 12px;
        padding: 14px 16px;
        background: rgba(255,255,255,0.02);
        border-bottom: 1px solid rgba(255,255,255,0.06);
      }

      .mini-head h3 {
        font-size: 0.9rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        color: var(--soft);
        margin: 0;
      }

      .mini-score {
        padding: 6px 10px;
        border-radius: 999px;
        font-size: 0.78rem;
        font-weight: 700;
        color: var(--gold);
        background: rgba(247, 201, 106, 0.12);
        border: 1px solid rgba(247, 201, 106, 0.35);
      }

      .game-wrap {
        padding: 14px;
      }

      .mini-scene {
        position: relative;
        width: 100%;
        height: 260px;
        background:
          linear-gradient(180deg, rgba(99,164,255,0.12), rgba(0,0,0,0.18)),
          linear-gradient(180deg, #15253d, #0f1725 32%, #111827 100%);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 18px;
        overflow: hidden;
      }

      .mini-scene::before {
        content: "";
        position: absolute;
        inset: 0;
        background:
          linear-gradient(transparent 0 76%, rgba(7,11,20,0.82) 76% 100%),
          linear-gradient(90deg, rgba(255,255,255,0.02) 0 4%, transparent 4% 100%);
        pointer-events: none;
      }

      .findable {
        position: absolute;
        width: 42px;
        height: 42px;
        transform: translate(-50%, -50%);
        border: none;
        background: transparent;
        cursor: pointer;
        padding: 0;
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
        box-shadow: 0 8px 16px rgba(0,0,0,0.23);
        font-size: 1.6rem;
      }

      .findable.found .sprite {
        background: rgba(58,212,157,0.18);
        border-color: rgba(58,212,157,0.9);
        box-shadow: 0 0 18px rgba(58,212,157,0.35);
      }

      .mini-footer {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 12px 14px 14px;
        gap: 10px;
      }

      .mini-hint {
        color: var(--muted);
        font-size: 0.85rem;
      }

      .small-btn {
        border: none;
        border-radius: 999px;
        padding: 9px 12px;
        background: rgba(255,255,255,0.06);
        color: var(--text);
        border: 1px solid rgba(255,255,255,0.08);
        cursor: pointer;
        font-weight: 700;
      }

      .small-btn.primary {
        background: linear-gradient(135deg, var(--gold), var(--gold-2));
        color: #111827;
        border: none;
      }

      @media (max-width: 1100px) {
        .main {
          grid-template-columns: 1fr;
        }

        .sidebar {
          border-left: none;
          border-top: 1px solid rgba(255,255,255,0.08);
        }
      }

      @media (max-width: 900px) {
        .cards {
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

        .cards {
          grid-template-columns: 1fr;
        }

        .hero {
          height: 350px;
        }

        .hero-inner {
          left: 18px;
          right: 18px;
          bottom: 18px;
        }
      }
    </style>
  </head>
  <body>
    <div class="app">
      <header class="topbar">
        <div class="brand-wrap">
          <div class="brand-mark">C</div>
          <div class="brand">CinemaWorld</div>
        </div>

        <nav class="nav" aria-label="Navigation">
          <div class="nav-chip active">Home</div>
          <div class="nav-chip">Movies</div>
          <div class="nav-chip">TV Shows</div>
          <div class="nav-chip">New & Popular</div>
          <div class="nav-chip">My List</div>
        </nav>

        <div class="user-pill">Guest User</div>
      </header>

      <div class="main">
        <main class="content">
          <section class="hero">
            <div class="hero-glow"></div>
            <div class="hero-inner">
              <div class="eyebrow">Featured Premiere</div>
              <h1 id="featuredTitle">Night Drift</h1>
              <div class="meta-row">
                <span>2026</span>
                <span>Drama / Sci‑Fi</span>
                <span>2h 12m</span>
                <span>4.9/5</span>
              </div>
              <div class="hero-actions">
                <button class="btn primary" id="watchBtn" type="button">Watch Now</button>
                <button class="btn secondary" type="button">+ My List</button>
              </div>
            </div>
          </section>

          <section class="section">
            <div class="section-head">
              <h2>Trending Now</h2>
              <div class="more">View all</div>
            </div>
            <div id="cards" class="cards"></div>
          </section>
        </main>

        <aside class="sidebar">
          <div class="player-panel">
            <video id="mainVideo" controls playsinline poster="https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?auto=format&fit=crop&w=1200&q=80">
              <source src="https://interactive-examples.mdn.mozilla.net/media/cc0-videos/flower.mp4" type="video/mp4" />
            </video>
          </div>

          <div class="mini-panel">
            <div class="mini-head">
              <h3>Mini Game</h3>
              <div id="miniScore" class="mini-score">0 / 6</div>
            </div>

            <div class="game-wrap">
              <div id="miniScene" class="mini-scene" aria-label="Mini game scene"></div>
            </div>

            <div class="mini-footer">
              <div id="miniHint" class="mini-hint">Find the movie clues.</div>
              <button id="miniRestartBtn" class="small-btn primary" type="button">Restart</button>
            </div>
          </div>
        </aside>
      </div>
    </div>

    <script>
      const catalog = [
        {
          id: 1,
          title: "Night Drift",
          type: "Movie",
          year: 2026,
          rating: 4.9,
          poster: "https://images.unsplash.com/photo-1517604931442-7e0c8ed2963c?auto=format&fit=crop&w=1000&q=80",
          hero: "https://images.unsplash.com/photo-1517604931442-7e0c8ed2963c?auto=format&fit=crop&w=1600&q=80"
        },
        {
          id: 2,
          title: "Skyline Echo",
          type: "Series",
          year: 2025,
          rating: 4.8,
          poster: "https://images.unsplash.com/photo-1504384308090-c894fdcc538d?auto=format&fit=crop&w=1000&q=80",
          hero: "https://images.unsplash.com/photo-1504384308090-c894fdcc538d?auto=format&fit=crop&w=1600&q=80"
        },
        {
          id: 3,
          title: "Pixel Harbor",
          type: "Movie",
          year: 2024,
          rating: 4.7,
          poster: "https://images.unsplash.com/photo-1513106580091-1d82408b8cd6?auto=format&fit=crop&w=1000&q=80",
          hero: "https://images.unsplash.com/photo-1513106580091-1d82408b8cd6?auto=format&fit=crop&w=1600&q=80"
        },
        {
          id: 4,
          title: "Signal Zero",
          type: "Series",
          year: 2026,
          rating: 4.9,
          poster: "https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?auto=format&fit=crop&w=1000&q=80",
          hero: "https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?auto=format&fit=crop&w=1600&q=80"
        },
        {
          id: 5,
          title: "Hidden Orbit",
          type: "Movie",
          year: 2025,
          rating: 4.6,
          poster: "https://images.unsplash.com/photo-1536440136628-849c177e76a1?auto=format&fit=crop&w=1000&q=80",
          hero: "https://images.unsplash.com/photo-1536440136628-849c177e76a1?auto=format&fit=crop&w=1600&q=80"
        },
        {
          id: 6,
          title: "Crimson Run",
          type: "Series",
          year: 2024,
          rating: 4.8,
          poster: "https://images.unsplash.com/photo-1524985069026-dd778a71c7b4?auto=format&fit=crop&w=1000&q=80",
          hero: "https://images.unsplash.com/photo-1524985069026-dd778a71c7b4?auto=format&fit=crop&w=1600&q=80"
        }
      ];

      const cardsContainer = document.getElementById("cards");
      const featuredTitle = document.getElementById("featuredTitle");
      const hero = document.querySelector(".hero");
      const mainVideo = document.getElementById("mainVideo");
      const watchBtn = document.getElementById("watchBtn");

      function renderCards() {
        cardsContainer.innerHTML = "";

        catalog.forEach((item) => {
          const card = document.createElement("div");
          card.className = "card";
          card.innerHTML = `
            <div class="poster" style="background-image: url('${item.poster}')">
              <div class="poster-badge">${item.type}</div>
            </div>
            <div class="card-body">
              <h3 class="card-title">${item.title}</h3>
              <div class="card-meta">${item.year} • ${item.rating}/5</div>
            </div>
          `;

          card.addEventListener("click", () => {
            featuredTitle.textContent = item.title;
            hero.style.background =
              `linear-gradient(90deg, rgba(0,0,0,0.72), rgba(0,0,0,0.18)), url('${item.hero}') center/cover no-repeat`;
            mainVideo.poster = item.poster;
            mainVideo.play();
          });

          cardsContainer.appendChild(card);
        });
      }

      renderCards();

      watchBtn.addEventListener("click", () => {
        mainVideo.play();
      });

      class HiddenMovieGame {
        constructor() {
          this.scene = document.getElementById("miniScene");
          this.scoreEl = document.getElementById("miniScore");
          this.hintEl = document.getElementById("miniHint");
          this.restartBtn = document.getElementById("miniRestartBtn");
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
          this.found = 0;
          this.hintEl.textContent = "Find the movie clues.";
          this.renderScore();

          const clueList = [
            { name: "Ticket", emoji: "🎟️" },
            { name: "Popcorn", emoji: "🍿" },
            { name: "Play", emoji: "▶️" },
            { name: "Camera", emoji: "🎥" },
            { name: "Reel", emoji: "🎞️" },
            { name: "Clapperboard", emoji: "🎬" }
          ];

          this.items = [];
          for (let i = 0; i < clueList.length; i++) {
            const item = clueList[i];
            let x = 0;
            let y = 0;
            let tries = 0;

            do {
              x = Math.random() * (this.sceneSize.width - 80) + 40;
              y = Math.random() * (this.sceneSize.height - 80) + 40;
              tries++;
            } while (
              tries < 300 &&
              this.items.some((existing) => {
                const dx = x - existing.x;
                const dy = y - existing.y;
                return Math.hypot(dx, dy) < 75;
              })
            );

            this.items.push({
              ...item,
              x,
              y,
              found: false
            });

            this.createObject(this.items[this.items.length - 1]);
          }
        }

        createObject(item) {
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
            this.hintEl.textContent = "You found all clues!";
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
          overlay.style.background = "rgba(0,0,0,0.4)";
          overlay.style.backdropFilter = "blur(2px)";
          overlay.style.fontWeight = "800";
          overlay.style.fontSize = "clamp(1.4rem, 2vw, 2.2rem)";
          overlay.style.color = "#d1fae5";
          overlay.textContent = "You found all clues!";
          this.scene.appendChild(overlay);
        }
      }

      new HiddenMovieGame();
    </script>
  </body>
</html>
