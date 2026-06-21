# March Design System

A portable design system for March language projects, aligned with the
[march-lang.org](https://march-lang.org) homepage. Deep-navy dark theme with a
cyan (oklch) accent, **Lora** serif headings, and **JetBrains Mono** for code
and labels.

---

## Color Palette

Colors are defined as CSS custom properties on `:root` (dark, default) with a
`[data-theme="light"]` override. The accent and badge hues use `oklch()` so they
stay perceptually consistent across both themes.

### Dark Theme (default)

| Token | Value | Usage |
|-------|-------|-------|
| `--bg` | `#07101a` | Page background (deep navy) |
| `--sb` | `#0a1622` | Sidebar, search modal background |
| `--bg-nav` | `rgba(7,16,26,0.92)` | Top bar (translucent, blurred) |
| `--card` | `#0c1928` | Cards, surfaces, code-block background |
| `--bdr` | `#0f2438` | Borders, dividers, separators |
| `--code` | `#0c1928` | Code block background |
| `--text` | `#cce5f5` | Primary body text (blue-tinted) |
| `--dim` | `#4a7898` | Secondary text, labels, captions |
| `--faint` | `#1e4060` | Faint text, chevrons, section labels |
| `--bright` | `#eaf4fb` | Headings, emphasis, high-contrast text |
| `--acc` | `oklch(63% 0.12 207)` | **Primary accent** (cyan) — links, active states, labels |
| `--acc2` | `oklch(74% 0.11 200)` | **Secondary accent** (lighter cyan) — hover, type cross-links |
| `--fn` | `oklch(74% 0.13 165)` | Function badge (green) |
| `--ty` | `oklch(82% 0.12 70)` | Type badge (amber/gold) |
| `--if` | `oklch(78% 0.11 235)` | Interface badge (blue) |
| `--prv` | `#3a5f7d` | Private/muted badge (steel) |

### Light Theme

| Token | Value | Usage |
|-------|-------|-------|
| `--bg` | `#f0f6fc` | Page background (blue-white) |
| `--sb` | `#e3eef8` | Sidebar background |
| `--bg-nav` | `rgba(240,246,252,0.92)` | Top bar |
| `--card` | `#ddeaf5` | Cards, surfaces, code blocks |
| `--bdr` | `#b5cce0` | Borders |
| `--code` | `#ddeaf5` | Code blocks (light in light mode, like the homepage) |
| `--text` | `#071828` | Primary text |
| `--dim` | `#2e5c7c` | Secondary text |
| `--faint` | `#6a96b5` | Faint text, section labels |
| `--bright` | `#071828` | Headings |
| `--acc` | `oklch(37% 0.11 210)` | Primary accent (darker cyan for contrast) |
| `--acc2` | `oklch(45% 0.11 215)` | Secondary accent |
| `--fn` | `oklch(45% 0.13 165)` | Function/success (darker green) |
| `--ty` | `oklch(52% 0.12 70)` | Type/warning (darker amber) |
| `--if` | `oklch(45% 0.11 235)` | Interface/info (darker blue) |
| `--prv` | `#6a96b5` | Private/muted |

### Semantic Badges

Pill badges identify item kinds. Backgrounds and borders are derived from the
badge hue with `color-mix`, so they adapt to any surface and to both themes:

| Badge | Background | Border | Text | Usage |
|-------|-----------|--------|------|-------|
| fn | `color-mix(in oklab, var(--fn) 13%, transparent)` | 24% | `--fn` | Public functions |
| pfn | `color-mix(in oklab, var(--prv) 18%, transparent)` | 30% | `--prv` | Private functions |
| type | `color-mix(in oklab, var(--ty) 12%, transparent)` | 24% | `--ty` | Public types |
| ptype | `color-mix(in oklab, var(--prv) 15%, transparent)` | 26% | `--prv` | Private types |
| interface | `color-mix(in oklab, var(--if) 12%, transparent)` | 24% | `--if` | Interfaces |
| module | `color-mix(in oklab, var(--acc) 13%, transparent)` | — | `--acc` | Modules (search) |

Badges are `border-radius: 100px` (pill), `JetBrains Mono`, 9px, uppercase.

---

## Typography

### Font Stack

Loaded from Google Fonts (`Lora` + `JetBrains Mono`) with system fallbacks:

```css
/* Body text */
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Inter', sans-serif;

/* Headings, brand */
font-family: 'Lora', Georgia, serif;

/* Code, signatures, labels, badges */
font-family: 'JetBrains Mono', 'Fira Code', 'SF Mono', monospace;
```

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Lora:ital,wght@0,500;0,600;1,400;1,600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
```

### Scale

| Element | Font | Size | Weight | Color | Extra |
|---------|------|------|--------|-------|-------|
| Page title (h1) | Lora serif | 2.1rem | 600 | `--bright` | letter-spacing -.02em |
| Section heading (h2) | JetBrains Mono | .72rem | 500 | `--acc` | Uppercase, letter-spacing .12em, bottom border |
| Module card title (h3) | Lora serif | 1.05rem | 600 | `--acc` | — |
| Guide heading (h3/h4) | Lora serif | 1.4 / 1.1rem | 600 | `--bright` | — |
| Body text | sans | 15px | 400 | `--text` | Line-height 1.6 |
| Secondary text | sans | 13–14px | 400 | `--dim` | — |
| Code (inline) | mono | 12px | 400 | `--acc` | Background `--code`, 4px radius |
| Code (block) | mono | 13px | 400 | `--text` | Background `--code`, 6px radius |
| Badge labels | mono | 9px | 500 | varies | Uppercase, letter-spacing .08em, pill |
| Breadcrumb | sans | 12px | 400 | `--dim` | — |
| Sidebar link | sans | 13px | 400/500 | `--dim`/`--acc` | 500 + accent bar when active |
| Sidebar section label | JetBrains Mono | 10px | 500 | `--faint` | Uppercase, letter-spacing .16em |

Headings use **Lora serif** to match the homepage; section headings and all
code/labels use **JetBrains Mono**.

---

## Spacing

| Context | Value |
|---------|-------|
| Top bar height | 60px |
| Sidebar width | 248px |
| Main content padding | 40px vertical, 52px horizontal (max-width 900px) |
| Card padding | 16–24px |
| Border radius (small) | 4–6px |
| Border radius (medium) | 6–8px |
| Border radius (pill) | 100px (badges, chips) |
| Border radius (large) | 12px (modals) |
| Item gap (between cards) | 12px |
| Section margin (h2) | 38px top, 14px bottom |

---

## Components

### Top Bar
- Sticky, **60px** tall, translucent `--bg-nav` with `backdrop-filter: blur(14px)`, bottom border
- Left: brand logo + name in **Lora serif** (18px, 600, `--text`)
- Right: search trigger button + theme toggle (mono)
- Search trigger: `--card` background, `--bdr` border, `⌘K` kbd shortcut

### Sidebar
- 248px wide, sticky below the top bar, independent scroll
- Section label: 10px **mono** uppercase, `--faint`, letter-spacing .16em
- Links: 13px, `--dim` default, `--text` on hover (accent-tinted background)
- **Active item:** `--acc` text + inset 2px accent left-bar + faint accent background
  (full-row for module groups via `:has(.sl.active)`)
- Collapsible groups: chevron (`▸`) rotates 90° and turns accent when open
- Sub-items: 12px, indented under a 1px `--bdr` **guide rail**, with mono kind markers (T/I/F)

### Cards
- `--card` background, 1px `--bdr` border, 8px radius
- Hover: border shifts toward accent (`color-mix(in srgb, var(--acc) 40%, var(--bdr))`)
- Module cards (index): lift on hover (`translateY(-1px)`)

### Item Rows (fn/type/interface)
- Header row (`.ih`): pill badge + name + signature + source link + anchor link
- Clickable to expand/collapse body
- Hover: background tints toward accent
- Source/anchor links: hidden by default, appear on hover

### Search Modal
- Fixed overlay with 60% black backdrop
- Modal: `--sb` background, 12px radius, 560px wide, heavy box-shadow
- Input: transparent, bottom border, 15px
- Results: pill kind badge + name + module, with doc snippet below

### Admonitions
- Left border accent (3px), `--card` background, 6px radius on right
- Note: `--acc2` (cyan) border · Warning: `--ty` (amber) border

### Code Blocks
- Follow theme tokens (`--code`): dark in dark mode, light in light mode (like the homepage)
- Copy button: absolute top-right, appears on hover; "Copied!" feedback in `--fn`

---

## Transitions

Interactive transitions use 100–150ms:

```css
transition: all .15s;                     /* buttons, borders */
transition: color .12s, background .12s;  /* sidebar links, item headers */
transition: opacity .15s;                 /* reveal elements (source links, anchors) */
transition: transform .15s;               /* chevron rotation */
```

---

## Responsive Breakpoints

| Breakpoint | Behavior |
|------------|----------|
| > 768px | Full layout: sidebar + main content |
| ≤ 768px | Sidebar hidden, main fills width, reduced padding (24px 16px) |

---

## Theme Toggle

```js
// Read preference: localStorage > system > dark
function getTheme() {
  var t = localStorage.getItem('march-doc-theme');
  if (t) return t;
  return window.matchMedia('(prefers-color-scheme: light)').matches ? 'light' : 'dark';
}

// Apply: set data-theme attribute on <html>
document.documentElement.setAttribute('data-theme', theme);

// Persist on toggle
localStorage.setItem('march-doc-theme', theme);
```

Icons: moon (dark mode active), sun (light mode active).

---

## CSS Custom Properties (copy-paste)

```css
/* Dark theme (default) */
:root {
  --bg: #07101a;
  --sb: #0a1622;
  --bg-nav: rgba(7,16,26,0.92);
  --card: #0c1928;
  --bdr: #0f2438;
  --code: #0c1928;
  --text: #cce5f5;
  --dim: #4a7898;
  --faint: #1e4060;
  --bright: #eaf4fb;
  --acc: oklch(63% 0.12 207);
  --acc2: oklch(74% 0.11 200);
  --fn: oklch(74% 0.13 165);
  --ty: oklch(82% 0.12 70);
  --if: oklch(78% 0.11 235);
  --prv: #3a5f7d;
}

/* Light theme */
[data-theme="light"] {
  --bg: #f0f6fc;
  --sb: #e3eef8;
  --bg-nav: rgba(240,246,252,0.92);
  --card: #ddeaf5;
  --bdr: #b5cce0;
  --code: #ddeaf5;
  --text: #071828;
  --dim: #2e5c7c;
  --faint: #6a96b5;
  --bright: #071828;
  --acc: oklch(37% 0.11 210);
  --acc2: oklch(45% 0.11 215);
  --fn: oklch(45% 0.13 165);
  --ty: oklch(52% 0.12 70);
  --if: oklch(45% 0.11 235);
  --prv: #6a96b5;
}
```
