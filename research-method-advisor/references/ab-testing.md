# A/B Testing Template

Use for: comparing two versions of a design to determine which performs better on a measurable metric, post-launch optimisation, validating the impact of a specific change.
Not suitable for: understanding why one version performs better (use interviews or usability testing), early-stage exploration, situations with low traffic (you won't reach significance).

---

## What it is

A/B testing (or split testing) randomly assigns users to one of two (or more) variants and measures behaviour — clicks, conversions, sign-ups, retention — to determine which performs better. It answers "which is better?" not "why?"

It requires:
- Sufficient traffic to reach statistical significance
- A clear, measurable success metric
- One variable changed at a time (otherwise you can't know what caused the difference)
- An engineering or analytics setup to run the test

---

## Before You Run an A/B Test

**Check these first:**

| Question | If no... |
|---|---|
| Do you have enough traffic? (typically 1,000+ users per variant per week) | Use qualitative methods instead; A/B test later |
| Do you have a single, measurable hypothesis? | Define it before starting |
| Is this a meaningful enough change to move the metric? | Small tweaks rarely produce detectable signal |
| Do you have an analytics setup to track the metric? | Set this up first |
| Can engineering implement the test? | Confirm before designing |

---

## Header

**Research goal:** [Which version performs better on which metric?]
**Hypothesis:** "We believe that [change] will [increase/decrease] [metric] because [reason]."
**Variant A:** [Control — current version]
**Variant B:** [Treatment — proposed change]
**Primary metric:** [The one metric that determines the winner]
**Secondary metrics:** [Guard rails — metrics you'll monitor to ensure the winner doesn't harm other areas]
**Minimum sample size:** [Calculate before running — see below]
**Estimated runtime:** [Days or weeks to reach significance]
**Traffic split:** 50/50 (default) or [justify if different]
**Tool / platform:** [Optimizely / LaunchDarkly / internal feature flags / Google Optimize / etc.]

---

## Hypothesis Writing

A well-formed hypothesis has three parts:

> "We believe that [specific change to the design] will [increase / decrease] [specific metric] for [user segment] because [rationale based on insight or data]."

**Good example:**
> "We believe that moving the primary CTA above the fold on the pricing page will increase sign-up conversion rate for new visitors because users who don't scroll are currently missing it."

**Bad example:**
> "We think a new button will help." — no metric, no rationale, no specificity.

---

## Sample Size Calculation

Run a sample size calculation before starting. Don't end the test early because it "looks like" one is winning — that's p-hacking.

Inputs needed:
- **Baseline conversion rate**: current % of users completing the action
- **Minimum detectable effect (MDE)**: smallest improvement you'd consider meaningful (e.g. 5% relative lift)
- **Statistical significance**: 95% (standard) or 90% (acceptable for lower-stakes tests)
- **Statistical power**: 80% (standard)

Use an online calculator (e.g. Evan Miller's A/B test calculator) or your analytics platform's built-in calculator.

**Minimum sample per variant:** [Result from calculation]
**Estimated days to reach sample:** [Sample needed ÷ daily unique visitors per variant]

---

## Running the Test

**Before launch checklist:**
- [ ] Both variants are correctly implemented and QA'd
- [ ] Analytics tracking is confirmed on both variants
- [ ] Randomisation is working (users consistently see the same variant on return)
- [ ] Test is not running during an anomalous period (major promotion, outage, seasonal spike)
- [ ] Start date and minimum runtime are agreed

**During the test:**
- Do not peek at results and call a winner early
- Monitor for anomalies: traffic drops, tracking errors, variant imbalances
- Do not run other major changes to the same page/flow during the test

---

## Analysing Results

**When to stop:**
- Reached the minimum sample size AND
- Reached the minimum runtime (at least 1–2 full business cycles — typically 2 weeks) AND
- Statistical significance is ≥95%

**Interpreting results:**

| Outcome | What it means |
|---|---|
| B wins (significant) | Roll out B. Document what changed and why it worked. |
| A wins / B loses (significant) | Keep A. Document the learning — the hypothesis was wrong. |
| No significant difference | Neither is better. The change may be too small, the sample too small, or the metric the wrong one to measure. |
| Significant result but small effect | Decide if the lift is worth the engineering cost. |

**Confidence interval:** Report the range, not just the point estimate. "B converted at 4.2% vs A at 3.8%, a 10.5% relative lift (95% CI: 3–18% lift)" is more honest than "B won by 10.5%."

---

## Analysis Notes

**Secondary metric review:**
Did B win on the primary metric but harm something else? (e.g. higher sign-ups but lower retention, more clicks but fewer completions). A test that improves one metric at the expense of another isn't a clean win.

**Segment analysis (post-hoc):**
After a significant result, check whether the effect holds across key segments (new vs returning users, mobile vs desktop, etc.). An average result can mask a strong positive for one segment and a negative for another.

**What to document after the test:**
- Hypothesis
- Result and confidence interval
- Sample size and runtime
- Secondary metric impact
- Decision made and rationale
- What this teaches us about our users

**What A/B testing will NOT tell you:**
- Why one version performed better (use usability testing or interviews to investigate)
- Whether the winning variant is the best possible version (it's only better than what you tested)
- Anything reliable if you don't have enough traffic
