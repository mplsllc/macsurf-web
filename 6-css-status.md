# Tier 3 — CSS status page

## Authoritative source

[`docs/css-status.md`](https://github.com/mplsllc/macsurf/blob/master/docs/css-status.md) in the macsurf repo **is** the implementation truth. Generated 2026-05-19, revised after fixes148 hardware-verification. Roughly 150 properties categorised by done / partial / planned / deferred.

**Harvest this verbatim.** Do not paraphrase from the website's existing copy or invent statuses — this file is the only document that's been cross-checked against actual code paths.

## What's in there (table of contents you can mirror)

The status doc is organised by CSS module:

1. Box model (margin, padding, border, border-radius)
2. Background (color, image, gradient, position)
3. Typography (font-family, font-size, font-weight, line-height, text-align, text-decoration)
4. Color (rgb / rgba / hsl / hsla / hex / named)
5. Display + positioning (block, inline, inline-block, none, position absolute/relative/fixed)
6. Flexbox (flex-direction, justify-content, align-items, align-content, order, flex-wrap — partial)
7. Grid V1 (grid-template-columns, grid-template-rows, grid-gap, grid-column-gap, grid-row-gap)
8. Transforms (rotate, scale, translate)
9. Effects (box-shadow, text-shadow, opacity)
10. Custom properties (var(), --custom)
11. Pseudo-classes / pseudo-elements (:hover, :first-child, ::before, ::after)
12. Media queries (min-width / max-width)
13. Viewport units (vh, vw)
14. Aspect-ratio
15. Counters
16. text-overflow, word-break, overflow-wrap

For each entry the status doc has: **status** (done / partial / planned / deferred) + **last verified** (fix number) + **probe URL** (where on `advanced.html` it's exercised).

## Caveats to surface on the page

- **"Done" means done on PowerPC G3 hardware**, not just compile-clean. Every "done" entry has a fix-number citation backing it.
- **"Partial" usually means parser-side done, layout/plot incomplete.** The exact gap is in the doc.
- **CSS Grid is V1 only.** No subgrid, no `grid-template-areas`, no named lines, no negative indexing yet. Explicit placement (`grid-column: A / B`) is the next round (fixes158, scoped).
- **No CSS Custom Layout, no Houdini, no @container, no @scope, no @starting-style.** The list is post-2020 CSS only insofar as MacSurf has caught up — major modern features deliberately out of scope.

## If `docs/css-status.md` looks out of date

It was generated 2026-05-19. Major features landed after that date through fixes157:
- fixes150 — CSS Grid `grid-template-columns/rows`
- fixes151 — Grid column placement (span, full-row, positional)
- fixes152 — aspect-ratio
- fixes157 — font-family aliases (sans → Helvetica, serif → Times, mono → Monaco)

If the page is going to be authoritative, request a refreshed `docs/css-status.md` from Patrick — easy ask, takes him ten minutes.
