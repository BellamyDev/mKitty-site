# Push This Site to GitHub

Quick guide. Delete this file once the site is live.

## With GitHub CLI (~60 seconds)

```bash
# Install gh once: brew install gh && gh auth login

git init
git add .
git commit -m "chore: initial site scaffold"
gh repo create mkitty-site --public --source=. --remote=origin --push
```

## Without GitHub CLI

1. Create an empty public repo at https://github.com/new (name it `mkitty-site`, do NOT initialize with README/LICENSE/.gitignore)
2. Copy the repo URL
3. Then:

```bash
git init
git add .
git commit -m "chore: initial site scaffold"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/mkitty-site.git
git push -u origin main
```

## Enable GitHub Pages

1. Go to **Settings → Pages** in the repo
2. Under **Source**, select **GitHub Actions**
3. The deploy workflow runs automatically; site goes live at:
   `https://YOUR_USERNAME.github.io/mkitty-site/`

First deploy takes ~1-2 minutes. After that, every push to `main` redeploys in ~30 seconds.

## Update placeholder URLs

The README and `index.html` reference `YOUR_USERNAME` in a few spots. Quick find-and-replace:

```bash
# macOS sed
find . -type f \( -name "*.md" -o -name "*.html" \) -exec sed -i '' 's/YOUR_USERNAME/your-actual-handle/g' {} +

git add . && git commit -m "docs: update placeholder URLs" && git push
```

## After it's live

- Update the main `mKitty` repo's README to link to the live site
- Add an OpenGraph image (`assets/og-image.png`, 1200×630) so the site renders nicely when shared on Slack/Twitter/etc.
- Consider a custom domain if you want — add a `CNAME` file at the repo root with one line: `mkitty.io` (or whatever)

## Delete this file

```bash
rm PUSH_TO_GITHUB.md
git add . && git commit -m "chore: remove push instructions" && git push
```
