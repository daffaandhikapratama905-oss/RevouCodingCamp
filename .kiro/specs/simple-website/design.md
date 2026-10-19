# Design Specification

## Overview

**Project:** Revou Landing Page — single-page static website
**Purpose:** Convert prospective students by clearly communicating what Revou offers, why it works, and how to get started
**User:** Adults 18–35 in Indonesia considering a career change into tech, browsing on both mobile and desktop
**Stack:** HTML5 + Tailwind CSS CDN + Vanilla JS — no build tools, no framework

The design serves one goal: build trust quickly. The user is making a significant life decision (career change). They need clarity and credibility, not excitement. Every visual choice reinforces that.

---

## Design Philosophy

### Trust is earned through restraint

Overcrowded, gradient-heavy, animation-rich pages signal "marketing template." This page needs to feel like it was designed for Revou specifically — not generated. That means fewer elements, stronger hierarchy, and deliberate whitespace.

### Typography carries the weight

If the layout feels empty without decorative elements, the typography is not doing its job. Inter at the right sizes and weights should establish hierarchy so clearly that icons, shadows, and colors are enhancements — not load-bearing walls.

### Section contrast through background, not decoration

Each section feels distinct because of background color changes (`gray-50` ↔ `white` ↔ `gray-900`), not because of card borders, shadows, or dividers everywhere. This creates natural breathing room without visual noise.

### One accent, used with discipline

A single accent color — deep indigo — appears only on interactive elements: buttons, active states, and meaningful labels. Every time the user sees indigo, it means something is actionable. This gives the accent meaning.

### Features are a list, not a card collection

Not everything needs to be a card. Six feature items shown as a clean two-column list with icon + text is more readable and less visually exhausting than six shadow-boxed cards. Cards are reserved for content-dense components (courses) where the boundary genuinely aids comprehension.

---

## Visual Direction

**Style:** Editorial-meets-product. Clean like technical documentation, but warm enough to be approachable.

**Mood:** Confident, grounded, direct. Professional without being cold. Not a startup, not an enterprise — an institution that delivers outcomes.

**What the user should feel:** "This place knows what it's doing. I can trust this."

**Feel references (not visual copy):**
- Linear.app — typographic confidence, minimal decoration
- Stripe — information clarity, purposeful spacing
- Vercel — whitespace as a design decision, not a default

### What to avoid and why

| Avoid | Why |
|---|---|
| Blue-to-purple gradient background | Has no brand identity. Signals AI template immediately. |
| Glassmorphism | Visual trick with no functional value. Reduces text legibility. |
| Rounded corners on everything (`rounded-2xl`, `rounded-3xl`) | Makes an educational institution look like a consumer app. |
| Floating cards over hero background | Decorative without being informative. Cheap visual depth. |
| Icon grids as the primary feature layout | Reduces features to icons, not substance. |
| All sections using the same visual pattern | No rhythm. No reason to keep scrolling. |
| More than 3 unique colors | Dilutes hierarchy. Every color competes for attention. |
| Scroll reveal / entrance animations | Delays the user from reading. Adds no value. |

---

## Color System

Palette is three-color: one accent (indigo), one neutral scale (gray), one dark (near-black). No fourth color.

| Token | Hex | Tailwind Class | Role |
|---|---|---|---|
| Accent | `#3730a3` | `indigo-700` | Primary buttons, active link states |
| Accent Hover | `#312e81` | `indigo-800` | Button hover state |
| Accent Subtle | `#e0e7ff` | `indigo-100` | Pre-heading label background |
| Accent Text | `#4338ca` | `indigo-600` | Small labels on light background |
| Background | `#f9fafb` | `gray-50` | Page background, Courses section |
| Surface | `#ffffff` | `white` | Navbar, Features section, Course cards |
| Dark | `#111827` | `gray-900` | CTA Banner, Footer |
| Text Primary | `#111827` | `text-gray-900` | All headings, primary body text |
| Text Secondary | `#4b5563` | `text-gray-600` | Descriptive paragraphs |
| Text Muted | `#9ca3af` | `text-gray-400` | Meta text, footer links |
| Text Inverse | `#f9fafb` | `text-gray-50` | Headings on dark sections |
| Text Inverse Secondary | `#9ca3af` | `text-gray-400` | Body text on dark sections |
| Border | `#e5e7eb` | `border-gray-200` | Card borders, separators |
| Border Dark | `#374151` | `border-gray-700` | Borders inside dark sections |

