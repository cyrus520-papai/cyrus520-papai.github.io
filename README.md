#808080<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Achroma Real</title>
  <style>
    :root{
      --achroma: #808080;
      --achroma-1: #727272;
      --achroma-2: #7a7a7a;
      --achroma-3: #8a8a8a;
      --achroma-4: #a0a0a0;
      --chrome: #7d7d7d;
      --chrome-2: #8d8d8d;
      --panel: rgba(255,255,255,0.07);
      --panel-strong: rgba(255,255,255,0.12);
      --line: rgba(0,0,0,0.18);
      --text: rgba(255,255,255,0.96);
      --muted: rgba(255,255,255,0.72);
      --shadow: rgba(0,0,0,0.28);
    }

    * { box-sizing: border-box; }

    html, body {
      margin: 0;
      width: 100%;
      height: 100%;
      background: #000;
      font-family: Arial, Helvetica, sans-serif;
      color: var(--text);
      overflow: hidden;
    }

    body {
      display: grid;
      place-items: center;
    }

    .browser {
      width: min(1010px, 90vw);
      height: min(620px, 82vh);
      background: var(--chrome);
      border: 1px solid rgba(0,0,0,0.24);
      box-shadow:
        0 28px 60px var(--shadow),
        inset 0 1px 0 rgba(255,255,255,0.12);
      position: relative;
      overflow: hidden;
    }

    .browser::before{
      content:"";
      position:absolute;
      inset:0;
      background:linear-gradient(
        180deg,
        rgba(255,255,255,0.08),
        rgba(255,255,255,0) 18%,
        rgba(0,0,0,0.04) 100%
      );
      pointer-events:none;
    }

    .titlebar{
      position:relative;
      z-index:1;
      height:58px;
      background:var(--achroma-2);
      border-bottom:1px solid var(--line);
      display:flex;
      align-items:center;
      padding:0 18px;
    }

    .traffic{
      display:flex;
      gap:10px;
      align-items:center;
      width:100px;
      z-index:2;
    }

    .dot{
      width:12px;
      height:12px;
      border-radius:50%;
      border:1px solid rgba(0,0,0,0.15);
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.2);
    }

    .dot:nth-child(1){ background:#dedede; }
    .dot:nth-child(2){ background:#d1d1d1; }
    .dot:nth-child(3){ background:#c5c5c5; }

    .tab-title{
      position:absolute;
      left:50%;
      transform:translateX(-50%);
      text-transform:uppercase;
      letter-spacing:0.14em;
      font-size:14px;
      font-weight:700;
      color:rgba(255,255,255,0.96);
      user-select:none;
    }

    .toolbar{
      position:relative;
      z-index:1;
      height:60px;
      background:var(--achroma-3);
      border-bottom:1px solid var(--line);
      display:flex;
      align-items:center;
      gap:12px;
      padding:0 16px;
    }

    .nav-btn{
      width:26px;
      height:26px;
      border-radius:50%;
      background:rgba(255,255,255,0.08);
      border:1px solid rgba(0,0,0,0.12);
      position:relative;
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.12);
    }

    .nav-btn::before{
      content:"";
      position:absolute;
      width:8px;
      height:8px;
      border:2px solid rgba(255,255,255,0.9);
      border-top:0;
      border-right:0;
      left:9px;
      top:8px;
      transform:rotate(45deg);
    }

    .nav-btn.forward{
      transform:rotate(180deg);
    }

    .address{
      flex:1;
      height:34px;
      border-radius:18px;
      background:rgba(255,255,255,0.11);
      border:1px solid rgba(0,0,0,0.14);
      display:flex;
      align-items:center;
      padding:0 16px;
      color:var(--text);
      font-size:13px;
      letter-spacing:0.03em;
      user-select:none;
    }

    .lock{
      width:10px;
      height:10px;
      border:2px solid rgba(255,255,255,0.82);
      border-radius:3px;
      position:relative;
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

    .app{
      position:relative;
      z-index:1;
      height:calc(100% - 118px);
      background:linear-gradient(180deg, #8a8a8a 0%, #7d7d7d 100%);
      display:flex;
    }

    .sidebar{
      width:220px;
      background:rgba(255,255,255,0.04);
      border-right:1px solid var(--line);
      padding:16px 12px 8px;
    }

    .brand{
      height:40px;
      display:flex;
      align-items:center;
      justify-content:center;
      text-transform:uppercase;
      letter-spacing:0.14em;
      font-size:12px;
      font-weight:700;
      color:rgba(255,255,255,0.95);
    }

    .nav-list{
      display:grid;
      gap:8px;
      margin-top:12px;
    }

    .nav-item{
      height:34px;
      border-radius:10px;
      background:rgba(255,255,255,0.06);
      border:1px solid rgba(0,0,0,0.08);
      display:flex;
      align-items:center;
      padding:0 12px;
      color:rgba(255,255,255,0.82);
      letter-spacing:0.08em;
      text-transform:uppercase;
      font-size:10px;
    }

    .nav-item.active{
      background:rgba(255,255,255,0.12);
      color:rgba(255,255,255,0.96);
    }

    .main{
      flex:1;
      display:flex;
      flex-direction:column;
      padding:18px 18px 12px;
      gap:14px;
    }

    .hero{
      height:130px;
      border-radius:16px;
      background:
        linear-gradient(135deg, rgba(255,255,255,0.16), rgba(255,255,255,0.04)),
        linear-gradient(120deg, rgba(255,255,255,0.08), transparent 40%);
      border:1px solid rgba(0,0,0,0.14);
      position:relative;
      overflow:hidden;
    }

    .hero::before{
      content:"";
      position:absolute;
      inset:0;
      background:linear-gradient(90deg, rgba(255,255,255,0.08), transparent 46%, rgba(0,0,0,0.06));
    }

    .hero-content{
      position:absolute;
      left:18px;
      right:18px;
      bottom:16px;
      display:flex;
      align-items:end;
      gap:12px;
    }

    .hero-line{
      height:14px;
      background:rgba(255,255,255,0.14);
      border-radius:8px;
    }

    .hero-line:nth-child(1){ width:42%; height:18px; }
    .hero-line:nth-child(2){ width:26%; }
    .hero-line:nth-child(3){ width:16%; }

    .section{
      display:grid;
      gap:10px;
    }

    .section-head{
      display:flex;
      align-items:center;
      justify-content:space-between;
      padding:0 2px;
      font-size:10px;
      letter-spacing:0.12em;
      text-transform:uppercase;
      color:rgba(255,255,255,0.92);
    }

    .cards{
      display:grid;
      grid-template-columns:repeat(4, minmax(0, 1fr));
      gap:12px;
    }

    .card{
      position:relative;
      overflow:hidden;
      height:146px;
      background:rgba(255,255,255,0.08);
      border:1px solid rgba(0,0,0,0.12);
      border-radius:14px;
    }

    .card::before{
      content:"";
      position:absolute;
      left:12px;
      right:12px;
      top:12px;
      height:72px;
      border-radius:10px;
      background:rgba(255,255,255,0.12);
      border:1px solid rgba(0,0,0,0.08);
    }

    .card::after{
      content:"";
      position:absolute;
      left:12px;
      right:28px;
      bottom:14px;
      height:12px;
      border-radius:8px;
      background:rgba(255,255,255,0.12);
    }

    .mini-dot{
      position:absolute;
      right:12px;
      top:12px;
      width:12px;
      height:12px;
      border-radius:50%;
      background:rgba(255,255,255,0.18);
      border:1px solid rgba(0,0,0,0.12);
    }

    .bottom-grid{
      display:grid;
      grid-template-columns:1.6fr 1fr;
      gap:14px;
      flex:1;
      min-height:0;
    }

    .panel{
      background:rgba(255,255,255,0.06);
      border:1px solid rgba(0,0,0,0.12);
      border-radius:14px;
      padding:12px;
    }

    .chat-list{
      display:grid;
      gap:8px;
      margin-top:10px;
    }

    .chat-line{
      height:28px;
      border-radius:8px;
      background:rgba(255,255,255,0.08);
      border:1px solid rgba(0,0,0,0.08);
      position:relative;
      overflow:hidden;
    }

    .chat-line::before{
      content:"";
      position:absolute;
      left:10px;
      top:9px;
      width:52%;
      height:9px;
      border-radius:6px;
      background:rgba(255,255,255,0.12);
    }

    .voice-grid{
      display:grid;
      grid-template-columns:repeat(2, minmax(0, 1fr));
      gap:8px;
      margin-top:10px;
    }

    .voice-pill{
      position:relative;
      height:42px;
      border-radius:10px;
      background:rgba(255,255,255,0.08);
      border:1px solid rgba(0,0,0,0.08);
      overflow:hidden;
    }

    .voice-pill::before{
      content:"";
      position:absolute;
      left:10px;
      top:11px;
      width:18px;
      height:18px;
      border-radius:50%;
      background:rgba(255,255,255,0.12);
    }

    .voice-pill::after{
      content:"";
      position:absolute;
      left:38px;
      top:15px;
      width:46%;
      height:10px;
      border-radius:6px;
      background:rgba(255,255,255,0.12);
    }

    @media (max-width: 860px){
      .sidebar{ display:none; }
      .cards{ grid-template-columns:repeat(2, minmax(0,1fr)); }
      .bottom-grid{ grid-template-columns:1fr; }
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
      <div class="tab-title">Achroma</div>
    </div>

    <div class="toolbar">
      <div class="nav-btn"></div>
      <div class="nav-btn forward"></div>
      <div class="address">
        <span class="lock"></span>
        achroma.example
      </div>
    </div>

    <div class="app">
      <aside class="sidebar">
        <div class="brand">Portal</div>
        <div class="nav-list">
          <div class="nav-item active">Home</div>
          <div class="nav-item">Games</div>
          <div class="nav-item">Movies</div>
          <div class="nav-item">Chat</div>
          <div class="nav-item">Voice</div>
          <div class="nav-item">Friends</div>
        </div>
      </aside>

      <main class="main">
        <div class="hero">
          <div class="hero-content">
            <div class="hero-line"></div>
            <div class="hero-line"></div>
            <div class="hero-line"></div>
          </div>
        </div>

        <div class="section">
          <div class="section-head">
            <span>Featured Games</span>
            <span>More</span>
          </div>

          <div class="cards">
            <div class="card"><div class="mini-dot"></div></div>
            <div class="card"><div class="mini-dot"></div></div>
            <div class="card"><div class="mini-dot"></div></div>
            <div class="card"><div class="mini-dot"></div></div>
          </div>
        </div>

        <div class="section">
          <div class="section-head">
            <span>Trending Movies</span>
            <span>More</span>
          </div>

          <div class="cards">
            <div class="card"><div class="mini-dot"></div></div>
            <div class="card"><div class="mini-dot"></div></div>
            <div class="card"><div class="mini-dot"></div></div>
            <div class="card"><div class="mini-dot"></div></div>
          </div>
        </div>

        <div class="bottom-grid">
          <div class="panel">
            <div class="section-head">
              <span>Live Chat</span>
              <span>Open</span>
            </div>

            <div class="chat-list">
              <div class="chat-line"></div>
              <div class="chat-line"></div>
              <div class="chat-line"></div>
              <div class="chat-line"></div>
            </div>
          </div>

          <div class="panel">
            <div class="section-head">
              <span>Voice Chat</span>
              <span>Live</span>
            </div>

            <div class="voice-grid">
              <div class="voice-pill"></div>
              <div class="voice-pill"></div>
              <div class="voice-pill"></div>
              <div class="voice-pill"></div>
            </div>
          </div>
        </div>
      </main>
    </div>
  </div>
</body>
</html>
