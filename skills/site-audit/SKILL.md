---
name: site-audit
description: >
  Technical audit of a live website — the engineering companion to the messaging audit in
  `website-copy-reframe`. Crawls the site and scores it across four dimensions: UX (clarity,
  navigation, forms, trust), accessibility (WCAG 2.1 AA), performance (Core Web Vitals /
  Lighthouse), and functional bugs (broken links, console errors, dead CTAs, responsive
  breakage). Produces a severity-ranked `site-audit-report.md` (Critical → High → Medium →
  Low) with a concrete fix per finding. Use when the user says: "technical audit", "site
  audit", "audit this site", "check this URL", "why is the site slow", "accessibility check",
  "is the site broken on mobile", "Lighthouse this", or pastes a URL and asks what's wrong.
  This is the TECHNICAL layer. NOT copy/messaging (that's `website-copy-reframe` audit mode)
  and NOT visual brand (design-system-generator). Run both audits together for a full
  pre-rebuild picture: messaging audit = does the copy convert; site audit = does the site work.
---

# Site Audit (technical)

The technical half of a website review. Where `website-copy-reframe` audit mode scores whether
the copy converts, this scores whether the site *works* — fast, accessible, unbroken, usable.

Run it before a rebuild (baseline the current site) and after (verify the new build).

## Output contract

A single `site-audit-report.md` in the working directory. Findings grouped by severity, most
severe first. Each finding: **what · where (URL + selector/metric) · why it matters · the fix**.
Open with a one-line verdict + a score per dimension. Close with the top 5 fixes to do first.

Severity:
- **Critical** — blocks use or conversion (broken checkout/CTA, JS error killing a page, unreadable contrast on the primary CTA, LCP > 4s on the money page).
- **High** — hurts many users (no mobile layout, missing form labels, 404s in the nav, CLS > 0.25).
- **Medium** — friction (slow images, minor contrast, missing alt text, no focus states).
- **Low** — polish (metadata, favicon, trailing best-practice nits).

## Step 0 — Scope

Confirm: which URL(s)? Whole site (crawl) or a few key pages (home + top service + contact)?
Which dimensions (default: all four)? Depth (default: home + up to ~5 key pages).

## Step 1 — Map the site

Discover pages, forms, links, and load-time errors. Prefer a real browser (Playwright MCP) to
crawl: for each page capture the DOM snapshot, real selectors, forms, internal/external links,
and console + network errors seen on load. If no browser is available, fetch the HTML and extract
links/forms/meta from the markup. Write a small sitemap (pages + selectors) the other steps read.

## Step 2 — Run the four dimensions

Use real tooling when present; fall back to HTML analysis when not.

- **Performance** — Lighthouse via `npx lighthouse <url> --output=json --quiet --chrome-flags="--headless"`
  (or PageSpeed). Capture LCP, CLS, INP/TBT, TTFB, total weight, render-blocking resources, unoptimized
  images. Audit up to 3 representative pages. See `reference/performance-checks.md`.
- **Accessibility** — axe-core (`npx @axe-core/cli <url>`) or pa11y (`npx pa11y <url>`). Check WCAG 2.1 AA:
  contrast, labels, alt text, heading order, focus order/visible focus, landmarks, tab traps, ARIA misuse.
  See `reference/accessibility-checks.md`.
- **UX** — heuristic review against `reference/ux-checks.md`: is the value prop clear above the fold;
  is the primary action obvious and singular; nav depth/labels; form length + inline validation; trust
  signals; mobile tap targets; empty/error states.
- **Bugs** — author a short Playwright spec from the real selectors and run it: every nav link resolves
  (no 404), primary CTAs and forms submit, no uncaught console errors, no layout breakage at 375 / 768 /
  1280. See `reference/bug-patterns.md`.

## Step 3 — Rank + write the report

Dedupe across dimensions, assign severity by user impact (not by how easy it is to find), and write
`site-audit-report.md`. Every finding gets a concrete, specific fix — not "improve performance" but
"defer the 240KB hero video; it blocks LCP (4.1s → ~2.2s)". Note anything you could NOT check (no
browser, auth-walled pages) — never let a skipped check read as a pass.

## Composes with the kit
- Run `site-audit` (technical) + `website-copy-reframe` audit mode (messaging) together = full
  pre-rebuild baseline: does it work + does it convert.
- Feed Critical/High findings into the rebuild spec alongside the reframed copy and design system.

## Reference files
- `reference/performance-checks.md` — Core Web Vitals thresholds + common perf wins
- `reference/accessibility-checks.md` — WCAG 2.1 AA checklist
- `reference/ux-checks.md` — conversion-oriented UX heuristics for service sites
- `reference/bug-patterns.md` — functional/responsive bug patterns + a Playwright recipe
