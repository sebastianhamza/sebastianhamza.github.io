# AGENTS.md

Hugo blog (vendored Cactus theme) deployed to GitHub Pages via GitHub Actions.

## Build & verify

```powershell
hugo --minify --gc      # production build into public/
hugo server -D          # local preview (includes drafts) at localhost:1313
```

Requirements: Hugo **extended** >= 0.158 and the **standalone** Dart Sass
(`sass` on `PATH`). On this machine: `%LOCALAPPDATA%\Programs\dart-sass`. Do not
use `npm install -g sass` — it lacks Hugo's embedded protocol and builds fail
with `TOCSS-DART` errors.

## Rules

- Never push to the remote without explicit user approval.
- Posts are Markdown in `content/posts/`; home/about/search pages live directly
  in `content/`.
- The theme is vendored at `themes/cactus/` — edits there are committed like any
  other file.
- The custom palette (used when `colorscheme = "custom"`) lives in
  `themes/cactus/assets/scss/_custom.scss`.
- CI in `.github/workflows/deploy.yml` pins Hugo 0.167.0 (extended) + Sass and
  deploys on push to `main`; keep the local Hugo version in sync when possible.
