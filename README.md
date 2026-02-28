# Stress Loop Mini App (PWA)

A lightweight, private, installable “stress loop” app you can run from a browser or add to your phone’s home screen.  
It supports:
- **Stress events** (rate → choose an action → 5-minute timer → evaluate improvement)
- **Notes anytime** (text + optional voice dictation)  
- **Attachments in notes** (photo + audio recording, stored locally)
- **Daily check-in** (evening reflection prompt)
- **Export** (CSV + JSON)

This is a **privacy-first** app: your data is stored **on your device**, not on a server.

---

## Why this app exists

The core idea is a simple, repeatable loop:

1. **Notice** stress
2. **Name** it (state + intensity)
3. **Do something now** (micro-action)
4. **Evaluate** if it helped (after 5 minutes)
5. **Learn** which actions work best for you over time

The app tracks “what worked” and surfaces your best-performing actions.

---

## What tech/tools were used to build it

This project is intentionally simple: **no frameworks** and no backend.

### Frontend
- **HTML + CSS + Vanilla JavaScript** (single-page app using hash routing)
- UI is fully client-side and runs in any modern browser

### “Installable app” packaging
This is a **Progressive Web App (PWA)** hosted on GitHub Pages:
- `manifest.webmanifest` makes it installable
- `sw.js` (Service Worker) enables offline use + caching
- Icons: `icon-192.png`, `icon-512.png` for home screen/app icon

### Local storage
The app stores data locally (no server):
- **localStorage** for structured app data (stress events, daily reviews, settings, note metadata)
- **IndexedDB** for large attachments (photos + audio recordings) as blobs

This avoids common storage limits and makes photo/audio possible without breaking saving.

### Hosting / deployment
- **GitHub Pages** for free static hosting
- Updates deploy automatically on each commit to `main`

---

## Data & privacy model (important)

### Where is my data stored?
On **your device** only:
- **Stress events, notes text, daily check-ins, settings:** stored in your browser storage (`localStorage`)
- **Note attachments (photos/audio):** stored in your browser database (`IndexedDB`)

### Can anyone else see my entries?
No. Other visitors to the site cannot access your local storage.  
However:
- Anyone using **your device** could open the app and view your entries.
- Clearing browser/site data can erase your local data.
- Attachments are stored locally and are not included in CSV export.

### No server
There is:
- no login
- no cloud database
- no analytics tracking
- no sharing of your private content unless you explicitly use the Share button

---

## Features (detailed)

### 1) Stress events (the core loop)
1. Tap **Stress event**
2. Fill:
   - State (stressed/anxious/angry/…)
   - Intensity (0–10)
   - “What happened?” (short)
   - Context (work/home/…)
3. Choose an action (or add your own)
4. Start a **5-minute timer**
5. Evaluate after timer:
   - New intensity (0–10)
   - “Did it work?” (yes/no/unsure)
   - Helpfulness rating (0–10)
6. The app computes:
   - **Improvement Δ = start intensity − end intensity**
7. The dashboard learns which actions produce the biggest improvement

### 2) Notes (any time)
- Write a note any time
- Optional **voice dictation-to-text** (depends on browser support)
- Optional attachments:
  - **📷 Photo**
  - **🎙️ Audio recording** (depends on browser support)
- View attachments later inside the app

### 3) Daily check-in (evening reflection)
At a time you choose (default 8pm):
- “How was your day overall?”
- “What did you achieve?”
- “What can be better tomorrow?”

Note: phone browsers do not reliably run background tasks, so the reminder appears when the app is open after that time.

### 4) Export
- Stress events: CSV
- Notes: CSV (includes IDs for attachments)
- Daily check-ins: CSV
- JSON backup: includes full state (not attachments)

---

## Installation (how users use it like a real app)

### iPhone (Safari)
1. Open the GitHub Pages URL
2. Tap **Share**
3. Tap **Add to Home Screen**
4. Open from the new icon

### Android (Chrome)
1. Open the GitHub Pages URL
2. Tap **⋮**
3. Tap **Install app** (or “Add to Home screen”)

---

## Repository structure
