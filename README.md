# Website Messaging Kit

Reusable system for rewriting a service-business website (homepage + service pages) through
Viktor Shulha's copywriting framework. Turns vague, generic agency copy into
champion-facing, proof-led messaging — and ships the brand + preview to match.

Proven on a live client build (2026-07). Repeat for any client.

## What's in here

```
skills/website-copy-reframe/   copy engine (Claude Code skill) — audit | homepage | service-page
skills/site-audit/             technical engine (Claude Code skill) — UX · a11y · perf · bugs
```

Two audits, one rebuild: **messaging** (does the copy convert) + **technical** (does the site
work). Run both to baseline a site before a rewrite. Companion client-facing docs (Framework
Guide + Template Pack) live in the private workspace, not in this public repo.

## The copy skill — 3 modes

Install: copy `skills/website-copy-reframe/` into `~/.claude/skills/`.

| Mode | Input | Output |
| --- | --- | --- |
| `audit` | live URL | 0–100 messaging scorecard vs the 5 fundamentals + brand-voice rules + ranked gap list |
| `homepage` | URL / draft + canvas | Hero · Problem · Solution + lower-half sections |
| `service-page` | one offer + canvas | summary · benefits · problems-it-fixes · proof · FAQ/objections · SEO · CTA |

All three share ONE copywriting canvas (audience → champion → situation → current way →
limitations → problems → capabilities → features → benefits) and a **proof-bank** step
(inventory real numbers/cases/testimonials, source-or-cut, before writing).

## The technical skill — `site-audit`

Install: copy `skills/site-audit/` into `~/.claude/skills/`. Crawls the site and scores four
dimensions — **UX**, **accessibility** (WCAG 2.1 AA), **performance** (Core Web Vitals / Lighthouse),
**functional bugs** (broken links, console errors, responsive breakage) — into a severity-ranked
`site-audit-report.md` with a concrete fix per finding. The engineering companion to the messaging
audit; run both before a rebuild.

## Process

1. **Ingest** — scrape the live site + pull the client's positioning/ICP docs.
2. **Audit — messaging** (`website-copy-reframe` audit mode) → scorecard + gaps.
3. **Audit — technical** (`site-audit`) → UX/a11y/perf/bug report. Baseline before rebuild.
4. **Proof bank** — inventory real numbers, cases, testimonials, trust.
5. **Canvas** — one primary use case, vertical positioning, written to the champion.
6. **Homepage** (`homepage` mode) — Hero/Problem/Solution + sections.
7. **Service pages** (`service-page` mode) — one per offer, SEO-mapped, colour-coded.
8. **Design system** — `design-system-generator` skill → brand tokens + Netlify.
9. **Blueprint** — single-file HTML: sitemap + rendered homepage preview.
10. **Handoff** — one doc: links + what we did + what the client does next.

## Rules

- Write to the **champion** (the user near the pain), not the exec buyer or "your business".
- Numbers over adjectives · proof before claim · name the buyer's tech vocabulary · no hype.
- Obey the **client's own brand-voice rules first**.
- Vertical positioning for high-ticket / complex-sale services.
- Humanize before shipping (kill AI-slop, negative parallelism "не X а Y").

## Companion

Pairs with the `design-system-generator` skill (brand system → single-file HTML) to ship the
look alongside the copy. Client worked-examples are kept private, not in this repo.

---
Built by Viktor Shulha

---

Built by [Victor Shulga](https://victorshulga.com), Fractional CRO for B2B service companies. Full skill stack: [victorshulga.com/stack](https://victorshulga.com/stack/).
