---
name: rs-cpl-usu-brand
description: >-
  Apply the RS CPL USU visual identity — a warm, light-committed cream + coral
  design language for Rumah Sakit Pendidikan Prof. Dr. Chairuddin P. Lubis,
  Universitas Sumatera Utara. Use whenever building or restyling a UI, web page,
  web app, artifact, document, slide, report, dashboard, or form for RS CPL USU
  / RS USU / Universitas Sumatera Utara, or when the user asks for the "RS CPL
  USU", "RS USU", or "USU hospital" theme, branding, color scheme, letterhead,
  kop surat, or design language. Provides the palette, the three institutional
  logos, ready-to-use CSS tokens, and header/card/button component patterns.
---

# RS CPL USU — Design Language

Visual identity for **Rumah Sakit Pendidikan Prof. Dr. Chairuddin P. Lubis**,
Universitas Sumatera Utara (Medan).
- **Tagline:** *CAREST* — six work-culture values: **C**ompassion, **A**cademic Excellence, **R**esponsibility, **E**xcellence through Innovation, **S**afety First, **T**eamwork & Trust.
- **Motto:** *The Era of Ultimate Excellence*
- **Character:** warm, clean, institutional, trustworthy. A **light-committed**
  identity (cream ground + coral accent). Do **not** produce a dark theme unless
  the user explicitly asks.

## How to use this skill

1. Drop **`assets/tokens.css`** into the project (or paste its `:root` block).
   Style everything through `var(--rscpl-*)` tokens — never hard-code the hexes.
2. Add the **three logos** to the header/letterhead (see *Logos*).
   - For a self-contained single file (artifact, offline HTML, Word export
     fidelity): embed as data URIs from **`assets/logo-datauris.md`**.
   - For a normal web project: copy the PNGs from `assets/` and reference them.
3. Follow the **Header**, **Components**, and **Responsive** patterns below.
4. Respect the **Do / Don't** rules, especially: brand the *app chrome*, but
   leave *formal printed documents* (official tables, kop-surat bodies) in their
   existing formal style unless the user asks to restyle them too.

## Palette

Full tokens in `assets/tokens.css`. Key values:

| Token | Hex | Use |
|---|---|---|
| `--rscpl-cream` | `#FCF5E8` | Page background (the signature warm ground) |
| `--rscpl-surface` | `#FFFDF8` | Header / raised surfaces |
| `--rscpl-card` | `#FFFFFF` | Cards on the cream page |
| `--rscpl-coral` | `#E8674C` | **Primary accent** — buttons, card headers, links |
| `--rscpl-coral-600` | `#D9573F` | Hover, emphasis, the script tagline |
| `--rscpl-coral-100` | `#FBE3DA` | Light coral fill (badges, focus tint) |
| `--rscpl-coral-border` | `#F2C7BB` | Outline-button borders |
| `--rscpl-coral-grad` | `linear-gradient(135deg,#E8674C,#D9573F)` | Card/header/button bars |
| `--rscpl-hero-grad` | `linear-gradient(90deg,#E8674C,#F0A692,#FBEEDD)` | Signature "WHY?" banner |
| `--rscpl-ink` | `#2C2A28` | Body text (warm near-black) |
| `--rscpl-muted` | `#8C8178` | Secondary text |
| `--rscpl-line` | `#EADFCC` | Neutral warm borders |
| `--rscpl-danger` | `#DC3545` | Required markers, errors, destructive actions |

Semantic colors (danger/ok/warn) are **separate** from the coral accent — keep
them for state, don't use them as decoration.

## Typography

- **UI / headings:** system sans — `"Segoe UI", system-ui, -apple-system, Arial, sans-serif`.
  Titles are heavy (weight 800), slightly tight tracking.
- **Tagline accent:** the *"CAREST"* motto line is set in
  **serif italic** (`Georgia, serif`) as a nod to the brand's script wordmark.
  (If a true script face is required and web-fonts are allowed, embed it as a
  `@font-face` **data URI** — never link a font CDN in a sandboxed artifact.)
- **Labels / data:** uppercase, small, letter-spaced, `--rscpl-muted`.

## Logos

Three institutional marks live in `assets/` (transparent PNG, plus ready data
URIs in `assets/logo-datauris.md`):

| File | Mark | Notes |
|---|---|---|
| `logo-usu.png` | USU seal (circular emblem) | Square |
| `logo-rs-cpl.png` | RS CPL cross (red/orange squares) | Square |
| `logo-era-excellence.png` | *The Era of Ultimate Excellence* | Wide (~2.7:1), includes text |

**Placement:** top-right of the header, like an official letterhead.
**Order (left → right):** `USU · RS CPL · Era of Ultimate Excellence`.
**Sizing:** height ~48–52px on desktop, ~40–44px on mobile; the Era mark is wider
— set height and let width follow (`width:auto`). Keep ~16–20px gap between logos.
**Never** recolor, stretch, add effects to, or place the logos on a dark/coral
ground — they're designed for a light (cream/white) surface.

