# Usability Test Plan Template

Use for: validating whether users can complete tasks, finding friction in a flow, testing a prototype or live product.
Not suitable for: understanding why users behave a certain way — use interview-guide.md for that.

---

## Moderated vs Unmoderated

| | Moderated | Unmoderated |
|---|---|---|
| **When to use** | Complex flows, early prototypes, need to probe "why" | Simple tasks, later-stage designs, need scale or speed |
| **Time to run** | 1–2 weeks | 2–3 days |
| **Participants** | 5–8 | 15–30 |
| **Tools** | Zoom + Figma / staging | Maze, Lookback, UserTesting |
| **Output** | Rich qualitative insight + task data | Task completion rates, time-on-task, click paths |

If you're unsure, start moderated. You can always run unmoderated at scale after.

---

## Header

**Research goal:** [What usability question are we answering?]
**Method:** [Moderated / Unmoderated] usability test
**Prototype / URL:** [Link]
**Participants:** [Role / type / recruitment criteria] — 5–8 for moderated, 15–30 for unmoderated
**Session length:** [45–60 min for moderated / 15–20 min for unmoderated]
**Facilitator:** [Name]
**Observer(s):** [Names — observers should stay silent and take notes]
**Recording:** Yes — [state consent approach]

---

## Research Questions

List 2–4 specific questions this test will answer. These are not tasks — they're the questions that drive the task design.

Example:
- Can users find the [feature] without guidance?
- Do users understand what [element] does before clicking it?
- Where do users get stuck in the [flow]?
- Does the [copy / label / CTA] set the right expectations?

---

## Tasks

Write 3–5 tasks. Each task should:
- Reflect a realistic scenario the user would actually be in
- Not contain the answer (don't use the exact label from the UI)
- Have a clear success state you can observe
- Be written as a scenario, not an instruction

**Task format:**
> Scenario: [Set the context in 1–2 sentences]
> Task: [What you want them to do — written as a goal, not a step]

**Example:**
> Scenario: You've just joined the platform and want to connect your first data source.
> Task: Go ahead and do that.

**Success criteria per task:**
| Task | Success state | Failure state | Time limit |
|---|---|---|---|
| Task 1 | | | |
| Task 2 | | | |

---

## Moderator Script (moderated only)

### Opening (5 min)

> "Thanks for joining. A few things before we start — we're testing the design, not you. There are no wrong answers. If something doesn't make sense, that's useful feedback for us. Please think out loud as you work — tell me what you're looking at, what you're thinking, what you're expecting to happen. I won't be able to answer questions during the tasks, but I'll ask for your thoughts after. Is it OK if I record this session?"

> "Before we look at anything — can you tell me a little about your role and how you typically [relevant context]?"

### Transition to tasks

> "I'm going to give you a series of scenarios. Take your time. If you get stuck, just tell me what you're thinking — don't worry about finding the 'right' answer."

### During tasks — probing prompts

- "What are you thinking right now?"
- "What would you expect to happen if you clicked that?"
- "What are you looking for?"
- "If this were real, what would you do next?"
- "On a scale of 1–5, how confident did you feel completing that task?"

Do NOT: answer questions about the UI, confirm or deny actions, or show reactions to errors.

### After each task

- "How did that feel?"
- "Was anything unclear or unexpected?"
- "Is this what you expected?"

### Close (5 min)

- "Overall, what was your impression?"
- "What was the most confusing part?"
- "What worked well?"
- "Anything else you want to share?"

---

## Observation Notes Template

During sessions, note-takers should capture:

| Participant | Task | Completed? | Time | Errors / hesitations | Quotes | Severity |
|---|---|---|---|---|---|---|
| P1 | Task 1 | Y / N / Partial | | | | 1–4 |

**Severity scale:**
- 1 — Minor: slight hesitation, recovers immediately
- 2 — Moderate: confusion, takes longer than expected
- 3 — Serious: significant struggle, needs help or gives up temporarily
- 4 — Critical: cannot complete, abandons task

---

## Analysis Notes

**After each session (immediately):**
- What was the biggest surprise?
- Which task had the most friction?
- Any quotes worth preserving verbatim?

**After all sessions:**
- Task completion rates: [# who completed] / [# who attempted]
- Common failure points: where did multiple participants get stuck?
- Severity map: what's critical to fix before launch vs. nice to have?

**What to present to stakeholders:**
- Lead with task completion rates — they're concrete and hard to argue with
- Show video clips of critical failures (60–90 seconds max)
- Prioritise findings by severity, not by frequency alone
- A single participant hitting a critical blocker is worth fixing even if others didn't

**What usability tests will NOT tell you:**
- Why users have certain expectations (use interviews)
- How many users in the real world are affected (use analytics or surveys)
- Which of two designs is strategically better (use a different framework)
