# ROYAL CHERRY — Security Review Notes

Review date: 2026-11-23  
Repository target: `MaryamRazzaghNejad/MaryamRazzaghNejad`

## Scope

This is a static-content and configuration review of the files in this package. It is not a formal penetration test, a full audit of upstream dependencies, or a guarantee of absolute security.

## Checks performed on the package

- ZIP integrity test passed; no corrupt archive member was detected.
- Archive paths were checked for absolute paths and `..` traversal components; none were found.
- Text files were scanned for obvious hard-coded GitHub tokens, private-key headers, `javascript:` URLs, inline HTML event-handler attributes, `eval()`, cookie access, and local-storage access; none were found.
- SVG assets contain vector artwork and a small SMIL opacity animation. No SVG `<script>` or `<foreignObject>` element was found.
- The animated GIF is an image asset (800 × 280 pixels, 24-second cycle, infinite-loop metadata). It is generated from 240 source frames at 100 ms each; GIF optimization merges identical hold frames into 195 encoded frames. The displayed first and last frames are pixel-identical. It is not an executable program.
- The interactive GitHub Pages page uses a small local JavaScript file that only toggles the curtain's CSS class and updates the button label/ARIA state. It does not fetch data, evaluate strings, access cookies, use local storage, or load third-party JavaScript.
- The Pages page uses a Content Security Policy with `default-src 'self'`, local-only scripts and styles, and blocks objects and base-URL changes.
- GitHub Actions references are pinned to full commit SHAs rather than mutable version tags.

## GitHub Actions permissions and behavior

The snake workflow has no repository permissions by default and grants only `contents: write` to the single job that publishes generated SVGs to the `output` branch. It does not run on `pull_request` or `pull_request_target`, does not check out or execute repository-controlled project code, and uses the automatically generated `GITHUB_TOKEN` rather than a user-created Personal Access Token.

Pinned upstream references:

- `Platane/snk` v3.5.0 — `d8f6715049803e982ee5ff501b6b9b7d5deeb09b`
- `peaceiris/actions-gh-pages` v4.1.0 — `84c30a85c19949d7eee79c4ff27748b70285e453`

Pinning reduces the risk of a tag being moved to different code, but it does not prove upstream code is vulnerability-free. Review upstream changes before updating either SHA.

## External services used by README images

The README requests images from these providers:

- `skillicons.dev`
- `img.shields.io`
- `github-readme-stats.vercel.app`
- `github-readme-activity-graph.vercel.app`
- `komarev.com`
- GitHub raw content for the generated snake image

These providers receive ordinary image requests when a visitor opens the README. Depending on each provider's logging and privacy practices, the request can expose visitor network metadata (such as IP address) and the requested URL. The public GitHub username is included in some image URLs. These are not credentials, but they do create third-party network dependencies and can affect availability or visitor privacy. Remove the corresponding image tags if you prefer a more private, self-contained profile.

## Limits and user responsibilities

- No security scan can establish "complete security" or rule out all vulnerabilities.
- GitHub Pages is public when enabled for a public repository; do not publish private information there.
- Do not commit passwords, access tokens, private keys, session cookies, or other secrets.
- If a service or Action changes ownership, release, permissions, or behavior, reassess it before updating the project.
- Keep GitHub account two-factor authentication enabled and review connected apps / authorized OAuth applications periodically.

## Recommended repository settings

- Keep the profile repository public (required for a public profile README).
- Keep the default branch protected from unreviewed changes where practical.
- Allow GitHub Actions to use `GITHUB_TOKEN` with the narrow `contents: write` permission declared in the workflow; do not add a PAT secret.
- Review the Actions run logs after the first manual execution.
