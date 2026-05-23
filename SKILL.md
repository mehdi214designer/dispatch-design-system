---
name: ember-design-system
description: "Ember — complete design system for the Ember brand. Use when building any UI, page, component, or layout in the Ember visual language. Covers tokens (colors, typography, spacing, radius, motion), all components (buttons, cards, nav, badges, forms, accordion, pricing, workflow, stats), layout rules, anti-patterns, and a full AI-readable specification. Trigger on: Ember, Ember website, Ember brand, dark warm UI, ember design system, ember design system, ember component."
version: "1.0.0"
source: "https://dispatch.framer.website/"
extracted: "2026-04-30"
stack: "HTML + CSS (framework-agnostic)"
---

# Ember Design System — AI Skill

A complete, self-contained skill for generating Ember-branded UI with zero design drift. Every token, rule, and component pattern is derived directly from the live Ember (dispatch.framer.website) stylesheet.

---

## When to Use This Skill

Activate this skill whenever:
- Building any page, section, or component for the Ember brand
- A user asks to "use the Ember design system"
- Reproducing or extending Ember-style UI
- Reviewing code for Ember design compliance
- Creating new components that must feel native to Ember

Do NOT activate for generic dark-mode UIs, other brands, or when the user explicitly wants a different visual language.

---

## Core Philosophy — 3 Principles

Memorize these. Every decision flows from them.

| Principle | Meaning | Violation example |
|-----------|---------|-------------------|
| **Warm Darkness** | Backgrounds are warm near-black with brown undertones, never cold grays | Using `#18181b` or `slate-900` instead of `#1d1d1d` |
| **Sharp Precision** | `1px` border-radius on all UI elements. No softness. | Using `rounded-lg`, `8px`, or `12px` on a card or input |
| **Restrained Motion** | One easing curve, one base duration, always consistent | Using `ease-in-out` or `0.3s` instead of `cubic-bezier(.44,0,.56,1)` and `400ms` |

---

## CSS Custom Properties — The Complete Token Set

**Always include this `:root` block in every generated HTML file. Never skip it.**

```css
:root {
  /* — Background — */
  --bg-primary:    #1d1d1d;   /* page / body */
  --bg-deep:       #1c1c1c;   /* sidebar, code blocks, below-surface */
  --bg-elevated:   #262626;   /* cards, inputs, modals — primary surface */
  --surface-1:     #383838;   /* hover states only */
  --surface-2:     #424242;   /* active / pressed states only */
  --warm-gray:     #635d5a;   /* tertiary text, separators */

  /* — Text — */
  --text-primary:   #f0e8da;              /* headings, titles, active */
  --text-secondary: #e3d8c5;              /* strong body */
  --text-muted:     #d1c2a5;              /* body, descriptions, nav links */
  --text-disabled:  rgba(209,194,165,.66);/* labels, placeholders */

  /* — Accent — */
  --accent:        #ff7038;               /* CTA, focus, highlight */
  --accent-hover:  #de5d35;               /* accent pressed/hover only */
  --accent-dim:    rgba(255,112,56,.12);  /* badge/tag background */
  --accent-border: rgba(255,112,56,.20);  /* accent badge border */

  /* — Border — */
  --border:        rgba(59,58,56,.74);    /* all UI borders — 1px solid */
  --border-subtle: rgba(204,189,159,.10); /* row separators, inner dividers */

  /* — Typography — */
  --font-sans:  "Geist", system-ui, sans-serif;
  --font-mono:  "IBM Plex Mono", monospace;
  --font-serif: "LT Remark", "Playfair Display", Georgia, serif;

  /* — Font sizes (only these 16 values are valid) — */
  --text-xs:   10px;
  --text-sm:   14px;
  --text-base: 16px;
  --text-lg:   18px;
  --text-xl:   20px;
  --text-2xl:  24px;
  --text-3xl:  28px;
  --text-4xl:  32px;
  --text-5xl:  40px;
  --text-6xl:  48px;
  --text-7xl:  56px;
  --text-8xl:  72px;
  --text-9xl:  80px;

  /* — Spacing (only these values are valid) — */
  --sp-1:  4px;   --sp-2:  8px;   --sp-3:  12px;  --sp-4:  16px;
  --sp-5:  20px;  --sp-6:  24px;  --sp-7:  28px;  --sp-8:  32px;
  --sp-9:  36px;  --sp-10: 40px;  --sp-14: 60px;  --sp-20: 80px;

  /* — Border radius (only these 2 values exist) — */
  --radius-sharp: 1px;    /* cards, inputs, icons, all UI */
  --radius-pill:  678px;  /* buttons, badges only */

  /* — Motion — */
  --ease:     cubic-bezier(.44, 0, .56, 1); /* the ONLY easing */
  --dur-fast: 150ms;
  --dur-base: 400ms;
  --dur-slow: 600ms;

  /* — Layout — */
  --max-w:      1600px;
  --content-w:  1228px;
  --nav-height: 80px;
}
```

---

## Color Token Usage Map

| Token | Use for | Never use for |
|-------|---------|---------------|
| `--bg-primary` | `body`, page sections | cards, inputs, interactive elements |
| `--bg-deep` | sidebar, code blocks, featured card, below-surface panels | default card background |
| `--bg-elevated` | **cards, inputs, modals, dropdowns** (most common surface) | page background |
| `--surface-1` | hover state background only | default/resting state |
| `--surface-2` | active/pressed state only | default/resting state |
| `--warm-gray` | tertiary metadata, timestamps, code values | body copy, headings |
| `--text-primary` | headings, card titles, active nav, button text on dark | body paragraphs |
| `--text-muted` | **body text, descriptions, nav links, form hints** (most common) | headings |
| `--text-disabled` | mono uppercase labels, placeholders, section numbers | readable body content |
| `--accent` | primary CTA button, active state, focus ring, hover border | more than 1–2 uses per section |
| `--accent-hover` | accent element hover/pressed state only | standalone default color |
| `--accent-dim` | badge/tag with orange tint | card backgrounds |
| `--border` | **all structural borders** — always `1px solid` | 2px borders, dashed |
| `--border-subtle` | row separators, workflow step dividers | card outlines |

