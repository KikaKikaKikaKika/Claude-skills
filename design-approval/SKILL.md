---
name: design-approval
description: Submit a design for Head of Design approval before publishing. Generates a structured approval package and sends email and Slack notifications automatically. Run this when a design is ready to publish.
disable-model-invocation: true
allowed-tools: Bash, Read, Write
---

## Configuration
Before using this skill, confirm the following are set in your environment:
- `HOD_EMAIL` — Head of Design email address
- `SLACK_WEBHOOK_URL` — Slack incoming webhook URL
- `SLACK_CHANNEL` — Slack channel (e.g. `#design-approvals`)

---

## Process

1. Collect submission details from $ARGUMENTS or prompt for missing fields
2. Generate the approval package
3. Send Slack notification
4. Send email notification
5. Confirm delivery to submitter

---

## Step 1 — Collect submission info

Ask for any fields not provided in $ARGUMENTS:

**Required:**
- Submitter name and role
- Feature / design name
- Staging URL (preview link)
- Figma link (if available)
- Feature description (what it is, one paragraph)
- Goals: business goal + user goal
- Success metrics
- Dependencies (what this affects or relies on)
- Deadline / desired publish date

**Optional:**
- Design decisions made (key choices and rationale)
- Open questions or known risks
- Stakeholders already consulted

---

## Step 2 — Generate approval package

Compile the collected information into the following structure:

---

### APPROVAL PACKAGE

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DESIGN APPROVAL REQUEST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Feature:     [Feature / design name]
Submitted:   [Date and time]
Submitted by:[Name, Role]
Status:      PENDING REVIEW

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PREVIEW
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Staging URL: [staging URL]
Figma:       [Figma URL or "Not provided"]

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

Heuristic review (Nielsen's 10):  [Passed / Issues found: list]
Accessibility review (WCAG AA):   [Passed / Issues found: list]
Visual style guide:                [Compliant / Deviations: list]

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

## Step 3 — Send Slack notification

Run the following bash command to send the Slack notification:

```bash
curl -s -X POST "$SLACK_WEBHOOK_URL" \
  -H 'Content-type: application/json' \
  --data '{
    "channel": "'"$SLACK_CHANNEL"'",
    "text": "🔔 *Design Approval Request*",
    "blocks": [
      {
        "type": "header",
        "text": {
          "type": "plain_text",
          "text": "🔔 Design Approval Request"
        }
      },
      {
        "type": "section",
        "fields": [
          {
            "type": "mrkdwn",
            "text": "*Feature:*\n[Feature name]"
          },
          {
            "type": "mrkdwn",
            "text": "*Submitted by:*\n[Name, Role]"
          },
          {
            "type": "mrkdwn",
            "text": "*Deadline:*\n[Publish date]"
          },
          {
            "type": "mrkdwn",
            "text": "*Status:*\nPending review ⏳"
          }
        ]
      },
      {
        "type": "section",
        "text": {
          "type": "mrkdwn",
          "text": "*Description:*\n[One-line feature description]"
        }
      },
      {
        "type": "actions",
        "elements": [
          {
            "type": "button",
            "text": { "type": "plain_text", "text": "View staging preview" },
            "url": "[staging URL]",
            "style": "primary"
          },
          {
            "type": "button",
            "text": { "type": "plain_text", "text": "View in Figma" },
            "url": "[Figma URL]"
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

## Step 4 — Send email notification

Run the following to send the email. Requires `mail` to be configured, or substitute with your preferred sending method.

```bash
cat <<'EMAILBODY' | mail -s "Design Approval Request: [Feature name]" -a "Content-Type: text/plain; charset=UTF-8" "$HOD_EMAIL"
[Insert full approval package text from Step 2 here]
EMAILBODY
```

If `mail` is not configured, output the full email body and instruct the submitter to send it manually to `$HOD_EMAIL`.

---

## Step 5 — Confirm to submitter

After sending, output the following confirmation:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SUBMISSION CONFIRMED
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Your design has been submitted for approval.

Feature:      [Feature name]
Submitted:    [Date and time]
Notified:     Head of Design via email + Slack
Response SLA: 48 hours

You will be notified once a decision is made.
If you haven't heard back in 48 hours, follow up in [SLACK_CHANNEL].
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Edge cases

- **Staging URL missing**: Do not proceed. A preview link is required for approval.
- **Deadline is under 48 hours**: Flag this clearly in the Slack and email — mark as URGENT.
- **Quality checks not passed**: Warn the submitter that unresolved heuristic, accessibility, or style violations are present. Ask if they want to fix them first or proceed with the flag visible to the reviewer.
- **Slack send fails**: Fall back to email only. Inform submitter that Slack notification failed.
- **Email send fails**: Fall back to Slack only. Inform submitter that email notification failed.
- **Both fail**: Output the full approval package for the submitter to send manually.
