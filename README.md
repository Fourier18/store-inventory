# Store Inventory

A phone app for walking through a store once and building a raw digital archive of every item: photo, category, condition, location, notes and a printed SKU label. It installs from the browser (a Progressive Web App), works offline, and keeps all data on the phone.

**Install:** open the GitHub Pages link for this repo in Chrome on Android and tap **Install the app** (or ⋮ → Add to home screen).

## Files
- `index.html` — install page with a big Install button and large-print fallback steps
- `app.html` — the app itself
- `manifest.webmanifest`, `icons/` — what makes it installable
- `sw.js` — service worker that keeps the app's files on the phone for offline use

## Data
Items are stored in the phone's IndexedDB (one record per item, photos compressed to about 1280 px JPEG). Nothing is sent anywhere unless you use **Send today's work**, which shares a CSV through the share sheet or saves a JSON file with photos to Downloads.

Each item has a hidden permanent ID (ULID, which encodes the creation time) and a regenerable SKU label: `CATEGORY-SUBCATEGORY-ORIGIN-WORKER-NUMBER`, e.g. `MED-REC-BB-D-0001`.
