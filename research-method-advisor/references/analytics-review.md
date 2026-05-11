# Analytics Review Template

Use for: post-launch research to understand what users are actually doing, identifying where users drop off or get stuck, quantifying a problem found in qualitative research, prioritising where to focus next.
Not suitable for: understanding why users behave a certain way (pair with interviews), early-stage design work before launch, anything that requires user motivation or context.

---

## What it is

An analytics review uses quantitative behavioural data — page views, funnels, click maps, session recordings, error logs — to understand how users interact with a product post-launch. It tells you **what** is happening; it cannot tell you **why**.

Used alone, analytics can mislead. A high bounce rate might mean users are confused — or that they found what they needed immediately. Always pair analytics findings with qualitative research to interpret them correctly.

---

## Header

**Research goal:** [What behaviour or metric are you trying to understand?]
**Time period:** [Date range — ensure it's representative and anomaly-free]
**Tools available:** [Google Analytics / Mixpanel / Amplitude / Heap / FullStory / Hotjar / etc.]
**Key flows or pages:** [Which parts of the product are in scope]
**Hypothesis (if any):** [What you expect to find, so you can confirm or challenge it]
**Owner:** [Name]

---

## Step 1: Define the Questions First

Don't open analytics and start clicking. Define what you want to know before you look.

Write 3–5 specific questions:
1. [e.g. "Where in the onboarding flow are users dropping off?"]
2. [e.g. "Which features are used most/least in the first 7 days?"]
3. [e.g. "What percentage of users who start [task] complete it?"]
4. [e.g. "How does retention differ between users who completed onboarding and those who didn't?"]
5.

---

## Step 2: Data Sources to Check

Review what's available for each question:

### Traffic & Engagement
- Page views, unique visitors, session duration
- Bounce rate (with context — high bounce isn't always bad)
- Entry and exit pages

### Funnels
- Step-by-step completion rates for key flows (signup, onboarding, checkout, etc.)
- Drop-off rates at each step
- Time between steps (long gaps = friction)

### Feature Usage
- Which features are used and how often
- Feature adoption over time (D1, D7, D30)
- Last-used features (candidates for deprecation)

### Errors
- JavaScript errors, API failures, form validation errors
- Which errors occur most, and in which flows
- Error rates over time

### Session Recordings & Heatmaps (qualitative analytics)
- Where users click vs where you expect them to
- Rage clicks (rapid repeated clicking = frustration)
- Scroll depth (how far down pages users get)
- Mouse movement patterns that suggest confusion

---

## Step 3: Funnel Analysis Template

For each key flow, map the funnel and calculate conversion at each step.

**Flow name:** [Onboarding / Checkout / Feature activation / etc.]
**Time period:** [Date range]

| Step | Screen / Action | Users entering | Users completing | Drop-off % | Notes |
|---|---|---|---|---|---|
| 1 | | | | | |
| 2 | | | | | |
| 3 | | | | | |
| 4 | | | | | |
| **End** | [Completion event] | | | | |

**Overall completion rate:** [% who start and finish]
**Biggest drop-off:** [Step with highest drop-off — this is where to focus]

---

## Step 4: Segment the Data

Never rely on averages alone. Segment by:

- **New vs returning users** (different patterns, different needs)
- **Acquisition channel** (users from ads behave differently from organic)
- **Device type** (mobile users often have worse completion rates — is that a design problem?)
- **Plan / tier** (free vs paid behaviour is often very different)
- **Geography** (if relevant — latency, language, localisation issues)
- **Cohort** (users who signed up in different months — are recent cohorts better or worse?)

---

## Step 5: Interpreting What You Find

### Common patterns and what they suggest

| Finding | Possible causes | What to investigate next |
|---|---|---|
| High drop-off at a specific step | Confusion, friction, unexpected ask, technical error | Session recordings at that step; interviews |
| Low feature adoption | Feature is hard to find, users don't understand the value, not part of their workflow | Usability test; interviews |
| High error rate on a form field | Unclear label, wrong validation, format mismatch | Review error messages; usability test |
| Short session duration on key pages | Users found what they needed quickly (good) OR gave up quickly (bad) | Segment by outcome — did they convert or leave? |
| High rage clicks | Element looks interactive but isn't; expected behaviour missing | Session recordings; heuristic review |

---

## Analysis Notes

**What to present to stakeholders:**
- Lead with the headline finding and its business impact ("38% of users who start onboarding don't complete it — that's [estimated lost revenue or users/month]")
- Show the funnel with the biggest drop-off highlighted
- Include 2–3 session recording clips if available — concrete video is more persuasive than numbers alone
- Be clear about what you don't know: "We know where users drop off. We don't yet know why. We recommend 5 interviews with users who abandoned at Step 3."

**What analytics will NOT tell you:**
- Why users are doing what they're doing (use interviews or contextual inquiry)
- Whether a design change will improve the metric (use usability testing first, then A/B test)
- What users want or need (analytics shows behaviour, not motivation)
