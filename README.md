# Cheap-Cheap — marketing + policy site

Self-contained static site (no build, no dependencies) — the public web presence that also
provides the **privacy-policy** and **support** URLs both app stores require.

```
site/
├── index.html        # marketing landing (hero, features, screenshots, download CTAs, links)
├── privacy.html      # privacy policy
├── support.html      # support / contact + FAQ
├── assets/logo.png   # Cheap-Cheap logo
└── screens/*.png     # app screenshots used on the landing
```

Brand: paper `#F1ECE1`, ink `#1a1813`, red `#E8332E`, green `#1E7B34`; Inter Tight + Spline Sans
Mono — matching the app's receipt aesthetic.

## Preview locally
```bash
cd site && python3 -m http.server 8090   # → http://localhost:8090/index.html
```

## Host it (gives you the URLs to paste into both stores)

**Easiest — Netlify Drop (~30s, no account coupling):** drag this `site/` folder onto
https://app.netlify.com/drop → you get `https://<name>.netlify.app/` (landing),
`…/privacy.html`, `…/support.html`.

**GitHub Pages on a *new public* repo** (keeps the private app repo private):
```bash
gh repo create cheapcheap-site --public --source=site --remote=site-origin --push
# Settings → Pages → Source: main / root → https://<you>.github.io/cheapcheap-site/
```
Do **not** enable Pages on the private app repo (it would publish internal docs).

**Cloudflare Pages / Vercel:** point at the public repo or drop the folder.

## After hosting — wire the URLs
- **App Store Connect:** Privacy Policy URL + Support URL (App Information / App Privacy).
- **Google Play:** Privacy policy URL (App content) + support contact.
- When the apps are live, replace the `#` hrefs on the "App Store" / "Google Play" buttons in
  `index.html` with the real store links.
