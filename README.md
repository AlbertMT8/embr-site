# EMBR — skilled hands, captured

Landing page for **EMBR** — egocentric, tactile, and mocap data captured from
skilled hands on real production lines.

A scroll-driven site built around 15 clips of real factory work: a full-bleed
hero clip track, a coverage section, a geography/accuracy section, and a
closing CTA.

## Live site

**https://ben-jpg-del.github.io/embr-site/**

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
| `clips/*.mp4` | Factory clips referenced as `clips/<slug>.mp4`. 15 present; the 6 welding clips (`c0*`) the hero registry also lists are **not yet in this repo** — see below. |
| `clips/thumbs/*.jpg` | Poster frames, used as each video's `poster`. |
| `embr-logo.png`, `embr-mark.png` | Brand assets. |

## Editing

Edit `EMBR.dc.html`, then mirror it to `index.html` to redeploy:

```bash
cp "EMBR.dc.html" index.html && git commit -am "Update site" && git push
```

## Missing hero clips

The hero rotation is six clips. Three of them are welding footage that lives in
the Claude Design project but not here, because the design-sync read caps at
256 KiB and these are multi-megabyte videos:

```
clips/c05_measure_long_span.mp4
clips/c07_arc_weld_electrode.mp4
clips/c09_alternate_angle_weld.mp4
```

`CLIPS` also registers `c01_corner_weld_sparks`, `c06_weld_setup_alignment` and
`c08_vertical_joint_fitup`, which nothing currently renders.

Until the files are added the rotation runs on the three clips it has: a video
that fails to load is marked `data-dead` and stepped over by `cycleHero`, so a
missing file costs a slot rather than showing black. Drop the `.mp4`s into
`clips/` and the full six-clip rotation starts working with no code change.

## Not published

The handoff `uploads/` folder (pitch deck PDF, screenshots, working notes, and
duplicate copies of the clips) is deliberately excluded from this repo, as is
the handoff `.zip` itself — see `.gitignore`.
