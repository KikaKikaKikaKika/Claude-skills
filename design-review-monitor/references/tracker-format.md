# Tracker Format

Used when the Head of Design requests a team overview or scorecard export.

Commands that trigger this: "show me the team overview", "export scorecard", "how is the team doing", "tracker", "team scores".

---

## Trend Calculation

Compare the overall scores of the last two reviews:
- **Improving** — latest overall is ≥0.3 higher than previous
- **Declining** — latest overall is ≥0.3 lower than previous
- **Stable** — difference is less than 0.3
- **New** — only one review on record

---

## Output Format 1: Team Overview Table (default)

```
## Design Team — Skills Tracker
Last updated: [date]
Reviews on record: [total count]

| Name | Role | Reviews | Content | Visual | UX | Research | Business | Org Std | Overall | Trend | Last Review |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Anna K | Product Designer | 3 | 3.7 | 4.3 | 3.3 | 2.7 | 4.0 | 3.7 | 3.5 | ↑ Improving | 2026-04-18 |
| Marcus T | UX Designer | 2 | 4.0 | 3.5 | 4.5 | 3.0 | 3.5 | 4.0 | 3.8 | → Stable | 2026-05-01 |
| Priya N | Product Manager | 1 | 3.0 | 2.0 | 4.0 | 3.0 | 5.0 | 2.0 | 3.1 | ● New | 2026-05-11 |

Trend key: ↑ Improving · → Stable · ↓ Declining · ● New (1 review)
```

Scores shown are averages across all reviews. Overall is weighted (UX and Research at 1.5×).

---

## Output Format 2: Individual Summary Cards

When asked about a specific person ("how is Anna doing", "show me Marcus's history"):

```
## Anna K — Product Designer
Reviews: 3 | Last review: 2026-04-18

Scores over time:

| Review | Date | Brief | Content | Visual | UX | Research | Business | Org Std | Overall | Process |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-02-10 | Mobile onboarding redesign | 3 | 4 | 3 | 2 | 4 | 3 | 3.1 | Adequate |
| 2 | 2026-03-22 | Empty state redesign | 4 | 4 | 3 | 2 | 4 | 4 | 3.4 | Adequate |
| 3 | 2026-04-18 | Settings page overhaul | 4 | 5 | 4 | 3 | 4 | 4 | 3.9 | Strong |

Averages: Content 3.7 · Visual 4.3 · UX 3.3 · Research 2.7 · Business 4.0 · Org Std 3.7 · Overall 3.5

Trend: ↑ Improving overall. Visual and business alignment are strengths. Research grounding
remains the weakest dimension — improving slowly but still below team average.
```

---

## Output Format 3: Dimension Leaderboard

When asked "who is strongest at X" or "where is the team weakest":

```
## Team — Research Grounding
Sorted by average score (all reviews)

| Rank | Name | Avg Score | Reviews | Trend |
|---|---|---|---|---|
| 1 | Marcus T | 3.5 | 2 | → Stable |
| 2 | Priya N | 3.0 | 1 | ● New |
| 3 | Anna K | 2.7 | 3 | ↑ Improving |

Team average: 3.1 / 5
```

---

## Output Format 4: CSV Export

When asked to export as CSV:

```csv
Name,Role,Reviews,Content_Avg,Visual_Avg,UX_Avg,Research_Avg,Business_Avg,OrgStd_Avg,Overall_Avg,Trend,Last_Review
Anna K,Product Designer,3,3.7,4.3,3.3,2.7,4.0,3.7,3.5,Improving,2026-04-18
Marcus T,UX Designer,2,4.0,3.5,4.5,3.0,3.5,4.0,3.8,Stable,2026-05-01
Priya N,Product Manager,1,3.0,2.0,4.0,3.0,5.0,2.0,3.1,New,2026-05-11
```

---

## Coaching Summary (Head of Design only)

Append this at the end of any team overview:

```
## Coaching Priorities

↑ Ready for more: [Name] — [one sentence on why]
⚠ Watch closely: [Name] — [one sentence on concern]
📍 Team-wide gap: [Dimension] — average [X/5] across team. Consider a team session or shared resource.
```
