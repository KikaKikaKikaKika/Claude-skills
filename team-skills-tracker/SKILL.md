---
name: team-skills-tracker
description: Head of Design only. Reads from design-review-monitor persistent storage, maps review data to 22 design competencies, and generates spider/radar charts per person and for the team overall. Run monthly.
disable-model-invocation: true
allowed-tools: Read, Write, Bash
---

# Team Skills Tracker

Head of Design only. This output is never shared with team members.

---

## Competency Framework

22 competencies rated 0–6:

| Score | Label |
|---|---|
| 0 | Unfamiliar |
| 1 | Learner |
| 2 | Beginner |
| 3 | Junior |
| 4 | Intermediate |
| 5 | Senior |
| 6 | Expert |

### The 22 Competencies

1. UX Leadership
2. UX Strategy and Planning
3. UX Writing
4. Information Architecture
5. User Flows
6. Communication and Presenting
7. Wireframing
8. Prototyping
9. Branding
10. User Interface Design
11. Interaction Design
12. Workshop Facilitation
13. Stakeholder Management
14. Agile
15. Usability Evaluation
16. User Need Evaluation
17. General Research
18. Metrics and Measurements
19. Analysis
20. Audit
21. Business and Strategy
22. Design System

---

## Process

1. Load all person records from storage
2. Map review dimension scores to competency scores
3. Generate individual spider chart per person
4. Generate team aggregate spider chart
5. Output summary and coaching notes

---

## Step 1 — Load Records

Read all JSON files from `~/.claude/projects/design-review-monitor/`.

For each person record, extract:
- All review scores (content, visual, ux, research, business, org_standards, overall)
- All process scores (Strong / Adequate / Weak)
- Role
- Number of reviews

Use averages across all reviews for each dimension.

Convert process score to numeric:
- Strong → 5
- Adequate → 3
- Weak → 1

If a person has only 1 review, note this in the output — single-review data is directional only.

---

## Step 2 — Map Dimensions to Competencies

Review dimensions (1–5 scale) → competency scores (0–6 scale).

**Scale conversion:** `competency = round((dimension_avg - 1) / 4 * 6, 1)`

This maps 1→0, 3→3, 5→6.

### Mapping Rules

Each competency derives from one or more dimensions. Where multiple dimensions contribute, use the weighted formula shown.

| Competency | Formula |
|---|---|
| UX Writing | content × 1.0 |
| User Interface Design | visual × 1.0 |
| Branding | (visual × 0.6) + (org_standards × 0.4) |
| Design System | (org_standards × 0.7) + (visual × 0.3) |
| Information Architecture | ux × 1.0 |
| User Flows | (ux × 0.7) + (research × 0.3) |
| Interaction Design | (ux × 0.5) + (visual × 0.5) |
| Wireframing | (ux × 0.6) + (visual × 0.4) |
| Prototyping | (ux × 0.7) + (visual × 0.3) |
| Usability Evaluation | (ux × 0.5) + (research × 0.5) |
| User Need Evaluation | (research × 0.7) + (ux × 0.3) |
| General Research | research × 1.0 |
| Metrics and Measurements | (research × 0.5) + (business × 0.5) |
| Analysis | (research × 0.6) + (business × 0.4) |
| Audit | (org_standards × 0.6) + (ux × 0.4) |
| Business and Strategy | business × 1.0 |
| Stakeholder Management | (business × 0.5) + (process × 0.5) |
| Communication and Presenting | (business × 0.4) + (content × 0.3) + (process × 0.3) |
| Workshop Facilitation | (research × 0.4) + (process × 0.4) + (ux × 0.2) |
| Agile | process × 1.0 |
| UX Strategy and Planning | (ux × 0.5) + (business × 0.3) + (research × 0.2) |
| UX Leadership | (overall × 0.5) + (process × 0.3) + (business × 0.2) |

Apply scale conversion to each dimension average before applying the formula:
`dim_scaled = (dim_avg - 1) / 4 * 6`

