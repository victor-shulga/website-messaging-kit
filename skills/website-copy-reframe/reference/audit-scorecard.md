# Audit scorecard — 0–100 messaging rubric

Mode `audit` output. Score the CURRENT copy (scraped) against the framework. This is the
diagnostic that precedes any rewrite. Formalizes the "Section 0 — Gaps" table.

## Scoring (100 total)

### A. The 5 fundamentals — can a target-market visitor answer each easily? (50 pts, 10 each)
1. **Which services?** — is the offer legible in 5 seconds, or buried under a spray of industries?
2. **How does it work?** — is the engagement / process shown, or implied?
3. **What exactly gets done?** — concrete deliverables named, or vague "solutions"?
4. **When would I use it?** — is the trigger/situation clear?
5. **How does it help me progress?** — tied to the champion's job, or generic "efficiency"?

Score each 0–10: 0 = absent/misleading · 5 = present but vague · 10 = crisp, specific, champion-facing.

### B. Champion clarity (10 pts)
Written to the champion close to the pain (GIS Manager, BIM Coordinator, CTO) — or to an abstract
"your business" / the exec buyer? 0 = no persona · 10 = one clear champion addressed.

### C. Proof before claim (10 pts)
Do metrics / named cases lead, with capability following — or do adjectives claim first and
scramble for evidence? 0 = adjective soup · 10 = every claim carries a number or a case.

### D. Voice compliance (20 pts) — score against the CLIENT's own brand rules
Deduct per violation found (cap 0). Common rule set:
- Emojis anywhere (client rule "no emojis") — −4
- Hype words ("cutting-edge", "top-tier", "world-class", "revolutionising") — −3
- "Free pilot / free trial" where a "demo dataset" belongs — −3
- Broken / placeholder stats ("0+ years", "0+ projects") — −4
- Horizontal spray across unrelated industries (vertical positioning breached) — −3
- Missing domain vocabulary the buyer expects (e.g. PostGIS/CRS/LOD for geospatial) — −3

## Output format

```
<Client> homepage — Messaging Audit · Score XX/100

A. Five fundamentals        __/50   (1:_ 2:_ 3:_ 4:_ 5:_)
B. Champion clarity         __/10
C. Proof before claim       __/10
D. Voice compliance         __/20
                            ─────
                            XX/100  ·  <one-line verdict>

Ranked gaps (most costly first):
1. <what's wrong> → <why it costs a lead> → <the fix>
2. …
```

## Reading the score
- **80–100** — solid; tighten, don't rebuild.
- **55–79** — real leaks; run homepage mode on Hero/Problem/Solution.
- **< 55** — the copy is fighting the strategy; full reframe + rebuild the structure.

Always end with the recommended next mode (homepage / service-page) and which blocks to fix first.
Common sub-55 pattern: emojis, placeholder/broken counters, a spray across unrelated industries,
"free pilot" language, and a buried secondary offer — a site whose copy fights its own positioning.
