# Kristina Hergottová — Design Portfolio
## Brand & Visual Style Guide

**Version 1.0 · May 2026**
Applies to: Website · LinkedIn · Case Study PDFs · Proposals · Presentations · Documents · Social Media

> This is one of several brand identities. Visual style is specific to this brand.
> Content and copy rules are shared across all brands — see copy skills.

---

## 1. Brand Identity

### Name
**Kristina Hergottová** — Design Portfolio

### Positioning
Design leader with 10+ years across startups and global brands. Known for end-to-end ownership: strategy, research, systems, and execution. Not just vision — delivery.

### Personality
**Warm. Considered. Direct.**

| Trait | What it means in practice |
|---|---|
| **Warm** | Human, approachable, never cold or corporate |
| **Considered** | Thoughtful decisions, nothing arbitrary, detail-oriented |
| **Direct** | Clear communication, no filler, confident |

### Mark / Logo
No logo at this time. The `~/kristina` terminal-style mark is used **on the website only** — it does not carry to other touchpoints. Documents, presentations, and social use the name in typography only.

### What this brand is not
- Not minimalist to the point of being cold
- Not loud or self-promotional
- Not generic corporate blue-and-white
- Not AI-generated or stock-heavy

---

## 2. Color

All values given in **oklch** (web/Figma) and **hex** (documents, presentations, all other tools).

### Core Palette

| Token | Role | oklch | Hex |
|---|---|---|---|
| `--bg` | Page / slide background | `oklch(98.2% 0.007 78)` | `#F9F8F4` |
| `--bg2` | Subtle surface (cards, sections) | `oklch(96.0% 0.010 78)` | `#F4F2EC` |
| `--bg3` | Stronger surface | `oklch(93.5% 0.012 78)` | `#EFECE5` |
| `--ink` | Primary text | `oklch(15% 0.012 78)` | `#201D18` |
| `--ink2` | Secondary text, captions | `oklch(42% 0.010 78)` | `#6A665F` |
| `--ink3` | Tertiary text, metadata | `oklch(62% 0.008 78)` | `#9B9790` |
| `--accent` | Links, CTAs, highlights | `oklch(65% 0.16 55)` | `#C07A38` |
| `--border` | Dividers, outlines | `oklch(89% 0.009 78)` | `#E0DDD7` |

### Accent Variants

One accent color per context. Never mix.

| Name | oklch | Hex | When to use |
|---|---|---|---|
| **Amber** (default) | `oklch(65% 0.16 55)` | `#C07A38` | Website, general use |
| Sage | `oklch(62% 0.16 145)` | `#4A9464` | Sustainability/nature contexts |
| Sky | `oklch(65% 0.16 200)` | `#2E8FB5` | Tech/data contexts |
| Violet | `oklch(62% 0.16 280)` | `#7A5EC0` | Creative/editorial contexts |
| Rose | `oklch(65% 0.16 320)` | `#C0488A` | Bold/campaign contexts |

### Rules

- Background is **never pure white** — always `#F9F8F4`, not `#FFFFFF`
- Text is **never pure black** — always `#201D18`, not `#000000`
- Accent is used **sparingly** — links, one highlight per section, CTA buttons only
- Dark backgrounds: `#201D18` with `#F9F8F4` text — used for hero slides or section breaks only
- No gradients. No multi-color fills.

---

## 3. Typography

### Typefaces

| Role | Family | Fallback |
|---|---|---|
| Primary — UI, body, headings | **DM Sans** | Inter → system-ui → sans-serif |
| Monospace — labels, stats, code | **DM Mono** | monospace |

Both available free on Google Fonts. Download `.ttf` for Keynote/PowerPoint/Word use.
If DM Sans is unavailable: use **Inter**. If neither: **SF Pro** (macOS) or **Segoe UI** (Windows).

### Type Scale

| Level | Size | Weight | Line Height | Use |
|---|---|---|---|---|
| Display / Hero | 38–60px fluid | 300 Light | 1.12 | Page or slide headlines only |
| H1 | 32px | 400 Regular | 1.2 | Section titles |
| H2 | 22–24px | 500 Medium | 1.3 | Subsection headings |
| H3 | 16–18px | 600 Semibold | 1.4 | Card/component titles |
| Body | 15–16px | 400 Regular | 1.65 | Body text |
| Label / Small | 12–14px | 500 Medium | 1.5 | Tags, metadata, captions |
| Micro / Mono | 10–12px | 400–500 | 1.85 | Terminal labels, stats |

### Rules

- Hero headlines use **weight 300** — hierarchy comes from weight contrast, not size alone
- **No bold (700+)** in body copy — use 500 or 600 for emphasis
- **Sentence case** everywhere — no all-caps headings (exception: micro mono labels only)
- Letter spacing: `-0.01em` to `-0.02em` on large headings; `0.04em` to `0.08em` on small mono labels
- Max line length: **65–72 characters** for body text
- **Never justify** text. Left-align body copy. Center short headlines only.

---

## 4. Spacing & Layout

### Scale (base unit: 8px)

| Token | Value | Use |
|---|---|---|
| xs | 4px | Tight internal gaps |
| sm | 8px | Icon gaps, inline pairs |
| md | 16px | Default component padding |
| lg | 24–32px | Card padding |
| xl | 40px | Between components |
| 2xl | 64px | Between sections |
| 3xl | 80–96px | Top/bottom section padding |

### Layout

