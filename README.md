# Website Messaging Kit

Reusable system for rewriting a service-business website (homepage + service pages) through
Viktor Shulha's copywriting framework. Turns vague, generic agency copy into
champion-facing, proof-led messaging — and ships the brand + preview to match.

Proven on a live client build (2026-07). Repeat for any client.

## What's in here

```
skills/website-copy-reframe/   the engine (Claude Code skill) — audit | homepage | service-page
```

Companion client-facing docs (Framework Guide + Template Pack) live in the private workspace,
not in this public repo.

## The skill — 3 modes

Install: copy `skills/website-copy-reframe/` into `~/.claude/skills/`.

| Mode | Input | Output |
| --- | --- | --- |
| `audit` | live URL | 0–100 messaging scorecard vs the 5 fundamentals + brand-voice rules + ranked gap list |
| `homepage` | URL / draft + canvas | Hero · Problem · Solution + lower-half sections |
| `service-page` | one offer + canvas | summary · benefits · problems-it-fixes · proof · FAQ/objections · SEO · CTA |

All three share ONE copywriting canvas (audience → champion → situation → current way →
limitations → problems → capabilities → features → benefits) and a **proof-bank** step
(inventory real numbers/cases/testimonials, source-or-cut, before writing).

## Process

1. **Ingest** — scrape the live site + pull the client's positioning/ICP docs.
2. **Audit** (`audit` mode) → scorecard + gaps (the case for the rewrite).
3. **Proof bank** — inventory real numbers, cases, testimonials, trust.
4. **Canvas** — one primary use case, vertical positioning, written to the champion.
5. **Homepage** (`homepage` mode) — Hero/Problem/Solution + sections.
6. **Service pages** (`service-page` mode) — one per offer, SEO-mapped, colour-coded.
7. **Design system** — `design-system-generator` skill → brand tokens + Netlify.
8. **Blueprint** — single-file HTML: sitemap + rendered homepage preview.
9. **Handoff** — one doc: links + what we did + what the client does next.

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
