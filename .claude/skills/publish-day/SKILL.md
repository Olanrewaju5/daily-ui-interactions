---
name: publish-day
description: Publish a finished daily build — update gallery and README, commit, push, and verify the live Vercel URL. Use after /verify-interaction passes.
---

# Publish the day's build

## Steps

1. **Gallery**: add the new build to root `index.html`, newest first, matching the existing card markup.
2. **README**: add a row to the top of the builds table — Day number, linked title, highlights sentence, tech.
3. **Commit**: `Day N: Title — short description` (follow-ups: `Day N update: …`). Stage only the build folder, `index.html`, and `README.md` — never `.env.local`.
4. **Push to `main`**. Vercel's git integration auto-deploys — do **not** run `vercel deploy` (it can stream logs past the Bash timeout even when the deploy succeeded).
5. **Verify live** (~20s after push):
   ```bash
   curl -s "https://daily-ui-interactions.vercel.app/daily-builds/<date>-<slug>/" | grep -i "<distinctive string from the build>"
   curl -s "https://daily-ui-interactions.vercel.app/" | grep -i "<slug>"
   ```
   If the grep misses, wait and retry once or twice before assuming failure — the deploy may still be building.
6. Report the live URL to the user.