**Usage rules:**
- Indigo only appears on interactive elements and meaningful labels
- `gray-900` background only for CTA Banner and Footer — nowhere else
- No color is used purely decoratively

---

## Typography

**Font family:** Inter — loaded via Google Fonts (weights 400, 500, 600, 700, 800)

Tailwind config extension:
```
fontFamily: { sans: ['Inter', 'ui-sans-serif', 'system-ui'] }
```

### Type Scale

| Level | Desktop Size | Mobile Size | Weight | Line Height | Tracking | Tailwind Classes |
|---|---|---|---|---|---|---|
| H1 Display | 48px | 36px | 800 | 1.1 | −0.02em | `text-4xl lg:text-5xl font-extrabold leading-tight tracking-tight` |
| H2 Section | 30px | 24px | 700 | 1.2 | −0.01em | `text-2xl lg:text-3xl font-bold leading-snug tracking-tight` |
| H3 Component | 16px | 16px | 600 | 1.4 | 0 | `text-base font-semibold` |
| Body | 16px | 15px | 400 | 1.625 | 0 | `text-base leading-relaxed text-gray-600` |
| Small / Meta | 14px | 14px | 400 | 1.5 | 0 | `text-sm text-gray-400` |
| Label | 12px | 12px | 600 | 1 | +0.08em | `text-xs font-semibold uppercase tracking-widest` |
| Stat Number | 30px | 28px | 700 | 1 | −0.01em | `text-3xl font-bold text-gray-900 tabular-nums` |
| Nav Link | 14px | 14px | 500 | 1 | 0 | `text-sm font-medium` |
| Button | 14px | 14px | 600 | 1 | 0 | `text-sm font-semibold` |

### Typography principles
- H1 is the loudest element on the page — it should dominate without help from color or decoration
- Section H2s are clearly subordinate but still commanding
- Body text uses `text-gray-600` not `text-gray-500` — more readable at paragraph length
- Labels and badges use uppercase + wide tracking to visually separate from running text

---

## Layout System

### Container
```
max-width: 1280px   → max-w-7xl
padding:   px-4 (mobile) → px-6 (sm) → px-8 (lg)
center:    mx-auto
```

### Grid per Section

| Section | Grid | Gap |
|---|---|---|
| Navbar | `flex items-center justify-between` | — |
| Hero | `grid grid-cols-1 lg:grid-cols-2` | `gap-12 lg:gap-16` |
| Features | `grid grid-cols-1 sm:grid-cols-2` (no lg:grid-cols-3, see note) | `gap-x-16 gap-y-0` |
| Courses | `grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3` | `gap-6` |
| CTA Banner | `flex flex-col items-center text-center` | `gap-6` |
| Footer | `grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4` | `gap-8` |

> **Features grid note:** Feature items are a 2-column list (not 3), because the list layout with separator lines needs wider columns to be readable. On mobile it collapses to 1 column.

### Section Spacing — Intentionally Varied

Monotone spacing makes the page feel like a template. Each section has a deliberate rhythm.

| Section | Padding | Reasoning |
|---|---|---|
| Navbar | `h-16` (fixed height) | Compact. It's utility, not a statement. |
| Hero | `pt-32 pb-20 lg:pt-40 lg:pb-28` | Large top padding absorbs navbar height. Generous bottom lets H1 breathe. |
| Features | `py-16 lg:py-20` | Standard. Medium density — list format is already airy. |
| Courses | `py-16 lg:py-24` | Slightly more — cards are denser, need more surrounding space. |
| CTA Banner | `py-20 lg:py-28` | Dark section. More space makes the text feel monumental, not cramped. |
| Footer | `pt-12 pb-8` | Compact end-of-page treatment. |

