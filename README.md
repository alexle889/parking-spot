# פה חניתי — Desktop App Setup

This folder is a self-contained web app. It uses `localStorage` (not Claude's
artifact storage), so it works fully offline once installed, independent of
Claude entirely.

## Quickest option — no server needed (2 minutes)

1. Unzip this folder anywhere on your computer.
2. Open `index.html` in Chrome or Edge (double-click it).
3. Click the **⋮** menu (top right) → **Cast, save, and share** → **Install page as app**
   (Chrome) — or **⋮** → **Apps** → **Install this site as an app** (Edge).
4. It'll open in its own window and add a desktop/Start-menu icon, just like a
   real app.

This works straight from the file — no hosting needed. The install banner
inside the app itself only appears when served over `http://` or `https://`
(see below), so if you don't see it, use the browser menu instead.

## Full PWA option — offline caching + in-app install banner

Browsers only enable the full install prompt and service worker (offline
caching) over `http://`/`https://`, not `file://`. To get that:

1. Open a terminal in this folder.
2. Run:
   ```
   python3 -m http.server 8080
   ```
3. Open `http://localhost:8080` in Chrome or Edge.
4. You'll see the green **"אפשר להתקין את האפליקציה"** banner in the app, or
   an install icon in the address bar — click it.
5. Once installed, you can stop the local server; the installed app keeps
   working offline (service worker caches everything).

## Notes

- All data (your saved spot, photo, notes) is stored **only on this device**,
  in the browser profile that opened it. It won't sync across computers.
- Photos are compressed client-side before saving, so storage stays small.
- Files:
  - `index.html` — the app
  - `manifest.json` — app name/icon metadata for installability
  - `service-worker.js` — offline caching
  - `icons/` — app icons
