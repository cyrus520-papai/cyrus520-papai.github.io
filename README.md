<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Achroma</title>
    <style>
      :root {
        --bg: #05070d;
        --panel: rgba(14, 17, 25, 0.88);
        --panel-strong: rgba(20, 23, 30, 0.95);
        --line: rgba(255, 255, 255, 0.09);
        --text: #f2f5fb;
        --muted: rgba(255,255,255,0.55);
        --soft: rgba(255,255,255,0.08);
        --red-1: #c0132d;
        --red-2: #ee234b;
        --red-3: #8d0e20;
        --pink: #ff7b95;
        --shadow: 0 18px 40px rgba(0,0,0,0.42);
        --glow: rgba(255,255,255,0.8);
      }

      * {
        box-sizing: border-box;
      }

      html, body {
        margin: 0;
        width: 100%;
        height: 100%;
        background: var(--bg);
        color: var(--text);
        font-family: Inter, "Segoe UI", sans-serif;
      }

      body {
        overflow: hidden;
      }

      .page {
        width: 100vw;
        height: 100vh;
        position: relative;
        background:
          radial-gradient(circle at 50% 35%, rgba(255,255,255,0.08), transparent 28%),
          radial-gradient(circle at 60% 55%, rgba(255,255,255,0.03), transparent 20%),
          linear-gradient(180deg, #03060a 0%, #070b13 100%);
      }

      .page::before {
        content: "";
        position: absolute;
        inset: 0;
        background-image:
          radial-gradient(circle, rgba(255,255,255,0.18) 1px, transparent 1.2px);
        background-size: 22px 22px;
        opacity: 0.32;
        pointer-events: none;
      }

      .app-shell {
        position: relative;
        z-index: 1;
        width: 100%;
        height: 100%;
        display: flex;
      }

      .sidebar {
        width: 220px;
        background: rgba(11, 13, 20, 0.94);
        border-right: 1px solid var(--line);
        display: flex;
        flex-direction: column;
        padding: 14px 10px 12px 10px;
      }

      .app-icons {
        display: flex;
        flex-direction: column;
        gap: 10px;
        align-items: center;
        padding-bottom: 12px;
        border-bottom: 1px solid var(--line);
      }

      .icon-row {
        display: flex;
        gap: 10px;
      }

      .icon {
        width: 42px;
        height: 42px;
        border-radius: 12px;
        display: grid;
        place-items: center;
        font-weight: 700;
        font-size: 18px;
        color: white;
        background: rgba(255,255,255,0.06);
        border: 1px solid rgba(255,255,255,0.07);
        box-shadow: inset 0 0 0 1px rgba(255,255,255,0.03);
      }

      .icon.red { background: linear-gradient(135deg, #ff4d4d, #be1e42); }
      .icon.orange { background: linear-gradient(135deg, #ff9e3d, #e15a1d); }
      .icon.blue { background: linear-gradient(135deg, #3d9dff, #1d5df5); }
      .icon.green { background: linear-gradient(135deg, #40df8d, #0d9b6c); }
      .icon.purple { background: linear-gradient(135deg, #b279ff, #7144ef); }
      .icon.dark { background: rgba(255,255,255,0.04); }

      .icon.active {
        border: 1px solid rgba(255,255,255,0.15);
        box-shadow: 0 0 0 1px rgba(255,255,255,0.08), inset 0 0 18px rgba(255,255,255,0.06);
      }

      .plus {
        font-size: 30px;
        line-height: 0;
      }

      .nav-area {
        margin-top: 12px;
        padding: 0 8px;
      }

      .tabs-header {
        font-size: 12px;
        color: rgba(255,255,255,0.44);
        letter-spacing: 0.16em;
        text-transform: uppercase;
        margin: 8px 0 10px;
        padding-left: 8px;
      }

      .tab {
        width: 100%;
        display: flex;
        align-items: center;
        gap: 10px;
        color: rgba(255,255,255,0.78);
        background: rgba(255,255,255,0.0);
        border: none;
        padding: 10px 8px 10px 8px;
        border-radius: 10px;
        cursor: pointer;
        font-size: 14px;
        margin: 4px 0;
      }

      .tab.active {
        background: rgba(255,255,255,0.03);
        border: 1px solid rgba(255,255,255,0.04);
      }

      .tab .dot {
        width: 14px;
        height: 14px;
        display: inline-flex;
        align-items: center;
        justify-content: center;
        color: rgba(255,255,255,0.7);
        font-size: 11px;
      }

      .badge {
        margin-left: auto;
        background: linear-gradient(135deg, #ff4c5e, #ff3d76);
        color: white;
        font-size: 11px;
        font-weight: 700;
        padding: 4px 7px;
        border-radius: 999px;
        min-width: 26px;
        text-align: center;
      }

      .new-tag {
        margin-left: 10px;
        background: rgba(255,255,255,0.12);
        color: white;
        border-radius: 8px;
        padding: 4px 8px;
        font-size: 11px;
        font-weight: 600;
      }

      .nav-bottom {
        margin-top: auto;
        padding: 0 8px 8px;
      }

      .main {
        flex: 1;
        position: relative;
        overflow: hidden;
      }

      .browser-bar {
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        height: 66px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 14px 18px 10px 18px;
      }

      .browser-controls {
        display: flex;
        align-items: center;
        gap: 12px;
        color: rgba(255,255,255,0.8);
        padding-left: 10px;
      }

      .nav-button {
        width: 20px;
        height: 20px;
        display: grid;
        place-items: center;
        font-size: 18px;
        color: rgba(255,255,255,0.7);
      }

      .address-bar {
        height: 36px;
        width: 51%;
        min-width: 500px;
        max-width: 820px;
        background: rgba(255,255,255,0.03);
        border: 1px solid rgba(255,255,255,0.07);
        border-radius: 999px;
        display: flex;
        align-items: center;
        padding: 0 16px 0 12px;
        margin: 0 auto;
        box-shadow: inset 0 0 0 1px rgba(255,255,255,0.025);
      }

      .search-glass {
        font-size: 18px;
        opacity: 0.8;
        margin-right: 10px;
      }

      .address-text {
        color: rgba(255,255,255,0.72);
        font-size: 14px;
        letter-spacing: 0.01em;
      }

      .user-pill {
        display: flex;
        align-items: center;
        gap: 10px;
        color: rgba(255,255,255,0.9);
        font-weight: 600;
        font-size: 14px;
      }

      .user-pill .dot {
        width: 8px;
        height: 8px;
        border-radius: 50%;
        background: #2ddd7b;
        box-shadow: 0 0 10px rgba(46,221,123,0.8);
      }

      .hero {
        position: absolute;
        inset: 0 0 0 0;
        display: flex;
        justify-content: center;
        align-items: center;
        background: transparent;
      }

      .hero-shape {
        position: absolute;
        right: -120px;
        bottom: -130px;
        width: 100%;
        height: 82%;
        background: linear-gradient(180deg, rgba(160, 14, 30, 0.5), rgba(160, 14, 30, 0.78));
        clip-path: ellipse(65% 46% at 73% 54%);
        filter: drop-shadow(0 0 26px rgba(236, 42, 82, 0.25));
      }

      .hero-shape::before {
        content: "";
        position: absolute;
        inset: 0;
        background: linear-gradient(180deg, rgba(255,255,255,0.0), rgba(255,255,255,0.04));
      }

      .hero-content {
        position: relative;
        z-index: 1;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        margin-top: 70px;
      }

      .brand {
        font-family: "Segoe Print", "Bradley Hand", cursive;
        font-size: clamp(80px, 10vw, 190px);
        font-weight: 700;
        letter-spacing: -0.05em;
        color: rgba(255,255,255,0.98);
        text-shadow:
          0 0 12px rgba(255,255,255,0.1),
          0 0 30px rgba(255,255,255,0.35);
        line-height: 0.9;
        transform: rotate(-2deg);
        margin-bottom: 26px;
        user-select: none;
      }

      .search-box {
        width: min(600px, 60vw);
        height: 62px;
        display: flex;
        align-items: center;
        gap: 14px;
        padding: 0 20px 0 18px;
        background: rgba(0,0,0,0.33);
        border: 1px solid rgba(255,255,255,0.06);
        border-radius: 18px;
        box-shadow: inset 0 0 0 1px rgba(255,255,255,0.02);
        backdrop-filter: blur(2px);
      }

      .search-box .icon {
        width: 16px;
        height: 16px;
        font-size: 16px;
        color: rgba(255,255,255,0.85);
      }

      .search-box input {
        width: 100%;
        height: 100%;
        border: none;
        background: transparent;
        outline: none;
        color: var(--text);
        font-size: 19px;
      }

      .search-box input::placeholder {
        color: rgba(255,255,255,0.55);
      }

      .chip-row {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        gap: 10px;
        margin-top: 18px;
      }

      .chip {
        display: inline-flex;
        align-items: center;
        gap: 8px;
        height: 34px;
        padding: 0 14px;
        border-radius: 999px;
        border: 1px solid rgba(255,255,255,0.12);
        background: rgba(0,0,0,0.28);
        color: rgba(255,255,255,0.8);
        font-size: 13px;
        font-weight: 600;
        box-shadow: inset 0 0 0 1px rgba(255,255,255,0.02);
      }

      .chip .mini {
        width: 16px;
        height: 16px;
        display: inline-block;
        background: rgba(255,255,255,0.18);
        border-radius: 5px;
        position: relative;
      }

      .chip .mini::before {
        content: "";
        position: absolute;
        inset: 3px;
        border-radius: 4px;
        background: rgba(255,255,255,0.85);
      }

      .chip .mini.game::before {
        background: linear-gradient(135deg, #ffffff, #d9d9d9);
      }

      .chip .mini.music::before {
        background: linear-gradient(135deg, #f9e38d, #caa72d);
      }

      .chip .mini.movie::before {
        background: linear-gradient(135deg, #ff9cb0, #ff5978);
      }

      .chip .mini.ai::before {
        background: linear-gradient(135deg, #71d7ff, #5d7eff);
      }

      .chip .mini.chat::before {
        background: linear-gradient(135deg, #73ffbb, #27b96a);
      }

      .chip .mini.vm::before {
        background: linear-gradient(135deg, #ffbe70, #ff8a00);
      }

      .chip .badge-small {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        min-width: 28px;
        height: 18px;
        border-radius: 999px;
        background: linear-gradient(135deg, #ff4f7c, #ff2d61);
        color: #fff;
        font-size: 10px;
        font-weight: 800;
        padding: 0 7px;
      }

      .bottom-status {
        position: absolute;
        right: 20px;
        bottom: 12px;
        color: rgba(255,255,255,0.62);
        font-size: 12px;
        letter-spacing: 0.02em;
      }
    </style>
  </head>
  <body>
    <div class="page">
      <div class="app-shell">
        <aside class="sidebar">
          <div class="app-icons">
            <div class="icon-row">
              <div class="icon red active">▶</div>
              <div class="icon orange">✦</div>
              <div class="icon dark">G</div>
            </div>
            <div class="icon-row">
              <div class="icon green">◉</div>
              <div class="icon dark">◌</div>
              <div class="icon dark">⊕</div>
            </div>
          </div>

          <div class="nav-area">
            <div class="tabs-header">Tabs</div>

            <button class="tab active">
              <span class="dot">⌂</span>
              <span>Home</span>
            </button>

            <button class="tab">
              <span class="dot">◫</span>
              <span>Games</span>
            </button>

            <button class="tab">
              <span class="dot">♫</span>
              <span>Music</span>
            </button>

            <button class="tab">
              <span class="dot">▶</span>
              <span>Movies</span>
            </button>

            <button class="tab">
              <span class="dot">✦</span>
              <span>AI</span>
            </button>

            <button class="tab">
              <span class="dot">☰</span>
              <span>Chat</span>
              <span class="badge">99+</span>
            </button>

            <button class="tab">
              <span class="dot">◫</span>
              <span>VMs</span>
            </button>

            <button class="tab">
              <span class="dot">⌁</span>
              <span>Linkgen</span>
            </button>

            <button class="tab">
              <span class="dot">◍</span>
              <span>Shop</span>
            </button>

            <button class="tab">
              <span class="dot">⚙</span>
              <span>Settings</span>
            </button>
          </div>

          <div class="nav-bottom">
            <button class="tab">
              <span>Join our Discord</span>
            </button>
          </div>
        </aside>

        <main class="main">
          <header class="browser-bar">
            <div class="browser-controls">
              <div class="nav-button">←</div>
              <div class="nav-button">→</div>
              <div class="nav-button">↻</div>
            </div>

            <div class="address-bar">
              <span class="search-glass">⌕</span>
              <span class="address-text">Search or enter website name</span>
            </div>

            <div class="user-pill">
              <span>Cyrus520papa92</span>
              <span class="dot"></span>
              <span style="font-size: 12px; font-weight: 700; color: rgba(255,255,255,0.85);">4</span>
            </div>
          </header>

          <div class="hero">
            <div class="hero-shape"></div>
            <div class="hero-content">
              <div class="brand">achroma</div>

              <div class="search-box">
                <span class="icon">⌕</span>
                <input type="text" placeholder="Search anything..." />
              </div>

              <div class="chip-row">
                <div class="chip"><span class="mini game"></span> Games</div>
                <div class="chip"><span class="mini music"></span> Music</div>
                <div class="chip"><span class="mini movie"></span> Movies</div>
                <div class="chip"><span class="mini ai"></span> AI</div>
                <div class="chip"><span class="mini chat"></span> Chat</div>
                <div class="chip"><span class="mini vm"></span> VMs</div>
              </div>
            </div>
          </div>

          <div class="bottom-status">
            537e050 • v1 • 70 ms
          </div>
        </main>
      </div>
    </div>
  </body>
</html>
