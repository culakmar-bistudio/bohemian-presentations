# Presentation Template — Slide Layouts

All available slide layout patterns, extracted from the website-strategy presentation.

---

## 1. Cover Slide

Full-viewport opening slide with large title, subtitle, and metadata.

```
┌──────────────────────────────────────────────┐
│  [grid lines background]         [glow blob] │
│                                              │
│  ── Eyebrow Text                             │
│                                              │
│  LARGE                                       │
│  TITLE                                       │
│  ACCENT LINE                                 │
│                                              │
│  Subtitle paragraph text,                    │
│  max-width 560px                             │
│                                              │
│  Author  /  Department  /  Date              │
│                                              │
└──────────────────────────────────────────────┘
```

**Key properties:**
- Background: subtle grid lines + radial glow in bottom-right
- Eyebrow: green accent line before text, uppercase, `12px`
- Title: largest type scale `clamp(56px, 9vw, 120px)`, one word per line
- Accent word: `.green` class for colored text
- Subtitle: dimmed text, `max-width: 560px`
- Metadata: row of items separated by `/` dividers

---

## 2. Title + Two Column

Large title with tag, content split into two columns below.

```
┌──────────────────────────────────────────────┐
│  ── Tag Label                                │
│                                              │
│  LARGE TITLE                                 │
│  SECOND LINE                                 │
│                                              │
│  ┌─────────────────┐  ┌─────────────────┐    │
│  │  Body text       │  │  Cards / Grid   │    │
│  │                  │  │  or visual      │    │
│  │  + stat cards    │  │  elements       │    │
│  │    below         │  │                 │    │
│  └─────────────────┘  └─────────────────┘    │
└──────────────────────────────────────────────┘
```

**Used in:** Problem slide, Proposal slide  
**Grid:** `grid-template-columns: 1fr 1fr; gap: 48px;`  
**Mobile:** Collapses to single column at `860px`

---

## 3. Title + Type Grid (4 Column Cards)

Title and description, followed by a 4-column card grid.

```
┌──────────────────────────────────────────────┐
│  ── Tag Label                                │
│                                              │
│  LARGE TITLE                                 │
│                                              │
│  Description text (full width)               │
│                                              │
│  ┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐        │
│  │ 01   │ │ 02   │ │ 03   │ │ 04   │        │
│  │ NAME │ │ NAME │ │ NAME │ │ NAME │ │       │
│  │ desc │ │ desc │ │ desc │ │ desc │        │
│  └──────┘ └──────┘ └──────┘ └──────┘        │
│                                              │
│  ┌─ Comparison Table ──────────────────┐     │
│  │  Header  │  Col 2  │  Col 3  │ ... │     │
│  │  Row 1   │         │         │     │     │
│  │  Row 2   │         │         │     │     │
│  └─────────────────────────────────────┘     │
└──────────────────────────────────────────────┘
```

**Used in:** Taxonomy slide  
**Grid:** `grid-template-columns: repeat(4, 1fr); gap: 16px;`  
**Mobile:** 2 columns at `900px`  
**Cards have:** number, name, badge (emoji), description

---

## 4. Split Layout — Content + Banner Image

Left side has content (60%), right side has a banner image or visual panel (40%).

```
┌──────────────────────────────────────────────┐
│  ┌─────────────────────┐ ┌────────────────┐  │
│  │  ── Tag Label        │ │                │  │
│  │                      │ │  Background    │  │
│  │  TITLE               │ │  Image         │  │
│  │                      │ │  (opacity 0.35)│  │
│  │  [prop badges]       │ │                │  │
│  │                      │ │  gradient      │  │
│  │  Body text           │ │  overlay       │  │
│  │                      │ │  from left     │  │
│  │  Examples list       │ │                │  │
│  │                      │ │                │  │
│  │  Diagram/visual      │ │                │  │
│  └─────────────────────┘ └────────────────┘  │
└──────────────────────────────────────────────┘
```