---

## Typography Rules

### Font Assignment (mandatory)
```
Geist (--font-sans)      → ALL UI text: headings, body, nav, buttons, card text
IBM Plex Mono (--font-mono) → labels, badges, section numbers, code, metrics ONLY
LT Remark (--font-serif) → italic words inside hero display headings ONLY
```

### Font Weight (only 2 values)
```
400 → body, descriptions, headings, nav links
500 → button labels, card titles, active/emphasis text
FORBIDDEN: 600, 700, bold, bolder
```

### Letter Spacing (mandatory by size)
```
80–72px  → letter-spacing: -0.05em
56–48px  → letter-spacing: -0.04em
40–32px  → letter-spacing: -0.03em
24–20px  → letter-spacing: -0.02em
16–14px  → letter-spacing: 0
mono uppercase labels → letter-spacing: +0.06em to +0.10em
```

### Line Height
```
Display/hero headings → line-height: 1em
Large headings        → line-height: 1.2em
Medium headings       → line-height: 1.25em
Compact body          → line-height: 1.35em
Standard body         → line-height: 1.5em
Relaxed body          → line-height: 1.6em
```

### Mono Label Format (required pattern for all labels/eyebrows/badges)
```css
font-family: var(--font-mono);
font-size: 10px; /* or 11px */
letter-spacing: .08em;
text-transform: uppercase;
color: var(--text-disabled);
```

### Serif Italic Mixing (display headings only)
```html
<!-- CORRECT: serif italic mixed into sans heading -->
<h1 style="font-family:var(--font-sans)">
  Resolve Faster with
  <em style="font-family:var(--font-serif);font-style:italic">AI Workflows</em>
</h1>
<!-- WRONG: serif used standalone -->
<p style="font-family:var(--font-serif)">body text</p>
```

### Valid Font Sizes
```
10 · 14 · 16 · 18 · 20 · 24 · 28 · 32 · 36 · 40 · 48 · 52 · 56 · 60 · 72 · 80px
FORBIDDEN: 13px, 15px, 17px, 22px, 26px, or any value not in this list
```

---

## Spacing Rules

### Valid Spacing Values
```
4 · 8 · 12 · 16 · 20 · 24 · 28 · 32 · 36 · 40 · 60 · 80px
FORBIDDEN: 5, 7, 9, 11, 13, 15, 17, 19, 21, 25, 30px or any not in list
```

### Key Spacing Patterns
```
Section padding desktop  → padding: 80px
Section padding tablet   → padding: 60px 40px
Section padding mobile   → padding: 40px 20px
Card padding standard    → padding: 24px
Card padding feature     → padding: 24px 24px 32px (or 36px, 40px)
Nav height               → height: 80px (fixed — never change)
Nav horizontal padding   → padding: 0 40px (fixed — never change)
Nav link gap             → gap: 32px to 40px
Inline element gap       → gap: 6px to 10px
Sibling block gap        → gap: 12px to 16px
```

### Card Grid Technique (required for multi-card layouts)
```css
/* CORRECT: 1px gap on border-colored background */
.grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr); /* or 3 */
  gap: 1px;
  background: var(--border); /* THIS is what creates the grid lines */
  border: 1px solid var(--border);
}
.grid-item {
  background: var(--bg-elevated); /* solid bg "covers" the gap color */
}

/* WRONG: individual borders on each card */
.card { border: 1px solid var(--border); } /* creates double borders in grids */
```

---

## Border & Radius Rules

```
--radius-sharp → 1px: cards, inputs, textareas, selects, icons, workflow items, ALL UI
--radius-pill  → 678px: buttons, badges, tags — NOTHING ELSE

FORBIDDEN values: 2px, 4px, 6px, 8px, 10px, 12px, 16px, 24px, 50%, 100%
(only 1px and 678px exist in this system)
```

### Border Rules
```
All borders: 1px solid var(--border)   ← always 1px, always solid
Focus border: 1px solid var(--accent)  ← only on form inputs
FORBIDDEN: 2px borders, dashed, dotted, box-shadow for depth
Depth/separation: use background color steps + 1px border, never box-shadow
```

---

## Motion Rules

### The One Easing Curve
```css
/* This is the ONLY transition easing in the system */
transition: [property] 400ms cubic-bezier(.44, 0, .56, 1);

/* FORBIDDEN */
transition: [property] 300ms ease;
transition: [property] 200ms ease-in-out;
transition: [property] 0.3s linear;
```

### Duration Tiers
```
150ms → micro-interactions (small button hover, dot color)
400ms → standard transitions (nav link, card hover, border-color, input focus) ← DEFAULT
600ms → large transitions (image zoom, page-level reveals)
```

### Animatable Properties (whitelist)
```
✓ color
✓ background-color
✓ border-color
✓ opacity
✓ transform (translateX, scale — NOT layout-affecting transforms)
✓ max-height (accordion expand only)
✓ filter (brightness/saturation on images only)

✗ NEVER animate: width, height, padding, margin, top, left, right, bottom
```

