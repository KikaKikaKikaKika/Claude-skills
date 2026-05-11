---
name: design-approval
description: Submit a design for Head of Design approval before publishing. Generates the design in Figma, creates a structured approval package, and sends email and Slack notifications. Run this when a design is ready to publish.
disable-model-invocation: true
allowed-tools: Bash, Read, Write, mcp__claude_ai_Figma__use_figma, mcp__claude_ai_Figma__create_new_file, mcp__claude_ai_Figma__get_metadata
---

## Configuration
Before using this skill, confirm the following are set in your environment:
- `HOD_EMAIL` — Head of Design email address
- `SLACK_WEBHOOK_URL` — Slack incoming webhook URL
- `SLACK_CHANNEL` — Slack channel (e.g. `#design-approvals`)

---

## Process

1. Collect submission details
2. Set up Figma — create or update the file
3. Generate the design in Figma
4. Generate the approval package
5. Send Slack notification
6. Send email notification
7. Confirm delivery to submitter

---

## Step 1 — Collect submission info

Ask for any fields not provided in $ARGUMENTS:

**Required:**
- Submitter name and role
- Feature / design name
- Staging URL (preview link)
- Feature description (what it is, one paragraph)
- Goals: business goal + user goal
- Success metrics
- Dependencies (what this affects or relies on)
- Deadline / desired publish date
- **Is this an edit to an existing project, or a new design?**
  - If edit → ask for the existing Figma file URL

**Optional:**
- Design decisions made (key choices and rationale)
- Open questions or known risks
- Stakeholders already consulted

---

## Step 2 — Set up Figma

Figma is the single source of truth. Every submitted design must exist in Figma before approval is sent.

### If this is an edit to an existing project

1. Use `mcp__claude_ai_Figma__get_metadata` to confirm the existing Figma file is accessible
2. Create a new page in that file named: **`[Feature name] — Ready for Approval · [YYYY-MM-DD]`**
3. This keeps the approved production design and the pending changes clearly separated in the same file
4. The Head of Design can merge or replace the production page after approval

### If this is a new design (no existing Figma file)

