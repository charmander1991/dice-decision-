<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>The Oracle's Roll</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cinzel+Decorative:wght@700;900&family=Cinzel:wght@400;600;700&family=IM+Fell+English:ital@0;1&display=swap" rel="stylesheet">
<style>
/* ─── Variables ─────────────────────────────────────────── */
:root {
  --gold:       #c9a84c;
  --gold-lt:    #e8c96e;
  --gold-dk:    #7a5e18;
  --bg:         #08070a;
  --bg-card:    #0f0d12;
  --bg-raised:  #16131c;
  --text:       #cdc0a4;
  --text-dim:   #7a6e58;
  --border:     rgba(201,168,76,.2);
  --glow:       rgba(201,168,76,.12);
  --red:        rgba(180,30,30,.7);
  --blue:       rgba(20,90,160,.7);
  --green:      rgba(20,110,60,.7);
  --white:      rgba(200,185,155,.7);
  --black:      rgba(80,20,130,.7);
}

/* ─── Reset & base ──────────────────────────────────────── */
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{
  background:var(--bg);
  color:var(--text);
  font-family:'IM Fell English',serif;
  min-height:100vh;
  overflow-x:hidden;
}

/* ─── Animated background ───────────────────────────────── */
.bg-layer{
  position:fixed;inset:0;pointer-events:none;z-index:0;
  background:
    radial-gradient(ellipse 70% 50% at 50% -10%, rgba(201,168,76,.06) 0%, transparent 65%),
    radial-gradient(ellipse 50% 70% at -5%  60%, rgba(20,90,160,.04) 0%, transparent 60%),
    radial-gradient(ellipse 50% 70% at 105% 40%, rgba(180,30,30,.04) 0%, transparent 60%);
}
/* Floating particle stars */
.stars{position:fixed;inset:0;pointer-events:none;z-index:0}
.star{
  position:absolute;border-radius:50%;background:var(--gold);
  animation:twinkle var(--d) var(--dl) infinite ease-in-out;
}
@keyframes twinkle{0%,100%{opacity:0}50%{opacity:var(--op)}}

/* ─── Layout ────────────────────────────────────────────── */
.wrap{
  position:relative;z-index:1;
  max-width:720px;margin:0 auto;
  padding:48px 20px 100px;
}

/* ─── Header ────────────────────────────────────────────── */
header{text-align:center;margin-bottom:52px}

.sigil{
  width:80px;height:80px;margin:0 auto 24px;
  animation:sigil-glow 4s ease-in-out infinite;
}
@keyframes sigil-glow{
  0%,100%{filter:drop-shadow(0 0 8px rgba(201,168,76,.35))}
  50%    {filter:drop-shadow(0 0 22px rgba(201,168,76,.75))}
}

h1{
  font-family:'Cinzel Decorative',cursive;
  font-size:clamp(20px,5vw,36px);
  font-weight:900;
  color:var(--gold-lt);
  letter-spacing:.06em;
  text-shadow:0 0 40px rgba(201,168,76,.35);
  line-height:1.15;
}
.tagline{
  font-family:'Cinzel',serif;
  font-size:11px;letter-spacing:.35em;
  color:var(--text-dim);text-transform:uppercase;
  margin-top:10px;
}
.rule{
  display:flex;align-items:center;gap:14px;
  margin:28px 0 0;color:var(--gold-dk);
}
.rule::before,.rule::after{
  content:'';flex:1;height:1px;
  background:linear-gradient(to right,transparent,var(--gold-dk),transparent);
}

/* ─── Panel / card ──────────────────────────────────────── */
.card{
  background:var(--bg-card);
  border:1px solid var(--border);
  border-radius:3px;
  padding:30px 28px;
  margin-bottom:24px;
  position:relative;
  box-shadow:0 4px 60px rgba(0,0,0,.55), inset 0 1px 0 rgba(201,168,76,.07);
}
/* top-centre diamond pip */
.card::after{
  content:'◆';
  position:absolute;top:-8px;left:50%;transform:translateX(-50%);
  font-size:12px;color:var(--gold);
  background:var(--bg-card);padding:0 8px;
}

/* ─── Form elements ─────────────────────────────────────── */
.field-label{
  display:block;
  font-family:'Cinzel',serif;font-size:10px;
  letter-spacing:.3em;text-transform:uppercase;
  color:var(--gold);margin-bottom:9px;
}

