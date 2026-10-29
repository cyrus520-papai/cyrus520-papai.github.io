<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Hidden Movie & Show Hunt</title>
    <style>
      :root {
        --bg-1: #0b1020;
        --bg-2: #171f36;
        --panel: #1d2438;
        --panel-2: #2b3550;
        --primary: #fbbf24;
        --primary-2: #f97316;
        --text: #f5f7ff;
        --muted: #c9d1ea;
        --accent: #7dd3fc;
        --success: #4ade80;
        --danger: #f87171;
      }

      * {
        box-sizing: border-box;
      }

      body {
        margin: 0;
        min-height: 100vh;
        display: grid;
        place-items: center;
        font-family: Arial, sans-serif;
        background:
          radial-gradient(circle at top, rgba(125, 211, 252, 0.18), transparent 30%),
          linear-gradient(160deg, var(--bg-1), var(--bg-2));
        color: var(--text);
      }

      .game-shell {
        width: min(92vw, 980px);
        background: rgba(11, 16, 32, 0.9);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 20px;
        overflow: hidden;
        box-shadow: 0 30px 60px rgba(0,0,0,0.38);
      }

      .hud {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 16px;
        padding: 18px 22px;
        background: var(--panel);
        border-bottom: 1px solid rgba(255,255,255,0.08);
      }

      .brand {
        font-size: 1.25rem;
        font-weight: 800;
        letter-spacing: 0.06em;
        text-transform: uppercase;
      }

      .stats {
        display: flex;
        flex-wrap: wrap;
        gap: 12px;
      }

      .stat {
        background: var(--panel-2);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 999px;
        padding: 8px 14px;
        font-size: 0.96rem;
      }

      .scene-wrap {
        padding: 18px;
        background:
          linear-gradient(180deg, rgba(25,33,52,0.85), rgba(11,16,32,0.85));
      }

      .scene {
        position: relative;
        width: 100%;
        aspect-ratio: 16 / 9;
        background:
          linear-gradient(180deg, rgba(59,130,246,0.15), rgba(0,0,0,0.15)),
          linear-gradient(180deg, #1b2a4f 0%, #0f172a 28%, #121b2b 29%, #2f3b1d 100%);
        border-radius: 16px;
        overflow: hidden;
        border: 1px solid rgba(255,255,255,0.08);
        box-shadow: inset 0 0 36px rgba(0,0,0,0.35);
      }

      .scene::before {
        content: "";
        position: absolute;
        inset: 0;
        background:
          linear-gradient(transparent 0 75%, rgba(13,19,29,0.82) 75% 100%),
          linear-gradient(90deg, rgba(255,255,255,0.02) 0 4%, transparent 4% 100%);
        pointer-events: none;
      }

      .movie-object {
        position: absolute;
        width: 42px;
        height: 42px;
        transform: translate(-50%, -50%);
        border: none;
        background: transparent;
        cursor: pointer;
        user-select: none;
        padding: 0;
        transition: transform 0.12s ease, filter 0.12s ease;
      }

      .movie-object:hover {
        transform: translate(-50%, -50%) scale(1.08);
      }

      .movie-object:focus-visible {
        outline: 3px solid rgba(255,255,255,0.8);
        outline-offset: 5px;
        border-radius: 10px;
      }

      .movie-object.hidden {
        opacity: 0;
        pointer-events: none;
      }

      .movie-object .sprite {
        width: 100%;
        height: 100%;
        display: grid;
        place-items: center;
        border-radius: 14px;
        font-size: 1.7rem;
        background: rgba(255,255,255,0.08);
        border: 2px solid rgba(255,255,255,0.18);
        box-shadow: 0 8px 16px rgba(0,0,0,0.24);
      }

      .movie-object.found .sprite {
        background: rgba(74,222,128,0.18);
        border-color: rgba(74,222,128,0.9);
        box-shadow: 0 0 20px rgba(74,222,128,0.5);
      }

      .message {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 16px;
        min-height: 70px;
        padding: 16px 22px 20px;
        color: var(--muted);
        background: rgba(17, 24, 39, 0.75);
      }

      .message strong {
        color: var(--text);
      }

      .btn {
        border: none;
        background: linear-gradient(135deg, var(--primary), var(--primary-2));
        color: #111827;
        font-weight: 800;
        border-radius: 999px;
        padding: 10px 18px;
        cursor: pointer;
      }

      .btn:hover {
        filter: brightness(1.05);
      }

      .btn.secondary {
        background: #374151;
        color: var(--text);
      }

      @media (max-width: 700px) {
        .hud {
          flex-direction: column;
          align-items: flex-start;
        }

        .message {
          flex-direction: column;
          align-items: flex-start;
        }
      }
    </style>
  </head>
  <body>
    <div class="game-shell">
      <div class="hud">
        <div class="brand">Movie Hideout</div>
        <div class="stats">
          <div class="stat" id="timer">Time: 60s</div>
          <div class="stat" id="score">Found: 0 / 8</div>
        </div>
      </div>

      <div class="scene-wrap">
        <div id="scene" class="scene" aria-label="Hidden movie and show objects scene"></div>
      </div>

      <div class="message">
        <div><strong>Find all movie-night clues</strong> before the timer runs out.</div>
        <button id="restartBtn" class="btn secondary" type="button">Restart</button>
      </div>
    </div>

    <script>
      const ITEMS = [
        { name: "Ticket", emoji: "🎟️" },
        { name: "Popcorn", emoji: "🍿" },
        { name: "Camera", emoji: "🎥" },
        { name: "TV", emoji: "📺" },
        { name: "Play Button", emoji: "▶️" },
        { name: "Movie Reel", emoji: "🎞️" },
        { name: "Remote", emoji: "📺" }, // intentionally duplicates to show variety
        { name: "Clapperboard", emoji: "🎬" }
      ];

      class HiddenMovieGame {
        constructor() {
          this.items = [];
          this.foundCount = 0;
          this.secondsLeft = 60;
          this.gameOver = false;
          this.timerId = null;
          this.sceneBounds = { width: 0, height: 0 };
          this.scene = document.getElementById("scene");
          this.timerEl = document.getElementById("timer");
          this.scoreEl = document.getElementById("score");
          this.restartBtn = document.getElementById("restartBtn");
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
          this.sceneBounds.width = rect.width;
          this.sceneBounds.height = rect.height;
        }

        start() {
          clearInterval(this.timerId);

          this.scene.innerHTML = "";
          this.items = [];
          this.foundCount = 0;
          this.secondsLeft = 60;
          this.gameOver = false;

          this.generateItems(ITEMS);
          this.renderScore();
          this.renderTimer();
          this.timerId = setInterval(() => {
            if (this.gameOver) return;

            this.secondsLeft -= 1;
            this.renderTimer();

            if (this.secondsLeft <= 0) {
              this.endGame(false);
            }
          }, 1000);
        }

        generateItems(list) {
          const placedItems = [];

          for (let i = 0; i < list.length; i++) {
            const itemData = list[i];
            let x = 0;
            let y = 0;
            let tries = 0;

            do {
              x = Math.random() * (this.sceneBounds.width - 80) + 40;
              y = Math.random() * (this.sceneBounds.height - 80) + 40;
              tries++;
            } while (
              tries < 250 &&
              placedItems.some((existing) => {
                const dx = x - existing.x;
                const dy = y - existing.y;
                return Math.hypot(dx, dy) < 80;
              })
            );

            const item = {
              ...itemData,
              x,
              y,
              found: false
            };

            placedItems.push(item);
            this.createObject(item);
          }

          this.items = placedItems;
        }

        createObject(item) {
          const button = document.createElement("button");
          button.type = "button";
          button.className = "movie-object";
          button.setAttribute("aria-label", `Find ${item.name}`);
          button.style.left = `${item.x}px`;
          button.style.top = `${item.y}px`;

          const sprite = document.createElement("span");
          sprite.className = "sprite";
          sprite.textContent = item.emoji;

          button.appendChild(sprite);
          button.addEventListener("click", () => this.onObjectFound(item, button));
          this.scene.appendChild(button);
        }

        onObjectFound(item, element) {
          if (this.gameOver || item.found) return;

          item.found = true;
          element.classList.add("found");
          element.classList.add("hidden");

          this.foundCount += 1;
          this.renderScore();

          if (this.foundCount === this.items.length) {
            this.endGame(true);
          }
        }

        renderScore() {
          this.scoreEl.textContent = `Found: ${this.foundCount} / ${this.items.length}`;
        }

        renderTimer() {
          this.timerEl.textContent = `Time: ${this.secondsLeft}s`;
        }

        endGame(win) {
          this.gameOver = true;
          clearInterval(this.timerId);

          const overlay = document.createElement("div");
          overlay.style.position = "absolute";
          overlay.style.inset = "0";
          overlay.style.display = "grid";
          overlay.style.placeItems = "center";
          overlay.style.fontSize = "clamp(1.4rem, 3vw, 2.3rem)";
          overlay.style.fontWeight = "800";
          overlay.style.color = win ? "#d1fae5" : "#fee2e2";
          overlay.style.background = "rgba(0,0,0,0.34)";
          overlay.style.backdropFilter = "blur(2px)";
          overlay.style.zIndex = "10";
          overlay.textContent = win ? "You found them all!" : "Time's up! Try again.";

          this.scene.appendChild(overlay);
        }
      }

      new HiddenMovieGame();
    </script>
  </body>
</html>
