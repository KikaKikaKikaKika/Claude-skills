---
name: research-method-advisor
description: >
  Use this skill whenever a designer or researcher describes a design problem, product challenge, or research question and wants help choosing a research method or planning research. Trigger when someone says things like "I need to research...", "we want to understand users better", "how should I validate this", "what research should I do for...", "I'm working on [problem] and need to find out...", or describes a design stage (discovery, ideation, validation, post-launch) alongside a question. Also trigger when someone describes a habit-driven method choice ("I was going to do user interviews") and you should challenge whether that's the right fit. This skill guides Claude to first recommend the right research method, then generate a ready-to-use research draft (discussion guide, survey, test plan, etc.) tailored to the problem.
---

# Research Method Advisor

A two-stage skill for design teams:
1. **Recommend** the right research method based on the problem and stage
2. **Generate** a ready-to-use research draft (discussion guide, survey script, usability test plan, etc.)

---

## Stage 1: Diagnose Before Recommending

Before recommending any method, ask these diagnostic questions if not already answered in the designer's description. Ask them all at once, concisely:

1. **What decision will this research inform?** (What will change based on what you find?)
2. **What stage are you in?** (Discovery / Ideation / Validation / Post-launch)
3. **Do you already have a hypothesis?** (Yes = evaluative; No = generative)
4. **What's your timeline and access?** (Days vs weeks; can you recruit users?)
5. **What do you already know?** (Avoid re-researching what's known)

If the designer has already provided enough context, skip straight to the recommendation — don't ask questions they've already answered.

---

## Stage 2: Challenge Habit-Driven Choices

If the designer has already named a method ("I want to do user interviews"), **challenge it** before accepting it:

- Is the question generative or evaluative? (Interviews ≠ validation)
- Is the timeline realistic for that method?
- Is there a faster method that answers the same question?
- Are they solving for behaviour or attitude? (Observation > interviews for behaviour)

Gently push back if the method doesn't fit. Example:
> "User interviews are great for generative questions, but you've described a validation scenario. A quick unmoderated usability test would give you faster, more reliable signal here."

---

## Stage 3: Method Recommendation

Use this framework to select the right method:

### By Research Stage

| Stage | Goal | Best Methods |
|-------|------|-------------|
| **Discovery** | Understand the problem space, users, context | Contextual inquiry, diary studies, stakeholder interviews, desk research, user interviews (generative) |
| **Ideation** | Explore directions, get reactions to early concepts | Co-design workshops, concept testing, card sorting, tree testing |
| **Validation** | Test whether a solution works | Usability testing (moderated or unmoderated), A/B testing, cognitive walkthrough, prototype testing |
| **Post-launch** | Measure impact, find improvement areas | Analytics review, surveys (CSAT/NPS), diary studies, support ticket analysis |

### By Question Type

| Question Type | Method |
|--------------|--------|
| "Why do users behave this way?" | Contextual inquiry, diary study, interviews |
| "What do users need/want?" | Generative interviews, surveys, desk research |
| "Can users complete this task?" | Usability testing |
| "Which version performs better?" | A/B test, preference test |
| "How do users think about this?" | Card sorting, mental model interviews |
| "What are users doing post-launch?" | Analytics + follow-up surveys |

### By Constraints

- **Tight timeline (< 1 week)**: Unmoderated usability test, guerrilla testing, 5-second test, expert review
- **No user access**: Desk research, analytics, competitor analysis, expert review
- **Small budget**: Guerrilla testing, unmoderated tools (Maze, Lookback), surveys

---

## Stage 4: Generate the Research Draft

Once the method is confirmed, generate a complete, ready-to-use draft. Use the templates below as a base and tailor everything to the specific problem described.

Read the relevant reference file for full template guidance:
- Generative interviews → [references/interview-guide.md](references/interview-guide.md)
- Usability testing → [references/usability-test-plan.md](references/usability-test-plan.md)
- Surveys → [references/survey-template.md](references/survey-template.md)
- Other methods → use the universal structure below

### Universal Draft Structure

Every draft should include:

**Header**
- Research goal (one sentence)
- Method chosen and why
- Target participants (who, how many, recruitment criteria)
- Estimated time per session / completion time

**Core Content** (method-specific — see reference files)

**Analysis Notes**
- What to look for
- How to synthesise findings
- How to present to stakeholders

---

## Output Format

Always structure your response in two clear sections:

### Section 1: Method Recommendation
- Recommended method (bold)
- Why this fits the problem and stage (2–3 sentences)
- What it will tell you (and what it won't)
- Any alternatives worth considering
- If challenging a habit choice: explain why the original method was a poor fit

### Section 2: Research Draft
- Full, editable draft ready to use
- Tailored to the specific problem — no generic placeholders
- Clearly labelled sections
- Conversational, human tone (not corporate)

---

## Tone and Style

- Be direct. Don't hedge unnecessarily.
- Challenge politely but clearly when the method doesn't fit.
- Write drafts in plain language — these will be read to real users.
- Avoid jargon in discussion guides and survey questions.
- Keep questions open-ended in generative research; closed/specific in evaluative.
