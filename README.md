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
| **Agenda** | A weekday + date header, then a checklist. | One to-do per line (see syntax below); leftover rows are blank ruled lines. |
| **Habits** | A month header and the current week's dates with **today highlighted**, then a tick grid. | One habit per line with optional per-day ticks (see syntax below). |

The Date, Agenda, and Habit templates read the current date automatically. "Today" is baked in at export, so generate on the day you want shown.

### Agenda syntax
One task per line. Prefix a line with `[x]` to show it done (checkmark in the box and a line through the text); `[ ]` or no prefix leaves it open. Blank slots become ruled lines.

```
[x] Reply to the void
[x] Alphabetize the spice rack (again)
[ ] Finally learn to whistle
Water the imaginary plant
```

### Habit syntax
One habit per line. After a `|`, mark which days of the week are ticked (Sun→Sat) using `x` for done and `.` or a space for empty. Compact (`xxx....`) and spaced (`x x x . . . .`) both work; `x`, `1`, `o`, and `✓` all count as ticked. No `|` means an empty row.

```
Touch grass | x . x . x . .
Doomscroll less | x x x x x x x
Hydrate (allegedly) | . . x . . . x
Blink manually | xxxxx
