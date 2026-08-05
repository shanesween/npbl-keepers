# NPBL 2026 Keeper Board

Static single-page keeper declaration sheet for the NPBL fantasy football league.
Everything is in `index.html` — no build step, no dependencies, no data leaves the page.

## Deploy to GitHub Pages

```bash
gh repo create npbl-keepers --public --source=. --remote=origin
git init && git add -A && git commit -m "2026 keeper board"
git branch -M main && git push -u origin main
gh api -X POST repos/:owner/npbl-keepers/pages -f source[branch]=main -f source[path]=/
```

Without the `gh` CLI: create the repo on github.com, push, then
**Settings → Pages → Source: Deploy from a branch → main / (root)**.

Live at `https://<user>.github.io/npbl-keepers/` within a minute or two.

## Notes

- `.nojekyll` stops GitHub's Jekyll build from touching the file.
- `noindex,nofollow` is set — the page won't show up in search, but the URL is public
  to anyone who has it. There's nothing sensitive here, just rosters.
- Checkboxes are native inputs, so they still toggle if JavaScript is blocked. The
  counter, round-clash check and copy button need JS, which is why this needs to be
  a real URL rather than an emailed attachment.

## Regenerating

Rebuilt from the 2025 final rosters, draft results and full transaction log. Source
data and the generator live outside this repo — edit `index.html` directly for small
copy fixes, or regenerate for anything touching prices or eligibility.
