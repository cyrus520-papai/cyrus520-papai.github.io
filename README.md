<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Achroma | Watch, Play, Chat</title>
    <meta
      name="description"
      content="Achroma brings together real movie trailers, real games, and voice chat in one immersive entertainment hub."
    />
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap" rel="stylesheet" />
    <style>
      :root {
        --bg: #070b12;
        --bg-2: #0d1420;
        --panel: rgba(16, 23, 35, 0.88);
        --soft-panel: rgba(15, 23, 42, 0.7);
        --line: rgba(148, 163, 184, 0.12);
        --muted: #9aa9bd;
        --text: #edf2ff;
        --text-soft: #d6def1;
        --primary: #7c3aed;
        --primary-2: #8b5cf6;
        --accent: #22d3ee;
        --success: #34d399;
        --gold: #fbbf24;
        --danger: #f87171;
        --shadow: 0 30px 60px rgba(3, 7, 18, 0.6);
        --container: 1220px;
      }

      * { box-sizing: border-box; }
      html { scroll-behavior: smooth; }
      body {
        margin: 0;
        font-family: "Inter", sans-serif;
        line-height: 1.6;
        background:
          radial-gradient(circle at top left, rgba(124, 58, 237, 0.18), transparent 28%),
          radial-gradient(circle at top right, rgba(34, 211, 238, 0.12), transparent 22%),
          linear-gradient(180deg, #060911 0%, #0b1220 100%);
        color: var(--text);
      }
      a { color: inherit; text-decoration: none; }
      img { display: block; max-width: 100%; }
      button { font: inherit; }

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
        gap: 10px;
        padding: 8px 14px;
        border-radius: 999px;
        background: rgba(124, 58, 237, 0.12);
        border: 1px solid rgba(168, 85, 247, 0.2);
        color: #d9c4ff;
        font-size: 11px;
        font-weight: 700;
        letter-spacing: 0.14em;
        text-transform: uppercase;
      }
      .eyebrow::before {
        content: "";
        width: 8px;
        height: 8px;
        border-radius: 50%;
        background: linear-gradient(135deg, #8b5cf6, #22d3ee);
        box-shadow: 0 0 18px rgba(124, 58, 237, 0.8);
      }

      .btn {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        gap: 10px;
        padding: 15px 24px;
        border-radius: 14px;
        border: 1px solid transparent;
        cursor: pointer;
        font-weight: 700;
        transition: 0.25s ease;
      }
      .btn-primary {
        background: linear-gradient(135deg, var(--primary), var(--primary-2));
        color: white;
        box-shadow: 0 18px 35px rgba(124, 58, 237, 0.35);
      }
      .btn-primary:hover {
        transform: translateY(-2px);
        box-shadow: 0 26px 45px rgba(124, 58, 237, 0.4);
      }
      .btn-secondary {
        background: rgba(148, 163, 184, 0.07);
        border-color: rgba(148, 163, 184, 0.18);
        color: var(--text);
      }
      .btn-secondary:hover {
        background: rgba(148, 163, 184, 0.12);
      }

      .header {
        position: sticky;
        top: 0;
        z-index: 40;
        backdrop-filter: blur(18px);
        background: rgba(7, 11, 18, 0.54);
        border-bottom: 1px solid rgba(255,255,255,0.03);
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
        font-size: 1.5rem;
        font-weight: 800;
        letter-spacing: -0.05em;
      }
      .brand-mark {
        width: 32px;
        height: 32px;
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
        background: rgba(7, 11, 18, 0.88);
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
        background: rgba(148, 163, 184, 0.06);
        border: 1px solid var(--line);
      }
      .ham {
        display: none;
        width: 40px;
        height: 40px;
        border-radius: 12px;
        border: 1px solid var(--line);
        background: rgba(148, 163, 184, 0.06);
        align-items: center;
        justify-content:*

