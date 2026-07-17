# ⚔ Servo-Scribe

A companion **battle ledger** for Warhammer 40,000 (11th edition) that lets **any AI assistant** act as your opponent or tactical coach.

You move the models — on a physical table or in Tabletop Simulator — and Servo-Scribe keeps the bookkeeping (rosters, wounds, command points, victory points, objectives). Each turn you copy the battle state into your AI of choice (Claude, ChatGPT, Gemini, …) and it plays the opponent or advises your moves. For physical games you can send it a photo of the board so it reads unit positions.

Installable as a web app (PWA): works offline, gets its own icon, and stores all data locally on your device — nothing is uploaded.

---

## Features

- Two-army tracker with per-unit models, wounds, Toughness/Save/Invuln/OC, points, and notes
- Per-turn status flags: in cover, hidden, battle-shocked, engaged, in reserve
- Objective control, command points, victory points, battle round & phase
- **Import list** — paste a text export from the Warhammer 40,000 app, BattleScribe, or New Recruit
- **Copy state for AI** — puts the whole battle on your clipboard as a ready-to-paste prompt
- **Get stats from AI** — asks any AI to fill datasheet stats for imported units
- Built-in **Help & guide** for playtesters
- Faction-agnostic, offline, no account, no tracking

---

## Run it locally

Just open `index.html` in any browser. (The "install" option only appears when it's served over https — see below.)

---

## Deploy to GitHub Pages

### Option 1 — Web upload (no command line)

1. Create a new **public** repository on GitHub (e.g. `servo-scribe`).
2. On the repo page choose **Add file → Upload files**, drag in all the files from this folder, and **Commit**.
3. Go to **Settings → Pages**.
4. Under **Build and deployment → Source**, choose **Deploy from a branch**.
5. Set branch to **`main`** and folder to **`/ (root)`**, then **Save**.
6. Wait ~1–2 minutes. Your app is live at:
   `https://<your-username>.github.io/<repo-name>/`

### Option 2 — Command line

```bash
git init
git add .
git commit -m "Servo-Scribe: initial commit"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

Then enable Pages via **Settings → Pages** as in steps 3–6 above.

---

## Installing the app (share this with playtesters)

- **Android / Chrome:** open the link → menu (⋮) → **Add to Home screen**
- **iPhone / Safari:** open the link → Share → **Add to Home Screen**
- **Desktop Chrome/Edge:** open the link → **Install** icon in the address bar

---

## Updating after changes

The service worker caches files for offline use. Whenever you edit the app, bump the cache version so users get the update:

1. In `sw.js`, change `const CACHE = "servo-scribe-v1";` to `"servo-scribe-v2"`, etc.
2. Commit and push.
3. Users receive the new version on their next reload.

---

## File layout

```
index.html                 the app (HTML + CSS + JS, single file)
manifest.webmanifest       PWA metadata
sw.js                      service worker (offline cache)
icon-192.png               app icon
icon-512.png               app icon
icon-512-maskable.png      maskable app icon (Android)
README.md                  this file
HOSTING.md                 hosting options (Netlify / Pages / Cloudflare)
```

---

## Notes

- 11th-edition rules assumptions baked into the AI prompt: 2″ engagement range, terrain gives −1 to hit + Hidden, objectives sit inside terrain.
- Datasheet stats are not included in army-list exports, so imported units start flagged for stats — fill them with **Get stats from AI** or by hand.
- Not affiliated with or endorsed by Games Workshop. Warhammer 40,000 is a trademark of Games Workshop Ltd. This is an unofficial fan-made tool.
