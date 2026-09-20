# SRM Team ROBOCON Workshops: Website Source

A one-page, Batman-themed website announcing two workshops (**ShapeWaves** and **ReactBits**) conducted by SRM Team **ROBOCON** at TP Ganeshan Auditorium.

## How to use

1. Copy the code block below into a new file named `index.html`.
2. Open `index.html` in any browser. No build step or install is needed.
3. To host it, upload the file to any static host (GitHub Pages, Netlify, and so on).

## Things to update

- **Date and time:** search for `To be announced` (it appears in both workshop cards).
- **Workshop descriptions:** edit the `<p>` inside each `<article class="card">`.
- **Registration:** add a button linking to your form inside `<div class="cta">`.

## Full code (`index.html`)

````html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<meta name="color-scheme" content="dark">
<title>SRM Team ROBOCON Workshops: ShapeWaves and ReactBits</title>
<meta name="description" content="SRM Team ROBOCON is conducting two workshops, ShapeWaves and ReactBits, at TP Ganeshan Auditorium.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Big+Shoulders+Display:wght@700;900&family=Barlow:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --gotham: #0f1419;
    --asphalt: #171d24;
    --steel: #2a3440;
    --concrete: #9aa5b1;
    --bone: #eceae3;
    --signal: #f5c518;
    --signal-deep: #d9a808;

    --display: "Big Shoulders Display", Impact, "Arial Narrow Bold", "Arial Narrow", sans-serif;
    --body: "Barlow", "Segoe UI", system-ui, -apple-system, Roboto, Arial, sans-serif;

    box-sizing: border-box;
    padding-top: env(safe-area-inset-top, 0px);
    padding-bottom: env(safe-area-inset-bottom, 0px);
    color-scheme: dark;
  }
  html { scroll-padding-top: env(safe-area-inset-top, 0px); scroll-behavior: smooth; }
  *, *::before, *::after { box-sizing: inherit; }
  body {
    margin: 0;
    background: var(--gotham);
    color: var(--bone);
    font-family: var(--body);
    font-size: 1.0625rem;
    line-height: 1.6;
    -webkit-font-smoothing: antialiased;
  }
  a { color: inherit; }
  :focus-visible { outline: 3px solid var(--signal); outline-offset: 3px; }

  .wrap { width: 100%; max-width: 1100px; margin-inline: auto; padding-inline: 1.25rem; }

  /* The word the client wants bold, wherever it appears in running text */
  .rc {
    font-family: var(--display);
    font-weight: 900;
    letter-spacing: .04em;
    color: var(--signal);
    text-transform: uppercase;
  }

  /* ---------- Header ---------- */
  .site-header {
    position: sticky;
    top: env(safe-area-inset-top, 0px);
    z-index: 20;
    background: rgba(15, 20, 25, .88);
    -webkit-backdrop-filter: blur(8px);
    backdrop-filter: blur(8px);
    border-bottom: 1px solid var(--steel);
  }
  .site-header .wrap { display: flex; align-items: center; justify-content: space-between; min-height: 60px; gap: 1rem; }
  .brand { display: flex; align-items: center; gap: .6rem; text-decoration: none; font-family: var(--display); font-weight: 900; font-size: 1.35rem; letter-spacing: .03em; text-transform: uppercase; }
  .brand svg { width: 38px; height: auto; fill: var(--signal); }
  .brand .rc { letter-spacing: .03em; }
  .nav { display: flex; gap: 1.5rem; font-weight: 500; }
  .nav a { text-decoration: none; color: var(--concrete); padding: .25rem 0; border-bottom: 2px solid transparent; transition: color .15s, border-color .15s; }
  .nav a:hover { color: var(--bone); border-color: var(--signal); }
  @media (max-width: 560px) { .nav a.opt { display: none; } .nav { gap: 1rem; } }

  /* ---------- Hero ---------- */
  .hero {
    --sig: clamp(120px, 22vw, 240px);
    --sx: 5vw;
    --sy: 28px;
    position: relative;
    overflow: hidden;
    min-height: calc(100svh - 60px);
    min-height: max(560px, calc(100svh - 60px));
    display: flex;
    align-items: flex-end;
    background:
      radial-gradient(ellipse 60% 50% at calc(100% - var(--sx) - var(--sig) / 2) calc(var(--sy) + var(--sig) / 2), rgba(245, 197, 24, .10), transparent 70%),
      linear-gradient(180deg, #0c1116 0%, var(--gotham) 55%, #1a222b 100%);
  }
  .signal {
    position: absolute;
    top: var(--sy);
    right: var(--sx);
    width: var(--sig);
    height: var(--sig);
    border-radius: 50%;
    display: grid;
    place-items: center;
    background: radial-gradient(circle at 50% 42%, #fff7cf 0%, #f8d23a 46%, var(--signal-deep) 100%);
    box-shadow: 0 0 50px 14px rgba(245, 197, 24, .35), 0 0 150px 50px rgba(245, 197, 24, .16);
    z-index: 1;
    animation: ignite 1.5s ease-out both;
  }
  .signal svg { width: 64%; height: auto; fill: var(--gotham); }
  .beam {
    position: absolute;
    top: calc(var(--sy) + var(--sig) / 2);
    right: calc(var(--sx) + var(--sig) / 2);
    width: min(1100px, 150vw);
    height: min(88%, 860px);
    background: linear-gradient(to bottom left, rgba(245, 197, 24, .30), rgba(245, 197, 24, 0) 78%);
    clip-path: polygon(100% 0, 0 100%, 52% 100%);
    pointer-events: none;
    z-index: 0;
    animation: beam-on 1.4s ease-out .9s both;
  }
  @keyframes ignite {
    0% { opacity: 0; }
    12% { opacity: .9; }
    20% { opacity: .1; }
    34% { opacity: 1; }
    44% { opacity: .35; }
    60%, 100% { opacity: 1; }
  }
  @keyframes beam-on { from { opacity: 0; } to { opacity: 1; } }

  .skyline {
    position: absolute;
    left: 0; right: 0; bottom: 0;
    width: 100%;
    height: clamp(120px, 18vw, 230px);
    z-index: 2;
    display: block;
  }
  .hero-body {
    position: relative;
    z-index: 3;
    width: 100%;
    padding-top: 190px;
    padding-bottom: calc(clamp(120px, 18vw, 230px) + 2rem);
  }
  .hero h1 { margin: 0; line-height: .86; font-family: var(--display); text-transform: uppercase; }
  .hero h1 .pre {
    display: block;
    font-weight: 700;
    font-size: clamp(1.7rem, 5.2vw, 3.2rem);
    letter-spacing: .06em;
    color: var(--bone);
    margin-bottom: .2em;
  }
  .hero h1 .big {
    display: block;
    font-weight: 900;
    font-size: clamp(4.2rem, 22vw, 15rem);
    letter-spacing: .01em;
    color: var(--signal);
    text-shadow: 0 0 40px rgba(245, 197, 24, .28), 0 4px 0 #8a6a00;
  }
  .lede { max-width: 34rem; margin: 1.4rem 0 1.8rem; font-size: 1.2rem; color: #d9d7d0; }
  .lede b { color: var(--bone); font-weight: 600; }
  .cta { display: flex; flex-wrap: wrap; gap: .8rem; }
  .btn {
    display: inline-block;
    padding: .8rem 1.5rem;
    font: 600 1rem/1.2 var(--body);
    text-decoration: none;
    border: 2px solid var(--signal);
    transition: background .15s, color .15s;
  }
  .btn-solid { background: var(--signal); color: var(--gotham); }
  .btn-solid:hover { background: var(--bone); border-color: var(--bone); }
  .btn-line { color: var(--signal); background: transparent; }
  .btn-line:hover { background: var(--signal); color: var(--gotham); }

  /* ---------- Sections ---------- */
  section { padding: clamp(3.5rem, 8vw, 6rem) 0; }
  h2 {
    margin: 0 0 .6rem;
    font-family: var(--display);
    font-weight: 900;
    font-size: clamp(2.4rem, 7vw, 4.2rem);
    line-height: .95;
    text-transform: uppercase;
  }
  .section-note { max-width: 36rem; margin: 0 0 2.5rem; color: var(--concrete); font-size: 1.1rem; }

  .cards { display: grid; gap: 1.5rem; grid-template-columns: 1fr; }
  @media (min-width: 780px) { .cards { grid-template-columns: 1fr 1fr; } }
  .card {
    position: relative;
    background: var(--asphalt);
    padding: 2.25rem 1.75rem 1.75rem;
    clip-path: polygon(0 0, calc(100% - 28px) 0, 100% 28px, 100% 100%, 0 100%);
  }
  .card::before { content: ""; position: absolute; left: 0; top: 0; width: 100%; height: 5px; background: var(--signal); }
  .glyph { width: 60px; height: 60px; margin-bottom: 1rem; fill: none; stroke: var(--signal); stroke-width: 2.5; stroke-linecap: round; }
  .card h3 {
    margin: 0 0 .6rem;
    font-family: var(--display);
    font-weight: 900;
    font-size: clamp(2.2rem, 6vw, 3.2rem);
    line-height: 1;
    text-transform: uppercase;
  }
  .card p { margin: 0 0 1.5rem; color: #cfcdc6; max-width: 32rem; }
  .facts { margin: 0; display: grid; grid-template-columns: auto 1fr; column-gap: 1.25rem; }
  .facts dt, .facts dd { padding: .7rem 0; border-top: 1px solid var(--steel); margin: 0; }
  .facts dt { color: var(--concrete); }
  .facts dd { font-weight: 500; }

  /* Venue band */
  .venue { position: relative; overflow: hidden; background: var(--signal); color: var(--gotham); }
  .venue .mark { position: absolute; right: -40px; bottom: -50px; width: min(520px, 70vw); fill: rgba(15, 20, 25, .09); pointer-events: none; }
  .venue .wrap { position: relative; }
  .venue .kicker { margin: 0 0 .5rem; font-size: 1.15rem; font-weight: 600; }
  .venue h2 { font-size: clamp(3rem, 10.5vw, 8rem); line-height: .88; margin-bottom: 1.6rem; }
  .venue .btn { border-color: var(--gotham); color: var(--gotham); }
  .venue .btn:hover { background: var(--gotham); color: var(--signal); }

  /* ---------- Footer ---------- */
  footer { background: var(--asphalt); border-top: 1px solid var(--steel); padding: 3rem 0 2rem; }
  .foot-grid { display: grid; gap: 2rem; grid-template-columns: 1fr; }
  @media (min-width: 720px) { .foot-grid { grid-template-columns: 1fr 1.4fr; gap: 3rem; } }
  footer h3 { margin: 0 0 .7rem; font-family: var(--display); font-weight: 900; font-size: 1.8rem; text-transform: uppercase; }
  footer address { font-style: normal; color: #d9d7d0; line-height: 1.7; }
  footer address strong { color: var(--bone); font-weight: 600; }
  footer .maplink { display: inline-block; margin-top: 1rem; color: var(--signal); font-weight: 600; text-underline-offset: 4px; }
  footer .maplink:hover { color: var(--bone); }
  .brand-col p { margin: .7rem 0 0; color: var(--concrete); max-width: 22rem; }
  .brand-col .brand { font-size: 1.6rem; }
  .brand-col .brand svg { width: 52px; }
  .legal { margin-top: 2.5rem; padding-top: 1.2rem; border-top: 1px solid var(--steel); color: var(--concrete); font-size: .95rem; }

  @media (prefers-reduced-motion: reduce) {
    html { scroll-behavior: auto; }
    .signal, .beam { animation: none; }
  }
</style>
</head>
<body>

<!-- Reusable bat symbol -->
<svg width="0" height="0" style="position:absolute" aria-hidden="true" focusable="false">
  <symbol id="bat" viewBox="0 0 200 100">
    <path d="M100 16 C96 16 94 23 92 28 C88 25 84 21 79 21 C69 34 49 30 18 20 C29 33 27 48 34 58 C42 52 52 52 58 61 C66 54 76 56 82 69 C88 62 94 64 100 78 C106 64 112 62 118 69 C124 56 134 54 142 61 C148 52 158 52 166 58 C173 48 171 33 182 20 C151 30 131 34 121 21 C116 21 112 25 108 28 C106 23 104 16 100 16 Z"/>
  </symbol>
</svg>

<header class="site-header">
  <div class="wrap">
    <a class="brand" href="#top" aria-label="SRM Team ROBOCON home">
      <svg viewBox="0 0 200 100" aria-hidden="true"><use href="#bat"/></svg>
      <span>SRM Team <span class="rc">ROBOCON</span></span>
    </a>
    <nav class="nav" aria-label="Main">
      <a href="#workshops">Workshops</a>
      <a href="#venue">Venue</a>
      <a class="opt" href="#find-us">Find us</a>
    </nav>
  </div>
</header>

<main id="top">
  <div class="hero">
    <div class="beam" aria-hidden="true"></div>
    <div class="signal" aria-hidden="true">
      <svg viewBox="0 0 200 100"><use href="#bat"/></svg>
    </div>
    <svg class="skyline" id="skyline" viewBox="0 0 1440 240" preserveAspectRatio="xMidYMax slice" aria-hidden="true"></svg>

    <div class="wrap hero-body">
      <h1>
        <span class="pre">SRM Team</span>
        <span class="big">ROBOCON</span>
      </h1>
      <p class="lede">
        We are conducting two workshops, <b>ShapeWaves</b> and <b>ReactBits</b>, at <b>TP Ganeshan Auditorium</b>. Come build with us.
      </p>
      <div class="cta">
        <a class="btn btn-solid" href="#workshops">See the workshops</a>
        <a class="btn btn-line" href="#venue">Find the venue</a>
      </div>
    </div>
  </div>

  <section id="workshops">
    <div class="wrap">
      <h2>Two workshops</h2>
      <p class="section-note">Both sessions are conducted by SRM Team <strong class="rc">ROBOCON</strong> and held in the same auditorium.</p>

      <div class="cards">
        <article class="card">
          <svg class="glyph" viewBox="0 0 64 64" aria-hidden="true">
            <path d="M4 18 C14 6 22 6 32 18 S50 30 60 18"/>
            <path d="M4 34 C14 22 22 22 32 34 S50 46 60 34"/>
            <path d="M4 50 C14 38 22 38 32 50 S50 62 60 50"/>
          </svg>
          <h3>ShapeWaves</h3>
          <p>A hands-on workshop led by SRM Team <strong class="rc">ROBOCON</strong>. Bring your laptop and build along with the team.</p>
          <dl class="facts">
            <dt>Conducted by</dt><dd>SRM Team <span class="rc">ROBOCON</span></dd>
            <dt>Venue</dt><dd>TP Ganeshan Auditorium</dd>
            <dt>Date and time</dt><dd>To be announced</dd>
          </dl>
        </article>

        <article class="card">
          <svg class="glyph" viewBox="0 0 64 64" aria-hidden="true">
            <ellipse cx="32" cy="32" rx="28" ry="11"/>
            <ellipse cx="32" cy="32" rx="28" ry="11" transform="rotate(60 32 32)"/>
            <ellipse cx="32" cy="32" rx="28" ry="11" transform="rotate(120 32 32)"/>
            <circle cx="32" cy="32" r="3.5" fill="#f5c518" stroke="none"/>
          </svg>
          <h3>ReactBits</h3>
          <p>A hands-on workshop on animated React components, taught by SRM Team <strong class="rc">ROBOCON</strong>. Bring your laptop and build along with the team.</p>
          <dl class="facts">
            <dt>Conducted by</dt><dd>SRM Team <span class="rc">ROBOCON</span></dd>
            <dt>Venue</dt><dd>TP Ganeshan Auditorium</dd>
            <dt>Date and time</dt><dd>27 September 2026</dd>
          </dl>
        </article>
      </div>
    </div>
  </section>

  <section class="venue" id="venue">
    <svg class="mark" viewBox="0 0 200 100" aria-hidden="true"><use href="#bat"/></svg>
    <div class="wrap">
      <p class="kicker">Both workshops take place at</p>
      <h2>TP Ganeshan<br>Auditorium</h2>
      <a class="btn" href="https://www.google.com/maps/search/?api=1&amp;query=TP+Ganeshan+Auditorium+SRM+Kattankulathur" target="_blank" rel="noopener">Get directions</a>
    </div>
  </section>
</main>

<footer id="find-us">
  <div class="wrap">
    <div class="foot-grid">
      <div class="brand-col">
        <a class="brand" href="#top" aria-label="Back to top">
          <svg viewBox="0 0 200 100" aria-hidden="true"><use href="#bat"/></svg>
          <span>SRM Team <span class="rc">ROBOCON</span></span>
        </a>
        <p>Building robots and running workshops on the SRM campus.</p>
      </div>
      <div>
        <h3>Club location</h3>
        <address>
          <strong>SRM Team Robocon Lab</strong><br>
          Aarush building, Main campus<br>
          SRMIST, Kattankulathur<br>
          Chennai 603203
        </address>
        <a class="maplink" href="https://www.google.com/maps/search/?api=1&amp;query=SRM+Team+Robocon+Lab+Aarush+Building+SRMIST+Kattankulathur+Chennai+603203" target="_blank" rel="noopener">Open the lab in Maps</a>
      </div>
    </div>
    <div class="legal">&copy; 2026 SRM Team ROBOCON. All rights reserved.</div>
  </div>
</footer>

<script>
  // Gotham skyline: silhouette towers with a few lit windows (deterministic, so it looks the same every load)
  (function () {
    var svg = document.getElementById('skyline');
    if (!svg) return;
    var W = 1440, H = 240, x = 0, seed = 11, out = '';
    function rnd() { seed = (seed * 16807) % 2147483647; return (seed - 1) / 2147483646; }
    while (x < W) {
      var w = 34 + Math.floor(rnd() * 62);
      var h = 48 + Math.floor(rnd() * 170);
      out += '<rect x="' + x + '" y="' + (H - h) + '" width="' + (w - 2) + '" height="' + h + '" fill="#070a0e"/>';
      if (rnd() > 0.78) {
        out += '<rect x="' + (x + w / 2 - 3) + '" y="' + (H - h - 28) + '" width="4" height="28" fill="#070a0e"/>';
      }
      for (var wy = H - h + 12; wy < H - 10; wy += 14) {
        for (var wx = x + 7; wx < x + w - 12; wx += 11) {
          if (rnd() > 0.87) {
            out += '<rect x="' + wx + '" y="' + wy + '" width="4" height="6" fill="#f5c518" opacity="' + (0.45 + rnd() * 0.4).toFixed(2) + '"/>';
          }
        }
      }
      x += w;
    }
    svg.innerHTML = out;
  })();
</script>
</body>
</html>

````