---

## Page Structure

Reading flow: top-to-bottom, left-to-right (desktop), single column (mobile).

```
[Navbar]          fixed, always present
  ↓
[Hero]            What Revou is + why now + stats. First decision point.
  ↓
[Features]        Why Revou specifically. Addresses objections.
  ↓
[Courses]         What's available. Addresses "is there something for me?"
  ↓
[CTA Banner]      The ask. After the user has enough context.
  ↓
[Footer]          Navigation fallback + legal. No decision pressure.
```

**Section backgrounds:**

| Section | Background | Purpose |
|---|---|---|
| Navbar | `bg-white/95` (blur) | Transparent feel, separates on scroll |
| Hero | `bg-gray-50` | Warm off-white. Distinct from pure white sections below. |
| Features | `bg-white` | Clean contrast from hero |
| Courses | `bg-gray-50` | Alternates back — creates rhythm without adding color |
| CTA Banner | `bg-gray-900` | Maximum contrast. This is the ask. |
| Footer | `bg-gray-900` | Continuous with CTA Banner — bottom of page has weight |

---

## Architecture

Website is a single HTML file. No routing, no components framework, no build step.

```
index.html
├── <head>
│   ├── Google Fonts (Inter, preconnect)
│   ├── tailwind.config inline script
│   └── Tailwind CSS CDN script
└── <body>
    ├── <header>  → Navbar (fixed, z-50)
    ├── <main>
    │   ├── <section id="about">    → Hero
    │   ├── <section id="features"> → Features
    │   ├── <section id="courses">  → Courses
    │   └── <section id="contact">  → CTA Banner
    └── <footer>  → Footer

script.js (deferred)
├── Hamburger toggle + icon swap + aria-expanded
├── Mobile menu auto-close on link click
├── Smooth scroll with navbar offset
└── Scroll-based navbar shadow (passive listener)
```

**Navigation flow:** All links are `<a href="#section-id">`. Clicks are intercepted by `script.js`, which calculates the correct scroll offset accounting for the fixed navbar height (64px) plus 8px breathing room.

**Scroll shadow threshold:** `window.scrollY > 10` triggers class `scrolled` on `<header>`, which switches `border-transparent` to `border-gray-200` and adds `shadow-sm`.

---

## Components and Interfaces

### Navbar

**Purpose:** Persistent wayfinding. Stays out of the way visually until the user needs it.

**Structure:**
```
header (fixed, z-50)
└── nav (max-w-7xl container)
    └── div (flex, h-16)
        ├── Logo (a)
        ├── Nav links (ul, hidden on mobile)
        ├── Auth buttons (div, hidden on mobile)
        └── Hamburger button (button, hidden on desktop)
    └── Mobile menu (div, hidden by default)
```

**Visual treatment:**
- Default: `bg-white/95 backdrop-blur-sm border-b border-transparent`
- Scrolled state (JS adds class `scrolled`): `border-gray-200 shadow-sm`
- Transition: `transition-all duration-200`
- Logo badge: `w-7 h-7 bg-indigo-700 text-white text-xs font-bold rounded flex items-center justify-center`
- Logo text: `text-base font-semibold text-gray-900`

**Nav links:**
- Default: `text-sm font-medium text-gray-600`
- Hover: `hover:text-gray-900 transition-colors duration-150`
- No underline decoration — color change is sufficient

**Mobile menu:**
- Background: `bg-white border-t border-gray-200`
- Links: full-width, `px-4 py-3 text-sm font-medium text-gray-700 hover:bg-gray-50`
- Separator before buttons: `border-t border-gray-100 mt-2 pt-3`

---

### Primary Button

**Used for:** Get Started (navbar), Explore Courses (hero), Apply Now (CTA Banner)

