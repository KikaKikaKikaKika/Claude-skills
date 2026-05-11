# Tree Testing Template

Use for: validating a navigation structure before building it, testing whether users can find things in a proposed IA, comparing two navigation structures.
Not suitable for: designing IA from scratch (use card sorting first), understanding why users navigate the way they do, testing visual design or labels in context (use usability testing).

---

## What it is

Tree testing presents participants with a text-only hierarchy (the "tree") and asks them to find specific items. Because there's no visual design — just the structure — it isolates IA problems from visual or label problems. If users can't find things in a tree test, your structure is the issue.

Run after card sorting. Run before building navigation. Run again if you make major IA changes.

---

## Header

**Research goal:** [What navigation or findability question are you answering?]
**Tree:** [The navigation structure being tested — attach or describe]
**Tasks:** [3–10 findability tasks]
**Participants:** [Recruitment criteria] — 50+ for reliable quantitative data; minimum 20
**Method:** [Remote unmoderated — Optimal Workshop Treejack, UXtweak, or equivalent]
**Estimated time:** 10–20 minutes per participant

---

## Building the Tree

The tree should reflect your proposed navigation structure — exactly as you plan to build it. Text only: category names and subcategory names, no descriptions or icons.

**Rules:**
- Use the labels you actually plan to use — this tests labels, not just structure
- Include all top-level categories and at least 2–3 levels of depth
- Don't include "everything" — a tree with 200 nodes is too long. Focus on the sections relevant to your tasks.
- Make sure the correct answer exists somewhere in the tree before writing a task around it

---

## Writing Tasks

Tasks should represent real goals users have — not echo the navigation labels.

**Good task:** "You want to change what email address your account notifications are sent to. Where would you go?"
**Bad task:** "Find the notification settings." — uses the nav label, which makes it a vocabulary test not a findability test.

**Task writing rules:**
- Write in plain language from the user's perspective
- Never use words from the tree labels in the task — that's a hint
- One clear goal per task
- Include a realistic scenario where it helps
- Confirm the correct destination before launching

**Task answer:**
For each task, define the correct destination in the tree. Some tasks may have more than one valid answer — mark all acceptable paths.

| Task | Correct destination(s) |
|---|---|
| Task 1 | [Path: Top level > Category > Item] |
| Task 2 | |

---

## Running the Study (Unmoderated)

**Intro screen copy:**
> "In this study, you'll see a list of categories — like a site map — and be asked to find specific things within it. The categories don't have any visual design — just text. Click through the levels to find where you'd go to complete each task, then click 'I'd find it here' when you land on your answer."

> "Take your time. There are no right or wrong answers — we're testing the structure, not you."

**Post-task question (optional, per task):**
- "How confident were you in your answer?" — 1–5 scale
- "Was there anywhere else you considered going?" — open text

**Post-study question:**
- "Was there anything confusing or missing in the navigation structure?"

---

## Metrics

For each task, tree testing tools automatically calculate:

| Metric | What it means | Target |
|---|---|---|
| **Success rate** | % who landed on the correct destination | >70% = good; <50% = problem |
| **Directness** | % who took a direct path (no backtracking) | Higher = clearer structure |
| **Time on task** | Average time to complete | Relative — compare across tasks |
| **First click** | Where participants went first | High agreement = good labelling |

**Overall IA health:**
- >70% success across all tasks: structure is solid
- 50–70%: several findability problems, worth redesigning before build
- <50%: structural problems — revisit the IA, consider re-running card sorting

---

## Analysis Notes

**Task-level analysis:**
For each failed task, look at:
- Where people ended up instead (wrong destination patterns)
- Where they entered the wrong branch (first-click errors reveal label problems)
- Whether they backtracked (hesitation and recovery — structure is ambiguous)

**Destination maps:**
Most tools provide a visualisation of where participants ended up. Items spread across many wrong destinations = confusing label. Items concentrated in one wrong destination = users have a different mental model of where this belongs.

**Fixing failures:**
- High first-click errors on a specific top-level category → rename the category
- Items consistently placed in the wrong subcategory → move or cross-link
- High backtracking on a specific path → the deeper labels are misleading

**What to present to stakeholders:**
- Success rate per task (clear, hard to argue with)
- The 2–3 tasks with the worst performance — show the destination map
- Proposed changes to labels or structure based on findings
- Before/after if you're validating a redesign

**What tree testing will NOT tell you:**
- Whether the visual design of navigation works (use usability testing)
- How users conceptualise the content (use card sorting)
- Whether users can complete a full workflow (use usability testing)
