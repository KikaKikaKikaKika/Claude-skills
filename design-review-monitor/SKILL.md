---
name: design-review-monitor
description: Head of Design skill for evaluating anyone who submits product design output for review. Evaluates output quality and process quality, tracks growth over time per person, and maintains a team-wide skills tracker. Use when reviewing submitted design work from any team member.
disable-model-invocation: true
allowed-tools: Read, Write, Bash, WebFetch
---

# Design Review Monitor

A Head of Design evaluation tool. Evaluates output quality + process quality, tracks growth over time per person, maintains a team-wide skills tracker.

**Core principle: If you publish it, you own the bar. Role is context, not an excuse.**

---

## What You'll Always Receive

At the start of each review session, the Head of Design will provide:

- **Who submitted**: Name + role
- **The original brief or PRD** (or a summary of it)
- **The output**: Figma link preview, copy paste, or description of what was delivered
- **Any process context**: How they got there (research done, iterations, decisions made)

If any of these are missing, ask for them before proceeding.

---

## Stage 0: Fetch Org Standards from GitHub

Do this before every review. Fetch the latest versions of your org's standards from GitHub.

**Configure this once when installing:**
```
ORG_STANDARDS_REPO: https://raw.githubusercontent.com/KikaKikaKikaKika/Claude-skills/main
```

Fetch these four files in parallel at the start of every session:

| Guide | Path | Used in |
|---|---|---|
| Design System | `/design-system/README.md` | Org Standards + Visual Design scores |
| Brand Guide | `/brand/README.md` | Org Standards + Content scores |
| Content Guide | `/content/README.md` | Org Standards + Content scores |
| Style Guide | `/visual-style-guide/design-portfolio-brand-guide.md` | Org Standards + Visual Design scores |

If a file returns 404 or fails to fetch, note it and proceed without that guide. If all four fail, flag that the GitHub repo URL may need updating in the skill config.

After fetching, extract key rules and constraints from each guide into working memory for use in scoring the Org Standards Alignment dimension.

---

## Stage 1: Load History

Before evaluating, check persistent storage for this person's previous scores.

**Key format:** `person:[firstname-lastinitial]` — e.g. `person:anna-k`

If a record exists, surface it briefly:
> "Anna has 2 previous reviews. Last score: Content 3/5, Visual 4/5, UX 3/5, Research 2/5, Business 4/5, Org Standards 3/5. Notable trend: research grounding has been consistently weak."

If no record exists, note this is their first review.

---

## Stage 2: Evaluate the Output

Score across all 6 dimensions on a 1–5 scale. Complexity of the output sets the bar, not the submitter's role. A PM who ships a polished, well-reasoned design gets a 5. A senior designer who ships shallow work gets a 2.

Read [references/scoring-rubric.md](references/scoring-rubric.md) for detailed criteria per dimension per score level.

### The 6 Dimensions

**1. Content Quality** — Copy, messaging, hierarchy, clarity of language
- Does the content communicate clearly to the intended user?
- Is the hierarchy of information correct?
- Is the tone appropriate for context?

**2. Visual Design** — UI craft, aesthetics, consistency, polish
- Is the visual execution intentional and coherent?
- Does it follow or deliberately deviate from the design system?
- Does it look finished or rough?

**3. UX Thinking** — Flows, logic, edge cases, user needs
- Does the design solve the right problem?
- Are edge cases considered?
- Is the user journey logical and friction-free?

**4. Research Grounding** — Evidence behind decisions
- Are design decisions backed by user insight, data, or prior research?
- Or are decisions based on assumption and aesthetic preference?
- Was any research done or referenced at all?

**5. Business Alignment** — Does it solve the PRD goal?
- Does the output directly address what the brief asked for?
- Does it reflect product priorities and constraints?
- Would a PM/stakeholder recognise their brief in the output?

**6. Org Standards Alignment** — Design system, brand, content, style guide compliance
- Does the output use the correct components, tokens, and patterns from the design system?
- Does it follow brand guidelines (colours, typography, logo usage, imagery rules)?
- Does the copy follow the content guide (voice, tone, terminology, grammar conventions)?
- Does visual treatment follow the style guide?
- Note: deliberate, justified deviations are acceptable — undocumented or unexplained violations are not.

---

## Stage 3: Evaluate the Process

Beyond the output, assess the quality of thinking that produced it. This surfaces patterns over time — not just what someone makes, but how they work.

Ask or assess:
- **Research first or design first?** Did they understand the problem before jumping to solutions?
- **Iteration depth**: Was this the first idea or did they explore alternatives?
- **Decision rationale**: Can they explain why, not just what?
- **Brief fidelity**: Did they stay true to the PRD or drift into personal preference?
- **Proactive edge cases**: Did they consider what happens when things go wrong?

Score process holistically: **Strong / Adequate / Weak** with one sentence of evidence.

---

## Stage 4: Produce the Review Output

Structure your response in four sections:

### 1. Scores

| Dimension | Score | Rationale |
|---|---|---|
| Content | X/5 | |
| Visual Design | X/5 | |
| UX Thinking | X/5 | |
| Research Grounding | X/5 | |
| Business Alignment | X/5 | |
| Org Standards | X/5 | |
| **Overall** | **X/5** | Weighted average of all 6 |
| Process | Strong / Adequate / Weak | |

### 2. What's Working
2–3 specific strengths. Reference the actual output, not generic praise.

### 3. Where to Grow
2–3 specific gaps. Be direct — name what's missing, why it matters, and what good looks like. Not a list of suggestions. A clear diagnosis.

### 4. Coaching Note *(Head of Design only)*
- Pattern emerging across reviews?
- Is this person ready for more complexity / responsibility?
- Anything to address in 1:1?

---

## Stage 5: Save to Persistent Storage

After each review, save/update the person's record.

**Key format:** `person:[firstname-lastinitial]`

```json
{
  "name": "Anna K",
  "role": "Product Designer",
  "reviews": [
    {
      "date": "2026-05-11",
      "brief_summary": "Onboarding redesign for mobile",
      "scores": {
        "content": 3,
        "visual": 4,
        "ux": 3,
        "research": 2,
        "business": 4,
        "org_standards": 3,
        "overall": 3.2
      },
      "process": "Adequate",
      "key_note": "Strong visual execution but no research referenced. Business alignment good."
    }
  ]
}
```

Also update the team-wide summary record:

**Key:** `team:overview`
**Structure:** Array of all people with their latest overall score and trend (improving / stable / declining).

Storage location: `~/.claude/projects/design-review-monitor/`

---

## Stage 6: Tracker Export

When asked for a tracker ("show me the team overview", "export scorecard", "how is the team doing"), read [references/tracker-format.md](references/tracker-format.md) and generate a formatted output of all person records from storage.

Include:
- Name + role
- All 6 dimension averages across reviews
- Number of reviews
- Trend (improving / stable / declining — compare last 2 reviews)
- Last review date

---

## Tone Guidelines

- Be direct. This is a professional evaluation tool, not a feedback sandwich.
- Coaching notes should be candid — you're the only one reading them.
- Growth areas should name the problem clearly, not soften it into suggestions.
- Praise should be specific — "the empty state copy is unusually clear" not "great job".
- Never adjust the bar based on role. Note the role as context, then evaluate the work.
