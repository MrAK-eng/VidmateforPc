# Video Downloader Website (static HTML/CSS/JS)

## Run locally
Open `index.html`, or run `python -m http.server 8000` in this folder and visit http://localhost:8000.

## Customize (start here)
1. **`js/config.js`** – app name, tagline, version, download URL, file size, date, checksum, email. Every page reads from it.
   The current download is `Vidmate.exe` in the site folder; keep it beside `index.html` when deploying so the download buttons can find it.
2. **Find & replace** `[YOUR-DOMAIN]` in the HTML files (titles, meta tags, canonical, sitemap, robots).
3. **Screenshots** – the home page gallery uses three `assets/copilot-image-*.png` screenshots. Update the image paths and alt text in `index.html` when refreshing the gallery.
4. **Features** – edit `index.html` and `features.html`. Keep only features your app really has.
5. **Legal** – fill `privacy.html` / `terms.html` placeholders; get them reviewed.

## Release a new version (GitHub Releases)
1. Build your installer; compute its hash: `Get-FileHash .\Setup.exe -Algorithm SHA256`.
2. GitHub repo → Releases → Draft new release → tag `v1.2.0` → upload `YourApp-Setup.exe` → Publish.
3. Copy the asset link (https://github.com/USER/REPO/releases/download/v1.2.0/YourApp-Setup.exe) into `downloadUrl` in `js/config.js`; update version, size, date, checksum and "What's new" in `download.html`.
4. Commit and push.

## Deploy
Use any static host (GitHub Pages, Netlify, Cloudflare Pages). Custom domain: add it in the host's settings, then create the DNS records it shows (CNAME for www, A/ALIAS for apex). Enable HTTPS.

## Later: version API / auto-update
Swap the static `APP_CONFIG` for a fetch to `GET /latest-version` returning `{version, download, size, releaseDate}`. For app updates: app checks latest version, compares with its own, prompts if newer. Nothing in the site claims this exists yet.

## Security
All frontend code is public. Never put API keys, passwords or tokens in it; use a backend for secrets.

## Not included in this first cut
`changelog.html`, `about.html`, `contact.html`, `js/download.js|faq.js|version.js` (merged into `main.js`/`config.js`; FAQ uses native `<details>`), separate `responsive.css`/`animations.css` (merged into `style.css`), Open Graph tags on every page already set but `hero-preview.webp` must be added. No analytics are installed.

## Features, steps and copy
Edit `js/features.js`. Home cards, the Features explorer and the "How it works" walkthrough are all generated from it. Keep only what Vidmate really does.

## Visual design and effects
`css/style.css` contains the shared responsive design system used by every page. `css/animations.css` and `js/effects.js` add a brief first-visit loader, subtle lighting, staggered hero and scroll reveals, screenshot presentation, card hover lighting, restrained magnetic buttons and page transitions. Pointer effects only run on mouse-capable devices; visitors who prefer reduced motion do not receive the motion layer. To remove the effects, delete those two files and their stylesheet/script tags from the HTML pages.
