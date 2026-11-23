# ROYAL CHERRY — Installation Guide

## 1. Target repository

Your GitHub username is `MaryamRazzaghNejad`. The profile repository must be public and named exactly `MaryamRazzaghNejad`:

`https://github.com/MaryamRazzaghNejad/MaryamRazzaghNejad`

Upload the **contents** of this project folder into the repository root. Do not upload the enclosing folder as a nested directory.

Expected layout:

```text
README.md
INSTALLATION.md
PAGES-SETUP.md
SECURITY-REVIEW.md
assets/
  royal-header.gif
  royal-header-static.svg
  royal-header-closed.svg
  royal-header-animated.svg
  ornaments/royal-divider.svg
docs/
  index.html
  site.css
  curtains.js
.github/workflows/snake.yml
```

## 2. Replace the profile README

1. Open the profile repository and select `README.md`.
2. Use **Edit** and replace its content with this package's `README.md`.
3. Replace `YOUR_LINKEDIN_URL` and `YOUR_LEETCODE_URL` with your actual public profile URLs, or remove those two badges.
4. Commit the changes.

## 3. Upload local assets

Upload the `assets/` folder, `docs/` folder, and `.github/workflows/snake.yml` while preserving their exact paths. The GIF is referenced as `./assets/royal-header.gif`; do not rename it. The header is a 24-second seamless loop: approximately 10 seconds to open fully, 2 seconds fully open, approximately 10 seconds to close fully, and about 2 seconds fully closed. It is encoded at 800 × 280 pixels; duplicate hold frames are coalesced to keep the file compact. The displayed first and last frames are pixel-identical, and the GIF loop metadata is set to infinite.

## 4. Contribution Snake workflow

The workflow runs daily, manually from **Actions → Generate Royal Cherry contribution snake → Run workflow**, or after changes to `README.md` / the workflow on `main`.

It uses two third-party Actions pinned to full commit SHAs:

- `Platane/snk` v3.5.0
- `peaceiris/actions-gh-pages` v4.1.0

The only write permission is `contents: write`, scoped to the generation job because it publishes the generated SVGs to the `output` branch. It uses the automatically supplied `GITHUB_TOKEN`; do not create or paste a Personal Access Token for this workflow.

If publishing fails with a 403, check whether repository or organization policy permits `GITHUB_TOKEN` to write repository contents. Do not broaden permissions beyond `contents: write`.

The `output` branch is created after the first successful run. Until then, the snake image may not render.

Expected image URLs:

- `https://raw.githubusercontent.com/MaryamRazzaghNejad/MaryamRazzaghNejad/output/github-snake.svg`
- `https://raw.githubusercontent.com/MaryamRazzaghNejad/MaryamRazzaghNejad/output/github-snake-dark.svg`

## 5. Interactive curtain page

See [PAGES-SETUP.md](./PAGES-SETUP.md). The README itself uses a GIF because GitHub does not run arbitrary JavaScript or reliably allow hover interactions inside README content. The interactive hover / keyboard / click experience is hosted separately through GitHub Pages.

## 6. Keep it safe

- Never place passwords, API keys, Personal Access Tokens, SSH private keys, or other secrets in README files, SVGs, HTML, or this repository.
- Do not add a `pull_request_target` trigger to this workflow.
- Review changes to third-party Actions before changing their pinned commit SHAs.
- See [SECURITY-REVIEW.md](./SECURITY-REVIEW.md) for the inspection scope and external-service notes.
