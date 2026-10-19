# Requirements Document

## Introduction

Revou Landing Page adalah sebuah **single-page static website** yang berfungsi sebagai halaman pemasaran utama untuk **Revou**, sebuah tech bootcamp terkemuka di Indonesia. Website ini dirancang untuk menarik calon peserta didik, menampilkan program kursus yang tersedia, dan mendorong konversi (pendaftaran atau konsultasi).

Website dibangun tanpa framework atau build tool — murni HTML5 semantik, Tailwind CSS via CDN, dan Vanilla JavaScript. Tidak ada backend, tidak ada proses build, dan tidak ada framework JavaScript.

**Target Pengguna:** Calon peserta bootcamp berusia 18–35 tahun yang mencari program pendidikan teknologi di Indonesia, menggunakan perangkat desktop maupun mobile.

**Tech Stack:**
- HTML5 (semantic markup)
- Tailwind CSS via CDN
- Vanilla JavaScript (jika diperlukan)
- Tidak menggunakan React, Vue, Next.js, backend, atau build tools

**Scope:** Satu halaman HTML statis (`index.html`) dengan satu file JavaScript (`script.js`) yang mencakup: Navbar, Hero Section, Features Section, Courses Section, CTA Banner, dan Footer.

---

## Glossary

- **Website**: Aplikasi web single-page statis yang dibahas dalam dokumen ini.
- **Navbar**: Bilah navigasi tetap (fixed/sticky) yang tampil di bagian paling atas halaman.
- **Mobile Menu**: Menu navigasi vertikal yang tampil di perangkat mobile ketika Hamburger Button diklik.
- **Hamburger Button**: Tombol ikon tiga garis horizontal yang memicu tampilnya Mobile Menu pada tampilan mobile.
- **Hero Section**: Bagian pembuka utama halaman (id="about") yang menampilkan proposisi nilai utama Revou.
- **Features Section**: Bagian halaman (id="features") yang menampilkan keunggulan-keunggulan program Revou.
- **Courses Section**: Bagian halaman (id="courses") yang menampilkan daftar program kursus populer Revou.
- **CTA Banner**: Bagian halaman (id="contact") berisi ajakan bertindak utama kepada pengguna.
- **Footer**: Bagian penutup halaman yang berisi tautan, informasi legal, dan hak cipta.
- **Smooth Scroll**: Efek gulir halus saat pengguna berpindah antar section melalui tautan navigasi.

---

## Requirements

### Requirement 1: Navbar

**User Story:** As a visitor, I want to see a persistent navigation bar at the top of the page, so that I can access any section of the website at any time without scrolling back to the top.

#### Acceptance Criteria

1. THE Navbar SHALL render in a fixed position at the top of the Viewport, remaining visible during vertical scroll.
2. THE Navbar SHALL display a logo composed of a badge containing the text "RV" and an adjacent text label "Revou".
3. WHILE the Viewport width is Desktop, THE Navbar SHALL display navigation links for "About", "Features", "Courses", and "Contact" in a horizontal row.
4. WHILE the Viewport width is Desktop, THE Navbar SHALL display a "Log in" button and a "Get Started" button to the right of the navigation links.
5. WHILE the Viewport width is Mobile, THE Navbar SHALL hide the horizontal navigation links and display only the Hamburger Button.
6. THE Navbar SHALL have a z-index value sufficient to appear above all other page content.

---

### Requirement 2: Mobile Navigation Toggle

**User Story:** As a mobile user, I want to open and close a navigation menu using a hamburger button, so that I can navigate between sections without the menu taking up permanent screen space.

#### Acceptance Criteria

1. WHEN the Hamburger Button is clicked while the Mobile Menu is closed, THE Navbar SHALL display the Mobile Menu.
2. WHEN the Hamburger Button is clicked while the Mobile Menu is open, THE Navbar SHALL hide the Mobile Menu.
3. THE Mobile Menu SHALL display navigation links "About", "Features", "Courses", and "Contact" arranged vertically.
4. THE Mobile Menu SHALL display a "Log in" button and a "Get Started" button below the navigation links.
5. WHEN a navigation link inside the Mobile Menu is clicked, THE Navbar SHALL automatically close the Mobile Menu.
6. THE Hamburger Button SHALL toggle its icon between a three-line state and an X state.
7. THE Hamburger Button SHALL have an aria-expanded attribute reflecting the current menu state.

