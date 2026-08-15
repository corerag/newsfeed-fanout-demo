# Contributing

Thanks for taking a look. This is a small, single-file teaching demo, so the
process is intentionally lightweight.

## Project shape

- `index.html` is the entire app: markup, CSS, and vanilla JS in one file.
  No build step, no dependencies, no framework.
- Keep it that way. If a change needs a bundler, a package.json, or a
  frontend framework, it's probably out of scope for this repo — open an
  issue first to discuss before adding tooling.
- The diagram is hand-drawn inline SVG, positioned via a small `POS` layout
  table in the script. Follow that pattern rather than introducing a
  charting or diagramming library.

## Making a change

1. Fork the repo and create a branch off `master`.
2. Edit `index.html` directly. Open it in a browser to check your change —
   there's no automated test suite, so manual verification in-browser is
   the bar. At minimum, click through the action buttons (post as Alice,
   post as celebrity, traffic burst), exercise the sliders, and confirm
   both light and dark OS themes still render legibly.
3. Keep additions consistent with the existing style: plain functions over
   classes, `var`, no semicolon-optional style, CSS custom properties for
   all colors (no hardcoded hex in component rules), and no build-time
   dependencies.
4. Update `README.md` if you add a new concept, control, or scenario worth
   knowing about.
5. Open a pull request describing what changed and why. Screenshots or a
   short clip are appreciated for anything visual.

## Reporting bugs / suggesting ideas

Open a GitHub issue. For bugs, include the browser/OS and steps to
reproduce. For new scenario ideas (e.g. another system-design concept to
visualize), a short description of the mechanism you want to show is more
useful than a full spec.

## Code of conduct

This project follows the guidelines in [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).
