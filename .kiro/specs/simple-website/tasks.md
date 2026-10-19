# Implementation Plan: Revou Landing Page

## Overview

Single-page static website for Revou — a tech bootcamp landing page. Built with HTML5, Tailwind CSS via CDN, and Vanilla JavaScript. No build tools, no framework. 11 tasks in logical implementation order: project setup → HTML shell → sections (Navbar, Hero, Features, Courses, CTA Banner, Footer) → JavaScript → Accessibility → QA.

## Tasks

- [ ] 1. Create project file structure — create empty `index.html`, `script.js`, and `assets/` folder at workspace root. Verify all three exist before proceeding. (Req 12.1)

- [ ] 2. Build HTML document shell — add DOCTYPE, `<html lang="id">`, `<head>` with charset and viewport meta, Inter font via Google Fonts (preconnect + stylesheet, weights 400–800), inline `tailwind.config` script extending `fontFamily.sans` to `['Inter', 'ui-sans-serif', 'system-ui', 'sans-serif']`, Tailwind CDN script, a `<style>` block for the `header.scrolled` rule (`border-color: #e5e7eb; box-shadow: 0 1px 3px 0 rgb(0 0 0/0.1)`), semantic `<header id="navbar">`, `<main>` with four empty section placeholders (`#about`, `#features`, `#courses`, `#contact`), `<footer>`, and `<script src="script.js" defer>` as last body child. Verify page opens without console errors and Inter font loads. (Req 11.1, 12.3, 12.5; Design: Architecture, Tailwind CSS Strategy)

- [ ] 3. Implement Navbar — inside `<header>` add `class="fixed top-0 left-0 right-0 z-50 bg-white/95 backdrop-blur-sm border-b border-transparent transition-all duration-200"`. Add `<nav aria-label="Main navigation">` with `max-w-7xl mx-auto px-4 sm:px-6 lg:px-8` container. Inner flex row (`flex items-center justify-between h-16`) contains: (a) logo `<a href="#">` with indigo badge `w-7 h-7 bg-indigo-700 text-white text-xs font-bold rounded` showing "RV" and text `text-base font-semibold text-gray-900` showing "Revou"; (b) desktop nav `<ul class="hidden lg:flex items-center gap-6">` with four links (About `#about`, Features `#features`, Courses `#courses`, Contact `#contact`) each `text-sm font-medium text-gray-600 hover:text-gray-900 transition-colors duration-150`; (c) desktop auth `<div class="hidden lg:flex items-center gap-3">` with Log in (secondary, small: `bg-white border border-gray-300 text-gray-700 text-sm font-semibold rounded-lg px-4 py-2 hover:bg-gray-50 hover:border-gray-400 focus:outline-none focus:ring-2 focus:ring-gray-400 focus:ring-offset-2 transition-all duration-150`) and Get Started (primary, small: `bg-indigo-700 hover:bg-indigo-800 text-white text-sm font-semibold rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-indigo-700 focus:ring-offset-2 transition-colors duration-150`); (d) hamburger `<button id="menu-toggle" aria-label="Toggle navigation menu" aria-expanded="false" aria-controls="mobile-menu" class="lg:hidden p-2 text-gray-600 hover:text-gray-900 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-700 focus:ring-offset-2 transition-colors duration-150">` with two inline Heroicons SVGs: `id="icon-bars"` (Bars3Icon) and `id="icon-x" class="hidden"` (XMarkIcon), both `aria-hidden="true" w-5 h-5`. After the flex row add mobile menu `<div id="mobile-menu" class="hidden lg:hidden bg-white border-t border-gray-200" aria-label="Mobile navigation">` with vertical links (`block px-4 py-3 text-sm font-medium text-gray-700 hover:bg-gray-50`) and Log in + Get Started buttons full-width below a separator. Verify: at lg+ nav links visible and hamburger hidden; below lg hamburger visible and nav links hidden. (Req 1.1–1.6, 2.1–2.7; Design: Components → Navbar, Primary Button, Secondary Button)