---

### Requirement 3: Hero Section

**User Story:** As a prospective student, I want to see a compelling hero section when I first visit the page, so that I can immediately understand what Revou offers and take action.

#### Acceptance Criteria

1. THE Hero Section SHALL be assigned the HTML id attribute value "about".
2. THE Hero Section SHALL display a badge containing the text "#1 Tech Bootcamp in Indonesia".
3. THE Hero Section SHALL display an h1 heading with the text "Launch Your Tech Career in 6 Months".
4. THE Hero Section SHALL display a short descriptive paragraph conveying Revou's value proposition.
5. THE Hero Section SHALL display a CTA button labeled "Explore Courses" that initiates a Smooth Scroll to id="courses".
6. THE Hero Section SHALL display a secondary CTA button labeled "Learn More" that initiates a Smooth Scroll to id="features".
7. THE Hero Section SHALL display three statistics: "10K+ Graduates", "93% Job Placement", and "500+ Hiring Partners".
8. THE Hero Section SHALL display a visual placeholder element.
9. WHILE the Viewport width is Desktop, THE Hero Section SHALL arrange content in a two-column layout.
10. WHILE the Viewport width is Mobile, THE Hero Section SHALL arrange content in a single-column layout.

---

### Requirement 4: Features Section

**User Story:** As a prospective student, I want to see a clear list of Revou's key advantages, so that I can understand why I should choose Revou over other programs.

#### Acceptance Criteria

1. THE Features Section SHALL be assigned the HTML id attribute value "features".
2. THE Features Section SHALL display an h2 heading with the text "Why Choose Revou?".
3. THE Features Section SHALL display exactly six feature cards: "Structured Curriculum", "1-on-1 Mentorship", "Job Guarantee", "Learn by Doing", "Strong Community", and "Flexible Schedule".
4. WHILE the Viewport width is Mobile, THE Features Section SHALL arrange the feature cards in a single-column grid.
5. WHILE the Viewport width is Tablet, THE Features Section SHALL arrange the feature cards in a two-column grid.
6. WHILE the Viewport width is Desktop, THE Features Section SHALL arrange the feature cards in a three-column grid.
7. WHEN a user hovers over a feature card, THE Features Section SHALL apply a lift and increased shadow effect.

---

### Requirement 5: Courses Section

**User Story:** As a prospective student, I want to browse available courses with key details, so that I can quickly identify a program that matches my career goals.

#### Acceptance Criteria

1. THE Courses Section SHALL be assigned the HTML id attribute value "courses".
2. THE Courses Section SHALL display an h2 heading with the text "Popular Courses".
3. THE Courses Section SHALL display exactly three course cards: "Full Stack Software Engineering" (6 bulan), "Data Analytics" (3 bulan), and "Product Management" (4 bulan).
4. THE Courses Section SHALL render each course card with a gradient header, category badge, title, description, duration, and format.
5. WHILE the Viewport width is Mobile, THE Courses Section SHALL arrange course cards in a single-column grid.
6. WHILE the Viewport width is Tablet, THE Courses Section SHALL arrange course cards in a two-column grid.
7. WHILE the Viewport width is Desktop, THE Courses Section SHALL arrange course cards in a three-column grid.
8. WHEN a user hovers over a course card, THE Courses Section SHALL apply a lift and increased shadow effect.
9. THE Courses Section SHALL display a "View All Courses" button below the course cards grid.

---

### Requirement 6: CTA Banner Section

**User Story:** As a prospective student who has reviewed the page, I want to see a prominent call-to-action area, so that I am encouraged to apply or speak with an advisor.

#### Acceptance Criteria

