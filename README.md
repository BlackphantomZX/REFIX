# REFIX 🔧
Smart Repairs. Second Life.
Smartphone repair and refurbishment made simple.

**Status:** Pre-launch · Validation stage · Eureka! 2026 Zonals

🔗 **Live Site:** [Add your Netlify URL here]

---

## 📌 Executive Summary

REFIX replaces the fragmented, low-trust world of smartphone repair — informal technicians, blind quotes, unverified parts — with one structured journey. Customers get a transparent price before committing, a quality-checked repair, and a full service history they can actually trust.
BOOK DIAGNOSIS ──► GET RECOMMENDATION ──► REPAIR / REFURBISH ──► QUALITY CHECK ──► RETURN WITH WARRANTY


## 🌟 Key Features

### 🔍 Structured Diagnosis Flow
- Select your phone model and describe the issue in a guided flow, not a blind shop visit.
- Instant repair recommendation with an upfront estimated cost.

### 🛡️ The Trust Layer
- Transparent pricing shown before you commit.
- Every repair passes a quality check.
- Full repair and service history attached to the device, not lost in a shop's paper log.

### 💸 Tiered, Transparent Pricing
| Tier | Starting Price | What's Included |
|---|---|---|
| Basic Repair | ₹499+ | Common repairs |
| Standard Repair | ₹999+ | Parts + repair + quality check |
| Refurbish | ₹1,999+ | Repair + refurbishment + quality check |

*Planned launch pricing — confirmed at go-live.*

### 📶 Installable, Offline-Capable PWA
- Full Web App Manifest — installs to home screen on Android, iOS (via Safari "Add to Home Screen"), and desktop.
- Service worker with network-first loading for your own files, so updates reach visitors on their next open — not stuck behind a stale cache.
- Automatic update check on return visits and every 30 minutes while the app is open.
- Offline fallback so the page still loads without a connection.

### 📬 Waitlist Capture
- Client-side validated email form with inline success/error feedback.
- Pluggable submission endpoint (Formspree, Apps Script, or your own API) — falls back to local storage until one is configured.

## 🚀 Live Access

| Platform | How to Access | Notes |
|---|---|---|
| 🌐 Web / Desktop | Open the live link | Click the install icon in Chrome/Edge's address bar to install |
| 📱 Android | Open the live link in Chrome | Tap **Install app** in the site menu or Chrome's ⋮ menu |
| 🍎 iPhone | Open the live link in **Safari** | Share → **Add to Home Screen** (no install prompt exists on iOS) |

## ⚡ Quick Start (Local Development)

This is a static site — no build step, no dependencies to install.

### Prerequisites
- Any static file server (Python, Node's `serve`, or VS Code's Live Server extension)

### Run locally
```bash
git clone https://github.com/BlackphantomZX/REFIX.git
cd REFIX
python3 -m http.server 8000
```
Then open `http://localhost:8000`.

> ⚠️ Don't open `index.html` directly as a file — the service worker and install prompt only work when served over `http(s)://`, including `localhost`.

**With VS Code instead:** install the *Live Server* extension → right-click `index.html` → **Open with Live Server**.

## 🛠️ Tech Stack

- **Markup & Styling:** HTML5, Tailwind CSS (via CDN), custom CSS for glassmorphism/theming
- **Fonts:** Space Grotesk (display), Inter (body) — Google Fonts
- **Scripting:** Vanilla JavaScript — mobile menu, waitlist form, install prompt
- **PWA:** Web App Manifest, custom Service Worker (network-first for own assets, stale-while-revalidate for CDN assets)
- **Hosting/Deploy:** Netlify, auto-deployed from this repo on every push to `main`

## 📁 Project Structure

├── index.html # All page content, styling, and JS
├── manifest.webmanifest # App name, colors, icons for install
├── sw.js # Offline caching + auto-update logic
├── _headers # Netlify cache-control rules
└── icons/ # App icons (192, 512, maskable, apple-touch, svg)


## 🧪 Quick Test Checklist

1. **Install flow:** open the live link on Android Chrome → confirm the install icon/button appears → install → icon lands on home screen.
2. **Offline mode:** load the site once → open DevTools → Application → Service Workers → tick "Offline" → refresh → page still loads.
3. **Waitlist form:** submit an invalid email → inline error shows. Submit a valid one → success message shows and resets the field.
4. **Update propagation:** change `VERSION` in `sw.js`, push, reopen the app on a device that's already visited it → it reloads once with the new version.

## ⚙️ Configuration

Set these in `index.html`, inside the `<script>` block near the bottom, before launch:

```js
const CONFIG = {
  WAITLIST_ENDPOINT: '',   // e.g. a Formspree or Apps Script URL
  SOCIAL: { instagram: '', linkedin: '', email: '' }
};
```

Until `WAITLIST_ENDPOINT` is set, submitted emails are saved only in each visitor's own browser and won't reach you.

## 🔄 Deploying Updates

1. Edit the relevant file(s).
2. Bump `VERSION` at the top of `sw.js` (e.g. `refix-v2` → `refix-v3`) so installed copies refresh their cache.
3. Commit and push to `main` — Netlify auto-deploys.

## 🏆 Recognition

Selected for the **Zonals Round** of **Eureka! 2026**, E-Cell IIT Bombay's flagship business model competition.

---

**REFIX** · Smart Repairs. Second Life.
