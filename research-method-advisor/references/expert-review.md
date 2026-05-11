# Expert Review Template

Use for: identifying usability problems quickly without users, evaluating a design when you have no time or access for user research, auditing an existing product for known issues, supplementing (not replacing) user research.
Not suitable for: replacing user testing, understanding user mental models, validating behaviour.

---

## What it is

An expert review (also called a heuristic evaluation or cognitive walkthrough) is a structured evaluation of a design by someone with UX expertise — without users. It uses established principles to systematically identify usability problems.

Two main types:
- **Heuristic evaluation**: evaluator reviews the design against a set of usability heuristics (e.g. Nielsen's 10) and flags violations
- **Cognitive walkthrough**: evaluator steps through specific tasks as if they were a new user, asking four questions at each step

Use heuristic evaluation for broad coverage. Use cognitive walkthrough for specific task flows, especially onboarding and first-use.

---

## Header

**Design being reviewed:** [Product / feature / flow]
**Method:** [Heuristic evaluation / Cognitive walkthrough / Both]
**Evaluator(s):** [Name — multiple evaluators find more issues; 3–5 is ideal]
**Heuristics used:** Nielsen's 10 (default) or [specify alternative]
**Tasks for walkthrough:** [List 2–5 tasks if doing cognitive walkthrough]
**Estimated time:** 1–3 hours per evaluator depending on scope

---

## Heuristic Evaluation

For each screen or flow, evaluate against Nielsen's 10 heuristics. Flag each violation with a severity rating.

### The 10 Heuristics (Nielsen)

1. **Visibility of system status** — Does the user always know what's happening?
2. **Match between system and the real world** — Does it use language and concepts familiar to users?
3. **User control and freedom** — Can users undo mistakes and exit flows easily?
4. **Consistency and standards** — Are conventions followed consistently?
5. **Error prevention** — Does the design prevent errors before they happen?
6. **Recognition rather than recall** — Does the design minimise memory load?
7. **Flexibility and efficiency of use** — Does it work for both novice and expert users?
8. **Aesthetic and minimalist design** — Is every element necessary?
9. **Help users recognise, diagnose, and recover from errors** — Are error messages clear and actionable?
10. **Help and documentation** — Is help available when needed?

### Issue Log

For each issue found:

| # | Location | Heuristic | Description | Severity | Recommendation |
|---|---|---|---|---|---|
| 1 | [Screen / flow / element] | H1 | [What the issue is] | 1–4 | [What to do] |

**Severity scale:**
- 1 — Cosmetic: minor issue, fix if time allows
- 2 — Minor: causes slight confusion, low priority
- 3 — Major: causes significant usability problems, high priority
- 4 — Catastrophic: prevents task completion or causes errors, fix before launch

---

## Cognitive Walkthrough

Step through each task as a new user. At each interaction point, ask four questions:

1. **Will users try to achieve the right effect?** (Will they know what to do at this point?)
2. **Will users notice the correct action is available?** (Is the right control visible and identifiable?)
3. **Will users associate the correct action with the effect they want?** (Does the label/icon match their expectation?)
4. **Will users know the system has progressed correctly?** (Is there clear feedback after the action?)

If the answer to any question is "no" or "maybe not" — log an issue.

### Task Walkthrough Log

**Task:** [User's goal — written as the user would express it]
**Starting point:** [Screen / state the user starts from]

| Step | Action | Q1 | Q2 | Q3 | Q4 | Issue |
|---|---|---|---|---|---|---|
| 1 | [What the user must do] | ✅/⚠️/❌ | ✅/⚠️/❌ | ✅/⚠️/❌ | ✅/⚠️/❌ | [Description if issue] |

---

## Aggregating Findings (Multiple Evaluators)

If running with multiple evaluators:
1. Each evaluator works independently — don't discuss until all reviews are done
2. Combine issue lists and remove duplicates
3. Re-rate severity as a group — use the most severe rating when evaluators disagree
4. Issues found by 3+ evaluators are your highest priority

---

## Analysis Notes

**Prioritise by:**
- Severity 4 issues: fix before launch, no exceptions
- Severity 3 issues: fix before launch if possible; schedule if not
- Severity 2 issues: schedule for next sprint
- Severity 1 issues: backlog

**What to present to stakeholders:**
- Total issue count by severity (gives a quick health signal)
- Top 5 most critical issues with screenshots and recommendations
- Quick wins: low-effort severity 2 issues that can be fixed immediately
- Note what the expert review cannot confirm — recommend follow-up user testing for severity 3–4 issues

**Important caveat — always include this:**
An expert review identifies potential problems based on heuristic principles. It does not replace user testing. Some flagged issues may not bother real users; some issues not flagged here may be serious in practice. Use expert review to prioritise, then validate critical fixes with users.

**What expert review will NOT tell you:**
- How real users actually experience the product
- Whether problems are as severe in practice as they appear in review
- What users expect or want (use interviews for that)
