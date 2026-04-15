# Presentation Template — Branding

How to adapt the template for different presentation topics and brands.

---

## Base Identity

The template uses **Bohemia Interactive** corporate branding as its default:

| Element | Default Value |
|---|---|
| Company | Bohemia Interactive |
| Primary Accent | `#6ba539` (BI Green) |
| Logo | BI arrow SVG |
| Font | Barlow / Barlow Condensed |
| Background | Near-black `#0a0a0a` |
| Tone | Dark, technical, premium |

---

## Customizing Per Presentation

Each new presentation folder can override these values by changing the CSS custom properties in the `<style>` block:

```css
:root {
  --bi-green: #6ba539;      /* ← change this to your accent color */
  --bi-green-dark: #417714;  /* ← darker variant for hovers */
  --bg: #0a0a0a;            /* ← main background */
  --bg2: #111111;           /* ← secondary background */
  --bg3: #181818;           /* ← card/panel background */
  --text: #f0f0ee;          /* ← primary text color */
  --dim: rgba(240,240,238,0.45);  /* ← dimmed text */
  --border: rgba(255,255,255,0.08); /* ← subtle borders */
}
```

---

## Brand Color Reference (BI Games)

For presentations about specific BI products, use these brand colors:

| Brand | Primary Color | Background Tint | Character |
|---|---|---|---|
| Bohemia Interactive | `#6ba539` | `#0a0a0a` neutral | Corporate, green |
| DayZ | `#c0392b` | `#080808` warm black | Blood red, survival horror |
| Arma Reforger | `#c49020` | `#0c0e09` green-black | Military gold, tactical |
| Enfusion Engine | `#00A3E0` | `#040608` blue-black | Electric blue, tech |

---

## Logo

The nav bar logo area consists of:

1. **SVG icon** — the BI arrow mark (see `COMPONENTS.md` for the nav bar)
2. **Company text** — `Barlow Condensed 13px 700`, uppercase, `letter-spacing: 0.1em`

To rebrand for a different team/division:
- Replace the SVG with your logo
- Update the text label
- Keep the sizing: icon at `22x24px`, text at `13px`

---

## Cover Slide Branding

The cover slide establishes the presentation identity:

- **Eyebrow:** `"Company Name · Context"` — e.g., `"Bohemia Interactive · Internal Presentation"`
- **Title:** 2-3 lines, one word accented with `.green` class
- **Subtitle:** 1-2 sentences explaining the topic
- **Metadata row:** Author / Department / Date

---

## Dark Theme Only

The template is designed exclusively for dark backgrounds. All text colors, border opacities, and surface colors assume a dark context. Do not use on light backgrounds without a full retheme.

---

## Accessibility Notes

- Text contrast ratios are optimized for dark mode but some dimmed elements (`--dim`) are decorative and should not carry critical information alone
- The green accent `#6ba539` on `#0a0a0a` meets WCAG AA for large text
- Interactive elements (cards, dots, arrows) have hover states with visible color changes
