# EMBR — Hero

Interactive hero section for **EMBR · Tactile Data Systems**.

A point-cloud rendering of a human hand on an HTML canvas. Moving the cursor
"captures" nearby points — a mocap-style tracking bracket, tactile readout
(X/Y/pressure), and gold tracer links follow the pointer.

## Live site

Served via GitHub Pages from [`index.html`](index.html).

## Files

| File | Purpose |
| --- | --- |
| `index.html` | Self-contained, deployable bundle (DC runtime + fonts + markup + canvas logic inline). This is what GitHub Pages serves. |
| `EMBR Hero.html` | Identical copy of the original bundle export. |
| `EMBR Hero.dc.html` | Claude Design source (`<x-dc>` component + `DCLogic`). Imported from the [Claude Design project](https://claude.ai/design/p/552b8884-0864-4521-900f-37a2097657ff). |

## Source

Built in [Claude Design](https://claude.ai/design/p/552b8884-0864-4521-900f-37a2097657ff).
The `.dc.html` is the editable component source; `index.html` is its bundled,
standalone build.
