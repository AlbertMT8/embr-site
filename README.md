# EMBR — skilled hands, captured

Landing page for **EMBR** — egocentric, tactile, and mocap data captured from
skilled hands on real production lines.

A scroll-driven site built around 15 clips of real factory work: a full-bleed
hero clip track, a coverage section, a geography/accuracy section, and a
closing CTA.

## Live site

**https://ben-jpg-del.github.io/embr-hero/**

## How it's hosted

The page is the Claude Design component running standalone via its runtime.
`index.html` loads `support.js`, which boots React/ReactDOM (UMD, from unpkg)
and renders the `<x-dc>` component — pixel-identical to the design. Runtime
dependencies: unpkg (React/ReactDOM) and Google Fonts (Archivo + JetBrains Mono).

## Files

| Path | Purpose |
| --- | --- |
| `index.html` | Served entry — a copy of `EMBR.dc.html`. This is what GitHub Pages serves. |
| `EMBR.dc.html` | **Canonical Claude Design source** (`<x-dc>` markup + `class Component extends DCLogic`). |
| `EMBR Animation Options.dc.html` | Design exploration of overlay animation variants. Not linked from the site. |
| `support.js` | Claude Design runtime (`dc-runtime`) — parses `<x-dc>`, compiles the logic, mounts via React. |
| `clips/*.mp4` | 15 factory clips referenced as `clips/<slug>.mp4`. |
| `clips/thumbs/*.jpg` | Poster frames, used as each video's `poster`. |
| `embr-logo.png`, `embr-mark.png` | Brand assets. |

## Editing

Edit `EMBR.dc.html`, then mirror it to `index.html` to redeploy:

```bash
cp "EMBR.dc.html" index.html && git commit -am "Update site" && git push
```

## Not published

The handoff `uploads/` folder (pitch deck PDF, screenshots, working notes, and
duplicate copies of the clips) is deliberately excluded from this repo, as is
the handoff `.zip` itself — see `.gitignore`.