textarea,input[type=text]{
  width:100%;
  background:rgba(0,0,0,.45);
  border:1px solid rgba(201,168,76,.18);
  border-radius:2px;
  color:var(--text);
  font-family:'IM Fell English',serif;font-size:16px;line-height:1.6;
  padding:13px 15px;outline:none;
  transition:border-color .25s,box-shadow .25s;
}
textarea{resize:vertical;min-height:88px}
textarea::placeholder,input::placeholder{color:var(--text-dim);font-style:italic}
textarea:focus,input:focus{
  border-color:rgba(201,168,76,.45);
  box-shadow:0 0 0 3px rgba(201,168,76,.06);
}

/* options chips */
.options-row{
  display:flex;flex-wrap:wrap;gap:8px;
  margin-top:10px;
}
.opt-chip{
  background:rgba(201,168,76,.07);
  border:1px solid rgba(201,168,76,.25);
  border-radius:2px;
  color:var(--gold-lt);
  font-family:'Cinzel',serif;font-size:11px;letter-spacing:.1em;
  padding:5px 12px;cursor:default;
}

/* ─── Die selector ──────────────────────────────────────── */
.die-grid{display:flex;flex-wrap:wrap;gap:9px;margin-top:10px}
.die-btn{
  background:rgba(0,0,0,.5);
  border:1px solid rgba(201,168,76,.18);border-radius:2px;
  color:var(--text-dim);
  font-family:'Cinzel',serif;font-size:12px;letter-spacing:.12em;
  padding:8px 18px;cursor:pointer;
  transition:all .2s;
}
.die-btn:hover{
  border-color:rgba(201,168,76,.45);color:var(--gold-lt);
  background:rgba(201,168,76,.06);
}
.die-btn.active{
  border-color:var(--gold);color:var(--gold-lt);
  background:rgba(201,168,76,.1);
  box-shadow:0 0 14px rgba(201,168,76,.18);
}

/* die hint */
.die-hint{
  font-size:12px;color:var(--text-dim);font-style:italic;
  margin-top:8px;min-height:18px;transition:opacity .3s;
}

/* ─── Roll button ───────────────────────────────────────── */
.roll-btn{
  display:block;width:100%;margin-top:26px;padding:16px;
  background:linear-gradient(135deg,#1e1608 0%,#2e200a 50%,#1e1608 100%);
  border:1px solid var(--gold);border-radius:2px;
  color:var(--gold-lt);
  font-family:'Cinzel Decorative',cursive;font-size:14px;letter-spacing:.18em;
  cursor:pointer;text-transform:uppercase;
  box-shadow:0 0 24px rgba(201,168,76,.12),inset 0 1px 0 rgba(201,168,76,.18);
  position:relative;overflow:hidden;
  transition:box-shadow .3s,color .3s;
}
.roll-btn::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(90deg,transparent,rgba(201,168,76,.12),transparent);
  transform:translateX(-100%);transition:transform .55s;
}
.roll-btn:hover:not(:disabled)::before{transform:translateX(100%)}
.roll-btn:hover:not(:disabled){
  box-shadow:0 0 36px rgba(201,168,76,.28),inset 0 1px 0 rgba(201,168,76,.3);
  color:#fff;
}
.roll-btn:disabled{opacity:.45;cursor:not-allowed}

/* ─── Dice arena ────────────────────────────────────────── */
.dice-arena{
  text-align:center;padding:10px 0 4px;
  display:none;
}
.dice-arena.show{display:block}

.die-wrap{
  display:inline-block;position:relative;
  width:130px;height:130px;
}
.die-wrap svg{
  width:100%;height:100%;
  filter:drop-shadow(0 0 18px rgba(201,168,76,.45));
}
.die-wrap.rolling svg{animation:tumble 1.1s cubic-bezier(.22,.61,.36,1) forwards}
@keyframes tumble{
  0%  {transform:rotate(0deg)   scale(.4);opacity:0}
  25% {transform:rotate(540deg) scale(1.12);opacity:1}
  65% {transform:rotate(900deg) scale(.97)}
  82% {transform:rotate(990deg) scale(1.04)}
  100%{transform:rotate(1080deg)scale(1)}
}