```
px-4 py-2        (navbar size)
px-6 py-3        (hero, CTA size)

base:  bg-indigo-700 text-white text-sm font-semibold rounded-lg
hover: bg-indigo-800
focus: outline-none ring-2 ring-indigo-700 ring-offset-2
transition: transition-colors duration-150
```

No shadows on buttons. Color change on hover is the signal — shadow would be redundant.

---

### Secondary Button

**Used for:** Log in (navbar), Learn More (hero), View All Courses, Talk to an Advisor

```
px-4 py-2        (navbar size)
px-6 py-3        (hero, CTA size)

base:  bg-white border border-gray-300 text-gray-700 text-sm font-semibold rounded-lg
hover: bg-gray-50 border-gray-400
focus: outline-none ring-2 ring-gray-400 ring-offset-2
transition: transition-all duration-150
```

**Variant on dark background (CTA Banner):**
```
bg-transparent border border-white/30 text-white
hover: bg-white/10 border-white/50
focus: ring-2 ring-white ring-offset-gray-900
```

---

### Feature Item

**Purpose:** Show six program advantages. List format, not card format.

This is the key anti-slop decision for Features. A list with a horizontal rule reads faster and doesn't fragment the section into 6 isolated boxes.

**Structure:**
```
div (flex gap-4, py-5 border-b border-gray-100, last:border-b-0)
├── div (icon container, w-9 h-9 flex-shrink-0, rounded-lg bg-gray-100)
│   └── svg (w-5 h-5 text-gray-700, aria-hidden="true")
└── div
    ├── h3 (text-base font-semibold text-gray-900)
    └── p  (text-sm leading-relaxed text-gray-600 mt-1)
```

**Visual treatment:**
- No card border. No shadow. No background fill.
- Separator: `border-b border-gray-100` between items, `last:border-b-0` on final item
- Icon container: `bg-gray-100` — neutral, not colored. Indigo is reserved for interactive elements.
- Hover: `hover:bg-gray-50 rounded-lg px-2 -mx-2 transition-colors duration-150` — very subtle

**Icon mapping (Heroicons outline 20px):**
- Structured Curriculum → `AcademicCapIcon`
- 1-on-1 Mentorship → `UserCircleIcon`
- Job Guarantee → `BriefcaseIcon`
- Learn by Doing → `WrenchScrewdriverIcon`
- Strong Community → `UsersIcon`
- Flexible Schedule → `CalendarDaysIcon`

---

### Course Card

**Purpose:** Present three programs with enough detail for evaluation. Content-dense — card format is justified here.

**Structure:**
```
article (bg-white border border-gray-200 rounded-xl overflow-hidden)
├── div (card header h-28, bg-[solid-color], px-5 flex items-end pb-4)
│   └── span (text-xs font-semibold uppercase tracking-widest text-white/70)
└── div (card body p-5)
    ├── h3 (text-base font-semibold text-gray-900)
    ├── p  (text-sm text-gray-500 leading-relaxed mt-1 mb-4)
    └── div (flex items-center gap-3 text-sm text-gray-400 border-t border-gray-100 pt-3)
        ├── span (duration)
        ├── span ("·" separator)
        └── span (format)
```

**Card header colors (solid, not gradient):**
- Full Stack Software Engineering: `bg-indigo-700`
- Data Analytics: `bg-teal-700`
- Product Management: `bg-violet-700`

These three are the exception to the 3-color rule — each course track needs distinct identity. All are muted/dark tones, never bright or neon.

**Hover state:**
```
hover:shadow-md hover:-translate-y-0.5 transition-all duration-200 ease-in-out
```
Default state has no shadow — hover effect is noticeable because the baseline is flat.

---

### Stats Item

**Used in:** Hero section, grouped below CTA buttons

```
div (flex flex-col)
├── span (text-3xl font-bold text-gray-900 leading-none tabular-nums)
└── span (text-sm text-gray-500 mt-1)
```

Three stats in a row: `flex items-center divide-x divide-gray-200`, each item `px-5 first:pl-0`.

---

### Hero Visual Placeholder

