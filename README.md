<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Achroma | Real Movies, Games & Browser</title>
    <meta
      name="description"
      content="Achroma is a legal entertainment platform with real movie trailers, official games, and a browser launcher to real sites."
    />
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap"
      rel="stylesheet"
    />
    <style>
      :root {
        --bg: #070b12;
        --bg-2: #0d1420;
        --panel: rgba(16, 23, 35, 0.82);
        --panel-strong: rgba(12, 18, 29, 0.9);
        --line: rgba(148, 163, 184, 0.14);
        --text: #edf2ff;
        --text-soft: #dfe7ff;
        --muted: #9aa9bd;
        --primary: #7c3aed;
        --primary-2: #8b5cf6;
        --accent: #22d3ee;
        --success: #34d399;
        --gold: #fbbf24;
        --danger: #f87171;
        --shadow: 0 30px 80px rgba(2, 6, 23, 0.7);
        --container: 1220px;
      }

      * { box-sizing: border-box; }
      html { scroll-behavior: smooth; }
      body {
        margin: 0;
        font-family: "Inter", sans-serif;
        background:
          radial-gradient(circle at top left, rgba(124,58,237,0.18), transparent 25%),
          radial-gradient(circle at top right, rgba(34,211,238,0.12), transparent 24%),
          linear-gradient(180deg, #050a11 0%, #0a1120 52%, #0b1020 100%);
        color: var(--text);
        line-height: 1.6;
      }

      a { color: inherit; text-decoration: none; }
      img { display: block; max-width: 100%; }
      button, input { font: inherit; }

      .container {
        width: min(var(--container), calc(100% - 28px));
        margin: 0 auto;
      }

      .section {
        padding: 90px 0;
      }

      .eyebrow {
        display: inline-flex;
        align-items: center;
        gap: 12px;
        padding: 8px 14px;
        border-radius: 999px;
        background: rgba(124,58,237,0.12);
        border: 1px solid rgba(168,85,247,0.2);
        color: #d9c4ff;
        font-size: 11px;
        letter-spacing: 0.14em;
        font-weight: 700;
        text-transform: uppercase;
      }

      .eyebrow::before {
        content: "";
        width: 8px;
        height: 8px;
        border-radius: 50%;
        background: linear-gradient(135deg, #8b5cf6, #22d3ee);
        box-shadow: 0 0 16px rgba(124,58,237,0.9);
      }

      .btn {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        gap: 10px;
        padding: 15px 24px;
        border-radius: 14px;
        border: 1px solid transparent;
        font-weight: 700;
        cursor: pointer;
        transition: 0.25s ease;
      }

      .btn-primary {
        background: linear-gradient(135deg, var(--primary), var(--primary-2));
        color: white;
        box-shadow: 0 18px 35px rgba(124,58,237,0.35);
      }

      .btn-primary:hover {
        transform: translateY(-2px);
        box-shadow: 0 26px 45px rgba(124,58,237,0.4);
      }

      .btn-secondary {
        background: rgba(148,163,184,0.06);
        border-color: rgba(148,163,184,0.18);
        color: var(--text);
      }

      .btn-secondary:hover {
        background: rgba(148,163,184,0.12);
      }

      .header {
        position: sticky;
        top: 0;
        z-index: 50;
        backdrop-filter: blur(18px);
        background: rgba(6,11,18,0.56);
        border-bottom: 1px solid rgba(255,255,255,0.04);
      }

      .nav {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 18px 0;
      }

      .brand {
        display: inline-flex;
        align-items: center;
        gap: 12px;
        font-size: 1.48rem;
        font-weight: 800;
        letter-spacing: -0.04em;
      }

      .brand-mark {
        width: 32px;
        height: 32px;
        border-radius: 10px;
        background: linear-gradient(135deg, var(--primary), var(--accent));
        box-shadow: 0 0 24px rgba(124,58,237,0.7);
        position: relative;
      }

      .brand-mark::before {
        content: "";
        position: absolute;
        inset: 6px;
        border-radius: 7px;
        background: rgba(7,11,18,0.88);
      }

      .nav-links {
        display: flex;
        align-items: center;
        gap: 26px;
        color: var(--text-soft);
        font-size: 0.95rem;
      }

      .nav-links a:hover { color: var(--text); }

      .nav-actions {
        display: flex;
        align-items: center;
        gap: 14px;
      }

      .search {
        width: 42px;
        height: 42px;
        display: grid;
        place-items: center;
        border-radius: 12px;
        background: rgba(148,163,184,0.06);
        border: 1px solid var(--line);
        color: var(--text-soft);
      }

      .ham {
        display: none;
        width: 40px;
        height: 40px;
        border-radius: 12px;
        border: 1px solid var(--line);
        background: rgba(148,163,184,0.06);
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 5px;
        cursor: pointer;
      }

      .ham span {
        width: 18px;
        height: 2px;
        background: white;
        border-radius: 2px;
      }

      .hero {
        padding-top: 34px;
        padding-bottom: 20px;
      }

      .hero-box {
        position: relative;
        min-height: 660px;
        border-radius: 30px;
        overflow: hidden;
        border: 1px solid rgba(255,255,255,0.08);
        background:
          linear-gradient(90deg, rgba(4,7,13,0.96) 0%, rgba(4,7,13,0.72) 38%, rgba(4,7,13,0.22) 100%),
          url("https://images.unsplash.com/photo-1517604931442-7e0c8ed2963c?auto=format&fit=crop&w=1600&q=80") center/cover no-repeat;
        box-shadow: var(--shadow);
      }

      .hero-content {
        position: relative;
        z-index: 2;
        width: min(620px, calc(100% - 60px));
        padding: 62px 50px 50px;
      }

      .hero-meta {
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        gap: 14px;
        margin-bottom: 18px;
      }

      .meta-pill {
        display: inline-flex;
        align-items: center;
        gap: 8px;
        padding: 8px 12px;
        border-radius: 999px;
        border: 1px solid rgba(255,255,255,0.1);
        background: rgba(255,255,255,0.06);
        color: #e8efff;
        font-size: 0.76rem;
        font-weight: 600;
      }

      .hero-content h1 {
        font-size: clamp(3rem, 6vw, 6rem);
        line-height: 0.92;
        letter-spacing: -0.08em;
        margin: 0 0 18px;
      }

      .hero-content p {
        max-width: 560px;
        color: rgba(237,242,255,0.8);
        font-size: 1.08rem;
        margin-bottom: 28px;
      }

      .hero-actions {
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        gap: 16px;
        margin-bottom: 30px;
      }

      .hero-stats {
        display: flex;
        flex-wrap: wrap;
        gap: 24px;
      }

      .stat-box {
        min-width: 120px;
      }

      .stat-box .label {
        display: block;
        color: rgba(237,242,255,0.66);
        font-size: 0.8rem;
        margin-bottom: 6px;
      }

      .stat-box strong {
        font-size: 1.8rem;
        letter-spacing: -0.06em;
      }

      .hero-side-panel {
        position: absolute;
        right: 26px;
        bottom: 26px;
        width: min(320px, calc(100% - 40px));
        padding: 18px 16px;
        border-radius: 20px;
        background: rgba(15,23,42,0.84);
        border: 1px solid rgba(255,255,255,0.08);
        backdrop-filter: blur(12px);
        box-shadow: var(--shadow);
      }

      .hero-side-panel .row {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 8px;
        font-size: 0.75rem;
        letter-spacing: 0.12em;
        text-transform: uppercase;
        color: var(--text-soft);
      }

      .movie-title {
        font-size: 1.6rem;
        font-weight: 800;
        letter-spacing: -0.05em;
        margin-bottom: 10px;
      }

      .tags {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
      }

      .tag {
        padding: 6px 10px;
        border-radius: 999px;
        font-size: 0.72rem;
        font-weight: 600;
        border: 1px solid rgba(168,85,247,0.18);
        background: rgba(124,58,237,0.12);
        color: #d9c4ff;
      }

      .section-head {
        display: flex;
        justify-content: space-between;
        align-items: end;
        gap: 20px;
        margin-bottom: 28px;
      }

      .section-head h2 {
        margin: 14px 0 0;
        font-size: clamp(2.1rem, 3vw, 3.5rem);
        line-height: 1;
        letter-spacing: -0.06em;
      }

      .section-head p {
        color: var(--muted);
        max-width: 560px;
        margin: 0;
      }

      .chip-row {
        display: flex;
        flex-wrap: wrap;
        gap: 10px;
      }

      .chip {
        padding: 9px 14px;
        border-radius: 999px;
        background: rgba(148,163,184,0.04);
        border: 1px solid var(--line);
        color: var(--text-soft);
        font-size: 0.8rem;
        font-weight: 600;
      }

      .chip.active {
        background: linear-gradient(135deg, rgba(124,58,237,0.18), rgba(34,211,238,0.12));
        color: white;
        border-color: rgba(168,85,247,0.28);
      }

      .featured-player {
        margin-bottom: 24px;
        background: rgba(15,23,42,0.7);
        border: 1px solid var(--line);
        border-radius: 26px;
        overflow: hidden;
      }

      .video-wrap {
        position: relative;
        width: 100%;
        padding-top: 56.25%;
      }

      .video-wrap iframe {
        position: absolute;
        inset: 0;
        width: 100%;
        height: 100%;
        border: 0;
      }

      .media-grid {
        display: grid;
        grid-template-columns: repeat(5, minmax(0, 1fr));
        gap: 18px;
      }

      .card {
        position: relative;
        overflow: hidden;
        border-radius: 20px;
        border: 1px solid var(--line);
        background: rgba(15,23,42,0.7);
        transition: transform 0.25s ease, box-shadow 0.25s ease;
      }

      .card:hover {
        transform: translateY(-4px);
        box-shadow: 0 26px 50px rgba(0,0,0,0.25);
      }

      .poster {
        position: relative;
        aspect-ratio: 3 / 4.5;
        overflow: hidden;
      }

      .poster img {
        width: 100%;
        height: 100%;
        object-fit: cover;
      }

      .poster::after {
        content: "";
        position: absolute;
        inset: 0;
        background: linear-gradient(180deg, rgba(10,12,20,0.04), rgba(10,12,20,0.82));
      }

      .card-content {
        position: absolute;
        inset: auto 0 0 0;
        z-index: 1;
        padding: 18px 16px 16px;
      }

      .rating-row {
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-bottom: 8px;
      }

      .rating {
        display: inline-flex;
        align-items: center;
        gap: 6px;
        color: #fef3c7;
        font-size: 0.8rem;
      }

      .rating::before {
        content: "★";
        color: var(--gold);
      }

      .duration {
        color: rgba(237,242,255,0.72);
        font-size: 0.75rem;
      }

      .card-title {
        margin: 0;
        font-size: 1.08rem;
        letter-spacing: -0.04em;
        font-weight: 700;
      }

      .sub {
        margin-top: 5px;
        color: rgba(237,242,255,0.76);
        font-size: 0.76rem;
      }

      .feature-panel {
        background: rgba(15, 23, 42, 0.7);
        border: 1px solid var(--line);
        border-radius: 28px;
        overflow: hidden;
      }

      .feature-panel.large {
        display: grid;
        grid-template-columns: 1.25fr 0.75fr;
      }

      .feature-image {
        min-height: 330px;
        background:
          linear-gradient(135deg, rgba(10,12,20,0.18), rgba(10,12,20,0.78)),
          url("https://images.unsplash.com/photo-1524985069026-dd778a71c7b4?auto=format&fit=crop&w=1200&q=80") center/cover no-repeat;
      }

      .feature-copy {
        padding: 28px 26px;
      }

      .feature-copy h3 {
        margin: 18px 0 12px;
        font-size: clamp(2rem, 2.9vw, 3rem);
        letter-spacing: -0.06em;
        line-height: 1;
      }

      .feature-copy p {
        color: var(--muted);
        margin: 0 0 18px;
      }

      .mini-list {
        list-style: none;
        margin: 0 0 22px;
        padding: 0;
      }

      .mini-list li {
        display: flex;
        align-items: center;
        gap: 10px;
        color: var(--text-soft);
        margin-bottom: 10px;
      }

      .mini-list li::before {
        content: "✓";
        width: 22px;
        height: 22px;
        display: inline-grid;
        place-items: center;
        border-radius: 50%;
        background:*

