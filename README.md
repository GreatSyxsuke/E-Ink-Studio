# E Ink Studio

Turn text and photos into high-contrast, grayscale wallpapers sized for e-ink devices — Kindle, Kobo, reMarkable, Boox, Supernote, XTEink, and more. Runs entirely in the browser as a single self-contained HTML file. No build step, no dependencies, no data leaves your device.

**Live demo:** https://greatsyxsuke.github.io/E-Ink-Studio/

## Features

- **Templates** — build a **Quote**, a **Date** card, an **Agenda**, or a **Habit** tracker (see below). The date-driven templates fill in automatically from the current date.
- **Text to wallpaper** — type a quote, word, or mantra with an optional attribution line, auto-fit to the screen. Supports **template tokens** (see below) for dates and times.
- **Device presets** — XTEink X3 / X4 Pro / X4 Classic, reMarkable 2 & Paper Pro, Kindle Paperwhite / Oasis / Scribe, Kobo Clara 2E / Libra 2, Boox Note Air & Tab, Supernote A5 X, phone lock screen, square, or a custom pixel size — each with a **portrait / landscape** toggle. Exports at true device resolution.
- **Typography** — serif, geometric, or monospace type stacks, plus upload your own font (.ttf/.otf/.woff/.woff2). Regular / bold / UPPERCASE and a size control.
- **Layout** — left/center/right alignment, top/middle/bottom placement, adjustable margin (applies to the Quote template).
- **Photos** — drop in an image and convert it to grayscale, sized to the exact preset:
  - Fit: **Cover** or **Contain**, with **zoom** and **horizontal/vertical pan** to reposition and crop
  - Look: **Greyscale**, **16-level**, **4-level**, **Floyd–Steinberg**, **Atkinson**, **Bayer** (ordered), **Halftone** (dot grid), **Two-tone** (1-bit)
  - Tone: brightness, contrast, gamma, sharpen, **black-point / white-point levels**, and an **adjustable 1-bit threshold** (also biases the dithered modes)
  - Effects: **vignette** and **rounded corners**
  - Fade behind text for legible overlays
- **QR codes** — turn any URL into a scannable code (self-contained generator, no external library), place it in any corner with an optional caption. Always rendered black-on-white so it scans on any theme.
- **Finish** — Paper / Inverted / Slate themes, hairline border, accent rule, dither texture, **paper-grain texture**, **auto text color** (samples the photo behind the text and picks black or white for contrast), and a **lock-screen safe-zone guide** (preview-only markers for the iPhone clock, widgets, and home bar).
- **E-ink render** — optionally dither the whole finished wallpaper to the panel's real depth (**1-bit** via Floyd / Atkinson / Bayer, or **16-level** grey). The preview then matches what the device shows, and the device displays it verbatim instead of adding its own grain.
- **Batch export** — write multiple wallpapers separated by a line of three dashes and generate them all at once.
- **Saved looks** — store your full setup in the browser, and copy a portable settings code to move a look between devices.
- **Export formats** — download as **PNG**, **24-bit BMP**, or **8-bit greyscale BMP**. Many e-ink devices (XTEink among them) will *display* a PNG but only accept a **24-bit BMP** as an actual wallpaper — pick that format for those. Also: open the image in a new tab (for iOS "Save to Photos"), or export the whole tool as a single HTML file.

## Templates

| Template | What it draws | How the main text is used |
| --- | --- | --- |
| **Quote** | A single centered quote with optional attribution. | The quote; attribution is the footer. |
| **Date** | A large day number with the weekday above and month/year below. | A subtitle line under the date; attribution is the footer. |
| **Agenda** | A weekday + date header, then a checklist. | Each line becomes a to-do item; leftover rows are blank ruled lines to write on. |
| **Habits** | A month header and a 7-column week grid (S–S). | Each line becomes a habit row with a week of empty boxes to tick. |

The Date, Agenda, and Habit templates read the current date automatically, so they always open current.

## Template tokens

Type any of these into the main text, attribution, or QR caption and they're filled in when you generate:

| Token | Example |
| --- | --- |
| `{date}` | October 7, 2026 |
| `{shortdate}` | 10/7/2026 |
| `{weekday}` | Wednesday |
| `{day}` | 7 |
| `{month}` | October |
| `{year}` | 2026 |
| `{time}` | 7:50 PM |

Tokens are resolved at the moment you export, producing a static image (great for a dated "daily" wallpaper you regenerate — not a self-updating clock).

## Usage

### Online
Just open the live demo link above in any modern browser.

### On iPhone / iPad
Open the hosted URL in **Safari** (not the Files app preview, which won't run the tool's JavaScript). To save a wallpaper: tap **Open image in new tab**, then long-press the PNG and choose **Save to Photos**. Optionally use **Share → Add to Home Screen** for an app-like icon.

### On an e-ink reader (e.g. XTEink)
1. Choose your device's preset and orientation.
2. Set **E-ink render** to match the panel — try **16-level grey** first; if the screen still speckles, use **1-bit · Atkinson** or **1-bit · Bayer**. This does the dithering in the tool so the panel won't add its own grain, and the preview shows exactly what you'll get.
3. Set the format to **24-bit BMP**, download, transfer it to the device, and set it as your wallpaper. If the wallpaper picker rejects the 24-bit BMP, try the **8-bit greyscale BMP** instead.

### Run your own copy
This is a single `index.html` file — host it anywhere static.

**GitHub Pages:**
1. Add `index.html` to a public repo.
2. Settings → Pages → Source: **Deploy from a branch** → `main` / `root` → Save.
3. Open the `https://<username>.github.io/<repo>/` URL.

## Tech notes

- Vanilla HTML/CSS/JavaScript with the Canvas API — no frameworks, no build tooling.
- Grayscale conversion, levels, gamma, sharpening, vignette, dithering (Floyd–Steinberg, Atkinson, Bayer, halftone), and quantization run as pixel passes on the canvas; results are cached so only changed settings trigger a re-process. The optional **E-ink render** applies a final whole-image dither/quantize so preview and device agree.
- PNG export uses the canvas encoder; BMP export is a self-contained encoder that writes uncompressed 24-bit or 8-bit (palettized greyscale) Windows BMP files directly from the pixel data, since browsers can't emit BMP natively.
- The QR generator is a self-contained implementation (byte mode, error-correction level M, auto version selection up to v10), based on `qrcode-generator` by Kazuhiko Arase (MIT).
- Works fully offline once loaded — every asset is inline.

## License

MIT — do whatever you like; attribution appreciated.
