---
name: visual-style
description: Apply or review visual style and brand guidelines. Always ask which brand before proceeding. Use when working on design, layout, visual assets, presentations, documents, or any visual output.
disable-model-invocation: true
---

Before doing anything, ask the user:

**"Which brand should I apply?**
1. Design Portfolio (kristinadesign.netlify.app)
2. [Other brand — specify]"

Wait for their answer. Then proceed based on their choice.

---

## Brand 1: Design Portfolio

Full guidelines are in [design-portfolio-brand-guide.md](design-portfolio-brand-guide.md).

Key rules to apply:

**Colors**
- Background: `#F9F8F4` (never pure white)
- Text: `#201D18` (never pure black), secondary `#6A665F`, tertiary `#9B9790`
- Accent: `#C07A38` (amber) — used sparingly
- Border: `#E0DDD7`

**Typography**
- DM Sans (300, 400, 500, 600) + DM Mono (400, 500)
- Display headlines: weight 300
- Sentence case everywhere
- No bold (700+) in body copy
- Left-align body; never justify

**Spacing**
- Base 8px unit
- Section padding 80–96px
- Max content width 860px

**Photography**
- Realistic only — no AI-generated, no stock
- Product screenshots or candid people photos
- Light backgrounds

**By touchpoint**
- Website: full CSS token system
- Presentations: `#F9F8F4` slides, dark section breaks with `#201D18`, max 5 lines/slide
- PDFs/proposals: light bg, accent for callouts only, no shadows
- LinkedIn/social: clean, light, real visuals — no decorative templates

**Never**
- Pure white/black
- More than one accent color
- Gradients or text shadows
- AI-generated imagery
- `~/kristina` mark outside the website
- More than two typefaces

---

## Other Brands

Not yet defined. If the user selects a brand that doesn't have a guide yet, say:
"I don't have a style guide for that brand yet. Would you like to create one?"

---

## Task: $ARGUMENTS

Apply the selected brand's visual guidelines to the task described above.
