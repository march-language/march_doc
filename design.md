# March Design System

A portable design system for March language projects. Near-black dark theme with teal and blue brand accents.

---

## Color Palette

### Dark Theme (default)

| Token | Hex | Usage |
|-------|-----|-------|
| `--bg` | `#09090b` | Page background |
| `--sb` | `#0f0f12` | Sidebar, top bar, modal backgrounds |
| `--card` | `#141418` | Cards, surfaces, elevated elements |
| `--bdr` | `#23252b` | Borders, dividers, separators |
| `--code` | `#0c0c0f` | Code block backgrounds |
| `--text` | `#d4d4d8` | Primary body text |
| `--dim` | `#71717a` | Secondary text, labels, captions |
| `--bright` | `#fafafa` | Headings, emphasis, high-contrast text |
| `--acc` | `#6FE3D6` | **Primary accent** (teal) -- links, active states, interactive elements |
| `--acc2` | `#3ABFF8` | **Secondary accent** (blue) -- hover states, type cross-links, alternate highlights |
| `--fn` | `#36D399` | Function badge, success states (green) |
| `--ty` | `#FBBF24` | Type badge, warning states (amber) |
| `--if` | `#3ABFF8` | Interface badge, info states (blue) |
| `--prv` | `#3f3f46` | Private/muted badge, disabled states (zinc) |

### Light Theme

| Token | Hex | Usage |
|-------|-----|-------|
| `--bg` | `#ffffff` | Page background |
| `--sb` | `#f4f9fb` | Sidebar background |
| `--card` | `#ffffff` | Cards, surfaces |
| `--bdr` | `#d0e3eb` | Borders |
| `--code` | `#0F2A36` | Code blocks (stays dark) |
| `--text` | `#0B1F2A` | Primary text |
| `--dim` | `#4a6d7a` | Secondary text |
| `--bright` | `#0B1F2A` | Headings |
| `--acc` | `#0d9e8f` | Primary accent (darker teal for contrast on white) |
| `--acc2` | `#0284c7` | Secondary accent (darker blue) |
| `--fn` | `#047857` | Function/success (darker green) |
| `--ty` | `#b45309` | Type/warning (darker amber) |
| `--if` | `#0284c7` | Interface/info (darker blue) |
| `--prv` | `#8b9da7` | Private/muted |

### Semantic Badges

Colored pill badges identify item types. Use rgba backgrounds so they adapt to any surface:

| Badge | Background | Text Color | Usage |
|-------|-----------|------------|-------|
| fn | `rgba(54,211,153,.12)` | `--fn` | Public functions |
| pfn | `rgba(61,96,112,.2)` | `--prv` | Private functions |
| type | `rgba(251,191,36,.1)` | `--ty` | Public types |
| ptype | `rgba(61,96,112,.15)` | `--prv` | Private types |
| interface | `rgba(58,191,248,.1)` | `--if` | Interfaces |
| module | `rgba(111,227,214,.1)` | `--acc` | Modules |

---

## Typography

### Font Stack

```css
/* Body text */
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Inter', sans-serif;

/* Code and signatures */
font-family: 'JetBrains Mono', 'Fira Code', 'SF Mono', monospace;
```

### Scale

| Element | Size | Weight | Color | Extra |
|---------|------|--------|-------|-------|
| Page title (h1) | 1.6rem | 700 | `--bright` | -- |
| Section heading (h2) | .85rem | 600 | `--bright` | Uppercase, letter-spacing .04em, bottom border |
| Body text | 15px | 400 | `--text` | Line-height 1.6 |
| Secondary text | 13-14px | 400 | `--dim` | -- |
| Code (inline) | 12px | 400 | `--acc` | Background `--code`, 2px 6px padding, 4px radius |
| Code (block) | 13px | 400 | `--text` | Background `--code`, 14px 18px padding, 6px radius |
| Badge labels | 9px | 700 | varies | Uppercase, letter-spacing .08em |
| Breadcrumb | 12px | 400 | `--dim` | -- |
| Sidebar links | 13px | 400/500 | `--dim`/`--acc` | 500 weight when active |
| Sidebar heading | 10px | 700 | `--dim` | Uppercase, letter-spacing .08em |