## Header / letterhead pattern

Cream/white surface, brand text left, logos top-right, a **coral bottom rule**.

```html
<header class="rscpl-header">
  <div class="rscpl-brand">
    <div class="rscpl-brand-top">
      <h1><span class="mark">⚕</span> App / Document Title</h1>
      <!-- optional action, e.g. a help button, sits inline with the title -->
    </div>
    <p>RS Pendidikan Prof. Dr. Chairuddin P. Lubis · Universitas Sumatera Utara</p>
    <span class="rscpl-tagline">CAREST</span>
  </div>
  <div class="rscpl-logos">
    <img src="assets/logo-usu.png"            alt="Universitas Sumatera Utara">
    <img src="assets/logo-rs-cpl.png"         alt="RS Prof. Dr. Chairuddin P. Lubis">
    <img src="assets/logo-era-excellence.png" alt="The Era of Ultimate Excellence">
  </div>
</header>
```

```css
.rscpl-header{ background:var(--rscpl-surface); color:var(--rscpl-ink);
  display:flex; align-items:center; justify-content:space-between; gap:28px; flex-wrap:wrap;
  padding:16px 28px; border-bottom:3px solid var(--rscpl-coral);
  box-shadow:0 3px 14px -8px rgba(217,87,63,.35); }
.rscpl-brand{ display:flex; flex-direction:column; gap:4px; align-items:flex-start; }
.rscpl-brand-top{ display:flex; align-items:center; gap:12px; flex-wrap:wrap; }
.rscpl-header h1{ font-size:22px; font-weight:800; letter-spacing:-.2px; color:var(--rscpl-ink); }
.rscpl-header h1 .mark{ color:var(--rscpl-coral); }
.rscpl-header p{ font-size:11.5px; font-weight:600; color:var(--rscpl-muted); }
.rscpl-logos{ display:flex; align-items:center; gap:18px; flex-shrink:0; }
.rscpl-logos img{ height:52px; width:auto; display:block; }
.rscpl-logos img:last-child{ height:44px; }   /* Era mark is wider */
```

## Components

- **Card:** white card on the cream page, with a **coral-gradient header bar**
  (`--rscpl-coral-grad`) and a plain body. Class helpers: `.rscpl-card`,
  `.rscpl-card__head`, `.rscpl-card__body` (in `tokens.css`).
- **Buttons:** primary = coral solid (`.rscpl-btn--primary`); secondary = coral
  **outline** on white (`.rscpl-btn--outline`); tertiary = ghost; destructive =
  red danger (`.rscpl-btn--danger`). Reserve red strictly for destructive/reset.
- **Inputs:** white, `--rscpl-line` border, **coral focus ring**
  (`box-shadow:0 0 0 3px rgba(232,103,76,.18)`).
- **Badges / required:** coral-tint pill (`.rscpl-badge`); a *required* marker is
  a red pill (`.rscpl-badge--required`) + a red star `★`.
- **Hero / section banner:** the signature coral→cream horizontal gradient
  (`--rscpl-hero-grad`), white text — echoes the template's "WHY?" band. Use once,
  as a focal accent, not everywhere.
- **Footer:** a soft coral-tint bar with the RS name + address + tagline.

## Responsive

Header collapses cleanly on small screens:

```css
@media (max-width:640px){
  .rscpl-header{ flex-direction:column; align-items:stretch; gap:12px; padding:14px 18px; }
  .rscpl-header h1{ font-size:18px; }
  .rscpl-brand{ width:100%; }
  .rscpl-brand-top{ width:100%; justify-content:space-between; gap:10px; }
  .rscpl-logos{ width:100%; justify-content:center; gap:18px; }   /* centre logos */
  .rscpl-logos img{ height:44px; }
  .rscpl-logos img:last-child{ height:38px; }
}
```

## Do / Don't

**Do**
- Use the cream ground + coral accent; spend boldness on **one** focal element
  (a hero band or the primary CTA), keep the rest calm.
- Put the three logos top-right, on a light surface, in the fixed order.
- Brand the **application chrome** (header, cards, buttons, nav).

**Don't**
- Don't recolor, distort, outline, or shadow the logos.
- Don't set coral text on a coral fill, or push saturation past the tokens.
- Don't ship a dark theme for this identity unless explicitly requested.
- Don't restyle **official printed documents** (formal tables, kop-surat report
  bodies meant for signing/printing) unless the user asks — brand the app, not
  the legal document. (In the source project, the Clinical Pathway table keeps
  its formal navy styling for exactly this reason.)

## Installer notes

- **This project:** already discovered from `.claude/skills/`.
- **All your projects (global):** copy this folder to `~/.claude/skills/rs-cpl-usu-brand/`.
- **Another repo:** copy the folder into that repo's `.claude/skills/`.
- Keep the `assets/` folder alongside `SKILL.md` so the logos and tokens travel with it.
