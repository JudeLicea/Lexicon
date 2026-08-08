# Getting Lexicon onto your phone

Six files, one host, five minutes. After this it lives on your home screen and saves everything locally, forever.

---

## 1. Put the files online

**GitHub Pages** (free, permanent, works from your phone):

1. Go to github.com → **New repository** → name it `lexicon` → **Public** → Create.
2. On the repo page: **Add file → Upload files**. Drag in all six:
   `index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`, `apple-touch-icon.png`
3. **Commit changes.**
4. **Settings → Pages** → under Branch pick `main` and `/ (root)` → **Save**.
5. Wait about a minute, then refresh. It gives you a URL like
   `https://yourname.github.io/lexicon/`

That URL is yours permanently. HTTPS is required for the offline caching to work, and Pages gives you that automatically.

**Alternative:** drag the folder onto [app.netlify.com/drop](https://app.netlify.com/drop). Faster, but claim the site with an account or it expires.

---

## 2. Add it to your home screen

On your iPhone, open the URL **in Safari** (not Chrome — the install prompt is Safari-only on iOS):

Share button → **Add to Home Screen** → Add.

You now have an icon. Tapping it opens fullscreen with no browser chrome, no address bar. It behaves like an app because at that point it is one, as far as iOS is concerned.

---

## 3. Where your words live

In the app's own storage on your phone. They survive closing it, restarting the phone, and being offline.

Two things will wipe them, so know about them:
- Clearing Safari website data
- iOS evicting storage from a web app you haven't opened in about a week — rare once it's on your home screen and in regular use, but real

The **Copy backup** button in the Drawer tab exists for this. Paste it into a note every so often. **Paste backup** restores it, and accepts the backup from the chat version too.

---

## 4. Better definitions (optional)

Out of the box it uses a free dictionary API — no key, no cost, decent definitions, mediocre example sentences.

For definitions written by Claude, with real usage notes and examples that show connotation:

1. Get a key at [console.anthropic.com](https://console.anthropic.com) → API keys. Put $5 on it.
2. In the app: **Drawer** tab → scroll to **Definitions** → paste the key → Save.

The key is stored only on your phone and is never in the code you uploaded, so a public repo is fine. At Haiku pricing, a lookup costs a fraction of a cent — $5 covers years of this.

To use a stronger model, change one line near the top of `index.html`:
```js
const MODEL = 'claude-haiku-4-5-20251001';   // → 'claude-sonnet-5'
```

---

## Updating it later

Edit `index.html` on GitHub (pencil icon), commit, and reopen the app. The service worker fetches fresh and falls back to cache only when offline, so changes show up on the next launch. Your saved words are untouched by updates.
