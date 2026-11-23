# Publish the Royal Cherry curtain experience

The profile README uses `assets/royal-header.gif` because GitHub README rendering does not run arbitrary JavaScript or provide reliable hover-triggered interaction. The separate page in `docs/` reproduces the slow curtain cycle with CSS and includes a pause/resume control.

1. Open `MaryamRazzaghNejad/MaryamRazzaghNejad`.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, select **Deploy from a branch**.
4. Choose branch `main` and folder `/docs`, then save.
5. After deployment, open:

   `https://maryamrazzaghnejad.github.io/MaryamRazzaghNejad/`

The page repeats a 24-second cycle: about 10 seconds opening, a short fully-open pause, about 10 seconds closing, and a short closed pause. Use **Pause the performance** / **Resume the performance** to stop or resume the loop. The page includes local-only scripts and styles, a restrictive Content Security Policy, keyboard-focus styling, and `prefers-reduced-motion` support.
