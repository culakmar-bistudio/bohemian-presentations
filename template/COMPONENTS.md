# Presentation Template — Components

Reusable UI components available for building slides.

---

## Navigation Bar

Fixed top bar with logo, progress dots, slide label, and counter.

```css
height: 52px;
background: rgba(10,10,10,0.92);
backdrop-filter: blur(12px);
border-bottom: 1px solid var(--border);
z-index: 100;
```

**Elements:**
- **Logo area:** SVG icon + company name, `Barlow Condensed 13px 700`, uppercase
- **Progress dots:** One per slide, `6px` circles, active = green + `scale(1.4)`
- **Slide label:** Current slide name, `11px 500`, uppercase
- **Slide counter:** `"3 / 10"` format, `Barlow Condensed 13px 600`

---

## Slide Tag

Green-accented section label at the top of each slide content area.

```css
font-family: 'Barlow Condensed', sans-serif;
font-size: 11px;
font-weight: 700;
letter-spacing: 0.18em;
text-transform: uppercase;
color: var(--bi-green);
```

Includes a `32px` green line before the text via `::before` pseudo-element.

---

## Stat Card

Numeric highlight card for key metrics.

```
┌─────────────────┐
│  40px number     │  ← Barlow Condensed 900, green
│  LABEL TEXT      │  ← 12px uppercase, dimmed
└─────────────────┘
```

```css
background: var(--bg3);
border: 1px solid var(--border);
padding: 20px 24px;
flex: 1;
min-width: 150px;
```

---

## Type Card (Numbered)

Card with number prefix, title, badge, and description. Used in grids.

```
┌─────────────────────────┐
│  01              badge   │
│  CARD                    │
│  TITLE                   │
│  Description text here   │
└─────────────────────────┘
```

**Properties:**
- Number: `Barlow Condensed 11px 700`, green, `letter-spacing: 0.15em`
- Title: `Barlow Condensed 20px 800`, uppercase, white
- Badge: emoji, `18px`, `opacity: 0.5`, positioned top-right
- Description: `12px`, dimmed, `line-height: 1.5`
- Hover: border goes green, card lifts `3px`

---

## Property Badge

Small tag showing a yes/no property.

```css
font-size: 11px;
font-weight: 600;
letter-spacing: 0.08em;
text-transform: uppercase;
padding: 4px 10px;
border: 1px solid;
```

Variants:
- `.yes` — green border, green text, green tinted background
- `.no` — red border, red text, red tinted background

---

## Domain Pill

Small pill for showing URLs/domains in lists.

```css
font-family: 'Barlow Condensed', sans-serif;
font-size: 12px;
font-weight: 600;
letter-spacing: 0.04em;
padding: 5px 10px;
border: 1px solid;
white-space: nowrap;
```

Variants:
- `.old` — red tinted (deprecated/current)
- `.new` — green tinted (proposed/future)
- `.dim` — neutral gray (supplementary)

---

## Comparison Table

Data table for side-by-side comparisons.

```css
border-collapse: collapse;
font-size: 13px;
```

- **Headers:** `Barlow Condensed 12px 700`, uppercase, dimmed, bottom border
- **Cells:** `padding: 12px 16px`, subtle bottom border
- **Type column:** white, `font-weight: 600`
- **Symbols:** `.check` (green checkmark), `.cross` (red), `.maybe` (yellow)

---

## Conclusion Card

Summary card with icon, title, and description.

```
┌─────────────────────┐
│  icon (28px emoji)   │
│  UPPERCASE TITLE     │
│  Description text    │
│  in dimmed color     │
└─────────────────────┘
```

```css
background: var(--bg3);
border: 1px solid var(--border);
padding: 24px;
```

- Icon: `28px` emoji, `margin-bottom: 14px`
- Title: `Barlow Condensed 18px 800`, uppercase, white
- Text: `13px`, dimmed, `line-height: 1.55`

---

## CTA Banner

Full-width call-to-action strip at the bottom of a slide.

```css
padding: 20px 28px;
border: 1px solid rgba(107,165,57,0.3);
background: rgba(107,165,57,0.05);
display: flex;
align-items: center;
gap: 20px;
```

- Arrow icon: `28px`, flex-shrink
- Text: `15px`, `line-height: 1.55`, with bold lead-in

---

## Highlight Panel (Accent Border)

Information panel with colored left border.

```css
background: var(--bg3);
border: 1px solid var(--border);
border-left: 3px solid var(--bi-green);  /* or any accent color */
padding: 20px 24px;
```

- Header: `Barlow Condensed 14px 800`, uppercase, accent colored
- Body: `13px`, dimmed, with inline `<code>` elements

---

## Flow Diagram (Horizontal)

Chain of connected nodes showing a process flow.

```
[Node 1] → [Node 2] → [Hub Node] → [Node 3]
```

- Nodes: `var(--bg3)` background, `min-width: 140px`, `padding: 16px 20px`
- Hub node: green border + green tinted background
- Arrow: `20px` character, `rgba(255,255,255,0.2)`
- Label: `Barlow Condensed 13px 800`, uppercase
- Sub-label: `10px`, dimmed

---

## Nav Anatomy Diagram

Mock navigation bar showing shared vs. brand-specific elements.

Composed of:
- `.nav-anatomy` container with dark background
- `.nav-anatomy-bar` rows showing different brand variants
- Hub section (shared) + brand-specific section
- Annotation row explaining what changes vs. stays the same

---

## Arrow Controls

Fixed bottom-right navigation buttons.

```css
position: fixed;
bottom: 32px;
width: 44px; height: 44px;
border-radius: 50%;
border: 1px solid var(--border);
color: rgba(255,255,255,0.5);
```

- Hover: green border, green text, green tinted background
- Previous: `right: 100px`
- Next: `right: 44px`

---

## Keyboard Hint

Fixed bottom-center helper text.

```css
position: fixed;
bottom: 32px;
left: 50%;
transform: translateX(-50%);
font-size: 11px;
color: rgba(255,255,255,0.2);
pointer-events: none;
```