### Special Cases
```css
/* Marquee: linear is allowed ONLY for infinite scroll animations */
animation: marquee 40s linear infinite;

/* Accordion icon: always rotate 45deg, never swap icons */
.accordion-item.open .icon { transform: rotate(45deg); }

/* Reduced motion: mandatory */
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    transition-duration: 1ms !important;
    animation-duration: 1ms !important;
  }
}
```

---

## Scroll Appear Animation System (Spring Physics)

Ember uses Framer's spring physics engine for scroll-triggered appear animations. The table below converts Framer spring configs into CSS cubic-bezier equivalents for use without Framer.

### Spring → CSS Conversion Table

| Framer Spring Config | CSS cubic-bezier | Feel |
|---------------------|-----------------|------|
| `spring(duration:1, bounce:0.2)` | `cubic-bezier(0.34, 1.56, 0.64, 1)` | Slight overshoot — standard |
| `spring(duration:1, bounce:0)` | `cubic-bezier(0.22, 1, 0.36, 1)` | Clean ease-out — large elements |

### The 6 Scroll Animation Patterns

| ID | `data-scroll` value | Y offset | Duration | Easing | Use for |
|----|---------------------|----------|----------|--------|---------|
| A | `data-scroll` (default) | 24px | 1000ms | `cubic-bezier(0.34,1.56,0.64,1)` | Cards, body blocks, most elements |
| B | `data-scroll="large"` | 36px | 1000ms | `cubic-bezier(0.22,1,0.36,1)` | Section headings, hero sub-elements |
| C | `data-scroll="subtle"` | 16px | 1000ms | `cubic-bezier(0.34,1.56,0.64,1)` | Small items, inline elements, badges |
| D | `data-scroll="fade"` | 0px | 700ms | `cubic-bezier(0.34,1.56,0.64,1)` | Images, backgrounds, overlays |
| E | `data-hero-delay` | 20px | 1000ms | `cubic-bezier(0.22,1,0.36,1)` | Page-load hero stagger (CSS anim, not IO) |
| F | `data-scroll` + `data-scroll-delay="2000"` | 24px | 1000ms | `cubic-bezier(0.34,1.56,0.64,1)` | Delayed hero secondary content |

### Stagger Rules
```
Stagger increment (scroll-triggered) : 100ms between siblings (data-scroll-delay)
Maximum stagger cap (scroll)          : 700ms
Hero page-load delays                 : 1.0s → 1.1s → 1.2s → 1.3s → 1.4s
data-scroll-delay unit                : milliseconds (e.g. data-scroll-delay="200")
IntersectionObserver threshold        : 0.1 (fires when 10% visible)
IntersectionObserver fires            : once — unobserve after trigger
```

### CSS Implementation (drop-in)

```css
/* ── Scroll Appear System ── */
[data-scroll] {
  opacity: 0;
  transform: translateY(24px);
  will-change: transform, opacity;
  transition:
    opacity  1s cubic-bezier(0.34, 1.56, 0.64, 1),
    transform 1s cubic-bezier(0.34, 1.56, 0.64, 1);
}
[data-scroll="large"] {
  transform: translateY(36px);
  transition:
    opacity  1s cubic-bezier(0.22, 1, 0.36, 1),
    transform 1s cubic-bezier(0.22, 1, 0.36, 1);
}
[data-scroll="subtle"] {
  transform: translateY(16px);
  /* inherits transition from [data-scroll] */
}
[data-scroll="fade"] {
  transform: none;
  transition: opacity 0.7s cubic-bezier(0.34, 1.56, 0.64, 1);
}
[data-scroll].is-visible {
  opacity: 1;
  transform: translateY(0);
}

/* ── Hero Page-Load Stagger (CSS animation — no IntersectionObserver) ── */
@keyframes hero-in {
  from { opacity: 0; transform: translateY(20px); }
  to   { opacity: 1; transform: translateY(0); }
}
[data-hero-delay] {
  opacity: 0;
  animation: hero-in 1s cubic-bezier(0.22, 1, 0.36, 1) forwards;
}
[data-hero-delay="1.0"] { animation-delay: 1.0s; }
[data-hero-delay="1.1"] { animation-delay: 1.1s; }
[data-hero-delay="1.2"] { animation-delay: 1.2s; }
[data-hero-delay="1.3"] { animation-delay: 1.3s; }
[data-hero-delay="1.4"] { animation-delay: 1.4s; }

/* ── Reduced motion: skip ALL scroll animations ── */
@media (prefers-reduced-motion: reduce) {
  [data-scroll], [data-hero-delay] {
    opacity: 1 !important;
    transform: none !important;
    animation: none !important;
    transition: none !important;
  }
}
```

### JavaScript Implementation (IntersectionObserver)

```javascript
// Scroll appear — fires once per element
const scrollIO = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      const el = entry.target;
      const delay = el.dataset.scrollDelay ? parseInt(el.dataset.scrollDelay) : 0;
      setTimeout(() => el.classList.add('is-visible'), delay);
      scrollIO.unobserve(el);
    }
  });
}, { threshold: 0.1 });

document.querySelectorAll('[data-scroll]').forEach(el => scrollIO.observe(el));
```

### Smooth Scroll Library (Lenis)

The live Ember site uses **Lenis v1.3.19** for buttery smooth scrolling. Add before closing `</body>`:

```html
<script src="https://unpkg.com/lenis@1.3.19/dist/lenis.min.js"></script>
<script>
  const lenis = new Lenis({ lerp: 0.1, smooth: true });
  function raf(time) { lenis.raf(time); requestAnimationFrame(raf); }
  requestAnimationFrame(raf);
</script>
```

### Usage Examples

