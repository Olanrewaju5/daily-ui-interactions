# Daily UI Interactions

A daily practice of unique UI interactions, micro-interactions, and animation — built with the latest Claude models. One small, finishable thing at a time, with a focus on *feel*: easing, spring physics, choreography, and the tiny details that push a UI toward award-winning quality.

**Live:** deployed on Vercel · **Each build** is a self-contained `index.html` (no build step — just open it).

## Builds

| Day | Build | Highlights | Tech |
|-----|-------|-----------|------|
| 16 | [Memory Lane Timeline](./daily-builds/2026-06-24-memory-lane/) | Editorial photo-timeline slider — drag/fling slides, filmstrip scrubber that re-centres the active frame with dock falloff, peeking neighbours, photo parallax, self-drawing handwritten arrows | Vanilla spring physics, CSS 3D, SVG |
| 15 | [Vintage Turntable](./daily-builds/2026-06-24-vinyl-player/) | Interactive record player — spinning vinyl, dropping tonearm, live VU meter; play/pause/stop/skip a generative lo-fi loop with vinyl crackle | Web Audio (generative), CSS turntable |
| 14 | [Candy Jar — Physics](./daily-builds/2026-06-24-physics-jar/) | Tactile Matter.js sandbox — colorful shapes fall and pile, drag to fling, shake to jumble, drop more; collision plinks scaled to impact | Matter.js rigid-body physics |
| 13 | [Raymarched Metaball](./daily-builds/2026-06-24-raymarch-blob/) | 3D from pure shader math — metaball SDFs + smooth-min, raymarched with gradient normals for lighting, iridescent fresnel rim, cursor-reactive bulge + rotation | WebGL, GLSL raymarching, SDF |
| 12 | [Holographic Achievement](./daily-builds/2026-06-24-holographic-achievement/) | myMind-style holographic card — drop-in bounce, cursor-tilt foil shimmer, then click to flip (rotateY) revealing a gold-medal award with a confetti burst | CSS 3D transforms, blend-mode foil, canvas confetti |
| 11 | [Grow — Scroll Story](./daily-builds/2026-06-24-scrolltrigger-grow/) | Pinned scroll-driven story (GSAP ScrollTrigger) — plant grows seed→bloom across 4 beats, sky crossfades, stem draws, snap-to-beat + progress rail | GSAP ScrollTrigger (pin, scrub, snap) |
| 10 | [Cloth in the Wind](./daily-builds/2026-06-24-threejs-cloth/) | Real-time Verlet cloth in Three.js — particle grid + distance constraints, traveling wind, gravity drape, cursor-push collision, lit folds | Three.js, Verlet integration |
| 09 | [Liquid Light](./daily-builds/2026-06-24-liquid-shader/) | Raw GLSL fragment shader — domain-warped fBm noise → iridescent palette, cursor-reactive swirl + glow, rendered per-pixel on the GPU | WebGL, GLSL |
| 08 | [Achievement Unlocked](./daily-builds/2026-06-24-achievement-unlocked/) | myMind-style reward — GSAP-choreographed light-ray sunburst, 3D medal pop with gloss sweep, confetti burst, staggered text, idle shimmer | GSAP timeline (3D), canvas particles, Web Audio |
| 07 | [Morning Brew](./daily-builds/2026-06-24-gsap-brew/) | A coffee brew choreographed on one GSAP timeline — cup fills, steam rises, checkmark pops, each step offset; pour + ding audio | GSAP timeline, SVG, Web Audio |
| 06 | [Interactive Zipper](./daily-builds/2026-06-24-interactive-zipper/) | Flashbacks-style onboarding — drag the pull to unzip a widening V of splaying teeth, revealing the screen behind; per-tooth zip clicks + reveal chime | Parametric SVG, spring drag, Web Audio |
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
