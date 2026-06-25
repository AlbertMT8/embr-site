# EMBR — Hero

Interactive hero for **EMBR · Tactile Data Systems**.

A point-cloud rendering of a human hand on an HTML canvas. At rest the cursor
"captures" nearby points (mocap-style tracking bracket, gold tracer links, live
X/Y/pressure readout). **As you scroll**, the hand point-cloud disperses into a
contact-data field, the `FIG.01` label flips to `FIG.02 — CONTACT DATA FIELD`,
and a three-column panel reveals the story: `01 / DATA`, `02 / ENVIRONMENT`
(recorded in live factories), `03 / SCALE` (30,000+ workers).

## Live site

Served via GitHub Pages: **https://ben-jpg-del.github.io/embr-hero/**

## How it's hosted

The page is the actual Claude Design component running standalone via its
runtime. `index.html` loads `support.js`, which boots React/ReactDOM (UMD, from
unpkg) and renders the `<x-dc>` component — pixel-identical to the design. The
only runtime dependencies are the unpkg CDN (React/ReactDOM) and Google Fonts
(JetBrains Mono).

## Files

| File | Purpose |
| --- | --- |
| `index.html` | Served entry — a copy of `EMBR Hero.dc.html`. This is what GitHub Pages serves. |
| `EMBR Hero.dc.html` | **Canonical Claude Design source** (`<x-dc>` markup + `class Component extends DCLogic`), imported from the [design project](https://claude.ai/design/p/552b8884-0864-4521-900f-37a2097657ff) handoff bundle. The scroll experience. |
| `support.js` | Claude Design (`dc-runtime`) — parses `<x-dc>`, compiles the logic, mounts via React. |
| `EMBR Hero.html` | **v1 archived bundle** — the earlier *static* hero (single 100vh, no scroll). Fully self-contained (fonts + runtime inlined, no CDN). Kept for reference; not served. |

## Source

Built in [Claude Design](https://claude.ai/design/p/552b8884-0864-4521-900f-37a2097657ff).
Edit `EMBR Hero.dc.html`, then mirror it to `index.html` to redeploy.