- [ ] 4. Implement Hero Section — add to `<section id="about">`: `class="bg-gray-50 pt-32 pb-20 lg:pt-40 lg:pb-28"` and `aria-labelledby="hero-heading"`. Inside `max-w-7xl` container add two-column grid `grid grid-cols-1 lg:grid-cols-2 items-center gap-12 lg:gap-16`. Left column: section label `<span class="inline-block text-xs font-semibold uppercase tracking-widest text-indigo-600 bg-indigo-50 px-3 py-1 rounded-md mb-4">#1 Tech Bootcamp in Indonesia</span>`; `<h1 id="hero-heading" class="text-4xl lg:text-5xl font-extrabold tracking-tight leading-tight text-gray-900 mt-2 mb-4">Launch Your Tech Career in 6 Months</h1>`; description `<p class="text-base leading-relaxed text-gray-600 mb-8">`; CTA buttons `<div class="flex flex-col sm:flex-row gap-3">` with "Explore Courses" `<a href="#courses">` (primary, large: `px-6 py-3`) and "Learn More" `<a href="#features">` (secondary, large: `px-6 py-3`); stats row `<div class="flex items-center divide-x divide-gray-200 mt-10">` with three `<div class="flex flex-col px-5 first:pl-0">` items showing `text-3xl font-bold tabular-nums` value and `text-sm text-gray-500 mt-1` label for 10K+ Graduates, 93% Job Placement, 500+ Hiring Partners. Right column: code snippet block `<div class="bg-gray-900 rounded-xl overflow-hidden shadow-lg">` with header bar `bg-gray-800 px-4 py-3 flex items-center gap-2` containing three dots (`w-3 h-3 rounded-full` in red-400/70, yellow-400/70, green-400/70) and `<pre class="p-5 text-sm font-mono leading-relaxed overflow-x-auto text-gray-300">` with short JS snippet using `<span>` for syntax colors (keywords `text-indigo-400`, strings `text-emerald-400`, numbers `text-amber-400`). On mobile: text centered (`text-center lg:text-left`), CTA buttons centered (`justify-center sm:justify-start`), right column stacks below. Verify all content visible and layout switches at lg. (Req 3.1–3.10; Design: Components → Hero Visual Placeholder, Stats Item, Section Label)

- [ ] 5. Implement Features Section — add to `<section id="features">`: `class="bg-white py-16 lg:py-20"` and `aria-labelledby="features-heading"`. Inside container add `<h2 id="features-heading" class="text-2xl lg:text-3xl font-bold tracking-tight text-gray-900 mb-2">Why Choose Revou?</h2>` and supporting description `<p>`. Add features grid `<div class="grid grid-cols-1 sm:grid-cols-2 gap-x-16 gap-y-0">`. Each of 6 items: `<div class="flex gap-4 py-5 border-b border-gray-100 last:border-b-0 hover:bg-gray-50 rounded-lg px-2 -mx-2 transition-colors duration-150">` containing icon container `<div class="w-9 h-9 flex-shrink-0 rounded-lg bg-gray-100 flex items-center justify-center">` with Heroicon SVG (`w-5 h-5 text-gray-700 aria-hidden="true"`) and text div with `<h3 class="text-base font-semibold text-gray-900">` and `<p class="text-sm leading-relaxed text-gray-600 mt-1">`. Items: (1) AcademicCapIcon — Structured Curriculum; (2) UserCircleIcon — 1-on-1 Mentorship; (3) BriefcaseIcon — Job Guarantee; (4) WrenchScrewdriverIcon — Learn by Doing; (5) UsersIcon — Strong Community; (6) CalendarDaysIcon — Flexible Schedule. Verify: no card borders or shadows, separator lines between items, 2-col at sm+, subtle hover background. (Req 4.1–4.7; Design: Components → Feature Item — list format, not cards)

