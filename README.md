<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>SocialStream Hub</title>
    <style>
      :root {
        --bg: #070b13;
        --bg-2: #111827;
        --panel: #111827;
        --panel-2: #172235;
        --panel-3: #1d2b3d;
        --soft: #edf3ff;
        --muted: #a8b7d3;
        --text: #f7f9ff;
        --gold: #f7c96a;
        --gold-2: #ef8d3d;
        --blue: #60a5fa;
        --purple: #8b5cf6;
        --green: #3ad49d;
        --red: #f87171;
        --shadow: rgba(0, 0, 0, 0.38);
      }

      * {
        box-sizing: border-box;
      }

      html, body {
        margin: 0;
        min-height: 100vh;
        background:
          radial-gradient(circle at top, rgba(96,165,250,0.15), transparent 25%),
          linear-gradient(180deg, var(--bg), var(--bg-2));
        color: var(--text);
        font-family: Arial, Helvetica, sans-serif;
      }

      body {
        display: grid;
        place-items: center;
      }

      button, input {
        font: inherit;
      }

      .app {
        width: min(1460px, 96vw);
        min-height: 92vh;
        display: grid;
        grid-template-rows: auto 1fr;
        background: rgba(8, 12, 20, 0.9);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 26px;
        box-shadow: 0 30px 70px var(--shadow);
        overflow: hidden;
      }

      .topbar {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 16px;
        padding: 18px 24px;
        background: rgba(18, 24, 35, 0.9);
        border-bottom: 1px solid rgba(255,255,255,0.08);
      }

      .brand-wrap {
        display: flex;
        align-items: center;
        gap: 12px;
      }

      .brand-mark {
        width: 38px;
        height: 38px;
        display: grid;
        place-items: center;
        background: linear-gradient(135deg, var(--gold), var(--gold-2));
        color: #111827;
        border-radius: 12px;
        font-weight: 900;
      }

      .brand-name {
        font-size: 1.18rem;
        font-weight: 800;
        letter-spacing: 0.08em;
        text-transform: uppercase;
      }

      .nav {
        display: flex;
        align-items: center;
        gap: 10px;
        flex-wrap: wrap;
      }

      .tab {
        border: 1px solid rgba(255,255,255,0.08);
        background: rgba(255,255,255,0.04);
        color: var(--muted);
        padding: 8px 14px;
        border-radius: 999px;
        cursor: pointer;
        transition: all 0.12s ease;
      }

      .tab.active {
        color: var(--text);
        background: linear-gradient(135deg, rgba(96,165,250,0.25), rgba(139,92,246,0.18));
        border-color: rgba(96,165,250,0.45);
      }

      .user-pill {
        background: rgba(255,255,255,0.03);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 999px;
        padding: 9px 14px;
        color: var(--soft);
      }

      .main {
        display: grid;
        grid-template-columns: minmax(0, 1.8fr) minmax(300px, 0.9fr);
        min-height: 0;
      }

      .content {
        padding: 20px;
        background: linear-gradient(180deg, rgba(17,24,39,0.9), rgba(8,12,17,0.95));
        min-height: 0;
      }

      .section {
        display: none;
        min-height: 700px;
      }

      .section.active {
        display: block;
      }

      .browser-panel {
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 20px;
        overflow: hidden;
      }

      .browser-top {
        display: flex;
        align-items: center;
        gap: 10px;
        padding: 12px 14px;
        background: rgba(255,255,255,0.04);
        border-bottom: 1px solid rgba(255,255,255,0.06);
      }

      .traffic {
        display: flex;
        gap: 8px;
      }

      .dot {
        width: 12px;
        height: 12px;
        border-radius: 50%;
      }

      .dot.red { background: #ef4444; }
      .dot.yellow { background: #fbbf24; }
      .dot.green { background: #34d399; }

      .address-bar {
        flex: 1;
        background: rgba(0,0,0,0.16);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 999px;
        padding: 9px 14px;
        color: var(--muted);
        overflow: auto;
      }

      .browser-body {
        display: grid;
        grid-template-columns: 180px 1fr;
        min-height: 740px;
      }

      .sidebar-links {
        background: rgba(255,255,255,0.02);
        border-right: 1px solid rgba(255,255,255,0.06);
        padding: 16px 12px;
      }

      .sidebar-links .link {
        display: block;
        text-decoration: none;
        color: var(--muted);
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.04);
        border-radius: 12px;
        padding: 10px 12px;
        margin-bottom: 10px;
      }

      .sidebar-links .link.active {
        color: var(--text);
        background: rgba(96,165,250,0.12);
        border-color: rgba(96,165,250,0.3);
      }

      .browser-page {
        padding: 18px;
      }

      .page-hero {
        background:
          linear-gradient(135deg, rgba(31,41,55,0.8), rgba(15,23,42,0.72)),
          url("https://images.unsplash.com/photo-1524985069026-dd778a71c7b4?auto=format&fit=crop&w=1200&q=80") center/cover no-repeat;
        border-radius: 18px;
        padding: 24px;
        min-height: 220px;
        display: flex;
        align-items: end;
      }

      .page-hero h2 {
        margin: 0;
        font-size: clamp(2rem, 3vw, 3.2rem);
        letter-spacing: -0.04em;
      }

      .site-grid {
        display: grid;
        grid-template-columns: repeat(3, minmax(0, 1fr));
        gap: 16px;
        margin-top: 18px;
      }

      .site-card {
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 16px;
        overflow: hidden;
      }

      .site-card .image {
        aspect-ratio: 16 / 9;
        background-size: cover;
        background-position: center;
      }

      .site-card .body {
        padding: 12px 12px 14px;
      }

      .site-card h4 {
        margin: 0 0 6px;
        font-size: 1rem;
      }

      .site-card p {
        margin: 0;
        color: var(--muted);
        font-size: 0.86rem;
      }

      .movie-layout {
        display: grid;
        gap: 20px;
      }

      .featured-banner {
        height: 300px;
        border-radius: 22px;
        background:
          linear-gradient(90deg, rgba(0,0,0,0.68), rgba(0,0,0,0.22)),
          url("https://images.unsplash.com/photo-1536440136628-849c177e76a1?auto=format&fit=crop&w=1400&q=80") center/cover no-repeat;
        border: 1px solid rgba(255,255,255,0.08);
        position: relative;
        overflow: hidden;
      }

      .featured-content {
        position: absolute;
        left: 28px;
        right: 28px;
        bottom: 24px;
      }

      .eyebrow {
        display: inline-block;
        padding: 7px 11px;
        border-radius: 999px;
        border: 1px solid rgba(255,255,255,0.12);
        background: rgba(255,255,255,0.08);
        font-size: 0.72rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        color: var(--soft);
      }

      .featured-content h2 {
        margin: 14px 0 10px;
        font-size: clamp(2rem, 4vw, 4rem);
        line-height: 0.96;
        letter-spacing: -0.04em;
      }

      .meta-row {
        display: flex;
        gap: 14px;
        flex-wrap: wrap;
        color: var(--muted);
        font-size: 0.88rem;
      }

      .action-row {
        margin-top: 18px;
        display: flex;
        gap: 12px;
        flex-wrap: wrap;
      }

      .primary-btn, .secondary-btn, .tiny-btn {
        border: none;
        border-radius: 999px;
        padding: 11px 17px;
        font-weight: 800;
        cursor: pointer;
      }

      .primary-btn {
        background: linear-gradient(135deg, var(--gold), var(--gold-2));
        color: #111827;
      }

      .secondary-btn {
        background: rgba(255,255,255,0.08);
        border: 1px solid rgba(255,255,255,0.12);
        color: var(--text);
      }

      .rows {
        display: grid;
        gap: 16px;
      }

      .row-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
      }

      .row-header h3 {
        margin: 0;
        font-size: 0.95rem;
        text-transform: uppercase;
        letter-spacing: 0.08em;
        color: var(--soft);
      }

      .more {
        color: var(--gold);
        font-weight: 700;
      }

      .movie-cards {
        display: grid;
        grid-template-columns: repeat(4, minmax(0, 1fr));
        gap: 18px;
      }

      .movie-card {
        background: linear-gradient(180deg, rgba(22,33,50,0.9), rgba(10,15,25,0.95));
        border: 1px solid rgba(255,255,255,0.06);
        border-radius: 18px;
        overflow: hidden;
        cursor: pointer;
        transition: transform 0.15s ease, border-color 0.15s ease;
      }

      .movie-card:hover {
        transform: translateY(-2px);
        border-color: rgba(96,165,250,0.35);
      }

      .movie-poster {
        aspect-ratio: 4 / 5.2;
        background-size: cover;
        background-position: center;
        position: relative;
      }

      .movie-badge {
        position: absolute;
        left: 10px;
        top: 10px;
        padding: 6px 9px;
        border-radius: 999px;
        font-size: 0.7rem;
        background: rgba(12,18,29,0.78);
        color: var(--soft);
        border: 1px solid rgba(255,255,255,0.12);
        font-weight: 700;
      }

      .movie-info {
        padding: 12px 12px 14px;
      }

      .movie-info h4 {
        margin: 0 0 6px;
        font-size: 1rem;
      }

      .movie-info p {
        margin: 0;
        color: var(--muted);
        font-size: 0.82rem;
      }

      .player-card {
        background: rgba(0,0,0,0.24);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 20px;
        overflow: hidden;
      }

      video {
        width: 100%;
        height: 260px;
        display: block;
        background: #000;
        object-fit: cover;
      }

      .game-card {
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 20px;
        padding: 16px;
      }

      .mini-wrapper {
        display: grid;
        gap: 12px;
      }

      .mini-scene {
        position: relative;
        width: 100%;
        height: 290px;
        background:
          linear-gradient(180deg, rgba(96,165,250,0.12), rgba(0,0,0,0.22)),
          linear-gradient(180deg, #11213d, #0d1523 35%, #0e1626 100%);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 18px;
        overflow: hidden;
      }

      .mini-scene::before {
        content: "";
        position: absolute;
        inset: 0;
        background:
          linear-gradient(transparent 0 76%, rgba(7,11,20,0.9) 76% 100%),
          linear-gradient(90deg, rgba(255,255,255,0.02) 0 4%, transparent 4% 100%);
        pointer-events: none;
      }

      .findable {
        position: absolute;
        width: 42px;
        height: 42px;
        transform: translate(-50%, -50%);
        border: none;
        background: transparent;
        padding: 0;
        cursor: pointer;
        user-select: none;
        transition: transform 0.12s ease, filter 0.12s ease;
      }

      .findable:hover {
        transform: translate(-50%, -50%) scale(1.08);
      }

      .findable.hidden {
        opacity: 0;
        pointer-events: none;
      }

      .findable .sprite {
        width: 100%;
        height: 100%;
        display: grid;
        place-items: center;
        border-radius: 12px;
        background: rgba(255,255,255,0.08);
        border: 2px solid rgba(255,255,255,0.18);
        box-shadow: 0 8px 18px rgba(0,0,0,0.25);
        font-size: 1.6rem;
      }

      .findable.found .sprite {
        background: rgba(58,212,157,0.18);
        border-color: rgba(58,212,157,0.9);
        box-shadow: 0 0 18px rgba(58,212,157,0.33);
      }

      .game-row {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 12px;
      }

      .score-badge {
        padding: 6px 10px;
        border-radius: 999px;
        background: rgba(247, 201,*