.die-number{
  position:absolute;inset:0;
  display:flex;align-items:center;justify-content:center;
  font-family:'Cinzel Decorative',cursive;
  font-size:30px;font-weight:900;
  color:var(--gold-lt);
  text-shadow:0 0 12px rgba(201,168,76,.9);
  opacity:0;transition:opacity .4s .9s;
  pointer-events:none;
}
.die-number.show{opacity:1}

.roll-meta{
  font-family:'Cinzel',serif;font-size:11px;
  letter-spacing:.28em;color:var(--text-dim);
  text-transform:uppercase;margin-top:14px;
  min-height:18px;
}

/* ─── Verdict panel ─────────────────────────────────────── */
.verdict{
  display:none;
  background:var(--bg-raised);
  border:1px solid rgba(201,168,76,.28);
  border-radius:3px;padding:30px 28px;
  animation:rise .55s ease forwards;
  box-shadow:0 0 50px rgba(201,168,76,.04);
}
.verdict.show{display:block}
@keyframes rise{
  from{opacity:0;transform:translateY(14px)}
  to  {opacity:1;transform:translateY(0)}
}

.verdict-header{
  font-family:'Cinzel',serif;font-size:10px;
  letter-spacing:.32em;color:var(--gold);
  text-transform:uppercase;margin-bottom:18px;
  display:flex;align-items:center;gap:10px;
}
.verdict-header::after{
  content:'';flex:1;height:1px;
  background:linear-gradient(to right,rgba(201,168,76,.3),transparent);
}

.verdict-chosen{
  font-family:'Cinzel Decorative',cursive;
  font-size:clamp(20px,4vw,28px);
  color:var(--gold-lt);
  text-shadow:0 0 20px rgba(201,168,76,.4);
  margin-bottom:14px;
  letter-spacing:.04em;
}

.verdict-flavor{
  font-size:17px;line-height:1.75;
  color:var(--text);font-style:italic;
}
.verdict-flavor b{color:var(--gold-lt);font-style:normal}

/* roll meter */
.roll-meter{
  margin-top:20px;
  height:4px;background:rgba(255,255,255,.06);
  border-radius:2px;overflow:hidden;
}
.roll-fill{
  height:100%;
  background:linear-gradient(to right,var(--gold-dk),var(--gold-lt));
  border-radius:2px;
  transition:width 1s .8s ease;
}

/* ─── History ───────────────────────────────────────────── */
.history{margin-top:44px}
.history-title{
  font-family:'Cinzel',serif;font-size:10px;
  letter-spacing:.3em;color:var(--text-dim);
  text-transform:uppercase;margin-bottom:14px;
  display:flex;align-items:center;gap:10px;
}
.history-title::after{content:'';flex:1;height:1px;background:rgba(201,168,76,.08)}

.hist-list{display:flex;flex-direction:column;gap:7px}
.hist-item{
  background:rgba(0,0,0,.28);
  border:1px solid rgba(201,168,76,.07);
  border-radius:2px;padding:9px 14px;
  display:grid;grid-template-columns:auto 1fr auto;
  gap:10px;align-items:center;
  font-size:13px;color:var(--text-dim);
}
.hist-badge{
  font-family:'Cinzel',serif;font-size:10px;
  color:var(--gold-dk);
  background:rgba(201,168,76,.05);
  border:1px solid rgba(201,168,76,.12);
  padding:2px 7px;border-radius:2px;white-space:nowrap;
}
.hist-winner{
  font-family:'Cinzel',serif;font-size:11px;
  color:var(--gold);text-align:right;white-space:nowrap;
}

/* ─── Mana pip footer ───────────────────────────────────── */
.pips{
  display:flex;justify-content:center;gap:7px;
  margin-top:30px;opacity:.35;
}
.pip{width:10px;height:10px;border-radius:50%}

footer{
  text-align:center;margin-top:20px;
  font-family:'Cinzel',serif;font-size:10px;
  letter-spacing:.2em;color:var(--text-dim);
}

/* ─── Responsive ────────────────────────────────────────── */
@media(max-width:480px){
  .card,.verdict{padding:20px 18px}
  .die-btn{padding:7px 13px;font-size:11px}
}
</style>
</head>
<body>

<div class="bg-layer"></div>
<div class="stars" id="stars"></div>

