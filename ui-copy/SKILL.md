---
name: ui-copy
description: Write or review UI copy (buttons, headings, links, tooltips, error messages, empty states, confirmations) following the content style guide. Use when working on interface text, microcopy, or UI components.
---

Write or review UI copy for the following: $ARGUMENTS

Apply the UI copy rules from the content style guide below.

---

## UI Copy Rules

### General UI Principles
- Sentence case everywhere: capitalize first word and proper nouns only
- No periods in UI text unless it's a full sentence (body text, descriptions, help text)
- No articles (a, an, the) in labels and short UI strings — use them in full sentences only
- Active voice, present tense
- Clear, concise — users scan, they don't read

### Headings & Subheadings
- Informative and descriptive: tell users what they'll find in the section
- Single sentence maximum
- Sentence case
- No punctuation (no periods, commas, semicolons)
- No articles unless essential

### Sentences / Body Copy
- Start with an imperative verb when telling users what to do: "Add your first item…"
- Do NOT use permissive language like "you can"
- ✅ "Add your first item and see how it looks in the list."
- 🚫 "You can add your first item so you can see how it looks."

### Buttons
- Lead with a strong verb
- Formula: {verb} + {noun} — "Add secret", "Upload photo", "Start quick launch"
- Common actions are exceptions: "Done", "Close", "Cancel", "OK"
- Sentence case, no period
- ✅ "Add action" 🚫 "Add Action" or "Upload a photo"

### Links
- Describe where the user will go or what they'll see
- Never use "click here" or "here" as link text
- In sentences: link only the descriptive text, not the whole sentence
- Outside sentences: use {verb + noun} pattern — "Learn more", "View details"
- No trailing punctuation (except question marks when needed)
- ✅ "Get started with our guide to Nextflow."
- 🚫 "Want to learn more about Nextflow? Click here."

### Dropdown Menus
- Actions follow {verb} + {noun} pattern
- If context is clear, verb alone is fine
- ✅ "Rename", "Duplicate" 🚫 "Duplicate this order so that you can make edits"

### Lists
- Introduce with a colon or heading
- Each item starts with a capital letter
- If any item has 2+ sentences, punctuate all items; otherwise no punctuation
- No commas or semicolons at the end of list items
- Consistent tense and structure across all items

### Error / Alert Messages
- State: "No [items] are [verb in past tense] yet." e.g., "No pipelines are configured yet."
- Item available but unused: "No [item] in use."
- Search result: "No [item] found."
- Unavailable: "No [item] available."
- Error: be specific and plain — "Sign-in error: You entered an incorrect password"
- 🚫 "System error (code: #1235): An authentication error has occurred"

### Confirmations
- Title: concise {verb} + {noun} question, sentence case, question mark only, no articles
  - ✅ "Delete workflow?" 🚫 "Are you sure you want to delete the workflow?"
- Body: one line, plain language; clearly state if irreversible. Don't start with "Are you sure?"
- Buttons: one-word CTAs are fine in context — "Cancel" / "Delete"
- Always give option to confirm or cancel

### Tooltips
- Short, no period
- Sentence case

### Placeholder Copy
- No ellipses ("Search files" not "Start typing to search for files…")
- No period

### Empty States
- Explain what's missing and what the user can do
- Start with an imperative verb or a brief description

---

## Output Format

Provide the UI copy for each component requested. For reviews, list issues and fixes using:

**Issue**: [quote]
**Rule**: [rule violated]
**Fix**: [corrected copy]
