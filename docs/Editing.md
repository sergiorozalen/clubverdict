# Editing and publishing

[← Home](Home.md)

## Where the source of truth is

`index.html` in this repo is what's live. On the Mac, `site/page_template.html` is the template and `site/update_site.py` refreshes the embedded snapshot and injects the Supabase URL and publishable key from `.env`. When changing the page in this repo, copy the change back to the template too, or the next snapshot refresh from the Mac will overwrite it.

## Publishing

GitHub Pages serves the `main` branch. Every push to `main` is live within a minute or two; a hard refresh (Cmd+Shift+R) skips the browser cache.

## Changing the page safely

1. Edit `index.html` (it is plain HTML, CSS and JavaScript, no build step).
2. Test locally: open the file in a browser. It uses the live database exactly as the published site does.
3. Check both leagues, all four tabs, a club with a postponed game, dark mode, and a phone-width window.
4. Commit and push.

## Rules

- Only the **publishable** Supabase key goes in this repo. Never the secret key.
- New database tables the page needs must have a public read policy (see the pipeline repo's *Operations* page).
- Keep external scripts on pinned versions from trusted CDNs.
