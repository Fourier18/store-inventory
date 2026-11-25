# Store Inventory

**Install the app: https://fourier18.github.io/store-inventory/**

Version: Test 016

A phone app for walking through a store once and building a digital archive of every item: photo, category, condition, location, notes and a printed SKU label. It works offline and keeps all data on the phone. No account needed.

## Install on Android
1. Open **https://fourier18.github.io/store-inventory/** in Chrome.
2. Tap **Install the app**.
3. If there's no button: tap **⋮** (top right) → **Add to home screen** (or **Install app**) → **Install**.
4. Open the green **Inventory** icon on the home screen.

## Install on iPhone or iPad
1. Open **https://fourier18.github.io/store-inventory/** in **Safari**.
2. Tap **⋯** next to the web address, then **Share**. (Older iPhones: tap the Share button at the bottom.)
3. Scroll down and tap **Add to Home Screen**.
4. Leave **Open as Web App** on and tap **Add**.
5. Always open the green **Inventory** icon. Items saved in a Safari tab can be erased by iOS after 7 days without use and don't move into the home screen app.

To use it without installing: https://fourier18.github.io/store-inventory/app.html

Plans for future builds are in the [dev log](DEVLOG.md).

## Changelog
- **Test 016**: In Settings, the theme button that said "Store green (follows the phone)" now says **Store green**, with "(follows the phone's light/dark mode)" in smaller print under it, and it's last in the theme list. It's still the theme a new install starts with.
- **Test 015**: New **Save or send as PDF** button, both on the Send today's work screen and on the report page. It opens the phone's print screen with a clean printable copy: each item with up to 4 smaller photos, its label, and all its details, with no search bar or buttons. Pick **Save as PDF** there, then share the saved file from the phone's Files app, Drive or email. On the report page the PDF holds the items showing at that moment, so a search or filter narrows it. The report page itself is unchanged and still carries the full data for the master inventory. Printing tags works as before.
- **Test 014**: New **Report a problem or idea** button at the top of Settings (the gear). Pick "Something is wrong" or "An idea or request", type or talk the message, and tap Send. It goes straight to Joshua's email through Web3Forms, with no email account needed on the phone. The app version, phone type and screen size go with it. Without internet the report waits on the phone and sends by itself once it's back online.
- **Test 013**: Works on iPhone and iPad. The install page shows iPhone steps (Safari: ⋯, Share, Add to Home Screen, Add) and tells people in other iPhone browsers to open it in Safari, with a Copy the address button. In a Safari tab on iPhone, the app shows a banner asking to put it on the home screen first, because iOS can erase a Safari tab's saved items after 7 days without use. Talking on iPhone restarts by itself when Safari stops after a pause, removes repeated words, and shows plain iPhone messages when it can't work (Siri off, microphone not allowed, or not working in the home screen app); if talking ever closes the app, it switches itself off on that phone and Type stays ready. The Google Lens button on iPhone says to pick Google from the share menu. Android is unchanged.
- **Test 012**: The "Look it up" buttons (eBay sold, eBay for sale, Reverb, Discogs, AbeBooks, Vinted, Google Lens) now show on every item card from the start. Until then they appeared only after a name was typed. Google Lens works from the photo; the name buttons ask for a name if there isn't one yet.
- **Test 011**: New gear button beside the name button opens Settings: add, rename and remove custom categories, subcategories, statuses and collections, pick the label size, change who is using the phone, and pick a theme (Store green, plus the seven themes from tu-torus: Light, Dark, Forest Green, Azure Night, Desert Sunset, Arctic Dawn, Plum Midnight). Custom statuses can also be added right on the item card. "Where it's kept" is now "Building" and the separate "You're working in" box is gone: the building picked when an item is first saved sets the label's building code, and moving it later changes only the Building field, not its label. Removed the helper lines that said the obvious.
- **Test 010**: The price box is now labeled just "Price".
- **Test 009**: New **Price** field on every item, included in the spreadsheet, the daily report and the item list. The printed tag now shows the price large beside the QR code, with the label (SKU) a little smaller. The big "Tap to talk / Type instead" bar is now a small two-button pill (Talk | Type) at the right edge above the keyboard. Tap Talk to open the talking panel; tap Type, or just start typing, and the pill steps aside for that box and doesn't come back on re-taps.
- **Test 008**: "Print tag" button on the Saved screen and on every saved item. The tag has a QR code of the item's permanent ID, the label (SKU) and the title. Prints through the phone's print screen to any printer, or saves/shares the tag as a picture. Label sizes: 2 × 1 in, 50 × 30 mm, 2¼ × 1¼ in, and a 2 × 3½ in hang tag with room for a string hole. The QR code is made on the phone, no internet needed.
- **Test 007**: "Send today's work" now makes one report page (inventory-D-2026-11-20.html) with every item, its photos (tap to enlarge), search and filters, plus Download spreadsheet and Download photos buttons. The page also carries the full data for the future master inventory. The separate JSON file is gone; the spreadsheet is still there.
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
