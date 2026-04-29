# Rollback Plan — .info Site

## Current Production State (post-merge)

- **Commit:** `feat/black-glass-v2` merged to `main`
- **Theme:** Glass Runway / Neon Horizon (Black Glass v2)
- **Routes:** `/` (Field Guide), `/reject-return` (stub), `_redirects` catch-all

## Prior State (rollback target)

- **Commit:** `43ac756` — "fix: add Resume Builder link with correct alignment to nav + footer"
- **Date:** April 3, 2026

## Rollback Command

To revert the live site to the April 3 state:

```bash
cd thispagedoesnotexist12345-info
git revert HEAD --no-edit
git push origin main
```

Netlify will auto-deploy the revert within ~2 minutes.

## Selective Rollback (index.html only)

```bash
git checkout 43ac756 -- index.html
git commit -m "revert: restore index.html to 43ac756 (pre-Black-Glass-v2)"
git push origin main
```

## What is NOT rolled back by the above

- `reject-return/index.html` — stub page (safe to leave in place)
- `_redirects` — catch-all 301 (safe to leave in place)
- `downloads/The-Ultimate-Journey-Dashboard-Template.xlsx` — V5 asset (safe to leave in place)
- `ROLLBACK.md` — this file

To remove all Phase 1 additions entirely, use `git revert HEAD` which reverts the full merge commit.
