# Accessibility checks — WCAG 2.1 AA

Run axe-core (`npx @axe-core/cli <url>`) or pa11y (`npx pa11y <url>`) per key page; supplement with
manual checks below (automation catches ~40% of issues). Report the WCAG criterion + selector + fix.

## Perceivable
- **Contrast** — text ≥ 4.5:1 (normal), ≥ 3:1 (large ≥ 18.66px bold / 24px). UI components + focus indicators ≥ 3:1. The PRIMARY CTA failing contrast = Critical.
- **Alt text** — every meaningful `<img>` has descriptive `alt`; decorative images `alt=""`. Icon-only buttons have an accessible name.
- **Text resize** — content usable at 200% zoom, no horizontal scroll / clipping.
- **Not colour-alone** — errors/links/states don't rely on colour only (add icon/underline/text).

## Operable
- **Keyboard** — every interactive element reachable and operable by keyboard; no traps. Test Tab/Shift-Tab/Enter/Esc.
- **Visible focus** — a clear focus ring on every focusable element (never `outline:none` without a replacement).
- **Focus order** — matches visual/reading order; modals trap focus and return it on close.
- **Skip link** — "skip to content" for keyboard/screen-reader users.
- **Tap targets** — ≥ 44×44px on mobile, adequate spacing.

## Understandable
- **Form labels** — every field has a programmatic `<label>`/`aria-label`; placeholders are NOT labels.
- **Error identification** — errors described in text, tied to the field (`aria-describedby`), not colour-only.
- **Language** — `<html lang>` set; consistent nav/labelling.

## Robust
- **Semantic structure** — one `<h1>`, logical heading order (no skipped levels), landmarks (`header`/`nav`/`main`/`footer`).
- **Valid ARIA** — roles/states used correctly, not overriding native semantics; no `aria-hidden` on focusable content.
- **Name/role/value** — custom widgets expose proper name, role, state to assistive tech.

## Severity guide
Blocks a task for AT users (unlabelled required field, keyboard trap, CTA contrast fail) = Critical/High.
Cosmetic (minor decorative alt, low-priority contrast) = Medium/Low.
