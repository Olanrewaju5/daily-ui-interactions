---
name: new-day
description: Scaffold today's daily UI build — folder, stub index.html, day number, and idea framing. Use at the start of each day's practice session.
---

# New Day scaffold

Set up today's build so the session starts at the fun part.

## Steps

1. **Determine the day number**: read the top row of the README builds table — today is that day + 1.
2. **Get the idea.** If the user gave one, use it. Otherwise propose 2–3 candidate interactions and let them pick. Draw from the user's inspiration bar (designspells.com, myMind, Family/Flashbacks-style mobile craft, award-site micro-interactions). Check the README table first — **don't repeat a spell already built** (e.g. the myMind "achievement unlocked" exists twice: Day 8 and Day 12).
3. **Vary the stack over time.** Look at the last ~5 builds' tech column and pick something that broadens range: vanilla springs, GSAP, Three.js, raw WebGL/GLSL, Matter.js, React + Framer Motion (import-map, no build), View Transitions, etc.
4. **Create the folder**: `daily-builds/<YYYY-MM-DD>-<slug>/` using **today's real date** (not the repo's start date — old folders are wrong, don't copy them).
5. **Stub `index.html`**: self-contained, viewport meta, dark-friendly background, a `<main>` stage, and an empty `<script>` block. CDN tags only if the chosen library needs them.
6. **State the plan in one paragraph**: the core interaction, the motion beats (entrance → interaction → reward/idle), and what "feels great" means for this one — then build.
7. **Spec the motion in `/motion-taste` vocabulary** before writing code: name the hero motion, its regime (expressive vs product-UI), and rough numbers (durations, easing, spring character, stagger). One sentence per animated element.

## During the build

- Add deterministic debug hooks as you go (`window.__seek(p)`, `window.__setState(...)`) — `/verify-interaction` depends on them.
- Synthesize sound with Web Audio; never ship audio files.
- Finish with the `/motion-taste` critique protocol, then `/verify-interaction`, then `/publish-day`.
