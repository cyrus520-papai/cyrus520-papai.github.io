<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Exact Browser Mock</title>
  <style>
    :root{
      --bg:#000000;
      --outer:#7a7a7a;
      --outer-2:#7e7e7e;
      --topbar:#7e7e7e;
      --toolbar:#8d8d8d;
      --page:#8a8a8a;
      --page2:#9c9c9c;
      --line:rgba(0,0,0,0.18);
      --text:rgba(255,255,255,0.92);
      --muted:rgba(255,255,255,0.72);
      --darktext:rgba(0,0,0,0.70);
    }

    * { box-sizing: border-box; }

    html, body{
      margin:0;
      width:100%;
      height:100%;
      background:var(--bg);
      overflow:hidden;
      font-family: Arial, Helvetica, sans-serif;
    }

    body{
      display:flex;
      align-items:flex-end;
      justify-content:center;
      padding:0;
    }

    .canvas{
      position:relative;
      width: 870px;
      height: 560px;
      background: var(--outer);
      border: 1px solid rgba(0,0,0,0.18);
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.06);
    }

    .doctype{
      position:absolute;
      left: 18px;
      top: 12px;
      font-family: "Courier New", monospace;
      font-size: 14px;
      font-weight: 700;
      color: var(--darktext);
      letter-spacing: 0.01em;
      user-select:none;
    }

    .browser{
      position:absolute;
      left: 16px;
      right: 16px;
      top: 42px;
      bottom: 16px;
      background: var(--outer);
      border: 1px solid rgba(0,0,0,0.16);
      overflow:hidden;
    }

    .browser-top{
      position:relative;
      height: 54px;
      background: var(--topbar);
      border-bottom: 1px solid var(--line);
      display:flex;
      align-items:center;
      padding-left: 14px;
    }

    .traffic{
      display:flex;
      align-items:center;
      gap: 10px;
      z-index:2;
    }

    .dot{
      width: 12px;
      height: 12px;
      border-radius:50%;
      border: 1px solid rgba(0,0,0,0.15);
      background: rgba(255,255,255,0.76);
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.18);
    }

    .dot:nth-child(1){ background:#d8d8d8; }
    .dot:nth-child(2){ background:#d0d0d0; }
    .dot:nth-child(3){ background:#c8c8c8; }

    .title{
      position:absolute;
      left:50%;
      transform:translateX(-50%);
      color: rgba(255,255,255,0.92);
      font-size: 15px;
      font-weight: 700;
      letter-spacing: 0.10em;
      text-transform: uppercase;
      user-select:none;
    }

    .toolbar{
      position:relative;
      height: 60px;
      background: var(--toolbar);
      border-bottom: 1px solid var(--line);
      display:flex;
      align-items:center;
      gap: 12px;
      padding: 0 16px;
    }

    .nav{
      width: 22px;
      height: 22px;
      border-radius:50%;
      border: 1px solid rgba(0,0,0,0.12);
      background: rgba(255,255,255,0.08);
      position:relative;
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.10);
    }

    .nav::before{
      content:"";
      position:absolute;
      width: 7px;
      height: 7px;
      border: 2px solid rgba(255,255,255,0.85);
      border-top: 0;
      border-right: 0;
      left: 8px;
      top: 6px;
      transform: rotate(45deg);
    }

    .nav.forward{
      transform: rotate(180deg);
      margin-left: -2px;
    }

    .address{
      flex:1;
      height: 32px;
      background: rgba(255,255,255,0.10);
      border: 1px solid rgba(0,0,0,0.12);
      border-radius: 17px;
      display:flex;
      align-items:center;
      padding: 0 14px;
      color: rgba(255,255,255,0.92);
      font-size: 13px;
      letter-spacing: 0.02em;
      user-select:none;
    }

    .lock{
      width: 10px;
      height: 10px;
      border: 2px solid rgba(255,255,255,0.8);
      border-radius: 3px;
      position:relative;
      margin-right:9px;
      flex-shrink:0;
    }

    .lock::before{
      content:"";
      position:absolute;
      width: 9px;
      height: 7px;
      border: 2px solid rgba(255,255,255,0.8);
      border-bottom:0;
      border-radius: 8px 8px 0 0;
      left:-2px;
      top:-9px;
    }

    .page{
      position:absolute;
      left:0;
      right:0;
      top: 114px;
      bottom:0;
      background: var(--page);
      padding: 18px 18px 0 18px;
    }

    .page-inner{
      position:relative;
      width:100%;
      height:100%;
      background: rgba(255,255,255,0.03);
      border: 1px solid rgba(0,0,0,0.06);
    }

    .page-label{
      position:absolute;
      left: 18px;
      top: 18px;
      color: rgba(255,255,255,0.92);
      font-size: 15px;
      font-weight: 700;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      user-select:none;
    }

    .bars{
      position:absolute;
      left: 18px;
      top: 54px;
      width: 62%;
      display:flex;
      flex-direction:column;
      gap: 15px;
    }

    .bar{
      height: 18px;
      border-radius: 10px;
      background: rgba(255,255,255,0.12);
    }

    .bar:nth-child(2){ width: 78%; }
    .bar:nth-child(3){ width: 58%; }

    .card{
      position:absolute;
      left: 18px;
      bottom: 18px;
      width: 200px;
      height: 120px;
      background: rgba(255,255,255,0.06);
      border: 1px solid rgba(0,0,0,0.10);
    }
  </style>
</head>
<body>
  <div class="canvas">
    <div class="doctype">&lt;!DOCTYPE html&gt;</div>

    <div class="browser">
      <div class="browser-top">
        <div class="traffic">
          <div class="dot"></div>
          <div class="dot"></div>
          <div class="dot"></div>
        </div>
        <div class="title">ACHROMA</div>
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
        <div class="page-inner">
          <div class="page-label">BROWSER PAGE</div>

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