**Used in:** Format detail slides (Presentation Website, Landing Page, Microsite, Web App)  
**Banner:** `position: absolute; right: 0; width: 38%;` with gradient overlay  
**Content:** `max-width: 62%`, padded away from banner  
**Mobile:** Banner hidden at `860px`, content goes full width

---

## 5. Demo / Tile Grid

Title + description, followed by a grid of clickable image tiles.

```
┌──────────────────────────────────────────────┐
│  ── Tag Label                                │
│                                              │
│  LARGE TITLE                                 │
│                                              │
│  Description text                            │
│                                              │
│  ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐│
│  │  img   │ │  img   │ │  img   │ │  img   ││
│  │  ───── │ │  ───── │ │  ───── │ │  ───── ││
│  │  Label │ │  Label │ │  Label │ │  Label ││
│  └────────┘ └────────┘ └────────┘ └────────┘│
│                                              │
│  ┌─ Info Panel ────────────────────────────┐ │
│  │  Bullet points                          │ │
│  └─────────────────────────────────────────┘ │
└──────────────────────────────────────────────┘
```

**Used in:** Live Demo slide  
**Tiles:** `aspect-ratio: 16/10`, image with label overlay at bottom  
**Grid:** `grid-template-columns: repeat(4, 1fr); gap: 12px;`  
**Mobile:** 2 columns at `900px`

---

## 6. Conclusion / Summary Grid

Title + subtitle, followed by a 3-column card grid for key takeaways.

```
┌──────────────────────────────────────────────┐
│  ── Tag Label                                │
│                                              │
│  LARGE TITLE                                 │
│                                              │
│  Summary paragraph                           │
│                                              │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐     │
│  │ icon     │ │ icon     │ │ icon     │     │
│  │ TITLE    │ │ TITLE    │ │ TITLE    │     │
│  │ text     │ │ text     │ │ text     │     │
│  └──────────┘ └──────────┘ └──────────┘     │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐     │
│  │ icon     │ │ icon     │ │ icon     │     │
│  │ TITLE    │ │ TITLE    │ │ TITLE    │     │
│  │ text     │ │ text     │ │ text     │     │
│  └──────────┘ └──────────┘ └──────────┘     │
│                                              │
│  ┌─ CTA Banner ───────────────────────────┐  │
│  │  → Call to action / next steps          │  │
│  └─────────────────────────────────────────┘  │
└──────────────────────────────────────────────┘
```

**Used in:** Summary/Conclusion slide  
**Grid:** `grid-template-columns: repeat(3, 1fr); gap: 20px;`  
**Mobile:** Single column at `800px`  
**Cards have:** icon (emoji), uppercase title, description text  
**CTA Banner:** green-tinted border + background, arrow icon + bold text

---

## 7. Quote Slide (Embedded)

Not a standalone layout, but a component within two-column. Large italic quote with green left border.

```
│  "Quote text goes here,                      │
│   large condensed italic."                   │
│  ┃ (4px green left border)                   │
```

**CSS:**
```css
.thesis-quote {
  font-family: 'Barlow Condensed', sans-serif;
  font-size: clamp(26px, 4vw, 48px);
  font-weight: 700;
  line-height: 1.2;
  border-left: 4px solid var(--bi-green);
  padding-left: 28px;
  font-style: italic;
}
```

---

## 8. Section Divider (Available Pattern)

Full-slide divider with large background number. Used for separating major sections.

```
┌──────────────────────────────────────────────┐
│  ── Tag Label                                │
│                                              │
│  SECTION TITLE                               │
│                                              │
│                                     02       │
│                               (giant faded)  │
└──────────────────────────────────────────────┘
```

**Background:** `var(--bg2)` (#111111) — slightly lighter than standard  
**Number:** `clamp(80px, 14vw, 200px)`, color `rgba(255,255,255,0.04)`