1. Use `mcp__claude_ai_Figma__create_new_file` to create a new file
   - File name: **`[Feature name]`**
   - Place in folder: **`New/Ready for Approval`** (create the folder if it doesn't exist)
2. The page name within the file: **`Ready for Approval · [YYYY-MM-DD]`**

### After Figma setup

Note the Figma file URL and page URL — these go into the approval package and notifications.

---

## Step 3 — Generate the design in Figma

Using `mcp__claude_ai_Figma__use_figma`, generate the design on the newly created page.

**Before generating:**
- Load the `/figma-use` skill if available
- Load the visual style guide: fetch `https://raw.githubusercontent.com/KikaKikaKikaKika/Claude-skills/main/visual-style-guide/design-portfolio-brand-guide.md`
- Apply brand colours, typography (DM Sans, DM Mono), spacing, and component styles from the guide

**What to generate:**
- All screens, states, and flows described in the feature description
- Key states: default, empty, error, loading, success — wherever applicable
- Mobile and desktop layouts if the feature spans both
- Annotate key design decisions directly on the frame

**Quality gates — before proceeding to Step 4:**
- Run `design-critique` (Nielsen's 10 heuristics) on the generated design
- Run `accessibility-review` (WCAG 2.1 AA) on the generated design
- Fix all violations before continuing
- If violations cannot be resolved automatically, flag them clearly in the approval package

---

## Step 4 — Generate approval package

Compile into the following structure:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DESIGN APPROVAL REQUEST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Feature:      [Feature / design name]
Submitted:    [Date and time]
Submitted by: [Name, Role]
Type:         [New design / Edit to existing]
Status:       PENDING REVIEW

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PREVIEW
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Figma:        [Direct link to the Ready for Approval page]
Staging URL:  [Staging URL]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DESCRIPTION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[Feature description — what it is, who it's for, what it does]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
GOALS & STRATEGY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Business goal:   [Business goal]
User goal:       [User goal]
Success metric:  [How success is measured]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
KEY DESIGN DECISIONS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[List of key decisions made and why — or "None specified"]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DEPENDENCIES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[What this design depends on or affects — other features, systems, teams]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TIMELINE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Publish deadline: [Date]
Time to review:   Please respond within 48 hours

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
OPEN QUESTIONS / RISKS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[Any open questions or risks the reviewer should know about — or "None"]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
QUALITY CHECKS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Heuristic review (Nielsen's 10):  [Passed / Issues found and resolved: list]
Accessibility review (WCAG AA):   [Passed / Issues found and resolved: list]
Visual style guide:                [Compliant / Deviations: list]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
FIGMA FILE LOCATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[If new design]
File:   New/Ready for Approval / [Feature name]
Page:   Ready for Approval · [YYYY-MM-DD]
Link:   [Figma URL]

[If edit to existing]
File:   [Existing file name]
Page:   [Feature name] — Ready for Approval · [YYYY-MM-DD]
Link:   [Figma URL]

After approval, the Head of Design will move this to the correct folder
and merge or replace the production page in Figma.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TO APPROVE OR REJECT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Reply to this email or respond in Slack with:

  ✅ APPROVED — [Feature name]
  ❌ REJECTED — [Feature name]: [reason]
  🔄 CHANGES REQUESTED — [Feature name]: [what needs to change]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Step 5 — Send Slack notification

```bash
curl -s -X POST "$SLACK_WEBHOOK_URL" \
  -H 'Content-type: application/json' \
  --data '{
    "channel": "'"$SLACK_CHANNEL"'",
    "text": "🔔 *Design Approval Request*",
    "blocks": [
      {
        "type": "header",
        "text": { "type": "plain_text", "text": "🔔 Design Approval Request" }
      },
      {
        "type": "section",
        "fields": [
          { "type": "mrkdwn", "text": "*Feature:*\n[Feature name]" },
          { "type": "mrkdwn", "text": "*Submitted by:*\n[Name, Role]" },
          { "type": "mrkdwn", "text": "*Type:*\n[New design / Edit to existing]" },
          { "type": "mrkdwn", "text": "*Deadline:*\n[Publish date]" }
        ]
      },
      {
        "type": "section",
        "text": { "type": "mrkdwn", "text": "*Description:*\n[One-line feature description]" }
      },
      {
        "type": "actions",
        "elements": [
          {
            "type": "button",
            "text": { "type": "plain_text", "text": "View in Figma" },
            "url": "[Figma page URL]",
            "style": "primary"
          },
          {
            "type": "button",
            "text": { "type": "plain_text", "text": "View staging" },
            "url": "[Staging URL]"
          }
        ]
      },
      {
        "type": "section",
        "text": {
          "type": "mrkdwn",
          "text": "Reply with ✅ *APPROVED*, ❌ *REJECTED*, or 🔄 *CHANGES REQUESTED* — [Feature name]"
        }
      }
    ]
  }'
```

---

## Step 6 — Send email notification

```bash
cat <<'EMAILBODY' | mail -s "Design Approval Request: [Feature name]" -a "Content-Type: text/plain; charset=UTF-8" "$HOD_EMAIL"
[Insert full approval package text from Step 4 here]
EMAILBODY
```

If `mail` is not configured, output the full email body for the submitter to send manually.

---

## Step 7 — Confirm to submitter

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SUBMISSION CONFIRMED
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Your design has been submitted for approval.

Feature:      [Feature name]
Submitted:    [Date and time]
Figma:        [Link to the Ready for Approval page]
Notified:     Head of Design via email + Slack
Response SLA: 48 hours

You will be notified once a decision is made.
If you haven't heard back in 48 hours, follow up in [SLACK_CHANNEL].
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Edge cases

- **Staging URL missing**: Do not proceed — a preview link is required.
- **Figma creation fails**: Flag to submitter, proceed with approval package and notify HoD that Figma file could not be created — include description of what was designed.
- **Existing Figma file inaccessible**: Ask submitter to check sharing permissions and retry. Do not create a duplicate file.
- **Deadline under 48 hours**: Mark as URGENT in Slack and email.
- **Quality checks not resolved**: Flag unresolved violations in the approval package. Do not block submission — the reviewer needs to see the state accurately.
- **Slack fails**: Fall back to email only.
- **Email fails**: Fall back to Slack only.
- **Both fail**: Output full package for manual sending.

---

## After approval — Head of Design actions

When approved:
1. Move the Figma file from `New/Ready for Approval` to the correct project folder — or merge the approval page into the main production file
2. Archive or delete the `Ready for Approval` page once merged
3. Notify the submitter via Slack that the design is approved and the Figma source has been updated
