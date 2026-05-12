# Portfolio Hooks

Project-level Claude Code hooks for the Kristina portfolio site (kristinadesign.netlify.app).

## Setup

Copy `settings.json` into the `.claude/` folder inside your portfolio project directory.

## Hooks included

| Hook | Trigger | Action |
|------|---------|--------|
| **Auto-preview** | After any file edit | Opens browser automatically |
| **Copy review reminder** | After any file edit | Flags changed text for copy-review skill |
| **Version comparison** | Before any deploy command | Compares local vs live site, blocks if identical |
| **Design approval gate** | Before any deploy command | Prompts confirmation that design-approval was run |
| **Accessibility reminder** | After Claude finishes a response | Reminds to run accessibility-review skill |

## Notes

- Update the local paths in `settings.json` to match your machine if cloning to a new location.
- These hooks only activate when Claude Code is opened from inside the portfolio project folder.