A code snippet block — communicates "tech" functionally without being a generic gradient box.

```
div (bg-gray-900 rounded-xl overflow-hidden shadow-lg)
├── div (header bar px-4 py-3 bg-gray-800 flex items-center gap-2)
│   ├── div (w-3 h-3 rounded-full bg-red-400/70)
│   ├── div (w-3 h-3 rounded-full bg-yellow-400/70)
│   └── div (w-3 h-3 rounded-full bg-green-400/70)
└── pre (p-5 text-sm font-mono leading-relaxed overflow-x-auto)
    └── [syntax spans: keywords indigo-400, strings emerald-400, numbers amber-400, default gray-300]
```

Purely presentational HTML — no JavaScript required.

---

### Section Label

Pre-heading label above H2. Used sparingly — not on every section.

```
span (inline-block text-xs font-semibold uppercase tracking-widest
      text-indigo-600 bg-indigo-50 px-3 py-1 rounded-md mb-3)
```

Only where a section needs framing context before the H2. Never decorative.

---

## Data Models

All content is static — hardcoded in HTML. No API, no database. Conceptual structure for reference during implementation:

### NavLink
```
{ label: string, href: string }
// Examples: { label: "About", href: "#about" }
```

### Stat
```
{ value: string, label: string }
// Hardcoded three: "10K+" Graduates | "93%" Job Placement | "500+" Hiring Partners
```

### FeatureItem
```
{ icon: HeroiconName, title: string, description: string }
// Six items: Structured Curriculum, 1-on-1 Mentorship, Job Guarantee,
//            Learn by Doing, Strong Community, Flexible Schedule
```

### CourseCard
```
{ headerColor: TailwindBgClass, category: string, title: string,
  description: string, duration: string, format: string }
// Three items:
// { headerColor: "bg-indigo-700", category: "Software Engineering",
//   title: "Full Stack Software Engineering", duration: "6 bulan", format: "Online" }
// { headerColor: "bg-teal-700", category: "Data",
//   title: "Data Analytics", duration: "3 bulan", format: "Online" }
// { headerColor: "bg-violet-700", category: "Product",
//   title: "Product Management", duration: "4 bulan", format: "Online" }
```

### FooterLinkGroup
```
{ heading: string, links: Array<{ label: string, href: string }> }
// "Company": About, Courses, Features, Contact
// "Legal": Privacy Policy, Terms of Service, Cookie Policy
```

---

## Correctness Properties

### Property 1: Navbar always visible

`∀ scrollY ≥ 0`: navbar remains at `position: fixed, top: 0, z-index: 50`.
No scroll position causes navbar to hide or reposition.
**Validates: Requirements 1.1, 1.6**

### Property 2: Mobile menu state consistency

At all times, the following four values must be in sync:
- `#mobile-menu` has `hidden` ↔ menu is closed
- `#icon-bars` has `hidden` ↔ menu is open
- `#icon-x` has `hidden` ↔ menu is closed
- `aria-expanded` on hamburger = `"true"` ↔ menu is open

**Validates: Requirements 2.1, 2.2, 2.6, 2.7**

### Property 3: Smooth scroll offset correctness

After scroll completes: `targetElement.getBoundingClientRect().top ≈ navbarHeight + 8`
Section heading is never obscured by the fixed navbar.
**Validates: Requirements 8.1, 8.2**

### Property 4: Scroll shadow threshold

- `scrollY > 10` → header has `shadow-sm` and `border-gray-200`
- `scrollY ≤ 10` → header has no shadow and `border-transparent`
Transition is smooth (CSS `transition-all duration-200`).
**Validates: Requirements 9.1, 9.2, 9.3**

### Property 5: No horizontal overflow

At 320px, 768px, 1280px viewport widths: `document.documentElement.scrollWidth === window.innerWidth`.
No element causes horizontal scroll.
**Validates: Requirements 10.1**

---

## Error Handling

### Anchor target not found

