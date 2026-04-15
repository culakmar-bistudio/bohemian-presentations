# Bohemia.net Demo — Handover for OpenCode

## Context

Martin Baar (Web/Marketing @ Bohemia Interactive) built this demo for a **website strategy presentation** arguing for a unified `bohemia.net` hub over individual game websites. The demo is meant to convince brand managers they won't lose creative identity within a shared hub.

**Meeting:** Internal strategy presentation — "Websites Strategy 2026–2027"  
**Core argument:** One nav structure, one domain, one account system — but each game brand (DayZ, Arma, Enfusion) retains a completely distinct visual identity. The hub switcher dropdown (BI logo click) is the visual proof.

---

## Project Location

```
C:\Users\MartinBaar\Claude Code\Bohemia.net Demo\
├── index.html          ← Hub homepage (Bohemia Interactive)
├── dayz.html           ← DayZ brand page
├── arma.html           ← Arma Reforger brand page
├── enfusion.html       ← Enfusion Engine page
├── logo-dropdown.png   ← Figma reference: hub switcher dropdown variants
├── primary-navigation.png ← Figma reference: 4 nav bar designs
└── HANDOVER.md         ← This file
```

To preview: serve with any static HTTP server from this directory.  
Python: `python -m http.server 8052`  
Then open: `http://localhost:8052/index.html`

---

## Design System (sourced from live careers.bohemia.net)

| Token | Value |
|---|---|
| Font | **Effra** (commercial) → **Barlow** via Google Fonts (substitute used in demo) |
| BI Green | `#6ba539` |
| BI Green Dark | `#417714` |
| Text Primary | `#222` |
| Nav height | `64px` |
| Framework | Pure HTML/CSS — no build pipeline |

---

## Nav Architecture (THE KEY DEMO ELEMENT)

All 4 pages share the **same leftmost element**: the BI logo hub-switcher button. Clicking it opens a dropdown showing the full ecosystem. Everything to the right of it changes per brand.

```
[BI logo ▾] | [Game logo]    [nav links...]    [Account] [CTA]
 ↑ IDENTICAL                  ↑ DIFFERENT       ↑ DIFFERENT
  on all pages
```

### Hub Switcher Dropdown (shared on ALL pages)
```
Games           Hub
Arma Reforger   Home
DayZ            Store
Arma 3          Careers
All games →     Community
                Forums
Development
Enfusion Engine
Incubator
```

### Nav variants by page:
| Page | Nav bg | Game logo | Nav links | CTA |
|---|---|---|---|---|
| `index.html` | `#f0f0ee` (light) | "Bohemia Interactive" text | HOME · GAMES · COMMUNITY · CAREERS · COMPANY · SHOP | — |
| `dayz.html` | transparent → `#080808` | "DayZ" bold white | GAME · DEV HUB · FORUMS · FAQ · PRESS KIT · MINI DAYZ · MERCH | "BUY DAYZ NOW" outlined white |
| `arma.html` | transparent → `#0c0e09` | Diamond icon + "ARMA REFORGER" | GAME · ROADMAP · DEV HUB · FAQ · NEWS · MEDIA · STORE · WORKSHOP | "PLAY ARMA REFORGER NOW" gold `#c49020` |
| `enfusion.html` | transparent → `#040608` | "ENFU**SION**" (SION in blue) | ENGINE · FEATURES · DOCUMENTATION · GAMES · SHOWCASE | "EXPLORE ENFUSION" blue `#00A3E0` |

---

## Page Visual Identities

### index.html — Hub
- Light gray nav `#f0f0ee`, dark text
- Hero: Arma Reforger library_hero.jpg with dark overlay
- Headline: "GAMES WORTH [PLAYING]" — "PLAYING" in green highlight box (careers.bohemia.net pattern)
- Sections: Brand tiles grid (DayZ/Arma/Enfusion), News grid, "One Hub. Infinite Worlds." value strip

### dayz.html — Survival Horror
- Background: `#080808` near-black
- Accent: `#c0392b` blood red
- Font character: Bold condensed, tracking
- Hero: DayZ library_hero.jpg, "THIS IS YOUR [STORY]" — STORY in red
- Sections: DayZ Badlands featured announcement, news grid (dark cards), red CTA strip

### arma.html — Military Simulation
- Background: `#0c0e09` dark green-black
- Accent: `#c49020` military gold
- Hero: Arma Reforger library_hero.jpg, "CHOICE IS [YOURS]" — YOURS in gold
- Sections: 3 feature blocks (01 Multiplatform / 02 Multiplayer / 03 Workshop), Kolguyev Island announcement, news grid, Road to Arma 4 section with numbered steps

### enfusion.html — Tech/Engine
- Background: `#040608` near-black with blue tint
- Accent: `#00A3E0` electric blue
- Hero: Animated CSS grid background (no image), tech metrics panel on right (100+ km² / 128 players / 60fps)
- Headline: "POWERING THE NEXT [GENERATION]" — GENERATION in blue
- Sections: 3 tech pillars, 4-item tech detail grid, Games built on Enfusion, CTA block

---

