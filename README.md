<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Disguised Browser</title>
  <style>
    :root {
      --achroma: #808080;
      --dark: #666666;
      --light: #9a9a9a;
      --panel: #a0a0a0;
      --text: #ffffff;
      --shadow: rgba(0,0,0,0.22);
    }

    * { box-sizing: border-box; }

    body {
      margin: 0;
      min-height: 100vh;
      display: grid;
      place-items: center;
      background: var(--achroma);
      font-family: Arial, sans-serif;
    }

    .browser {
      width: 860px;
      max-width: 90vw;
      background: var(--panel);
      border: 2px solid #6d6d6d;
      border-radius: 14px;
      box-shadow: 0 18px 40px var(--shadow);
      overflow: hidden;
    }

    .browser-top {
      height: 52px;
      background: var(--achroma);
      display: flex;
      align-items: center;
      padding: 0 14px;
      gap: 10px;
      border-bottom: 2px solid #707070;
    }

    .dot {
      width: 12px;
      height: 12px;
      border-radius: 50%;
      background: #d9d9d9;
      border: 1px solid rgba(0,0,0,0.2);
    }

    .tab {
      flex: 0 0 160px;
      height: 32px;
      background: #7e7e7e;
      border: 1px solid #666;
      border-bottom: none;
      border-radius: 10px 10px 0 0;
      display: flex;
      align-items: center;
      justify-content: center;
      color: var(--text);
      font-size: 12px;
      letter-spacing: 0.04em;
      text-transform: uppercase;
    }

    .browser-toolbar {
      height: 54px;
      background: #8a8a8a;
      border-bottom: 2px solid #707070;
      display: flex;
      align-items: center;
      padding: 0 14px;
      gap: 12px;
    }

    .nav-btn {
      width: 26px;
      height: 26px;
      border-radius: 50%;
      background: #b3b3b3;
      border: 1px solid rgba(0,0,0,0.25);
      position: relative;
    }

    .nav-btn::before {
      content: "";
      position: absolute;
      inset: 8px;
      border: 2px solid #5a5a5a;
      border-top: 0;
      border-right: 0;
      transform: rotate(45deg);
    }

    .nav-btn.back::before {
      transform: rotate(225deg);
      left: 11px;
    }

    .address {
      flex: 1;
      height: 34px;
      background: #a1a1a1;
      border: 1px solid #696969;
      border-radius: 17px;
      display: flex;
      align-items: center;
      padding: 0 16px;
      color: #efefef;
      font-size: 14px;
      letter-spacing: 0.02em;
    }

    .browser-body {
      height: 420px;
      background: linear-gradient(180deg, #8e8e8e 0%, #7f7f7f 100%);
      position: relative;
      padding: 18px;
    }

    .page {
      width: 100%;
      height: 100%;
      background: #9b9b9b;
      border: 1px solid #686868;
      border-radius: 8px;
      position: relative;
      overflow: hidden;
    }

    .page-header {
      height: 52px;
      background: rgba(255,255,255,0.08);
      border-bottom: 1px solid rgba(0,0,0,0.18);
      display: flex;
      align-items: center;
      padding: 0 18px;
      color: #f5f5f5;
      font-weight: 700;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      font-size: 12px;
    }

    .columns {
      display: grid;
      grid-template-columns: 1.2fr 2.2fr;
      height: calc(100% - 52px);
    }

    .sidebar {
      background: rgba(255,255,255,0.06);
      border-right: 1px solid rgba(0,0,0,0.18);
      padding: 20px 16px;
    }

    .menu-item {
      height: 18px;
      background: rgba(255,255,255,0.12);
      border-radius: 8px;
      margin-bottom: 14px;
    }

    .content {
      padding: 22px 24px;
    }

    .hero {
      width: 100%;
      height: 120px;
      background: rgba(255,255,255,0.12);
      border-radius: 10px;
      margin-bottom: 20px;
    }

    .grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 14px;
    }

    .card {
      height: 120px;
      background: rgba(255,255,255,0.1);
      border-radius: 10px;
    }
  </style>
</head>
<body>
  <div class="browser">
    <div class="browser-top">
      <div class="dot"></div>
      <div class="dot"></div>
      <div class="dot"></div>
      <div class="tab">Achroma</div>
    </div>

    <div class="browser-toolbar">
      <div class="nav-btn back"></div>
      <div class="nav-btn" style="transform: rotate(180deg);"></div>
      <div class="address">achroma.example</div>
    </div>

    <div class="browser-body">
      <div class="page">
        <div class="page-header">Browser Page</div>
        <div class="columns">
          <div class="sidebar">
            <div class="menu-item" style="width: 78%;"></div>
            <div class="menu-item" style="width: 92%;"></div>
            <div class="menu-item" style="width: 64%;"></div>
            <div class="menu-item" style="width: 88%;"></div>
          </div>
          <div class="content">
            <div class="hero"></div>
            <div class="grid">
              <div class="card"></div>
              <div class="card"></div>
              <div class="card"></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</body>
</html>
