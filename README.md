# Putting Wortdetektiv on GitHub Pages

**You do not need Git, a terminal, or any developer tools.** Everything below happens in a browser, by dragging files onto a web page. It takes about ten minutes.

---

## Before you start — two things that will surprise you

**1. The repository has to be public.** GitHub Pages only works from a **public** repository on the free plan; private-repo Pages requires GitHub Pro. So the app will sit at a public web address that anyone who guesses the URL can open.

**Is that a problem?** Weigh it yourself, but the facts are:
- The files contain only German and French vocabulary and word histories. Nothing about Laya.
- Her progress is stored **in her browser**, not on the server. It is never uploaded, and no one else can see it.
- The URL is not indexed or advertised, but it is not secret either.
- Do **not** put her name in the repository name. `wortdetektiv` — not `laya-german`.

**2. You will probably hit two-factor authentication.** GitHub made 2FA mandatory for accounts that push code. If it has been a while, expect a password reset and a 2FA enrolment (authenticator app or SMS) before you can do anything. Budget five minutes for this and do it first.

---

## Step 1 — Get into GitHub

1. Go to **github.com** and sign in. Reset the password if you need to.
2. Complete the 2FA enrolment if it asks.

## Step 2 — Make the repository

1. Top right, **+** → **New repository**.
2. **Repository name:** `wortdetektiv`
3. **Public** (it has to be — see above).
4. Leave every checkbox unticked. Do **not** add a README.
5. **Create repository**.

## Step 3 — Upload the files

1. On the empty repository page, click **uploading an existing file**.
2. Drag in all six files:
   - `index.html`
   - `manifest.webmanifest`
   - `sw.js`
   - `icon-192.png`
   - `icon-512.png`
   - `apple-touch-icon.png`
3. **Commit changes**.

> Keep them at the top level. Do not put them in a folder — the paths expect the root.

## Step 4 — Switch Pages on

1. **Settings** (repository tab, not your account settings).
2. Left sidebar → **Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. **Branch:** `main`, folder `/ (root)`. **Save**.
5. Wait one to two minutes. Refresh. A green box appears with the address.

Your address will be:

```
https://YOUR-USERNAME.github.io/wortdetektiv/
```

> **The first deploy can 404 for a couple of minutes.** That is normal. Give it five before assuming anything is wrong.

## Step 5 — Install it on her devices

**iPhone / iPad** — must be Safari, not Chrome:
1. Open the address in **Safari**.
2. Share button (the square with the arrow) → **Add to Home Screen**.
3. Name it **Wortdetektiv** → **Add**.

**Android** — Chrome → three-dot menu → **Add to Home screen** / **Install app**.

**Windows desktop** — Chrome or Edge → the install icon in the address bar, or three-dot menu → **Cast, save and share** / **Apps** → **Install this site as an app**.

## Step 6 — The test that actually matters

On **each** device, separately:

1. Open it from the home screen icon.
2. Check the header chip says **✓ Gesichert**.
3. Open one case.
4. **Fully close the app** — swipe it away, do not just background it.
5. Reopen. Is the case still open in **Archiv**?

If yes, that device is sound. If the chip says **⚠ Nicht gesichert**, that device is blocking storage — check it is not in Private Browsing.

---

## Things to know afterwards

**Progress does not sync between devices.** Each device keeps its own. That is what browser storage is. If she does cases on the iPad and you want them on the laptop, use the **Sichern** tab: **Kopieren** on one, paste into the box on the other, **Laden**.

**Suchen is switched off here.** The live Detektiv needs an API key, and a key on a public page is a key anyone can take and bill to you. All 95 filed cases work normally. Turning it back on means a small proxy — a Cloudflare Worker on the free tier — which keeps the key on a server instead of in the page.

**To update the app later:** upload a new `index.html`, *and* open `sw.js` and change `wortdetektiv-v1` to `wortdetektiv-v2`. If you forget, phones will keep serving the cached old version and you will think the upload failed.

**Never change the storage key.** It is `wortdetektiv:v1`, near the top of the script in `index.html`. Change it and she starts from zero.

**It works offline.** After the first successful load, the service worker caches everything. No signal needed on a train or a plane.