## Image Sources (hotlinked from Steam CDN — reliable for demo)

```
DayZ hero:    https://cdn.akamai.steamstatic.com/steam/apps/221100/library_hero.jpg
DayZ header:  https://cdn.akamai.steamstatic.com/steam/apps/221100/header.jpg
Arma hero:    https://cdn.akamai.steamstatic.com/steam/apps/1874880/library_hero.jpg
Arma header:  https://cdn.akamai.steamstatic.com/steam/apps/1874880/header.jpg
Arma 3 hero:  https://cdn.akamai.steamstatic.com/steam/apps/107410/library_hero.jpg
```

---

## ⚠️ KNOWN BUG TO FIX FIRST

### BI Logo SVG is malformed

The BI arrow logo SVG path in all 4 nav bars is a rough manual approximation that renders incorrectly. The **full correct path data** was retrieved from the live careers.bohemia.net source just before handover.

**In every HTML file, find this block and replace the `<path d="...">` inside the `.bi-logo` SVG:**

```html
<!-- FIND this SVG in the nav (present in all 4 files): -->
<svg class="bi-logo" viewBox="0 0 61 65" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M36.5 1.6L40 12.7 ... [rough approximation]" fill="white"/>
</svg>

<!-- REPLACE the path with these 3 correct paths: -->
<svg class="bi-logo" viewBox="0 0 61 65" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M36.5263 1.59133C36.251 2.4754 35.3267 5.34373 34.4614 7.96648L32.8882 12.7405L31.1478 12.7994C23.4389 13.0843 15.9956 16.4438 9.10282 22.7698C6.80196 24.8817 4.75675 27.5045 3.25234 30.2746L2.78037 31.139H4.4421H6.10383L6.96911 29.7343C9.06349 26.3061 11.1382 24.0271 14.3535 21.6107C18.7389 18.3101 23.7733 16.1392 28.5815 15.4713C29.7614 15.3141 32.0033 15.1668 32.0033 15.2552C32.0033 15.373 30.7643 18.8406 28.021 26.424C26.5166 30.5595 25.2285 34.1252 25.1498 34.3511L25.0023 34.7735H20.4498H15.8972L13.9012 37.5927C12.7999 39.1448 11.8855 40.4414 11.8658 40.4905C11.8461 40.5298 12.0231 40.5004 12.2591 40.412C13.3702 40.019 16.8903 39.2528 19.5648 38.8108C21.3249 38.5161 23.6553 38.192 23.6946 38.2312C23.7143 38.2509 22.3573 42.0524 20.6661 46.6889L17.6081 55.1072H16.1234C13.0261 55.1072 10.4302 54.5178 7.98188 53.2703C5.90718 52.2094 4.30444 50.7949 3.03602 48.9089C2.31823 47.8382 1.94458 47.0622 1.57094 45.8539C1.32512 45.0681 1.25629 44.96 0.676162 44.3903C0.322183 44.0563 0.0272013 43.8009 0.00753588 43.8206C-0.0121296 43.8402 0.00753588 44.1938 0.0566996 44.5966C0.322183 46.9934 1.0793 49.1545 2.32806 51.0307C3.09502 52.1996 4.9829 54.0562 6.21199 54.8518C8.93566 56.6298 12.4558 57.6612 15.8087 57.6612C16.2807 57.6612 16.6642 57.671 16.6642 57.6907C16.6642 57.7103 16.0644 59.3606 15.3368 61.3547C14.6091 63.3487 14.0094 64.9892 14.0094 64.999C14.0094 65.0187 14.4027 64.7436 14.8746 64.39L15.7399 63.7613L16.9592 60.7063C17.9523 58.2015 18.2079 57.6514 18.3751 57.6219C18.4931 57.5924 19.024 57.5335 19.5648 57.4647C24.7074 56.9048 30.666 54.4 35.4054 50.8244C40.1743 47.2291 44.186 42.3667 46.2214 37.7106L46.6934 36.6399H53.1928H59.6922L60.351 35.7067L61 34.7735H54.2252C50.0955 34.7735 47.4407 34.7342 47.4407 34.6851C47.4407 34.636 47.5685 34.0859 47.7258 33.4769C48.2863 31.306 48.3748 30.5889 48.3649 28.143C48.3649 26.1686 48.3453 25.756 48.1486 24.8817C47.5193 21.9938 46.3099 19.6461 44.4613 17.7208C43.3699 16.5813 42.603 15.9624 41.305 15.1864C40.1054 14.4595 38.5912 13.8407 37.018 13.4379C35.9265 13.153 35.8577 13.1236 35.9364 12.9271C36.015 12.7208 40.9216 0.35363 41.0199 0.117874C41.0592 0.0294724 40.6266 0 39.0533 0H37.0278L36.5263 1.59133Z" fill="currentColor"/>
  <path d="M36.5165 15.8249C39.5548 16.6206 42.2981 18.4869 43.8517 20.8248C44.4515 21.7187 45.2086 23.3493 45.4643 24.2629C46.2509 27.1214 46.1132 30.4416 45.071 33.8109L44.776 34.7735H36.0248C27.7162 34.7735 27.2639 34.7637 27.3229 34.5967C27.3622 34.5083 29.0829 30.1764 31.1478 24.9701L34.9039 15.5106L35.3366 15.5695C35.5725 15.6088 36.1035 15.7169 36.5165 15.8249Z" fill="currentColor"/>
  <path d="M43.9009 36.8658C43.9009 36.9248 43.5862 37.5633 43.2027 38.2607C40.6561 42.9365 36.9983 46.8755 32.2982 49.9894C29.7614 51.6692 27.3917 52.8283 24.6287 53.732C22.6917 54.3705 19.5353 55.0581 19.3584 54.8813C19.2994 54.8223 25.8578 38.1527 26.0053 37.9857C26.1921 37.7696 34.9531 37.0918 40.7052 36.8462C43.5764 36.7185 43.9009 36.7185 43.9009 36.8658Z" fill="currentColor"/>
</svg>
```

