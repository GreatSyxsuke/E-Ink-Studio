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
- Four layout templates: **Quote**, **Date**, **Agenda**, **Habits**
- **Template tokens** resolved live: `{date}`, `{weekday}`, `{day}`, `{month}`, `{year}`, `{time}`, `{shortdate}`
- **Agenda** — mark items done by starting a line with `[x]` (renders a strikethrough)
- **Habits** — tick a row with `Label | x x . x . . .` (filled vs. empty cells)
- Built-in fonts plus **custom font upload** (any `.ttf`/`.otf`/`.woff`)
- Control style, size, alignment, vertical position, and margin

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

### E-ink render
Optionally quantize the whole composition to the panel's depth (1-bit Floyd / Atkinson / Bayer, or 16-level grey) so the preview matches the device and the panel won't re-dither it.

### Export
- **PNG** — for sharing or phone lock screens
- **24-bit BMP** — the format the XTEink readers accept for custom wallpapers

### Save & reuse
- **Saved looks** persist in your browser, plus a copyable settings code to move a look between devices
- **Save this app** exports a standalone copy of the tool itself
- Add to Home Screen on iOS/Android for an app-like launch

## Using it on the X3

1. Open the live link in **Safari** (not the Files app preview — that won't run the tool).
2. Build your wallpaper and export as **24-bit BMP**.
3. On the X3, set it as your custom sleep/wallpaper image.

> If a photo looks grainy on-device, start from a higher-resolution source and try the **16-level** look or turn on **E-ink render**.

## License

MIT © 2026 greatsyxsuke
