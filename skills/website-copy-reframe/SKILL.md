---
name: website-copy-reframe
description: >
  Viktor's engine for a service-business website's messaging. THREE modes:
  (1) audit — score an existing homepage/site against the framework's 5 fundamentals +
  brand-voice rules → a 0–100 scorecard + ranked gap list; (2) homepage — reframe the home
  page into Hero / Problem / Solution + sections; (3) service-page — write a single
  service/offer page (summary + benefits + problems-it-fixes + proof + FAQ/objections +
  SEO + CTA). All three share ONE copywriting canvas (audience → champion → situation →
  current way → limitations → problems → capabilities → features → benefits) and a
  proof-bank step (inventory real cases/numbers/testimonials before writing). Scrapes the
  live site (or takes pasted draft). Default output = a client-ready Google Doc. Trigger
  when Viktor says: "прожени сайт через фреймворк", "рефрейм текстів сайту", "перепиши
  homepage копі", "reframe website copy", "прогнати тексти сайту через АІ", "аудит
  homepage / messaging аудит", "оціни homepage", "напиши сервісну сторінку", "service page
  copy", "заповни копірайтинг канву для [client]", or pastes a client URL / draft and asks
  to audit, reframe, or write a page. This is the COPY layer. NOT the visual brand system
  (design-system-generator) and NOT technical UX/perf/a11y audit (that's the site-audit
  plugin) and NOT cold outbound copy (sequence-writer / 03-copy-generation). Pairs with
  hypo-generator / offer-factory (they define ICP+offer; this writes the site copy).
---

# Website Copy Reframe

Viktor's house engine for a service company's website messaging. Most agency sites fail the
same way — vague, generic copy that tries to please founders + delivery + sales + HR at once.
This skill forces the copy back onto one champion, one situation, and a tight
capability→feature→benefit chain, obeying the client's own brand voice.

The homepage's job is to answer 5 fundamentals for the target market:
1. Which services does the company provide?
2. How does it work?
3. What exactly gets done?
4. When would I use it?
5. How does it help me make progress on what I'm trying to do?

Until most of the target market can answer these easily, resist vague messaging.

## Three modes (pick in Step 0)

| Mode | Input | Output |
| --- | --- | --- |
| **audit** | a live URL (current copy) | 0–100 scorecard vs the 5 fundamentals + voice rules, ranked gap list with fixes |
| **homepage** | URL / draft + canvas | Hero · Problem · Solution + lower-half sections |
| **service-page** | one service/offer + canvas | Summary · benefits · problems-it-fixes · proof · FAQ/objections · SEO · CTA |

Natural pipeline: **audit → homepage → service-page** (diagnose, then rewrite home, then the
offer pages). Modes share Steps 1–3 (ingest · proof bank · canvas).

## Output contract

A **client-ready Google Doc** titled `<Client> — <Mode> (<page>)`, saved locally to
`~/Desktop/gtm-workspace/<client>-copy-reframe/`. Every copy block cites the canvas cell it came
from (rationale line), so the client sees the logic. Plus a memory file.

Reference canvas (a filled reference example, source of truth for structure):
the copywriting canvas Sheet (kept in the private workspace).

---

## Step 0 — Pick mode + forks (AskUserQuestion)

Lock:
1. **Mode** — audit · homepage · service-page (skip if obvious from the request).
2. **Input source** — scrape live URL · pasted draft · generate-from-scratch.
3. **Output form** — Google Doc (default) · fill a duplicated Sheet canvas · HTML preview.
4. **Positioning** — default **vertical** (persona/company type); the doc argues vertical beats
   horizontal for high-ticket / complex-sale services with budget < $50K.

## Step 1 — Ingest the current copy (shared)

- **Scrape:** use `website-scraper` / Apify to pull homepage + key service pages. Capture
  headlines, subheads, body, CTAs, proof (logos, cases, awards). Treat as the **"current way"**
  the client describes itself — raw material, not the answer.
- **Paste:** take the draft verbatim.
- Cross-read any existing `hypo-generator` / `offer-factory` / ICP doc for the client.

## Step 2 — Proof bank (shared, NEW — do before writing)

