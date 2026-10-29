<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>NovaSphere</title>
    <style>
      :root {
        --bg: #050b14;
        --bg-2: #0d1726;
        --panel: #101b2d;
        --panel-2: #16263d;
        --panel-3: #1d324c;
        --panel-4: #0f1726;
        --soft: #edf3ff;
        --muted: #aabbd7;
        --text: #f5f9ff;
        --gold: #f7ca6a;
        --gold-2: #eb8a3a;
        --blue: #60a5fa;
        --purple: #8b5cf6;
        --pink: #f472b6;
        --green: #3ad49d;
        --red: #fb7185;
        --shadow: rgba(0, 0, 0, 0.45);
      }

      * { box-sizing: border-box; }

      html, body {
        margin: 0;
        min-height: 100vh;
        font-family: Arial, Helvetica, sans-serif;
        background:
          radial-gradient(circle at top left, rgba(96,165,250,0.16), transparent 22%),
          radial-gradient(circle at top right, rgba(139,92,246,0.12), transparent 24%),
          linear-gradient(180deg, var(--bg), var(--bg-2));
        color: var(--text);
      }

      body {
        display: grid;
        place-items: center;
      }

      button, input {
        font: inherit;
      }

      .app {
        width: min(1500px, 96vw);
        min-height: 92vh;
        display: grid;
        grid-template-rows: auto 1fr;
        background: rgba(7, 11, 20, 0.96);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 26px;
        overflow: hidden;
        box-shadow: 0 32px 90px rgba(0,0,0,0.52);
      }

      .topbar {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 18px;
        padding: 18px 22px;
        background: rgba(15, 21, 31, 0.96);
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
        border-radius: 12px;
        background: linear-gradient(135deg, var(--gold), var(--gold-2));
        color: #101827;
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
        flex-wrap: wrap;
        gap: 10px;
      }

      .tab {
        background: rgba(255,255,255,0.04);
        border: 1px solid rgba(255,255,255,0.08);
        color: var(--muted);
        padding: 8px 15px;
        border-radius: 999px;
        cursor: pointer;
        transition: all 0.14s ease;
      }

      .tab:hover {
        border-color: rgba(255,255,255,0.14);
      }

      .tab.active {
        background: linear-gradient(135deg, rgba(96,165,250,0.2), rgba(139,92,246,0.16));
        border-color: rgba(96,165,250,0.45);
        color: var(--text);
      }

      .user-pill {
        background: rgba(255,255,255,0.04);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 999px;
        padding: 9px 13px;
        color: var(--soft);
      }

      .main {
        display: grid;
        grid-template-columns: minmax(0, 1.7fr) minmax(320px, 0.88fr);
        min-height: 0;
      }

      .content {
        padding: 22px;
        background: linear-gradient(180deg, rgba(15,23,36,0.9), rgba(7,11,18,0.96));
      }

      .section {
        display: none;
        min-height: 760px;
      }

      .section.active {
        display: block;
      }

      .browser-panel {
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 24px;
        overflow: hidden;
      }

      .browser-top {
        display: flex;
        align-items: center;
        gap: 12px;
        padding: 12px 14px;
        background: rgba(255,255,255,0.03);
        border-bottom: 1px solid rgba(255,255,255,0.06);
      }

      .traffic {
        display: flex;
        gap: 9px;
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
        border-radius: 999px;
        border: 1px solid rgba(255,255,255,0.08);
        background: rgba(0,0,0,0.16);
        color: var(--muted);
        padding: 9px 14px;
      }

      .browser-body {
        display: grid;
        grid-template-columns: 180px minmax(0,1fr);
        min-height: 760px;
      }

      .side-nav {
        background: rgba(255,255,255,0.015);
        border-right: 1px solid rgba(255,255,255,0.06);
        padding: 18px 12px;
      }

      .side-nav-item {
        display: block;
        text-decoration: none;
        padding: 10px 12px;
        border-radius: 12px;
        margin-bottom: 10px;
        color: var(--muted);
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.04);
      }

      .side-nav-item.active {
        background: rgba(96,165,250,0.12);
        border-color: rgba(96,165,250,0.35);
        color: var(--text);
      }

      .browser-page {
        padding: 18px;
      }

      .page-hero {
        min-height: 220px;
        border-radius: 18px;
        padding: 22px;
        display: flex;
        align-items: flex-end;
        border: 1px solid rgba(255,255,255,0.08);
        background:
          linear-gradient(135deg, rgba(17,24,39,0.78), rgba(15,23,42,0.72)),
          url("https://images.unsplash.com/photo-1524985069026-dd778a71c7b4?auto=format&fit=crop&w=1400&q=80") center/cover no-repeat;
      }

      .page-hero h2 {
        margin: 0;
        font-size: clamp(2rem, 3vw, 3.5rem);
        letter-spacing: -0.05em;
      }

      .site-grid {
        margin-top: 18px;
        display: grid;
        grid-template-columns: repeat(3, minmax(0, 1fr));
        gap: 16px;
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
        gap: 18px;
      }

      .featured-banner {
        position: relative;
        height: 335px;
        border-radius: 22px;
        overflow: hidden;
        border: 1px solid rgba(255,255,255,0.08);
        background:
          linear-gradient(90deg, rgba(0,0,0,0.72), rgba(0,0,0,0.2)),
          url("https://images.unsplash.com/photo-1536440136628-849c177e76a1?auto=format&fit=crop&w=1600&q=80") center/cover no-repeat;
      }

      .featured-content {
        position: absolute;
        left: 28px;
        right: 28px;
        bottom: 24px;
      }

      .eyebrow {
        display: inline-block;
        padding: 7px 12px;
        border-radius: 999px;
        background: rgba(255,255,255,0.08);
        border: 1px solid rgba(255,255,255,0.12);
        font-size: 0.72rem;
        text-transform: uppercase;
        letter-spacing: 0.08em;
      }

      .featured-content h2 {
        margin: 16px 0 10px;
        font-size: clamp(2.3rem, 4vw, 4.3rem);
        line-height: 0.96;
        letter-spacing: -0.04em;
      }

      .meta-row {
        display: flex;
        gap: 14px;
        flex-wrap: wrap;
        color: var(--soft);
        font-size: 0.9rem;
      }

      .action-row {
        display: flex;
        flex-wrap: wrap;
        gap: 12px;
        margin-top: 18px;
      }

      .primary-btn, .secondary-btn, .tiny-btn {
        border: none;
        border-radius: 999px;
        cursor: pointer;
        font-weight: 800;
      }

      .primary-btn {
        padding: 12px 18px;
        background: linear-gradient(135deg, var(--gold), var(--gold-2));
        color: #111827;
      }

      .secondary-btn {
        padding: 11px 17px;
        background: rgba(255,255,255,0.08);
        border: 1px solid rgba(255,255,255,0.12);
        color: var(--text);
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
        border-color: rgba(96,165,250,0.4);
      }

      .movie-poster {
        position: relative;
        aspect-ratio: 4 / 5.2;
        background-size: cover;
        background-position: center;
      }

      .movie-badge {
        position: absolute;
        left: 10px;
        top: 10px;
        padding: 6px 8px;
        border-radius: 999px;
        font-size: 0.7rem;
        font-weight: 700;
        border: 1px solid rgba(255,255,255,0.12);
        background: rgba(12,18,29,0.7);
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
        background: rgba(0,0,0,0.22);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 20px;
        overflow: hidden;
      }

      .player-card video {
        display: block;
        width: 100%;
        height: 260px;
        object-fit: cover;
        background: #000;
      }

      .game-card {
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 20px;
        padding: 16px;
      }

      .game-top {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 12px;
        margin-bottom: 12px;
      }

      .game-top h3 {
        margin: 0;
        font-size: 0.95rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        color: var(--soft);
      }

      .score-badge {
        padding: 6px 10px;
        border-radius: 999px;
        background: rgba(247, 201, 106, 0.12);
        border: 1px solid rgba(247, 201, 106, 0.35);
        color: var(--gold);
        font-size: 0.75rem;
        font-weight: 700;
      }

      .mini-scene {
        position: relative;
        width: 100%;
        height: 320px;
        background:
          linear-gradient(180deg, rgba(96,165,250,0.12), rgba(0,0,0,0.2)),
          linear-gradient(180deg, #14263f 0%, #0f1725 36%, #111827 100%);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 18px;
        overflow: hidden;
      }

      .mini-scene::before {
        content: "";
        position: absolute;
        inset: 0;
        background:
          linear-gradient(transparent 0 76%, rgba(7,11,20,0.88) 76% 100%),
          linear-gradient(90deg, rgba(255,255,255,0.02) 0 5%, transparent 5% 100%);
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
        transition: transform 0.12s ease;
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
        box-shadow: 0 8px 16px rgba(0,0,0,0.25);
        font-size: 1.6rem;
      }

      .findable.found .sprite {
        background: rgba(58,212,157,0.18);
        border-color: rgba(58,212,157,0.9);
        box-shadow: 0 0 18px rgba(58,212,157,0.3);
      }

      .game-footer {
        margin-top: 12px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 12px;
      }

      .game-hint {
        color: var(--muted);
        font-size: 0.85rem;
      }

      .tiny-btn {
        padding: 9px 12px;
        background: rgba(255,255,255,0.06);
        border: 1px solid rgba(255,255,255,0.08);
        color: var(--text);
      }

      .tiny-btn.primary {
        background: linear-gradient(135deg, var(--gold), var(--gold-2));
        color: #111827;
        border: none;
      }

      .chat-panel {
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 20px;
        overflow: hidden;
      }

      .chat-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 14px 16px;
        border-bottom: 1px solid rgba(255,255,255,0.08);
      }

      .chat-header h3 {
        margin: 0;
        font-size: 0.9rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        color: var(--soft);
      }

      .online-pill {
        padding: 6px 10px;
        border-radius: 999px;
        background: rgba(58,212,157,0.12);
        border: 1px solid rgba(58,212,157,0.38);
        color: var(--green);
        font-size: 0.75rem;
        font-weight: 700;
      }

      .chat-box {
        min-height: 360px;
        display: flex;
        flex*

