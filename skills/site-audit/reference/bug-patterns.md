# Bug patterns — functional & responsive

Author a short Playwright spec from the REAL selectors captured in Step 1, run it, and turn
failures into findings. On machines where `npx playwright` is unreliable, drive a browser MCP
interactively and record the same checks.

## What to check
- **Links** — every nav + in-body + footer link resolves (no 404/500, no `#` dead links, no
  broken external links on key pages).
- **CTAs & forms** — primary buttons do something; forms submit and show a success state; required
  validation fires; no silent failures.
- **Console** — no uncaught JS errors or unhandled promise rejections on load or on interaction.
- **Network** — no failed requests (missing images, 4xx/5xx assets, mixed-content over HTTPS).
- **Responsive** — no horizontal scroll, overlap, clipped text, or off-screen CTA at 375 / 768 / 1280.
- **Interactive** — menus, accordions, tabs, modals, carousels open/close/trap-and-return focus.
- **Media** — images load (no broken icons), videos have poster/fallback, no layout jump.
- **State** — 404 page exists and offers a route back; search no-results is handled; back button works.

## Playwright recipe (sketch)
```js
// build from sitemap.json selectors captured in Step 1
for (const url of pages) {
  await page.goto(url, { waitUntil: 'networkidle' });
  // console + network error collectors registered before goto
  expect(consoleErrors, `console errors on ${url}`).toEqual([]);
  for (const link of internalLinks) {
    const resp = await request.get(link);
    expect(resp.status(), `${link}`).toBeLessThan(400);
  }
  for (const vp of [375, 768, 1280]) {
    await page.setViewportSize({ width: vp, height: 900 });
    const overflow = await page.evaluate(() => document.documentElement.scrollWidth > window.innerWidth + 1);
    expect(overflow, `h-scroll at ${vp} on ${url}`).toBeFalsy();
  }
}
```

## Severity
Broken CTA / form / checkout, JS error killing a page, 404 in the primary nav = Critical.
Responsive breakage on a key page, broken secondary link = High. Cosmetic overflow = Medium/Low.
Report: `<page> · <what broke> · <selector/URL> · <repro> → <fix>`.
