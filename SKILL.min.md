---
name: ember-design-system-min
description: "Ember — minified Ember design system. All tokens, rules, components, and motion specs. No prose — spec data only. Use for Claude Projects / token-efficient sessions."
version: "1.0.0-min"
source: "https://dispatch.framer.website/"
---

# Ember Design System — Minified

**3 laws:** Warm dark backgrounds (#1d1d1d, never cool grays) · 1px radius on all UI · cubic-bezier(.44,0,.56,1) for all transitions.

---

## Tokens — :root

```css
:root {
  --bg-primary:#1d1d1d; --bg-deep:#1c1c1c; --bg-elevated:#262626;
  --surface-1:#383838; --surface-2:#424242; --warm-gray:#635d5a;
  --text-primary:#f0e8da; --text-secondary:#e3d8c5; --text-muted:#d1c2a5;
  --text-disabled:rgba(209,194,165,.66);
  --accent:#ff7038; --accent-hover:#de5d35;
  --accent-dim:rgba(255,112,56,.12); --accent-border:rgba(255,112,56,.20);
  --border:rgba(59,58,56,.74); --border-subtle:rgba(204,189,159,.10);
  --font-sans:"Geist",system-ui,sans-serif;
  --font-mono:"IBM Plex Mono",monospace;
  --font-serif:"LT Remark","Playfair Display",Georgia,serif;
  --text-xs:10px; --text-sm:14px; --text-base:16px; --text-lg:18px;
  --text-xl:20px; --text-2xl:24px; --text-3xl:28px; --text-4xl:32px;
  --text-5xl:40px; --text-6xl:48px; --text-7xl:56px; --text-8xl:72px; --text-9xl:80px;
  --sp-1:4px; --sp-2:8px; --sp-3:12px; --sp-4:16px; --sp-5:20px; --sp-6:24px;
  --sp-7:28px; --sp-8:32px; --sp-9:36px; --sp-10:40px; --sp-14:60px; --sp-20:80px;
  --radius-sharp:1px; --radius-pill:678px;
  --ease:cubic-bezier(.44,0,.56,1); --dur-fast:150ms; --dur-base:400ms; --dur-slow:600ms;
  --max-w:1600px; --content-w:1228px; --nav-height:80px;
}
```

---

## Color Usage

| Token | Use for | Never |
|-------|---------|-------|
| `--bg-primary` | body, page sections | cards, inputs |
| `--bg-deep` | sidebar, code blocks, featured card | default card bg |
| `--bg-elevated` | cards, inputs, modals, dropdowns | page background |
| `--surface-1` | hover bg only | resting state |
| `--surface-2` | active/pressed only | resting state |
| `--text-primary` | headings, titles, active nav | body paragraphs |
| `--text-muted` | body, descriptions, nav links | headings |
| `--text-disabled` | mono labels, placeholders | readable body |
| `--accent` | CTA, focus ring, active | >2 uses/section |
| `--border` | all borders — 1px solid only | 2px, dashed |
| `--border-subtle` | row separators, inner dividers | card outlines |

---

## Typography

```
FONTS
  Geist (--font-sans)   → all UI: headings, body, nav, buttons
  IBM Plex Mono         → labels, badges, code, metrics ONLY
  LT Remark (--font-serif) → italic em inside hero headings ONLY

WEIGHTS  400 body/headings  ·  500 buttons/emphasis  ·  NEVER 600+

LETTER-SPACING (mandatory by size)
  80–72px → -0.05em  ·  56–48px → -0.04em  ·  40–32px → -0.03em
  24–20px → -0.02em  ·  16–14px → 0  ·  mono-uppercase → +0.06em–+0.10em

LINE-HEIGHT
  display  → 1em  ·  h2  → 1.2em  ·  h3  → 1.25em
  compact  → 1.35em  ·  body → 1.5em  ·  relaxed → 1.6em

VALID SIZES ONLY: 10 14 16 18 20 24 28 32 36 40 48 52 56 60 72 80px

MONO LABEL PATTERN (required for all eyebrows/badges/section-nums)
  font-family:var(--font-mono); font-size:10px; letter-spacing:.08em;
  text-transform:uppercase; color:var(--text-disabled);

SERIF ITALIC (display only)
  <h1>Heading <em style="font-family:var(--font-serif);font-style:italic">word</em></h1>
```

---

## Spacing

```
VALID VALUES: 4 8 12 16 20 24 28 32 36 40 60 80px  — no others
Section desktop → 80px  ·  tablet → 60px 40px  ·  mobile → 40px 20px
Card padding    → 24px  ·  feature card → 24px 24px 36px
Nav height      → 80px (fixed)  ·  nav padding → 0 40px (fixed)
Nav link gap    → 32–40px  ·  inline gap → 6–10px  ·  block gap → 12–16px
```

---

## Borders & Radius

```
--radius-sharp 1px  → cards, inputs, textareas, icons, ALL UI
--radius-pill 678px → buttons, badges ONLY
FORBIDDEN: 2 4 6 8 10 12 16 24px · 50% · 100% · box-shadow

All borders: 1px solid var(--border)
Focus:       1px solid var(--accent)  [inputs only]
FORBIDDEN: 2px · dashed · dotted · box-shadow for depth
```

---

## Motion — UI Transitions

```
SINGLE EASING: cubic-bezier(.44,0,.56,1) — no other value
DURATIONS: 150ms micro  ·  400ms default  ·  600ms large
ANIMATE ONLY: color · background-color · border-color · opacity · transform · max-height
NEVER ANIMATE: width · height · padding · margin · top · left

Special:
  marquee → animation: marquee 40s linear infinite  [linear OK here only]
  accordion → .open .icon { transform: rotate(45deg); }
  @media(prefers-reduced-motion:reduce){ *{ transition-duration:1ms!important; } }
```

---

## Motion — Scroll Appear System

**Spring → CSS** `bounce:0.2` → `cubic-bezier(0.34,1.56,0.64,1)` (overshoot) · `bounce:0` → `cubic-bezier(0.22,1,0.36,1)` (clean)

| Pattern | Attribute | Y | Duration | Easing |
|---------|-----------|---|----------|--------|
| A Standard | `data-scroll` | 24px | 1s | 0.34,1.56,0.64,1 |
| B Large | `data-scroll="large"` | 36px | 1s | 0.22,1,0.36,1 |
| C Subtle | `data-scroll="subtle"` | 16px | 1s | 0.34,1.56,0.64,1 |
| D Fade | `data-scroll="fade"` | 0 | 0.7s | 0.34,1.56,0.64,1 |
| E Hero | `data-hero-delay="1.0"–"1.4"` | 20px | 1s | 0.22,1,0.36,1 |

**Stagger:** 100ms steps · max 700ms cap · `data-scroll-delay="200"` (ms) · Hero uses CSS animation-delay, NOT IntersectionObserver

```css
[data-scroll]{opacity:0;transform:translateY(24px);will-change:transform,opacity;
  transition:opacity 1s cubic-bezier(.34,1.56,.64,1),transform 1s cubic-bezier(.34,1.56,.64,1)}
[data-scroll="large"]{transform:translateY(36px);
  transition:opacity 1s cubic-bezier(.22,1,.36,1),transform 1s cubic-bezier(.22,1,.36,1)}
[data-scroll="subtle"]{transform:translateY(16px)}
[data-scroll="fade"]{transform:none;transition:opacity .7s cubic-bezier(.34,1.56,.64,1)}
[data-scroll].is-visible{opacity:1;transform:translateY(0)}
@keyframes hero-in{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:none}}
[data-hero-delay]{opacity:0;animation:hero-in 1s cubic-bezier(.22,1,.36,1) forwards}
[data-hero-delay="1.0"]{animation-delay:1.0s}[data-hero-delay="1.1"]{animation-delay:1.1s}
[data-hero-delay="1.2"]{animation-delay:1.2s}[data-hero-delay="1.3"]{animation-delay:1.3s}
[data-hero-delay="1.4"]{animation-delay:1.4s}
@media(prefers-reduced-motion:reduce){[data-scroll],[data-hero-delay]{
  opacity:1!important;transform:none!important;animation:none!important;transition:none!important}}
```

```js
const io=new IntersectionObserver(entries=>{
  entries.forEach(e=>{if(!e.isIntersecting)return;
    const el=e.target,d=el.dataset.scrollDelay?+el.dataset.scrollDelay:0;
    setTimeout(()=>el.classList.add('is-visible'),d);io.unobserve(el);
  });},{threshold:0.08});
document.querySelectorAll('[data-scroll]').forEach(el=>io.observe(el));
```

Smooth scroll: `<script src="https://unpkg.com/lenis@1.3.19/dist/lenis.min.js"></script>` + `new Lenis({lerp:0.1})`

---

## Layout

```
Breakpoints: mobile ≤809px · tablet 810–1279px · desktop ≥1280px
Container:   max-width:1600px outer · 1228px content · 100% full-bleed
Grids:       2-col or 3-col ONLY · mobile always 1-col
No box-shadow · no background gradients on sections
```

**1px Gap Grid (required for card/stat/pricing grids):**
```css
.grid{display:grid;grid-template-columns:repeat(2,1fr);gap:1px;background:var(--border);border:1px solid var(--border)}
.grid>*{background:var(--bg-elevated)}
```

---

## Components — CSS Reference

```css
/* BUTTON */
.btn{display:inline-flex;align-items:center;gap:8px;border:none;font-family:var(--font-sans);
  font-weight:400;cursor:pointer;border-radius:678px;
  transition:background-color var(--dur-base) var(--ease),color var(--dur-base) var(--ease)}
.btn-primary{background:var(--accent);color:#1d1d1d;padding:12px 24px;font-size:14px}
.btn-primary:hover{background:var(--accent-hover)}
.btn-secondary{background:var(--bg-elevated);color:var(--text-primary);border:1px solid var(--border);padding:12px 24px;font-size:14px}
.btn-secondary:hover{background:var(--surface-1)}
.btn-ghost{background:transparent;color:var(--text-muted);padding:12px 24px;font-size:14px}
.btn-ghost:hover{color:var(--text-primary)}
.btn-sm{font-size:10px;padding:8px 16px} .btn-lg{font-size:16px;padding:16px 36px}
.btn:disabled{opacity:.35;cursor:not-allowed}
/* RULE: btn-primary text always #1d1d1d (dark). Max 1 primary per section. */

/* BADGE */
.badge{display:inline-flex;align-items:center;gap:6px;border-radius:678px;
  font-family:var(--font-mono);font-size:10px;letter-spacing:.06em;
  text-transform:uppercase;padding:4px 10px;border:1px solid transparent}
.badge-default{background:var(--bg-elevated);color:var(--text-muted);border-color:var(--border)}
.badge-accent{background:var(--accent-dim);color:var(--accent);border-color:var(--accent-border)}
.badge-warm{background:rgba(204,189,159,.08);color:var(--text-muted);border-color:var(--border-subtle)}
.badge-mono{background:var(--bg-deep);color:var(--warm-gray);border-color:var(--border);font-size:9px}
.badge-dot{width:5px;height:5px;border-radius:50%;background:currentColor}

/* NAV */
.nav{height:80px;padding:0 40px;display:flex;align-items:center;gap:40px;
  background:var(--bg-elevated);border-bottom:1px solid var(--border)}
.nav-logo{font-size:15px;font-weight:500;color:var(--text-primary);letter-spacing:-.02em}
.nav-links{display:flex;align-items:center;gap:32px;flex:1}
.nav-link{font-size:14px;color:var(--text-muted);text-decoration:none;
  transition:color var(--dur-base) var(--ease)}
.nav-link:hover{color:var(--text-primary)}
/* RULE: height 80px fixed · padding 0 40px fixed · CTA order: ghost→primary right */

/* CARD */
.card{background:var(--bg-elevated);border:1px solid var(--border);border-radius:1px;overflow:hidden}
.card-body{padding:24px}
.card-label{font-family:var(--font-mono);font-size:10px;letter-spacing:.08em;
  text-transform:uppercase;color:var(--text-disabled);margin-bottom:12px}
.card-title{font-size:20px;font-weight:400;letter-spacing:-.02em;color:var(--text-primary);margin-bottom:8px}
.card-desc{font-size:14px;color:var(--text-muted);line-height:1.6em}

/* FORM */
.form-group{margin-bottom:20px}
.form-label{display:block;font-family:var(--font-mono);font-size:11px;letter-spacing:.04em;
  color:var(--text-muted);margin-bottom:8px}
.form-input{width:100%;background:var(--bg-elevated);border:1px solid var(--border);
  border-radius:1px;color:var(--text-primary);font-family:var(--font-sans);font-size:14px;
  padding:11px 14px;outline:none;transition:border-color var(--dur-base) var(--ease)}
.form-input:focus{border-color:var(--accent)}
.form-input::placeholder{color:var(--text-disabled)}
.form-input.error{border-color:#c0544a}
.form-hint{font-family:var(--font-mono);font-size:11px;color:var(--warm-gray);margin-top:6px;display:block}
/* RULE: radius always 1px · focus = orange border only, no outline ring */

/* ACCORDION */
.accordion{border:1px solid var(--border)}
.acc-item{border-bottom:1px solid var(--border)}
.acc-item:last-child{border-bottom:none}
.acc-trigger{width:100%;display:flex;align-items:center;justify-content:space-between;
  padding:18px 22px;background:none;border:none;color:var(--text-primary);
  font-family:var(--font-sans);font-size:14px;cursor:pointer;
  transition:background-color var(--dur-base) var(--ease)}
.acc-trigger:hover{background:var(--bg-elevated)}
.acc-icon{width:18px;height:18px;flex-shrink:0;color:var(--text-muted);
  transition:transform var(--dur-base) var(--ease)}
.acc-item.open .acc-icon{transform:rotate(45deg)}
.acc-content{max-height:0;overflow:hidden;transition:max-height var(--dur-base) var(--ease)}
.acc-item.open .acc-content{max-height:200px}
.acc-body{padding:0 22px 18px;font-size:14px;color:var(--text-muted);line-height:1.6em}
/* RULE: icon is + SVG rotated 45deg — never swap two icons */

/* STATS */
.stats-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(160px,1fr));
  gap:1px;background:var(--border);border:1px solid var(--border)}
.stat-item{background:var(--bg-elevated);padding:24px}
.stat-label{font-family:var(--font-mono);font-size:10px;letter-spacing:.07em;
  text-transform:uppercase;color:var(--text-disabled);margin-bottom:12px}
.stat-value{font-size:40px;font-weight:400;letter-spacing:-.04em;line-height:1em;color:var(--text-primary)}
.stat-sub{font-family:var(--font-mono);font-size:11px;color:var(--text-muted);margin-top:8px}

/* WORKFLOW */
.workflow-card{background:var(--bg-deep);border:1px solid var(--border);padding:4px}
.workflow-step{display:flex;align-items:center;gap:14px;padding:12px 16px;
  border-bottom:1px solid var(--border-subtle)}
.workflow-step:last-child{border-bottom:none}
.workflow-icon{width:28px;height:28px;background:var(--bg-elevated);border:1px solid var(--border);
  border-radius:1px;display:flex;align-items:center;justify-content:center;
  font-family:var(--font-mono);font-size:10px;color:var(--text-muted);flex-shrink:0}
.workflow-name{font-size:13px;color:var(--text-primary);font-weight:500}
.workflow-sub{font-size:11px;font-family:var(--font-mono);color:var(--text-muted)}
.workflow-status{font-size:11px;font-family:var(--font-mono)}
.s-done{color:#8db88a} .s-active{color:#ff7038} .s-pending{color:#635d5a}

/* PRICING */
.pricing-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1px;
  background:var(--border);border:1px solid var(--border)}
.price-card{background:var(--bg-elevated);padding:32px 26px 36px}
.price-card.featured{background:var(--bg-deep)}
.price-plan{font-family:var(--font-mono);font-size:10px;letter-spacing:.10em;
  text-transform:uppercase;color:var(--text-disabled);margin-bottom:16px}
.price-amount{font-size:48px;font-weight:400;letter-spacing:-.04em;line-height:1em;color:var(--text-primary)}
.price-period{font-family:var(--font-mono);font-size:12px;color:var(--text-muted);margin:6px 0 24px}
.price-features{list-style:none;display:flex;flex-direction:column;gap:10px;margin-bottom:28px}
.price-feature{font-size:14px;color:var(--text-muted);display:flex;align-items:center;gap:10px}
.feat-dot{width:4px;height:4px;border-radius:50%;background:var(--accent);flex-shrink:0}
.feat-dot.muted{background:var(--warm-gray)}

/* HERO */
.hero{padding:80px 40px;text-align:center;display:flex;flex-direction:column;
  align-items:center;gap:20px;background:var(--bg-deep)}
.hero-eyebrow{font-family:var(--font-mono);font-size:11px;letter-spacing:.08em;
  text-transform:uppercase;color:var(--accent)}
.hero-title{font-family:var(--font-sans);font-size:56px;font-weight:400;
  letter-spacing:-.04em;line-height:1.1em;color:var(--text-primary);max-width:640px}
.hero-desc{font-size:18px;color:var(--text-muted);line-height:1.6em;max-width:480px;letter-spacing:-.01em}
.hero-btns{display:flex;gap:12px}

/* TICKER */
.ticker-outer{overflow:hidden;border-top:1px solid var(--border);
  border-bottom:1px solid var(--border);padding:14px 0}
.ticker-track{display:flex;gap:48px;white-space:nowrap;animation:marquee 40s linear infinite}
.ticker-item{font-family:var(--font-mono);font-size:11px;color:var(--text-muted);flex-shrink:0}
.ticker-sep{color:var(--warm-gray)}
@keyframes marquee{from{transform:translateX(0)}to{transform:translateX(-50%)}}
```

---

## Anti-Patterns

```
COLOR:    raw hex in CSS · cool gray bg (#18181b, slate-900) · 2 accent CTAs/section · second accent color
TYPE:     font-weight 600+ · font-size off-scale · Geist on badges · Mono on headings · no neg-ls on headings
RADIUS:   anything 2–677px · box-shadow for depth · 2px borders · dashed borders
MOTION:   ease / ease-in-out (UI) · animate width/height/padding · duration outside 150/400/600ms
SCROLL:   re-trigger on scroll-out · ease easing · stagger >700ms · data-scroll + data-hero-delay same el
          · JS setTimeout chains for hero · animate non-opacity/transform · skip prefers-reduced-motion
LAYOUT:   box-shadow · bg gradients on sections · 4-col/5-col grids · individual borders in grid · padding <40px mobile
```

---

## Base Template

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"><meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Page — Ember</title>
  <link href="https://fonts.googleapis.com/css2?family=Geist:wght@400;500&family=IBM+Plex+Mono:wght@400;500&family=Playfair+Display:ital,wght@1,400&display=swap" rel="stylesheet">
  <style>
    :root{ /* paste token block */ }
    *,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
    body{background:var(--bg-primary);color:var(--text-primary);font-family:var(--font-sans);font-size:16px;line-height:1.5;-webkit-font-smoothing:antialiased}
    [data-scroll]{opacity:0;transform:translateY(24px);will-change:transform,opacity;transition:opacity 1s cubic-bezier(.34,1.56,.64,1),transform 1s cubic-bezier(.34,1.56,.64,1)}
    [data-scroll="large"]{transform:translateY(36px);transition:opacity 1s cubic-bezier(.22,1,.36,1),transform 1s cubic-bezier(.22,1,.36,1)}
    [data-scroll="subtle"]{transform:translateY(16px)}
    [data-scroll="fade"]{transform:none;transition:opacity .7s cubic-bezier(.34,1.56,.64,1)}
    [data-scroll].is-visible{opacity:1;transform:translateY(0)}
    @keyframes hero-in{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:none}}
    [data-hero-delay]{opacity:0;animation:hero-in 1s cubic-bezier(.22,1,.36,1) forwards}
    [data-hero-delay="1.0"]{animation-delay:1.0s}[data-hero-delay="1.1"]{animation-delay:1.1s}
    [data-hero-delay="1.2"]{animation-delay:1.2s}[data-hero-delay="1.3"]{animation-delay:1.3s}
    [data-hero-delay="1.4"]{animation-delay:1.4s}
    @media(prefers-reduced-motion:reduce){[data-scroll],[data-hero-delay]{opacity:1!important;transform:none!important;animation:none!important;transition:none!important}}
  </style>
