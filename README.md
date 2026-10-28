<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Achroma Browser</title>
  <style>
    :root {
      --achroma: #808080;
      --achroma-1: #6b6b6b;
      --achroma-2: #7a7a7a;
      --achroma-3: #8b8b8b;
      --achroma-4: #9a9a9a;
      --achroma-5: #b2b2b2;
      --chrome: #7d7d7d;
      --chrome-dark: #666666;
      --chrome-light: #a3a3a3;
      --surface: #8f8f8f;
      --surface-2: #9f9f9f;
      --line: rgba(0,0,0,0.18);
      --shadow: rgba(0,0,0,0.25);
      --text: #f4f4f4;
      --muted: #efefef;
      --glass: rgba(255,255,255,0.08);
    }

    * { box-sizing: border-box; }

    html, body {
      height: 100%;
      margin: 0;
      background: var(--achroma);
      font-family: "Segoe UI", Arial, sans-serif;
    }

    body {
      display: grid;
      place-items: center;
    }

    .window {
      width: min(1080px, 90vw);
      height: min(760px, 82vh);
      background: var(--chrome);
      border: 2px solid rgba(0,0,0,0.28);
      border-radius: 18px;
      box-shadow:
        0 28px 70px rgba(0,0,0,0.28),
        inset 0 1px 0 rgba(255,255,255,0.18);
      overflow: hidden;
      position: relative;
    }

    .window::before {
      content: "";
      position: absolute;
      inset: 0;
      background: linear-gradient(
        180deg,
        rgba(255,255,255,0.08),
        rgba(255,255,255,0) 18%,
        rgba(0,0,0,0.05) 100%
      );
      pointer-events: none;
    }

    .titlebar {
      height: 64px;
      background: var(--achroma);
      border-bottom: 1px solid var(--line);
      display: flex;
      align-items: center;
      padding: 0 18px;
      gap: 14px;
      position: relative;
      z-index: 1;
    }

    .traffic {
      display: flex;
      gap: 8px;
      align-items: center;
      margin-right: 8px;
    }

    .dot {
      width: 13px;
      height: 13px;
      border-radius: 50%;
      background: rgba(255,255,255,0.7);
      border: 1px solid rgba(0,0,0,0.12);
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.35);
    }

    .dot:nth-child(1) { background: #d7d7d7; }
    .dot:nth-child(2) { background: #cfcfcf; }
    .dot:nth-child(3) { background: #c6c6c6; }

    .tabs {
      display: flex;
      align-items: end;
      gap: 8px;
      flex: 1;
      min-width: 0;
    }

    .tab {
      min-width: 160px;
      max-width: 230px;
      height: 36px;
      background: rgba(255,255,255,0.08);
      border: 1px solid rgba(0,0,0,0.16);
      border-bottom: none;
      border-radius: 12px 12px 0 0;
      color: var(--text);
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 0 18px;
      font-size: 11px;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
      opacity: 0.82;
    }

    .tab.active {
      opacity: 1;
      background: rgba(255,255,255,0.12);
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.18);
    }

    .toolbar {
      height: 58px;
      background: var(--achroma-2);
      border-bottom: 1px solid var(--line);
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 0 16px;
      position: relative;
      z-index: 1;
    }

    .nav-btn {
      width: 30px;
      height: 30px;
      border-radius: 50%;
      background: rgba(255,255,255,0.08);
      border: 1px solid rgba(0,0,0,0.18);
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
      left: 11px;
      top: 9px;
      transform: rotate(45deg);
    }

    .nav-btn.forward {
      transform: rotate(180deg);
    }

    .address {
      flex: 1;
      height: 36px;
      border-radius: 19px;
      background: rgba(255,255,255,0.09);
      border: 1px solid rgba(0,0,0,0.18);
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.08);
      display: flex;
      align-items: center;
      padding: 0 16px;
      color: var(--muted);*

