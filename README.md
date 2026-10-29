<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Achroma | Design. Build. Elevate.</title>
    <meta
      name="description"
      content="Achroma is a premium creative and digital studio helping brands grow through strategy, design, and digital experiences."
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
        --panel: rgba(17, 24, 39, 0.8);
        --panel-strong: #111827;
        --card: #0f172a;
        --muted: #9aa8bd;
        --text: #edf2ff;
        --text-soft: #c5d0e6;
        --primary: #7c3aed;
        --primary-2: #a855f7;
        --accent: #22d3ee;
        --success: #34d399;
        --border: rgba(148, 163, 184, 0.16);
        --shadow: 0 20px 50px rgba(17, 24, 39, 0.45);
        --radius: 22px;
        --container: 1180px;
      }

      * {
        box-sizing: border-box;
      }

      html {
        scroll-behavior: smooth;
      }

      body {
        margin: 0;
        font-family: "Inter", sans-serif;
        background:
          radial-gradient(circle at top left, rgba(124, 58, 237, 0.18), transparent 30%),
          radial-gradient(circle at top right, rgba(34, 211, 238, 0.10), transparent 25%),
          var(--bg);
        color: var(--text);
        line-height: 1.6;
      }

      img {
        max-width: 100%;
        display: block;
      }

      a {
        color: inherit;
        text-decoration: none;
      }

      .container {
        width: min(var(--container), calc(100% - 32px));
        margin: 0 auto;
      }

      .section {
        padding: 100px 0;
      }

      .eyebrow {
        display: inline-flex;
        align-items: center;
        gap: 10px;
        padding: 8px 14px;
        border-radius: 999px;
        background: rgba(124, 58, 237, 0.12);
        border: 1px solid rgba(168, 85, 247, 0.2);
        color: #d9c4ff;
        font-size: 12px;
        font-weight: 600;
        letter-spacing: 0.12em;
        text-transform: uppercase;
      }

      .eyebrow::before {
        content: "";
        width: 8px;
        height: 8px;
        border-radius: 50%;
        background: linear-gradient(135deg, var(--primary), var(--accent));
        box-shadow: 0 0 18px rgba(124, 58, 237, 0.8);
      }

      h1, h2, h3, h4, p {
        margin-top: 0;
      }

      .btn {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        gap: 10px;
        padding: 16px 24px;
        border-radius: 14px;
        font-weight: 700;
        transition: 0.25s ease;
        border: 1px solid transparent;
        cursor: pointer;
      }

      .btn-primary {
        background: linear-gradient(135deg, var(--primary), var(--primary-2));
        color: white;
        box-shadow: 0 20px 35px rgba(124, 58, 237, 0.35);
      }

      .btn-primary:hover {
        transform: translateY(-2px);
        box-shadow: 0 26px 40px rgba(124, 58, 237, 0.45);
      }

      .btn-secondary {
        background: rgba(148, 163, 184, 0.06);
        border-color: var(--border);
        color: var(--text);
      }

      .btn-secondary:hover {
        background: rgba(148, 163, 184, 0.1);
      }

      .header {
        position: sticky;
        top: 0;
        z-index: 50;
        backdrop-filter: blur(18px);
        background: rgba(7, 11, 18, 0.55);
        border-bottom: 1px solid rgba(255, 255, 255, 0.03);
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
        font-weight: 800;
        letter-spacing: -0.04em;
        font-size: 1.4rem;
      }

      .brand-mark {
        width: 30px;
        height: 30px;
        border-radius: 10px;
        background: linear-gradient(135deg, var(--primary), var(--accent));
        box-shadow: 0 0 24px rgba(124, 58, 237, 0.6);
        position: relative;
      }

      .brand-mark::before {
        content: "";
        position: absolute;
        inset: 6px;
        border-radius: 7px;
        background: rgba(7, 11, 18, 0.85);
      }

      .nav-links {
        display: flex;
        align-items: center;
        gap: 28px;
        color: var(--text-soft);
        font-size: 0.96rem;
      }

      .nav-links a:hover {
        color: var(--text);
      }

      .nav-actions {
        display: flex;
        align-items: center;
        gap: 14px;
      }

      .ham {
        display: none;
        flex-direction: column;
        gap: 5px;
        width: 38px;
        height: 38px;
        border-radius: 12px;
        background: rgba(148, 163, 184, 0.06);
        border: 1px solid var(--border);
        align-items: center;
        justify-content: center;
        cursor: pointer;
      }

      .ham span {
        width: 18px;
        height: 2px;
        background: white;
        border-radius: 2px;
      }

      .hero {
        padding-top: 60px;
        padding-bottom: 30px;
      }

      .hero-inner {
        display: grid;
        grid-template-columns: 1.1fr 0.9fr;
        align-items: center;
        gap: 50px;
      }

      .hero-copy h1 {
        font-size: clamp(2.8rem, 5vw, 6rem);
        line-height: 0.96;
        letter-spacing: -0.06em;
        margin-bottom: 20px;
      }

      .hero-copy h1 .gradient {
        background: linear-gradient(135deg, #d8b4fe, #7dd3fc 60%, #bbf7d0);
        -webkit-background-clip: text;
        background-clip: text;
        color: transparent;
      }

      .hero-copy p {
        font-size: 1.08rem;
        color: var(--muted);
        max-width: 620px;
        margin-bottom: 28px;
      }

      .hero-actions {
        display: flex;
        align-items: center;
        flex-wrap: wrap;
        gap: 16px;
        margin-bottom: 28px;
      }

      .mini-proof {
        display: flex;
        align-items: center;
        gap: 15px;
        color: var(--muted);
        font-size: 0.85rem;
      }

      .avatars {
        display: flex;
        align-items: center;*

