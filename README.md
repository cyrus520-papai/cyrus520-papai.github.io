<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>NovaSphere Social</title>
    <style>
      :root {
        --bg: #070d18;
        --bg-2: #0d1726;
        --panel: #101b2d;
        --panel-2: #17263d;
        --panel-3: #1d324c;
        --soft: #edf5ff;
        --muted: #a9bbd4;
        --text: #f6faff;
        --gold: #f7ca6e;
        --gold-2: #eb8e3d;
        --blue: #5ea3ff;
        --purple: #8b5cf6;
        --green: #3ad49d;
        --red: #f87171;
        --shadow: rgba(0,0,0,0.46);
      }

      * { box-sizing: border-box; }

      html, body {
        margin: 0;
        min-height: 100vh;
        font-family: Arial, Helvetica, sans-serif;
        background:
          radial-gradient(circle at top left, rgba(94,163,255,0.12), transparent 25%),
          radial-gradient(circle at top right, rgba(139,92,246,0.12), transparent 22%),
          linear-gradient(180deg, var(--bg), var(--bg-2));
        color: var(--text);
      }

      body {
        display: grid;
        place-items: center;
      }

      a {
        text-decoration: none;
        color: inherit;
      }

      button, input {
        font: inherit;
      }

      .app {
        width: min(1540px, 97vw);
        min-height: 92vh;
        display: grid;
        grid-template-columns: 230px minmax(0, 1fr) 340px;
        background: rgba(7, 11, 20, 0.96);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 28px;
        overflow: hidden;
        box-shadow: 0 30px 90px rgba(0,0,0,0.5);
      }

      .sidebar {
        background: linear-gradient(180deg, rgba(16,27,44,0.96), rgba(8,12,20,0.98));
        border-right: 1px solid rgba(255,255,255,0.08);
        padding: 18px 14px;
      }

      .brand {
        display: flex;
        align-items: center;
        gap: 12px;
        padding: 8px 8px 18px;
      }

      .brand-mark {
        width: 38px;
        height: 38px;
        display: grid;
        place-items: center;
        border-radius: 12px;
        background: linear-gradient(135deg, var(--gold), var(--gold-2));
        color: #111827;
        font-weight: 900;
      }

      .brand-name {
        font-size: 1.08rem;
        font-weight: 800;
        letter-spacing: 0.08em;
        text-transform: uppercase;
      }

      .nav-section {
        margin-top: 20px;
      }

      .nav-title {
        padding: 0 10px 10px;
        color: var(--muted);
        letter-spacing: 0.1em;
        text-transform: uppercase;
        font-size: 0.68rem;
      }

      .nav-item {
        display: flex;
        align-items: center;
        gap: 12px;
        padding: 11px 12px;
        border-radius: 12px;
        background: transparent;
        color: var(--muted);
        border: 1px solid transparent;
        margin-bottom: 6px;
        cursor: pointer;
        transition: all 0.14s ease;
      }

      .nav-item:hover {
        border-color: rgba(255,255,255,0.06);
        color: var(--text);
      }

      .nav-item.active {
        background: linear-gradient(135deg, rgba(94,163,255,0.14), rgba(139,92,246,0.12));
        border-color: rgba(94,163,255,0.32);
        color: var(--text);
      }

      .nav-icon {
        width: 28px;
        height: 28px;
        border-radius: 10px;
        display: grid;
        place-items: center;
        background: rgba(255,255,255,0.05);
        border: 1px solid rgba(255,255,255,0.06);
        font-size: 0.9rem;
      }

      .profile-card {
        margin-top: 18px;
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 18px;
        padding: 14px 12px;
      }

      .profile-row {
        display: flex;
        align-items: center;
        gap: 10px;
      }

      .avatar {
        width: 38px;
        height: 38px;
        border-radius: 50%;
        display: grid;
        place-items: center;
        color: #111827;
        font-weight: 800;
        font-size: 0.78rem;
      }

      .avatar.a1 { background: linear-gradient(135deg, #60a5fa, #93c5fd); }
      .avatar.a2 { background: linear-gradient(135deg, #f9a8d4, #fca5a5); }
      .avatar.a3 { background: linear-gradient(135deg, #fbbf24, #f59e0b); }
      .avatar.a4 { background: linear-gradient(135deg, #4ade80, #34d399); }

      .profile-name {
        font-weight: 700;
      }

      .profile-meta {
        font-size: 0.76rem;
        color: var(--muted);
      }

      .stats {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 8px;
        margin-top: 14px;
      }

      .stat-box {
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.06);
        border-radius: 10px;
        padding: 10px 8px;
        text-align: center;
      }

      .stat-box strong {
        display: block;
        font-size: 1rem;
      }

      .stat-box span {
        display: block;
        color: var(--muted);
        font-size: 0.7rem;
        margin-top: 2px;
      }

      .main-panel {
        background: linear-gradient(180deg, rgba(12,18,29,0.96), rgba(8,12,20,0.98));
        min-width: 0;
      }

      .topbar {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 18px;
        padding: 18px 22px;
        border-bottom: 1px solid rgba(255,255,255,0.08);
        background: rgba(15,22,33,0.92);
      }

      .search-wrap {
        position: relative;
        flex: 1;
        max-width: 680px;
      }

      .search {
        width: 100%;
        padding: 12px 18px 12px 42px;
        border-radius: 999px;
        background: rgba(255,255,255,0.04);
        border: 1px solid rgba(255,255,255,0.08);
        color: var(--text);
        outline: none;
      }

      .search::placeholder {
        color: var(--muted);
      }

      .search-icon {
        position: absolute;
        left: 15px;
        top: 50%;
        transform: translateY(-50%);
        color: var(--muted);
      }

      .top-actions {
        display: flex;
        align-items: center;
        gap: 12px;
      }

      .ghost-btn {
        background: rgba(255,255,255,0.04);
        border: 1px solid rgba(255,255,255,0.08);
        color: var(--text);
        padding: 10px 14px;
        border-radius: 999px;
        cursor: pointer;
      }

      .primary-btn {
        background: linear-gradient(135deg, var(--gold), var(--gold-2));
        border: none;
        color: #111827;
        border-radius: 999px;
        padding: 10px 16px;
        font-weight: 800;
        cursor: pointer;
      }

      .content-wrap {
        padding: 22px;
      }

      .section {
        display: none;
        min-height: 820px;
      }

      .section.active {
        display: block;
      }

      .hero {
        position: relative;
        height: 420px;
        border-radius: 26px;
        overflow: hidden;
        border: 1px solid rgba(255,255,255,0.08);
        background:
          linear-gradient(90deg, rgba(0,0,0,0.72), rgba(0,0,0,0.16)),
          url("https://images.unsplash.com/photo-1536440136628-849c177e76a1?auto=format&fit=crop&w=1600&q=80") center/cover no-repeat;
      }

      .hero-glow {
        position: absolute;
        inset: 0;
        background: linear-gradient(180deg, rgba(0,0,0,0.12), rgba(0,0,0,0.58));
      }

      .hero-content {
        position: absolute;
        left: 28px;
        right: 28px;
        bottom: 24px;
        z-index: 1;
      }

      .eyebrow {
        display: inline-block;
        padding: 7px 12px;
        border-radius: 999px;
        background: rgba(255,255,255,0.08);
        border: 1px solid rgba(255,255,255,0.12);
        font-size: 0.7rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
      }

      .hero h1 {
        margin: 16px 0 10px;
        font-size: clamp(2.3rem, 4.6vw, 4.8rem);
        letter-spacing: -0.05em;
        line-height: 0.96;
      }

      .hero-meta {
        display: flex;
        flex-wrap: wrap;
        gap: 14px;
        color: var(--soft);
        font-size: 0.9rem;
      }

      .hero-actions {
        display: flex;
        flex-wrap: wrap;
        gap: 12px;
        margin-top: 18px;
      }

      .secondary-btn {
        background: rgba(255,255,255,0.08);
        border: 1px solid rgba(255,255,255,0.12);
        color: var(--text);
        border-radius: 999px;
        padding: 11px 16px;
        cursor: pointer;
      }

      .section-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin: 26px 0 14px;
      }

      .section-header h2 {
        margin: 0;
        font-size: 1.06rem;
        text-transform: uppercase;
        letter-spacing: 0.08em;
        color: var(--soft);
      }

      .more {
        color: var(--gold);
        font-weight: 700;
      }

      .card-grid {
        display: grid;
        grid-template-columns: repeat(4, minmax(0, 1fr));
        gap: 16px;
      }

      .media-card {
        background: linear-gradient(180deg, rgba(22,33,50,0.9), rgba(10,15,25,0.95));
        border: 1px solid rgba(255,255,255,0.06);
        border-radius: 18px;
        overflow: hidden;
        cursor: pointer;
        transition: all 0.14s ease;
      }

      .media-card:hover {
        transform: translateY(-2px);
        border-color: rgba(94,163,255,0.4);
        box-shadow: 0 14px 28px rgba(0,0,0,0.18);
      }

      .poster {
        position: relative;
        aspect-ratio: 4 / 5.3;
        background-size: cover;
        background-position: center;
      }

      .poster-badge {
        position: absolute;
        left: 10px;
        top: 10px;
        padding: 6px 8px;
        background: rgba(12,18,29,0.76);
        border: 1px solid rgba(255,255,255,0.12);
        border-radius: 999px;
        color: var(--soft);
        font-size: 0.7rem;
        font-weight: 700;
      }

      .card-body {
        padding: 12px 12px 14px;
      }

      .card-title {
        margin: 0 0 6px;
        font-size: 1rem;
      }

      .card-meta {
        margin: 0;
        color: var(--muted);
        font-size: 0.82rem;
      }

      .browser-panel {
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 22px;
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

      .browser-bar {
        flex: 1;
        border-radius: 999px;
        background: rgba(0,0,0,0.18);
        border: 1px solid rgba(255,255,255,0.08);
        color: var(--muted);
        padding: 9px 14px;
      }

      .browser-body {
        display: grid;
        grid-template-columns: 180px minmax(0,1fr);
        min-height: 760px;
      }

      .browser-sidebar {
        background: rgba(255,255,255,0.015);
        border-right: 1px solid rgba(255,255,255,0.06);
        padding: 16px 12px;
      }

      .browser-link {
        display: block;
        padding: 10px 12px;
        margin-bottom: 10px;
        border-radius: 12px;
        color: var(--muted);
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.05);
      }

      .browser-link.active {
        background: rgba(94,163,255,0.12);
        border-color: rgba(94,163,255,0.32);
        color: var(--text);
      }

      .browser-page {
        padding: 18px;
      }

      .browser-hero {
        min-height: 220px;
        border-radius: 18px;
        padding: 24px;
        display: flex;
        align-items: flex-end;
        border: 1px solid rgba(255,255,255,0.08);
        background:
          linear-gradient(135deg, rgba(17,24,39,0.82), rgba(15,23,42,0.74)),
          url("https://images.unsplash.com/photo-1524985069026-dd778a71c7b4?auto=format&fit=crop&w=1400&q=80") center/cover no-repeat;
      }

      .browser-hero h2 {
        margin: 0;
        font-size: clamp(2rem, 3vw, 3.5rem);
        letter-spacing: -0.05em;
      }

      .browser-grid {
        display: grid;
        grid-template-columns: repeat(3, minmax(0, 1fr));
        gap: 16px;
        margin-top: 18px;
      }

      .browser-card {
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 16px;
        overflow: hidden;
      }

      .browser-card .image {
        aspect-ratio: 16 / 9;
        background-size: cover;
        background-position: center;
      }

      .browser-card .body {
        padding: 12px 12px 14px;
      }

      .browser-card h4 {
        margin: 0 0 6px;
        font-size: 1rem;
      }

      .browser-card p {
        margin: 0;
        color: var(--muted);
        font-size: 0.84rem;
      }

      .game-card {
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 20px;
        padding: 16px;
      }

      .game-head {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 12px;
        margin-bottom: 12px;
      }

      .game-head h3 {
        margin: 0;
        color: var(--soft);
        text-transform: uppercase;
        letter-spacing: 0.08em;
        font-size: 0.95rem;
      }

      .score-badge {
        background: rgba(247, 201, 106, 0.12);
        border: 1px solid rgba(247, 201, 106, 0.35);
        color: var(--gold);
        padding: 6px 10px;
        border-radius: 999px;
        font-size: 0.75rem;
        font-weight: 700;
      }

      .mini-scene {
        position: relative;
        width: 100%;
        height: 330px;
        background:
          linear-gradient(180deg, rgba(96,165,250,0.12), rgba(0,0,0,0.2)),
          linear-gradient(180deg, #14263f, #0f1725 36%, #111827 100%);
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
        border-radius: 999px;
        border: 1px solid rgba(255,255,255,0.08);
        background: rgba(255,255,255,0.04);
        color: var(--text);
        cursor: pointer;
        font-weight: 700;
      }

      .tiny-btn.primary {
        background: linear-gradient(135deg, var(--gold), var(--gold-2));
        color: #111827;
        border: none;
      }

      .player-card {
        background: rgba(0,0,0,0.22);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 20px;
        overflow: hidden;
        margin-top: 18px;
      }

      .player-card video {
        display: block;
        width: 100%;
        height: 260px;
        object-fit: cover;
        background: #000;
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
        text-transform: uppercase;
        letter-spacing: 0.08em;
        font-size: 0.9rem;
        color: var(--soft);
      }

      .online-pill {
        padding: 6px 10px;
        border-radius: 999px;
        background: rgba(58,212,157,0.12);
        border: 1px solid rgba(58,212,157,0.38);
        color: var(--green);
        font-size: 0.74rem;
        font-weight: 700;
      }

      .chat-box {
        display: flex;
        flex-direction: column;
        gap: 12px;
        min-height: 400px;
        padding: 16px;
        background: rgba(0,0,0,0.05);
      }

      .msg {
        max-width: 85%;
        padding: 10px 12px;
        border-radius: 14px;
        line-height: 1.35;
        font-size: 0.9rem;
      }

      .msg.self {
        align-self: flex-end;
        background: linear-gradient(135deg, rgba(94,163,255,0.34), rgba(139,92,246,0.26));
        border: 1px solid rgba(94,163,255,0.35);
      }

      .msg.other {
        align-self: flex-start;
        background: rgba(255,255,255,0.04);
        border: 1px solid rgba(255,255,255,0.06);
        color: var(--soft);
      }

      .composer {
        display: flex;
        gap: 10px;
        padding: 14px 16px 16px;
        border-top: 1px solid rgba(255,255,255,0.08);
        background: rgba(255,255,255,0.02);
      }

      .composer input {
        flex: 1;
        padding: 11px 14px;
        background: rgba(255,255,255,0.04);
        border: 1px solid rgba(255,255,255,0.08);
        color: var(--text);
        border-radius: 999px;
      }

      .voice-panel {
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 20px;
        padding: 18px 16px;
      }

      .voice-head {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 16px;
      }

      .voice-head h3 {
        margin: 0;
        font-size: 0.94rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        color: var(--soft);
      }

      .voice-users {
        display: grid;
        gap: 10px;
      }

      .voice-user {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 12px;
        padding: 10px 12px;
        border-radius: 14px;
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
      }

      .user-name {
        display: flex;
        align-items: center;
        gap: 10px;
      }

      .voice-actions {
        display: flex;
        gap: 8px;
        flex-wrap: wrap;
        margin-top: 16px;
      }

      .status {
        width: 10px;
        height: 10px;
        border-radius: 50%;
        background: var(--green);
        box-shadow: 0 0 10px rgba(58,212,157,0.8);
      }

      .status.idle { background: #fbbf24; }
      .status.muted { background: var(--red); }

      .rightbar {
        background: linear-gradient(180deg, rgba(19,28,41,0.96), rgba(9,14,22,0.96));
        border-left: 1px solid rgba(255,255,255,0.08);
        padding: 18px;
      }

      .right-stack {
        display: grid;
        gap: 18px;
      }

      .feed-card {
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 18px;
        overflow: hidden;
      }

      .feed-head {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 12px;
        padding: 14px 16px;
        border-bottom: 1px solid rgba(255,255,255,0.08);
      }

      .feed-head h3 {
        margin: 0;
        font-size: 0.9rem;
        text-transform: uppercase;
        letter-spacing: 0.08em;
        color: var(--soft);
      }

      .feed-body {
        padding: 14px 16px 16px;
        display: grid;
        gap: 12px;
      }

      .friend-row {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 12px;
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 12px;
        padding: 10px 12px;
      }

      .friend-meta {
        display: flex;
        align-items: center;
        gap: 10px;
      }

      .muted-text {
        color: var(--muted);
        font-size: 0.72rem;
      }

      .modal {
        position: fixed;
        inset: 0;
        display: none;
        place-items: center;
        background: rgba(0,0,0,0.64);
        backdrop-filter: blur(8px);
        z-index: 100;
      }

      .modal.active {
        display: grid;
      }

      .modal-card {
        width: min(820px, 90vw);
        background: linear-gradient(180deg, rgba(19,26,39,0.98), rgba(8,12,19,0.99));
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 24px;
        overflow: hidden;
        box-shadow: 0 30px 90px rgba(0,0,0,0.45);
      }

      .modal-image {
        height: 260px;
        background-size: cover;
        background-position: center;
      }

      .modal-body {
        padding: 20px 22px 24px;
      }

      .modal-header {
        display: flex;
        justify-content: space-between;
        align-items: start;
        gap: 12px;
      }

      .modal-title {
        margin: 0 0 10px;
        font-size: clamp(1.8rem, 3vw, 3rem);
      }

      .modal-meta {
        display: flex;
        flex-wrap: wrap;
        gap: 12px;
        color: var(--muted);
        font-size: 0.9rem;
      }

      .close-btn {
        background: rgba(255,255,255,0.06);
        border: 1px solid rgba(255,255,255,0.08);
        color: var(--text);
        border-radius: 999px;
        padding: 8px 12px;
        cursor: pointer;
      }

      .modal-actions {
        display: flex;
        flex-wrap: wrap;
        gap: 12px;
        margin-top: 18px;
      }

      .modal p {
        margin: 18px 0 0;
        color: var(--soft);
        line-height: 1.6;
      }

      @media (max-width: 1280px) {
        .app {
          grid-template-columns: 220px minmax(0,1fr);
        }

        .rightbar {
          display: none;
        }
      }

      @media (max-width: 960px) {
        .app {
          grid-template-columns: 1fr;
        }

        .sidebar {
          border-right: none;
          border-bottom: 1px solid rgba(255,255,255,0.08);
        }

        .browser-body {
          grid-template-columns: 1fr;
        }

        .browser-sidebar {
          border-right: none;
          border-bottom: 1px solid rgba(255,255,255,0.08);
        }

        .card-grid {
          grid-template-columns: repeat(2, minmax(0, 1fr));
        }
      }

      @media (max-width: 620px) {
        .topbar {
          flex-direction: column;
          align-items: flex-start;
        }

        .search-wrap {
          width: 100%;
          max-width: none;
        }

        .card-grid, .browser-grid {
          grid-template-columns: 1fr;
        }

        .hero {
          height: 340px;
        }
      }
    </style>
  </head>
  <body>
    <div class="app">
      <aside class="sidebar">
        <div class="brand">
          <div class="brand-mark">N</div>
          <div class="brand-name">NovaSphere</div>
        </div>

        <div class="nav-section">
          <div class="nav-title">Main</div>
          <div class="nav-item active" data-target="browserSection"><div class="nav-icon">◈</div>Home</div>
          <div class="nav-item" data-target="browserSection"><div class="nav-icon">◌</div>Discover</div>
          <div class="nav-item" data-target="chatSection"><div class="nav-icon">◍</div>Community</div>
          <div class="nav-item" data-target="moviesSection"><div class="nav-icon">★</div>Favorites</div>
        </div>

        <div class="nav-section">
          <div class="nav-title">Explore</div>
          <div class="nav-item" data-target="moviesSection"><div class="nav-icon">▶</div>Movies</div>
          <div class="nav-item" data-target="moviesSection"><div class="nav-icon">▣</div>Shows</div>
          <div class="nav-item" data-target="gamesSection"><div class="nav-icon">◧</div>Games</div>
          <div class="nav-item" data-target="voiceSection"><div class="nav-icon">☎</div>Voice</div>
        </div>

        <div class="profile-card">
          <div class="profile-row">
            <div class="avatar a1">GM</div>
            <div>
              <div class="profile-name">Guest Mode</div>
              <div class="profile-meta">Level 29</div>
            </div>
          </div>

          <div class="stats">
            <div class="stat-box">
              <strong>148</strong>
              <span>Friends</span>
            </div>
            <div class="stat-box">
              <strong>42</strong>
              <span>Rooms</span>
            </div>
            <div class="stat-box">
              <strong>9.8</strong>
              <span>Rating</span>
            </div>
          </div>
        </div>
      </aside>

      <main class="main-panel">
        <header class="topbar">
          <div class="search-wrap">
            <span class="search-icon">⌕</span>
            <input class="search" type="text" placeholder="Search movies, games, creators, rooms..." />
          </div>

          <div class="top-actions">
            <button class="ghost-btn" type="button">Invite</button>
            <button class="primary-btn" type="button">Create Room</button>
          </div>
        </header>

        <div class="content-wrap">
          <section class="section active" id="browserSection">
            <div class="browser-panel">
              <div class="browser-top">
                <div class="traffic">
                  <div class="dot red"></div>
                  <div class="dot yellow"></div>
                  <div class="dot green"></div>
                </div>
                <div class="browser-bar">novasphere.app/explore</div>
              </div>

              <div class="browser-body">
                <aside class="browser-sidebar">
                  <a href="#" class="browser-link active">Explore</a>
                  <a href="#" class="browser-link">Live</a>
                  <a href="#" class="browser-link">Movies</a>
                  <a href="#" class="browser-link">Games</a>
                  <a href="#" class="browser-link">Friends</a>
                  <a href="#" class="browser-link">Saved</a>
                </aside>

                <div class="browser-page">
                  <div class="browser-hero">
                    <h2>Discover the internet together.</h2>
                  </div>

                  <div class="browser-grid">
                    <div class="browser-card">
                      <div class="image" style="background-image:url('https://images.unsplash.com/photo-1517604931442-7e0c8ed2963c?auto=format&fit=crop&w=1200&q=80')"></div>
                      <div class="body">
                        <h4>Movie Night</h4>
                        <p>Watch premieres with your friends in one room.</p>
                      </div>
                    </div>

                    <div class="browser-card">
                      <div class="image" style="background-image:url('https://images.unsplash.com/photo-1493711662062-fa541adb3fc8?auto=format&fit=crop&w=1200&q=80')"></div>
                      <div class="body">
                        <h4>Arcade Lounge</h4>
                        <p>Play quick games and compete in real time.</p>
                      </div>
                    </div>

                    <div class="browser-card">
                      <div class="image" style="background-image:url('https://images.unsplash.com/photo-1524985069026-dd778a71c7b4?auto=format&fit=crop&w=1200&q=80')"></div>
                      <div class="body">
                        <h4>Community Rooms</h4>
                        <p>Join public or private social spaces.</p>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </section>

          <section class="section" id="gamesSection">
            <div class="game-card">
              <div class="game-head">
                <h3>Mini Game</h3>
                <div class="score-badge" id="scoreDisplay">0 / 6</div>
              </div>
              <div class="mini-scene" id="miniScene"></div>
              <div class="game-footer">
                <div class="game-hint" id="gameHint">Find the movie clues.</div>
                <button class="tiny-btn primary" id="restartGameBtn" type="button">Restart</button>
              </div>
            </div>
          </section>

          <section class="section" id="moviesSection">
            <div class="hero">
              <div class="hero-glow"></div>
              <div class="hero-content">
                <div class="eyebrow">Featured Premiere</div>
                <h1 id="heroTitle">Night Drift</h1>
                <div class="hero-meta">
                  <span>2026</span>
                  <span>Drama / Sci‑Fi</span>
                  <span>2h 12m</span>
                  <span>4.9/5</span>
                </div>
                <div class="hero-actions">
                  <button class="primary-btn" id="watchNowBtn" type="button">Watch Now</button>
                  <button class="secondary-btn" type="button">+ My List</button>
                </div>
              </div>
            </div>

            <div class="section-header">
              <h2>Trending Now</h2>
              <div class="more">View all</div>
            </div>

            <div class="card-grid" id="movieGrid"></div>

            <div class="player-card">
              <video id="movieVideo" controls playsinline poster="https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?auto=format&fit=crop&w=1200&q=80">
                <source src="https://interactive-examples.mdn.mozilla.net/media/cc0-videos/flower.mp4" type="video/mp4">
              </video>
            </div>
          </section>

          <section class="section" id="chatSection">
            <div class="chat-panel">
              <div class="chat-header">
                <h3>Community Chat</h3>
                <div class="online-pill">24 online</div>
              </div>

              <div class="chat-box" id="chatBox">
                <div class="msg other">Hey everyone! Anyone watching the new movie tonight?</div>
                <div class="msg self">I’m in. Let’s do a group watch.</div>
                <div class="msg other">I’ve got the room ready. You can join anytime.</div>
                <div class="msg self">Perfect. I’ll bring snacks.</div>
              </div>

              <div class="composer">
                <input id="chatInput" type="text" placeholder="Type a message..." />
                <button class="primary-btn" id="sendChatBtn" type="button">Send</button>
              </div>
            </div>
          </section>

          <section class="section" id="voiceSection">
            <div class="voice-panel">
              <div class="voice-head">
                <h3>Voice Chat</h3>
                <div class="online-pill">Live</div>
              </div>

              <div class="voice-users">
                <div class="voice-user">
                  <div class="user-name">
                    <div class="avatar a1" style="width:30px;height:30px;">A</div>
                    <div>
                      <div>Alice</div>
                      <div class="muted-text">Hosting room</div>
                    </div>
                  </div>
                  <div class="status"></div>
                </div>

                <div class="voice-user">
                  <div class="user-name">
                    <div class="avatar a2" style="width:30px;height:30px;">B</div>
                    <div>
                      <div>Ben</div>
                      <div class="muted-text">Talking</div>
                    </div>
                  </div>
                  <div class="status"></div>
                </div>

                <div class="voice-user">
                  <div class="user-name">
                    <div class="avatar a3" style="width:30px;height:30px;">C</div>
                    <div>
                      <div>Chloe</div>
                      <div class="muted-text">Muted</div>
                    </div>
                  </div>
                  <div class="status muted"></div>
                </div>

                <div class="voice-user">
                  <div class="user-name">
                    <div class="avatar a4" style="width:30px;height:30px;">D</div>
                    <div>
                      <div>Dan</div>
                      <div class="muted-text">Away</div>
                    </div>
                  </div>
                  <div class="status idle"></div>
                </div>
              </div>

              <div class="voice-actions">
                <button class="tiny-btn primary" type="button">Join Voice</button>
                <button class="tiny-btn" type="button">Mute</button>
                <button class="tiny-btn" type="button">Settings</button>
              </div>
            </div>
          </section>
        </div>
      </main>

      <aside class="rightbar">
        <div class="right-stack">
          <div class="feed-card">
            <div class="feed-head">
              <h3>Room Feed</h3>
              <div class="online-pill">Live</div>
            </div>
            <div class="feed-body">
              <div class="friend-row">
                <div class="friend-meta">
                  <div class="avatar a1" style="width:28px;height:28px;font-size:0.7rem;">A</div>
                  <div>
                    <div>Alice</div>
                    <div class="muted-text">Hosting</div>
                  </div>
                </div>
                <div class="status"></div>
              </div>

              <div class="friend-row">
                <div class="friend-meta">
                  <div class="avatar a2" style="width:28px;height:28px;font-size:0.7rem;">B</div>
                  <div>
                    <div>Ben</div>
                    <div class="muted-text">Playing</div>
                  </div>
                </div>
                <div class="status"></div>
              </div>

              <div class="friend-row">
                <div class="friend-meta">
                  <div class="avatar a3" style="width:28px;height:28px;font-size:0.7rem;">C</div>
                  <div>
                    <div>Chloe</div>
                    <div class="muted-text">Watching</div>
                  </div>
                </div>
                <div class="status"></div>
              </div>
            </div>
          </div>

          <div class="feed-card">
            <div class="feed-head">
              <h3>Friends</h3>
              <div class="online-pill">42 online</div>
            </div>
            <div class="feed-body">
              <div class="friend-row">
                <div class="friend-meta">
                  <div class="avatar a1" style="width:28px;height:28px;font-size:0.7rem;">L</div>
                  <div>
                    <div>Lana</div>
                    <div class="muted-text">Available</div>
                  </div>
                </div>
                <div class="status"></div>
              </div>

              <div class="friend-row">
                <div class="friend-meta">
                  <div class="avatar a2" style="width:28px;height:28px;font-size:0.7rem;">K</div>
                  <div>
                    <div>Kai</div>
                    <div class="muted-text">In chat</div>
                  </div>
                </div>
                <div class="status"></div>
              </div>

              <div class="friend-row">
                <div class="friend-meta">
                  <div class="avatar a3" style="width:28px;height:28px;font-size:0.7rem;">R</div>
                  <div>
                    <div>Rin</div>
                    <div class="muted-text">Away</div>
                  </div>
                </div>
                <div class="status idle"></div>
              </div>
            </div>
          </div>
        </div>
      </aside>
    </div>

    <div class="modal" id="movieModal">
      <div class="modal-card">
        <div class="modal-image" id="modalImage"></div>
        <div class="modal-body">
          <div class="modal-header">
            <div>
              <h3 class="modal-title" id="modalTitle">Night Drift</h3>
              <div class="modal-meta">
                <span>2026</span>
                <span>Drama / Sci‑Fi</span>
                <span>2h 12m</span>
                <span>4.9/5</span>
              </div>
            </div>
            <button class="close-btn" id="closeModalBtn" type="button">Close</button>
          </div>

          <div class="modal-actions">
            <button class="primary-btn" type="button">Watch Now</button>
            <button class="secondary-btn" type="button">+ My List</button>
          </div>

          <p id="modalDescription">
            A rogue group of pilots searches for a lost signal buried beneath the final frontier. As reality folds and trust breaks apart, one impossible mission becomes a fight for the future.
          </p>
        </div>
      </div>
    </div>

    <script>
      const navItems = document.querySelectorAll(".nav-item");
      const sections = document.querySelectorAll(".section");

      navItems.forEach((item) => {
        item.addEventListener("click", () => {
          navItems.forEach((el) => el.classList.remove("active"));
          item.classList.add("active");

          const targetId = item.dataset.target;
          sections.forEach((section) => {
            section.classList.toggle("active", section.id === targetId);
          });
        });
      });

      const movies = [
        {
          title: "Night Drift",
          tag: "Movie",
          year: "2026",
          rating: "4.9",
          description: "A rogue group of pilots searches for a lost signal buried beneath the final frontier. As reality folds and trust breaks apart, one impossible mission becomes a fight for the future.",
          image: "https://images.unsplash.com/photo-1517604931442-7e0c8ed2963c?auto=format&fit=crop&w=1000&q=80"
        },
        {
          title: "Skyline Echo",
          tag: "Series",
          year: "2025",
          rating: "4.8",
          description: "A long-buried radio signal awakens a forgotten city and draws strangers together in the middle of a collapsing sky.",
          image: "https://images.unsplash.com/photo-1504384308090-c894fdcc538d?auto=format&fit=crop&w=1000&q=80"
        },
        {
          title: "Pixel Harbor",
          tag: "Movie",
          year: "2024",
          rating: "4.7",
          description: "A future city of glass and light hides a secret beneath its waters, and a young hacker may be the only one who can save it.",
          image: "https://images.unsplash.com/photo-1513106580091-1d82408b8cd6?auto=format&fit=crop&w=1000&q=80"
        },
        {
          title: "Signal Zero",
          tag: "Series",
          year: "2026",
          rating: "4.9",
          description: "When a dead transmission comes back online, an elite team must follow it across a fractured world before it reaches the wrong hands.",
          image: "https://images.unsplash.com/photo-1489599849927-2ee91cede3ba?auto=format&fit=crop&w=1000&q=80"
        }
      ];

      const movieGrid = document.getElementById("movieGrid");
      const heroTitle = document.getElementById("heroTitle");
      const movieVideo = document.getElementById("movieVideo");
      const watchNowBtn = document.getElementById("watchNowBtn");

      function renderMovies() {
        movieGrid.innerHTML = "";

        movies.forEach((movie) => {
          const card = document.createElement("div");
          card.className = "media-card";

          card.innerHTML = `
            <div class="poster" style="background-image: url('${movie.image}')">
              <div class="poster-badge">${movie.tag}</div>
            </div>
            <div class="card-body">
              <h3 class="card-title">${movie.title}</h3>
              <p class="card-meta">${movie.year} • ${movie.rating}/5</p>
            </div>
          `;

          card.addEventListener("click", () => {
            heroTitle.textContent = movie.title;
            modalTitle.textContent = movie.title;
            modalDescription.textContent = movie.description;
            modalImage.style.backgroundImage = `url('${movie.image}')`;
            modal.classList.add("active");
          });

          movieGrid.appendChild(card);
        });
      }

      renderMovies();

      watchNowBtn.addEventListener("click", () => {
        movieVideo.play();
      });

      const modal = document.getElementById("movieModal");
      const modalTitle = document.getElementById("modalTitle");
      const modalDescription = document.getElementById("modalDescription");
      const modalImage = document.getElementById("modalImage");
      const closeModalBtn = document.getElementById("closeModalBtn");

      closeModalBtn.addEventListener("click", () => {
        modal.classList.remove("active");
      });

      modal.addEventListener("click", (event) => {
        if (event.target === modal) {
          modal.classList.remove("active");
        }
      });

      const chatInput = document.getElementById("chatInput");
      const chatBox = document.getElementById("chatBox");
      const sendChatBtn = document.getElementById("sendChatBtn");

      sendChatBtn.addEventListener("click", () => {
        const value = chatInput.value.trim();
        if (!value) return;

        const selfMsg = document.createElement("div");
        selfMsg.className = "msg self";
        selfMsg.textContent = value;
        chatBox.appendChild(selfMsg);

        chatInput.value = "";

        const reply = document.createElement("div");
        reply.className = "msg other";
        reply.textContent = "Sounds good! I’ll join the room.";
        chatBox.appendChild(reply);

        chatBox.scrollTop = chatBox.scrollHeight;
      });

      chatInput.addEventListener("keydown", (event) => {
        if (event.key === "Enter") {
          sendChatBtn.click();
        }
      });

      class MiniGame {
        constructor() {
          this.scene = document.getElementById("miniScene");
          this.scoreEl = document.getElementById("scoreDisplay");
          this.hintEl = document.getElementById("gameHint");
          this.restartBtn = document.getElementById("restartGameBtn");
          this.items = [];
          this.found = 0;
          this.sceneSize = { width: 0, height: 0 };
          this.setup();
        }

        setup() {
          this.bindEvents();
          this.resetSceneSize();
          this.start();
        }

        bindEvents() {
          this.restartBtn.addEventListener("click", () => this.start());
          window.addEventListener("resize", () => this.resetSceneSize());
        }

        resetSceneSize() {
          const rect = this.scene.getBoundingClientRect();
          this.sceneSize.width = rect.width;
          this.sceneSize.height = rect.height;
        }

        start() {
          this.scene.innerHTML = "";
          this.items = [];
          this.found = 0;
          this.hintEl.textContent = "Find the movie clues.";
          this.renderScore();

          const clues = [
            { name: "Ticket", emoji: "🎟️" },
            { name: "Popcorn", emoji: "🍿" },
            { name: "Play", emoji: "▶️" },
            { name: "Camera", emoji: "🎥" },
            { name: "Reel", emoji: "🎞️" },
            { name: "Clapperboard", emoji: "🎬" }
          ];

          clues.forEach((clue) => {
            let x = 0;
            let y = 0;
            let tries = 0;

            do {
              x = Math.random() * (this.sceneSize.width - 80) + 40;
              y = Math.random() * (this.sceneSize.height - 80) + 40;
              tries++;
            } while (
              tries < 250 &&
              this.items.some((item) => {
                const dx = x - item.x;
                const dy = y - item.y;
                return Math.hypot(dx, dy) < 72;
              })
            );

            const obj = { ...clue, x, y, found: false };
            this.items.push(obj);
            this.createItem(obj);
          });
        }

        createItem(item) {
          const btn = document.createElement("button");
          btn.type = "button";
          btn.className = "findable";
          btn.style.left = `${item.x}px`;
          btn.style.top = `${item.y}px`;
          btn.setAttribute("aria-label", `Find ${item.name}`);

          const sprite = document.createElement("span");
          sprite.className = "sprite";
          sprite.textContent = item.emoji;

          btn.appendChild(sprite);
          btn.addEventListener("click", () => this.onFound(item, btn));
          this.scene.appendChild(btn);
        }

        onFound(item, button) {
          if (item.found) return;

          item.found = true;
          button.classList.add("found");
          button.classList.add("hidden");

          this.found += 1;
          this.renderScore();

          if (this.found === this.items.length) {
            this.hintEl.textContent = "You found them all!";
            this.showWinOverlay();
          } else {
            this.hintEl.textContent = `Nice! ${this.found} found so far.`;
          }
        }

        renderScore() {
          this.scoreEl.textContent = `${this.found} / ${this.items.length}`;
        }

        showWinOverlay() {
          const overlay = document.createElement("div");
          overlay.style.position = "absolute";
          overlay.style.inset = "0";
          overlay.style.display = "grid";
          overlay.style.placeItems = "center";
          overlay.style.background = "rgba(0,0,0,0.42)";
          overlay.style.backdropFilter = "blur(2px)";
          overlay.style.fontSize = "clamp(1.3rem, 2vw, 2.1rem)";
          overlay.style.fontWeight = "800";
          overlay.style.color = "#d1fae5";
          overlay.textContent = "You found all clues!";
          this.scene.appendChild(overlay);
        }
      }

      new MiniGame();
    </script>
  </body>
</html>