Inventory the client's **real proof** into one table so every claim later is defensible. Without
this, service pages go soft. See `reference/proof-bank.md`. Capture:
- **Numbers** — verified metrics (e.g. `<7% rework`, `570+ projects`, `500 km / 4 days`). Source each.
- **Cases** — named client projects, result-first, tagged to an offer/vertical.
- **Testimonials** — quotes tied to the champion's problem, with attribution.
- **Trust** — certifications, memberships, geo, entity, years, team make-up.
Flag anything unsourced → do NOT ship it. Map each proof point to the offer/vertical it serves.

## Step 3 — The canvas (shared)

Fill left→right (see `reference/framework.md`, `reference/copy-blocks.md`):
- **Audience** — company type × person/department × situation → pick ONE primary (vertical).
- **Champion** — the user close to the pain who pushes the 3–6-month deal, NOT the exec buyer.
- **Situation / activities** — functional, tool-agnostic ACTIVITIES (not outcomes). Detail until
  slightly uncomfortably specific.
- **Current way → limitations → problems** (left half) — one primary use case.
- **Capabilities → features → benefits** (right half) — capabilities improve limitations;
  benefits solve problems.

---

## Step 4A — MODE: audit

Score the ingested copy against the rubric in `reference/audit-scorecard.md`:
- **5 fundamentals** (can a target-market visitor answer each easily?) — 0–10 each.
- **Champion clarity** — is it written to the champion or a vague "your business"? 0–10.
- **Proof before claim** — metrics/cases lead vs adjectives scrambling for evidence? 0–10.
- **Voice compliance** — client's own brand rules (emoji, hype, "free pilot", positioning). 0–20.
Output: a **0–100 score**, a per-criterion breakdown, and a **ranked gap list** — each gap =
`what's wrong → why it costs → the fix`, most-costly first. This is the Section-0 gap table
formalized. Hand off to homepage/service-page mode for the actual rewrite.

## Step 4B — MODE: homepage

Translate the canvas into blocks (see `reference/copy-blocks.md`):
- **Hero** = top-row message + key capabilities + service category + trust line.
- **Problem Section** = current-way + limitations + problems (empathy + qualification).
- **Solution** = 3 arguments from capabilities/features/benefits.
- **Lower-half sections** (pick per client): Services · Industries · Testimonials · Why-us ·
  Persona/Company segmentation · ROI · Calendar/Form.

## Step 4C — MODE: service-page

Write ONE service/offer page (see `reference/service-page-blocks.md`). Different job from the
homepage: one service deep, bottom-funnel, SEO. Blocks:
- **Hero** — service name + the champion outcome + one proof metric.
- **What it is / what gets done** — concrete deliverables (fundamental #3).
- **Problems it fixes** — the limitations→problems this service specifically removes.
- **Benefits** — outcomes, numeric where possible.
- **Proof** — the offer's matched cases + testimonial (from the proof bank).
- **How it works / engagement** — steps, models, turnaround (fundamental #2, #4).
- **FAQ / objections** — the buying blockers pre-empted (IP, QC, security, price-after-demo).
- **SEO** — target keyword cluster, title/meta, H1/H2 map, internal links.
- **CTA** — the demo/sample next step.

## Step 5 — Humanize + ship (shared)

- Run copy through `anticopywriting-ai` (kill AI-slop, negative parallelism "не X а Y",
  канцелярит); pull Viktor's voice from `about-viktor` if it's his own asset. Obey the CLIENT's
  brand-voice rules first (they win over generic style).
- Assemble the Google Doc (canvas + proof bank + mode output + rationale), save locally, create
  the doc via Drive MCP, share the link.
- Write/refresh `project_<client>_copy_reframe.md` + MEMORY.md pointer.

---

## Reference files
- `reference/framework.md` — the full 6-step method (source of truth)
- `reference/copy-blocks.md` — homepage block templates + worked example + reframe heuristics
- `reference/service-page-blocks.md` — service/offer-page template + SEO map
- `reference/audit-scorecard.md` — the 0–100 rubric + scoring + gap-list format
- `reference/proof-bank.md` — proof-inventory template
