# E Ink Studio

A single-file, offline web tool that turns text and photos into high-contrast grayscale wallpapers sized exactly for e-ink devices. Built for the XTEink X3 pocket reader, with presets for most popular e-readers and tablets.

**Live:** https://greatsyxsuke.github.io/E-Ink-Studio/

Everything runs in one `index.html` — no build step, no dependencies, no network. Open it in any browser and it works offline.

## Features

### Device presets
Pick your device and the canvas is sized to its native resolution:

- XTEink X3 (528×792), X4 Pro (480×800), X4 Classic (480×800)
- reMarkable 2 / Paper Pro, Kindle Paperwhite 11th, Oasis, Scribe
- Kobo Clara 2E, Libra 2 — Boox Note Air / Tab — Supernote A5 X
- Phone lock screen (grayscale), Square 1:1, and a Custom size

Toggle **portrait / landscape** on any preset.

### Text wallpapers
- Five layout templates: **Quote**, **Date**, **Agenda**, **Habits**, **Reading**
- Built-in fonts plus **custom font upload** (any `.ttf`/`.otf`/`.woff`)
- Control style, size, alignment, vertical position, and margin
- **Surprise me** button to shuffle a fresh look

#### Template tokens
Resolved live from the device clock when you generate the image:

| Token | Example |
|---|---|
| `{date}` | October 12, 2026 |
| `{shortdate}` | 10/12/2026 |
| `{weekday}` | Monday |
| `{day}` `{month}` `{monthnum}` `{year}` | 12 · October · 10 · 2026 |
| `{time}` `{time24}` | 10:15 PM · 22:15 |
| `{weeknum}` `{dayofyear}` | 42 · 285 |
| `{moonphase}` | Waxing Gibbous |

#### Layout syntax
- **Agenda** — one to-do per line. Start a line with `[x]` to show it checked and struck through; empty slots become ruled lines.
- **Habits** — one habit per line, current week + today highlighted. Add ticks after a `|` — e.g. `Floss | x x . x . . .` (`x` = done).
- **Reading** — line 1 = title, line 2 = author. Add a line like `142/320` (or `44%`) to fill a circular progress ring showing the percentage and page count.

### Finish
- Light or dark theme
- Accent rule and hairline border
- **Extras:** auto text color, lock-screen safe-zone guide, paper grain

### QR codes
Drop in a URL and place a self-contained QR code in any corner. It always sits on a white patch so it scans on either theme.

### Photos
Load a JPG/PNG/WebP and it's converted to grayscale and sized to the preset.

- **Look:** Greyscale, 16-level, Floyd, Atkinson, Bayer, Halftone, Two-tone
- **Fade** to keep overlaid text legible
- **Position & crop:** zoom and pan
- **Adjust tone:** brightness, contrast, sharpen
- **Effects:** threshold, vignette, rounded corners

### E-ink render & preview
Optionally quantize the whole composition to the panel's depth (1-bit Floyd / Atkinson / Bayer, or 16-level grey) so the preview matches the device and the panel won't re-dither it.

Turn on **Compare smooth vs e-ink** to split the preview side by side — the smooth composite next to what the panel will actually show — so you can judge grain before exporting.

### Export
- **PNG** — for sharing or phone lock screens
- **24-bit BMP** — the format the XTEink readers accept for custom wallpapers
- Exports are **rendered at 2× and downscaled** for crisper text and edges, then dithered at true panel resolution (1-bit photo looks render at native size to stay sharp)
- **Copy image to clipboard** for quick pasting, alongside Download and Open-in-new-tab

### Save & reuse
- **Saved looks** persist in your browser, plus a copyable settings code to move a look between devices
- **Save this app** exports a standalone copy of the tool itself
- Add to Home Screen on iOS/Android for an app-like launch

## Using it on the X3

1. Open the live link in **Safari** (not the Files app preview — that won't run the tool).
2. Build your wallpaper and export as **24-bit BMP**.
3. On the X3, set it as your custom sleep/wallpaper image.

> If a photo looks grainy on-device, start from a higher-resolution source and try the **16-level** look or turn on **E-ink render**. Use **Compare smooth vs e-ink** to preview the result first.

> Tokens like `{moonphase}` and `{weeknum}` are a snapshot of the moment you generate the image — regenerate to refresh them.

## Repo files

- `index.html` — the entire app
- `README.md` — this file
- `LICENSE` — MIT
- `og-image.png` — social-share preview image (1200×630). Generate it from the **"share image"** link in the app footer and drop it in the repo root; the page's Open Graph tags point here.

## License

MIT © 2026 greatsyxsuke
