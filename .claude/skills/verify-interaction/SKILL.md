---
name: verify-interaction
description: Verification recipes for daily UI builds — deterministic screenshots of animated/scrubbed/physics states, WebGL and GSAP gotchas, viewport checks. Use before calling any build done.
---

# Verify an interaction build

Never call a build done on faith. Drive it, screenshot the key states, and check the console. These recipes were learned the hard way — follow them instead of rediscovering.

## Core loop

1. Serve the build's folder and open it in the browser preview (`preview_start`).
2. `read_console_messages` — zero errors is the bar.
3. Screenshot each key state: initial, mid-interaction, completed/reward, and any idle loop.
4. `resize_window` to mobile (375px) and re-check layout + the primary interaction.
5. If anything is off: fix source, reload, repeat.

## Deterministic states (the preview throttles rAF in background tabs — animations won't settle on their own)

- **Expose debug hooks in every build**: e.g. `window.__setOpen(v)`, `window.__seek(p)`, `window.__settle(n)`. Call them via `javascript_tool`, then screenshot.
- **GSAP timelines**: store on `window.__tl`; jump with `__tl.progress(1)` for the end state.
- **ScrollTrigger scrubs**: don't scroll — expose `window.__seek(p)` that calls `tl.scrollTrigger.disable(false)` then `tl.progress(p)` (otherwise the rAF scrub reverts it).
- **Physics (Matter.js)**: expose a `window.__settle(n)` that steps `Engine.update` + `Render.world` n times headlessly.

## WebGL / shader gotchas

- Verify shader output with a **screenshot**, not `readPixels` — it reads transparent after compositing unless `preserveDrawingBuffer: true`.
- Check `gl.getShaderParameter(s, COMPILE_STATUS)` and `getProgramParameter(p, LINK_STATUS)` and surface errors visibly.
- Call WebGL `init()` **after** all module-scope `const`s are declared (TDZ ReferenceErrors silently abort setup).
- Size the canvas in `init()` too, not only in the throttled rAF loop; floor responsive widths with `clamp(300px, …)` — `92vw` can be 0 in the preview after reload.
- Volumetric glow: track closest approach `dmin = min(dmin, d)` and add halo `exp(-dmin*k)` only for missed rays; per-step `sum += c/(eps+d*d)` blows out white near surfaces.

## Animation gotchas

- GSAP writes the **whole** `transform` — it clobbers CSS `translate(-50%,-50%)` centering (use `xPercent/yPercent: -50` or margin centering) and authored SVG `transform` attributes (animate the parent `<g>` with `svgOrigin` instead).
- Don't drive reversible reveals with Web Animations API + `fill: 'forwards'` — the fill overrides inline styles and `cancel()` won't reliably revert. Lerp a plain value in the rAF loop instead.
- `mix-blend-mode: color-dodge` foil is invisible over near-white — use a mid-tone pearl/silver base.
- Separate entrance animation (outer wrapper, CSS keyframes) from cursor-tilt (inner wrapper, JS transform) so they don't fight over `transform`.

## Performance

- Primary interaction should hold ~60fps: animate transform/opacity, no layout reads inside rAF loops.
- No-build React/Framer Motion pages need `react/jsx-runtime` (and `jsx-dev-runtime`) in the import map, and must be verified via the preview server (inline widgets ignore injected import maps; `npx http-server`, not python, under the preview sandbox).
