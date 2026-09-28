# strunden.com — static clone (GitHub Pages)

Free static mirror of the Adobe Portfolio site at https://strunden.com, for hosting **without Creative Cloud / Adobe Portfolio payment**.

This folder is the GitHub Pages site root for repo **`Strunden/strunden.com`**.

## Local preview

```bash
cd /path/to/strunden-pages   # this folder
python3 -m http.server 8000
# open http://127.0.0.1:8000/  or  /profile.html  /work.html
```

Do not open `index.html` via `file://` — absolute `/dist/...` and `/cdn/...` paths need an HTTP server.

## Deploy to GitHub Pages (Financy / Fabian)

1. Create empty public repo **`strunden.com`** under **`@Strunden`** (do not push from this agent).
2. Push this folder to `main` (site root = repository root):
   ```bash
   git init
   git add .
   git commit -m "Static Portfolio clone for GitHub Pages"
   git branch -M main
   git remote add origin git@github.com:Strunden/strunden.com.git
   git push -u origin main
   ```
3. GitHub → **Settings → Pages**:
   - Source: **Deploy from a branch**
   - Branch: `main` / `/ (root)`
4. Leave the custom domain unset. `CNAME` is not in this tree, so Pages keeps serving the `github.io` preview and does not attach `strunden.com`.
5. Do not change external DNS yet. Remap `strunden.com` only after the `github.io` preview is accepted.

Preview: https://strunden.github.io/strunden.com/

## What was changed vs live Portfolio

- Assets inlined under `/cdn/...`, `/dist/...` (no Adobe CDN required at runtime).
- Typekit → self-hosted Inter as `vcsm` (approximate).
- Google Analytics tracking code cleared from page config.
- Internal links keep `*.html` pages and also publish extensionless folder routes (`work/index.html`, `profile/index.html`, and each project directory).
- `og:image` URLs are absolute. `robots.txt` and `sitemap.xml` are at the site root.

## Login

No Adobe login is required to view or host this clone.
