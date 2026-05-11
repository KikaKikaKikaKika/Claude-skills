# Scoring Rubric

Detailed criteria for each dimension at each score level. Use this to calibrate scores consistently across reviewers and over time.

The bar is set by the complexity of the output — not the seniority of the person who made it.

---

## 1. Content Quality

Evaluates: copy, messaging, information hierarchy, language clarity, tone appropriateness.

| Score | Label | Criteria |
|---|---|---|
| **5** | Exceptional | Copy is precise and purposeful. Every word earns its place. Hierarchy is immediately clear without explanation. Tone is calibrated perfectly to context and user. Nothing to cut, nothing missing. |
| **4** | Strong | Copy communicates clearly. Minor wording improvements possible but no meaningful gaps. Hierarchy is correct. Tone is appropriate. A reviewer would ship this. |
| **3** | Adequate | The message gets through but copy is loose — some padding, some vagueness, or slightly off tone. Hierarchy works but isn't optimised. Functional, not sharp. |
| **2** | Weak | Content has meaningful gaps: unclear hierarchy, wrong tone, jargon, or copy that doesn't match user needs. A reader would be confused or misled at least once. |
| **1** | Poor | Copy is missing, placeholder-heavy, or actively misleading. No evidence that content was treated as a design decision. Requires significant rework before use. |

---

## 2. Visual Design

Evaluates: UI craft, aesthetics, consistency with design system, polish level, intentionality.

| Score | Label | Criteria |
|---|---|---|
| **5** | Exceptional | Visual execution is intentional, coherent, and refined. Every spacing, colour, and typography decision serves the design. Design system used correctly or deviations are clearly justified. Looks finished. |
| **4** | Strong | Visually solid. Minor inconsistencies exist but don't undermine the work. Design system mostly followed. A reviewer would ship this with small polish fixes. |
| **3** | Adequate | Functional visual design. Some inconsistencies in spacing, type, or colour. Design system partially followed. Looks like a work in progress — not broken, but not polished. |
| **2** | Weak | Noticeable inconsistencies that undermine credibility. Design system poorly applied or ignored. Looks unfinished. Would need a visual pass before shipping. |
| **1** | Poor | Visual design does not meet a shippable standard. Major inconsistencies, incorrect use of components, or significant deviation from design system without justification. |

---

## 3. UX Thinking

Evaluates: problem framing, flow logic, edge cases, user needs consideration, friction points.

| Score | Label | Criteria |
|---|---|---|
| **5** | Exceptional | The design solves the right problem in the right way. All edge cases considered and handled — empty states, errors, loading, permission states, extremes of content length. The user journey is frictionless and logical. Nothing missing. |
| **4** | Strong | Solid UX reasoning. The main journey is well-considered. Most edge cases handled. One or two minor gaps but nothing that would break the experience or mislead users. |
| **3** | Adequate | Core flow works. Edge cases partially addressed. Some states missing (e.g. empty state, error state). The main use case is solved but edge use cases are not. |
| **2** | Weak | UX has meaningful gaps that would create user confusion or failure. Key edge cases missing. Flow logic has one or more breaks. Would require significant rethinking before shipping. |
| **1** | Poor | The design does not solve the stated user problem. Flows are incomplete or illogical. No evidence of user thinking. Requires a fundamental rethink. |

---

## 4. Research Grounding

Evaluates: whether design decisions are backed by user insight, data, or evidence — or are based on assumption and preference.

| Score | Label | Criteria |
|---|---|---|
| **5** | Exceptional | Design decisions are clearly connected to research, data, or validated insights. The "why" behind every significant decision is traceable to user evidence. Designer can articulate what they learned and how it shaped the design. |
| **4** | Strong | Most decisions reference prior research or user data. A few decisions are assumption-based but flagged as such. Evidence is relevant and recent. |
| **3** | Adequate | Some research referenced but not consistently applied. Decisions are reasonable but the link between insight and design choice is not always clear. More assumption than evidence overall. |
| **2** | Weak | Minimal research grounding. Most decisions appear to be based on aesthetic preference or convention rather than user insight. Research is referenced superficially or not at all. |
| **1** | Poor | No research grounding. Decisions are entirely assumption-based. No attempt to connect design to user evidence, prior learning, or data. |

---

## 5. Business Alignment

Evaluates: fidelity to the brief, reflection of product priorities, stakeholder recognisability.

| Score | Label | Criteria |
|---|---|---|
| **5** | Exceptional | Output directly and completely addresses the PRD. Every design decision maps to a stated goal or constraint. A PM reading the brief would immediately recognise their requirements in the output. Trade-offs are explicit. |
| **4** | Strong | Output addresses the core brief well. Minor scope drift or gaps but nothing that changes what gets built. PM would be satisfied. |
| **3** | Adequate | Output addresses most of the brief. Some requirements underserved or not reflected. Functional but the designer has prioritised some things at the expense of others without flagging it. |
| **2** | Weak | Notable gaps between the brief and the output. Key requirements missing or significantly deprioritised. PM would need to push back. |
| **1** | Poor | Output does not address the brief. Significant misalignment between what was asked for and what was delivered. Requires a reset. |

---

## 6. Org Standards Alignment

Evaluates: compliance with the org's design system, brand guidelines, content guide, and style guide — as fetched from GitHub in Stage 0.

| Score | Label | Criteria |
|---|---|---|
| **5** | Exceptional | Fully compliant with all fetched standards. Any deliberate deviations are documented and justified within the output. Demonstrates deep understanding of org standards. |
| **4** | Strong | Mostly compliant. One or two minor violations — likely oversights, not misunderstanding. No systematic misuse of standards. |
| **3** | Adequate | Partially compliant. Some standards followed, others not. Mix of oversights and gaps in understanding. Would need a standards pass before shipping. |
| **2** | Weak | Multiple violations across standards. Design system components incorrectly used or ignored. Brand, content, or style guide not followed. Requires significant remediation. |
| **1** | Poor | Org standards largely ignored. Design appears to have been produced without reference to any org guides. Significant rework required to align. |

*Note: if org standards files could not be fetched (Stage 0 failure), score this dimension as N/A and note the reason.*

---

## Process Score

Process is scored holistically — not a number, but a clear label.

| Label | Criteria |
|---|---|
| **Strong** | Researched before designing. Explored multiple directions. Decisions are articulated with clear rationale. Brief was followed closely. Edge cases were proactively considered, not added after feedback. |
| **Adequate** | Some research or iteration evident. Can explain most decisions. Brief was mostly followed. A few gaps in process — minor scope drift, some assumption-based choices — but overall a reasonable approach. |
| **Weak** | Jumped to solution before understanding the problem. First idea shipped without iteration. Decisions cannot be explained beyond "it felt right" or "I thought it looked better." Brief was not closely followed. |

---

## Overall Score Calculation

Weighted average of all 6 dimensions:

| Dimension | Weight |
|---|---|
| Content Quality | 1× |
| Visual Design | 1× |
| UX Thinking | 1.5× |
| Research Grounding | 1.5× |
| Business Alignment | 1× |
| Org Standards | 1× |

**Formula:** (Content + Visual + (UX × 1.5) + (Research × 1.5) + Business + Org) ÷ 8

Round to one decimal place.
