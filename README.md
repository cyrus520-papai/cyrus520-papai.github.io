<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>CinemaWorld</title>
    <style>
      :root {
        --bg: #070b14;
        --bg-2: #101827;
        --panel: #111827;
        --panel-2: #182235;
        --panel-3: #1d2a3c;
        --soft: #d9e3f0;
        --muted: #a5b4cf;
        --text: #eff6ff;
        --gold: #f5c76d;
        --gold-2: #ee8f3c;
        --accent: #60a5fa;
        --accent-2: #7c3aed;
        --success: #34d399;
        --danger: #f87171;
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
          radial-gradient(circle at top, rgba(96, 165, 250, 0.18), transparent 30%),
          linear-gradient(180deg, var(--bg), var(--bg-2));
        color: var(--text);
      }

      body {
        display: grid;
        place-items: center;
      }

      .app {
        width: min(1440px, 96vw);
        min-height: 92vh;
        background: rgba(8, 12, 20, 0.88);
        border: 1px solid rgba(255, 255, 255, 0.08);
        border-radius: 24px;
        overflow: hidden;
        box-shadow: 0 24px 60px var(--shadow);
      }

      .topbar {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 18px 24px;
        border-bottom: 1px solid rgba(255,255,255,0.08);
        background: rgba(17, 24, 39, 0.8);
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
        background: linear-gradient(135deg, var(--gold), var(--gold-2));
        color: #111827;
        font-weight: 800;
      }

      .brand {
        font-size: 1.2rem;
        font-weight: 800;
        letter-spacing: 0.08em;
        text-transform: uppercase;
      }

      .nav {
        display: flex;
        align-items: center;
        gap: 12px;
        flex-wrap: wrap;
      }

      .nav-chip {
        padding: 8px 14px;
        border-radius: 999px;
        background: rgba(255,255,255,0.04);
        border: 1px solid rgba(255,255,255,0.06);
        color: var(--soft);
        font-size: 0.9rem;
      }

      .nav-chip.active {
        background: linear-gradient(135deg, rgba(96,165,250,0.3), rgba(124,58,237,0.2));
        border-color: rgba(96,165,250,0.5);
        color: #fff;
      }

      .user-pill {
        padding: 10px 14px;
        background: rgba(255,255,255,0.05);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 999px;
        color: var(--soft);
        font-size: 0.9rem;
      }

      .main {
        display: grid;
        grid-template-columns: minmax(0, 1.8fr) minmax(330px, 0.85fr);
        min-height: calc(92vh - 78px);
      }

      .content {
        padding: 20px 20px 22px;
        background: linear-gradient(180deg, rgba(17,24,39,0.9), rgba(9,13,19,0.9));
      }

      .hero {
        position: relative;
        height: 420px;
        border-radius: 24px;
        overflow: hidden;
        background:
          linear-gradient(90deg, rgba(0,0,0,0.72), rgba(0,0,0,0.18)),
          url("https://images.unsplash.com/photo-1536440136628-849c177e76a1?auto=format&fit=crop&w=1400&q=80") center/cover no-repeat;
        border: 1px solid rgba(255,255,255,0.08);
      }

      .hero-overlay {
        position: absolute;
        inset: 0;
        background: linear-gradient(180deg, rgba(0,0,0,0.15), rgba(0,0,0,0.5));
      }

      .hero-inner {
        position: absolute;
        left: 28px;
        bottom: 28px;
        z-index: 1;
        max-width: 680px;
      }

      .eyebrow {
        display: inline-block;
        background: rgba(255,255,255,0.08);
        border: 1px solid rgba(255,255,255,0.12);
        border-radius: 999px;
        padding: 7px 12px;
        font-size: 0.75rem;
        letter-spacing: 0.06em;
        text-transform: uppercase;
        color: var(--soft);
      }

      .hero h1 {
        margin: 16px 0 10px;
        font-size: clamp(2.2rem, 4vw, 4rem);
        line-height: 1;
      }

      .hero-meta {
        display: flex;
        flex-wrap: wrap;
        gap: 14px;
        color: var(--soft);
        margin-bottom: 18px;
        font-size: 0.9rem;
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
        margin-top: 24px;
      }

      .section-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 14px;
      }

      .section-header h2 {
        margin: 0;
        font-size: 1.1rem;
        letter-spacing: 0.04em;
        text-transform: uppercase;
        color: var(--soft);
      }

      .more {
        color: var(--gold);
        font-size: 0.88rem;
        font-weight: 700;
      }

      .card-row {
        display: grid;
        grid-template-columns: repeat(4, minmax(0, 1fr));
        gap: 16px;
      }

      .media-card {
        background: linear-gradient(180deg, rgba(24,34,53,0.9), rgba(12,18,30,0.9));
        border: 1px solid rgba(255,255,255,0.06);
        border-radius: 18px;
        overflow: hidden;
        cursor: pointer;
        transition: transform 0.15s ease, border-color 0.15s ease;
      }

      .media-card:hover {
        transform: translateY(-2px);
        border-color: rgba(96,165,250,0.4);
      }

      .media-poster {
        position: relative;
        aspect-ratio: 4 / 5.3;
        background-size: cover;
        background-position: center;
        overflow: hidden;
      }

      .badge {
        position: absolute;
        top: 10px;
        left: 10px;
        background: rgba(17,24,39,0.8);
        color: var(--soft);
        border: 1px solid rgba(255,255,255,0.12);
        border-radius: 999px;
        padding: 5px 8px;
        font-size: 0.7rem;
        font-weight: 700;
      }

      .media-info {
        padding: 12px 12px 14px;
      }

      .media-title {
        font-size: 1rem;
        font-weight: 800;
        margin: 0 0 6px;
      }

      .media-meta {
        color: var(--muted);
        font-size: 0.82rem;
      }

      .sidebar {
        background: linear-gradient(180deg, rgba(24,34,53,0.9), rgba(8,12,20,0.9));
        border-left: 1px solid rgba(255,255,255,0.08);
        padding: 20px 18px 18px;
      }

      .watch-player {
        background: #000;
        border-radius: 18px;
        overflow: hidden;
        border: 1px solid rgba(255,255,255,0.08);
      }

      video {
        width: 100%;
        display: block;
        height: 260px;
        object-fit: cover;
        background: #000;
      }

      .mini-panel {
        margin-top: 20px;
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 20px;
        overflow: hidden;
      }

      .mini-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 12px;
        padding: 14px 16px;
        border-bottom: 1px solid rgba(255,255,255,0.06);
        background: rgba(255,255,255,0.02);
      }

      .mini-header h3 {
        margin: 0;
        font-size: 0.95rem;
        letter-spacing: 0.06em;
        text-transform: uppercase;
        color: var(--soft);
      }

      .mini-score {
        background: rgba(245, 199, 109, 0.12);
        border: 1px solid rgba(245, 199, 109, 0.45);
        color: var(--gold);
        border-radius: 999px;
        padding: 6px 10px;
        font-size: 0.75rem;
        font-weight: 700;
      }

      .game-box {
        position: relative;
        padding: 14px;
        min-height: 310px;
      }

      .mini-scene {
        position: relative;
        width: 100%;
        height: 250px;
        border-radius: 16px;
        overflow: hidden;
        border: 1px solid rgba(255,255,255,0.08);
        background:
          linear-gradient(180deg, rgba(96,165,250,0.12), rgba(0,0,0,0.2)),
          linear-gradient(180deg, #14233d 0%, #121823 30%, #172435 100%);
      }

      .mini-scene::before {
        content: "";
        position: absolute;
        inset: 0;
        background:
          linear-gradient(transparent 0 76%, rgba(7,11,20,0.85) 76% 100%),
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
        box-shadow: 0 8px 18px rgba(0,0,0,0.22);
        font-size: 1.6rem;
      }

      .findable.found .sprite {
        background: rgba(52,211,153,0.18);
        border-color: rgba(52,211,153,0.9);
        box-shadow: 0 0 18px rgba(52,211,153,0.44);
      }

      .mini-footer {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 10px;
        padding: 12px 14px 14px;
      }

      .mini-hint {
        color: var(--muted);
        font-size: 0.85rem;
      }

      .small-btn {
        border: none;
        background: linear-gradient(135deg, var(--gold), var(--gold-2));
        color: #111827;
        border-radius: 999px;
        padding: 9px 12px;
        font-weight: 800;
        cursor: pointer;
      }

      .small-btn.secondary {
        background: rgba(255,255,255,0.06);
        border: 1px solid rgba(255,255,255,0.08);
        color: var(--text);
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

      @media (max-width: 860px) {
        .card-row {
          grid-template-columns: repeat(2, minmax(0, 1fr));
        }
      }

      @media (max-width: 560px) {
        .topbar {
          flex-direction: column;
          align-items: flex-start;
        }

        .nav {
          width: 100%;
        }

        .card-row {
          grid-template-columns: 1fr;
        }

        .hero {
          height: 340px;
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

        <nav class="nav" aria-label="main navigation">
          <div class="nav-chip active">Home</div>
          <div class="nav-chip">Movies</div>
          <div class="nav-chip">Series</div>
          <div class="nav-chip">New</div>
          <div class="nav-chip">My List</div>
        </nav>

        <div class="user-pill">Guest User</div>
      </header>

      <div class="main">
        <main class="content">
          <section class="hero">
            <div class="hero-overlay"></div>
            <div class="hero-inner">
              <div class="eyebrow">Featured Premiere</div>
              <h1>Night Drift</h1>
              <div class="hero-meta">
                <span>2026</span>
                <span>Drama / Sci‑Fi</span>
                <span>2h 12m</span>
                <span>4.9/5</span>
              </div>
              <div class="hero-actions">
                <button class="btn primary" type="button" id="watchFeaturedBtn">Watch Now</button>
                <button class="btn secondary" type="button">+ My List</button>
              </div>
            </div>
          </section>

          <section class="section">
            <div class="section-header">
              <h2>Trending Now</h2>
              <div class="more">View all</div>
            </div>

            <div class="card-row" id="contentGrid"></div>
          </section>
        </main>

        <aside class="sidebar">
          <div class="watch-player">
            <video id="mainVideo" controls playsinline poster="https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?auto=format&fit=crop&w=1200&q=80">
              <source src="https://interactive-examples.mdn.mozilla.net/media/cc0-videos/flower.mp4" type="video/mp4" />
            </video>
          </div>

          <div class="mini-panel">
            <div class="mini-header">
              <h3>Mini Game</h3>
              <div class="mini-score" id="miniScore">0 / 6</div>
            </div>

            <div class="game-box">
              <div id="miniScene" class="mini-scene" aria-label="Hidden movie objects mini game"></div>
            </div>

            <div class="mini-footer">
              <div class="mini-hint" id="miniHint">Find the movie clues.</div>
              <button type="button" id="miniRestartBtn" class="small-btn secondary">Restart</button>
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
          rating: "4.9",
          poster: "https://images.unsplash.com/photo-1517604931442-7e0c8ed2963c?auto=format&fit=crop&w=900&q=80"
        },
        {
          id: 2,
          title: "Skyline Echo",
          type: "Series",
          year: 2025,
          rating: "4.8",
          poster: "https://images.unsplash.com/photo-1504384308090-c894fdcc538d?auto=format&fit=crop&w=900&q=80"
        },
        {
          id: 3,
          title: "Pixel Harbor",
          type: "Movie",
          year: 2024,
          rating: "4.7",
          poster: "https://images.unsplash.com/photo-1513106580091-1d82408b8cd6?auto=format&fit=crop&w=900&q=80"
        },
        {
          id: 4,
          title: "Signal Zero",
          type: "Series",
          year: 2026,
          rating: "4.9",
          poster: "https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?auto=format&fit=crop&w=900&q=80"
        }
      ];

      const mainVideo = document.getElementById("mainVideo");
      const contentGrid = document.getElementById("contentGrid");
      const watchFeaturedBtn = document.getElementById("watchFeaturedBtn");

      function renderCards() {
        contentGrid.innerHTML = "";

        catalog.forEach((item) => {
          const card = document.createElement("div");
          card.className = "media-card";
          card.innerHTML = `
            <div class="media-poster" style="background-image: url('${item.poster}')">
              <div class="badge">${item.type}</div>
            </div>
            <div class="media-info">
              <h3 class="media-title">${item.title}</h3>
              <div class="media-meta">${item.year} • ${item.rating}/5</div>
            </div>
          `;
          card.addEventListener("click", () => {
            const hero = document.querySelector(".hero");
            hero.style.background =
              `linear-gradient(90deg, rgba(0,0,0,0.72), rgba(0,0,0,0.18)), url('${item.poster}') center/cover no-repeat`;
            const title = document.querySelector(".hero h1");
            title.textContent = item.title;
            const videoSource = document.querySelector("#mainVideo source");
            videoSource.src = "https://interactive-examples.mdn.mozilla.net/media/cc0-videos/flower.mp4";
            mainVideo.load();
            mainVideo.play();
          });

          contentGrid.appendChild(card);
        });
      }

      renderCards();

      watchFeaturedBtn.addEventListener("click", () => {
        mainVideo.play();
      });

      class MiniGame {
        constructor() {
          this.scene = document.getElementById("miniScene");
          this.scoreEl = document.getElementById("miniScore");
          this.hintEl = document.getElementById("miniHint");
          this.restartBtn = document.getElementById("miniRestartBtn");
          this.items = [];
          this.foundCount = 0;
          this.gameOver = false;
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
          this.foundCount = 0;
          this.gameOver = false;
          this.hintEl.textContent = "Find the movie clues.";
          this.renderScore();
          this.generateItems([
            { name: "Ticket", emoji: "🎟️" },
            { name: "Popcorn", emoji: "🍿" },
            { name: "Play", emoji: "▶️" },
            { name: "Camera", emoji: "🎥" },
            { name: "Reel", emoji: "🎞️" },
            { name: "Clapperboard", emoji: "🎬" }
          ]);
        }

        renderScore() {
          this.scoreEl.textContent = `${this.foundCount} / ${this.items.length}`;
        }

        generateItems(list) {
          const placed = [];

          for (let i = 0; i < list.length; i++) {
            const item = list[i];
            let x = 0;
            let y = 0;
            let tries = 0;

            do {
              x = Math.random() * (this.sceneSize.width - 80) + 40;
              y = Math.random() * (this.sceneSize.height - 80) + 40;
              tries++;
            } while (
              tries < 200 &&
              placed.some((existing) => {
                const dx = x - existing.x;
                const dy = y - existing.y;
                return Math.hypot(dx, dy) < 72;
              })
            );

            const data = {
              ...item,
              x,
              y,
              found: false
            };

            placed.push(data);
            this.createObject(data);
          }

          this.items = placed;
          this.renderScore();
        }

        createObject(item) {
          const button = document.createElement("button");
          button.type = "button";
          button.className = "findable";
          button.style.left = `${item.x}px`;
          button.style.top = `${item.y}px`;
          button.setAttribute("aria-label", `Find ${item.name}`);

          const sprite = document.createElement("span");
          sprite.className = "sprite";
          sprite.textContent = item.emoji;

          button.appendChild(sprite);
          button.addEventListener("click", () => this.onFound(item, button));
          this.scene.appendChild(button);
        }

        onFound(item, element) {
          if (this.gameOver || item.found) return;

          item.found = true;
          element.classList.add("found");
          element.classList.add("hidden");

          this.foundCount += 1;
          this.renderScore();

          if (this.foundCount === this.items.length) {
            this.gameOver = true;
            this.hintEl.textContent = "All clues found! You win!";
            this.showWinOverlay();
          } else {
            this.hintEl.textContent = `Nice! ${this.foundCount} found so far.`;
          }
        }

        showWinOverlay() {
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
          overlay.textContent = "You found them all!";
          this.scene.appendChild(overlay);
        }
      }

      new MiniGame();
    </script>
  </body>
</html>