<div class="wrap">

  <!-- ── Header ── -->
  <header>
    <div class="sigil">
      <svg viewBox="0 0 80 80" fill="none" xmlns="http://www.w3.org/2000/svg">
        <circle cx="40" cy="40" r="37" stroke="#c9a84c" stroke-width="1.2" stroke-dasharray="5 3.5" opacity=".55"/>
        <circle cx="40" cy="40" r="27" stroke="#c9a84c" stroke-width=".7" opacity=".3"/>
        <polygon points="40,7 47.6,29.5 71.5,29.5 52.5,43.8 60.1,66.3 40,52 19.9,66.3 27.5,43.8 8.5,29.5 32.4,29.5"
                 stroke="#c9a84c" stroke-width="1" fill="rgba(201,168,76,.07)" opacity=".85"/>
        <polygon points="40,29 46,40 40,51 34,40" fill="#c9a84c" opacity=".95"/>
        <circle cx="40" cy="10"  r="2.2" fill="#c9a84c" opacity=".75"/>
        <circle cx="68" cy="27"  r="2.2" fill="#5090d0" opacity=".75"/>
        <circle cx="68" cy="55"  r="2.2" fill="#c04040" opacity=".75"/>
        <circle cx="40" cy="70"  r="2.2" fill="#40a060" opacity=".75"/>
        <circle cx="12" cy="55"  r="2.2" fill="#8060c0" opacity=".75"/>
        <circle cx="12" cy="27"  r="2.2" fill="#c8b89a" opacity=".75"/>
      </svg>
    </div>
    <h1>The Oracle's Roll</h1>
    <p class="tagline">Decisions forged by fate &amp; the multiverse</p>
    <div class="rule">✦</div>
  </header>

  <!-- ── Input card ── -->
  <div class="card" id="inputCard">

    <label class="field-label" for="qInput">Pose your question</label>
    <textarea id="qInput"
      placeholder="e.g. Tacos or pizza tonight? &#10;Should I watch horror or comedy? &#10;Work from home or go to the office?"></textarea>

    <!-- live option detection -->
    <div id="optionsPreview" class="options-row" style="display:none"></div>
    <p id="optionHint" style="font-size:12px;color:var(--text-dim);font-style:italic;margin-top:6px"></p>

    <!-- Die picker -->
    <div style="margin-top:22px">
      <label class="field-label">Choose your die</label>
      <div class="die-grid" id="dieGrid">
        <button class="die-btn" data-sides="4"   title="d4">d4</button>
        <button class="die-btn" data-sides="6"   title="d6">d6</button>
        <button class="die-btn active" data-sides="8" title="d8">d8</button>
        <button class="die-btn" data-sides="10"  title="d10">d10</button>
        <button class="die-btn" data-sides="12"  title="d12">d12</button>
        <button class="die-btn" data-sides="20"  title="d20">d20 ⚔</button>
        <button class="die-btn" data-sides="100" title="d100">d100</button>
      </div>
      <p class="die-hint" id="dieHint">8-sided die — balanced fate, favored by mages</p>
    </div>

    <button class="roll-btn" id="rollBtn" onclick="doRoll()">✦ Consult the Oracle ✦</button>
  </div>

  <!-- ── Dice arena ── -->
  <div class="dice-arena" id="arena">
    <div class="die-wrap" id="dieWrap">
      <svg id="dieSvg" viewBox="0 0 120 120"></svg>
      <div class="die-number" id="dieNum"></div>
    </div>
    <p class="roll-meta" id="rollMeta"></p>
  </div>

  <!-- ── Verdict ── -->
  <div class="verdict" id="verdict">
    <div class="verdict-header">✦ The Oracle Decrees</div>
    <div class="verdict-chosen" id="vChosen"></div>
    <div class="verdict-flavor" id="vFlavor"></div>
    <div class="roll-meter"><div class="roll-fill" id="vMeter" style="width:0%"></div></div>
  </div>

  <!-- ── History ── -->
  <div class="history" id="historySection" style="display:none">
    <div class="history-title">✦ Chronicle of Rolls</div>
    <div class="hist-list" id="histList"></div>
  </div>

  <!-- footer accents -->
  <div class="pips">
    <div class="pip" style="background:#5090d0"></div>
    <div class="pip" style="background:#8060c0"></div>
    <div class="pip" style="background:#c04040"></div>
    <div class="pip" style="background:#40a060"></div>
    <div class="pip" style="background:#c8b89a"></div>
  </div>
  <footer>Inscribed in the annals of the Multiverse &nbsp;·&nbsp; No planeswalkers were harmed</footer>

</div><!-- /wrap -->

