# Store Inventory

**Install the app: https://fourier18.github.io/store-inventory/**

Version: Test 006

A phone app for walking through a store once and building a digital archive of every item: photo, category, condition, location, notes and a printed SKU label. It works offline and keeps all data on the phone. No account needed.

## Install on Android
1. Open **https://fourier18.github.io/store-inventory/** in Chrome.
2. Tap **Install the app**.
3. If there's no button: tap **⋮** (top right) → **Add to home screen** (or **Install app**) → **Install**.
4. Open the green **Inventory** icon on the home screen.

To use it without installing: https://fourier18.github.io/store-inventory/app.html

## Changelog
- **Test 006**: Every typing box is now a plain text area instead of a form field, so Chrome's autofill strip (key, card and pin icons) shouldn't appear above the keyboard. Gboard's own toolbar and mic are unchanged.
- **Test 005**: Words no longer break in the middle (the label box said "m / ake"). The app now picks up a new version the first time you reopen it.
- **Test 004**: The big Save item bar is gone. Saving is a small round **Save** button in the top-right of the header, so the form keeps the space above the keyboard. Text fields ask Chrome not to offer autofill.
- **Test 003**: Starts blank. The three sample items and two sample collections are gone, and phones that ran Test 001 or 002 remove them on first open. Items you made yourself are kept. Category and subcategory presets stay.
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
