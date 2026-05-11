---
name: design-system
description: Design system skill for Head of Design. Two modes — Build (no DS exists yet) and Evolve (DS exists, needs audit or expansion). Covers token architecture, component library structure, documentation, Figma setup, and contribution governance. Run Build Mode to create a design system from scratch; run Evolve Mode to audit coverage, catch drift, and plan what's next.
disable-model-invocation: true
allowed-tools: Read, Write, Bash, WebFetch, mcp__claude_ai_Figma__get_metadata, mcp__claude_ai_Figma__get_design_context, mcp__claude_ai_Figma__use_figma, mcp__claude_ai_Figma__create_new_file, mcp__claude_ai_Figma__get_variable_defs, mcp__claude_ai_Figma__get_libraries
---

# Design System Skill

## Mode Detection

Determine the mode from context or ask:

> "Do you have an existing design system, or are we building one from scratch?"

- **No DS exists** → Stage 1: Build Mode
- **DS exists** → Stage 2: Evolve Mode

---

## Stage 1 — Build Mode

Use when there is no design system yet. The goal is to establish a foundation that is complete enough to use immediately, without over-engineering before you have real usage patterns.

### What to collect before starting

Ask for any of these not already provided:

- Brand guide or visual style guide (if one exists — fetch from GitHub if linked)
- Existing product files in Figma (to extract what's already in use)
- Product type: web app / marketing site / mobile / multi-platform
- Team size and contribution model: solo, small team, or open contribution
- Any component framework already in use (React, Vue, etc.)

If a visual style guide skill is available, run it first to lock in brand colours, typography, and spacing before building tokens.

---

### Step 1.1 — Token Architecture

Define the token layers before creating components. Tokens are the foundation everything else inherits from.

**Three layers:**

```
Primitive tokens      →  Raw values. Never used directly in components.
                         color/blue/500: #3B82F6
                         spacing/4: 16px

Semantic tokens       →  Intent-mapped aliases of primitives.
                         color/action/primary: → color/blue/500
                         spacing/component/gap: → spacing/4

Component tokens      →  Component-specific overrides (use sparingly).
                         button/padding/horizontal: → spacing/component/gap
```

**Required token categories for a complete foundation:**

| Category | Required | What to define |
|---|---|---|
| Color | Yes | Brand, semantic (action, success, warning, error, neutral), surface, text, border |
| Typography | Yes | Font families, size scale, line height, weight, letter spacing |
| Spacing | Yes | Base unit (8px default), scale steps (2, 4, 8, 12, 16, 24, 32, 48, 64) |
| Border radius | Yes | None, sm, md, lg, full |
| Elevation / shadow | Yes | 0–4 levels |
| Motion | Yes | Duration (instant, fast, normal, slow), easing curves |
| Z-index | Yes | Named layers: base, overlay, modal, toast |
| Breakpoints | If web | sm, md, lg, xl, 2xl |

**Output format:** Document each token as a table with path, value, and usage note.

---

### Step 1.2 — Component Prioritisation

Do not build every component. Build what the product needs now.

**Tier 1 — Always build first (universal primitives):**
- Button (primary, secondary, ghost, destructive + sizes + states)
- Input (text, with label, error state, disabled)
- Typography (heading scale H1–H4, body, caption, label)
- Icon system (sizing, naming convention, accessible usage)
- Color swatches (semantic palette documentation)

**Tier 2 — Build once the product shape is clear:**
- Form elements: checkbox, radio, select, textarea, toggle
- Feedback: toast/snackbar, alert/banner, badge, tooltip
- Navigation: tabs, breadcrumb, pagination, sidebar
- Overlay: modal, drawer, popover
- Data: table, card, list item

**Tier 3 — Build on demand:**
- Complex patterns: data tables with sorting, multi-step forms, date pickers
- Charts and data visualisation
- Onboarding flows

For each Tier 1 component, define:
- All interactive states: default, hover, active, focus, disabled, loading
- All size variants
- All semantic variants (e.g. button: primary / secondary / ghost / destructive)
- Accessibility requirements (ARIA role, keyboard behaviour, focus style)

---

### Step 1.3 — Figma File Structure

Create a Figma file using `mcp__claude_ai_Figma__create_new_file` named **Design System**.

Recommended page structure:

```
_Cover             — Title, version, last updated date
_Changelog         — Running log of changes
Foundations        — Tokens: color, typography, spacing, etc.
Components         — All components with all variants
Patterns           — Composed patterns (forms, empty states, etc.)
Icons              — Icon library
[Do not use]       — Deprecated components, kept for reference
```

Within each component frame, use Figma's component properties (variants, boolean props, text props) so consumers can configure without detaching.

---

### Step 1.4 — Documentation Requirements

Each component must be documented with:

1. **Usage** — What it's for. When to use it vs. alternatives.
2. **Variants** — Every variant shown visually with labels.
3. **States** — Default, hover, active, focus, disabled, loading, error.
4. **Anatomy** — Labelled diagram of the component parts.
5. **Specs** — Token references for all visual properties.
6. **Accessibility** — Keyboard interaction, ARIA, focus behaviour.
7. **Do / Don't** — At least one clear misuse example.

Tokens must be documented with:
- Token path
- Value (or alias target)
- Usage note
- Do not use directly / use semantic alias note where applicable

---

### Step 1.5 — Contribution Governance

Define how designers (and engineers) can propose additions before the system is shipped.

**Minimum governance for a small team:**

```
PROPOSE     →  File a component proposal (use component-proposal skill if available)
REVIEW      →  Head of Design reviews: does it belong in the DS or stay local?
BUILD       →  Approved proposals built to DS standards
PUBLISH     →  Published to library with changelog entry
DEPRECATE   →  Old versions kept in [Do not use] page for one release cycle
```

**Criteria for something going into the DS:**

- Used in 3 or more product contexts, OR
- Likely to be needed in 3 or more contexts, AND
- Can be made generic without losing its usefulness

If it only works in one context — keep it local.

---

### Step 1.6 — Build Mode Output

After completing Steps 1.1–1.5, produce:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DESIGN SYSTEM FOUNDATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Status:       Foundation draft complete
Figma file:   [URL]
Created:      [Date]

TOKEN SUMMARY
━━━━━━━━━━━━━
[Table: Category | Token count | Notes]

COMPONENT ROADMAP
━━━━━━━━━━━━━━━━━
Tier 1 (build now):  [list]
Tier 2 (next):       [list]
Tier 3 (backlog):    [list]

WHAT'S MISSING
━━━━━━━━━━━━━━
[Honest list of what was skipped and why, with recommendation to revisit]

NEXT STEPS
━━━━━━━━━━
1. [First action — usually: publish Figma library and connect to product files]
2. ...
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Stage 2 — Evolve Mode

Use when a design system already exists. Evolve Mode audits what's there, surfaces gaps and drift, and produces a prioritised action plan.

Read [references/audit-format.md](references/audit-format.md) before producing any audit output.

---

### Step 2.1 — Access Check

Before auditing, confirm access:

1. Use `mcp__claude_ai_Figma__get_metadata` to verify the DS Figma file is accessible
2. Use `mcp__claude_ai_Figma__get_libraries` to list connected libraries
3. Use `mcp__claude_ai_Figma__get_variable_defs` to extract defined tokens
4. Ask: "Do you have product file URLs to include in the drift check?"

If product files are not provided, proceed with DS-only scope and flag the limitation per the audit format.

---

### Step 2.2 — Run the Audit

Using `mcp__claude_ai_Figma__get_design_context` on the DS file and any product files provided, produce a full audit per [references/audit-format.md](references/audit-format.md):

- Section 1: Coverage Summary
- Section 2: Drift Report
- Section 3: Orphan Report
- Section 4: Gap Report
- Prioritised action list

---

### Step 2.3 — Expansion Planning

After the audit, if the Head of Design asks "what should we add next" or "what's missing":

1. Pull the gap report from the audit
2. Cross-reference against Tier 2 and Tier 3 component lists from Build Mode
3. Score each gap: frequency of manual workarounds × effort to build properly
4. Recommend the top 3 additions with rationale

---

### Step 2.4 — Version and Changelog

When changes are made to the DS:

- Every published change gets a changelog entry: what changed, why, migration note if breaking
- Breaking changes are flagged at the top of the changelog page in Figma
- Deprecated components stay in `[Do not use]` for one release cycle before removal

---

## Edge Cases

- **No Figma access**: Proceed with documentation and token architecture in text form. Note that Figma file creation will need to be done manually.
- **No brand guide**: Ask for primary colour, preferred font, and product type. Build a minimal token set from answers. Flag that a brand guide should be created (use visual-style-guide skill).
- **Existing Figma library with no tokens**: Audit the library for hardcoded values and produce a token extraction plan before building the DS.
- **Engineer asks about code tokens**: Note that design tokens should be exported as JSON and consumed via Style Dictionary or equivalent. This skill covers the design side — recommend coordinating with engineering on the export pipeline.
