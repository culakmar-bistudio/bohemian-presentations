# Presentation Template — Slide Engine

How the slide deck system works: navigation, transitions, keyboard controls.

---

## HTML Structure

```html
<body>
  <!-- Fixed nav bar -->
  <nav id="nav-bar">
    <div class="nav-logo">...</div>
    <div class="nav-progress" id="nav-dots"></div>
    <span class="nav-label" id="nav-slide-label"></span>
    <span class="slide-counter" id="slide-counter"></span>
  </nav>

  <!-- Slide deck container -->
  <div id="deck">
    <div class="slide active" id="slide-0">
      <div class="slide-inner">
        <!-- slide content -->
      </div>
    </div>
    <div class="slide" id="slide-1">
      <div class="slide-inner">
        <!-- slide content -->
      </div>
    </div>
    <!-- ... more slides -->
  </div>

  <!-- Fixed controls -->
  <button class="arrow-btn" id="btn-prev" onclick="changeSlide(-1)">←</button>
  <button class="arrow-btn" id="btn-next" onclick="changeSlide(1)">→</button>
  <div class="key-hint">← → arrow keys to navigate · click dots to jump</div>
</body>
```

---

## Slide Configuration

Define slides in the JavaScript `SLIDES` array. Each entry needs a `label` for the nav:

```javascript
const SLIDES = [
  { label: 'Cover' },
  { label: 'The Problem' },
  { label: 'The Proposal' },
  // ... add more as needed
];
```

The engine auto-generates progress dots from this array.

---

## Adding a New Slide

1. Add a new `<div class="slide" id="slide-N">` inside `#deck`
2. Add a matching entry to the `SLIDES` array
3. The slide engine handles everything else (dots, counter, transitions)

```html
<div class="slide" id="slide-10">
  <div class="slide-inner">
    <div class="slide-tag">New Section</div>
    <h1 class="slide-title">Your Title<br>Goes <span class="hl">Here</span></h1>
    <p class="slide-body">Your content.</p>
  </div>
</div>
```

---

## Navigation Controls

| Input | Action |
|---|---|
| `→` / `↓` / `Space` / `PageDown` | Next slide |
| `←` / `↑` / `PageUp` | Previous slide |
| Click progress dot | Jump to specific slide |
| Click arrow buttons | Next / Previous |
| Touch swipe (mobile) | Next / Previous (50px threshold) |

---

## Transition System

Slides use CSS transitions on `opacity` and `transform`:

- **Inactive:** `opacity: 0; transform: translateY(30px); pointer-events: none;`
- **Active:** `opacity: 1; transform: translateY(0); pointer-events: all;`
- **Exiting:** `opacity: 0; transform: translateY(-30px);`
- **Duration:** `0.55s` with `cubic-bezier(0.4, 0, 0.2, 1)` easing
- Exit class is removed after `600ms` timeout

---

## Scrollable Slides

Slides with content taller than the viewport scroll independently:

```css
.slide {
  overflow-y: auto;
}
```

When navigating to a new slide, `scrollTop` is reset to `0`.

---

## Creating a New Presentation

1. Create a new folder in the project root (e.g., `my-topic/`)
2. Copy the slide engine boilerplate (see below) into `my-topic/index.html`
3. Add your slides and update the `SLIDES` array
4. Serve with any static HTTP server

### Minimal Boilerplate

The essential structure for a new presentation:

```
my-presentation/
└── index.html    ← self-contained, all CSS/JS inline
```

Each presentation is a single HTML file with embedded CSS and JS. No build tools, no dependencies, no frameworks. Just open in a browser.