**Important:** 
- On `index.html` (light nav): use `fill="currentColor"` — the nav button has `color: var(--text-primary)` = `#222` (dark), so it renders dark on the light background. ✓
- On `dayz.html`, `arma.html`, `enfusion.html` (dark nav): use `fill="white"` on all 3 paths, or set `color: white` on the button. ✓

---

## Remaining Polish Tasks (priority order)

### 1. Fix BI Logo (see above) — do this first, all 4 files

### 2. index.html — Hero image is Arma (wrong for hub page)
The hub hero currently uses the Arma Reforger library_hero.jpg. This was a placeholder. Consider:
- Using a composite/neutral dark image
- OR: a CSS-animated dark background similar to the Enfusion grid
- OR: keep Arma but add a note in the demo that this would be BI's own brand imagery

### 3. News card images (dayz.html, arma.html)
The news card screenshot URLs use guessed Steam CDN screenshot IDs that may return 404. Add `onerror` fallbacks (already partially done) or replace with the header.jpg fallbacks. Could also use:
- `https://cdn.akamai.steamstatic.com/steam/apps/221100/ss_1.600x338.jpg` etc.
- Or simply use the `header.jpg` for all news card images as a reliable fallback

### 4. Hub dropdown styling refinement
The dropdown on dark pages (DayZ/Arma/Enfusion) renders correctly in dark. On `index.html` the dropdown is white/light which is correct. Minor: add a small top triangle/arrow pointer on the dropdown to make it feel more polished.

### 5. Mobile nav (not implemented)
No hamburger menu. For the demo presentation this is fine (presenting on laptop/screen). If needed later, add a simple hamburger that shows a full-screen overlay nav.

### 6. Scroll indicator on DayZ hero ("SCROLL" text)
The `hero-scroll` div is visible. On DayZ the hero fills 100vh and it works. The Arma/Enfusion pages don't have scroll indicators — consistent with their identity (more austere). Fine as-is.

### 7. Enfusion hero metrics panel
The metrics (100+ / 128 / 60fps) sit in `.hero-metrics` with `position: absolute; right: 64px`. At narrow widths this overlaps the headline. Add a media query to hide or reposition at < 1024px.

---

## What Was NOT Built (out of scope for demo)

- Individual game DLC/sub-pages
- Workshop page
- Careers sub-sections (already live at careers.bohemia.net)
- Feedback Tracker embed
- Search functionality
- Account/login flow
- Any actual CMS backend
- Mobile responsive nav (hamburger menu)
- The "Bohemia Account" concept / login wall features

---

## Figma Reference File

`https://www.figma.com/design/UvnfYiJz3J4vNIlgxtb05A/🌐-Bohemia.net`

Martin has View access via the BOHEMIA INTERACTIVE org seat. The file contains:
- Full nav component designs (4 variants)
- Hub switcher dropdown variants (multiple color themes)
- Full page designs for the hub and game pages

Note: Figma MCP call limit was hit during this session (View seat restriction on the Pro workspace). To access again, use the Figma desktop app with the file open for plugin-based tools.

---

## Reference: Live Sites Used for Content

| Site | Used for |
|---|---|
| `careers.bohemia.net` | Design system source of truth (live, already built in new design) |
| `dayz.com` | Real headlines, taglines, DayZ content |
| `reforger.armaplatform.com` | Real Arma Reforger content, feature copy |
| `bohemia.net` | Hub page structure reference |
| Steam CDN | All game hero/screenshot images |
| `cms-cdn.bistudio.com` | BI's own CDN for news thumbnails (requires known URLs) |

---

## Session Notes

- Font used in demo: **Barlow** (Google Fonts) as substitute for **Effra** (BI's commercial font, used on careers.bohemia.net). If Effra is available, swap the Google Fonts import for it.
- The careers logo SVG (white version) is at: `https://careers.bohemia.net/images/careers-logo.svg`
- The careers logo SVG (dark/black version) is at: `https://careers.bohemia.net/images/careers-black.svg`
- The BI green CSS variable from the live site: `--accent-bohemia: #6ba539`
- The nav on dark pages uses `backdrop-filter: blur(12px)` on scroll — requires a browser that supports it (all modern browsers do)