- [ ] 6. Implement Courses Section — add to `<section id="courses">`: `class="bg-gray-50 py-16 lg:py-24"` and `aria-labelledby="courses-heading"`. Inside container add `<h2 id="courses-heading">Popular Courses</h2>` (same H2 classes) and description. Add grid `<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">`. Each of 3 cards: `<article class="bg-white border border-gray-200 rounded-xl overflow-hidden hover:shadow-md hover:-translate-y-0.5 transition-all duration-200 ease-in-out">` with card header `<div class="h-28 bg-[color] px-5 flex items-end pb-4">` containing `<span class="text-xs font-semibold uppercase tracking-widest text-white/70">[Category]</span>` and card body `<div class="p-5">` with `<h3>`, description `<p class="text-sm text-gray-500 leading-relaxed mt-1 mb-4">`, and meta row `<div class="flex items-center gap-3 text-sm text-gray-400 border-t border-gray-100 pt-3">` with duration, separator dot "·", and format. Card header colors: Full Stack = `bg-indigo-700`; Data Analytics = `bg-teal-700`; Product Management = `bg-violet-700`. Below grid add "View All Courses" centered secondary button. Verify: solid-color headers (not gradient), hover lift + shadow with flat default state, correct 1→2→3 column grid. (Req 5.1–5.9; Design: Components → Course Card)

- [ ] 7. Implement CTA Banner — add to `<section id="contact">`: `class="bg-gray-900 py-20 lg:py-28"` and `aria-labelledby="cta-heading"`. Inside container add centered wrapper `<div class="max-w-2xl mx-auto text-center flex flex-col items-center gap-6">` with `<h2 id="cta-heading" class="text-2xl lg:text-3xl font-bold tracking-tight text-gray-50">Ready to Start Your Journey?</h2>`, description `<p class="text-base leading-relaxed text-gray-400">`, and buttons row `<div class="flex flex-col sm:flex-row gap-3">` with "Apply Now" (primary on dark: `bg-indigo-700 hover:bg-indigo-800 text-white text-sm font-semibold rounded-lg px-6 py-3 focus:outline-none focus:ring-2 focus:ring-white focus:ring-offset-gray-900 transition-colors duration-150`) and "Talk to an Advisor" (secondary on dark: `bg-transparent border border-white/30 text-white text-sm font-semibold rounded-lg px-6 py-3 hover:bg-white/10 hover:border-white/50 focus:outline-none focus:ring-2 focus:ring-white focus:ring-offset-gray-900 transition-all duration-150`). Verify: dark background (not gradient), both buttons legible in white text, stacked on mobile and side-by-side at sm+. (Req 6.1–6.6; Design: Page Structure → CTA Banner `bg-gray-900`; Anti-AI-Slop Checklist)

- [ ] 8. Implement Footer — add to `<footer>`: `class="bg-gray-900 pt-12 pb-8"` and `aria-label="Site footer"`. Inside container add top grid `<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8 pb-10 border-b border-gray-700">` with: brand column (`lg:col-span-2`) containing logo (same as navbar but text-white) and tagline `<p class="mt-3 text-sm text-gray-400 max-w-xs">`; Company column with `<h3 class="text-xs font-semibold uppercase tracking-widest text-gray-400 mb-3">Company</h3>` and links `<ul>` (About, Courses, Features, Contact) each `<a class="text-sm text-gray-400 hover:text-gray-50 transition-colors duration-150">`; Legal column same pattern with Privacy Policy, Terms of Service, Cookie Policy. Below grid add copyright bar `<div class="mt-8 flex flex-col sm:flex-row items-center justify-between gap-2 text-xs text-gray-500">` with `<span>© 2026 Revou. All rights reserved.</span>` and `<span>Made with ❤ in Indonesia</span>`. Verify: `bg-gray-900` continuous from CTA Banner, 4-col at lg, 1-col on mobile, hover transitions to near-white on all links. (Req 7.1–7.6; Design: Page Structure → Footer)