1. THE CTA Banner SHALL be assigned the HTML id attribute value "contact".
2. THE CTA Banner SHALL display an h2 heading with the text "Ready to Start Your Journey?".
3. THE CTA Banner SHALL display a short descriptive paragraph inviting the user to take action.
4. THE CTA Banner SHALL display an "Apply Now" button as the primary CTA.
5. THE CTA Banner SHALL display a "Talk to an Advisor" button as the secondary CTA.
6. THE CTA Banner SHALL have a distinct background that differentiates it from adjacent sections.

---

### Requirement 7: Footer

**User Story:** As a visitor, I want to find company information, navigation links, and legal policies at the bottom of the page, so that I can explore further or review policies.

#### Acceptance Criteria

1. THE Footer SHALL display the Revou logo and a tagline.
2. THE Footer SHALL display a "Company" link group: About, Courses, Features, Contact.
3. THE Footer SHALL display a "Legal" link group: Privacy Policy, Terms of Service, Cookie Policy.
4. THE Footer SHALL display copyright "© 2026 Revou. All rights reserved." and "Made with ❤ in Indonesia".
5. WHILE the Viewport width is Desktop, THE Footer SHALL arrange its content in a four-column grid layout.
6. WHILE the Viewport width is Mobile, THE Footer SHALL arrange its content in a single-column layout.

---

### Requirement 8: Smooth Scroll Navigation

**User Story:** As a visitor, I want clicking navigation links to smoothly scroll the page to the target section, so that the experience is seamless rather than jarring.

#### Acceptance Criteria

1. WHEN a navigation link pointing to an on-page anchor is clicked, THE Script SHALL scroll the Viewport smoothly to the target section.
2. WHEN smooth scrolling, THE Script SHALL offset the final scroll position by the Navbar height so the section heading is not obscured.
3. THE Script SHALL apply Smooth Scroll behavior to all anchor links in the Navbar and the Hero Section CTA buttons.

---

### Requirement 9: Scroll-Based Navbar Shadow

**User Story:** As a visitor, I want the navbar to visually indicate my scroll position, so that it remains legible and distinct from page content.

#### Acceptance Criteria

1. WHILE the vertical scroll position is greater than 10 pixels, THE Navbar SHALL display a drop shadow.
2. WHEN the vertical scroll position returns to 10 pixels or less, THE Navbar SHALL remove the drop shadow.
3. THE Script SHALL update the Navbar shadow state on each scroll event using a passive listener.

---

### Requirement 10: Responsive Layout

**User Story:** As a user on any device, I want the website to display correctly on my screen size, so that I can read content and navigate without issues.

#### Acceptance Criteria

1. THE Website SHALL render without horizontal overflow at viewport widths of 320px, 768px, and 1280px.
2. THE Website SHALL use Tailwind CSS responsive prefixes (sm, md, lg) to manage layout breakpoints.
3. WHILE the Viewport width is Mobile, THE Website SHALL display all text at a legible font size without requiring zoom.

---

### Requirement 11: Accessibility and Performance

**User Story:** As a user with assistive technology or a slow connection, I want the website to be accessible and load quickly.

#### Acceptance Criteria

1. THE Website SHALL use semantic HTML5 elements (header, nav, main, section, footer) throughout.
2. THE Hamburger Button SHALL have aria-label and aria-expanded attributes updated dynamically.
3. THE Website SHALL ensure all interactive elements are focusable via keyboard.
4. THE Website SHALL maintain a color contrast ratio of at least 4.5:1 for normal text.
5. THE Script SHALL be loaded with the defer attribute.

---

### Requirement 12: Technical Stack Constraints

**User Story:** As a developer, I want the website to use only the specified technologies so the project stays simple and dependency-free.

#### Acceptance Criteria

1. THE Website SHALL consist of index.html, script.js, and a static assets folder.
2. THE Website SHALL NOT depend on any JavaScript framework or library.
3. THE Website SHALL load Tailwind CSS exclusively via CDN.
4. THE Website SHALL NOT require a backend server, database, or server-side rendering.
5. THE Script SHALL be written in Vanilla JavaScript (ES6+) without external libraries.