<script>
/* ═══════════════════════════════════════════
   STARS
═══════════════════════════════════════════ */
const starsEl = document.getElementById('stars');
for (let i = 0; i < 90; i++) {
  const s = document.createElement('div');
  s.className = 'star';
  const sz = Math.random() < .7 ? 1.5 : 2.5;
  s.style.cssText = `width:${sz}px;height:${sz}px;left:${Math.random()*100}%;top:${Math.random()*100}%;`
    + `--d:${2+Math.random()*6}s;--dl:${Math.random()*8}s;--op:${.15+Math.random()*.55}`;
  starsEl.appendChild(s);
}

/* ═══════════════════════════════════════════
   DIE CONFIG
═══════════════════════════════════════════ */
const DIE_HINTS = {
  4:   'Unforgiving — only 4 fates await you.',
  6:   'The classic cube — simple truths, simple choices.',
  8:   '8-sided die — balanced fate, favored by mages.',
  10:  'A percentile warrior — probability made manifest.',
  12:  'Rare and deliberate — twelve paths through the planes.',
  20:  'The legendary d20 — glory or catastrophe.',
  100: 'The percentile oracle — fate measured to the last point.',
};

// SVG paths for each die shape
function buildDieSVG(sides) {
  const C = '#c9a84c', F = 'rgba(201,168,76,.08)', W = 2;
  const shapes = {
    4:   `<polygon points="60,8 112,98 8,98" fill="${F}" stroke="${C}" stroke-width="${W}" stroke-linejoin="round"/>
          <line x1="60" y1="8" x2="60" y2="98" stroke="${C}" stroke-width=".6" opacity=".35"/>
          <line x1="8"  y1="98" x2="86" y2="53" stroke="${C}" stroke-width=".6" opacity=".35"/>`,
    6:   `<rect x="8" y="8" width="104" height="104" rx="10" fill="${F}" stroke="${C}" stroke-width="${W}"/>
          <line x1="8" y1="60" x2="112" y2="60" stroke="${C}" stroke-width=".5" opacity=".25"/>
          <line x1="60" y1="8" x2="60" y2="112" stroke="${C}" stroke-width=".5" opacity=".25"/>`,
    8:   `<polygon points="60,5 112,60 60,115 8,60" fill="${F}" stroke="${C}" stroke-width="${W}" stroke-linejoin="round"/>
          <line x1="60" y1="5" x2="60" y2="115" stroke="${C}" stroke-width=".5" opacity=".3"/>
          <line x1="8" y1="60" x2="112" y2="60" stroke="${C}" stroke-width=".5" opacity=".3"/>`,
    10:  `<polygon points="60,5 108,38 98,100 22,100 12,38" fill="${F}" stroke="${C}" stroke-width="${W}" stroke-linejoin="round"/>
          <line x1="60" y1="5" x2="60" y2="100" stroke="${C}" stroke-width=".5" opacity=".3"/>`,
    12:  `<polygon points="60,4 94,18 112,52 98,90 62,112 22,90 8,52 26,18" fill="${F}" stroke="${C}" stroke-width="${W}" stroke-linejoin="round"/>`,
    20:  `<polygon points="60,4 110,32 114,84 60,116 6,84 10,32" fill="${F}" stroke="${C}" stroke-width="${W}" stroke-linejoin="round"/>
          <line x1="60" y1="4" x2="60" y2="116" stroke="${C}" stroke-width=".5" opacity=".25"/>
          <line x1="10" y1="32" x2="114" y2="84" stroke="${C}" stroke-width=".5" opacity=".25"/>
          <line x1="10" y1="84" x2="114" y2="32" stroke="${C}" stroke-width=".5" opacity=".25"/>`,
    100: `<circle cx="60" cy="60" r="54" fill="${F}" stroke="${C}" stroke-width="${W}"/>
          <circle cx="60" cy="60" r="40" fill="none" stroke="${C}" stroke-width=".6" opacity=".3"/>
          <circle cx="60" cy="60" r="24" fill="none" stroke="${C}" stroke-width=".4" opacity=".2"/>`,
  };
  return shapes[sides] || shapes[20];
}

/* ═══════════════════════════════════════════
   DIE SELECTION
═══════════════════════════════════════════ */
let selectedSides = 8;