**Condition:** `a[href="#something"]` clicked, but `document.querySelector('#something')` returns `null`.
**Response:** Early `return` — no scroll, no error thrown. Silent fail is acceptable because all anchors are hardcoded in the same HTML file.

```js
const target = document.querySelector(link.getAttribute('href'))
if (!target) return
```

### Google Fonts unavailable

**Condition:** No internet connection or Google Fonts blocked.
**Response:** Browser falls back to `ui-sans-serif, system-ui`. Layout remains intact. Tailwind config defines the fallback stack: `['Inter', 'ui-sans-serif', 'system-ui', 'sans-serif']`.

### JavaScript disabled

**Condition:** User has JS blocked.
**Response:** Hamburger button non-functional (mobile menu inaccessible), smooth scroll reverts to native jump, navbar shadow never appears. All static content remains visible and readable. Known limitation — acceptable for this scope.

### Tailwind CDN unavailable

**Condition:** CDN unreachable.
**Response:** Page renders unstyled but content (text, links, structure) remains accessible via semantic HTML. No CSS fallback planned — acceptable for static landing page.

---

## Testing Strategy

All testing is manual — no test framework (constraint: no build tools, no external libraries).

### Manual checklist per requirement

1. **Req 1 — Navbar:** Fixed at top, logo visible, desktop links/buttons show at lg+
2. **Req 2 — Mobile toggle:** Open/close via hamburger, icon swap, aria-expanded update, auto-close on link click
3. **Req 3 — Hero:** Badge, H1, description, 2 CTAs, 3 stats, code snippet visual
4. **Req 4 — Features:** 6 items with icon+text, list separator visible, 2-col at sm+
5. **Req 5 — Courses:** 3 cards with header/badge/title/duration, hover lift, "View All" button
6. **Req 6 — CTA Banner:** Dark background, heading, 2 buttons
7. **Req 7 — Footer:** Logo, both link groups, copyright, 4-col at lg+
8. **Req 8 — Smooth scroll:** All anchors scroll smoothly, no heading hidden behind navbar
9. **Req 9 — Scroll shadow:** Shadow appears/disappears at 10px threshold
10. **Req 10 — Responsive:** No horizontal overflow at 320px, 768px, 1280px
11. **Req 11 — Accessibility:** Keyboard navigation, focus rings visible, contrast ratios
12. **Req 12 — Stack:** Open index.html directly in browser, no server needed, no console errors

### Boundary testing

- Resize viewport to 639px and 640px — verify sm breakpoint behavior
- Resize to 767px and 768px — verify md breakpoint
- Resize to 1023px and 1024px — verify lg breakpoint (navbar switch)
- Scroll to exactly 9px, 10px, 11px — verify shadow threshold

### Cross-browser

Chrome (latest), Firefox (latest), Safari (latest), Edge (latest). Mobile: Chrome Android, Safari iOS.

---

## Responsive Design

Mobile-first. Real layout changes at each breakpoint — not just narrowing.

### Mobile default (< 640px)

- Navbar: Logo + hamburger only. All links and auth buttons hidden.
- Hero: Single column, text centered, H1 `text-4xl`, visual placeholder stacks below text.
- Stats: Flex row, wraps naturally, centered.
- Features: Single column list.
- Courses: Single column.
- CTA Banner: Text centered, buttons `flex-col` (stacked).
- Footer: Single column, centered.
- Container: `px-4`

### sm — 640px+

- Courses grid: 2 columns
- CTA buttons: `sm:flex-row` (side by side)
- Container: `px-6`

### md — 768px+

- Features grid: 2 columns
- Footer grid: 2 columns

### lg — 1024px+

- Navbar: Full horizontal nav visible, hamburger hidden.
- Hero: 2-column layout — text left-aligned, code snippet right. H1 `text-5xl`.
- Courses grid: 3 columns
- Footer grid: 4 columns
- Container: `px-8`

---

## Interaction Design

Only interactions required by requirements. No decoration-only motion.

