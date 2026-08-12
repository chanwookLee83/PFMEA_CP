# PFMEA / CP AI — notes for Claude

## Workflow

- After making code changes in this repo, always: bump the service worker
  cache version in `sw.js` (`CACHE_NAME`, e.g. `pfmea-cp-v2.9` → `v3.0`) so
  existing PWA installs pick up the new build, then `git commit` and
  `git push` to `origin/main` — without waiting for the user to ask each
  time. This repo has no build/deploy step beyond static files, so a push
  to `main` is the full "ship it" action (GitHub Pages, if enabled, picks
  it up automatically).
- Still use judgment: skip the auto-push for exploratory/incomplete work
  the user hasn't confirmed, or if a change is clearly experimental.
