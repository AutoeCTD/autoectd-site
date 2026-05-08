# AutoeCTD Marketing Website

Static three-page site for AutoeCTD Inc. (Canadian pharma SaaS).
Hosted on **GitHub Pages**. Custom domain: **autoectd.com**

## Files

- `index.html` — main marketing page
- `privacy.html` — Privacy Policy
- `terms.html` — Terms of Use
- `CNAME` — custom domain for GitHub Pages
- `.nojekyll` — disables Jekyll processing (so files starting with `_` are served as-is)

## Design system (don't change without asking)

- Colors: navy `#1B3A6B`, cream `#F2EEE5`
- Brand "e" colors: CTD `#93C5FD`, XML `#06B6D4`, DEF `#10B981`
- Fonts: Fraunces (display), DM Sans (body), JetBrains Mono (labels)
- All three pages share the same nav and footer — keep them in sync

## Local preview

No build step. Open `index.html` directly, or serve the folder:

```
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploying to GitHub Pages

First-time setup:

1. Create an empty repo on GitHub (e.g. `autoectd/autoectd-site`).
2. Push this folder:

   ```
   git remote add origin git@github.com:<owner>/<repo>.git
   git push -u origin main
   ```

3. In the repo on GitHub: **Settings → Pages**.
4. Under **Source**, choose **Deploy from a branch**, select `main` and `/ (root)`. Save.
5. Under **Custom domain**, enter `autoectd.com` and save (the `CNAME` file in this repo will be picked up automatically).
6. Check **Enforce HTTPS** once the cert provisions (a few minutes).

DNS at your registrar — point `autoectd.com` at GitHub Pages:

- `A` records for the apex `@`:
  - `185.199.108.153`
  - `185.199.109.153`
  - `185.199.110.153`
  - `185.199.111.153`
- `CNAME` for `www` → `<owner>.github.io`

After this, every push to `main` auto-deploys (typically within ~30 seconds).

## Updating the site

```
# edit a file
git add index.html
git commit -m "Update hero copy"
git push
```

That's it. No CI workflow, no build step.
