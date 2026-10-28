<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Achroma Browser - Media Hub</title>
  <style>
    :root {
      --bg: #000;
      --browser: #7a7a7a;
      --browser-2: #828282;
      --browser-3: #8f8f8f;
      --browser-4: #a4a4a4;
      --surface: #8d8d8d;
      --panel: rgba(255,255,255,0.07);
      --panel-2: rgba(255,255,255,0.12);
      --line: rgba(0,0,0,0.18);
      --text: #f3f3f3;
      --muted: rgba(255,255,255,0.8);
      --shadow: rgba(0,0,0,0.28);
      --accent: rgba(255,255,255,0.14);
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
      width: min(1100px, 92vw);
      height: min(700px, 84vh);
      background: var(--browser);
      border: 1px solid rgba(0,0,0,0.20);
      box-shadow:
        0 28px 60px var(--shadow),
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
      background: var(--browser-2);
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
      z-index: 2;
    }

    .dot {
      width: 12px;
      height: 12px;
      border-radius: 50%;
      border: 1px solid rgba(0,0,0,0.14);
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.24);
    }

    .dot:nth-child(1) { background: #dadada; }
    .dot:nth-child(2) { background: #cfcfcf; }
    .dot:nth-child(3) { background: #c4c4c4; }

    .tab-title {
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      text-transform: uppercase;
      letter-spacing: 0.12em;
      font-weight: 700;
      font-size: 14px;
      color: rgba(255,255,255,0.96);
      user-select: none;
    }

    .toolbar {
      position: relative;
      z-index: 1;
      height: 58px;
      background: var(--browser-3);
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

    .nav.forward {
      transform: rotate(180deg);
    }

    .address {
      flex: 1;
      height: 34px;
      border-radius: 18px;
      background: rgba(255,255,255,0.10);
      border: 1px solid rgba(0,0,0,0.15);
      display: flex;
      align-items: center;
      padding: 0 16px;
      color: rgba(255,255,255,0.92);
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
      height: calc(100% - 116px);
      background: linear-gradient(180deg, #8d8d8d 0%, #7d7d7d 100%);
      display: flex;
    }

    .sidebar {
      width: 220px;
      background: rgba(255,255,255,0.04);
      border-right: 1px solid var(--line);
      padding: 18px 14px 10px;
    }

    .brand {
      width: 100%;
      height: 36px;
      display: flex;
      align-items: center;
      padding: 0 10px;
      margin-bottom: 18px;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      font-weight: 700;
      color: rgba(255,255,255,0.9);
      font-size: 13px;
    }

    .menu {
      display: grid;
      gap: 8px;
    }

    .menu-item {
      height: 34px;
      border-radius: 10px;
      background: rgba(255,255,255,0.06);
      border: 1px solid rgba(0,0,0,0.08);
      display: flex;
      align-items: center;
      padding: 0 12px;
      color: rgba(255,255,255,0.85);
      font-size: 12px;
      letter-spacing: 0.06em;
      text-transform: uppercase;
    }

    .menu-item.active {
      background: rgba(255,255,255,0.12);
    }

    .main {
      flex: 1;
      padding: 18px 20px 14px;
      overflow: hidden;
    }

    .hero {
      height: 180px;
      background:
        linear-gradient(135deg, rgba(255,255,255,0.16), rgba(255,255,255,0.04)),
        linear-gradient(120deg, rgba(255,255,255,0.08), transparent 45%);
      border: 1px solid rgba(0,0,0,0.14);
      border-radius: 16px;
      position: relative;
      overflow: hidden;
      margin-bottom: 16px;
    }

    .hero::before {
      content: "";
      position: absolute;
      inset: 0;
      background: linear-gradient(90deg, rgba(255,255,255,0.08), transparent 40%, rgba(0,0,0,0.08));
    }

    .hero-content {
      position: absolute;
      left: 20px;
      right: 20px;
      bottom: 18px;
      display: flex;
      align-items: end;
      justify-content: space-between;
      gap: 12px;
    }

    .hero-text {
      flex: 1;
      display: grid;
      gap: 8px;
    }

    .hero-line {
      height: 16px;
      border-radius: 10px;
      background: rgba(255,255,255,0.15);
    }

    .hero-line:nth-child(1) { width: 52%; }
    .hero-line:nth-child(2) { width: 35%; }

    .cta {
      width: 120px;
      height: 34px;
      border-radius: 18px;
      background: rgba(255,255,255,0.12);
      border: 1px solid rgba(0,0,0,0.12);
    }

    .section {
      margin-top: 18px;
    }

    .section-head {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 12px;
      text-transform: uppercase;
      letter-spacing: 0.08em;
      font-size: 12px;
      color: rgba(255,255,255,0.9);
    }

    .section-head .more {
      opacity: 0.7;
    }

    .card-row {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 14px;
    }

    .card {
      height: 160px;
      border-radius: 14px;
      background: rgba(*

