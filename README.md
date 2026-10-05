# Djum HTML Editor

A self-contained, single-file live canvas HTML editor. Open `index.html` in any modern browser — no build step, no server, no dependencies.

## What it does

Upload an HTML file (or paste markup) and edit it visually in the browser:

- **Click text to edit** — every text element becomes contenteditable on load
- **Click images to replace** — opens a file picker; supports png, jpg, gif, svg, webp, avif, heic, heif, tif, bmp, ico
- **Drag containers to reposition** — drag handles appear on top-level containers
- **Slideshow preview** — click the play button to preview animations, or use prev/next arrow keys
- **LocalStorage auto-save** — your edits persist across reloads
- **Whole-document save/export** — Save As downloads a clean copy of the file with all editor overlays stripped (v6.6 fix: hidden scenes restored on export)

## Scene detection

Top-level elements matching `.scene`, `.slide`, `.step`, `.panel`, or `[data-slide]` / `[data-scene]` / `[data-step]` are detected as scenes. The editor navigates between them with the bottom nav bar.

Sub-scenes inside a parent scene are detected when they have CSS animations AND visible content. Each gets its own prev/next controls.

## Logo detection

Elements matching `[class*="logo"]`, `[class*="brand"]`, `[role="img"][aria-label]`, or single-image anchors without text are detected as logos. These are visually outlined but NOT made editable, so the brand stays intact while you work on the surrounding content.

## v6.6 changes (latest)

- **Whole-document save fix** — `cleanForExport` now strips the inline `display:none!important` on hidden scenes/sub-scenes, so saved/exported files contain all scenes (not just the one the user was viewing). Tagged via `data-bm-scene-hidden` / `data-bm-subscene-hidden` for tracking.
- **Pointer-events fix on drag handles** — handles no longer block clicks on the underlying contenteditable text.
- **Iframe load fallback** — if the iframe `load` event doesn't fire (rare browser behavior), 1s timeout manually triggers setup.

## Usage

1. Clone or download `index.html`
2. Open it in a browser
3. Click "Choose HTML File" or "Paste HTML"
4. Edit text by clicking on it
5. Click Save to persist (or Save As to download a clean copy)
6. Click the play button to preview animations

## License

MIT
