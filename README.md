# MHW: Iceborne — 100% Tracker

Live tracker for **ghost. (Alson)** and **qunyx.** — Monster Hunter: World: Iceborne, 100 achievements on Steam.

- Alson: 38/100 · qunyx.: 36/100 · both missing the same 62 (snapshot: 27 Nov 2026)
- Data source: Steam achievement feeds for `alsonn` and `Quunyx` (app 582010)
- The page reads `snapshot.json` in this same repo. Steam blocks a web page from
  pulling Steam directly, so the page itself cannot fetch Steam. rem refreshes
  `snapshot.json` from Steam every day, and any time you ask rem in chat to
  “refresh the MHW tracker now”. The “Check for updates” button on the page
  re-reads the latest `snapshot.json`.

## Setup — Alson, 2 steps (rem cannot do these)

The Muse GitHub App cannot create repositories (it returned
`403 Resource not accessible by integration` when rem tried), so:

1. **Create the repo:** on github.com, create a new **public** repository
   named `mhw-tracker` under `ghost-alson` (no README / .gitignore needed).
   Then, in Muse, go to Connectors → GitHub and make sure `mhw-tracker` is
   selected for the Muse GitHub App — otherwise rem cannot push to it.
2. **Push these files:** tell rem “push the MHW tracker files” — rem will push
   `index.html`, `snapshot.json` and this README to the `main` branch.
3. **Enable Pages:** in the repo, Settings → Pages → Build and deployment →
   Source: **Deploy from a branch**, Branch: **main**, Folder: **/ (root)** →
   Save. The site will then be live at:
   **https://ghost-alson.github.io/mhw-tracker/**
   (GitHub Pages can take a few minutes after the first deploy.)

## Files

- `index.html` — the tracker page. Real pictures only: official Steam library
  art for Monster Hunter: World, and the real Steam achievement icons
  (all 200 icon URLs verified HTTP 200 on 27 Nov 2026).
- `snapshot.json` — the Steam snapshot (100 achievements per player, with
  name, description, unlocked flag, unlock timestamp and icon URLs).
  Replaced on every refresh; the page never stores manual ticks — Steam is
  the source of truth.

## Daily refresh

A Muse cron re-pulls both Steam feeds and pushes an updated `snapshot.json`.
Manual refresh: ask rem in chat to refresh the tracker now.
