# heyman8018.github.io
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>台北家庭之旅 2026</title>
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --red: #D4364A;
    --red-dark: #b02a3b;
    --red-light: #fbe8ea;
    --green: #2e7d32;
    --green-bg: #e8f5e9;
    --green-border: #4caf50;
    --orange: #e65100;
    --orange-bg: #fff3e0;
    --orange-border: #ff9800;
    --yellow-bg: #fffde7;
    --yellow-border: #fbc02d;
    --gray-bg: #f5f5f5;
    --text: #1a1a1a;
    --text-light: #555;
    --radius: 12px;
    --shadow: 0 2px 8px rgba(0,0,0,0.1);
  }

  body {
    font-family: -apple-system, "PingFang TC", "Microsoft JhengHei", "微軟正黑體", sans-serif;
    font-size: 18px;
    color: var(--text);
    background: #f0f0f0;
    line-height: 1.6;
    -webkit-text-size-adjust: 100%;
  }

  /* ── HEADER ── */
  .header {
    background: linear-gradient(135deg, var(--red) 0%, #c0392b 100%);
    color: white;
    padding: 20px 16px 16px;
    text-align: center;
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 2px 12px rgba(0,0,0,0.25);
  }
  .header-flag { font-size: 28px; margin-bottom: 4px; }
  .header h1 {
    font-size: 22px;
    font-weight: 700;
    letter-spacing: 1px;
    line-height: 1.3;
  }
  .header-date {
    font-size: 15px;
    opacity: 0.9;
    margin-top: 4px;
  }

  /* ── TABS ── */
  .tabs {
    display: flex;
    background: white;
    border-bottom: 3px solid var(--red);
    position: sticky;
    top: 94px;
    z-index: 99;
    box-shadow: 0 2px 6px rgba(0,0,0,0.08);
  }
  .tab-btn {
    flex: 1;
    padding: 14px 8px;
    font-size: 17px;
    font-weight: 600;
    font-family: inherit;
    color: var(--text-light);
    background: white;
    border: none;
    cursor: pointer;
    transition: all 0.2s;
    border-bottom: 4px solid transparent;
    margin-bottom: -3px;
    line-height: 1.3;
    text-align: center;
  }
  .tab-btn .day-label { font-size: 13px; font-weight: 400; display: block; }
  .tab-btn.active {
    color: var(--red);
    border-bottom-color: var(--red);
    background: #fff5f6;
  }
  .tab-btn:active { background: var(--red-light); }

  /* ── PANELS ── */
  .panel { display: none; padding: 16px; padding-bottom: 32px; }
  .panel.active { display: block; }

  /* ── SUMMARY CARD ── */
  .summary-card {
    background: linear-gradient(135deg, var(--red) 0%, #c0392b 100%);
    color: white;
    border-radius: var(--radius);
    padding: 18px 16px;
    margin-bottom: 20px;
    box-shadow: var(--shadow);
  }
  .summary-card h2 {
    font-size: 20px;
    margin-bottom: 10px;
    border-bottom: 1px solid rgba(255,255,255,0.3);
    padding-bottom: 8px;
  }
  .summary-highlights {
    list-style: none;
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-top: 10px;
  }
  .summary-highlights li {
    background: rgba(255,255,255,0.2);
    border-radius: 20px;
    padding: 5px 12px;
    font-size: 15px;
    white-space: nowrap;
  }

  /* ── SECTION TITLE ── */
  .section-title {
    font-size: 16px;
    font-weight: 700;
    color: var(--text-light);
    text-transform: uppercase;
    letter-spacing: 1px;
    margin: 20px 0 10px;
    padding-left: 4px;
  }

  /* ── ACTIVITY CARD ── */
  .card {
    background: white;
    border-radius: var(--radius);
    padding: 16px;
    margin-bottom: 12px;
    box-shadow: var(--shadow);
    border-left: 5px solid #ddd;
    position: relative;
  }
  .card.confirmed {
    border-left-color: var(--green-border);
    background: #fdfffd;
  }
  .card.pending {
    border-left-color: var(--orange-border);
    background: #fffdf9;
  }
  .card.neutral {
    border-left-color: #bdbdbd;
  }

  .card-time {
    font-size: 15px;
    color: var(--text-light);
    font-weight: 600;
    margin-bottom: 4px;
    font-variant-numeric: tabular-nums;
  }
  .card-title {
    font-size: 19px;
    font-weight: 700;
    color: var(--text);
    margin-bottom: 6px;
    line-height: 1.4;
  }
  .card-note {
    font-size: 16px;
    color: var(--text-light);
    line-height: 1.5;
  }

  /* ── BADGES ── */
  .badge {
    display: inline-block;
    border-radius: 20px;
    padding: 3px 12px;
    font-size: 14px;
    font-weight: 700;
    margin-top: 8px;
  }
  .badge-confirmed {
    background: var(--green-bg);
    color: var(--green);
    border: 1px solid var(--green-border);
  }
  .badge-pending {
    background: var(--orange-bg);
    color: var(--orange);
    border: 1px solid var(--orange-border);
  }
  .badge-warning {
    background: #fff8e1;
    color: #e65100;
    border: 1px solid #ffcc02;
    font-size: 14px;
  }

  /* ── HERO CARTOON ── */
  .hero {
    background: white;
    overflow: hidden;
    line-height: 0;
  }
  .hero svg { width: 100%; display: block; }

  /* ── BACKUP ACTIVITIES ── */
  .backup-section {
    background: var(--yellow-bg);
    border: 2px dashed var(--yellow-border);
    border-radius: var(--radius);
    padding: 14px 16px;
    margin-bottom: 12px;
  }
  .backup-section-title {
    font-size: 15px;
    font-weight: 700;
    color: #795548;
    margin-bottom: 10px;
    display: flex;
    align-items: center;
    gap: 6px;
  }
  .backup-item {
    font-size: 17px;
    color: var(--text);
    padding: 8px 0;
    border-top: 1px solid rgba(0,0,0,0.08);
    line-height: 1.5;
  }
  .backup-item:first-of-type { border-top: none; }
  .backup-time {
    font-size: 14px;
    color: var(--text-light);
    font-weight: 600;
  }

  /* ── TIPS SECTION ── */
  .tips-section {
    background: white;
    border-radius: var(--radius);
    padding: 18px 16px;
    margin: 24px 0 0;
    box-shadow: var(--shadow);
    border-top: 4px solid #1976d2;
  }
  .tips-title {
    font-size: 19px;
    font-weight: 700;
    color: #1565c0;
    margin-bottom: 14px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .tip-item {
    display: flex;
    gap: 12px;
    margin-bottom: 12px;
    align-items: flex-start;
    font-size: 17px;
    line-height: 1.6;
  }
  .tip-icon { font-size: 22px; flex-shrink: 0; }
  .tip-text strong { display: block; color: var(--text); }
  .tip-text span { color: var(--text-light); font-size: 16px; }

  /* ── HOTEL LINK ── */
  .hotel-link {
    display: block;
    background: var(--red-light);
    border: 2px solid var(--red);
    border-radius: var(--radius);
    padding: 14px 16px;
    text-decoration: none;
    color: var(--red-dark);
    font-size: 17px;
    font-weight: 700;
    text-align: center;
    margin: 12px 0;
  }
  .hotel-link:active { background: var(--red); color: white; }

  /* ── FOOTER ── */
  .footer {
    background: #2c2c2c;
    color: #aaa;
    text-align: center;
    padding: 16px;
    font-size: 14px;
    margin-top: 24px;
  }
  .footer strong { color: white; }

  /* ── DIVIDER ── */
  .divider {
    display: flex;
    align-items: center;
    gap: 8px;
    margin: 16px 0 8px;
    color: var(--text-light);
    font-size: 14px;
    font-weight: 600;
  }
  .divider::before, .divider::after {
    content: '';
    flex: 1;
    height: 1px;
    background: #ddd;
  }
</style>
</head>
<body>

<!-- HEADER -->
<header class="header">
  <div class="header-flag">✈️ 🇹🇼</div>
  <h1>台北家庭之旅</h1>
  <div class="header-date">2026年 6月19日 — 21日</div>
</header>

<!-- CARTOON HERO BANNER -->
<div class="hero">
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 360 305">
<defs>
  <linearGradient id="skyG" x1="0" y1="0" x2="0" y2="1">
    <stop offset="0%" stop-color="#5BB8F5"/>
    <stop offset="60%" stop-color="#A8D8F0"/>
    <stop offset="100%" stop-color="#FFE4B5"/>
  </linearGradient>
  <linearGradient id="grassG" x1="0" y1="0" x2="0" y2="1">
    <stop offset="0%" stop-color="#8BC34A"/>
    <stop offset="100%" stop-color="#558B2F"/>
  </linearGradient>
  <clipPath id="bodyClip1"><rect x="-26" y="22" width="52" height="60" rx="14"/></clipPath>
  <clipPath id="bodyClip2"><rect x="-23" y="22" width="46" height="60" rx="13"/></clipPath>
  <clipPath id="bodyClip3"><rect x="-25" y="22" width="50" height="60" rx="14"/></clipPath>
  <clipPath id="bodyClip4"><rect x="-28" y="22" width="56" height="62" rx="15"/></clipPath>
</defs>

<!-- Sky -->
<rect width="360" height="305" fill="url(#skyG)"/>

<!-- Taipei 101 (background, right) -->
<g opacity="0.82">
  <rect x="295" y="128" width="46" height="130" fill="#4A6FA5" rx="2"/>
  <!-- Window rows -->
  <rect x="298" y="136" width="40" height="4" fill="#7BAED4" rx="1"/>
  <rect x="298" y="148" width="40" height="4" fill="#7BAED4" rx="1"/>
  <rect x="298" y="160" width="40" height="4" fill="#7BAED4" rx="1"/>
  <rect x="298" y="172" width="40" height="4" fill="#7BAED4" rx="1"/>
  <rect x="298" y="184" width="40" height="4" fill="#7BAED4" rx="1"/>
  <rect x="298" y="196" width="40" height="4" fill="#7BAED4" rx="1"/>
  <rect x="298" y="208" width="40" height="4" fill="#7BAED4" rx="1"/>
  <rect x="298" y="220" width="40" height="4" fill="#7BAED4" rx="1"/>
  <!-- Tiers -->
  <rect x="289" y="122" width="58" height="10" fill="#5A7EB5" rx="2"/>
  <rect x="293" y="112" width="50" height="12" fill="#5A7EB5" rx="2"/>
  <rect x="296" y="102" width="44" height="12" fill="#4A6FA5" rx="2"/>
  <rect x="299" y="92"  width="38" height="12" fill="#4A6FA5" rx="2"/>
  <rect x="302" y="83"  width="32" height="11" fill="#4A6FA5" rx="2"/>
  <rect x="305" y="75"  width="26" height="10" fill="#3D5A8A" rx="2"/>
  <rect x="308" y="67"  width="20" height="10" fill="#3D5A8A" rx="2"/>
  <rect x="311" y="60"  width="14" height="9"  fill="#3D5A8A" rx="2"/>
  <!-- Spire -->
  <rect x="316" y="20" width="4" height="42" fill="#2C4470" rx="2"/>
  <polygon points="318,13 314,22 322,22" fill="#D4364A"/>
  <circle cx="318" cy="13" r="3.5" fill="#FFD700"/>
</g>

<!-- Clouds -->
<ellipse cx="52"  cy="52" rx="34" ry="19" fill="white" opacity="0.93"/>
<ellipse cx="80"  cy="44" rx="28" ry="17" fill="white" opacity="0.93"/>
<ellipse cx="40"  cy="63" rx="22" ry="13" fill="white" opacity="0.85"/>
<ellipse cx="192" cy="36" rx="30" ry="17" fill="white" opacity="0.88"/>
<ellipse cx="220" cy="28" rx="24" ry="15" fill="white" opacity="0.88"/>
<ellipse cx="180" cy="46" rx="20" ry="12" fill="white" opacity="0.80"/>

<!-- Lantern string -->
<path d="M 8,4 Q 75,22 148,8 Q 218,24 270,6" stroke="#7B3F00" fill="none" stroke-width="1.5" opacity="0.65"/>
<!-- Lantern 1 -->
<g transform="translate(58,14)">
  <rect x="-10" y="-17" width="20" height="5" fill="#B71C1C" rx="2"/>
  <ellipse cx="0" cy="0" rx="11" ry="16" fill="#E53935"/>
  <ellipse cx="0" cy="0" rx="11" ry="5" fill="#B71C1C" opacity="0.55"/>
  <rect x="-10" y="14" width="20" height="5" fill="#B71C1C" rx="2"/>
  <line x1="-4" y1="19" x2="-6" y2="28" stroke="#E53935" stroke-width="1.5"/>
  <line x1="0"  y1="19" x2="0"  y2="29" stroke="#E53935" stroke-width="1.5"/>
  <line x1="4"  y1="19" x2="6"  y2="28" stroke="#E53935" stroke-width="1.5"/>
  <text x="0" y="5" text-anchor="middle" font-size="11" fill="#FFD700" font-family="serif">福</text>
</g>
<!-- Lantern 2 -->
<g transform="translate(148,18)">
  <rect x="-10" y="-17" width="20" height="5" fill="#B71C1C" rx="2"/>
  <ellipse cx="0" cy="0" rx="11" ry="16" fill="#E53935"/>
  <ellipse cx="0" cy="0" rx="11" ry="5" fill="#B71C1C" opacity="0.55"/>
  <rect x="-10" y="14" width="20" height="5" fill="#B71C1C" rx="2"/>
  <line x1="-4" y1="19" x2="-6" y2="28" stroke="#E53935" stroke-width="1.5"/>
  <line x1="0"  y1="19" x2="0"  y2="29" stroke="#E53935" stroke-width="1.5"/>
  <line x1="4"  y1="19" x2="6"  y2="28" stroke="#E53935" stroke-width="1.5"/>
  <text x="0" y="5" text-anchor="middle" font-size="11" fill="#FFD700" font-family="serif">樂</text>
</g>
<!-- Lantern 3 -->
<g transform="translate(240,16)">
  <rect x="-10" y="-17" width="20" height="5" fill="#B71C1C" rx="2"/>
  <ellipse cx="0" cy="0" rx="11" ry="16" fill="#E53935"/>
  <ellipse cx="0" cy="0" rx="11" ry="5" fill="#B71C1C" opacity="0.55"/>
  <rect x="-10" y="14" width="20" height="5" fill="#B71C1C" rx="2"/>
  <line x1="-4" y1="19" x2="-6" y2="28" stroke="#E53935" stroke-width="1.5"/>
  <line x1="0"  y1="19" x2="0"  y2="29" stroke="#E53935" stroke-width="1.5"/>
  <line x1="4"  y1="19" x2="6"  y2="28" stroke="#E53935" stroke-width="1.5"/>
  <text x="0" y="5" text-anchor="middle" font-size="11" fill="#FFD700" font-family="serif">遊</text>
</g>

<!-- Ground / Grass -->
<ellipse cx="180" cy="272" rx="195" ry="38" fill="url(#grassG)"/>
<!-- Stone path -->
<ellipse cx="178" cy="272" rx="135" ry="22" fill="#C8A875" opacity="0.75"/>
<!-- Path stones -->
<ellipse cx="100" cy="278" rx="22" ry="8"  fill="#B89660" opacity="0.5"/>
<ellipse cx="178" cy="282" rx="25" ry="9"  fill="#B89660" opacity="0.45"/>
<ellipse cx="255" cy="278" rx="20" ry="8"  fill="#B89660" opacity="0.5"/>

<!-- Plum blossoms (left tree area) -->
<g>
  <line x1="22" y1="220" x2="22" y2="170" stroke="#7B3F00" stroke-width="4"/>
  <line x1="22" y1="190" x2="5"  y2="165" stroke="#7B3F00" stroke-width="3"/>
  <line x1="22" y1="200" x2="42" y2="175" stroke="#7B3F00" stroke-width="3"/>
  <!-- Blossoms -->
  <g fill="#FF8A80">
    <circle cx="5"  cy="158" r="6"/><circle cx="0"  cy="152" r="5"/>
    <circle cx="10" cy="150" r="5"/><circle cx="15" cy="156" r="5"/><circle cx="7" cy="162" r="4"/>
    <circle cx="5"  cy="155" r="2.5" fill="#FFCC02"/>
  </g>
  <g fill="#FF8A80">
    <circle cx="42" cy="168" r="5"/><circle cx="36" cy="162" r="5"/>
    <circle cx="47" cy="162" r="5"/><circle cx="50" cy="169" r="4"/><circle cx="40" cy="173" r="4"/>
    <circle cx="43" cy="165" r="2.5" fill="#FFCC02"/>
  </g>
  <g fill="#FF8A80">
    <circle cx="22" cy="163" r="6"/><circle cx="15" cy="158" r="5"/>
    <circle cx="28" cy="157" r="5"/><circle cx="30" cy="165" r="4"/><circle cx="18" cy="167" r="4"/>
    <circle cx="22" cy="161" r="2.5" fill="#FFCC02"/>
  </g>
</g>

<!-- Taiwan mini-flag -->
<g transform="translate(4,225)">
  <line x1="0" y1="0" x2="0" y2="36" stroke="#7B3F00" stroke-width="2"/>
  <rect x="0" y="0" width="30" height="20" fill="#FE0000" rx="2"/>
  <rect x="0" y="0" width="15" height="10" fill="#000095" rx="1"/>
  <circle cx="7.5" cy="5" r="2.5" fill="white"/>
  <g stroke="white" stroke-width="0.8" opacity="0.9">
    <line x1="7.5" y1="1.5" x2="7.5" y2="3"/>
    <line x1="7.5" y1="7" x2="7.5" y2="8.5"/>
    <line x1="4"   y1="5"   x2="5.5" y2="5"/>
    <line x1="9.5" y1="5"   x2="11"  y2="5"/>
    <line x1="5"   y1="2.5" x2="6.1" y2="3.6"/>
    <line x1="8.9" y1="6.4" x2="10"  y2="7.5"/>
    <line x1="5"   y1="7.5" x2="6.1" y2="6.4"/>
    <line x1="8.9" y1="3.6" x2="10"  y2="2.5"/>
  </g>
</g>

<!-- Sparkles -->
<text x="110" y="125" font-size="16" opacity="0.8">✨</text>
<text x="200" y="110" font-size="13" opacity="0.7">⭐</text>
<text x="268" y="135" font-size="12" opacity="0.75">✨</text>

<!-- ══════════════════════════════════════ -->
<!-- CHARACTER 1 — 爸爸 (老先生, 藍夾克) -->
<!-- ══════════════════════════════════════ -->
<g transform="translate(64,155)">
  <ellipse cx="0" cy="114" rx="24" ry="7" fill="rgba(0,0,0,0.13)"/>
  <!-- Shoes -->
  <ellipse cx="-11" cy="110" rx="13" ry="6" fill="#263238"/>
  <ellipse cx="11"  cy="110" rx="13" ry="6" fill="#263238"/>
  <!-- Legs -->
  <rect x="-20" y="76" width="15" height="32" fill="#78909C" rx="7"/>
  <rect x="5"   y="76" width="15" height="32" fill="#78909C" rx="7"/>
  <!-- Body (blue jacket) — draw arms first (behind body) -->
  <rect x="-38" y="26" width="15" height="42" fill="#1E88E5" rx="7"/>
  <rect x="23"  y="26" width="15" height="42" fill="#1E88E5" rx="7"/>
  <ellipse cx="-31" cy="69" rx="9" ry="8" fill="#F5CBA7"/>
  <ellipse cx="31"  cy="69" rx="9" ry="8" fill="#F5CBA7"/>
  <!-- Body -->
  <rect x="-26" y="22" width="52" height="60" fill="#1E88E5" rx="14"/>
  <!-- Lapels -->
  <polygon points="0,22 -12,40 0,35"  fill="#1565C0"/>
  <polygon points="0,22  12,40 0,35"  fill="#1565C0"/>
  <!-- Shirt -->
  <rect x="-9" y="22" width="18" height="18" fill="#ECEFF1" rx="3"/>
  <!-- Head -->
  <circle cx="0" cy="0" r="27" fill="#F5CBA7"/>
  <!-- Gray hair -->
  <path d="M -23,-18 Q 0,-32 23,-18 Q 25,-8 23,8 Q 8,-4 0,-2 Q -8,-4 -23,8 Q -25,-8 -23,-18Z" fill="#9E9E9E"/>
  <rect x="-25" y="-18" width="6" height="24" fill="#9E9E9E" rx="3"/>
  <rect x="19"  y="-18" width="6" height="24" fill="#9E9E9E" rx="3"/>
  <!-- Ears -->
  <ellipse cx="-27" cy="2" rx="5" ry="7" fill="#F5CBA7"/>
  <ellipse cx="27"  cy="2" rx="5" ry="7" fill="#F5CBA7"/>
  <!-- Eyes -->
  <ellipse cx="-10" cy="-1" rx="5.5" ry="6" fill="white"/>
  <ellipse cx="10"  cy="-1" rx="5.5" ry="6" fill="white"/>
  <circle  cx="-10" cy="-1" r="3.2" fill="#3E2723"/>
  <circle  cx="10"  cy="-1" r="3.2" fill="#3E2723"/>
  <circle  cx="-8.5" cy="-2.5" r="1.1" fill="white"/>
  <circle  cx="11.5" cy="-2.5" r="1.1" fill="white"/>
  <!-- Eyebrows (gray/bushy) -->
  <path d="M -15,-9 Q -10,-14 -4,-9" stroke="#757575" fill="none" stroke-width="3"/>
  <path d="M 4,-9  Q  10,-14 15,-9"  stroke="#757575" fill="none" stroke-width="3"/>
  <!-- Wrinkle lines -->
  <path d="M -8,-6 Q -5,-8 -2,-6" stroke="#E0A07A" fill="none" stroke-width="1"/>
  <path d="M 2,-6  Q 5,-8  8,-6"  stroke="#E0A07A" fill="none" stroke-width="1"/>
  <!-- Nose -->
  <ellipse cx="0" cy="7" rx="4.5" ry="3.5" fill="#E8A87C"/>
  <!-- Gentle smile -->
  <path d="M -10,15 Q 0,22 10,15" stroke="#C07050" fill="none" stroke-width="2.5"/>
  <!-- Cheeks -->
  <ellipse cx="-18" cy="9" rx="6" ry="4" fill="#FFAB91" opacity="0.4"/>
  <ellipse cx="18"  cy="9" rx="6" ry="4" fill="#FFAB91" opacity="0.4"/>
  <!-- Name label -->
  <rect x="-14" y="117" width="28" height="14" fill="#1E88E5" rx="7"/>
  <text x="0" y="128" text-anchor="middle" font-size="9" fill="white" font-family="PingFang TC,Microsoft JhengHei,sans-serif" font-weight="bold">爸爸</text>
</g>

<!-- ══════════════════════════════════════ -->
<!-- CHARACTER 2 — 姐姐/妹妹 (眼鏡, 比耶) -->
<!-- ══════════════════════════════════════ -->
<g transform="translate(140,155)">
  <ellipse cx="0" cy="114" rx="22" ry="6" fill="rgba(0,0,0,0.13)"/>
  <!-- Shoes -->
  <ellipse cx="-10" cy="110" rx="12" ry="5" fill="#37474F"/>
  <ellipse cx="10"  cy="110" rx="12" ry="5" fill="#37474F"/>
  <!-- Legs -->
  <rect x="-18" y="76" width="13" height="32" fill="#455A64" rx="6"/>
  <rect x="5"   y="76" width="13" height="32" fill="#455A64" rx="6"/>
  <!-- Left arm (down) -->
  <rect x="-34" y="26" width="13" height="40" fill="#ECEFF1" rx="6"/>
  <rect x="-34" y="32" width="13" height="7"  fill="#37474F"/>
  <rect x="-34" y="46" width="13" height="7"  fill="#37474F"/>
  <ellipse cx="-28" cy="68" rx="8" ry="7" fill="#F5CBA7"/>
  <!-- Body -->
  <rect x="-23" y="22" width="46" height="60" fill="#ECEFF1" rx="13"/>
  <!-- Stripes -->
  <rect x="-23" y="29" width="46" height="8"  fill="#37474F" clip-path="url(#bodyClip2)"/>
  <rect x="-23" y="44" width="46" height="8"  fill="#37474F" clip-path="url(#bodyClip2)"/>
  <rect x="-23" y="59" width="46" height="8"  fill="#37474F" clip-path="url(#bodyClip2)"/>
  <rect x="-23" y="74" width="46" height="10" fill="#37474F" clip-path="url(#bodyClip2)"/>
  <!-- Right arm raised (peace sign) -->
  <g transform="translate(26,-5) rotate(-25)">
    <rect x="-6" y="0" width="13" height="32" fill="#ECEFF1" rx="6"/>
    <rect x="-6" y="5"  width="13" height="8" fill="#37474F"/>
    <rect x="-6" y="20" width="13" height="7" fill="#37474F"/>
    <!-- hand base -->
    <ellipse cx="0" cy="-3" rx="9" ry="9" fill="#F5CBA7"/>
    <!-- Index finger -->
    <rect x="-6" y="-18" width="6" height="18" fill="#F5CBA7" rx="3"/>
    <!-- Middle finger -->
    <rect x="0"  y="-19" width="6" height="19" fill="#F5CBA7" rx="3"/>
    <!-- Knuckles (ring+pinky folded) -->
    <rect x="-8" y="-3" width="6" height="9" fill="#F5CBA7" rx="3"/>
    <rect x="6"  y="-3" width="6" height="9" fill="#F5CBA7" rx="3"/>
  </g>
  <!-- Head -->
  <circle cx="0" cy="0" r="25" fill="#F5CBA7"/>
  <!-- Black bob hair (back) -->
  <rect x="-26" y="-16" width="7" height="30" fill="#1A1A2E" rx="4"/>
  <rect x="19"  y="-16" width="7" height="28" fill="#1A1A2E" rx="4"/>
  <!-- Hair top -->
  <path d="M -22,-17 Q 0,-31 22,-17 Q 24,-7 22,6 Q 10,-6 0,-4 Q -10,-6 -22,6 Q -24,-7 -22,-17Z" fill="#1A1A2E"/>
  <!-- Ears -->
  <ellipse cx="-25" cy="2" rx="4" ry="6" fill="#F5CBA7"/>
  <ellipse cx="25"  cy="2" rx="4" ry="6" fill="#F5CBA7"/>
  <!-- Glasses -->
  <rect x="-20" y="-8" width="16" height="12" fill="none" stroke="#424242" stroke-width="2.5" rx="4"/>
  <rect x="4"   y="-8" width="16" height="12" fill="none" stroke="#424242" stroke-width="2.5" rx="4"/>
  <line x1="-4" y1="-2" x2="4"   y2="-2" stroke="#424242" stroke-width="2"/>
  <line x1="-20" y1="-2" x2="-25" y2="-2" stroke="#424242" stroke-width="2"/>
  <line x1="20"  y1="-2" x2="25"  y2="-2" stroke="#424242" stroke-width="2"/>
  <!-- Eyes -->
  <circle cx="-12" cy="-2" r="3.2" fill="#3E2723"/>
  <circle cx="12"  cy="-2" r="3.2" fill="#3E2723"/>
  <circle cx="-10.5" cy="-3.5" r="1.1" fill="white"/>
  <circle cx="13.5"  cy="-3.5" r="1.1" fill="white"/>
  <!-- Eyebrows -->
  <path d="M -18,-11 Q -12,-15 -6,-11" stroke="#1A1A2E" fill="none" stroke-width="2"/>
  <path d="M 6,-11   Q 12,-15 18,-11" stroke="#1A1A2E" fill="none" stroke-width="2"/>
  <!-- Nose -->
  <ellipse cx="0" cy="7" rx="3.5" ry="2.8" fill="#E8A87C"/>
  <!-- Smile -->
  <path d="M -8,13 Q 0,20 8,13" stroke="#C07050" fill="none" stroke-width="2.5"/>
  <!-- Cheeks -->
  <ellipse cx="-17" cy="9" rx="6" ry="4" fill="#FFB3B3" opacity="0.55"/>
  <ellipse cx="17"  cy="9" rx="6" ry="4" fill="#FFB3B3" opacity="0.55"/>
  <!-- Name label -->
  <rect x="-14" y="117" width="28" height="14" fill="#37474F" rx="7"/>
  <text x="0" y="128" text-anchor="middle" font-size="9" fill="white" font-family="PingFang TC,Microsoft JhengHei,sans-serif" font-weight="bold">姐姐</text>
</g>

<!-- ══════════════════════════════════════ -->
<!-- CHARACTER 3 — 媽媽 (紅夾克, 背包)   -->
<!-- ══════════════════════════════════════ -->
<g transform="translate(216,155)">
  <ellipse cx="0" cy="114" rx="23" ry="7" fill="rgba(0,0,0,0.13)"/>
  <!-- Backpack (green, behind body) -->
  <rect x="14" y="16" width="24" height="42" fill="#388E3C" rx="9"/>
  <rect x="17" y="21" width="6"  height="22" fill="#2E7D32" rx="3"/>
  <rect x="25" y="21" width="6"  height="22" fill="#2E7D32" rx="3"/>
  <rect x="17" y="44" width="14" height="8"  fill="#1B5E20" rx="3"/>
  <!-- Shoes (lavender) -->
  <ellipse cx="-11" cy="110" rx="13" ry="6" fill="#9575CD"/>
  <ellipse cx="11"  cy="110" rx="13" ry="6" fill="#9575CD"/>
  <!-- Legs -->
  <rect x="-19" y="76" width="14" height="32" fill="#455A64" rx="7"/>
  <rect x="5"   y="76" width="14" height="32" fill="#455A64" rx="7"/>
  <!-- Arms (red jacket) -->
  <rect x="-36" y="26" width="13" height="42" fill="#E53935" rx="6"/>
  <ellipse cx="-30" cy="70" rx="9" ry="8" fill="#F5CBA7"/>
  <rect x="23"  y="26" width="13" height="42" fill="#E53935" rx="6"/>
  <ellipse cx="29" cy="70" rx="9" ry="8" fill="#F5CBA7"/>
  <!-- Body (red jacket) -->
  <rect x="-25" y="22" width="50" height="60" fill="#E53935" rx="14"/>
  <!-- Purple collar/vest -->
  <rect x="-10" y="22" width="20" height="20" fill="#7B1FA2" rx="4"/>
  <!-- Lapels -->
  <polygon points="0,22 -12,42 0,36" fill="#C62828"/>
  <polygon points="0,22  12,42 0,36" fill="#C62828"/>
  <!-- Head -->
  <circle cx="0" cy="0" r="26" fill="#F5CBA7"/>
  <!-- Short gray hair -->
  <path d="M -23,-17 Q 0,-30 23,-17 Q 25,-7 23,9 Q 10,-3 0,-1 Q -10,-3 -23,9 Q -25,-7 -23,-17Z" fill="#BDBDBD"/>
  <rect x="-25" y="-17" width="7" height="24" fill="#BDBDBD" rx="3"/>
  <rect x="18"  y="-17" width="7" height="24" fill="#BDBDBD" rx="3"/>
  <!-- Ears -->
  <ellipse cx="-26" cy="2" rx="5" ry="7" fill="#F5CBA7"/>
  <ellipse cx="26"  cy="2" rx="5" ry="7" fill="#F5CBA7"/>
  <!-- Eyes -->
  <ellipse cx="-10" cy="-1" rx="5" ry="6" fill="white"/>
  <ellipse cx="10"  cy="-1" rx="5" ry="6" fill="white"/>
  <circle  cx="-10" cy="-1" r="3" fill="#3E2723"/>
  <circle  cx="10"  cy="-1" r="3" fill="#3E2723"/>
  <circle  cx="-8.5" cy="-2.5" r="1" fill="white"/>
  <circle  cx="11.5" cy="-2.5" r="1" fill="white"/>
  <!-- Eyebrows (gray) -->
  <path d="M -15,-8 Q -10,-13 -5,-8" stroke="#9E9E9E" fill="none" stroke-width="2.5"/>
  <path d="M 5,-8   Q 10,-13 15,-8"  stroke="#9E9E9E" fill="none" stroke-width="2.5"/>
  <!-- Wrinkles -->
  <path d="M -7,-5 Q -5,-7 -3,-5" stroke="#E0A07A" fill="none" stroke-width="1"/>
  <path d="M 3,-5  Q 5,-7  7,-5"  stroke="#E0A07A" fill="none" stroke-width="1"/>
  <!-- Nose -->
  <ellipse cx="0" cy="7" rx="4.5" ry="3.5" fill="#E8A87C"/>
  <!-- Warm smile -->
  <path d="M -10,14 Q 0,22 10,14" stroke="#C07050" fill="none" stroke-width="2.5"/>
  <!-- Cheeks -->
  <ellipse cx="-18" cy="8" rx="7" ry="4" fill="#FFAB91" opacity="0.45"/>
  <ellipse cx="18"  cy="8" rx="7" ry="4" fill="#FFAB91" opacity="0.45"/>
  <!-- Name label -->
  <rect x="-14" y="117" width="28" height="14" fill="#E53935" rx="7"/>
  <text x="0" y="128" text-anchor="middle" font-size="9" fill="white" font-family="PingFang TC,Microsoft JhengHei,sans-serif" font-weight="bold">媽媽</text>
</g>

<!-- ══════════════════════════════════════ -->
<!-- CHARACTER 4 — 女兒 (長髮, 自拍)      -->
<!-- (in front: larger, translated forward) -->
<!-- ══════════════════════════════════════ -->
<g transform="translate(291,160)">
  <ellipse cx="0" cy="122" rx="30" ry="9" fill="rgba(0,0,0,0.16)"/>
  <!-- Shoes -->
  <ellipse cx="-13" cy="118" rx="15" ry="7" fill="#263238"/>
  <ellipse cx="13"  cy="118" rx="15" ry="7" fill="#263238"/>
  <!-- Legs -->
  <rect x="-22" y="80" width="17" height="36" fill="#37474F" rx="8"/>
  <rect x="5"   y="80" width="17" height="36" fill="#37474F" rx="8"/>
  <!-- Left arm (down, natural) -->
  <rect x="-42" y="28" width="16" height="48" fill="#ECEFF1" rx="8"/>
  <rect x="-42" y="35" width="16" height="9"  fill="#37474F"/>
  <rect x="-42" y="51" width="16" height="9"  fill="#37474F"/>
  <rect x="-42" y="67" width="16" height="9"  fill="#37474F"/>
  <ellipse cx="-34" cy="78" rx="10" ry="9" fill="#F5CBA7"/>
  <!-- Body (black/white stripe, slightly wider since in front) -->
  <rect x="-28" y="22" width="56" height="64" fill="#FAFAFA" rx="15"/>
  <!-- Stripes -->
  <rect x="-28" y="29" width="56" height="8"  fill="#212121" clip-path="url(#bodyClip4)"/>
  <rect x="-28" y="44" width="56" height="8"  fill="#212121" clip-path="url(#bodyClip4)"/>
  <rect x="-28" y="59" width="56" height="8"  fill="#212121" clip-path="url(#bodyClip4)"/>
  <rect x="-28" y="74" width="56" height="12" fill="#212121" clip-path="url(#bodyClip4)"/>
  <!-- Right arm raised (holding phone selfie-style) -->
  <g transform="translate(34,10) rotate(-30)">
    <rect x="-7" y="0" width="15" height="36" fill="#FAFAFA" rx="7"/>
    <rect x="-7" y="6"  width="15" height="8" fill="#212121"/>
    <rect x="-7" y="21" width="15" height="8" fill="#212121"/>
    <!-- Hand -->
    <ellipse cx="0.5" cy="-4" rx="11" ry="10" fill="#F5CBA7"/>
    <!-- Phone body -->
    <rect x="-10" y="-30" width="22" height="30" fill="#1A1A2E" rx="5"/>
    <rect x="-8"  y="-28" width="18" height="22" fill="#42A5F5" rx="3"/>
    <!-- Phone selfie camera flash -->
    <circle cx="1" cy="-8" r="4" fill="white" opacity="0.85"/>
    <circle cx="8" cy="-27" r="2" fill="#555"/>
    <!-- Flash sparkle -->
    <text x="-4" y="-32" font-size="9" fill="#FFD700">✦</text>
  </g>
  <!-- Head (bigger, in front) -->
  <circle cx="0" cy="0" r="32" fill="#F5CBA7"/>
  <!-- Long brown hair (back layers) -->
  <rect x="-33" y="-22" width="10" height="75" fill="#5D3317" rx="5"/>
  <rect x="23"  y="-22" width="10" height="68" fill="#5D3317" rx="5"/>
  <!-- Hair top -->
  <path d="M -26,-21 Q 0,-38 26,-21 Q 30,-10 27,8 Q 12,-8 0,-6 Q -12,-8 -27,8 Q -30,-10 -26,-21Z" fill="#6D3B1E"/>
  <!-- Hair front layers -->
  <rect x="-33" y="-21" width="10" height="68" fill="#6D3B1E" rx="5"/>
  <rect x="23"  y="-21" width="10" height="62" fill="#6D3B1E" rx="5"/>
  <!-- Hair highlight -->
  <path d="M -5,-36 Q 8,-40 20,-30" stroke="#8B5E3C" fill="none" stroke-width="3.5" opacity="0.55"/>
  <!-- Ears -->
  <ellipse cx="-32" cy="3" rx="5.5" ry="8" fill="#F5CBA7"/>
  <ellipse cx="32"  cy="3" rx="5.5" ry="8" fill="#F5CBA7"/>
  <!-- BIG happy eyes -->
  <ellipse cx="-12" cy="-2" rx="7" ry="8" fill="white"/>
  <ellipse cx="12"  cy="-2" rx="7" ry="8" fill="white"/>
  <circle  cx="-12" cy="-2" r="5"  fill="#3E2723"/>
  <circle  cx="12"  cy="-2" r="5"  fill="#3E2723"/>
  <!-- Eye shine -->
  <circle cx="-10" cy="-4" r="1.8" fill="white"/>
  <circle cx="14"  cy="-4" r="1.8" fill="white"/>
  <circle cx="-13" cy="-3" r="0.9" fill="white"/>
  <circle cx="11"  cy="-3" r="0.9" fill="white"/>
  <!-- Eyebrows -->
  <path d="M -19,-13 Q -12,-19 -5,-13" stroke="#5D3317" fill="none" stroke-width="3"/>
  <path d="M 5,-13   Q 12,-19 19,-13" stroke="#5D3317" fill="none" stroke-width="3"/>
  <!-- Nose -->
  <ellipse cx="0" cy="9" rx="5.5" ry="4.5" fill="#E8A87C"/>
  <!-- Big joyful smile -->
  <path d="M -15,17 Q 0,30 15,17" stroke="#C07050" fill="#FFAB91" stroke-width="2.5"/>
  <!-- Teeth -->
  <path d="M -12,18 Q 0,27 12,18" fill="white"/>
  <!-- Blush cheeks -->
  <ellipse cx="-22" cy="9"  rx="9" ry="6" fill="#FFB3B3" opacity="0.6"/>
  <ellipse cx="22"  cy="9"  rx="9" ry="6" fill="#FFB3B3" opacity="0.6"/>
  <!-- Dimples -->
  <circle cx="-20" cy="14" r="2.5" fill="#E8A87C" opacity="0.45"/>
  <circle cx="20"  cy="14" r="2.5" fill="#E8A87C" opacity="0.45"/>
  <!-- Name label -->
  <rect x="-14" y="126" width="28" height="14" fill="#D4364A" rx="7"/>
  <text x="0" y="137" text-anchor="middle" font-size="9" fill="white" font-family="PingFang TC,Microsoft JhengHei,sans-serif" font-weight="bold">自拍✌️</text>
</g>

<!-- Bottom banner -->
<rect x="30" y="284" width="300" height="18" fill="rgba(212,54,74,0.88)" rx="9"/>
<text x="180" y="296.5" text-anchor="middle" font-family="PingFang TC,Microsoft JhengHei,sans-serif" font-size="12" fill="white" font-weight="bold">🇹🇼 台北家庭之旅 2026 · 三天兩夜 🇹🇼</text>
</svg>
</div>

<!-- TABS -->
<nav class="tabs">
  <button class="tab-btn active" onclick="switchTab(1)">
    Day 1
    <span class="day-label">6月19日</span>
  </button>
  <button class="tab-btn" onclick="switchTab(2)">
    Day 2
    <span class="day-label">6月20日</span>
  </button>
  <button class="tab-btn" onclick="switchTab(3)">
    Day 3
    <span class="day-label">6月21日</span>
  </button>
</nav>

<!-- ═══════════════ DAY 1 ═══════════════ -->
<div class="panel active" id="panel-1">

  <div class="summary-card">
    <h2>🗓️ 6月19日（星期五）香港 → 台北</h2>
    <ul class="summary-highlights">
      <li>✈️ CX450 抵台</li>
      <li>🍲 無老鍋午餐</li>
      <li>🏨 晶華酒店</li>
      <li>🛍️ 中山商圈</li>
      <li>🍖 古北饕晚餐</li>
      <li>🦶 不老松按摩</li>
    </ul>
  </div>

  <div class="section-title">行程安排</div>

  <div class="card neutral">
    <div class="card-time">09:55 — 11:45</div>
    <div class="card-title">✈️ 班機 CX450 抵達台北</div>
    <div class="card-note">香港出發 → 桃園國際機場</div>
  </div>

  <div class="card neutral">
    <div class="card-time">11:45 — 13:30</div>
    <div class="card-title">🛃 入境 + 前往市區</div>
    <div class="card-note">辦理入境手續，乘機場捷運或計程車前往酒店</div>
  </div>

  <div class="card confirmed">
    <div class="card-time">13:30 — 15:00</div>
    <div class="card-title">🍲 午餐：無老鍋</div>
    <div class="card-note">台北知名麻辣鍋，享用豐盛午餐</div>
    <span class="badge badge-confirmed">✅ 已訂妥</span>
  </div>

  <div class="card confirmed">
    <div class="card-time">15:00</div>
    <div class="card-title">🏨 Check-in 台北晶華酒店</div>
    <div class="card-note">辦理入住手續，放置行李，稍作休息</div>
    <span class="badge badge-confirmed">✅ 已確認</span>
    <a class="hotel-link" href="https://www.regenttaiwan.com/" target="_blank">🔗 台北晶華酒店官網</a>
  </div>

  <div class="card neutral">
    <div class="card-time">15:30 — 17:00</div>
    <div class="card-title">🛍️ 中山商圈購物</div>
    <div class="card-note">新光三越 · 誠品生活 · 地下街漫步</div>
  </div>

  <div class="divider">備選活動</div>
  <div class="backup-section">
    <div class="backup-section-title">🌟 備選：寧夏夜市</div>
    <div class="backup-item">
      <div class="backup-time">17:00 出發（約 17:30 抵達）</div>
      <div>人流較少，適合早去</div>
    </div>
  </div>

  <div class="card confirmed">
    <div class="card-time">18:00 — 20:00</div>
    <div class="card-title">🍖 晚餐：古北饕旗艦店</div>
    <div class="card-note">訂座時間：18:00</div>
    <span class="badge badge-confirmed">✅ 已訂妥 18:00</span>
  </div>

  <div class="card confirmed">
    <div class="card-time">20:00 — 21:00</div>
    <div class="card-title">🦶 按摩：不老松足湯</div>
    <div class="card-note">放鬆雙腳，舒緩一天旅途疲勞</div>
    <span class="badge badge-confirmed">✅ Line 已確認</span>
  </div>

</div>

<!-- ═══════════════ DAY 2 ═══════════════ -->
<div class="panel" id="panel-2">

  <div class="summary-card">
    <h2>🗓️ 6月20日（星期六）台北101 + 信義區</h2>
    <ul class="summary-highlights">
      <li>🏙️ 台北101</li>
      <li>🍽️ 信義午餐</li>
      <li>🛍️ 信義百貨</li>
      <li>🔥 炭夕晚餐</li>
    </ul>
  </div>

  <div class="section-title">行程安排</div>

  <div class="card neutral">
    <div class="card-time">08:30 — 09:30</div>
    <div class="card-title">🍳 酒店內早餐</div>
    <div class="card-note">享用晶華酒店早餐，悠閒開始新的一天</div>
  </div>

  <div class="card neutral">
    <div class="card-time">09:30 — 10:30</div>
    <div class="card-title">🛋️ 酒店休息</div>
    <div class="card-note">休息放鬆，準備出發</div>
  </div>

  <div class="card neutral">
    <div class="card-time">10:30 — 11:00</div>
    <div class="card-title">🚗 出發去台北101</div>
    <div class="card-note">乘計程車或捷運前往信義區</div>
  </div>

  <div class="card neutral">
    <div class="card-time">11:00 — 13:00</div>
    <div class="card-title">🏙️ 台北101 觀光 + 信義區散步</div>
    <div class="card-note">登上觀景台，俯瞰台北全景，信義區漫步</div>
  </div>

  <div class="card pending">
    <div class="card-time">13:00 — 14:30</div>
    <div class="card-title">🍽️ 午餐：信義區美食</div>
    <div class="card-note">信義區附近選擇豐富，可按當日喜好決定</div>
    <span class="badge badge-pending">⚠️ 待訂位</span>
  </div>

  <div class="card neutral">
    <div class="card-time">14:30 — 16:30</div>
    <div class="card-title">🛍️ 信義區百貨繼續逛</div>
    <div class="card-note">台北101商場 · 新光三越信義 · ATT 4 FUN</div>
  </div>

  <div class="divider">備選活動</div>
  <div class="backup-section">
    <div class="backup-section-title">🌟 備選：饒河街夜市</div>
    <div class="backup-item">
      <div class="backup-time">16:30 出發（約 17:30 抵達）</div>
      <div>人流較少，適合早去品嚐小食</div>
    </div>
  </div>

  <div class="card neutral">
    <div class="card-time">17:00 — 17:45</div>
    <div class="card-title">🏨 酒店休息</div>
    <div class="card-note">回酒店休息，換衣準備晚餐</div>
  </div>

  <div class="card confirmed">
    <div class="card-time">18:15 — 20:30</div>
    <div class="card-title">🔥 晚餐：炭夕 炭火小料理</div>
    <div class="card-note">訂座時間：18:30 · 精緻炭火料理</div>
    <span class="badge badge-confirmed">✅ 已訂妥 18:30</span>
  </div>

  <div class="card neutral">
    <div class="card-time">20:30</div>
    <div class="card-title">🌙 回酒店休息</div>
    <div class="card-note">明天早上需退房，好好休息</div>
  </div>

</div>

<!-- ═══════════════ DAY 3 ═══════════════ -->
<div class="panel" id="panel-3">

  <div class="summary-card">
    <h2>🗓️ 6月21日（星期日）台北 → 香港</h2>
    <ul class="summary-highlights">
      <li>🧳 退房</li>
      <li>☕ Simple Kaffa</li>
      <li>🦶 不老松按摩</li>
      <li>✈️ CX479 返港</li>
    </ul>
  </div>

  <div class="section-title">行程安排</div>

  <div class="card neutral">
    <div class="card-time">08:30 — 09:30</div>
    <div class="card-title">🍳 酒店內早餐</div>
    <div class="card-note">最後一次享用晶華酒店早餐</div>
  </div>

  <div class="card neutral">
    <div class="card-time">09:30 — 10:30</div>
    <div class="card-title">🚶 逛逛酒店附近</div>
    <div class="card-note">輕鬆逛逛中山區，購買手信</div>
  </div>

  <div class="card neutral">
    <div class="card-time">10:30 — 11:00</div>
    <div class="card-title">🧳 Check-out 結帳退房</div>
    <div class="card-note">辦理退房手續，寄存行李</div>
  </div>

  <div class="card pending">
    <div class="card-time">11:00 — 12:00</div>
    <div class="card-title">☕ Simple Kaffa Sola 天空興波</div>
    <div class="card-note">台北知名精品咖啡店，享用咖啡輕食</div>
    <span class="badge badge-pending">⚠️ 待訂位</span>
    <div style="margin-top:10px;">
      <span class="badge badge-warning">⚠️ 注意：前一天 12:00 後取消收 $250／人</span>
    </div>
  </div>

  <div class="card neutral">
    <div class="card-time">12:00 — 14:00</div>
    <div class="card-title">🍽️ 午餐：TBC</div>
    <div class="card-note">待定，可視當日情況選擇</div>
  </div>

  <div class="card confirmed">
    <div class="card-time">16:00 — 17:00</div>
    <div class="card-title">🦶 按摩：不老松足湯</div>
    <div class="card-note">出發前最後放鬆，舒緩雙腳</div>
    <span class="badge badge-confirmed">✅ Line 已確認</span>
  </div>

  <div class="card neutral">
    <div class="card-time">17:00 — 18:00</div>
    <div class="card-title">🚉 逛逛台北車站</div>
    <div class="card-note">台北車站地下街，最後購物機會</div>
  </div>

  <div class="card neutral">
    <div class="card-time">18:30</div>
    <div class="card-title">🚌 出發前往機場</div>
    <div class="card-note">乘機場捷運前往桃園機場，預留充足時間</div>
  </div>

  <div class="card neutral">
    <div class="card-time">19:00 — 20:30</div>
    <div class="card-title">🛍️ 逛免稅店 + 小王煮瓜</div>
    <div class="card-note">機場免稅購物，品嚐台灣名物小王煮瓜</div>
  </div>

  <div class="card neutral">
    <div class="card-time">21:05 — 23:05</div>
    <div class="card-title">✈️ 班機 CX479 返港</div>
    <div class="card-note">圓滿結束台北家庭之旅，抵達香港</div>
  </div>

</div>

<!-- ═══════════════ TIPS (shared) ═══════════════ -->
<div style="padding: 0 16px;">
  <div class="tips-section">
    <div class="tips-title">🌤️ 旅行貼士</div>

    <div class="tip-item">
      <div class="tip-icon">🌡️</div>
      <div class="tip-text">
        <strong>天氣</strong>
        <span>台北 6月約 19–23°C，早晚涼快，日間溫暖</span>
      </div>
    </div>

    <div class="tip-item">
      <div class="tip-icon">👕</div>
      <div class="tip-text">
        <strong>穿著建議</strong>
        <span>輕便長袖薄外套，方便穿脫；室內冷氣較強可加薄衫</span>
      </div>
    </div>

    <div class="tip-item">
      <div class="tip-icon">☂️</div>
      <div class="tip-text">
        <strong>雨具必備</strong>
        <span>6月為台北梅雨季，隨身帶摺疊傘或輕便雨衣</span>
      </div>
    </div>

    <div class="tip-item">
      <div class="tip-icon">🚕</div>
      <div class="tip-text">
        <strong>交通</strong>
        <span>Uber / 計程車方便；捷運一日票 $200 NT 可任搭</span>
      </div>
    </div>

    <div class="tip-item">
      <div class="tip-icon">💴</div>
      <div class="tip-text">
        <strong>貨幣</strong>
        <span>台幣（NT$）；大型商場可刷卡，夜市多用現金</span>
      </div>
    </div>

    <div class="tip-item">
      <div class="tip-icon">🏨</div>
      <div class="tip-text">
        <strong>酒店位置</strong>
        <span>台北晶華酒店位於中山區，鄰近捷運中山站，出行便利</span>
      </div>
    </div>
  </div>
</div>

<!-- FOOTER -->
<footer class="footer">
  <strong>台北家庭之旅 2026</strong><br>
  6月19日 — 21日 &nbsp;·&nbsp; 台北晶華酒店<br>
  <span style="font-size:13px; color:#777;">祝旅途愉快，家人平安 🧡</span>
</footer>

<script>
  function switchTab(day) {
    document.querySelectorAll('.tab-btn').forEach((btn, i) => {
      btn.classList.toggle('active', i + 1 === day);
    });
    document.querySelectorAll('.panel').forEach((panel, i) => {
      panel.classList.toggle('active', i + 1 === day);
    });
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }
</script>

</body>
</html>