- Max content width: **860px**
- Horizontal page padding: 32px minimum
- Primary layout: **single column**
- Grid use: 2-column for stats/feature pairs; 3-column for tag grids only

### Rules

- Whitespace is structural — never reduce section spacing to fit more content; reduce content instead
- Mobile: horizontal padding ≥ 20px; section padding reduces to 48–64px

---

## 5. Components

### Buttons

| Type | Background | Text | Border | Radius | Padding |
|---|---|---|---|---|---|
| Primary | `--accent` / `#C07A38` | `--bg` / `#F9F8F4` | None | 8px | `10px 24px` |
| Secondary | `--bg2` / `#F4F2EC` | `--ink` / `#201D18` | `1px solid #E0DDD7` | 8px | `10px 24px` |
| Ghost | Transparent | `--ink2` / `#6A665F` | `1px solid #E0DDD7` | 8px | `10px 20px` |

- Sentence case, never all-caps
- Formula: {verb} + {noun} — "View my work", "Download CV", "Say hello"

### Cards & Surfaces

| Property | Value |
|---|---|
| Background | `#F4F2EC` |
| Border | `1px solid #E0DDD7` |
| Border radius | 14–18px |
| Shadow (rest) | `0 6px 28px rgba(0,0,0,0.07)` |
| Shadow (hover) | `0 12px 40px rgba(0,0,0,0.12)` |
| Padding | 24–32px |

### Tags / Labels

- Background: `#EFECE5`
- Border: `1px solid #E0DDD7`
- Border radius: 6px
- Font: 11–13px, weight 500, DM Sans or DM Mono
- Always neutral — never accent-colored

### Geometric Symbols

Used as section/service markers (Unicode, not SVG icons):

| Symbol | Meaning |
|---|---|
| `◎` | Strategy |
| `◈` | Leadership |
| `◐` | Collaboration |
| `◆` | Product design |
| `◇` | Service design |
| `○` | Research |

Render in accent color at 16–20px.

---

## 6. Photography

### Style

- **Realistic only** — no AI-generated images, no stock photography
- **Product photos**: real product screenshots, interface recordings, or design artifacts
- **People photos**: candid or semi-candid, natural light preferred
- **Light backgrounds** — photos should sit naturally on `#F9F8F4`; avoid images with dark or busy backgrounds as primary visuals
- No lifestyle shots (coffee cups, desks, hands typing) as primary content

### Treatment

- No filters or heavy color grading — keep images natural
- Screenshots: clean, no browser chrome unless context requires it
- Consistent aspect ratios within a single document or slide deck

---

## 7. Application by Touchpoint

### Website
Use all CSS tokens as defined. oklch in code. Full animation system applies.

### Case Study PDFs
- Background: `#F9F8F4` or white for print compatibility
- Section breaks: `#201D18` full-bleed with `#F9F8F4` text
- Accent: `#C07A38` for callouts, pull quotes, and data highlights
- Body: DM Sans 11–12pt, line height 1.6
- Headings: follow type scale, reduce sizes proportionally for print
- No shadows — use `1px solid #E0DDD7` borders instead

### Proposals
- White background for print compatibility; `#F9F8F4` cover page
- Name/title in DM Sans, display weight (300), large
- Use `#C07A38` sparingly — section numbers, key terms, links only
- Keep to single column; resist multi-column layouts

### Presentations (Keynote / Google Slides / PowerPoint)
- Slide background: `#F9F8F4`
- Dark slides (section breaks/hero): `#201D18` background, `#F9F8F4` text
- Title: Display weight (300–400), large — let whitespace carry the slide
- Max 5 lines of body text per slide
- Accent for: one key data point per chart, highlighted terms, CTAs
- No gradients, no text shadows, no decorative shapes
- Charts: `#201D18`, `#6A665F`, `#9B9790` for data series; accent for the single most important value only

### LinkedIn
- Cover image: `#F9F8F4` background, name in DM Sans, role/tagline in secondary text color
- Post visuals: consistent with case study PDF style — light, clean, real screenshots or simple text cards
- No branded templates with heavy graphic elements

### Social Media
- Same palette and typography rules as LinkedIn
- Keep text minimal on images — let visuals speak
- No decorative frames or borders around photos

### Documents (Notion / Google Docs)
- Background: `#F9F8F4` where supported; otherwise white
- Use heading styles following the type scale
- Accent color for links and key callouts only
- Dividers: `1px solid #E0DDD7` or equivalent

---

## 8. What to Avoid

- `#FFFFFF` or `#000000` — never pure white or pure black
- More than one accent color in the same piece
- Weight 700+ in body copy
- All-caps headings (except micro labels)
- AI-generated or stock imagery
- Gradients, heavy drop shadows, decorative borders
- More than two typefaces (DM Sans + DM Mono only)
- Justified or centered body text
- The `~/kristina` mark outside the website
- Busy, dark, or lifestyle photography as primary visuals

---

## 9. Quick Reference

```
BACKGROUNDS     #F9F8F4   #F4F2EC   #EFECE5
TEXT            #201D18   #6A665F   #9B9790
ACCENT          #C07A38   (amber, default)
BORDER          #E0DDD7

FONTS           DM Sans — 300, 400, 500, 600
                DM Mono — 400, 500

RADIUS          Buttons 8px · Cards 14–18px · Tags 6px
SPACING         Base 8px · Sections 80–96px · Max-width 860px
PHOTOS          Realistic · Product or candid · Light backgrounds · Not generated
```
