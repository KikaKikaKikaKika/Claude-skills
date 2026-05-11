# Survey Template

Use for: measuring attitudes at scale, post-launch satisfaction tracking, quantifying a problem found in qualitative research, reaching users you can't interview.
Not suitable for: understanding why users behave a certain way, validating whether a design works, or any question that requires follow-up.

---

## Before You Write a Survey

Surveys produce reliable data only when:
- You already know what to ask (use interviews first if you don't)
- Your questions are unambiguous
- Your sample is representative
- Response rate is high enough to be meaningful (aim for 50+ responses minimum; 200+ for segmented analysis)

If you have fewer than 50 likely respondents, run interviews instead.

---

## Header

**Research goal:** [What decision will this survey inform?]
**Target respondents:** [Who / how many / recruitment or distribution method]
**Estimated completion time:** [Keep under 5 min — aim for 10 questions max]
**Incentive:** [If any]
**Open:** [Date] → **Close:** [Date]
**Owner:** [Name]

---

## Survey Structure

### Part 1: Screening (optional — 1–2 questions)

Only include if your distribution method might reach the wrong audience.

Example:
- "Do you currently use [product] for your work?" Yes / No → [No = exit]
- "How often do you use [feature]?" Never / Rarely / Monthly / Weekly / Daily → [Never = exit or separate segment]

---

### Part 2: Context / Segmentation (2–3 questions)

Capture the variables that might explain differences in responses. Don't ask for anything you won't analyse.

Examples:
- "What best describes your role?" [Options]
- "How long have you been using [product]?" Less than 3 months / 3–12 months / Over a year
- "How often do you use [relevant feature]?" [Frequency scale]

---

### Part 3: Core Questions (4–6 questions)

This is the heart of the survey. Guidelines:

**Question types to use:**
- **Rating scales**: "On a scale of 1–5, how [easy / useful / clear] is [X]?" — use consistently (always 1 = low, 5 = high)
- **Multiple choice**: Use when options are mutually exclusive and exhaustive. Always include "Other (please specify)"
- **Ranking**: Use sparingly — cognitively demanding. Max 5 items.
- **Open text**: Use at the end. 1–2 open questions max. Gives richest data but hardest to analyse at scale.

**Question writing rules:**
- One idea per question. Never "How easy and useful is this?" — split into two.
- No leading questions. "How much do you enjoy using X?" assumes they enjoy it.
- No double negatives. "Do you not disagree that...?" — never.
- Avoid "always", "never", "all", "none" — they're extreme and people avoid them.
- Provide a neutral option on scales when genuinely neutral responses are valid.

**Standard scales to use:**

Satisfaction:
> 1 = Very dissatisfied, 2 = Dissatisfied, 3 = Neutral, 4 = Satisfied, 5 = Very satisfied

Ease / effort:
> 1 = Very difficult, 2 = Difficult, 3 = Neutral, 4 = Easy, 5 = Very easy

Agreement:
> 1 = Strongly disagree, 2 = Disagree, 3 = Neutral, 4 = Agree, 5 = Strongly agree

Frequency:
> Never / Rarely (a few times a year) / Sometimes (monthly) / Often (weekly) / Always (daily)

---

### Part 4: Standard Metrics (optional — include if tracking over time)

**NPS (Net Promoter Score)**
> "How likely are you to recommend [product / feature] to a colleague or friend?"
> 0–10 scale. 0 = Not at all likely, 10 = Extremely likely
> Promoters = 9–10, Passives = 7–8, Detractors = 0–6
> NPS = % Promoters − % Detractors

**CSAT (Customer Satisfaction)**
> "How satisfied are you with [specific interaction / feature]?"
> 1–5 scale (Very dissatisfied → Very satisfied)
> CSAT = (4s + 5s) / total responses × 100

**SUS (System Usability Scale) — 10 standard questions**
Use the standardised SUS questions verbatim if measuring overall usability. Do not modify them.

---

### Part 5: Open Question(s) (1–2 max)

Place at the end. These are optional for respondents.

Examples:
- "Is there anything about [feature / product] that you'd like to tell us that we didn't ask about?"
- "What's the one thing that would most improve your experience with [X]?"
- "What made you give [X] the rating you did?"

---

## Distribution Notes

- **Email**: Highest response rate for existing users. Keep the subject line direct: "2 minutes to improve [product]"
- **In-product**: High relevance, lower completion. Trigger after a key action, not randomly.
- **Social / open link**: Risk of unqualified respondents. Add screening questions.

Optimal send time: Tuesday–Thursday, mid-morning.
Follow-up reminder: 3–4 days after initial send. One reminder only.

---

## Analysis Notes

**Quantitative:**
- Calculate mean and distribution for each scale question — distribution reveals more than averages
- Segment by respondent type if sample allows (role, tenure, frequency)
- Flag questions with high "neutral" responses — may indicate unclear question or genuine ambivalence

**Qualitative (open text):**
- Code responses into themes (even informally for small sets)
- Preserve verbatim quotes that are representative or vivid
- Note unexpected responses — they often contain the most useful signal

**What to present to stakeholders:**
- Lead with the headline metric (NPS, CSAT, or top-line satisfaction score)
- Show distribution charts, not just averages
- Quote 3–5 verbatim open responses that illustrate the key themes
- Be honest about sample size and representativeness

**What surveys will NOT tell you:**
- Why users feel or behave a certain way (use interviews)
- Whether a design works (use usability testing)
- Anything with fewer than ~50 responses — call it directional, not statistically significant