document.getElementById('dieGrid').addEventListener('click', e => {
  const btn = e.target.closest('.die-btn');
  if (!btn) return;
  document.querySelectorAll('.die-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  selectedSides = parseInt(btn.dataset.sides);
  document.getElementById('dieHint').textContent = DIE_HINTS[selectedSides] || '';
});

/* ═══════════════════════════════════════════
   OPTION DETECTION
   Splits on "or", "vs", commas, slashes
═══════════════════════════════════════════ */
function parseOptions(text) {
  // strip trailing ? ! .
  text = text.replace(/[?!.]+$/, '').trim();
  // try splitting on " or " (case-insensitive)
  let parts = text.split(/\s+or\s+/i);
  if (parts.length < 2) parts = text.split(/\s+vs\.?\s+/i);
  if (parts.length < 2) parts = text.split(/[,\/]/);
  // clean up each
  parts = parts.map(p => p.trim()).filter(p => p.length > 0 && p.length < 60);
  return parts.length >= 2 ? parts : null;
}

const qInput = document.getElementById('qInput');
const optPreview = document.getElementById('optionsPreview');
const optHint = document.getElementById('optionHint');

qInput.addEventListener('input', () => {
  const opts = parseOptions(qInput.value);
  if (opts && opts.length >= 2) {
    optPreview.style.display = 'flex';
    optPreview.innerHTML = opts.map(o => `<span class="opt-chip">${o}</span>`).join('');
    optHint.textContent = `${opts.length} options detected — the die will choose between them.`;
  } else {
    optPreview.style.display = 'none';
    optHint.textContent = '';
  }
});

/* ═══════════════════════════════════════════
   FLAVOR TEXT ENGINE
   No AI — pure lookup tables + logic
═══════════════════════════════════════════ */
const FLAVOR = {
  // roll quality → flavor sets
  legendary: [ // top 10%
    "The planes themselves align. Fate has spoken without hesitation.",
    "A roll of this magnitude has not been seen since the Phyrexian war. The die is certain.",
    "The mana surge is undeniable — the multiverse points only one direction.",
    "Not even Nicol Bolas would argue with a roll like this.",
    "The Blind Eternities part. Your answer blazes like a beacon across every plane.",
  ],
  strong: [ // top 40%
    "A favorable wind stirs the aether. The die leans firmly toward one path.",
    "The oracle's eye is clear. Doubt not this verdict.",
    "From Ravnica to Innistrad, the vote is clear. Trust the die.",
    "A sturdy cast of fate — no mere coincidence guides this number.",
    "The mage within you already knew. The die simply confirms it.",
  ],
  neutral: [ // middle 30%
    "The scales of the Blind Eternities tip — but only just. The die has spoken.",
    "Fate is measured today, not extravagant. But measured is still certain.",
    "A balanced roll on balanced scales. The oracle sees a path forward.",
    "Not glory, not ruin — the die gives you a clear enough answer to act.",
    "In the great tapestry of the multiverse, this thread is yours to pull.",
  ],
  weak: [ // bottom 20%
    "The die rolls low — a stumble through the planes, but a direction nonetheless.",
    "Even a weak roll is a roll. The multiverse whispers: go the other way.",
    "The aether is thin. The die points away from this option — heed its counsel.",
    "A low cast of fate — the oracle raises an eyebrow but delivers judgment.",
    "Fate is hesitant... yet even hesitant fate is fate. The die has decided.",
  ],
  tragic: [ // bottom 5%
    "A roll of sorrow. Even Ob Nixilis would wince. And yet — here is your answer.",
    "Catastrophic by any measure. The die has delivered its cruelest verdict.",
    "The lowest whispers of the aether. But fate is fate, however grim.",
    "A tragic cast. The oracle bows its head — then points forward anyway.",
    "1. Or close enough. The multiverse tests your resolve this evening.",
  ],
};

const D20_SPECIAL = {
  1:  "A natural 1. The die weeps. The oracle covers its face. And yet — here is your truth.",
  20: "A NATURAL 20. The multiverse erupts. Even the Eldrazi pause. Glory is yours.",
};

function pickFlavor(roll, sides) {
  const pct = roll / sides;
  if (D20_SPECIAL[roll] && sides === 20) return D20_SPECIAL[roll];
  if (pct >= .90) return rand(FLAVOR.legendary);
  if (pct >= .60) return rand(FLAVOR.strong);
  if (pct >= .35) return rand(FLAVOR.neutral);
  if (pct >= .10) return rand(FLAVOR.weak);
  return rand(FLAVOR.tragic);
}

function rand(arr) { return arr[Math.floor(Math.random() * arr.length)]; }

/* ═══════════════════════════════════════════
   DECISION ENGINE
   Maps roll → chosen option
═══════════════════════════════════════════ */
function pickOption(opts, roll, sides) {
  const idx = (roll - 1) % opts.length;
  return opts[idx];
}

/* ═══════════════════════════════════════════
   ROLL
═══════════════════════════════════════════ */
const history = [];

async function doRoll() {
  const q = qInput.value.trim();
  if (!q) {
    qInput.focus();
    qInput.style.borderColor = 'rgba(200,50,50,.55)';
    setTimeout(() => { qInput.style.borderColor = ''; }, 1400);
    return;
  }

  const opts = parseOptions(q);
  const roll = Math.floor(Math.random() * selectedSides) + 1;
  const sides = selectedSides;

  // Disable button
  const btn = document.getElementById('rollBtn');
  btn.disabled = true;

  // Hide old verdict
  const vEl = document.getElementById('verdict');
  vEl.classList.remove('show');
  vEl.style.display = 'none';

  // Show arena
  const arena = document.getElementById('arena');
  arena.classList.add('show');

  // Draw die
  const svg = document.getElementById('dieSvg');
  svg.innerHTML = buildDieSVG(sides);

  // Reset number
  const numEl = document.getElementById('dieNum');
  numEl.textContent = '?';
  numEl.classList.remove('show');

  // Animate
  const wrap = document.getElementById('dieWrap');
  wrap.classList.remove('rolling');
  void wrap.offsetWidth; // reflow
  wrap.classList.add('rolling');

  document.getElementById('rollMeta').textContent = 'The die tumbles across the planes...';

  await sleep(1000);

  numEl.textContent = roll;
  numEl.classList.add('show');
  document.getElementById('rollMeta').textContent = `Rolled ${roll} on a d${sides}`;

  await sleep(500);

  // Build verdict
  const flavor = pickFlavor(roll, sides);
  const pct = Math.round((roll / sides) * 100);

  let chosenHTML, decreeText;

  if (opts && opts.length >= 2) {
    const chosen = pickOption(opts, roll, sides);
    chosenHTML = chosen.toUpperCase();
    decreeText = `<b>${chosen}</b> — ${flavor}`;
  } else {
    // No clear options: give roll-quality verdict
    chosenHTML = rollQualityLabel(roll, sides);
    decreeText = flavor;
  }

  document.getElementById('vChosen').textContent = chosenHTML;
  document.getElementById('vFlavor').innerHTML = decreeText;

  // Meter
  document.getElementById('vMeter').style.width = '0%';
  vEl.style.display = 'block';
  vEl.classList.add('show');
  requestAnimationFrame(() => {
    setTimeout(() => {
      document.getElementById('vMeter').style.width = pct + '%';
    }, 100);
  });

  // Scroll
  vEl.scrollIntoView({ behavior: 'smooth', block: 'nearest' });

  // History
  addHistory(q, roll, sides, opts ? pickOption(opts, roll, sides) : rollQualityLabel(roll, sides));

  btn.disabled = false;
}

function rollQualityLabel(roll, sides) {
  const pct = roll / sides;
  if (pct >= .90) return 'Legendary Roll';
  if (pct >= .60) return 'Strong Omen';
  if (pct >= .35) return 'Measured Fate';
  if (pct >= .10) return 'Weak Omen';
  return 'Tragic Cast';
}

/* ═══════════════════════════════════════════
   HISTORY
═══════════════════════════════════════════ */
function addHistory(q, roll, sides, winner) {
  history.unshift({ q, roll, sides, winner });
  if (history.length > 10) history.pop();

  const sec = document.getElementById('historySection');
  sec.style.display = 'block';

  document.getElementById('histList').innerHTML = history.map(h => `
    <div class="hist-item">
      <span class="hist-badge">d${h.sides}: ${h.roll}</span>
      <span>${h.q.length > 60 ? h.q.slice(0,60) + '…' : h.q}</span>
      <span class="hist-winner">${h.winner}</span>
    </div>
  `).join('');
}

/* ═══════════════════════════════════════════
   UTILS
═══════════════════════════════════════════ */
function sleep(ms) { return new Promise(r => setTimeout(r, ms)); }
</script>
</body>
</html>
