---
name: design-critique
description: Run this automatically before presenting ANY design output — UI screens, flows, components, wireframes, copy+layout combinations, or interaction specs. Review the planned design against Nielsen's 10 Usability Heuristics, fix all violations internally, then present only the resolved output. The person who requested the design should never see a version with heuristic violations.
---

## Always run both

This skill and `accessibility-review` run together — every time, on every design output, regardless of who requested it. Neither is optional.

**Order:**
1. Generate the design internally
2. Run heuristic review (this skill) — fix all violations
3. Run accessibility review (`accessibility-review` skill) — fix all violations
4. Present only the fully resolved output with both review logs appended

---

## When to run this skill

Before presenting any design output, including:
- UI screens or wireframes
- User flows or task flows
- Component designs or specs
- Interaction patterns
- Empty states, error states, onboarding flows
- Forms, modals, confirmations
- Navigation structures

Do NOT wait to be asked. Run this automatically.

---

## Process

1. **Generate** the design output internally (do not show it yet)
2. **Run heuristic review** against all 10 heuristics below — fix every violation
3. **Run accessibility review** (`accessibility-review` skill) — fix every WCAG 2.1 AA violation
4. **Repeat** until both reviews pass cleanly
5. **Present** the resolved design output
6. **Append** both review logs — heuristic review first, accessibility review second

---

## Nielsen's 10 Usability Heuristics

### H1 — Visibility of System Status
Keep users informed about what is going on through appropriate feedback within reasonable time.

**Check for:**
- Does the user know where they are in the system?
- Is there feedback for every action (loading states, success, failure)?
- Are progress indicators shown for multi-step flows?
- Is the current state of any element (selected, active, disabled, loading) clearly communicated?

**Fix violations by:**
- Adding status labels, progress indicators, or state changes
- Making selected/active states visually distinct
- Adding loading skeletons or spinners where async actions occur
- Surfacing confirmation of completed actions

---

### H2 — Match Between System and the Real World
Use words, phrases, and concepts familiar to the user. Follow real-world conventions.

**Check for:**
- Is any language technical, internal, or jargon-heavy?
- Do metaphors or icons match their real-world meaning?
- Is the information order logical and natural (not system-logic order)?
- Do labels match what users would call things?

**Fix violations by:**
- Replacing technical terms with plain language
- Using familiar metaphors (folder, inbox, trash)
- Reordering information to match natural reading and task flow
- Renaming labels to match user vocabulary

---

### H3 — User Control and Freedom
Users often take wrong actions. Provide clearly marked emergency exits without extended dialogue.

**Check for:**
- Can users undo or redo actions?
- Is there a clear way to cancel or exit every flow?
- Are destructive actions reversible, or at least confirmed?
- Can users recover from mistakes without losing their work?

**Fix violations by:**
- Adding undo/redo where relevant
- Adding cancel buttons to every modal, form, and multi-step flow
- Moving destructive actions away from common actions
- Adding confirmation dialogs for irreversible actions
- Auto-saving where appropriate

---

### H4 — Consistency and Standards
Users should not have to wonder whether different words, situations, or actions mean the same thing. Follow platform conventions.

**Check for:**
- Are the same actions labeled consistently throughout?
- Do similar components behave the same way everywhere?
- Does the design follow platform conventions (e.g. primary button on the right)?
- Are visual patterns consistent (same spacing, same hierarchy for similar content)?

**Fix violations by:**
- Aligning labels across all instances of the same action
- Making similar components behave identically
- Correcting deviations from established platform or design system patterns
- Fixing visual inconsistencies in spacing, color, or hierarchy

---

### H5 — Error Prevention
Design carefully to prevent problems from occurring in the first place.

**Check for:**
- Can users submit invalid data without warning?
- Are irreversible or high-risk actions too easy to trigger?
- Are there ambiguous options that could lead to the wrong choice?
- Are required fields, formats, or constraints clearly communicated upfront?

