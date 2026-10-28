<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Achroma Browser Mock</title>
  <style>
    :root {
      --bg: #000000;
      --chrome-1: #777777;
      --chrome-2: #7e7e7e;
      --chrome-3: #8e8e8e;
      --chrome-4: #a2a2a2;
      --surface: #8b8b8b;
      --surface-2: #959595;
      --panel: rgba(255,255,255,0.06);
      --line: rgba(0,0,0,0.18);
      --text: rgba(255,255,255,0.96);
      --muted: rgba(255,255,255,0.8);
      --shadow: rgba(0,0,0,0.28);
    }

    * {
      box-sizing: border-box;
    }

    html, body {
      margin: 0;
      width: 100%;
      height: 100%;
      background: var(--bg);
      font-family: Arial, Helvetica, sans-serif;
      overflow: hidden;
    }

    body {
      display: grid;
      place-items: end center;
    }

    .window {
      width: min(900px, 90vw);
      height: min(580px, 80vh);
      background: var(--chrome-1);
      border: 1px solid rgba(0,0,0,0.25);
      box-shadow:
        0 26px 52px var(--shadow),
        inset 0 1px 0 rgba(255,255,255,0.14);
      position: relative;
      overflow: hidden;
    }

    .window::before {
      content: "";
      position: absolute;
      inset: 0;
      background: linear-gradient(
        180deg,
        rgba(255,255,255,0.08),
        rgba(255,255,255,0) 18%,
        rgba(0,0,0,0.04) 100%
      );
      pointer-events: none;
    }

    .titlebar {
      position: relative;
      z-index: 1;
      height: 60px;
      background: var(--chrome-2);
      border-bottom: 1px solid var(--line);
      display: flex;
      align-items: center;
      padding: 0 18px;
    }

    .traffic {
      display: flex;
      align-items: center;
      gap: 10px;
      margin-right: 12px;
    }

    .dot {
      width: 13px;
      height: 13px;
      border-radius: 50%;
      background: rgba(255,255,255,0.75);
      border: 1px solid rgba(0,0,0,0.18);
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.2);
    }

    .dot:nth-child(1) { background: #dadada; }
    .dot:nth-child(2) { background: #d0d0d0; }
    .dot:nth-child(3) { background: #c4c4c4; }

    .tab-title {
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      color: rgba(255,255,255,0.96);
      font-size: 15px;
      font-weight: 700;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      user-select: none;
    }

    .toolbar {
      position: relative;
      z-index: 1;
      height: 62px;
      background: var(--chrome-3);
      border-bottom: 1px solid var(--line);
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 0 16px;
    }

    .nav {
      width: 28px;
      height: 28px;
      border-radius: 50%;
      background: rgba(255,255,255,0.08);
      border: 1px solid rgba(0,0,0,0.12);
      position: relative;
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.12);
    }

    .nav::before {
      content: "";
      position: absolute;
      width: 8px;
      height: 8px;
      border: 2px solid rgba(255,255,255,0.9);
      border-top: 0;
      border-right: 0;
      left: 10px;
      top: 8px;
      transform: rotate(45deg);
    }

    .nav.forward { transform: rotate(180deg); }

    .address {
      flex: 1;
      height: 34px;
      border-radius: 18px;
      background: rgba(255,255,255,0.1);
      border: 1px solid rgba(0,0,0,0.15);
      display: flex;
      align-items: center;
      padding: 0 16px;
      color: var(--text);
      font-size: 13px;
      letter-spacing: 0.03em;
      user-select: none;
    }

    .lock {
      width: 10px;
      height: 10px;
      border: 2px solid rgba(255,255,255,0.82);
      border-radius: 3px;
      position: relative;
      margin-right: 10px;
      flex-shrink: 0;
    }

    .lock::before {
      content: "";
      position: absolute;
      width: 9px;
      height: 7px;
      border: 2px solid rgba(255,255,255,0.82);
      border-bottom: 0;
      border-radius: 9px 9px 0 0;
      left: -2px;
      top: -9px;
    }

    .page {
      position: relative;
      z-index: 1;
      height: calc(100% - 122px);
      background: linear-gradient(180deg, #8a8a8a 0%, #7f7f7f 100%);
      display: flex;
    }

    .sidebar {
      width: 250px;
      background: rgba(255,255,255,0.05);
      border-right: 1px solid var(--line);
      padding: 20px 16px 16px;
    }

    .side-label {
      width: 72%;
      height: 16px;
      border-radius: 8px;
      background: rgba(255,255,255,0.15);
      margin-bottom: 18px;
    }

    .side-item {
      height: 12px;
      border-radius: 6px;
      background: rgba(255,255,255,0.1);
      margin-bottom: 12px;
    }

    .side-item:nth-child(2) { width: 83%; }
    .side-item:nth-child(3) { width: 68%; }
    .side-item:nth-child(4) { width: 89%; }
    .side-item:nth-child(5) { width: 72%; }
    .side-item:nth-child(6) { width: 90%; }

    .content {
      flex: 1;
      padding: 22px 26px 18px;
    }

    .hero {
      height: 158px;
      background: linear-gradient(135deg, rgba(255,255,255,0.12), rgba(255,255,255,0.04));
      border: 1px solid rgba(0,0,0,0.14);
      border-radius: 16px;
      position: relative;
      overflow: hidden;
      margin-bottom: 18px;
    }

    .hero::before {
      content: "";
      position: absolute;
      inset: 0;
      background: linear-gradient(
        120deg,
        rgba(255,255,255,0.06),
        transparent 42%,
        rgba(0,0,0,0.06)
      );
    }

    .hero-bars {
      position: absolute;
      left: 20px;
      right: 20px;
      bottom: 18px;
      display: flex;
      align-items: end;
      gap: 18px;
    }

    .hero-bar {
      background: rgba(255,255,255,0.12);
      border-radius: 10px;
      height: 18px;
    }

    .hero-bar:nth-child(1) { width: 58%; height: 22px; }
    .hero-bar:nth-child(2) { width: 22%; height: 18px; }
    .hero-bar:nth-child(3) { width: 16%; height: 16px; }

    .cards {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 18px;
      height: calc(100% - 176px);
    }

    .card {
      position: relative;
      background: rgba(255,255,255,0.08);
      border: 1px solid rgba(0,0,0,0.14);
      border-radius: 14px;
      overflow: hidden;
    }

    .card::before {
      content: "";
      position: absolute;
      left: 16px;
      right: 18px;
      top: 18px;
      height: 16px;
      background: rgba(255,255,255,0.12);
      border-radius: 8px;
    }

    .card::after {
      content: "";
      position: absolute;
      left: 16px;
      right: 20px;
      bottom: 18px;
      height: 92px;
      background: rgba(255,255,255,0.08);
      border-radius: 10px;
    }

    .mini {
      position: absolute;
      right: 16px;
      top: 18px;
      width: 12px;
      height: 12px;
      border-radius: 50%;
      background: rgba(255,255,255,0.18);
      border: 1px solid rgba(0,0,0,0.12);
    }

    @media (max-width: 760px) {
      .sidebar { display: none; }
      .cards { grid-template-columns: 1fr; }
      .tab-title { letter-spacing: 0.08em; }
    }
  </style>
</head>
<body>
  <div class="window">
    <div class="titlebar">
      <div class="traffic">
        <div class="dot"></div>
        <div class="dot"></div>
        <div class="dot"></div>
      </div>

      <div class="tab-title">ACHROMA</div>
    </div>

    <div class="toolbar">
      <div class="nav"></div>
      <div class="nav forward"></div>

      <div class="address">
        <span class="lock"></span>
        achroma.example
      </div>
    </div>

    <div class="page">
      <aside class="sidebar">
        <div class="side-label"></div>
        <div class="side-item"></div>
        <div class="side-item"></div>
        <div class="side-item"></div>
        <div class="side-item"></div>
        <div class="side-item"></div>
      </aside>

      <main class="content">
        <div class="hero">
          <div class="hero-bars">
            <div class="hero-bar"></div>
            <div class="hero-bar"></div>
            <div class="hero-bar"></div>
          </div>
        </div>

        <div class="cards">
          <div class="card"><div class="mini"></div></div>
          <div class="card"><div class="mini"></div></div>
          <div class="card"><div class="mini"></div></div>
        </div>
      </main>
    </div>
  </div>
</body>
</html>
