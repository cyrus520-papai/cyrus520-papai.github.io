<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>PlayBox</title>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap"
      rel="stylesheet"
    />
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <div class="page-shell">
      <header class="topbar">
        <div class="brand">
          <div class="brand-mark">P</div>
          <span>PlayBox</span>
        </div>

        <nav class="nav">
          <a href="#games">Games</a>
          <a href="#movies">Movies</a>
          <a href="#chat">Chat</a>
        </nav>

        <button class="ghost-btn">Sign in</button>
      </header>

      <main>
        <section class="hero">
          <div class="hero-copy">
            <p class="eyebrow">Entertainment hub</p>
            <h1>Play games. Watch movies. Talk with your crew.</h1>
            <p class="subtitle">
              Discover trending games, browse new movie picks, and chat with friends in one
              unified experience.
            </p>

            <div class="hero-actions">
              <button class="primary-btn<true>">Start exploring</button>
              <button class="secondary-btn">Join community</button>
            </div>

            <div class="stats">
              <div>
                <strong>120K+</strong>
                <span>players online</span>
              </div>
              <div>
                <strong>4.9/5</strong>
                <span>community rating</span>
              </div>
              <div>
                <strong>800+</strong>
                <span>movie picks</span>
              </div>
            </div>
          </div>

          <div class="hero-panel">
            <div class="showcase-card large">
              <div class="card-badge">Trending now</div>
              <h3>Cyber Drift</h3>
              <p>Race through futuristic cities in a pulse-pounding arcade challenge.</p>
              <div class="meta">
                <span>Action</span>
                <span>4.8 ★</span>
              </div>
            </div>

            <div class="mini-grid">
              <div class="showcase-card small">
                <div class="card-badge purple">Movie</div>
                <h4>Neon Nights</h4>
                <p>3D thriller</p>
              </div>

              <div class="showcase-card small">
                <div class="card-badge green">Chat</div>
                <h4>Squad Room</h4>
                <p>8 online</p>
              </div>
            </div>
          </div>
        </section>

        <section id="games" class="content-section">
          <div class="section-header">
            <div>
              <p class="eyebrow">Featured games</p>
              <h2>Top picks for today</h2>
            </div>
            <div class="filters">
              <button class="chip active" data-filter="all">All</button>
              <button class="chip" data-filter="action">Action</button>
              <button class="chip" data-filter="racing">Racing</button>
              <button class="chip" data-filter="puzzle">Puzzle</button>
            </div>
          </div>

          <div id="gamesGrid" class="card-grid"></div>
        </section>

        <section id="movies" class="content-section">
          <div class="section-header">
            <div>
              <p class="eyebrow">Trending movies</p>
              <h2>What everyone’s watching</h2>
            </div>
          </div>

          <div id="moviesGrid" class="card-grid"></div>
        </section>

        <section id="chat" class="chat-section">
          <div class="section-header">
            <div>
              <p class="eyebrow">Community</p>
              <h2>Chat with friends</h2>
            </div>
          </div>

          <div class="chat-layout">
            <aside class="friends-list">
              <h3>Online now</h3>
              <div class="friend">
                <div class="avatar avatar-pink">A</div>
                <div>
                  <strong>Ariana</strong>
                  <small>Playing Drift City</small>
                </div>
              </div>
              <div class="friend">
                <div class="avatar avatar-blue">J</div>
                <div>
                  <strong>Jules</strong>
                  <small>Watching Sci-Fi Night</small>
                </div>
              </div>
              <div class="friend">
                <div class="avatar avatar-green">M</div>
                <div>
                  <strong>Marco</strong>
                  <small>Ready for a co-op match</small>
                </div>
              </div>
            </aside>

            <div class="chat-panel">
              <div id="chatMessages" class="chat-messages" aria-live="polite"></div>

              <div class="quick-replies">
                <button>What’s trending?</button>
                <button>Movie rec
