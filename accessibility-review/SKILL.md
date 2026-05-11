---
name: accessibility-review
description: Run this automatically on ANY design output before presenting it — UI screens, flows, components, wireframes, interaction specs, or copy+layout combinations. Do not wait to be asked. Review against WCAG 2.1 AA, fix all violations internally, then present only the resolved output. This runs alongside design-critique — both must pass before a design is shown.
user-invocable: false
---

## When to run

Automatically, before presenting any design output. Never skip this. Never present a design that has not passed this review.

Run alongside `design-critique`. Both must complete before output is shown.

---

## Process

1. Generate the design internally — do not show it yet
2. Review against every applicable criterion below
3. Fix all violations — revise the design internally
4. Repeat until no violations remain
5. Present the resolved design
6. Append the accessibility review log (violations found + fixes applied)

---

## WCAG 2.1 AA Review

### 1. Color & Contrast

**1.1 Text contrast (SC 1.4.3)**
- Normal text (under 18pt / 14pt bold): minimum 4.5:1 ratio
- Large text (18pt+ or 14pt+ bold): minimum 3:1 ratio
- Check all text on all background combinations, including disabled states

**1.2 Non-text contrast (SC 1.4.11)**
- UI components (buttons, inputs, checkboxes): minimum 3:1 against adjacent color
- Meaningful icons: minimum 3:1
- Focus indicators: minimum 3:1

**1.3 Color alone (SC 1.4.1)**
- Errors must not rely on red alone — add icon + label
- Required fields must not be marked by color alone — add asterisk or label
- Charts and graphs must have labels, patterns, or textures, not only color differences

**Fix violations by:** adjusting color values, adding non-color indicators (icons, labels, patterns), ensuring sufficient contrast in all states including hover, focus, and disabled.

---

### 2. Typography & Readability

**2.1 Text resize (SC 1.4.4)**
- Text must scale to 200% without loss of content or function
- No fixed-height containers that clip text on zoom

**2.2 Text spacing (SC 1.4.12)**
- Layout must hold when: line height 1.5×, letter spacing 0.12em, word spacing 0.16em, paragraph spacing 2×
- Ensure no content overlaps or gets cut off with these adjustments

**2.3 Reflow (SC 1.4.10)**
- Content must reflow at 320px viewport width without horizontal scrolling
- Exception: content that requires two-dimensional layout (maps, data tables, certain diagrams)

**Fix violations by:** using relative units (em, rem, %), flexible containers, and min-height instead of fixed height.

---

### 3. Interactive Elements

**3.1 Keyboard navigation (SC 2.1.1)**
- Every interactive element reachable by Tab / Shift+Tab
- No keyboard traps — user can always navigate away
- Custom components (dropdowns, date pickers, modals, sliders) have full keyboard support
- Logical tab order that matches visual reading order

**3.2 Focus visible (SC 2.4.7)**
- Every interactive element has a visible focus indicator
- Focus indicator has minimum 3:1 contrast against adjacent colors
- Do not suppress the browser's default focus ring without providing an equal or better alternative

**3.3 Touch targets (SC 2.5.5)**
- Minimum 44×44px for all tap targets
- Adequate spacing between adjacent targets to prevent mis-taps

**Fix violations by:** adding visible :focus styles with sufficient contrast, ensuring touch target sizes, defining keyboard interaction patterns for custom components.

---

### 4. Content & Structure

**4.1 Heading hierarchy**
- Headings follow logical order: H1 → H2 → H3 (no skipped levels)
- Each page/screen has exactly one H1
- Headings are meaningful — they describe the section, not just look big

**4.2 Labels and instructions (SC 1.3.1, 3.3.2)**
- Every form field has a visible label (not placeholder text alone — placeholders disappear on input)
- Required fields are clearly identified (not by color alone)
- Format requirements stated before the field, not only after submission fails
- Group related inputs with fieldset/legend where appropriate

**4.3 Error identification (SC 3.3.1)**
- Errors identify the specific field that has the problem
- Error messages describe what went wrong AND how to fix it
- Errors appear inline, adjacent to the source field
- Error summary at top of form for multi-field forms

**4.4 Link and button purpose (SC 2.4.6)**
- All link text is descriptive in isolation — no "click here", no "learn more" alone
- Button labels clearly describe the action
- If visual context provides meaning, aria-label or aria-labelledby provides the same context to screen readers

**Fix violations by:** adding visible labels, writing descriptive link/button text, providing inline error messages with clear instructions.

---

### 5. Images & Media

**5.1 Text alternatives (SC 1.1.1)**
- Meaningful images: descriptive alt text that conveys the same information
- Decorative images: empty alt attribute (alt="") so screen readers skip them
- Functional images (e.g. icon-only buttons): alt text describes the function, not the icon
- Complex images (charts, diagrams): short alt text + long description nearby

**5.2 Images of text (SC 1.4.5)**
- Text is not embedded in images, except for logos or where specific visual presentation is essential

**Fix violations by:** writing meaningful alt text for all images, removing text from images, providing text alternatives for complex visuals.

---

### 6. Motion & Animation

**6.1 Reduced motion (SC 2.3.3)**
- All animations and transitions respect prefers-reduced-motion
- Provide static or reduced alternatives when this media query is active
- Animations that communicate state (loading, progress) need non-motion alternatives

**6.2 Flashing content (SC 2.3.1)**
- No content flashes more than 3 times per second
- This is a seizure safety criterion — treat it as critical

**Fix violations by:** wrapping all animations in @media (prefers-reduced-motion: no-preference), providing non-animated fallbacks.

---

### 7. Modals, Overlays & Dynamic Content

**7.1 Focus management**
- When a modal opens: focus moves to the modal (first interactive element or the modal container)
- While modal is open: focus is trapped inside — Tab cycles within the modal
- When modal closes: focus returns to the element that triggered it

**7.2 Screen reader announcements (SC 4.1.3)**
- Success and error messages are announced to screen readers without requiring focus change (use aria-live regions)
- Dynamic content changes (loading states, filter results, updated counts) are announced

**7.3 Dismissal**
- Modals and dialogs can always be dismissed with Escape key

**Fix violations by:** adding aria-modal, managing focus on open/close, implementing aria-live="polite" for status messages, supporting Escape key dismissal.

---

## Output Format

Present the final accessible design first. Then append:

---
**Accessibility Review (WCAG 2.1 AA)**

| Criterion | Issue found | Fix applied |
|---|---|---|
| SC 1.4.3 Text contrast | Body text on card background was 3.8:1 | Darkened text to meet 4.5:1 |
| SC 2.4.7 Focus visible | No focus ring on nav links | Added 2px accent-color outline |

List only criteria where violations were found and fixed.
If no violations: "No accessibility violations found — design meets WCAG 2.1 AA."

---

## Severity reference (for logging only — all must be fixed before output)

- **Critical**: blocks access entirely for users with disabilities (missing keyboard nav, no alt text on functional images, focus trap without escape)
- **Serious**: significantly impairs access (contrast failure, missing form labels, no error identification)
- **Moderate**: creates difficulty but workarounds exist (small touch targets, missing heading structure)
- **Minor**: marginal issues (slightly low contrast on decorative text, overly verbose alt text)

All severity levels must be resolved before presenting the design.