```html
<!-- Pattern A: Standard fade-up (cards, paragraphs) -->
<div class="card" data-scroll>Card content</div>

<!-- Pattern A with stagger (3-card row) -->
<div class="card" data-scroll data-scroll-delay="0">First</div>
<div class="card" data-scroll data-scroll-delay="100">Second</div>
<div class="card" data-scroll data-scroll-delay="200">Third</div>

<!-- Pattern B: Large fade-up (section headings) -->
<h2 class="section-title" data-scroll="large">Section Title</h2>

<!-- Pattern C: Subtle (inline/small items) -->
<span class="badge" data-scroll="subtle">Label</span>

<!-- Pattern D: Fade only (images, backgrounds) -->
<img src="product.png" alt="Ember dashboard" data-scroll="fade">

<!-- Pattern E: Hero stagger (page-load, no scroll trigger) -->
<span class="hero-eyebrow" data-hero-delay="1.0">Trusted by AI Innovators</span>
<h1 class="hero-title" data-hero-delay="1.1">Resolve Faster with AI</h1>
<p class="hero-desc" data-hero-delay="1.2">Connect your helpdesk...</p>
<div class="hero-btns" data-hero-delay="1.3">
  <button class="btn btn-primary btn-lg">Get Started</button>
</div>
```

### Scroll Animation Rules
```
✓ Add will-change: transform, opacity to all [data-scroll] elements
✓ IntersectionObserver fires once — unobserve immediately after trigger
✓ Threshold: 0.1 (triggers when 10% of element enters viewport)
✓ Stagger via data-scroll-delay in milliseconds: 0, 100, 200, 300...
✓ Cap stagger at 700ms for scroll-triggered sequences
✓ Hero stagger uses CSS animation (data-hero-delay) — NOT IntersectionObserver
✓ Hero delays: 1.0s → 1.4s in 0.1s steps for each hero child element
✓ Respect prefers-reduced-motion: remove all transforms + animations

✗ NEVER re-trigger scroll animations on scroll back
✗ NEVER use JS setTimeout chains instead of CSS animation-delay for hero
✗ NEVER animate more than opacity + transform in scroll animations
✗ NEVER use bounce:0.5+ (too bouncy — not Ember)
✗ NEVER apply data-scroll AND data-hero-delay to the same element
```

---

## Layout Rules

### Breakpoints (3 tiers — no intermediates)
```css
/* Mobile */
@media (max-width: 809px) { }

/* Tablet */
@media (min-width: 810px) and (max-width: 1279px) { }

/* Desktop */
@media (min-width: 1280px) { }
```

### Container Widths
```
Outer layout: max-width: 1600px
Inner content: max-width: 1228px
Full-bleed: width: 100% (ticker, background sections)
```

### Grid Columns
```
2-column → major features, side-by-side content
3-column → blog cards, pricing plans
FORBIDDEN: 4-column, 5-column grids
Mobile: always collapse to 1-column
```

### No Box-Shadow Rule
```
Depth comes from: background color steps + 1px borders
NEVER use: box-shadow, drop-shadow, filter: drop-shadow()
```

### No Background Gradients Rule
```
Section backgrounds: always flat solid colors
Gradients allowed ONLY for: image overlay fades, image caption scrim
```

---

## Component Reference

### Button

```html
<!-- Primary CTA — max 1 per section -->
<button class="btn btn-primary">Get Started</button>

<!-- Secondary — supporting action -->
<button class="btn btn-secondary">Learn More</button>

<!-- Ghost — nav / tertiary -->
<button class="btn btn-ghost">View Docs</button>

<!-- Outline — accent tinted -->
<button class="btn btn-outline">See Pricing</button>
```

```css
.btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  border: none;
  font-family: var(--font-sans);
  font-weight: 400;
  cursor: pointer;
  border-radius: var(--radius-pill); /* always 678px */
  transition: background-color var(--dur-base) var(--ease),
              color var(--dur-base) var(--ease);
}
.btn-primary  { background: var(--accent); color: #1d1d1d; padding: 12px 24px; font-size: 14px; }
.btn-primary:hover { background: var(--accent-hover); }
.btn-secondary { background: var(--bg-elevated); color: var(--text-primary); border: 1px solid var(--border); padding: 12px 24px; font-size: 14px; }
.btn-secondary:hover { background: var(--surface-1); }
.btn-ghost  { background: transparent; color: var(--text-muted); padding: 12px 24px; font-size: 14px; }
.btn-ghost:hover { color: var(--text-primary); }
/* Sizes */
.btn-sm { font-size: 10px; padding: 8px 16px; }
.btn-lg { font-size: 16px; padding: 16px 36px; }
/* Disabled */
.btn:disabled { opacity: .35; cursor: not-allowed; }
```

**Button rules:**
- Text on `btn-primary` → always `#1d1d1d` (dark), never white
- Maximum **1 primary button per visual section**
- All sizes use `border-radius: 678px` without exception

---

### Badge / Tag

```html
<span class="badge badge-default">Default</span>
<span class="badge badge-accent"><span class="badge-dot"></span>Active</span>
<span class="badge badge-warm">Secondary</span>
<span class="badge badge-mono">001</span>
```

```css
.badge {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  border-radius: 678px;
  font-family: var(--font-mono);
  font-size: 10px;
  letter-spacing: .06em;
  text-transform: uppercase;
  padding: 4px 10px;
  border: 1px solid transparent;
}
.badge-default { background: var(--bg-elevated); color: var(--text-muted); border-color: var(--border); }
.badge-accent  { background: var(--accent-dim); color: var(--accent); border-color: var(--accent-border); }
.badge-warm    { background: rgba(204,189,159,.08); color: var(--text-muted); border-color: var(--border-subtle); }
.badge-mono    { background: var(--bg-deep); color: var(--warm-gray); border-color: var(--border); font-size: 9px; }
.badge-dot     { width: 5px; height: 5px; border-radius: 50%; background: currentColor; }
```