**Fix violations by:**
- Adding inline validation before submission
- Showing format hints on form fields (e.g. "DD/MM/YYYY")
- Moving destructive actions behind confirmation or requiring deliberate input
- Disabling actions that aren't yet valid rather than letting them fail
- Distinguishing between similar options visually and in copy

---

### H6 — Recognition Rather Than Recall
Minimize memory load. Make objects, actions, and options visible. Users should not have to remember information from one part to use in another.

**Check for:**
- Do users need to remember information from a previous screen to proceed?
- Are actions and options visible rather than hidden in menus or requiring recall?
- Are recently used items, defaults, or suggestions surfaced?
- Do forms and flows pre-fill known information?

**Fix violations by:**
- Surfacing relevant context inline (e.g. showing the item being deleted in the confirmation)
- Adding visible labels to icons
- Pre-filling known user data in forms
- Showing breadcrumbs or step summaries in multi-step flows
- Making options visible rather than requiring users to remember commands

---

### H7 — Flexibility and Efficiency of Use
Allow accelerators for expert users while keeping the interface accessible for novices.

**Check for:**
- Is the flow optimised for first-time users only, ignoring frequent users?
- Are there keyboard shortcuts or quick actions for power users?
- Can frequent tasks be reached in fewer steps?
- Are defaults set to the most common use case?

**Fix violations by:**
- Setting smart defaults that work for most users
- Offering shortcuts for frequent actions without cluttering the main UI
- Reducing steps for common tasks
- Adding bulk actions where users regularly act on multiple items

---

### H8 — Aesthetic and Minimalist Design
Interfaces should not contain irrelevant or rarely needed information. Every extra unit of information competes with relevant information.

**Check for:**
- Is any element present that doesn't serve the current task?
- Is there visual noise — unnecessary decoration, too many competing elements?
- Is the hierarchy clear — does the most important thing feel most important?
- Is any copy redundant or overly explained?

**Fix violations by:**
- Removing decorative elements that don't carry meaning
- Reducing the number of competing calls to action
- Simplifying copy — cut anything that doesn't add information
- Using visual weight to establish clear hierarchy
- Moving secondary information to progressive disclosure (tooltips, expandable sections)

---

### H9 — Help Users Recognize, Diagnose, and Recover from Errors
Error messages should be expressed in plain language, precisely indicate the problem, and constructively suggest a solution.

**Check for:**
- Are error messages written in plain language (not error codes)?
- Do they explain what went wrong?
- Do they tell the user what to do next?
- Are errors shown close to where the problem occurred?

**Fix violations by:**
- Rewriting error messages: [what happened] + [why] + [what to do]
  - ✅ "Incorrect password. Check your password and try again, or reset it."
  - 🚫 "Authentication error (code 401)"
- Moving error messages inline, next to the relevant field
- Adding recovery actions directly in the error state (e.g. "Reset password" button)
- Using appropriate visual severity (warning vs. error vs. info)

---

### H10 — Help and Documentation
Even though it's better if the system can be used without documentation, it may be necessary to provide help. Such information should be easy to search, focused on the task, list concrete steps, and not be too large.

**Check for:**
- Are complex features or first-time experiences self-explanatory?
- Is help available in context (tooltips, inline hints) rather than only in a separate help centre?
- Are empty states instructional — do they tell users what to do first?
- Is onboarding provided for new users or new features?

**Fix violations by:**
- Adding inline help text or tooltips to complex inputs
- Making empty states instructional ("No pipelines yet. Create your first pipeline.")
- Adding onboarding hints or coach marks for new workflows
- Linking to documentation contextually, not just globally

---

## Output Format

Present the final, resolved design first. Then append:

---
**Heuristic Review**

| # | Heuristic | Finding | Fix applied |
|---|---|---|---|
| H1 | Visibility of system status | [what was missing] | [what was added] |
| H4 | Consistency and standards | [what was inconsistent] | [how it was resolved] |

Only list heuristics where violations were found. If none were found for a heuristic, omit it.
If no violations were found at all, write: "No heuristic violations found."
