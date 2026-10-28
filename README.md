<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Achroma Portal</title>
  <style>
    :root{
      --bg:#000000;
      --achroma:#808080;
      --achroma-1:#6f6f6f;
      --achroma-2:#7a7a7a;
      --achroma-3:#8a8a8a;
      --achroma-4:#9b9b9b;
      --achroma-5:#b2b2b2;
      --surface:#878787;
      --surface-2:#939393;
      --surface-3:#a7a7a7;
      --chrome:#7f7f7f;
      --chrome-2:#8d8d8d;
      --chrome-3:#9c9c9c;
      --panel:rgba(255,255,255,0.07);
      --panel-strong:rgba(255,255,255,0.12);
      --line:rgba(0,0,0,0.18);
      --text:rgba(255,255,255,0.96);
      --muted:rgba(255,255,255,0.8);
      --shadow:rgba(0,0,0,0.30);
    }

    * { box-sizing: border-box; }

    html, body{
      margin:0;
      width:100%;
      height:100%;
      background:#000;
      color:var(--text);
      font-family: Arial, Helvetica, sans-serif;
      overflow:hidden;
    }

    body{
      display:grid;
      place-items:center;
    }

    .window{
      width:min(1000px, 92vw);
      height:min(620px, 82vh);
      background:var(--chrome);
      border:1px solid rgba(0,0,0,0.24);
      box-shadow:
        0 24px 54px var(--shadow),
        inset 0 1px 0 rgba(255,255,255,0.12);
      position:relative;
      overflow:hidden;
      border-radius:4px;
    }

    .window::before{
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
      align-items:center;
      gap:10px;
      width:110px;
      z-index:2;
    }

    .dot{
      width:12px;
      height:12px;
      border-radius:50%;
      border:1px solid rgba(0,0,0,0.15);
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.2);
    }

    .dot:nth-child(1){ background:#d9d9d9; }
    .dot:nth-child(2){ background:#d0d0d0; }
    .dot:nth-child(3){ background:#c7c7c7; }

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
      background:var(--chrome-2);
      border-bottom:1px solid var(--line);
      display:flex;
      align-items:center;
      gap:12px;
      padding:0 16px;
    }

    .nav-btn{
      width:28px;
      height:28px;
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
      left:10px;
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
      background:rgba(255,255,255,0.12);
      border:1px solid rgba(0,0,0,0.15);
      display:flex;
      align-items:center;
      padding:0 16px;
      color:var(--text);
      font-size:13px;
      letter-spacing:0.04em;
      user-select:none;
    }

    .lock{
      width:10px;
      height:10px;
      border:2px solid rgba(255,255,255,0.8);
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
      border:2px solid rgba(255,255,255,0.8);
      border-bottom:0;
      border-radius:9px 9px 0 0;
      left:-2px;
      top:-9px;
    }

    .app-shell{
      position:relative;
      z-index:1;
      height:calc(100% - 118px);
      background:linear-gradient(180deg, #878787 0%, #7b7b7b 100%);
      display:flex;
    }

    .sidebar{
      width:220px;
      background:rgba(255,255,255,0.04);
      border-right:1px solid var(--line);
      padding:18px 12px 12px;
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
      color:rgba(255,255,255,0.94);
    }

    .side-nav{
      display:grid;
      gap:8px;
      margin-top:14px;
    }

    .side-item{
      height:34px;
      border-radius:10px;
      background:rgba(255,255,255,0.06);
      border:1px solid rgba(0,0,0,0.08);
      display:flex;
      align-items:center;
      padding:0 12px;
      text-transform:uppercase;
      letter-spacing:0.09em;
      font-size:10px;
      color:rgba(255,255,255,0.8);
    }

    .side-item.active{
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
        linear-gradient(120deg, rgba(255,255,255,0.08), transparent 45%);
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

    .hero-inner{
      position:absolute;
      left:18px;
      right:18px;
      bottom:16px;
      display:flex;
      align-items:end;
      gap:12px;
    }

    .hero-bar{
      height:14px;
      border-radius:8px;
      background:rgba(255,255,255,0.14);
    }

    .hero-bar:nth-child(1){ width:42%; height:18px; }
    .hero-bar:nth-child(2){ width:26%; }
    .hero-bar:nth-child(3){ width:16%; }

    .section{
      display:grid;
      gap:10px;
    }

    .section-head{
      display:flex;
      align-items:center;
      justify-content:space-between;
      font-size:10px;
      letter-spacing:0.12em;
      text-transform:uppercase;
      color:rgba(255,255,255,0.92);
      padding:0 2px;
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
      border-radius:14px;
      background:rgba(255,255,255,0.08);
      border:1px solid rgba(0,0,0,0.13);
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
      right:26px;
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
      .cards{ grid-template-columns: repeat(2, minmax(0,1fr)); }
      .bottom-grid{ grid-template-columns: 1fr; }
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
      <div class="nav-btn"></div>
      <div class="nav-btn forward"></div>

      <div class="address">
        <span class="lock"></span>
        achroma.example
      </div>
    </div>

    <div class="app-shell">
      <aside class="sidebar">
        <div class="brand">Portal</div>

        <div class="side-nav">
          <div class="side-item active">Home</div>
          <div class="side-item">Games</div>
          <div class="side-item">Movies</div>
          <div class="side-item">Chat</div>
          <div class="side-item">Voice</div>
          <div class="side-item">Friends</div>
        </div>
      </aside>

      <main class="main">
        <div class="hero">
          <div class="hero-inner">
            <div class="hero-bar"></div>
            <div class="hero-bar"></div>
            <div class="hero-bar"></div>
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
