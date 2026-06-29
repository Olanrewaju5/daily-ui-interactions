# Daily UI Interactions

A daily practice of unique UI interactions, micro-interactions, and animation — built with the latest Claude models. One small, finishable thing at a time, with a focus on *feel*: easing, spring physics, choreography, and the tiny details that push a UI toward award-winning quality.

**Live:** deployed on Vercel · **Each build** is a self-contained `index.html` (no build step — just open it).

## Builds

| Day | Build | Highlights | Tech |
|-----|-------|-----------|------|
| 05 | [Scratch to Reveal](./daily-builds/2026-06-24-scratch-reveal/) | Google Pay–style scratch card — canvas destination-out erasing, trailing sparkles, auto-complete confetti burst + reward chime | Canvas 2D, particle system, Web Audio |
| 04 | [Proximity Drawer](./daily-builds/2026-06-24-empty-state-drawer/) | Empty-state with a hand-built isometric filing cabinet; the drawer slides open as the cursor nears, with rolling-slide + wooden-clunk audio | Hand-built SVG isometric projection, Web Audio |
| 03 | [Expanding Cards](./daily-builds/2026-06-24-expanding-cards/) | Destinations grid that morph-expands into a detail view and back — shared-element transition with no FLIP math | React, Framer Motion (layoutId + AnimatePresence) |
| 02 | [Drag-to-Reorder List](./daily-builds/2026-06-24-reorder-list/) | "Up Next" playlist where dragging a track springs the others out of the way — drag handle, lift-on-grab, soft blip per swap | React, Framer Motion (Reorder) |
| 01 | [Adaptive Slider](./daily-builds/2026-06-24-adaptive-slider/) | $0–$1,500 amount picker — odometer number with per-digit motion blur, value-driven color, $100 ratchet ticks, theme switcher with a circular reveal | SVG filters, Web Audio, View Transitions API |
| — | [Liquid Toggle](./daily-builds/2026-06-24-liquid-toggle/) (warm-up) | Drag-and-fling gooey switch with throw physics and a synthesized water-drop pop | SVG goo filter, spring physics, Web Audio |

## Stack

Mostly framework-free — plain HTML/CSS/JS with hand-rolled spring physics and `requestAnimationFrame` loops, kept dependency-free so each interaction reads end-to-end in one file. Builds that explore a specific library (e.g. Day 2 uses React + Framer Motion) load it from a CDN via an import map, so there's still no build step.

## Local preview

```bash
# any static server works, e.g.
python3 -m http.server 8000
# then open http://localhost:8000
```

---

Built with [Claude Code](https://claude.com/claude-code).
