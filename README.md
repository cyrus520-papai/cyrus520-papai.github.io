<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Achroma Browser Mock</title>
  <style>
    :root {
      --bg: #000000;
      --window-bg: #7a7a7a;
      --window-dark: #6b6b6b;
      --window-mid: #8b8b8b;
      --window-light: #a3a3a3;
      --page-bg: #8f8f8f;
      --panel-bg: rgba(255,255,255,0.08);
      --soft-line: rgba(0,0,0,0.18);
      --text: rgba(255,255,255,0.95);
      --muted: rgba(255,255,255,0.75);
    }

    * { box-sizing: border-box; }

    html, body {
      margin: 0;
      width: 100%;
      height: 100%;
      background: var(--bg);
      font-family: Arial, Helvetica, sans-serif;
    }

    body {
      display: flex;
      justify-content: center;
      align-items: flex-end;
      overflow: hidden;
    }

    .browser {
      width: 870px;
      height: 560px;
      background: var(--window-bg);
      border: 1px solid rgba(0,0,0,0.22);
      position: relative;
      box-shadow:
        inset 0 1px 0 rgba(255,255,255,0.12),
        0 0 0 1px rgba(255,255,255,0.03);
    }

    .doctype {
      position: absolute;
      left: 22px;
      top: 10px;
      font-family: "Courier New", monospace;
      font-size: 14px;
      font-weight: 700;
      color: rgba(0,0,0,0.72);
      letter-spacing: 0.02em;
      user-select: none;
    }

    .titlebar {
      position: absolute;
      left: 18px;
      right: 18px;
      top: 38px;
      height: 56px;
      background: var(--window-mid);
      border: 1px solid var(--soft-line);
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 0 14px;
    }

    .traffic {
      display: flex;
      align-items: center;
      gap: 10px;
      width: 76px;
      padding-left: 2px;
    }

    .dot {
      width: 12px;
      height: 12px;
      border-radius: 50%;
      background: rgba(255,255,255,0.7);
      border: 1px solid rgba(0,0,0,0.18);
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.25);
    }

    .dot:nth-child(1) { background: #d9d9d9; }
    .dot:nth-child(2) { background: #d1d1d1; }
    .dot:nth-child(3) { background: #c9c9c9; }

    .tablabel {
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      font-size: 15px;
      font-weight: 700;
      letter-spacing: 0.08em;
      color: rgba(255,255,255,0.9);
      text-transform: uppercase;
      user-select: none;
    }

    .toolbar {
      position: absolute;
      left: 18px;
      right: 18px;
      top: 94px;
      height: 62px;
      background: var(--window-light);
      border: 1px solid var(--soft-line);
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 0 16px;
    }

    .nav {
      width: 26px;
      height: 26px;
      border-radius: 50%;
      background: rgba(255,255,255,0.08);*