### Navbar scroll shadow
- **Trigger:** `scroll` event on `window` (passive)
- **Logic:** `scrollY > 10` → add class `scrolled`; `scrollY ≤ 10` → remove class `scrolled`
- **Effect:** `border-transparent → border-gray-200`, `shadow-none → shadow-sm`
- **Transition:** `transition-all duration-200` on `<header>`

### Hamburger toggle
- **Trigger:** Click `#menu-toggle`
- **Changes:** toggle `hidden` on `#mobile-menu`, swap `hidden` between `#icon-bars`/`#icon-x`, toggle `aria-expanded`
- **No animation** on menu appearance — `hidden` toggle is cleaner and more accessible than slide/fade

### Mobile menu auto-close
- **Trigger:** Click any `<a>` inside `#mobile-menu`
- **Change:** Identical to closing hamburger

### Smooth scroll
- **Trigger:** Click any `a[href^="#"]`
- **Behavior:** `window.scrollTo({ top: offset, behavior: 'smooth' })`
- **Offset:** `target.getBoundingClientRect().top + window.scrollY - navbar.offsetHeight - 8`

### Course card hover
- **Trigger:** CSS `:hover`
- **Change:** `shadow-none → shadow-md`, `translateY(0) → translateY(-2px)`
- **Classes:** `hover:shadow-md hover:-translate-y-0.5 transition-all duration-200 ease-in-out`
- **Scope:** Course cards only. Feature items use subtler `hover:bg-gray-50`.

### Button hover
- Primary: `bg-indigo-700 → bg-indigo-800`, `transition-colors duration-150`
- Secondary: `bg-white border-gray-300 → bg-gray-50 border-gray-400`, `transition-all duration-150`

### Link hover (nav + footer)
- `text-gray-600 → text-gray-900`, `transition-colors duration-150`

---

## Accessibility

### Semantic HTML structure

```
<body>
  <header>
    <nav aria-label="Main navigation">
  <main>
    <section id="about"    aria-labelledby="hero-heading">
    <section id="features" aria-labelledby="features-heading">
    <section id="courses"  aria-labelledby="courses-heading">
    <section id="contact"  aria-labelledby="cta-heading">
  <footer aria-label="Site footer">
```

### Color contrast ratios

| Pair | Ratio | WCAG Level |
|---|---|---|
| `gray-900` on `gray-50` | ~17.8:1 | AAA |
| `gray-600` on `white` | ~5.9:1 | AA |
| `white` on `indigo-700` | ~7.5:1 | AAA |
| `white` on `gray-900` | ~18.1:1 | AAA |
| `gray-400` on `gray-900` | ~4.8:1 | AA |
| `indigo-600` on `white` | ~5.9:1 | AA |

All primary text pairs exceed WCAG AA minimum (4.5:1).

### Focus states

No `outline: none` without a visible replacement.

Light background: `focus:outline-none focus:ring-2 focus:ring-indigo-700 focus:ring-offset-2`
Dark background: `focus:outline-none focus:ring-2 focus:ring-white focus:ring-offset-gray-900`

### ARIA attributes

| Element | Attribute |
|---|---|
| `<nav>` | `aria-label="Main navigation"` |
| Hamburger `<button>` | `aria-label="Toggle navigation menu"`, `aria-expanded`, `aria-controls="mobile-menu"` |
| `<div id="mobile-menu">` | `aria-label="Mobile navigation"` |
| All decorative SVGs | `aria-hidden="true"` |
| Each `<section>` | `aria-labelledby` pointing to its H2 `id` |

### Keyboard navigation

- Tab order follows DOM order
- Hamburger activates on Enter and Space
- Hidden mobile menu links removed from tab order via `hidden` class
- All interactive elements reachable without mouse

---

## Tailwind CSS Strategy

### Config (inline, before CDN script)

```html
<script>
  tailwind.config = {
    theme: {
      extend: {
        fontFamily: {
          sans: ['Inter', 'ui-sans-serif', 'system-ui', 'sans-serif'],
        }
      }
    }
  }
</script>
<script src="https://cdn.tailwindcss.com"></script>
```