Then blend scaled values per the formula above to get the final competency score (0–6). Round to 1 decimal place.

---

## Step 3 — Generate Spider Charts

Use Python with matplotlib. Generate one chart per person, plus one team aggregate chart.

```python
import json, math, os, sys
import matplotlib.pyplot as plt
import matplotlib.patches as mpatches
import numpy as np

COMPETENCIES = [
    "UX Leadership", "UX Strategy", "UX Writing", "Info Architecture",
    "User Flows", "Communication", "Wireframing", "Prototyping",
    "Branding", "UI Design", "Interaction Design", "Workshop Facilitation",
    "Stakeholder Mgmt", "Agile", "Usability Eval", "User Need Eval",
    "General Research", "Metrics", "Analysis", "Audit",
    "Business & Strategy", "Design System"
]

SCORE_LABELS = {0: "Unfamiliar", 1: "Learner", 2: "Beginner", 3: "Junior",
                4: "Intermediate", 5: "Senior", 6: "Expert"}

def make_spider(scores_dict, title, output_path, color="#4F46E5"):
    N = len(COMPETENCIES)
    angles = [n / float(N) * 2 * math.pi for n in range(N)]
    angles += angles[:1]

    fig, ax = plt.subplots(1, 1, figsize=(10, 10), subplot_kw=dict(polar=True))
    fig.patch.set_facecolor("#0F0F0F")
    ax.set_facecolor("#0F0F0F")

    # Grid rings
    for level in range(1, 7):
        ring = [level] * N + [level]
        ax.plot(angles, ring, color="#333333", linewidth=0.5, linestyle="--")
        ax.fill(angles, ring, alpha=0)

    # Labels for rings
    for level, label in SCORE_LABELS.items():
        if level > 0:
            ax.text(0, level, str(level), color="#666666", size=7,
                    ha="center", va="center")

    # Plot each person/team
    if isinstance(scores_dict, dict) and any(isinstance(v, dict) for v in scores_dict.values()):
        # Multiple people on one chart (team overlay)
        palette = plt.cm.get_cmap("Set2", len(scores_dict))
        legend_patches = []
        for i, (name, scores) in enumerate(scores_dict.items()):
            values = [scores.get(c, 0) for c in COMPETENCIES]
            values += values[:1]
            c = palette(i)
            ax.plot(angles, values, color=c, linewidth=2, linestyle="solid")
            ax.fill(angles, values, color=c, alpha=0.1)
            legend_patches.append(mpatches.Patch(color=c, label=name))
        ax.legend(handles=legend_patches, loc="upper right",
                  bbox_to_anchor=(1.3, 1.1), framealpha=0.2, labelcolor="white",
                  facecolor="#1a1a1a")
    else:
        # Single person
        values = [scores_dict.get(c, 0) for c in COMPETENCIES]
        values += values[:1]
        ax.plot(angles, values, color=color, linewidth=2.5, linestyle="solid")
        ax.fill(angles, values, color=color, alpha=0.2)

    # Spoke labels
    ax.set_xticks(angles[:-1])
    ax.set_xticklabels(COMPETENCIES, size=8, color="white",
                       wrap=True)
    ax.set_ylim(0, 6)
    ax.set_yticks([])
    ax.spines["polar"].set_color("#333333")

    plt.title(title, size=14, color="white", pad=20, fontweight="bold")
    plt.tight_layout()
    plt.savefig(output_path, dpi=150, bbox_inches="tight",
                facecolor="#0F0F0F")
    plt.close()
    print(f"Saved: {output_path}")

# --- Load data passed via stdin as JSON ---
data = json.load(sys.stdin)
output_dir = data["output_dir"]
os.makedirs(output_dir, exist_ok=True)

# Individual charts
for person_key, info in data["people"].items():
    name = info["name"]
    scores = info["competency_scores"]
    fname = person_key.replace(":", "_").replace("/", "_")
    path = os.path.join(output_dir, f"{fname}_skills.png")
    make_spider(scores, f"{name} — Design Skills · {data['month']}", path)

# Team aggregate chart (averages)
if len(data["people"]) > 1:
    all_competencies = COMPETENCIES
    team_avgs = {}
    for comp in all_competencies:
        vals = [p["competency_scores"].get(comp, 0) for p in data["people"].values()]
        team_avgs[comp] = round(sum(vals) / len(vals), 1)
    path = os.path.join(output_dir, "team_aggregate_skills.png")
    make_spider(team_avgs, f"Team Aggregate — Design Skills · {data['month']}",
                path, color="#10B981")

    # Overlay chart (all people on one chart)
    overlay = {info["name"]: info["competency_scores"] for info in data["people"].values()}
    path = os.path.join(output_dir, "team_overlay_skills.png")
    make_spider(overlay, f"Team Overlay — Design Skills · {data['month']}", path)
```

