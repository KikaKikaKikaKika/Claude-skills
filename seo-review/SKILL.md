# SEO Review Protocol

Run this automatically on ANY web page, landing page, or content output before presenting it. Never skip. Never present a page that has not passed this review.

## When to Trigger

- Any HTML page, website, or landing page is created or updated
- A blog post, article, or content page is written
- A user asks to "check SEO", "improve SEO", "audit SEO", or similar
- A page is about to be deployed or published

## Audit Framework — Rate Before & After

Always score the page before changes, apply fixes, then score again after. Present both scores.

### 1. Title Tag
- Present, unique, and descriptive
- 50–60 characters
- Contains primary keyword near the front
- Not duplicated across pages

### 2. Meta Description
- Present and unique per page
- 140–160 characters
- Compelling, includes a call to action or key benefit
- Contains primary keyword naturally

### 3. Open Graph / Social
- `og:title` — matches or improves on the page title
- `og:description` — 1–2 sentence summary
- `og:image` — real image URL, ideally 1200×630px
- `og:url` — canonical page URL
- `og:type` — "website" or "article"
- `twitter:card` — at minimum "summary_large_image"

### 4. Structured Data (JSON-LD)
- Correct schema type for the page (LocalBusiness, Article, Product, etc.)
- Required fields for that schema type populated
- Valid JSON — no syntax errors
- Nested types where applicable (PostalAddress, OpeningHoursSpecification, etc.)

### 5. Canonical URL
- `<link rel="canonical" href="...">` present on every page
- Points to the correct self-referencing URL
- Consistent with the og:url

### 6. Image Alt Texts
- Every `<img>` has a non-empty `alt` attribute
- Alt text is descriptive and contextual (not keyword-stuffed)
- Decorative images use `alt=""`
- File names are human-readable (room-with-balcony.jpg not IMG_4392.jpg)

### 7. Heading Hierarchy
- Single `<h1>` per page, contains primary keyword
- Logical `h2` → `h3` nesting, no skipped levels
- Headings describe content sections accurately

### 8. Technical Basics
- `<html lang="...">` set correctly
- `<meta charset="UTF-8">` present
- `<meta name="viewport">` present
- Page has a `robots.txt` that allows crawling
- Page is listed in `sitemap.xml`
- No broken links to critical resources

### 9. Page Speed & Core Web Vitals (flag only)
- Images use `loading="lazy"` where appropriate
- Fonts use `display=swap`
- No render-blocking resources if avoidable

### 10. Content Quality
- Primary keyword appears in title, h1, first paragraph, and meta description
- Content answers what a user searching for this page actually wants
- Internal links between related pages exist

## Scoring

Score each area 0–10. Calculate overall score as average. Present a table:

| Area | Before | After |
|------|--------|-------|
| Title | x/10 | x/10 |
| Meta Description | x/10 | x/10 |
| Open Graph | x/10 | x/10 |
| Structured Data | x/10 | x/10 |
| Canonical | x/10 | x/10 |
| Image Alts | x/10 | x/10 |
| Heading Hierarchy | x/10 | x/10 |
| Technical Basics | x/10 | x/10 |
| Content Quality | x/10 | x/10 |
| **Overall** | **x/10** | **x/10** |

## Output Requirements

1. Show before score table
2. List all issues found with severity: Critical / Important / Minor
3. Apply all fixes
4. Show after score table
5. Note any items that require user input (e.g. real address, og:image URL, Google Search Console verification)
