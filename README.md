# REFIX — Smart Repairs. Second Life.

REFIX makes smartphone repair and refurbishment simple: transparent pricing, a quality check, and full service history — one structured repair journey instead of hunting for a technician you can trust.

This repo is the REFIX landing page, built as an installable Progressive Web App (PWA).

## Live site

[Add your Netlify URL here once deployed]

## Tech stack

- HTML5 + Tailwind CSS (via CDN)
- Vanilla JavaScript (mobile menu, waitlist form, PWA install prompt)
- Service worker for offline support and auto-updates
- Web App Manifest for installability

## Project structure
├── index.html # All page content, styling, and JS
├── manifest.webmanifest # App name, colors, icons for install
├── sw.js # Offline caching + auto-update logic
├── _headers # Netlify cache-control rules
└── icons/ # App icons (192, 512, maskable, apple-touch)


## Running locally

This is a static site with no build step. To preview it with the service worker working correctly, serve it — don't open `index.html` directly as a file.

**With VS Code:**
1. Install the Live Server extension.
2. Right-click `index.html` → Open with Live Server.

**With Python:**
```bash
python3 -m http.server 8000
```
Then open `http://localhost:8000`.

## Deploying

Connected to Netlify via this GitHub repo. Every push to `main` triggers an automatic deploy.

Publish directory: `.` (root, no build command needed).

## Updating

1. Edit the relevant file(s).
2. Bump the `VERSION` constant at the top of `sw.js` (e.g. `refix-v2` → `refix-v3`) so cached copies on installed devices refresh.
3. Commit and push. Netlify deploys automatically.

## Configuration

In `index.html`, inside the `<script>` at the bottom:

```js
const CONFIG = {
  WAITLIST_ENDPOINT: '',   // e.g. a Formspree or Apps Script URL
  SOCIAL: { instagram: '', linkedin: '', email: '' }
};
```

Set these before launch — until `WAITLIST_ENDPOINT` is filled in, emails are only saved in each visitor's own browser and won't reach you.

## Status

Pre-launch. Content sourced from the REFIX Eureka! 2026 pitch deck.
