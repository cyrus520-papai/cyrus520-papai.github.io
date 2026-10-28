#808080.achroma {
  background: #808080;
  color: #ffffff;
}.achroma {
  background: rgb(128, 128, 128);
}<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Achroma Exact</title>
  <style>
    :root {
      --achroma: #808080;
      --dark: #666666;
      --mid: #8a8a8a;
      --light: #9a9a9a;
      --panel: rgba(255,255,255,0.08);
      --text: #ffffff;
      --line: rgba(0,0,0,0.18);
    }

    * { box-sizing: border-box; }

    body {
      margin: 0;
      background: #000;
      display: grid;
      place-items: center;
      height: 100vh;
      font-family: Arial, sans-serif;
    }

    .browser {
      width: 900px;
      height: 560px;
      background: var(--achroma);
      border: 1px solid rgba(0,0,0,0.2);
      box-shadow: 0 20px 40px rgba(0,0,0,0.25);
      overflow: hidden;
    }

    .titlebar {
      height: 58px;
      background: var(--mid);
      border-bottom: 1px solid var(--line);
      display: flex;
      align-items: center;
      padding: 0 18px;
      position: relative;
    }

    .traffic {
      display: flex;
      gap: 10px;
      align-items: center;
    }

    .dot {
      width: 12px;
      height: 12px;
      border-radius: 50%;
      background: rgba(255,255,255,0.7);
      border: 1px solid rgba(0,0,0,0.15);
    }

    .tab {
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      color: var(--text);
      font-size: 14px;
      font-weight: 700;
      letter-spacing: 0.12em;
      text-transform: uppercase;
    }

    .toolbar {
      height: 58px;
      background: var(--light);
      border-bottom: 1px solid var(--line);
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 0 18px;
    }

    .nav {
      width: 24px;
      height: 24px;
      border-radius: 50%;
      background: rgba(255,255,255,0.08);
      border: 1px solid rgba(0,0,0,0.12);
      position: relative;
    }

    .nav::before {
      content: "";
      position: absolute;
      width: 8px;
      height: 8px;
      border: 2px solid rgba(255,255,255,0.85);
      border-top: 0;
      border-right: 0;
      left: 9px;
      top: 7px;
      transform: rotate(45deg);
    }

    .nav.forward {
      transform: rotate(180deg);
    }

    .address {
      flex: 1;
      height: 34px;
      border-radius: 18px;
      background: rgba(255,255,255,0.08);
      border: 1px solid rgba(0,0,0,0.14);
      display: flex;
      align-items: center;
      padding: 0 16px;
      color: var(--text);
      font-size: 13px;
    }

    .page {
      height: calc(100% - 116px);
      background: var(--achroma);
      padding: 18px 18px 0;
    }

    .content {
      width: 100%;
      height: 100%;
      background: rgba(255,255,255,0.03);
      border: 1px solid rgba(0,0,0,0.08);
      position: relative;
    }

    .header {
      position: absolute;
      left: 18px;
      top: 18px;
      font-size: 15px;
      font-weight: 700;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--text);
    }

    .bars {
      position: absolute;
      left: 18px;
      top: 56px;
      width: 60%;
      display: flex;
      flex-direction: column;
      gap: 16px;
    }

    .bar {
      height: 18px;
      background: rgba(255,255,255,0.12);
      border-radius: 10px;
    }

    .bar:nth-child(2) { width: 82%; }
    .bar:nth-child(3) { width: 60%; }

    .card {
      position: absolute;
      left: 18px;
      bottom: 18px;
      width: 200px;
      height: 120px;
      background: rgba(255,255,255,0.08);
      border: 1px solid rgba(0,0,0,0.1);
    }
  </style>
</head>
<body>
  <div class="browser">
    <div class="titlebar">
      <div class="traffic">
        <div class="dot"></div>
        <div class="dot"></div>
        <div class="dot"></div>
      </div>
      <div class="tab">ACHROMA</div>
    </div>

    <div class="toolbar">
      <div class="nav"></div>
      <div class="nav forward"></div>
      <div class="address">achroma.example</div>
    </div>

    <div class="page">
      <div class="content">
        <div class="header">BROWSER PAGE</div>

        <div class="bars">
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
        </div>

        <div class="card"></div>
      </div>
    </div>
  </div>
</body>
</html>