---

## Spacing

| Context | Value |
|---------|-------|
| Top bar height | 48px |
| Sidebar width | 240px |
| Main content padding | 36px vertical, 48px horizontal |
| Card padding | 16-24px |
| Border radius (small) | 4-5px |
| Border radius (medium) | 6-8px |
| Border radius (large) | 12px (modals) |
| Item gap (between cards) | 12px |
| Section margin (h2) | 32px top, 12px bottom |

---

## Components

### Top Bar
- Sticky, 48px tall, `--sb` background, bottom border
- Left: brand logo + name (14px, 700 weight, `--bright`)
- Right: search trigger button + theme toggle button
- Search trigger: `--card` background, `--bdr` border, kbd shortcut label

### Sidebar
- 240px wide, sticky below top bar, independent scroll
- Section headings: 10px uppercase labels
- Links: 13px, `--dim` default, `--acc` on hover/active
- Collapsible groups: chevron (&#9656;) rotates 90deg when open
- Sub-items: 12px, indented 16px, with colored kind indicators (T/I/F)

### Cards
- `--card` background, 1px `--bdr` border, 8px radius
- Hover: border shifts toward accent (`color-mix(in srgb, var(--acc) 40%, var(--bdr))`)
- Module cards (index): lift on hover (`translateY(-1px)`)

### Item Rows (fn/type/interface)
- Header row (`.ih`): badge + name + signature + source link + anchor link
- Clickable to expand/collapse body
- Hover: background tints toward accent (`color-mix(in srgb, var(--card) 80%, var(--acc) 20%)`)
- Source link and anchor link: hidden by default, appear on hover (opacity transition)

### Search Modal
- Fixed overlay with 60% black backdrop
- Modal: `--sb` background, 12px radius, 560px wide, heavy box-shadow
- Input: transparent background, bottom border, 15px font
- Results: badge + name + module, with doc snippet below

### Admonitions
- Left border accent (3px), `--card` background, 6px radius on right
- Note: `--acc2` (blue) border
- Warning: `--ty` (amber) border

### Code Blocks
- Always dark background (`--code`), even in light theme
- Copy button: absolute positioned top-right, appears on hover
- "Copied!" feedback with `--fn` color

---

## Transitions

All interactive transitions use 100-150ms:

```css
transition: all .15s;      /* buttons, borders */
transition: all .1s;       /* sidebar links, item headers */
transition: opacity .15s;  /* reveal elements (source links, anchors) */
transition: transform .15s; /* chevron rotation */
```

---

## Responsive Breakpoints

| Breakpoint | Behavior |
|------------|----------|
| > 768px | Full layout: sidebar + main content |
| <= 768px | Sidebar hidden, main content fills width, reduced padding (24px 16px) |

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
/* Dark theme */
:root {
  --bg: #09090b;
  --sb: #0f0f12;
  --card: #141418;
  --bdr: #23252b;
  --code: #0c0c0f;
  --text: #d4d4d8;
  --dim: #71717a;
  --bright: #fafafa;
  --acc: #6FE3D6;
  --acc2: #3ABFF8;
  --fn: #36D399;
  --ty: #FBBF24;
  --if: #3ABFF8;
  --prv: #3f3f46;
}

/* Light theme */
[data-theme="light"] {
  --bg: #ffffff;
  --sb: #f4f9fb;
  --card: #ffffff;
  --bdr: #d0e3eb;
  --code: #0F2A36;
  --text: #0B1F2A;
  --dim: #4a6d7a;
  --bright: #0B1F2A;
  --acc: #0d9e8f;
  --acc2: #0284c7;
  --fn: #047857;
  --ty: #b45309;
  --if: #0284c7;
  --prv: #8b9da7;
}
```
