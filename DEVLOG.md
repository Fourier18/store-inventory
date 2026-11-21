# Dev log

Plans and decisions for the store inventory app. Finished builds are listed in the changelog in the [README](README.md).

## Planned

### 1. In-app QR scanner (workers only)
- Add a **Scan tag** button that opens the camera inside the app.
- Scanning a tag opens the item's **full entry**: SKU, title, every field filled in for that item, and its photos.
- The app finds the entry by looking up the item's ID (scrambled, see item 2) in the items stored on that phone.
- The full record is not stored inside the QR code. A QR code on a 1 to 2 inch sticker reliably holds only about 100 to 150 characters before it's too dense to print and scan. The SKU and title would fit, but notes and all the fields would not, and photos never would. So the QR code stays small and holds the ID.
- The entry can also be opened from an imported HTML report or from the master list, not only from items made on that phone.
- Requested by Joshua, Nov 21, 2026.

### 2. QR codes readable only by the app
- Goal: customers must not be able to scan a tag and reach the inventory. Only workers using the app should be able to read it.
- Now (Test 008): the QR code holds only the item's plain permanent ID, a 26-character code such as `01M7XV5YV2276896MRT1C3CV4E`. It is not a web address. A customer's phone camera would show that code as text and open nothing.
- Plan: scramble the ID with a key kept in the app, so a normal camera app shows meaningless text and only the app's scanner (item 1) can turn it back into the item.
- Limit to keep in mind: the app's code is public on GitHub, so a key inside the app stops casual scanning but not a determined person who reads the code. A key the app keeps on the phone, set once in Settings, would close that gap.
- Build this together with the scanner. Tags printed before then hold the plain ID, so the scanner should still read those old tags.
- Requested by Joshua, Nov 21, 2026.

### 3. Import a report
- A phone can only open a tag for an item it has stored. Add an **Import a report** step that loads another worker's "Send today's work" report (or the master list) into the app.
- That way any worker's phone holds everyone's items and can open any tag.
- Importing the same report twice changes nothing, and a newer edit of an item replaces the older one (matched by the item's permanent ID).
- Requested by Joshua, Nov 21, 2026.

### 4. Optional: hang tags that open on any worker's phone
- A hang tag has room for a bigger QR code. It could also carry the SKU, title and a few key fields, scrambled with the same key as item 2.
- Then scanning it shows those details even on a phone that doesn't have the item yet. The full entry and photos still need the item on the phone (item 3).
- Stickers stay ID only, because they're too small.
- Requested by Joshua, Nov 21, 2026.