- [ ] 9. Implement Vanilla JavaScript in script.js — write four behaviors: (1) Hamburger toggle: get `#menu-toggle`, `#mobile-menu`, `#icon-bars`, `#icon-x`; on click toggle `hidden` on menu, swap `hidden` between icons, set `aria-expanded` to string of new open state. (2) Mobile menu auto-close: `mobileMenu.querySelectorAll('a')` forEach, on click add `hidden` to menu, show `icon-bars`, hide `icon-x`, set `aria-expanded="false"`. (3) Smooth scroll: `document.querySelectorAll('a[href^="#"]')` forEach; on click get target via `document.querySelector(href)`, return early if null, `preventDefault()`, compute `top = target.getBoundingClientRect().top + window.scrollY - document.getElementById('navbar').offsetHeight - 8`, call `window.scrollTo({ top, behavior: 'smooth' })`. (4) Scroll shadow: `window.addEventListener('scroll', () => { document.getElementById('navbar').classList.toggle('scrolled', window.scrollY > 10) }, { passive: true })`. Verify all four behaviors per completion criteria below. (Req 2.1–2.7, 8.1–8.3, 9.1–9.3, 11.5, 12.5; Design: Interaction Design; Correctness Properties 2, 3, 4)

- [ ] 10. Accessibility audit — verify and fix: all four `<section>` elements have `aria-labelledby` pointing to their H2 id; `<nav>` has `aria-label="Main navigation"`; `<footer>` has `aria-label="Site footer"`; hamburger `<button>` has `aria-label`, `aria-expanded`, `aria-controls`; `#mobile-menu` has `aria-label`; every inline SVG has `aria-hidden="true"`; tab through entire page and confirm all interactive elements reachable in logical DOM order; verify focus rings are visible (indigo on light, white on dark) on every focused element; confirm hidden mobile menu links are not in tab order when menu is closed. (Req 11.1–11.4; Design: Accessibility section)

- [ ] 11. Final QA — test the following and fix any issues found: (a) responsive layout at 320px, 640px, 768px, 1024px, 1280px — no horizontal overflow at any width; (b) navbar breakpoint — hamburger at 1023px, nav links at 1024px; (c) scroll shadow threshold — no shadow at 9px, shadow at 11px; (d) smooth scroll offset — every nav link leaves section heading clear of navbar; (e) mobile menu open/close/auto-close and icon swap; (f) open `index.html` by double-clicking from file explorer — must work with no server; (g) zero JS console errors on load and all interactions; (h) verify each item in the Anti-AI-Slop Checklist in design.md — no gradients on sections, feature list not cards, course card headers solid color; (i) test in Chrome, Firefox, and Edge. (Req 10.1–10.3, 12.1–12.5; Design: Testing Strategy, Anti-AI-Slop Checklist)

## Task Dependency Graph

```json
{
  "waves": [
    {
      "wave": 1,
      "tasks": ["1"],
      "description": "Project Setup"
    },
    {
      "wave": 2,
      "tasks": ["2"],
      "description": "HTML Document Shell"
    },
    {
      "wave": 3,
      "tasks": ["3", "4", "5", "6", "7", "8"],
      "description": "All page sections — independent of each other, all depend on Task 2"
    },
    {
      "wave": 4,
      "tasks": ["9"],
      "description": "Vanilla JavaScript — requires all section IDs to exist in DOM"
    },
    {
      "wave": 5,
      "tasks": ["10"],
      "description": "Accessibility Audit"
    },
    {
      "wave": 6,
      "tasks": ["11"],
      "description": "Final QA"
    }
  ]
}
```

## Notes

- Tasks 3–8 (sections) depend only on Task 2 and are independent of each other — they can be implemented in any order
- Task 9 (JavaScript) requires all section IDs and element IDs (`navbar`, `menu-toggle`, `mobile-menu`, `icon-bars`, `icon-x`) to exist in the DOM
- The `header.scrolled` CSS rule must live in a `<style>` block in `<head>` because Tailwind CDN does not support `@apply` in external stylesheets
- All Heroicon SVGs should be copied inline from heroicons.com (outline style, 20×20) — no external icon library
- Do not use `rounded-2xl` or larger on any card — maximum `rounded-xl`
- Do not use `bg-gradient-to-*` on any section background or course card header