**Badge rules:**
- Font: always `--font-mono`, always uppercase, always pill-shaped
- `badge-accent` → active status, highlighted features, primary section labels
- `badge-default` → neutral tags, navigation markers
- `badge-mono` → section numbers, code IDs

---

### Navigation

```html
<nav class="nav">
  <span class="nav-logo">Ember</span>
  <div class="nav-links">
    <a class="nav-link" href="#">Home</a>
    <a class="nav-link" href="#">About</a>
    <a class="nav-link" href="#">Blog</a>
  </div>
  <div class="nav-actions">
    <button class="btn btn-ghost btn-sm">Sign in</button>
    <button class="btn btn-primary btn-sm">Get Started</button>
  </div>
</nav>
```

```css
.nav {
  height: 80px;         /* fixed — never change */
  padding: 0 40px;      /* fixed — never change */
  display: flex;
  align-items: center;
  gap: 40px;
  background: var(--bg-elevated);
  border-bottom: 1px solid var(--border);
}
.nav-logo { font-size: 15px; font-weight: 500; color: var(--text-primary); letter-spacing: -.02em; }
.nav-links { display: flex; align-items: center; gap: 32px; flex: 1; }
.nav-link  { font-size: 14px; color: var(--text-muted); text-decoration: none; transition: color var(--dur-base) var(--ease); }
.nav-link:hover { color: var(--text-primary); }
```

**Nav rules:**
- Height: always `80px`
- Horizontal padding: always `40px`
- Link gap: `32–40px`
- CTA order: Ghost (Sign In) → Primary (Get Started), always right-aligned

---

### Card

```html
<div class="card">
  <div class="card-body">
    <div class="card-label">01 — Connect</div>
    <div class="card-title">Source Connect</div>
    <p class="card-desc">Link your helpdesk, CRM, and knowledge base.</p>
  </div>
</div>
```

```css
.card { background: var(--bg-elevated); border: 1px solid var(--border); border-radius: var(--radius-sharp); overflow: hidden; }
.card-body  { padding: 24px; }
.card-label { font-family: var(--font-mono); font-size: 10px; letter-spacing: .08em; text-transform: uppercase; color: var(--text-disabled); margin-bottom: 12px; }
.card-title { font-size: 20px; font-weight: 400; letter-spacing: -.02em; color: var(--text-primary); margin-bottom: 8px; }
.card-desc  { font-size: 14px; color: var(--text-muted); line-height: 1.6em; }
/* Card grid — use gap technique */
.card-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 1px; background: var(--border); border: 1px solid var(--border); }
.card-grid > * { background: var(--bg-elevated); }
```

**Card rules:**
- Background: always `--bg-elevated`
- Border: always `1px solid var(--border)`
- Radius: always `1px`
- Label above title: always mono, uppercase, `--text-disabled`
- In grids: use 1px gap + border background, not individual card borders

---

### Form Input

```html
<div class="form-group">
  <label class="form-label" for="email">Email address</label>
  <input class="form-input" id="email" type="email" placeholder="you@company.com">
  <span class="form-hint">We'll never share your email.</span>
</div>
```

```css
.form-group  { margin-bottom: 20px; }
.form-label  { display: block; font-family: var(--font-mono); font-size: 11px; letter-spacing: .04em; color: var(--text-muted); margin-bottom: 8px; }
.form-input  {
  width: 100%;
  background: var(--bg-elevated);
  border: 1px solid var(--border);
  border-radius: 1px;             /* always 1px, never rounded */
  color: var(--text-primary);
  font-family: var(--font-sans);
  font-size: 14px;
  padding: 11px 14px;
  outline: none;
  transition: border-color var(--dur-base) var(--ease);
}
.form-input:focus       { border-color: var(--accent); }
.form-input::placeholder { color: var(--text-disabled); }
.form-input.error       { border-color: #c0544a; }
.form-hint  { font-family: var(--font-mono); font-size: 11px; color: var(--warm-gray); margin-top: 6px; display: block; }
.form-error { font-family: var(--font-mono); font-size: 11px; color: #c0544a; margin-top: 6px; display: block; }
```

**Form rules:**
- Radius: always `1px` — never rounded
- Focus: `border-color: var(--accent)` — this IS the focus indicator, no outline ring
- Label: always `--font-mono`, 11px, standard case (not uppercase for form labels)

---

### Accordion / FAQ

```html
<div class="accordion">
  <div class="acc-item open">
    <button class="acc-trigger" onclick="this.closest('.acc-item').classList.toggle('open')">
      How does Ember integrate with my helpdesk?
      <svg class="acc-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
        <path d="M12 5v14M5 12h14"/>
      </svg>
    </button>
    <div class="acc-content">
      <p class="acc-body">Answer text goes here.</p>
    </div>
  </div>
</div>
```

```css
.accordion   { border: 1px solid var(--border); }
.acc-item    { border-bottom: 1px solid var(--border); }
.acc-item:last-child { border-bottom: none; }
.acc-trigger {
  width: 100%; display: flex; align-items: center; justify-content: space-between;
  padding: 18px 22px; background: none; border: none;
  color: var(--text-primary); font-family: var(--font-sans); font-size: 14px;
  text-align: left; cursor: pointer;
  transition: background-color var(--dur-base) var(--ease);
}
.acc-trigger:hover  { background: var(--bg-elevated); }
.acc-icon           { width: 18px; height: 18px; flex-shrink: 0; color: var(--text-muted); transition: transform var(--dur-base) var(--ease); }
.acc-item.open .acc-icon { transform: rotate(45deg); } /* + becomes × */
.acc-content        { max-height: 0; overflow: hidden; transition: max-height var(--dur-base) var(--ease); }
.acc-item.open .acc-content { max-height: 200px; }
.acc-body           { padding: 0 22px 18px; font-size: 14px; color: var(--text-muted); line-height: 1.6em; }
```

