<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>CinemaWorld Pro</title>
    <style>
      :root {
        --bg: #070b14;
        --bg-2: #101827;
        --panel: #111827;
        --panel-2: #172235;
        --panel-3: #1d2a3c;
        --soft: #e8edf7;
        --muted: #aab7ce;
        --text: #f7f9fc;
        --gold: #f7c96a;
        --gold-2: #ef8f3e;
        --blue: #63a4ff;
        --purple: #7c5fff;
        --green: #3ad49d;
        --danger: #fb7185;
        --shadow: rgba(0, 0, 0, 0.4);
      }

      * {
        box-sizing: border-box;
      }

      html, body {
        margin: 0;
        min-height: 100vh;
        font-family: Arial, Helvetica, sans-serif;
        background:
          radial-gradient(circle at top, rgba(99, 164, 255, 0.12), transparent 30%),
          linear-gradient(180deg, var(--bg), var(--bg-2));
        color: var(--text);
      }

      body {
        display: grid;
        place-items: center;
      }

      button {
        font: inherit;
      }

      .app {
        width: min(1420px, 96vw);
        min-height: 92vh;
        background: rgba(8, 12, 20, 0.9);
        border: 1px solid rgba(255,255,255,0.08);
        border-radius: 28px;
        overflow: hidden;
        box-shadow: 0 30px 70px var(--shadow);
      }

      .topbar {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 20px;
        padding: 18px 22px;
        background: rgba(17, 24, 39, 0.82);
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
        font-weight: 900;
        color: #111827;
        background: linear-gradient(135deg, var(--gold), var(--gold-2));
      }

      .brand {
        font-size: 1.2rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        font-weight: 800;
      }

      .nav {
        display: flex;
        align-items: center;
        gap: 10px;
        flex-wrap: wrap;
      }

      .nav-chip {
        background: rgba(255,255,255,0.04);
        border: 1px solid rgba(255,255,255,0.08);
        color: var(--muted);
        padding: 8px 14px;
        border-radius: 999px;
        cursor: pointer;
        transition: all 0.12s ease;
      }

      .nav-chip.active {
        color: var(--text);
        background: linear-gradient(135deg, rgba(99,164,255,0.24), rgba(124,95,255,0.2));
        border-color: rgba(99,164,255,0.5);
      }

      .nav-chip:hover {
        border-color: rgba(255,255,255,0.16);
      }

      .user-pill {
        padding: 10px 14px;
        border-radius: 999px;
        background: rgba(255,255,255,0.04);
        border: 1px solid rgba(255,255,255,0.08);
        color: var(--soft);
      }

      .main {
        display: grid;
        grid-template-columns: minmax(0, 1.8fr) minmax(360px, 0.9fr);
        min-height: calc(92vh - 76px);
      }

      .content {
        padding: 20px;
        background: linear-gradient(180deg, rgba(17,24,39,0.9), rgba(7,11,18,0.95));
      }

      .hero {
        position: relative;
        height: 430px;
        border-radius: 28px;
        overflow: hidden;
        border: 1px solid rgba(255,255,255,0.08);
        background:
          linear-gradient(90deg, rgba(0,0,0,0.72), rgba(0,0,0,0.12)),
          url("https://images.unsplash.com/photo-1517604931442-7e0c8ed2963c?auto=format&fit=crop&w=1600&q=80") center/cover no-repeat;
      }

      .hero-glow {
        position: absolute;
        inset: 0;
        background: linear-gradient(180deg, rgba(0,0,0,0.15), rgba(0,0,0,0.55));
      }

      .hero-inner {
        position: absolute;
        left: 30px;
        right: 30px;
        bottom: 28px;
        z-index: 1;
      }

      .eyebrow {
        display: inline-block;
        border-radius: 999px;
        background: rgba(255,255,255,0.08);
        border: 1px solid rgba(255,255,255,0.12);
        color: var(--soft);
        font-size: 0.74rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        padding: 8px 12px;
      }

      .hero h1 {
        margin: 18px 0 10px;
        font-size: clamp(2.4rem, 5vw, 4.6rem);
        letter-spacing: -0.05em;
        line-height: 0.96;
      }

      .meta-row {
        display: flex;
        gap: 14px;
        flex-wrap: wrap;
        color: var(--soft);
        font-size: 0.9rem;
        margin-bottom: 20px;
      }

      .hero-actions {
        display: flex;
        gap: 12px;
        flex-wrap: wrap;
      }

      .btn {
        border: none;
        border-radius: 999px;
        padding: 12px 18px;
        font-weight: 800;
        cursor: pointer;
        transition: transform 0.12s ease, filter 0.12s ease;
      }

      .btn:hover {
        transform: translateY(-1px);
        filter: brightness(1.04);
      }

      .btn.primary {
        background: linear-gradient(135deg, var(--gold), var(--gold-2));
        color: #111827;
      }

      .btn.secondary {
        background: rgba(255,255,255,0.08);
        color: var(--text);
        border: 1px solid rgba(255,255,255,0.12);
      }

      .section {
        margin-top: 26px;
      }

      .section-head {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 14px;
      }

      .section-head h2 {
        margin: 0;
        font-size: 1.08rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        color: var(--soft);
      }

      .more {
        color: var(--gold);
        font-weight: 700;
        font-size: 0.9rem;
      }

      .cards {
        display: grid;
        grid-template-columns: repeat(4, minmax(0, 1fr));
        gap: 18px;
      }

      .card {
        border: 1px solid rgba(255,255,255,0.06);
        background: linear-gradient(180deg, rgba(22,33,50,0.9), rgba(10,15,25,0.95));
        border-radius: 20px;
        overflow: hidden;
        cursor: pointer;
        transition: transform 0.15s ease, border-color 0.15s ease;
      }

      .card:hover {
        transform: translateY(-2px);
        border-color: rgba(99,164,255,0.45);
      }

      .poster {
        position: relative;
        aspect-ratio: 4 / 5.3;
        background-size: cover;
        background-position: center;
      }

      .poster-badge {
        position: absolute;
        top: 10px;
        left: 10px;
        border-radius: 999px;
        background: rgba(12, 18, 29, 0.7);
        border: 1px solid rgba(255,255,255,0.12);
        color: var(--soft);
        font-size: 0.7rem;
        font-weight: 700;
        padding: 6px 8px;
      }

      .card-body {
        padding: 12px 12px 14px;
      }

      .card-title {
        font-size: 1rem;
        font-weight: 800;
        margin: 0 0 6px;
      }

      .card-meta {
        color: var(--muted);
        font-size: 0.82rem;
      }

      .sidebar {
        background*

