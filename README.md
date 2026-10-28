<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Achroma Real App Shell</title>
  <style>
    :root {
      --bg: #000000;
      --shell: #7a7a7a;
      --shell-2: #808080;
      --shell-3: #8d8d8d;
      --shell-4: #9d9d9d;
      --surface: #8b8b8b;
      --surface-2: #969696;
      --surface-3: #a7a7a7;
      --panel: rgba(255,255,255,0.08);
      --panel-strong: rgba(255,255,255,0.12);
      --line: rgba(0,0,0,0.18);
      --text: rgba(255,255,255,0.96);
      --muted: rgba(255,255,255,0.72);
      --shadow: rgba(0,0,0,0.26);
    }

    * { box-sizing: border-box; }

    html, body {
      margin: 0;
      width: 100%;
      height: 100%;
      background: var(--bg);
      color: var(--text);
      font-family: Arial, Helvetica, sans-serif;
      overflow: hidden;
    }

    body {
      display: grid;
      place-items: center;
    }

    .window {
      width: min(980px, 90vw);
      height: min(620px, 82vh);
      background: var(--shell);
      border: 1px solid rgba(0,0,0,0.24);
      box-shadow:
        0 26px 56px var(--shadow),
        inset 0 1px 0 rgba(255,255,255,0.12);
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
      height: 58px;
      background: var(--shell-2);
      border-bottom: 1px solid var(--line);
      display: flex;
      align-items: center;
      padding: 0 18px;
    }

    .traffic {
      display: flex;
      gap: 10px;
      align-items: center;
      width: 110px;
    }

    .dot {
      width: 12px;
      height: 12px;
      border-radius: 50%;
      border: 1px solid rgba(0,0,0,0.16);
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.22);
    }

    .dot:nth-child(1) { background: #d9d9d9; }
    .dot:nth-child(2) { background: #d0d0d0; }
    .dot:nth-child(3) { background: #c7c7c7; }

    .tab-title {
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      font-size: 14px;
      font-weight: 700;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      color: rgba(255,255,255,0.96);
      user-select: none;
    }

    .toolbar {
      position: relative;
      z-index: 1;
      height: 60px;
      background: var(--shell-3);
      border-bottom: 1px solid var(--line);
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 0 16px;
    }

    .nav-btn {
      width: 26px;
      height: 26px;
      border-radius: 50%;
      background: rgba(255,255,255,0.08);
      border: 1px solid rgba(0,0,0,0.12);
      position: relative;
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.12);
    }

    .nav-btn::before {
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

    .nav-btn.forward { transform: rotate(180deg); }

    .address {
      flex: 1;
      height: 34px;
      border-radius: 18px;
      background: rgba(255,255,255,0.10);
      border: 1px solid rgba(0,0,0,0.16);
      display: flex;
      align-items: center;
      padding: 0 16px;
      color: var(--text);
      font-size: 13px;
      letter-spacing: 0.04em;
      user-select: none;
    }

    .lock {
      width: 10px;
      height: 10px;
      border: 2px solid rgba(255,255,255,0.82);
      border-radius: 3px;
      margin-right: 10px;
      position: relative;
      flex-shrink: 0;
    }

    .lock::before {
      content: "";
      position: absolute;
      width: 9px;
      height: 7px;
      border: 2px solid rgba(255,255,255,0.8);
      border-bottom: 0;
      border-radius: 9px 9px 0 0;
      left: -2px;
      top: -9px;
    }

    .app {
      position: relative;
      z-index: 1;
      height: calc(100% - 118px);
      background: linear-gradient(180deg, #8d8d8d 0%, #7f7f7f 100%);
      display: flex;
    }

    .sidebar {
      width: 220px;
      background: rgba(255,255,255,0.04);
      border-right: 1px solid var(--line);
      padding: 16px 12px;
    }

    .brand {
      height: 44px;
      display: flex;
      align-items: center;
      padding: 0 10px;
      text-transform: uppercase;
      letter-spacing: 0.12em;
      font-size: 12px;
      font-weight: 700;
      color: rgba(255,255,255,0.92);
    }

    .side-menu {
      display: grid;
      gap: 8px;
      margin-top:*

