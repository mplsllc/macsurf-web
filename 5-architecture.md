# Tier 3 — Architecture page

## Existing material

[`docs/architecture.md`](https://github.com/mplsllc/macsurf/blob/master/docs/architecture.md) in the macsurf repo is the source of truth. It's a substantial prose document covering:

- Rendering pipeline: fetch → parse → CSS cascade → layout → QuickDraw plot
- Front-end module map (`browser/netsurf/frontends/macos9/`)
- Open Transport networking model + cooperative-multitasking constraints
- Memory model (16 MB Carbon partition + 2 MB image cache + 128 fetcher slots)
- Plotter back buffer (offscreen GWorld since fixes77g)
- libcss / libdom / libhubbub / libparserutils library wiring

**Harvest this directly.** It's already structured for a doc page.

## No diagram exists yet

There is no SVG / image architecture diagram in the repo. Two options:

1. **Prose-only page now** (recommended). Use `docs/architecture.md` content, format as the website page.
2. **Draft a diagram for review.** If you (the website agent) want to mock one up, the rough shape is:

   ```
   Browser side (Mac OS 9, PowerPC, CW8):
     Event loop ──> NetSurf core ──> libcss / libdom / libhubbub / Duktape JS
            ↑                            │
            │                            ↓
       QuickDraw  ←── Plotter table ←── Layout
            ↑
       Carbon UI (WaitNextEvent, Controls, TextEdit URL bar)
            ↑
       Open Transport TCP ──> Go proxy (TLS-stripping) ──> Modern web
   ```

   But run that past Patrick before publishing — the real architecture has nuances (offscreen GWorld back buffer, JS engine living inside the NetSurf core, the macSSL sibling project for native HTTPS) that a clean diagram can elide misleadingly.

## What NOT to claim

- Don't claim macSSL is wired into the browser yet — it's a sibling library, not yet integrated.
- Don't claim a JIT — Duktape is a tree-walking interpreter.
- Don't claim preemptive threading — there is none. Cooperative multitasking only.
