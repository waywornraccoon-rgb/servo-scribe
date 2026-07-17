# Servo-Scribe — Hosting & Install Guide

You now have a full installable web app (PWA). These files must stay **together in one folder**:

```
index.html                 ← the app
manifest.webmanifest       ← app metadata (name, icons)
sw.js                      ← service worker (offline support)
icon-192.png
icon-512.png
icon-512-maskable.png
```

To make it installable, the folder needs to live at an **https:// URL** (installing won't work from a double-clicked local file — that still opens fine in a browser, just without the "Install" option). Pick any one host below; all are free.

---

## Option A — Netlify Drop (easiest, ~2 minutes)

1. Go to **https://app.netlify.com/drop**
2. Drag the whole folder (the six files above) onto the page.
3. Netlify gives you a live URL like `https://your-name.netlify.app`. Done — share that link.

To update later: drag the folder again (or connect it to a Git repo for auto-deploys).

---

## Option B — GitHub Pages (best if you want version control)

1. Create a new GitHub repository (public).
2. Upload the six files to the repo root.
3. Repo **Settings → Pages → Build and deployment → Source: Deploy from a branch**, pick `main` / `root`, Save.
4. Your app appears at `https://<username>.github.io/<repo>/` within a minute or two.

---

## Option C — Cloudflare Pages

1. **https://pages.cloudflare.com** → Create a project → Direct Upload.
2. Upload the folder. It deploys to a `*.pages.dev` URL.

---

## Installing the app (what your playtesters do)

- **Android / Chrome:** open the link → menu (⋮) → **Add to Home screen** (or an "Install" prompt appears).
- **iPhone / Safari:** open the link → Share → **Add to Home Screen**.
- **Desktop Chrome/Edge:** open the link → an **Install** icon appears in the address bar.

After install it launches full-screen with its own icon and works offline. All data is stored locally on each device (nothing is uploaded).

---

## Updating the app after changes

The service worker caches files for offline use, so bump the version whenever you edit the app:

1. Edit `sw.js` and change `const CACHE = "servo-scribe-v1";` to `"servo-scribe-v2"`, etc.
2. Re-upload to your host.
3. Users get the new version next time they open it (may take one reload).

---

## Custom domain (optional)

All three hosts let you attach a domain you own (e.g. `servoscribe.app`) for free in their dashboard under Domain settings.
