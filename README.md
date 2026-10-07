# Sebastian Hamza — personal blog

Hugo site using a vendored copy of the
[Cactus theme](https://github.com/iahsanujunda/hugo-theme-cactus), deployed to
GitHub Pages via GitHub Actions.

- **Live site:** https://sebastianhamza.github.io/
- **Content:** `content/` (posts live in `content/posts/`)
- **Config:** `hugo.toml`
- **Theme:** `themes/cactus/` (vendored — edit it freely)

## Quickest way to publish a post (browser only)

1. Open https://github.com/sebastianhamza/sebastianhamza.github.io
2. Go to `content/posts/` → **Add file** → **Create new file**
3. Name it `my-post-title.md` and paste:

   ```yaml
   ---
   title: "My post title"
   date: 2026-10-07
   draft: false
   tags: []
   categories: []
   ---
   ```

4. Write the post, scroll down, click **Commit changes**
5. GitHub Actions rebuilds and publishes in ~1 minute

Works from a phone too. Need a preview first? Use the local workflow below.

## Local workflow (recommended for writing)

One-time setup (already done on this machine):

```powershell
winget install Hugo.Hugo.Extended   # Hugo extended >= 0.158

# Dart Sass: use the standalone build from https://github.com/sass/dart-sass/releases
# (zip contains sass.bat + src\dart.exe — add the folder to PATH).
# Already installed here at: %LOCALAPPDATA%\Programs\dart-sass
# Do NOT use `npm install -g sass`: that package doesn't support the embedded
# protocol Hugo needs, and builds fail with TOCSS-DART errors.
```

Then:

```powershell
hugo server -D                       # live preview at http://localhost:1313
hugo new content posts/my-post.md    # create a post (draft by default)
```

`draft: true` posts are visible only in local preview with `-D`. To publish:
set `draft: false`, then

```powershell
git add -A
git commit -m "Add my post"
git push
```

Actions does the rest. Check the deploy at
https://github.com/sebastianhamza/sebastianhamza.github.io/actions

## Customizing

- **Name, bio, colors, menu, social links:** `hugo.toml` (`[params]` section).
  `colorscheme` accepts `dark`, `light`, `classic`, `white`, `custom` — the
  custom palette is defined in `themes/cactus/assets/scss/_custom.scss`.
- **Logo / favicons:** replace the files in `static/images/` (create the folder;
  it overrides the theme's defaults).
- **Projects on the home page:** `data/projects.yml`.
- **Theme templates & styles:** `themes/cactus/layouts/` and
  `themes/cactus/assets/scss/`.
- **Comments / analytics:** `[params.utterances]`, `[params.disqus]`,
  `[params.googleAnalytics]`, etc. in `hugo.toml`.

## Deployment

`.github/workflows/deploy.yml` builds with Hugo extended 0.167.0 + Dart Sass and
publishes `public/` to GitHub Pages. Any push to `main` triggers it.

One-time repo setting (already done): **Settings → Pages → Build and
deployment → Source = "GitHub Actions"**.