**Accordion rules:**
- Icon: `+` SVG that rotates `45deg` (becomes `×`) — do not use two separate icons
- Transition: `max-height` for the content panel at `400ms`
- No border-radius on the accordion container or items

---

### Stats / Metrics

```html
<div class="stats-grid">
  <div class="stat-item">
    <div class="stat-label">Weekly Tickets</div>
    <div class="stat-value">38k</div>
    <div class="stat-sub">CRM updates automated</div>
  </div>
</div>
```

```css
.stats-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(160px, 1fr)); gap: 1px; background: var(--border); border: 1px solid var(--border); }
.stat-item  { background: var(--bg-elevated); padding: 24px; }
.stat-label { font-family: var(--font-mono); font-size: 10px; letter-spacing: .07em; text-transform: uppercase; color: var(--text-disabled); margin-bottom: 12px; }
.stat-value { font-size: 40px; font-weight: 400; letter-spacing: -.04em; line-height: 1em; color: var(--text-primary); }
.stat-sub   { font-family: var(--font-mono); font-size: 11px; color: var(--text-muted); margin-top: 8px; }
```

---

### Workflow Item

```html
<div class="workflow-card">
  <div class="workflow-step">
    <div class="workflow-icon">VP</div>
    <div class="workflow-info">
      <div class="workflow-name">Verify policy</div>
      <div class="workflow-sub">Checking refund eligibility</div>
    </div>
    <span class="workflow-status s-done">✓ done</span>
  </div>
</div>
```

```css
.workflow-card { background: var(--bg-deep); border: 1px solid var(--border); padding: 4px; }
.workflow-step { display: flex; align-items: center; gap: 14px; padding: 12px 16px; border-bottom: 1px solid var(--border-subtle); }
.workflow-step:last-child { border-bottom: none; }
.workflow-icon { width: 28px; height: 28px; background: var(--bg-elevated); border: 1px solid var(--border); border-radius: 1px; display: flex; align-items: center; justify-content: center; font-family: var(--font-mono); font-size: 10px; color: var(--text-muted); flex-shrink: 0; }
.workflow-name { font-size: 13px; color: var(--text-primary); font-weight: 500; }
.workflow-sub  { font-size: 11px; font-family: var(--font-mono); color: var(--text-muted); }
.workflow-status { font-size: 11px; font-family: var(--font-mono); }
.s-done    { color: #8db88a; }
.s-active  { color: #ff7038; }
.s-pending { color: #635d5a; }
```

---

### Pricing Card

```html
<div class="pricing-grid">
  <div class="price-card">
    <div class="price-plan">Starter</div>
    <div class="price-amount">$49</div>
    <div class="price-period">/month</div>
    <ul class="price-features">
      <li class="price-feature"><span class="feat-dot"></span>1,000 tickets/mo</li>
    </ul>
    <button class="btn btn-secondary" style="width:100%;justify-content:center;">Get Started</button>
  </div>
  <div class="price-card featured"><!-- featured uses --bg-deep --></div>
  <div class="price-card"></div>
</div>
```

```css
.pricing-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1px; background: var(--border); border: 1px solid var(--border); }
.price-card   { background: var(--bg-elevated); padding: 32px 26px 36px; }
.price-card.featured { background: var(--bg-deep); } /* no extra border/highlight needed */
.price-plan   { font-family: var(--font-mono); font-size: 10px; letter-spacing: .10em; text-transform: uppercase; color: var(--text-disabled); margin-bottom: 16px; }
.price-plan.featured-label { color: var(--accent); }
.price-amount { font-size: 48px; font-weight: 400; letter-spacing: -.04em; line-height: 1em; color: var(--text-primary); }
.price-period { font-family: var(--font-mono); font-size: 12px; color: var(--text-muted); margin: 6px 0 24px; }
.price-features { list-style: none; display: flex; flex-direction: column; gap: 10px; margin-bottom: 28px; }
.price-feature  { font-size: 14px; color: var(--text-muted); display: flex; align-items: center; gap: 10px; }
.feat-dot       { width: 4px; height: 4px; border-radius: 50%; background: var(--accent); flex-shrink: 0; }
.feat-dot.muted { background: var(--warm-gray); }
```

---

### Hero Section Pattern

```html
<section class="hero">
  <div class="hero-eyebrow">Trusted by AI Innovators</div>
  <h1 class="hero-title">
    Resolve Faster with<br>
    <em style="font-family:var(--font-serif);font-style:italic;color:var(--text-muted)">AI Workflows</em>
  </h1>
  <p class="hero-desc">Connect your helpdesk, CRM, and knowledge base. Ember resolves tickets automatically.</p>
  <div class="hero-btns">
    <button class="btn btn-primary btn-lg">Get Started</button>
    <button class="btn btn-ghost btn-lg">See How It Works</button>
  </div>
</section>
```

```css
.hero         { padding: 80px 40px; text-align: center; display: flex; flex-direction: column; align-items: center; gap: 20px; background: var(--bg-deep); }
.hero-eyebrow { font-family: var(--font-mono); font-size: 11px; letter-spacing: .08em; text-transform: uppercase; color: var(--accent); }
.hero-title   { font-family: var(--font-sans); font-size: 56px; font-weight: 400; letter-spacing: -.04em; line-height: 1.1em; color: var(--text-primary); max-width: 640px; }
.hero-desc    { font-size: 18px; color: var(--text-muted); line-height: 1.6em; max-width: 480px; letter-spacing: -.01em; }
.hero-btns    { display: flex; gap: 12px; }
```

