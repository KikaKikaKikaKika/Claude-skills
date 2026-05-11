---
name: copy-review
description: Review copy against the content style guide. Use when asked to review, check, or audit text, copy, or content for style, grammar, tone, or clarity.
---

Review the following copy against the content style guide rules below. For each issue found, quote the problematic text, name the rule it violates, and provide a corrected version.

Text to review: $ARGUMENTS

---

## Style Guide Rules

### Voice & Tone
- Professional, conversational, practical, genuine
- Direct, savvy, clear
- Speak with clarity; strive for expertise
- Use "we" instead of "I" when writing as the company
- Always refer to users as "you" — never use "my" or "I" (except for user consent/permissions: "I agree to…")
- Use gender-neutral "they/their" instead of "she/her" or "he/his"
- Avoid inserting the company name where possible; use "we" if necessary

### Core Principles
- **Concise**: Every word must have a purpose. Under 30 words per sentence. No redundant or filler words.
- **Scannable**: Short paragraphs (max 5–6 sentences). Most important info first.
- **Consistent**: Use the same word throughout — don't swap for synonyms. Don't mix "your" and "my" in the same phrase.
- **No jargon**: Use plain language, especially in error messages.
- **Simple**: Write at ~sixth-grade level. Avoid long, complicated words (e.g., use "unclear" not "incomprehensible").
- **No excessive adjectives**: Remove unnecessary or redundant adjectives.
- **Present tense**: Avoid future tense ("Video will be downloaded" → "Download video").
- **Active voice**: Subject does the action. Passive voice only when avoiding self-reference or the object is more important.
- **Positive language**: Tell users what to do, not what they can't do ("To open a report, add a personal secret" not "You can't open a report if you don't have a personal secret").
- **Inclusive**: Avoid gendered, prejudiced, or discriminatory language. Use "people/folks", "underrepresented groups", "people with disabilities", "they".

### US Spelling
- Use "z": realize, organization, utilize, customize, personalize
- Use "ense": license, offense
- Use "og": analog, catalog, dialog
- No double-l: modeling, paneled (not modelling, panelled)
- Specific words: color, center, while, fulfill

### Punctuation
- **Ampersands**: Never use "&" — spell out "and"
- **Oxford comma**: Required in lists of 3+ items ("red, white, and blue")
- **Exclamation marks**: Avoid — only for truly exciting moments, max one per page
- **Question marks**: Avoid where possible; reword as affirmative statements
- **Periods**: Use in full sentences, body text, help text, descriptions. Do NOT use in buttons, headings, notifications, toasts, placeholders, nav items, tooltips, radio/checkbox text
- **Colons**: Avoid in sentences; use to introduce bulleted lists
- **Semicolons**: Avoid if possible
- **Ellipses**: Avoid in UI text; always use the ellipsis character "…" not three periods
- **Em dash "—"**: Use with spaces on either side ( — ); use sparingly
- **En dash "–"**: Use for ranges (50–100), no spaces
- **Hyphen "-"**: Use to concatenate words (one-time password)
- **Double quotes**: For defining words or quoting text; commas/periods go inside quotes

### Capitalization
- **Headings**: Sentence case — capitalize first word and proper nouns only (not every word)
- **Buttons**: Sentence case
- **Product/feature names**: Capitalize only if unique and marketable; generic terms lowercase
- **After slashes**: Lowercase ("ZIP/postal code required")
- **Lists**: Each item starts with a capital letter

### Articles
- **Headers/Titles**: Avoid articles (a, an, the) — "Create users" not "Create a user"
- **UI copy**: Avoid articles except in full sentences ("Add secret" not "Add a secret")

### Abbreviations
- Don't use internal abbreviations in customer-facing copy
- Spell out full words: "application" not "app"
- Spell out acronyms on first use: "Direct Data Mapping (DDM)", then "DDM"
- Number abbreviations: no space between number and abbreviation (230M, not 230 M); capitalize K, M, B
- Avoid abbreviating large numbers unless space-limited

### Numbers
- Write out zero to nine as words unless technical/precise
- Use numerals for 10 and above
- Use commas for thousands: 100,000
- Don't start a sentence with a numeral
- Ordinal numbers in text: spell out (first, twelfth, forty-third); use 11th, 12th, etc. for 11+
- Percentages: numeral + % with no space (12%)
- Decimal separator: period "." with zero before decimals less than 1 (0.6)

### Date & Time
- Time: numeral + space + AM/PM (3:00 PM), no leading zero
- Dates: Jan 6, 2022 or January 6, 2022 (spell out if space allows)
- Numerical dates only if necessary: YYYY-MM-DD format
- No 24-hour clock

---

## Output Format

List each issue found:

**Issue**: [quote the problematic text]
**Rule**: [which rule it violates]
**Fix**: [corrected version]

If no issues are found, say so and briefly confirm what the copy does well.
