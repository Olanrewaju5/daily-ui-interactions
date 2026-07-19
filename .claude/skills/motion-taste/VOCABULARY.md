# Motion vocabulary & prompting phrasebook

Shared language (after animations.dev/vocabulary + 60fps.design glossary). The point: **precise vocabulary produces precise prompts.** "Make it smoother" is slop-bait; "180ms ease-out, origin-aware, interruptible" is a spec.

## Entrances & exits
- **Fade / Slide / Scale in** — the basic three; scale usually pairs with fade (start ~0.95, not 0).
- **Pop in** — entrance with slight overshoot (spring or back-out bezier).
- **Reveal** — uncover via clip-path/mask rather than moving the element.
- **Origin-aware** — element grows from its trigger (menu from its button), not from its own center.
- **Exit** — faster and plainer than the entrance; users have already moved on.

## State transitions
- **Crossfade** — out/in in place; the reduced-motion fallback for almost everything.
- **Morph** — one shape continuously becomes another (Dynamic Island).
- **Shared element / continuity transition** — an element keeps its identity while traveling between layouts (Framer Motion `layoutId`, View Transitions API).
- **Layout animation** — size/position changes animate instead of snapping.
- **Direction-aware** — hover/transition responds to which side the cursor/navigation came from.

## Sequencing
- **Stagger** — same animation, per-item delay (20–50ms). **Orchestration** — different animations timed to read as one motion. **Choreography** — the whole plan: what leads, what follows, what's instant.
- **Overlap, don't queue** — start the next element before the previous finishes; sequential-blocking reads as slow.

## Physics & feel
- **Spring (stiffness / damping / mass / velocity)** — motion from physics, not duration. Low damping = bounce. High mass = heavy/sluggish.
- **Interruptible** — retarget mid-flight preserving velocity; the difference between "feels native" and "feels webby."
- **Momentum / inertia** — released drags keep velocity and decelerate.
- **Rubber-banding** — resistance past a boundary + snap back (iOS overscroll).
- **Follow-through / overshoot** — settle slightly past the target, return; adds weight.
- **Squash & stretch** — deformation conveying mass (expressive work only; ≤10% in UI).
- **Anticipation** — tiny counter-move before the main move (wind-up).

## Easing
- **ease-out** — fast→slow; default for anything the user initiated.
- **ease-in** — slow→fast; only for exits, if at all.
- **ease-in-out** — for elements already on screen moving A→B.
- **linear** — spinners and marquees only.
- **Asymmetric bezier** — accelerates and decelerates at different rates; feels more alive than symmetric. Handy curves: `cubic-bezier(0.32, 0.72, 0, 1)` (iOS-sheet feel), `cubic-bezier(0.34, 1.56, 0.64, 1)` (back-out pop).

## Feedback
- **Press feedback** — scale-down on pointer-down (0.96–0.98), spring back on release.
- **Hold-to-confirm** — progress fills while held; release cancels.
- **Shake / wiggle** — 2–3 fast x-oscillations = error/rejection.
- **Skeleton / shimmer** — loading placeholder with moving sheen.
- **Number ticker + tabular-nums** — rolling digits; fixed-width so layout doesn't shift.
- **Optimistic UI** — show the result before the server confirms; motion covers latency (perceived performance).

## Scroll
- **Scroll reveal** (enters once on viewport entry) vs **scroll-driven** (progress bound to scroll position) vs **parallax** (layers at different speeds — needs a depth story to justify itself).
- **Pin/scrub/snap** — hold a stage while scroll scrubs a timeline; snap to beats.

## Ambient
- **Idle animation / float / pulse** — sub-pixel-slow life in a resting element; must be ignorable.
- **Marquee / orbit / loop (alternate-yoyo)** — continuous; linear is correct here.

## Performance words
- **Compositing** — transform/opacity animate on the GPU; width/height/top/left trigger layout (**layout thrash**, **jank**).
- **will-change** — promotion hint; apply just before, remove after.
- **FPS budget** — 60fps = 16.7ms/frame; no layout reads inside rAF loops.

## Prompt patterns (for working with AI)

Spec motion like an art director, one sentence per element:

> "Dialog enters 220ms ease-out, scale 0.96→1 + fade, origin top; backdrop fades 150ms; exit 140ms, no scale. Interruptible."

> "List items stagger in 30ms apart, each 200ms ease-out slide-up 12px + fade; cap the stagger at 8 items, rest appear instantly."

> "Press feedback on every card: scale 0.97 on pointer-down (~80ms), spring back stiffness 400 damping 30. No hover animation on mobile."

Name the *feel* with a reference, then the numbers: "iOS-sheet feel", "Dynamic Island morph", "Raycast-instant (no animation)", "myMind reward moment (expressive, one-off)".
