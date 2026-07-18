# CLAUDE.md — Daily UI Interactions

A daily practice repo: one small, finishable UI interaction per day, focused on *feel* — easing, spring physics, choreography, micro-detail. Built with Claude Code, published to Vercel.

- **Live:** https://daily-ui-interactions.vercel.app
- **GitHub:** https://github.com/Olanrewaju5/daily-ui-interactions (`main` auto-deploys via Vercel git integration)

## Conventions

- Each build is a **self-contained `index.html`** in `daily-builds/<YYYY-MM-DD>-<slug>/` — use **today's actual date**. No build step, no local node_modules.
- Mostly framework-free (vanilla HTML/CSS/JS, hand-rolled springs, rAF loops). When a build explores a library (GSAP, Three.js, Matter.js, React + Framer Motion), load it from a CDN — global script tag or import map via esm.sh.
- Every new build must also be added to:
  1. the root `index.html` gallery (newest first)
  2. the `README.md` builds table (newest first)
- Commit message format: `Day N: Title — short description`. Follow-ups: `Day N update: what changed`.
- Prefer bite-sized and polished over sprawling. Lead with the interaction/motion idea. Sound (Web Audio, synthesized — no audio files) and haptic-feel details are encouraged.

## Workflow skills (in `.claude/skills/`)

- `/new-day` — scaffold today's build folder + stub, pick the day number
- `/verify-interaction` — hard-won verification recipes (GSAP seek hooks, WebGL screenshot gotchas, debug hooks); use before calling a build done
- `/publish-day` — gallery/README updates, commit, push, live-URL verification

## Quality bar

Before calling a build done:
- Run `/verify-interaction` and screenshot the key states.
- No console errors; works at 375px (mobile) and 1280px (desktop) viewports.
- Interactions should hold ~60fps; prefer transform/opacity animation, avoid layout thrash in rAF loops.
- Get a fresh-eyes critique: run the `interface-craft` design-critique skill (or a subagent) on the finished build and address the top findings.

## Environment notes

- The repo path contains a colon (`Design:Build with AI`) — always quote paths in shell commands.
- No `ffmpeg` on this machine. Extract video frames with a throwaway Swift script via `xcrun swift` (AVAssetImageGenerator) or `qlmanage -t` for a single poster frame.
- `timeout`/`gtimeout` are not available in this shell.
- `.env.local` must stay gitignored.
