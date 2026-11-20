# Store Inventory

**Install the app: https://fourier18.github.io/store-inventory/**

Version: Test 002

A phone app for walking through a store once and building a digital archive of every item: photo, category, condition, location, notes and a printed SKU label. It works offline and keeps all data on the phone. No account needed.

## Install on Android
1. Open **https://fourier18.github.io/store-inventory/** in Chrome.
2. Tap **Install the app**.
3. If there's no button: tap **⋮** (top right) → **Add to home screen** (or **Install app**) → **Install**.
4. Open the green **Inventory** icon on the home screen.

To use it without installing: https://fourier18.github.io/store-inventory/app.html

## Changelog
- **Test 002**: The talk panel no longer covers the field you're typing in. Tapping a field shows a slim "Tap to talk" bar above the keyboard, and the field scrolls into view above it. Added a big **Type instead** button that closes the panel and puts the cursor in the field.
- **Test 001**: First standalone build. Install page, offline support, items saved on the phone.

## Files
- `index.html`: install page with a big Install button and large-print fallback steps
- `app.html`: the app itself
- `manifest.webmanifest`, `icons/`: what makes it installable
- `sw.js`: service worker that keeps the app's files on the phone for offline use

## Data
Items are stored in the phone's IndexedDB (one record per item, photos compressed to about 1280 px JPEG). Nothing leaves the phone unless you use **Send today's work**, which shares a CSV through the share sheet or saves a JSON file with photos to Downloads.

Each item has a hidden permanent ID (ULID, which encodes the creation time) and a regenerable SKU label: `CATEGORY-SUBCATEGORY-ORIGIN-WORKER-NUMBER`, e.g. `MED-REC-BB-D-0001`.
