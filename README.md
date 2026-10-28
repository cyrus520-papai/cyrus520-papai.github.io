<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Browser Mock</title>
  <style>
    :root{
      --bg:#000000;
      --browser:#7a7a7a;
      --browser2:#818181;
      --browser3:#8b8b8b;
      --windowtop:#818181;
      --toolbar:#8d8d8d;
      --page:#8a8a8a;
      --panel:#9a9a9a;
      --line:rgba(0,0,0,0.18);
      --text:#f3f3f3;
      --muted:rgba(255,255,255,0.8);
    }

    * { box-sizing: border-box; }

    html, body{
      margin:0;
      width:100%;
      height:100%;
      background:#000;
      font-family: Arial, Helvetica, sans-serif;
    }

    body{
      display:flex;
      align-items:flex-end;
      justify-content:center;
      padding:0;
      overflow:hidden;
    }

    .frame{
      width: 870px;
      height: 560px;
      position:relative;
      background: var(--browser);
      border: 1px solid rgba(0,0,0,0.22);
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.08);
      margin-bottom:0;
    }

    .doctype{
      position:absolute;
      left: 20px;
      top: 12px;
      font: 700 15px "Courier New", monospace;
      color: rgba(0,0,0,0.72);
      letter-spacing: 0.01em;
    }

    .browser{
      position:absolute;
      left: 18px;
      right: 18px;
      top: 42px;
      bottom: 14px;
      background: var(--browser);
      border: 1px solid rgba(0,0,0,0.18);
    }

    .titlebar{
      height: 58px;
      background: var(--windowtop);
      border-bottom: 1px solid var(--line);
      position:relative;
      display:flex;
      align-items:center;
      padding-left: 14px;
    }

    .traffic{
      display:flex;
      align-items:center;
      gap:10px;
      z-index:2;
    }

    .dot{
      width: 12px;
      height: 12px;
      border-radius:50%;
      background: rgba(255,255,255,0.75);
      border: 1px solid rgba(0,0,0,0.18);
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.18);
    }

    .dot:nth-child(1){ background:#d8d8d8; }
    .dot:nth-child(2){ background:#d0d0d0; }
    .dot:nth-child(3){ background:#c6c6c6; }

    .title{
      position:absolute;
      left:50%;
      transform:translateX(-50%);
      color: rgba(255,255,255,0.95);
      font-size: 15px;
      font-weight:700;
      letter-spacing: 0.10em;
      text-transform: uppercase;
      user-select:none;
    }

    .toolbar{
      height: 58px;
      background: var(--toolbar);
      border-bottom: 1px solid var(--line);
      display:flex;
      align-items:center;
      gap:12px;
      padding: 0 16px;
    }

    .nav{
      width:27px;
      height:27px;
      border-radius:50%;
      background: rgba(255,255,255,0.07);
      border: 1px solid rgba(0,0,0,0.12);
      position:relative;
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.12);
    }

    .nav::before{
      content:"";
      position:absolute;
      width:8px;
      height:8px;
      border:2px solid rgba(255,255,255,0.85);
      border-top:0;
      border-right:0;
      left: 10px;
      top: 8px;
      transform: rotate(45deg);
    }

    .nav.back{
      margin-right: -4px;
    }

    .nav.forward{
      transform: rotate(180deg);
    }

    .address{
      flex:1;
      height:34px;
      background: rgba(255,255,255,0.10);
      border:1px solid rgba(0,0,0,0.15);
      border-radius:18px;
      display:flex;
      align-items:center;
      color: rgba(255,255,255,0.88);
      padding: 0 16px;
      font-size: 14px;
      letter-spacing:0.03em;
      user-select:none;
    }

    .lock{
      position:relative;
      width:10px;
      height:10px;
      border:2px solid rgba(255,255,255,0.82);
      border-radius:3px;
      margin-right:10px;
      flex-shrink:0;
    }

    .lock::before{
      content:"";
      position:absolute;
      width:9px;
      height:7px;
      border:2px solid rgba(255,255,255,0.82);
      border-bottom:0;
      border-radius:9px 9px 0 0;
      left:-2px;
      top:-9px;
    }

    .page{
      position:absolute;
      left:0;
      right:0;
      top:116px;
      bottom:0;
      background: var(--page);
      padding: 18px 14px 0 14px;
    }

    .page-inner{
      position:relative;
      width:100%;
      height:100%;
      background: rgba(255,255,255,0.03);
      border: 1px solid rgba(0,0,0,0.06);
    }

    .label{
      position:absolute;
      left: 18px;
      top: 16px;
      color: rgba(255,255,255,0.95);
      font-size: 15px;
      font-weight:700;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      user-select:none;
    }

    .bars{
      position:absolute;
      left: 18px;
      top: 60px;
      width: 61%;
      display:flex;
      flex-direction:column;
      gap: 16px;
    }

    .bar{
      height: 18px;
      border-radius: 10px;
      background: rgba(255,255,255,0.12);
    }

    .bar:nth-child(2){ width: 83%; }
    .bar:nth-child(3){ width: 62%; }

    .card{
      position:absolute;
      left: 18px;
      bottom: 16px;
      width: 200px;
      height: 120px;
      background: rgba(255,255,255,0.08);
      border:1px solid rgba(0,0,0,0.09);
    }
  </style>
</head>
<body>
  <div class="frame">
    <div class="doctype">&lt;!DOCTYPE html&gt;</div>

    <div class="browser">
      <div class="titlebar">
        <div class="traffic">
          <div class="dot"></div>
          <div class="dot"></div>
          <div class="dot"></div>
        </div>
        <div class="title">ACHROMA</div>
      </div>

      <div class="toolbar">
        <div class="nav back"></div>
        <div class="nav forward"></div>

        <div class="address">
          <span class="lock"></span>
          achroma.example
        </div>
      </div>

      <div class="page">
        <div class="page-inner">
          <div class="label">BROWSER PAGE</div>

          <div class="bars">
            <div class="bar"></div>
            <div class="bar"></div>
            <div class="bar"></div>
          </div>

          <div class="card"></div>
        </div>
      </div>
    </div>
  </div>
</body>
</html>