---

### Ticker / Marquee

```html
<div class="ticker-outer">
  <div class="ticker-track">
    <span class="ticker-item">Zendesk</span>
    <span class="ticker-sep">·</span>
    <span class="ticker-item">Intercom</span>
    <!-- duplicate content for seamless loop -->
    <span class="ticker-item">Zendesk</span>
    <span class="ticker-sep">·</span>
    <span class="ticker-item">Intercom</span>
  </div>
</div>
```

```css
.ticker-outer { overflow: hidden; border-top: 1px solid var(--border); border-bottom: 1px solid var(--border); padding: 14px 0; }
.ticker-track { display: flex; gap: 48px; white-space: nowrap; animation: marquee 40s linear infinite; }
.ticker-item  { font-family: var(--font-mono); font-size: 11px; color: var(--text-muted); flex-shrink: 0; }
.ticker-sep   { color: var(--warm-gray); }
@keyframes marquee { from { transform: translateX(0); } to { transform: translateX(-50%); } }
/* linear is the ONLY exception to the --ease rule */
```

---

## Anti-Patterns — Never Do These

### Color
```
✗ background: #262626          → use var(--bg-elevated)
✗ color: #d1c2a5               → use var(--text-muted)
✗ background: #18181b          → wrong (cool gray, not warm)
✗ background: slate-900        → wrong (Tailwind cool gray)
✗ two accent-colored CTAs in one section
✗ introducing a second accent color (blue, green, purple)
```

### Typography
```
✗ font-weight: 600 / 700 / bold
✗ font-size: 15px, 17px, 22px  → must be from valid scale
✗ font-family: Geist on badges  → use IBM Plex Mono
✗ font-family: IBM Plex Mono on headings → use Geist
✗ letter-spacing: 0 on a 48px heading → must be -.04em
✗ <em> text in sans font for serif italic pattern
```

### Borders & Radius
```
✗ border-radius: 4px, 8px, 12px, 16px on any element
✗ border-radius: 50% or 100% on non-circular elements
✗ box-shadow: 0 4px 20px rgba(0,0,0,.3) → use border instead
✗ border: 2px solid ...         → always 1px
✗ border: 1px dashed ...        → always solid
```

### Motion
```
✗ transition: all 0.3s ease
✗ transition: color 200ms ease-in-out
✗ animation-timing-function: ease / linear (except marquee)
✗ animating width, height, padding, margin
✗ transition duration outside 150ms / 400ms / 600ms range
```

### Scroll Animations
```
✗ re-triggering scroll animations when element scrolls back out of view
✗ using ease or ease-in-out for scroll appear (use spring cubic-bezier values)
✗ using bounce:0.5+ spring equivalent — too bouncy, not Ember
✗ stagger delays above 700ms for scroll-triggered sequences
✗ applying data-scroll AND data-hero-delay to the same element
✗ using JS setTimeout chains for hero stagger instead of CSS animation-delay
✗ animating anything other than opacity + transform in scroll appears
✗ omitting prefers-reduced-motion handling for scroll animations
```

### Layout
```
✗ box-shadow for elevation/depth on any element
✗ background: linear-gradient(#1d1d1d, #262626) on sections
✗ 4-column or 5-column grids
✗ individual borders on each card inside a grid (use gap technique)
✗ section padding below 40px on mobile
```

---

## Base HTML Template

Use this as the starting point for any new Ember page:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Page Title — Ember</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Geist:wght@400;500&family=IBM+Plex+Mono:ital,wght@0,400;0,500;1,500&family=Playfair+Display:wght@400;500&display=swap" rel="stylesheet">
  <style>
    /* paste full :root token block here */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }
    body {
      background: var(--bg-primary);
      color: var(--text-primary);
      font-family: var(--font-sans);
      font-size: var(--text-base);
      line-height: 1.5;
      -webkit-font-smoothing: antialiased;
    }
    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after {
        transition-duration: 1ms !important;
        animation-duration: 1ms !important;
      }
    }

    /* ── Scroll Appear System ── */
    [data-scroll] {
      opacity: 0;
      transform: translateY(24px);
      will-change: transform, opacity;
      transition:
        opacity  1s cubic-bezier(0.34, 1.56, 0.64, 1),
        transform 1s cubic-bezier(0.34, 1.56, 0.64, 1);
    }
    [data-scroll="large"] {
      transform: translateY(36px);
      transition:
        opacity  1s cubic-bezier(0.22, 1, 0.36, 1),
        transform 1s cubic-bezier(0.22, 1, 0.36, 1);
    }
    [data-scroll="subtle"] { transform: translateY(16px); }
    [data-scroll="fade"]   { transform: none; transition: opacity 0.7s cubic-bezier(0.34, 1.56, 0.64, 1); }
    [data-scroll].is-visible { opacity: 1; transform: translateY(0); }

    @keyframes hero-in {
      from { opacity: 0; transform: translateY(20px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    [data-hero-delay] {
      opacity: 0;
      animation: hero-in 1s cubic-bezier(0.22, 1, 0.36, 1) forwards;
    }
    [data-hero-delay="1.0"] { animation-delay: 1.0s; }
    [data-hero-delay="1.1"] { animation-delay: 1.1s; }
    [data-hero-delay="1.2"] { animation-delay: 1.2s; }
    [data-hero-delay="1.3"] { animation-delay: 1.3s; }
    [data-hero-delay="1.4"] { animation-delay: 1.4s; }

    @media (prefers-reduced-motion: reduce) {
      [data-scroll], [data-hero-delay] {
        opacity: 1 !important;
        transform: none !important;
        animation: none !important;
        transition: none !important;
      }
    }
  </style>
</head>
<body>
  <!-- nav -->
  <!-- hero -->
  <!-- sections -->
  <!-- footer -->

  <!-- Lenis smooth scroll -->
  <script src="https://unpkg.com/lenis@1.3.19/dist/lenis.min.js"></script>
  <script>
    // Smooth scroll
    const lenis = new Lenis({ lerp: 0.1, smooth: true });
    function raf(time) { lenis.raf(time); requestAnimationFrame(raf); }
    requestAnimationFrame(raf);

    // Scroll appear animations
    const scrollIO = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          const el = entry.target;
          const delay = el.dataset.scrollDelay ? parseInt(el.dataset.scrollDelay) : 0;
          setTimeout(() => el.classList.add('is-visible'), delay);
          scrollIO.unobserve(el);
        }
      });
    }, { threshold: 0.1 });
    document.querySelectorAll('[data-scroll]').forEach(el => scrollIO.observe(el));
  </script>