</head>
<body>
  <!-- nav · hero · sections · footer -->
  <script src="https://unpkg.com/lenis@1.3.19/dist/lenis.min.js"></script>
  <script>
    new Lenis({lerp:0.1});
    const io=new IntersectionObserver(e=>{e.forEach(e=>{if(!e.isIntersecting)return;
      const el=e.target,d=+el.dataset.scrollDelay||0;
      setTimeout(()=>el.classList.add('is-visible'),d);io.unobserve(el)});
    },{threshold:0.08});
    document.querySelectorAll('[data-scroll]').forEach(el=>io.observe(el));
  </script>
</body>
</html>
```

---

## Quick Prompt

```
Ember design system. Follow exactly:
TOKENS: CSS vars only. bg:#1d1d1d cards:#262626 accent:#ff7038 text:#f0e8da muted:#d1c2a5 border:rgba(59,58,56,.74) 1px solid.
TYPE: Geist UI · Mono labels/badges/code · Serif italic display em only. Weights 400/500 only.
RADIUS: 1px all UI · 678px buttons+badges only. Nothing between.
MOTION: cubic-bezier(.44,0,.56,1) · 400ms default · opacity/transform/color/border-color only.
SCROLL: data-scroll=large(36px) standard(24px) subtle(16px) fade(0). IntersectionObserver threshold 0.08 fires once. Hero: data-hero-delay="1.0"→"1.4" CSS anim. Stagger 100ms steps max 700ms.
LAYOUT: 80px section pad desktop · 40px mobile · 1px gap grid · no box-shadow · no bg-gradients · max 1 orange CTA/section.
NEVER: weight 600+ · radius 2–677px · cool grays · box-shadow · ease/ease-in-out · raw hex in CSS.
```

---

*Ember Design System — v1.0-min — dispatch.framer.website — 2026-04-30*
