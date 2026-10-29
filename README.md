<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Northstar Studio</title>
    <meta
      name="description"
      content="Modern website template with premium design and strong conversion structure."
    />
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap"
      rel="stylesheet"
    />
    <style>
      :root {
        --bg: #07111f;
        --bg-soft: #0d1b2d;
        --panel: rgba(13, 27, 45, 0.8);
        --panel-strong: #101d32;
        --text: #ecf7ff;
        --muted: #9ab5cc;
        --primary: #7c9cff;
        --primary-strong: #5f7dff;
        --secondary: #7ef0d8;
        --accent: #ffbf69;
        --line: rgba(154, 181, 204, 0.15);
        --shadow: 0 20px 60px rgba(14, 22, 36, 0.45);
        --radius: 22px;
        --max-width: 1200px;
      }

      * { box-sizing: border-box; }

      html {
        scroll-behavior: smooth;
      }

      body {
        margin: 0;
        font-family: "Inter", sans-serif;
        background:
          radial-gradient(circle at top left, rgba(124, 156, 255, 0.16), transparent 24%),
          radial-gradient(circle at top right, rgba(126, 240, 216, 0.12), transparent 22%),
          var(--bg);
        color: var(--text);
        line-height: 1.6;
      }

      img { max-width: 100%; display: block; }

      a {
        color: inherit;
        text-decoration: none;
      }

      button {
        font: inherit;
        cursor: pointer;
      }

      .container {
        width: min(var(--max-width), calc(100% - 32px));
        margin: 0 auto;
      }

      .section {
        padding: 110px 0;
      }

      .eyebrow {
        display: inline-block;
        font-size: 12px;
        letter-spacing: 0.14em;
        text-transform: uppercase;
        color: var(--secondary);
        background: rgba(126, 240, 216, 0.08);
        border: 1px solid rgba(126, 240, 216, 0.12);
        padding: 9px 12px;
        border-radius: 999px;
        font-weight: 700;
      }

      h1, h2, h3, h4, p {
        margin-top: 0;
      }

      h1 {
        font-size: clamp(2.8rem, 6vw, 5rem);
        line-height: 0.98;
        letter-spacing: -0.07em;
        margin-bottom: 18px;
      }

      h2 {
        font-size: clamp(2rem, 4vw, 3.2rem);
        line-height: 1.08;
        letter-spacing: -0.06em;
        margin-bottom: 16px;
      }

      p {
        color: var(--muted);
        font-size: 1.02rem;
      }

      .btn {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        gap: 10px;
        min-height: 52px;
        padding: 0 22px;
        border-radius: 14px;
        border: 1px solid transparent;
        transition: 0.2s ease;
        font-weight: 700;
      }

      .btn.primary {
        background: linear-gradient(135deg, var(--primary), var(--primary-strong));
        color: white;
        box-shadow: 0 12px 28px rgba(95, 125, 255, 0.45);
      }

      .btn.primary:hover {
        transform: translateY(-2px);
      }

      .btn.secondary {
        background: rgba(255, 255, 255, 0.02);
        border-color: var(--line);
        color: var(--text);
      }

      .btn.secondary:hover {
        background: rgba(255, 255, 255, 0.04);
      }

      .site-header {
        position: sticky;
        top: 0;
        z-index: 1000;
        backdrop-filter: blur(18px);
        background: rgba(7, 17, 31, 0.52);
        border-bottom: 1px solid rgba(255,255,255,0.04);
      }

      .nav {
        display: flex;
        align-items: center;
        justify-content: space-between;
        min-height: 76px;
      }

      .brand {
        display: flex;
        align-items: center;
        gap: 12px;
        font-weight: 800;
        letter-spacing: -0.04em;
      }

      .brand-mark {
        width: 32px;
        height: 32px;
        border-radius: 12px;
        display: grid;
        place-items: center;
        background: linear-gradient(135deg, var(--primary), var(--secondary));
        color: #06131f;
        font-weight: 900;
        box-shadow: 0 8px 20px rgba(124, 156, 255, 0.38);
      }

      .nav-links {
        display: flex;
        align-items: center;
        gap: 32px;
        color: var(--muted);
      }

      .nav-links a {
        transition: color 0.2s ease;
      }

      .nav-links a:hover {
        color: var(--text);
      }

      .nav-actions {
        display: flex;
        align-items: center;
        gap: 14px;
      }

      .nav-toggle {
        display: none;
      }

      .hero {
        padding-top: 72px;
        padding-bottom: 36px;
      }

      .hero-grid {
        display: grid;
        grid-template-columns: 1.12fr 0.88fr;
        align-items: center;
        gap: 48px;
      }

      .hero-copy {
        max-width: 650px;
      }

      .hero-copy p {
        font-size: 1.15rem;
        max-width: 560px;
        margin-bottom: 28px;
      }

      .cta-row {
        display: flex;
        flex-wrap: wrap;
        gap: 16px;
        margin-bottom: 30px;
      }

      .mini-proof {
        display: flex;
        align-items: center;
        gap: 20px;
        flex-wrap: wrap;
        color: var(--muted);
        font-size: 0.9rem;
      }

      .avatares {
        display: flex;
        align-items: center;
      }

      .avatar {
        width: 34px;
        height: 34px;
        border-radius: 50%;
        border: 2px solid var(--bg);
        margin-left: -8px;
        background: linear-gradient(135deg, #ffbf69, #a784ff);
      }

      .avatar:first-child {
        margin-left: 0;
      }

      .avatar:nth-child(2) {
        background: linear-gradient(135deg, #7ef0d8, #60a5fa);
      }

      .avatar:nth-child(3) {
        background: linear-gradient(135deg, #ef7cb1, #f9c784);
      }

      .hero-visual {
        position: relative;
      }

      .dashboard {
        position: relative;
        background: rgba(20, 31, 49, 0.9);
        border: 1px solid var(--line);
        border-radius: 28px;
        box-shadow: var(--shadow);
        overflow: hidden;
      }

      .dashboard-topbar {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 18px 22px;
        border-bottom: 1px solid var(--line);
      }

      .dots {
        display: flex;
        gap: 8px;
      }

      .dot {
        width: 10px;
        height: 10px;
        border-radius: 50%;
      }

      .dot.red { background: #ff7a7a; }
      .dot.yellow { background: #ffce6b; }
      .dot.green { background: #77e9ae; }

      .dashboard-body {
        padding: 22px;
      }

      .chart-card {
        background: linear-gradient(180deg, rgba(124,156,255,0.12), rgba(124,156,255,0.02));
        border: 1px solid rgba(124,156,255,0.16);
        border-radius: 20px;
        padding: 18px;
      }

      .chart-legend {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 12px;
        margin-bottom: 18px;
      }

      .spark {
        height: 180px;
        border-radius: 16px;
        background:
          linear-gradient(180deg, rgba(126,240,216,0.15), rgba(126,240,216,0.02)),
          linear-gradient(90deg, rgba(255,255,255,0.04) 1px, transparent 1px),
          linear-gradient(rgba(255,255,255,0.04) 1px, transparent 1px);
        background-size: auto, 32px 32px, 32px 32px;
        position: relative;
        overflow: hidden;
      }

      .spark svg {
        position: absolute;
        inset: 0;
        width: 100%;
        height: 100%;
      }

      .floating-card {
        position: absolute;
        right: -18px;
        bottom: 26px;
        width: 210px;
        background: rgba(12, 25, 39, 0.9);
        border: 1px solid var(--line);
        border-radius: 18px;
        padding: 16px;
        box-shadow: var(--shadow);
      }

      .metric-row {
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-bottom: 10px;
      }

      .metric-number {
        font-size: 1.9rem;
        font-weight: 800;
        letter-spacing: -0.06em;
      }

      .pill {
        font-size: 0.76rem;
        font-weight: 700;
        color: var(--secondary);
        background: rgba(126, 240, 216, 0.08);
        padding: 6px 9px;
        border-radius: 999px;
      }

      .stats-strip {
        display: grid;
        grid-template-columns: repeat(4, minmax(0, 1fr));
        gap: 18px;
        margin-top: 34px;
      }

      .stat {
        background: rgba(255,255,255,0.02);
        border: 1px solid var(--line);
        border-radius: 18px;
        padding: 22px 18px;
      }

      .stat strong {
        display: block;
        font-size: clamp(1.6rem, 2vw, 2.3rem);
        font-weight: 800;
        letter-spacing: -0.06em;
      }

      .section-header {
        display: flex;
        align-items: end;
        justify-content: space-between;
        gap: 18px;
        margin-bottom: 34px;
      }

      .section-header p {
        max-width: 520px;
      }

      .feature-grid {
        display: grid;
        grid-template-columns: repeat(3, minmax(0, 1fr));
        gap: 20px;
      }

      .feature-card {
        background: rgba(255,255,255,0.02);
        border: 1px solid var(--line);
        border-radius: 22px;
        padding: 28px 22px;
        transition: transform 0.25s ease, border-color 0.25s ease;
      }

      .feature-card:hover {
        transform: translateY(-6px);
        border-color: rgba(124, 156, 255, 0.45);
      }

      .icon-wrap {
        display: grid;
        place-items: center;
        width: 52px;
        height: 52px;
        border-radius: 16px;
        margin-bottom: 18px;
        font-size: 1.3rem;
        background: linear-gradient(135deg, rgba(124,156,255,0.18), rgba(126,240,216,0.18));
        border: 1px solid rgba(124,156,255,0.2);
      }

      .feature-card h3 {
        font-size: 1.35rem;
        margin-bottom: 12px;
      }

      .showcase {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 26px;
        align-items: center;
      }

      .showcase-panel {
        background: rgba(255,255,255,0.02);
        border: 1px solid var(--line);
        border-radius: 28px;
        padding: 26px;
      }

      .showcase-list {
        list-style: none;
        margin: 26px 0 0 0;
        padding: 0;
      }

      .showcase-list li {
        display: flex;
        align-items: flex-start;
        gap: 12px;
        margin-bottom: 14px;
        color: var(--muted);
      }

      .check {
        width: 24px;
        height: 24px;
        border-radius: 50%;
        background: rgba(126, 240, 216, 0.12);
        color: var(--secondary);
        display: grid;
        place-items: center;
        font-weight: 900;
        flex-shrink: 0;
        margin-top: 2px;
      }

      .steps {
        display: grid;
        grid-template-columns: repeat(3, minmax(0,1fr));
        gap: 18px;
      }

      .step {
        background: rgba(255,255,255,0.02);
        border: 1px solid var(--line);
        border-radius: 24px;
        padding: 26px 20px;
      }

      .step-index {
        display: inline-flex;
        width: 42px;
        height: 42px;
        align-items: center;
        justify-content: center;*

