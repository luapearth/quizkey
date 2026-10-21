# QuizKey website

The landing page and privacy policy for the QuizKey Android app, published with GitHub Pages at
**https://luapearth.com/quizkey/** (same setup as https://luapearth.com/bunnyclock/).

Plain HTML and CSS: no build step, no JavaScript, no external requests (the Fredoka font is bundled).

```
index.html      landing page
privacy.html    privacy policy (the URL to give Google Play)
404.html        "page not found" (uses /quizkey/ paths)
assets/         style.css, fonts, icons, app screens, character art, og-image.jpg
.nojekyll       serve files as-is (no Jekyll processing)
```

## Deploy to GitHub Pages
1. Create a GitHub repository named **`quizkey`** (the name sets the URL path `/quizkey/`).
2. Push this folder to its `main` branch:
   ```bash
   git remote add origin git@github.com:<your-account>/quizkey.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch: `main` / `(root)` → Save.**
4. Because `luapearth.com` is already the custom domain of your GitHub Pages user site, the project site appears at
   **https://luapearth.com/quizkey/** automatically. No `CNAME` file is needed in this repo.
5. After a minute or two, check both pages, then put **https://luapearth.com/quizkey/privacy.html** in
   Play Console → App content → Privacy policy.

## Preview locally
Any static file server works, for example:
```bash
python3 -m http.server 8000
```
Then open http://localhost:8000/. (`404.html` uses `/quizkey/` paths, so it only looks right once deployed.)

## Updating
- **When QuizKey is public on Google Play:** replace the "Coming soon to Google Play" pills (two in `index.html`) with
  links to `https://play.google.com/store/apps/details?id=com.luapearth.quizkey`.
- **After editing `assets/style.css`:** bump `?v=1` in the stylesheet links so visitors get the new version.
- **Privacy policy:** keep `privacy.html` in step with the app (QuizKey repo `docs/compliance/privacy-policy.md`) and
  update the effective date whenever it changes.
- Character art comes from the QuizKey repo: `node resources/marketing/source-art/export-web-art.mjs <this repo>/assets/art`.
