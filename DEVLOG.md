# Dev log

Plans and decisions for the store inventory app. Finished builds are listed in the changelog in the [README](README.md).

## Planned

### 1. In-app QR scanner (workers only)
- Add a **Scan tag** button that opens the camera inside the app. Scanning a tag opens that item's card.
- Requested by Joshua, Nov 21, 2026.

### 2. QR codes readable only by the app
- Goal: customers must not be able to scan a tag and reach the inventory. Only workers using the app should be able to read it.
- Now (Test 008): the QR code holds only the item's plain permanent ID, a 26-character code such as `01M7XV5YV2276896MRT1C3CV4E`. It is not a web address. A customer's phone camera would show that code as text and open nothing.
- Plan: scramble the ID with a key kept in the app, so a normal camera app shows meaningless text and only the app's scanner (item 1) can turn it back into the item.
- Limit to keep in mind: the app's code is public on GitHub, so a key inside the app stops casual scanning but not a determined person who reads the code. A key the app keeps on the phone, set once in Settings, would close that gap.
- Build this together with the scanner. Tags printed before then hold the plain ID, so the scanner should still read those old tags.
- Requested by Joshua, Nov 21, 2026.
