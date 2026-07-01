# UX checks — conversion heuristics for service-business sites

Heuristic review focused on whether a first-time visitor understands and acts. Pairs with the
messaging audit (`website-copy-reframe`), which grades the words; this grades the experience.

## Above the fold
- Value prop legible in ~5 seconds: what you do + for whom + why it matters.
- ONE primary action, visually dominant (book / send / get). Not five competing buttons.
- A trust signal in view (logos, a number, a certification) without scrolling.

## Navigation & IA
- ≤ ~7 top-level items, plain labels (not clever). Current section indicated.
- Every offer/service reachable in ≤ 2 clicks. No orphan pages, no dead ends.
- Footer carries the utility links (contact, legal, sitemap).
- Search present if the site is large.

## Forms & conversion
- Shortest viable form; each extra field costs conversions. Justify every one.
- Labels above fields, inline validation, human error messages, clear success state.
- CTA text states the outcome ("Get a sample back"), not "Submit".
- Contact/booking reachable from every page (sticky header or repeated CTA).

## Content & scannability
- Short paragraphs, meaningful subheads, bullets over walls of text.
- Claims backed by proof near them (metric/case), not vague adjectives.
- Clear next step at the end of each page (no dead ends).

## Mobile & states
- Real mobile layout at 375px: no horizontal scroll, tap targets ≥ 44px, thumb-reachable CTA.
- Sensible empty, loading, and error states (search no-results, form errors, 404 with a way back).
- Images have dimensions (no jumpy reflow); interactions give feedback.

## Performance-as-UX
- First meaningful content fast (see performance-checks). Slow = bounce, regardless of copy.

## Report each as
`<page/area> · <heuristic> → <what a visitor experiences> → <fix>`. Rank by how many users hit it
and how close it is to the conversion path (checkout/CTA-adjacent = higher severity).
