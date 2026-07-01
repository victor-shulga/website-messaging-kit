# Performance checks — Core Web Vitals + common wins

Audit up to 3 representative pages (home + heaviest template + a content page). Prefer Lighthouse
(`npx lighthouse <url> --output=json --quiet --chrome-flags="--headless"`); fall back to inspecting
the HTML for the patterns below.

## Thresholds (field-grade, "good")
| Metric | Good | Needs work | Poor |
| --- | --- | --- | --- |
| LCP (Largest Contentful Paint) | ≤ 2.5s | 2.5–4.0s | > 4.0s |
| CLS (Cumulative Layout Shift) | ≤ 0.1 | 0.1–0.25 | > 0.25 |
| INP (Interaction to Next Paint) | ≤ 200ms | 200–500ms | > 500ms |
| TTFB (server response) | ≤ 0.8s | 0.8–1.8s | > 1.8s |
| Total page weight | ≤ 1.5MB | 1.5–4MB | > 4MB |

Severity by user impact: money-page LCP > 4s = Critical; site-wide CLS > 0.25 = High.

## Common wins (name the specific offender + the fix)
- **Oversized/unoptimized images** — serve WebP/AVIF, correct dimensions, `loading="lazy"` below the fold, `width`/`height` set (prevents CLS). Hero images should be preloaded, not lazy.
- **Render-blocking resources** — defer non-critical JS, inline critical CSS, `preconnect` to font/CDN origins, `font-display: swap`.
- **Layout shift** — reserve space for images/ads/embeds; avoid injecting banners above content; set explicit media dimensions.
- **Heavy hero media** — autoplaying video/large hero blocking LCP → poster image + lazy video, or compress.
- **Third-party bloat** — chat widgets, analytics, tag managers loaded eagerly; load them `async`/on-idle.
- **No caching/compression** — enable gzip/brotli, long cache headers on static assets, a CDN.
- **Unminified / unused CSS-JS** — tree-shake, code-split, remove dead libraries.

## Report each as
`<page> · <metric> = <value> (threshold <x>) → <specific offender> → <fix + expected gain>`.
E.g. "home · LCP 4.1s (>2.5) → 240KB autoplay hero video blocks paint → poster + lazy load, ~2.2s".
