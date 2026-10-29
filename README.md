<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Cinema Quest</title>
    <style>
      :root {
        --bg: #0b1020;
        --panel: #111827;
        --panel-2: #1f2937;
        --panel-3: #273449;
        --gold: #f8c84c;
        --gold-2: #f59e0b;
        --text: #f3f4f6;
        --muted: #cbd5e1;
        --accent: #60a5fa;
        --success: #34d399;
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
        background:
          linear-gradient(180deg, rgba(12,18,30,0.9), rgba(8,12,18,1)),
          radial-gradient(circle at top, rgba(96,165,250,0.18), transparent 32%);
        font-family: Arial, sans-serif;
        color: var(--text);
      }

      .app {
        width: min(1200px, 96vw);
        min-height: 88vh;
        display: grid;
        grid-template-columns: minmax(0, 2.1fr) minmax(260px, 1fr);
        gap: 20px;
        background: rgba(17, 24, 39, 0.92);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 22px;
        box-shadow: 0 35px 60px rgba(0,0,0,0.35);
        overflow: hidden;
      }

      .movie-panel {
        display: flex;
        flex-direction: column;
        background: linear-gradient(180deg, #0f172a, #111827);
      }

      .topbar {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 18px 20px 12px;
        border-bottom: 1px solid rgba(255,255,255,0.06);
      }

      .brand {
        font-size: 1.15rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        font-weight: 800;
      }

      .status {
        background: rgba(255,255,255,0.05);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 999px;
        padding: 8px 12px;
        color: var(--muted);
        font-size: 0.9rem;
      }

      .video-wrap {
        position: relative;
        flex: 1;
        background: #000;
        min-height: 360px;
      }

      video {
        width: 100%;
        height: 100%;
        display: block;
        object-fit: cover;
        background: #000;
      }

      .overlay {
        position: absolute;
        inset: 0;
        pointer-events: none;
        background:
          linear-gradient(180deg, rgba(0, 0, 0, 0.15), rgba(0, 0, 0, 0.42)),
          radial-gradient(circle at 50% 20%, rgba(96,165,250,0.15), transparent 30%);
      }

      .info {
        padding: 16px 20px 18px;
        border-top: 1px solid rgba(255,255,255,0.06);
      }

      .movie-title {
        font-size: clamp(1.2rem, 2vw, 2rem);
        font-weight: 800;
        margin: 0 0 6px;
      }

      .meta {
        color: var(--muted);
        font-size: 0.95rem;
      }

      .side-panel {
        background: linear-gradient(180deg, var(--panel-2), var(--panel));
        border-left: 1px solid rgba(255,255,255,0.06);
        display: flex;
        flex-direction: column;
      }

      .side-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 18px 20px;
        border-bottom: 1px solid rgba(255,255,255,0.06);
      }

      .side-title {
        font-size: 1.05rem;
        font-weight: 800;
        letter-spacing: 0.04em;
        text-transform: uppercase;
      }

      .score {
        background: rgba(248, 200, 76, 0.12);
        border: 1px solid rgba(248, 200, 76, 0.35);
        color: var(--gold);
        border-radius: 999px;
        padding: 8px 12px;
        font-weight: 700;
        font-size: 0.9rem;
      }

      .game-area {
        position: relative;
        flex: 1;
        padding: 16px;
        background:
          linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01)),
          linear-gradient(180deg, #1a2436, #101725);
      }

      .mini-scene {
        position: relative;
        width: 100%;
        height: 100%;
        min-height: 360px;
        border-radius: 16px;
        overflow: hidden;
        border: 1px solid rgba(255,255,255,0.06);
        background:
          linear-gradient(180deg, rgba(59,130,246,0.12), rgba(0,0,0,0.15)),
          linear-gradient(180deg, #16253c 0%, #111827 28%, #111827 100%);
        box-shadow: inset 0 0 28px rgba(0,0,0,0.35);
      }

      .mini-scene::before {
        content: "";
        position: absolute;
        inset: 0;
        background:
          linear-gradient(transparent 0 76%, rgba(8,12,18,0.8) 76% 100%),
          linear-gradient(90deg, rgba(255,255,255,0.02) 0 5%, transparent 5% 100%);
        pointer-events: none;*

