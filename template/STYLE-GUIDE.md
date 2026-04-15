# Presentation Template — Style Guide

Visual design reference extracted from the website-strategy presentation.

---

## Color System

### Core Palette

| Token | Variable | Value | Usage |
|---|---|---|---|
| Background Primary | `--bg` | `#0a0a0a` | Main slide background |
| Background Secondary | `--bg2` | `#111111` | Divider slides, alternate sections |
| Background Tertiary | `--bg3` | `#181818` | Cards, panels, table rows |
| Text Primary | `--text` | `#f0f0ee` | Body text, headings |
| Text Dimmed | `--dim` | `rgba(240,240,238,0.45)` | Labels, captions, metadata |
| Border | `--border` | `rgba(255,255,255,0.08)` | Card edges, dividers, table rules |

### Accent Colors

| Name | Value | Usage |
|---|---|---|
| BI Green | `#6ba539` | Primary accent — tags, highlights, active states, dots |
| BI Green Dark | `#417714` | Hover states, secondary green |

### Status / Semantic Colors

| State | Value | Usage |
|---|---|---|
| Positive / Check | `var(--bi-green)` / `#8bc34a` | Checkmarks, "yes" badges |
| Negative / Cross | `rgba(255,100,100,0.7)` | Crosses, "no" badges, old/deprecated items |
| Warning / Maybe | `rgba(255,200,60,0.8)` | Partial states, "maybe" indicators |

### Highlight Box

Text highlighted with `.hl` class gets a solid green background box:
```css
.slide-title .hl {
  background: var(--bi-green);
  padding: 0 8px;
  display: inline;
}
```

---

## Typography

### Font Stack

- **Primary:** `Barlow` (Google Fonts) — body text, descriptions
- **Display / Condensed:** `Barlow Condensed` — headlines, tags, labels, numbers, navigation
- Substitute for Bohemia Interactive's commercial font **Effra**

### Google Fonts Import

```html
<link href="https://fonts.googleapis.com/css2?family=Barlow:ital,wght@0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,400&family=Barlow+Condensed:wght@300;400;600;700;800;900&display=swap" rel="stylesheet">
```

### Type Scale

| Element | Font | Size | Weight | Transform | Spacing |
|---|---|---|---|---|---|
| Cover Title | Barlow Condensed | `clamp(56px, 9vw, 120px)` | 900 | uppercase | `-0.02em` |
| Slide Title | Barlow Condensed | `clamp(42px, 7vw, 90px)` | 900 | uppercase | `-0.01em` |
| Sub-heading Title | Barlow Condensed | `clamp(38px, 5.5vw, 72px)` | 900 | uppercase | — |
| Slide Body | Barlow | `clamp(15px, 1.6vw, 18px)` | 400 | — | — |
| Slide Tag | Barlow Condensed | `11px` | 700 | uppercase | `0.18em` |
| Cover Eyebrow | Barlow Condensed | `12px` | 700 | uppercase | `0.2em` |
| Card Title | Barlow Condensed | `20px` | 800 | uppercase | `0.04em` |
| Card Number | Barlow Condensed | `40px` | 900 | — | — |
| Stat Label | Barlow | `12px` | 500 | uppercase | `0.06em` |
| Table Header | Barlow Condensed | `12px` | 700 | uppercase | `0.1em` |
| Table Body | Barlow | `13px` | 400 | — | — |
| Quote | Barlow Condensed | `clamp(26px, 4vw, 48px)` | 700 | — | — |
| Metadata | Barlow | `12px` | 500 | uppercase | `0.06em` |

### Line Heights

| Element | Line Height |
|---|---|
| Cover Title | `0.88` |
| Slide Title | `0.92` |
| Slide Body | `1.65` |
| Quote | `1.2` |
| Cover Subtitle | `1.55` |
| Card Description | `1.5` |

---

## Spacing

### Slide Padding

```css
--slide-pad: clamp(40px, 6vw, 96px);
```

- Inner content max-width: `1200px`, centered
- Top padding includes nav offset: `calc(52px + 64px)`
- Bottom padding: `80px`

### Component Gaps

| Context | Gap |
|---|---|
| Stats row | `20px` |
| Type grid (4-col) | `16px` |
| Conclusion grid (3-col) | `20px` |
| Two-column layout | `48px` |
| Domain pills | `8px` |
| Type props badges | `12px` |

---

## Borders & Surfaces

- Card border: `1px solid var(--border)` (`rgba(255,255,255,0.08)`)
- Card hover: `border-color: rgba(107,165,57,0.5)` + `translateY(-3px)`
- Active card: `border-color: var(--bi-green)`
- Accent left border: `3px solid var(--bi-green)` on highlight panels
- Nav bar border-bottom: `1px solid var(--border)`

---

## Effects

### Backdrop Blur (Nav)
```css
background: rgba(10,10,10,0.92);
backdrop-filter: blur(12px);
```

### Cover Background Effects
- Grid lines: `rgba(107,165,57,0.04)` at `60px` intervals
- Corner glow: `radial-gradient(circle, rgba(107,165,57,0.08) 0%, transparent 70%)`

### Slide Transitions
```css
transition: opacity 0.55s cubic-bezier(0.4,0,0.2,1),
            transform 0.55s cubic-bezier(0.4,0,0.2,1);
```
- Enter: `translateY(30px)` → `translateY(0)`
- Exit: `translateY(0)` → `translateY(-30px)`

### Scrollbar
```css
width: 4px;
thumb: rgba(107,165,57,0.4);
track: transparent;
```