No custom color tokens needed — all colors (`indigo-*`, `gray-*`, `teal-*`, `violet-*`) are in Tailwind's default palette.

### Key utility patterns

```
Container:       max-w-7xl mx-auto px-4 sm:px-6 lg:px-8
Fixed navbar:    fixed top-0 left-0 right-0 z-50
Hero grid:       grid grid-cols-1 lg:grid-cols-2 items-center gap-12 lg:gap-16
Section label:   text-xs font-semibold uppercase tracking-widest
H1:              text-4xl lg:text-5xl font-extrabold tracking-tight leading-tight
H2:              text-2xl lg:text-3xl font-bold tracking-tight
Card:            bg-white border border-gray-200 rounded-xl overflow-hidden
Card hover:      hover:shadow-md hover:-translate-y-0.5 transition-all duration-200
Primary button:  bg-indigo-700 hover:bg-indigo-800 text-white rounded-lg
Feature item:    flex gap-4 py-5 border-b border-gray-100 last:border-b-0
Stats row:       flex items-center divide-x divide-gray-200
```

### What to avoid in Tailwind

- `bg-gradient-to-*` on sections or large containers
- `rounded-2xl`, `rounded-3xl` on cards — maximum `rounded-xl`
- `rounded-full` except on logo badge and the three traffic-light dots
- `shadow-lg`, `shadow-xl`, `shadow-2xl` — maximum `shadow-md`, only on card hover
- `animate-*` — no CSS animations
- More than 1 brand color per section (exception: course card headers)

---

## Asset Strategy

### Font

Inter via Google Fonts. Loaded in `<head>` with `preconnect` before Tailwind CDN script.

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
```

### Icons

Heroicons — SVG inline, outline style, 20×20px. No external JS library. Copy SVG paths directly into HTML.

Required:
- `Bars3Icon` — hamburger
- `XMarkIcon` — close
- `AcademicCapIcon` — Structured Curriculum
- `UserCircleIcon` — 1-on-1 Mentorship
- `BriefcaseIcon` — Job Guarantee
- `WrenchScrewdriverIcon` — Learn by Doing
- `UsersIcon` — Strong Community
- `CalendarDaysIcon` — Flexible Schedule

All: `aria-hidden="true"`, `w-5 h-5`.

### Images

No `<img>` elements on this page.

- **Hero visual:** Code snippet block in HTML/CSS — `bg-gray-900 rounded-xl font-mono text-sm`
- **Course card headers:** Solid color blocks — no images
- **Testimonials/portraits:** Out of scope

---

## Anti-AI-Slop Checklist

- [ ] No `bg-gradient-to-*` used as a section background
- [ ] Feature section uses list layout with separators — not 6 shadow-boxed cards
- [ ] Course card headers use solid color blocks, not gradients
- [ ] No `rounded-2xl` or larger on cards — maximum `rounded-xl`
- [ ] `rounded-full` used only on logo badge and the three traffic-light decorative dots
- [ ] No box shadow in default card state — `shadow-md` only on hover
- [ ] Total unique brand colors ≤ 3 (indigo, gray scale, gray-900 dark)
- [ ] Course header colors are muted/dark — no bright or neon tones
- [ ] No glassmorphism except `backdrop-blur-sm` on navbar (justified: content beneath)
- [ ] No floating cards or elements overlaid on hero background
- [ ] H1 is the visually dominant element — readable without icons or color
- [ ] Section padding is not uniform — each section has its own vertical rhythm
- [ ] CTA Banner uses `bg-gray-900`, not a blue gradient
- [ ] Footer uses `bg-gray-900` solid, not a gradient
- [ ] No scroll reveal, fade-in, or entrance animations
- [ ] No `animate-bounce` or `animate-pulse`
- [ ] Every SVG icon has semantic purpose — remove it and text still communicates the same
- [ ] Section label (pre-heading badge) not applied to every section — used sparingly
- [ ] Mobile layout is a real redesign, not just a narrowed desktop
- [ ] All hover states are functional signals — none are purely decorative

