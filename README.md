# Motion Bed — Web app for Bluefy (iPhone, no Mac needed)

Same verified BLE logic as your original diagnostic page, restyled to
feel like a real app: connection status pill, a live bed-position
illustration that reflects Zero G / Flat, and a collapsible diagnostics
panel instead of one always-on log. No native app, no Xcode, no
Playgrounds, no iPad — just this page + the Bluefy browser.

## Why it needs to be hosted (can't just open the file directly)

Web Bluetooth only works on **secure origins** — basically HTTPS sites,
not a local file opened straight from your Files app. This is a browser
security rule, not something Bluefy or this page can work around. So
the page needs a real HTTPS URL. Good news: this can be free and doesn't
require any developer account.

## Hosting it for free with GitHub Pages (~5 minutes)

1. Create a free account at github.com if you don't have one.
2. Create a new repository (e.g. `motion-bed`), set it to **Public**.
3. Upload all three files from this folder — `index.html`,
   `manifest.json`, `icon.svg` — using the "Add file → Upload files"
   button in the repo's web UI (no git command line needed).
4. Go to the repo's **Settings → Pages**. Under "Build and deployment",
   set Source to **Deploy from a branch**, branch `main`, folder `/root`.
   Save.
5. GitHub gives you a URL like
   `https://YOUR-USERNAME.github.io/motion-bed/` — that's your app.
   (Takes a minute or two to go live after the first deploy.)

## Using it on your iPhone

1. Install **Bluefy – Web BLE Browser** from the App Store (free).
2. Open your GitHub Pages URL inside Bluefy (not Safari — Safari has no
   Web Bluetooth support at all).
3. Tap **Connect Bed**, select your bed from the picker, then use Zero G
   / Flat. Test with the bed unoccupied first.
4. Optional, for an app-like icon: in Bluefy's menu, look for "Add to
   Home Screen" (wording may vary by version). This uses the
   `manifest.json` / `icon.svg` included here so it opens full-screen
   without browser chrome, like an installed app.

## What this does and doesn't give you

- **Does:** a real, working, app-like control panel on your iPhone,
  today, for free.
- **Doesn't:** Siri/Shortcuts integration. Shortcuts can't trigger
  JavaScript running inside a browser tab (Bluefy or otherwise) — that
  requires native App Intents, which is the iPad/Xcode path from
  before. If Siri becomes a priority again later, the BLE logic here
  transfers directly into that native project; nothing here is wasted
  work.

## Adding more positions later

Capture the hex the same way you got Zero G / Flat, then add a new
button in `index.html` following the pattern of the existing two
(duplicate the button + the `send(...)` call with the new hex and a
label).
