# Daily UI Interactions

A daily practice of unique UI interactions, micro-interactions, and animation — built with the latest Claude models. One small, finishable thing at a time, with a focus on *feel*: easing, spring physics, choreography, and the tiny details that push a UI toward award-winning quality.

**Live:** deployed on Vercel · **Each build** is a self-contained `index.html` (no build step — just open it).

## Builds

| Day | Build | Highlights | Tech |
|-----|-------|-----------|------|
| 01 | [Adaptive Slider](./daily-builds/2026-06-24-adaptive-slider/) | $0–$1,500 amount picker — odometer number with per-digit motion blur, value-driven color, $100 ratchet ticks, theme switcher with a circular reveal | SVG filters, Web Audio, View Transitions API |
| — | [Liquid Toggle](./daily-builds/2026-06-24-liquid-toggle/) (warm-up) | Drag-and-fling gooey switch with throw physics and a synthesized water-drop pop | SVG goo filter, spring physics, Web Audio |

## Stack

No framework, no bundler. Plain HTML/CSS/JS with hand-rolled spring physics and `requestAnimationFrame` loops — kept deliberately dependency-free so each interaction can be read end-to-end in one file.

## Local preview

```bash
# any static server works, e.g.
python3 -m http.server 8000
# then open http://localhost:8000
```

---

Built with [Claude Code](https://claude.com/claude-code).
