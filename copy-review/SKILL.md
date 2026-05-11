---
name: copy-review
description: Review and/or rewrite copy against the content style guide. Use when asked to review, check, audit, improve, fix, or rewrite any text, copy, or content for style, grammar, tone, or clarity.
---

## How to use

Detect intent from $ARGUMENTS or the user's phrasing:

- **"Review / check / audit / is this OK?"** → run a review only (list issues, no rewrite)
- **"Rewrite / fix / improve / clean up"** → rewrite only (return improved copy + changes made)
- **"Review and rewrite / both"** → review first, then rewrite
- **Unclear** → do both: review, then present the rewritten version

---

## Style Guide Rules

### Voice & Tone
- Professional, conversational, practical, genuine
- Direct, savvy, clear — part of the team, not corporate
- Use "we" for the company, "you" for the user
- Gender-neutral: "they/their" instead of "she/her" or "he/his"
- Avoid inserting the company name unnecessarily — use "we" if needed

### Core Principles
- **Concise**: Every word has a purpose. Under 30 words per sentence. No filler, no redundancy.
- **Scannable**: Short paragraphs (max 5–6 sentences). Most important information first.
- **Consistent**: Same word throughout — don't swap for synonyms. Don't mix "your" and "my" in the same phrase.
- **No jargon**: Plain language. Especially in error messages.
- **Simple**: ~Sixth-grade reading level. Use "unclear" not "incomprehensible".
- **No excessive adjectives**: Remove unnecessary or redundant adjectives.
- **Present tense**: "Download video" not "Video will be downloaded".
- **Active voice**: Subject does the action. Passive only to avoid self-reference or when object matters more.
- **Positive framing**: Tell users what to do, not what they can't. "To open a report, add a personal secret" not "You can't open a report without a secret".
- **Inclusive**: "they/them", "people/folks", "underrepresented groups", "people with disabilities". No gendered or discriminatory language.

### US Spelling
- "z" spellings: realize, organize, customize, personalize
- "ense": license, offense
- "og": dialog, catalog, analog
- No double-l: modeling, paneled
- Specific words: color, center, while, fulfill

### Punctuation
- Spell out "and" — never use "&"
- Oxford comma required in lists of 3+ ("red, white, and blue")
- No exclamation marks unless truly warranted — max one per page
- Reword questions as affirmative statements where possible
- **Periods — use in**: complete sentences, body text, descriptions, help text under form fields
- **Periods — never use in**: buttons, headings, notifications, toasts, tooltips, nav items, placeholders, radio/checkbox text
- Introduce bulleted lists with a colon
- Use "…" (ellipsis character), not three periods
- Em dash with spaces on both sides: word — word
- En dash for ranges, no spaces: 50–100
- Avoid semicolons
- No ampersands

### Capitalization
- Sentence case for headings and buttons (first word + proper nouns only)
- Lowercase after slashes: "ZIP/postal code"
- List items start with a capital letter
- Product/feature names: capitalize only if unique and marketable; generic terms lowercase

### Articles
- Omit articles (a, an, the) in headings and UI labels
- Use articles normally in body copy and full sentences

### Numbers & Abbreviations
- Zero–nine: spell out (unless technical or precise)
- 10+: use numerals
- Spell out full words: "application" not "app"
- Spell out acronyms on first use: "Direct Data Mapping (DDM)", then "DDM"
- Don't start sentences with numerals

---

## Output Format

### Review only
List each issue found:

**Issue**: [quote the problematic text]
**Rule**: [which rule it violates]
**Fix**: [corrected version]

If no issues found, say so and confirm what the copy does well.

---

### Rewrite only

**Rewritten copy:**
[The rewritten text]

**Changes made:**
- [Brief bullet per change and why]

---

### Both (review + rewrite)

**Issues found:**
[Issue list as above]

**Rewritten copy:**
[Full rewritten version with all issues resolved]

**Changes made:**
- [Brief bullet per change]