Save this script to `/tmp/team_skills_chart.py` then run it via Bash.

---

## Step 4 — Orchestration

When triggered, execute the following sequence:

### 4a — Read storage

```bash
ls ~/.claude/projects/design-review-monitor/
```

Read each file that matches `person:*` pattern.

### 4b — Compute competency scores

For each person:
1. Average all review dimension scores across their review history
2. Apply scale conversion: `(avg - 1) / 4 * 6`
3. Apply blending formulas from Step 2
4. Round each competency to 1 decimal place

### 4c — Build JSON payload

```json
{
  "month": "2026-05",
  "output_dir": "/tmp/team-skills-tracker/2026-05",
  "people": {
    "person:anna-k": {
      "name": "Anna K",
      "role": "Product Designer",
      "review_count": 3,
      "competency_scores": {
        "UX Leadership": 3.8,
        "UX Strategy": 3.2,
        ...
      }
    }
  }
}
```

### 4d — Run chart generation

```bash
pip3 install matplotlib numpy --quiet 2>/dev/null || true
echo '<JSON_PAYLOAD>' | python3 /tmp/team_skills_chart.py
```

### 4e — Output summary table

After charts are generated, print:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TEAM SKILLS TRACKER — [MONTH YYYY]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Charts saved to: /tmp/team-skills-tracker/[YYYY-MM]/

  team_aggregate_skills.png — team average per competency
  team_overlay_skills.png   — all individuals overlaid
  [person]_skills.png       — per-person breakdown

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
COMPETENCY SCORES SUMMARY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[Table: Name | Role | Reviews | Top 3 competencies | Bottom 3 competencies | Overall avg]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TEAM GAPS (score < 3 / Junior)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[List competencies where team average is below Junior level, with names of who is below]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
COACHING PRIORITIES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[Same format as design-review-monitor tracker: Ready for more / Watch closely / Team-wide gap]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Step 5 — Save Monthly Snapshot

After each run, save a snapshot to persistent storage:

**Path:** `~/.claude/projects/design-review-monitor/team-skills-snapshot-[YYYY-MM].json`

```json
{
  "month": "2026-05",
  "generated": "2026-05-11T10:00:00",
  "people": {
    "person:anna-k": {
      "name": "Anna K",
      "role": "Product Designer",
      "review_count": 3,
      "competency_scores": { ... }
    }
  },
  "team_averages": { ... }
}
```

This enables month-over-month trend comparison in future runs. When a previous snapshot exists, compare and note which competencies improved, declined, or stalled per person.

---

## Edge Cases

- **No review data for a person**: Skip them and note their absence. Do not generate a chart with all zeros — it would be misleading.
- **Only 1 review on record**: Generate chart but annotate as "directional — based on 1 review".
- **matplotlib not installed**: Run `pip3 install matplotlib numpy` before chart generation.
- **Storage directory empty**: Output message: "No design review data found. Run design-review-monitor reviews first before generating the skills tracker."
- **Month not specified**: Default to current month.
- **Previous snapshot exists for same month**: Ask before overwriting.
