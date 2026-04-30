# mkitty-site

The marketing and interactive demo site for [mKitty](https://github.com/BellamyDev/mKitty), a cozy MCAT study RPG.

**Live site:** https://BellamyDev.github.io/mkitty-site

## What's here

A single self-contained `index.html` file that includes:

- Animated hero with the mKitty mascot and brand wordmark
- Scroll-driven walkthrough of the gameplay loop (pinned scene that morphs through 5 stages as you scroll)
- Interactive demos of two MCAT-style question types — **Match the Pairs** and **Label the Picture** — playable without install or signup
- Footer with project links

No build step, no dependencies beyond Google Fonts. The whole site is one HTML file.

## Develop locally

```bash
git clone https://github.com/BellamyDev/mkitty-site.git
cd mkitty-site

# Open index.html directly in a browser, OR run a local server:
python3 -m http.server 8000
# then visit http://localhost:8000
```

A local server is recommended for accurate testing — opening the file directly works, but some browsers handle CORS and module loading differently from `file://` URLs.

## Deploy

This site auto-deploys to GitHub Pages on every push to `main` via the workflow in `.github/workflows/deploy-pages.yml`. To enable:

1. Go to **Settings → Pages** in this repo
2. Under **Source**, select **GitHub Actions**
3. Push to `main` — the site goes live at `https://BellamyDev.github.io/mkitty-site/` in ~30 seconds

If you want a custom domain (e.g., `mkitty.io`), add a `CNAME` file at the root with the domain on a single line, then configure DNS at your registrar to point to GitHub Pages' IPs.

## Repository structure

```
mkitty-site/
├── index.html              # the entire site (HTML + CSS + JS in one file)
├── assets/                 # images, future logo files, OG images
├── .github/workflows/      # GitHub Pages deploy
├── README.md
└── LICENSE
```

## Updating the site

Common edits:

| What you want to change | Where to look |
|---|---|
| Hero slogan or copy | Search for `hero-tagline` and `hero-subtitle` in `index.html` |
| Walkthrough captions | Search for `walkthrough-step` |
| Question content (matching pairs, labels) | Search for `matchPairs` and `labels` in the `<script>` section |
| Color palette | The `:root` block at the top of `<style>` defines all design tokens |
| Logo | Search for `id="hero-logo"` for the mascot, `nav-logo-mark` for the nav |

## License

MIT — see [LICENSE](LICENSE).

## Related

- **[mKitty (main repo)](https://github.com/BellamyDev/mKitty)** — the actual game project (Unity)
