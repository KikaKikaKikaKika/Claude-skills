# Card Sorting Template

Use for: understanding how users mentally categorise information, designing or validating navigation structures, naming and labelling decisions, information architecture work.
Not suitable for: validating whether a design works, understanding user behaviour in context, or any research where you need qualitative "why" — pair with follow-up interviews for that.

---

## Open vs Closed vs Hybrid

| Type | What participants do | When to use |
|---|---|---|
| **Open** | Group cards AND name the groups themselves | Early IA — you don't have categories yet |
| **Closed** | Sort cards into pre-defined categories | Validating existing categories — do items belong where you put them? |
| **Hybrid** | Sort into pre-defined categories AND create new ones if needed | When you have draft categories but want to test and extend them |

If you're designing navigation from scratch: start open.
If you have an existing structure to validate: use closed or hybrid.

---

## Header

**Research goal:** [What IA or categorisation question are you answering?]
**Type:** [Open / Closed / Hybrid]
**Cards:** [Number of cards — 30–60 is optimal; over 80 is too many]
**Participants:** [Recruitment criteria] — 15–30 for quantitative analysis; 5–8 if adding qualitative follow-up
**Method:** [Remote unmoderated (Optimal Workshop, Maze) / in-person moderated]
**Estimated time per participant:** 20–45 min depending on card count
**Categories (closed only):** [List your pre-defined categories]

---

## Card Writing Guidelines

Each card represents one piece of content, feature, or item to be categorised.

**Good cards:**
- One concept per card, no ambiguity
- Written in user language, not internal product language
- Concrete enough that participants know what it is
- Tested with a pilot participant before the full study

**Bad cards:**
- Two concepts in one: "Settings and preferences" — split into two
- Internal jargon: "Entitlement management" — rewrite as users would say it
- Too vague: "Other" or "Misc" — avoid
- Overlapping concepts that could reasonably go in multiple places — flag these as interesting data, not errors

**Number of cards:**
- 30–40: ideal for most studies
- 40–60: feasible but increases drop-off
- Over 80: split into two studies or reduce scope

---

## Running the Study

### Moderated (in-person or remote call)

**Opening:**
> "I'm going to show you a set of cards, each with a label on it. Your job is to group them in a way that makes sense to you — there's no right or wrong answer. As you work, please think out loud. When you're done, I'll ask you to name each group."

**During:**
- Let them work without interrupting
- If they pause or look confused: "What are you thinking about that one?"
- If they ask where something 'should' go: "Where does it feel right to you?"
- If they want to put a card in two places: "Which group feels most natural as the primary home?"

**After grouping:**
- "Can you name each group for me?"
- "Are there any cards that didn't fit anywhere comfortably?"
- "Were there any that you almost put somewhere else? Why did you end up here?"
- "Is there anything missing — content you'd expect to find that wasn't there?"

### Unmoderated (remote tool)

- Use Optimal Workshop (Optimal Sort), Maze, or UXtweak
- Include a brief intro screen explaining the task
- Add a post-sort question: "Is there anything you'd like to tell us about how you grouped these?"
- Run a pilot with 1–2 people before launching to all participants

---

## Analysis

### Quantitative (15+ participants)

**Similarity matrix:**
Shows how often each pair of cards was grouped together. High co-occurrence = users see them as related.

**Dendrogram:**
Clusters cards by similarity. Use to identify natural groupings and how strongly participants agree.

**Standardisation grid (closed sorting):**
Shows how often each card was placed in each category. Ideal placement = 70%+ in one category. Items with spread across multiple categories = ambiguous — consider renaming or splitting.

**Agreement score:**
How consistently participants grouped cards. High agreement = clear mental model. Low agreement = users conceptualise the domain differently from each other (segment and analyse separately).

### Qualitative (always do this, regardless of sample size)

- Review group names participants gave — these are labelling candidates
- Note cards that caused hesitation or ended up in their own group
- Review open text responses for reasoning you can't see in the data

---

## Analysis Notes

**What to do with outliers:**
Cards that were grouped inconsistently across participants are your most interesting findings — they reveal where users' mental models diverge. Don't average them away; explore why.

**What to present to stakeholders:**
- Proposed IA based on the dendrogram clusters
- The group names participants used (vs your current labels)
- The 3–5 items with the most ambiguous placement — these need design decisions
- Any expected groupings that didn't emerge in the data

**What card sorting will NOT tell you:**
- Whether users can navigate the structure you build (use tree testing for that)
- Why users group things the way they do (follow up with interviews)
- Whether the labels you choose will work in context (use tree testing or usability testing)
