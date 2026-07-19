---
name: motion-taste
description: Taste pass for motion and interaction work — anti-slop checklist, numeric defaults for durations/easing/springs/stagger, the 12 principles with restraint warnings, and a comparative critique protocol. Run during design and again before calling a build done.
---

# Motion taste pass

Distilled from Emil Kowalski's essays, the animations.dev vocabulary, the 12 principles of animation, and the craft bar of 60fps.design / detail.design. Use it twice: when *choosing* the motion design, and as a critique pass before shipping. See [VOCABULARY.md](VOCABULARY.md) for the full term glossary and prompting phrasebook.

## 0. Regime check (do this first)

- **Product UI regime** — buttons, menus, forms, navigation: restraint wins. Frequency of use is the master variable; the best animation is often none.
- **Expressive regime** — toys, showcases, rewards, onboarding, empty states (this repo's daily builds): the 12 principles apply, exaggeration is allowed, but every motion still needs a *purpose* (orient, feedback, relationship, delight-once).

Most AI slop comes from applying the expressive regime to product UI. Know which one you're in.

## 1. Anti-slop checklist (the tells)

Kill any of these on sight:

- **Everything animates equally** — no hierarchy, no staging. Pick ONE hero motion per view; everything else supports or is instant.
- **Uniform 400–500ms ease-in-out on everything** — the default slop signature. User-initiated = fast ease-out.
- **Animation on high-frequency actions** — anything used many times per session gets faster + subtler, or nothing. Keyboard-initiated actions get *zero* animation.
- **Entrance animation replay** on every re-render/reopen of something the user sees constantly.
- **Non-interruptible motion** — rapid open/close must redirect smoothly mid-flight, never queue or snap.
- **Animation blocking input** — never make the user wait for motion to finish before they can act.
- **Bounce on everything** — overshoot is seasoning, not sauce. One bouncy element per view, max.
- **Slow stagger** — stagger that makes the user wait for row 8. Delay 20–50ms per item, total sequence under ~400ms, cap the count.
- **Decorative parallax / floating blobs / gradient shimmer** with no informational or emotional job.
- **Symmetric linear motion** — linear easing anywhere except spinners and marquees.
- **No reduced-motion path** — respect `prefers-reduced-motion` (crossfade instead of movement; keep opacity feedback).

## 2. Numbers that matter (defaults, not laws — deviate on purpose)

| Motion | Duration | Easing |
|---|---|---|
| Hover response | 150–200ms | ease-out |
| Press feedback | scale 0.96–0.98, ~100ms down, spring back | ease-out |
| Tooltip / dropdown / popover in | 150–200ms | ease-out |
| Dialog / sheet in | 200–300ms | ease-out or soft spring |
| Exit (any) | ~2/3 of the entrance, or instant | ease-in acceptable here only |
| On-screen A→B move | 200–350ms | ease-in-out or spring |
| Stagger step | 20–50ms | total < 400ms |
| Expressive hero moment | 400–700ms | custom bezier or underdamped spring |
| Anything UI | **< 300ms** (Emil's rule) | — |

Springs (rough Framer-Motion-scale anchors): snappy UI ≈ stiffness 300–500, damping 25–35 (no visible bounce); playful ≈ stiffness 200–300, damping 15–22 (one overshoot); heavy/dramatic ≈ lower stiffness, higher mass. Perceived settle matters more than mathematical rest.

Origin: animate **from the trigger** (transform-origin at the button that opened it), not from center. Distance: enter from 8–16px away, not from across the screen.

## 3. The 12 principles, with restraint warnings

- **Timing, Slow in/out, Follow-through, Staging, Anticipation** — safe everywhere; these ARE the craft.
- **Arcs, Secondary action, Solid drawing** — use in expressive work; in product UI only when subtle.
- **Squash & stretch, Exaggeration** — expressive regime only, and even there: deform ≤ ~10% for anything that isn't a character/toy.
- **Straight-ahead vs pose-to-pose** — in UI: define states and interpolate (pose-to-pose); hand-animate frames only for character work.
- **Appeal** — the output metric, not an input. Users say "feels good," never "nice bezier."

## 4. Critique protocol (train the judgement while shipping)

Before calling motion done:

1. **The delete test** — for each animation ask: would this interaction be *better* with no animation? If unsure, it would.
2. **A/B one variable** — render the key motion at duration ±30% (or damping ±30%) and pick the winner *and say why in one sentence*. If you can't articulate why, you haven't looked hard enough. Do this for the hero motion at minimum.
3. **The tenth-time test** — trigger the interaction 10 times fast. Still pleasant? Interruptible? Anything that irritates on rep 10 gets shortened or cut.
4. **Frequency audit** — list every animated element; for each, estimate uses/session; anything high-frequency moves toward instant.
5. **Reduced-motion pass** — toggle `prefers-reduced-motion` and confirm the build still communicates.

## 5. Active study (when drawing from galleries)

Never skim 60fps.design / detail.design / transitions.dev for vibes. Protocol: pick ONE shot → name its moves in vocabulary terms → *estimate* durations, easing, and stagger before any frame-stepping → rebuild or note the gap. One shot studied deeply beats fifty scrolled.
