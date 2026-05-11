# Audit Format Reference

Used in Stage 2 (Evolve Mode) when running a full design system coverage audit.

---

## Audit Output Structure

Produce the audit in four sections. If any section is clean, say so explicitly — don't omit it.

---

### Section 1: Coverage Summary

A top-level table before the detail:

| Area | Status | Notes |
|------|--------|-------|
| Color tokens | ✅ Complete | 42 tokens, all semantic |
| Spacing tokens | ⚠️ Partial | Missing sm/xs steps, hardcoded 6px found |
| Typography tokens | ✅ Complete | — |
| Border radius | ✅ Complete | — |
| Elevation | ❌ Missing | No elevation tokens defined |
| Motion | ⚠️ Partial | Duration tokens exist, easing missing |
| Component library | ⚠️ Partial | 28 components, 4 used-in-product but not published |
| Pattern documentation | ❌ Missing | No documented patterns |

---

### Section 2: Drift Report

List every inconsistency found between the Figma library and actual usage across product files.

Format each item:

```
DRIFT: [Component or token name]
Scope: Found in [N] product file(s)
Issue: [Exact description of drift]
Example: [File name or frame name where seen]
Severity: [Critical / Moderate / Minor]
Recommended fix: [Specific action]
```

Severity guide:
- **Critical**: User-facing inconsistency visible without scrutiny (wrong color, wrong spacing scale)
- **Moderate**: Inconsistency visible under inspection (slightly different radius, wrong token aliasing)
- **Minor**: Internal / structural (detached instance, overridden style that still looks right)

---

### Section 3: Orphan Report

**Orphaned components** — exist in the library, not used anywhere in product files:

```
ORPHAN COMPONENT: [Name]
Last updated: [date if known]
Recommended action: Deprecate / Archive / Keep (with reason)
```

**Orphaned tokens** — defined in variables but not referenced by any component or frame:

```
ORPHAN TOKEN: [token path]
Recommended action: Remove / Alias to active token
```

---

### Section 4: Gap Report

Patterns or components observed in product files that aren't in the library:

```
GAP: [Descriptive name]
Seen in: [file/frame names]
Frequency: [N occurrences]
Current approach: [How designers are handling it now — improvised, copied manually, etc.]
Proposal recommended: [Yes / No + brief rationale]
```

---

## Prioritization

After the four sections, produce a prioritized action list:

**Do now** (blocks consistency or accessibility)
1. ...

**Do soon** (friction for the team, not user-facing)
1. ...

**Backlog** (nice to have)
1. ...

---

## Audit Scope Notes

A full audit requires access to product files, not just the DS file. If only the DS file was available, note at the top:

> "⚠️ Audit scope limited to DS file only. Drift and gap reports are incomplete without access to product files. Share product file keys to complete the audit."
