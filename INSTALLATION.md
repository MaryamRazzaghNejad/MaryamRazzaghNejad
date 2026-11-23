# Royal Cherry Profile — installation

The profile repository name must be exactly `MaryamRazzaghNejad`, matching the GitHub username.

Upload the **contents** of this project folder into the root of that repository (do not nest this folder one level deeper). Keep this structure:

```text
README.md
assets/royal-header.gif
assets/royal-header-static.svg
assets/royal-header-animated.svg
assets/ornaments/royal-divider.svg
.github/workflows/snake.yml
docs/index.html
```

## Contribution Snake

The workflow runs daily, on pushes affecting the README/workflow, or manually via **Actions → Generate Royal Cherry contribution snake → Run workflow**. `Platane/snk@v3` generates two SVGs with custom `color_snake` and five `color_dots` values, then `peaceiris/actions-gh-pages@v4` publishes them to the `output` branch. Action documentation: https://github.com/Platane/snk

Required permission: **Settings → Actions → General → Workflow permissions → Read and write permissions**. The workflow declares `permissions: contents: write`. The `output` branch is created only after the first successful run, so snake images may be blank until then.

Expected image URLs after the run:

- `https://raw.githubusercontent.com/MaryamRazzaghNejad/MaryamRazzaghNejad/output/github-snake.svg`
- `https://raw.githubusercontent.com/MaryamRazzaghNejad/MaryamRazzaghNejad/output/github-snake-dark.svg`

## GitHub Pages

See [PAGES-SETUP.md](./PAGES-SETUP.md) to publish the hover/click curtain reveal from the `/docs` folder.

## Personal details

Replace `YOUR_LINKEDIN_URL` and `YOUR_LEETCODE_URL` in README.md with your actual URLs before publishing.

## Accuracy

HTML and CSS are described as current strengths based on your stated web-template experience. JavaScript is marked in progress. Dart and Python are previous study/practice, not professional mastery. Frameworks, databases, and AI are planned or long-term.
