# E Ink Studio

Turn text and photos into high-contrast, grayscale wallpapers sized for e-ink devices — Kindle, Kobo, reMarkable, Boox, Supernote, XTEink, and more. Runs entirely in the browser as a single self-contained HTML file. No build step, no dependencies, no data leaves your device.

**Live demo:** https://greatsyxsuke.github.io/E-Ink-Studio/

## Features

- **Text to wallpaper** — type a quote, word, or mantra with an optional attribution line, auto-fit to the screen.
- **Device presets** — XTEink X3 / X4 Pro / X4 Classic, reMarkable 2 & Paper Pro, Kindle Paperwhite / Oasis / Scribe, Kobo Clara 2E / Libra 2, Boox Note Air & Tab, Supernote A5 X, phone lock screen, square, or a custom pixel size. Exports at true device resolution.
- **Typography** — serif, geometric, or monospace type stacks, plus upload your own font (.ttf/.otf/.woff/.woff2). Regular / bold / UPPERCASE and a size control.
- **Layout** — left/center/right alignment, top/middle/bottom placement, adjustable margin.
- **Photos** — drop in an image and convert it to grayscale, sized to the exact preset:
  - Fit: **Cover** or **Contain**
  - Look: **Greyscale**, **16-level**, **4-level**, **Floyd–Steinberg**, **Atkinson**, **Bayer** (ordered), **Two-tone** (1-bit)
  - Brightness, contrast, gamma, and sharpen sliders
  - Fade behind text for legible overlays
- **QR codes** — turn any URL into a scannable code (self-contained generator, no external library), place it in any corner with an optional caption. Always rendered black-on-white so it scans on any theme.
- **Finish** — Paper / Inverted / Slate themes, hairline border, accent rule, dither texture, **auto text color** (samples the photo behind the text and picks black or white for contrast), and a **lock-screen safe-zone guide** (preview-only markers for the iPhone clock, widgets, and home bar).
- **Batch export** — write multiple wallpapers separated by a line of three dashes and generate them all at once.
- **Saved looks** — store your full setup in the browser, and copy a portable settings code to move a look between devices.
- **Export** — download a PNG, open it in a new tab (for iOS "Save to Photos"), or export the whole tool as a single HTML file.

## Usage

### Online
Just open the live demo link above in any modern browser.

### On iPhone / iPad
Open the hosted URL in **Safari** (not the Files app preview, which won't run the tool's JavaScript). To save a wallpaper: tap **Open image in new tab**, then long-press the PNG and choose **Save to Photos**. Optionally use **Share → Add to Home Screen** for an app-like icon.

### Run your own copy
This is a single `index.html` file — host it anywhere static.

**GitHub Pages:**
1. Add `index.html` to a public repo.
2. Settings → Pages → Source: **Deploy from a branch** → `main` / `root` → Save.
3. Open the `https://<username>.github.io/<repo>/` URL.

## Tech notes

- Vanilla HTML/CSS/JavaScript with the Canvas API — no frameworks, no build tooling.
- Dithering, gamma, and sharpening run as pixel passes on the canvas; results are cached so only changed settings trigger a re-process.
- The QR generator is a self-contained implementation (byte mode, error-correction level M, auto version selection up to v10), based on `qrcode-generator` by Kazuhiko Arase (MIT).
- Works fully offline once loaded — every asset is inline.

## License

MIT — do whatever you like; attribution appreciated.