</body>
</html>
```

---

## Compliance Checklist

Before delivering any Ember UI, verify:

### Tokens
- [ ] All colors use CSS custom properties — no raw hex in component styles
- [ ] `:root` token block is included in the file
- [ ] No cool-gray backgrounds used

### Typography
- [ ] Font weights are 400 or 500 only
- [ ] All headings have negative letter-spacing
- [ ] Mono labels are uppercase with positive tracking
- [ ] Font sizes are from the valid 16-value scale only

### Borders & Radius
- [ ] Cards and inputs use `border-radius: 1px`
- [ ] Buttons and badges use `border-radius: 678px`
- [ ] No `box-shadow` anywhere
- [ ] All borders are `1px solid`

### Spacing
- [ ] All spacing values from the defined scale
- [ ] Section padding is 80px desktop / 40px mobile minimum
- [ ] Card grids use 1px gap technique

### Motion (UI Transitions)
- [ ] All UI transitions use `cubic-bezier(.44, 0, .56, 1)`
- [ ] Default duration is 400ms
- [ ] No layout properties animated (no width, height, padding)
- [ ] `prefers-reduced-motion` handled for both transitions and scroll animations

### Scroll Appear Animations
- [ ] `[data-scroll]` CSS rules included in stylesheet
- [ ] IntersectionObserver JS included and observing all `[data-scroll]` elements
- [ ] `will-change: transform, opacity` on all scroll-animated elements
- [ ] Stagger delays use `data-scroll-delay` in ms (not custom CSS delays)
- [ ] Stagger cap does not exceed 700ms
- [ ] Hero elements use `data-hero-delay` CSS animation (not IntersectionObserver)
- [ ] `prefers-reduced-motion` resets all `[data-scroll]` and `[data-hero-delay]` states
- [ ] Only `opacity` and `transform` animated in scroll appears

### Components
- [ ] Maximum 1 primary button per section
- [ ] Primary button text is dark `#1d1d1d`, not white
- [ ] All badge/label text is monospace + uppercase
- [ ] Accordion icon rotates 45deg (not swapped)
- [ ] Input focus uses orange border, no outline ring

### Layout
- [ ] Only 2-col or 3-col grids used
- [ ] Mobile collapses to 1-col
- [ ] No gradients on flat backgrounds

---

## Quick Prompt Template for AI Sessions

Paste this at the start of any AI session to enforce Ember design system compliance:

```
You are building UI for the Ember brand. Follow the Ember design system exactly:

TOKENS: Use CSS vars. Never hardcode hex. Background: #1d1d1d (--bg-primary), 
cards: #262626 (--bg-elevated), accent: #ff7038. Text: #f0e8da (primary), 
#d1c2a5 (muted). Border: rgba(59,58,56,.74) always 1px solid.

TYPOGRAPHY: Geist for all UI, IBM Plex Mono for labels/badges/code only, 
LT Remark italic for display headings only. Weights: 400 or 500 only (never 600+). 
Headings: letter-spacing -.04em to -.05em. Mono labels: uppercase, ls .08em, 10–11px.

RADIUS: 1px for all UI elements. 678px for buttons and badges only. 
Nothing between 2px and 677px.

MOTION: cubic-bezier(.44,0,.56,1) exclusively. 400ms default. 
Only animate: color, background-color, border-color, opacity, transform, max-height.

LAYOUT: 80px section padding desktop. 40px mobile. 
1px gap grid technique for card grids. No box-shadow anywhere. 
Max 1 primary (orange) button per section. 3 breakpoints: 809px, 1279px.

SCROLL ANIMATIONS: Use [data-scroll] attribute on all section content.
Pattern A (default): translateY(24px), 1s, cubic-bezier(0.34,1.56,0.64,1).
Pattern B (large): translateY(36px), same duration, cubic-bezier(0.22,1,0.36,1).
Pattern D (fade): opacity only, 0.7s. Use data-scroll-delay (ms) for stagger, max 700ms.
Hero elements use data-hero-delay="1.0"→"1.4" with CSS @keyframes hero-in (not IntersectionObserver).
IntersectionObserver threshold: 0.1, fires once, adds .is-visible class.
Lenis v1.3.19 for smooth scroll. Respect prefers-reduced-motion.

FORBIDDEN: box-shadow, gradients on bg, font-weight 600+, border-radius 2–677px, 
cool grays, raw hex in component styles, ease/ease-in-out easing,
re-triggering scroll animations, stagger >700ms, bounce spring >0.2.
```

---

*Ember Design System — v1.0 — Extracted from https://dispatch.framer.website/ on 2026-04-30*
