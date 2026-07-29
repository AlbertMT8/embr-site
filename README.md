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
| `clips/*.mp4` | 21 clips referenced as `clips/<slug>.mp4` — 15 assembly (`01`–`15`) plus 6 welding (`c0*`). |
| `clips/thumbs/*.jpg` | Poster frames, used as each video's `poster`. |
| `embr-logo.png`, `assets/embr-mark.png` | Brand assets. |
| `favicon.ico`, `icon.png`, `apple-touch-icon.png` | Site favicons, generated from `assets/embr-mark.png`. |

## Editing

Edit `EMBR.dc.html`, then mirror it to `index.html` to redeploy:

```bash
cp "EMBR.dc.html" index.html && git commit -am "Update site" && git push
```

## Hero rotation

Six clips, alternating assembly and welding footage:

```
15_door_latch_installation   c09_alternate_angle_weld
14_rod_wiring_routing        c05_measure_long_span
09_panel_surface_inspection  c07_arc_weld_electrode
```

The welding clips ship without poster frames, so `CLIPS` marks them `noThumb`
and `prepMedia` skips the `poster` assignment for them.

Hero clips are attached by `warmUp()` rather than all at once: Chrome discards
the buffered media of a paused offscreen `<video>` and re-downloads it, so the
two lead clips attach immediately and the rest stagger in. A clip that fails to
load is marked `data-dead` and stepped over by `cycleHero`, so a missing or
broken file costs a slot instead of fading the hero to black.

`CLIPS` also registers `c01_corner_weld_sparks`, `c06_weld_setup_alignment` and
`c08_vertical_joint_fitup`. Their files are present but nothing renders them yet
— they are there to be swapped into `HERO`.

## Not published

The handoff `uploads/` folder (pitch deck PDF, screenshots, working notes, and
duplicate copies of the clips) is deliberately excluded from this repo, as is
the handoff `.zip` itself — see `.gitignore`.
