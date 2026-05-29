# Tier 3 — Version history

Two sources of truth, **prefer (a)**:

## (a) `docs/HISTORY.md` in the macsurf repo — authoritative timeline

[`docs/HISTORY.md`](https://github.com/mplsllc/macsurf/blob/master/docs/HISTORY.md) is a hand-written milestone timeline already structured for narrative consumption. Use this as the primary source for the version-history page — it groups commits into versioned milestones with explanation.

The other source of truth is `CLAUDE.md` at the repo root (also in git history), which has a per-fix log going back to v0.2. **Don't surface CLAUDE.md publicly** — it's an internal engineering journal. Pull facts from it, then rewrite for the website. Patrick will review the rewritten version before publishing.

## (b) Git tags (sparse — only major milestones tagged)

```
v0.4.5-fixes77g     — offscreen GWorld composite landed
v0.4.1              — first CSS3 hardware render
v0.4-css-applies    — CSS cascade applies on G3 hardware (the milestone)
v0.1.0-first-fetch  — first successful HTTP fetch over Open Transport
```

These are too sparse for a real version-history page on their own — use them as anchor points and fill in between them from `docs/HISTORY.md` + CLAUDE.md.

## Suggested page structure

```
v0.5  — current        — fixes157 font-family aliases, fixes156 clamp fix, full CSS Grid V1
v0.4  — May 2026       — CSS3 cascade on G3 hardware, all major properties
v0.3  — April 2026     — Full NetSurf pipeline, CSS cascade with var()
v0.2  — March 2026     — Plain text + JS via Duktape
v0.1  — April 2026     — First HTTP fetch over Open Transport
```

(Dates from git log on commits matching `v0.X` tag patterns. Sanity-check against `docs/HISTORY.md`.)
