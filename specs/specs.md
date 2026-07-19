# Apex Lab — Booking Website Specification

## 1. Project Overview

**Business:** 9X Auto Spa - Premium Care Studio  
**Location:** Kuala Lumpur, Malaysia (near KL Sentral)  
**Contact:** +60179977133  
**Currency:** MYR (RM)  
**Year:** 2026

A single-page booking website that showcases services, displays dynamic pricing by vehicle size, and routes booking requests to WhatsApp.

---

## 2. Site Structure

The website is a single-page application with the following sections:

| # | Section | Anchor ID | Purpose |
|---|---------|-----------|---------|
| 1 | Navigation Bar | — | Fixed top nav with logo, links, and CTA |
| 2 | Hero | — | Full-viewport video background with headline and CTAs |
| 3 | Services | `#treatments` | Bento-grid cards showcasing 4 service categories |
| 4 | Pricing | `#pricing` | Interactive pricing matrix with vehicle-size switcher |
| 5 | Booking | `#portal` | Split layout: booking form + map/contact |
| 6 | Footer | — | Fixed bottom bar with copyright and social links |

---

## 3. Design & Branding

### 3.1 Visual Style
- **Theme:** Dark premium (background `#050507`)
- **Typography:** Inter / system-ui sans-serif
- **Accent colors:** White for CTAs, `#a1a1aa` for muted text, `#71717a` for labels
- **Effects:** Blur nav backdrop, radial gradient accents, hover elevations
- **Icons:** Font Awesome 6.5.1

### 3.2 Responsive Breakpoints
- **Desktop:** Full grid layouts (2-col bento, 4-col pricing, 2-col booking)
- **Tablet (≤1024px):** Pricing grid collapses to 2 columns
- **Mobile (≤768px):** Single-column layouts, hidden nav links, reduced hero text size

---

## 4. Navigation Bar

- **Position:** Fixed top, full-width, 120px height
- **Background:** Semi-transparent (`rgba(5,5,7,0.85)`) with 12px backdrop blur
- **Layout:** CSS Grid — 3 columns (logo | links | action button)
- **Logo:** 240×55px image (`logo.png`)
- **Links:** Services, Pricing, Book Now
- **CTA Button:** "Get Started" → scrolls to `#portal`
- **Mobile:** Only logo visible (centered), links and CTA hidden

---

## 5. Hero Section

- **Layout:** Centered, full viewport height (90vh min)
- **Background:** Looping video (`0628.mp4`) at 40% opacity with dark overlay
- **Content (z-index 2):**
  - Badge: "Premium Paint Protection & Detailing"
  - Headline: "We engineer absolute automotive perfection."
  - Two buttons: "View Services" → `#treatments`, "Reserve Slot" → `#portal`

---

## 6. Services Section

### 6.1 Layout
- 2-column bento grid, 380px row height, 24px gap
- Cards have background images with gradient overlays

### 6.2 Service Cards

| Card | Category Label | Title | Description | Image |
|------|---------------|-------|-------------|-------|
| 1 | Exterior Base | Car Wash | Cleans the outside, removes dirt, and adds a quick shine. | `detailing.webp` |
| 2 | Cabin Refresh | Interior Cleaning | Deep cleans the seats, vacuums the floors, and kills odors inside. | `interior.webp` |
| 3 | Defect Removal | Polish | Removes scratches and swirl marks to make the paint look brand new. | `paint correction.webp` |
| 4 | Surface Armor | Coating | Adds a long-lasting protective layer that keeps the car shiny and easy to clean. | `ceramic coating.webp` |

---

## 7. Pricing Section

### 7.1 Vehicle Size Switcher
Interactive button group with 6 sizes:
- Compact (default/active)
- Luxury
- SUV
- MPV / 4x4++
- Van
- Lorry

### 7.2 Pricing Matrix (all values in RM)

| Vehicle Size | Car Wash | Interior Cleaning | Polish | Coating |
|--------------|----------|-------------------|--------|---------|
| **Compact** | 15 | 25 | 199 | 50 |
| **Luxury** | 20 | 35 | 299 | 60 |
| **SUV** | 25 | 45 | 399 | 78 |
| **MPV / 4x4++** | 30 | 55 | 499 | 88 |
| **Van** | 40 | N/A | N/A | 60 |
| **Lorry** | 50 | N/A | N/A | 80 |

### 7.3 Sub-Labels per Size

| Vehicle Size | Wash Label | Interior Label | Polish Label | Coating Label |
|--------------|-----------|----------------|--------------|---------------|
| Compact–MPV | Normal Wash | Nano Mist Base | 1-Step Polish | Water Coating |
| Van | Normal Wash | Not Available | Not Available | Chemical Wash |
| Lorry | Normal Wash | Not Available | Not Available | Chemical Wash |

### 7.4 Pricing Cards (4 columns on desktop)
Each card displays:
- Service title
- Description
- Dynamic price (RM value)
- Dynamic sub-label

---

## 8. Booking Section

### 8.1 Layout
- Split 2-column grid inside a rounded card container
- Left: Booking form
- Right: Map, social links, phone number

### 8.2 Booking Form Fields

| Field | Type | Label | Placeholder / Options |
|-------|------|-------|----------------------|
| Full Name | text input | Full Name | "e.g. John Smith" |
| Vehicle | text input | Vehicle Model & Year | "e.g. Honda Civic FE 2022" |
| Vehicle Size | select dropdown | Vehicle Size Classification | Compact (Axia, Myvi, Yaris), Luxury (Civic, BMW 3 Series, C-Class), SUV (X50, CR-V, CX-5), MPV / 4x4++ (Alphard, Hilux), Van, Lorry |
| Service | select dropdown | Requested Service Line | Premium Car Wash, Interior Cleaning Package, Machine Polishing System, Advanced Protective Coating |
| Date/Time | text input | Preferred Date & Time | "e.g. Next Monday morning" |

### 8.3 Form Submission Behavior
- **Action:** Opens WhatsApp (`api.whatsapp.com`) in a new tab
- **Recipient:** +60102697127
- **Message template:**
  ```
  Hi 9X Auto Spa,

  I would like to lock in a detailing slot:

  • Name: {name}
  • Vehicle: {car}
  • Size Class: {size}
  • Service: {selectedService}
  • Preferred Time: {date}

  Please let me know if this slot is available. Thanks!
  ```

### 8.4 Map & Contact Panel
- **Map:** Google Maps embed (KL Sentral area), inverted color filter for dark theme
- **Social icons:** Instagram, TikTok, Facebook
- **Phone link:** +60179977133 (clickable `tel:` link)

---

## 9. Footer

- **Position:** Fixed bottom, full-width, 60px height
- **Content:**
  - Left: Empty links container (reserved)
  - Right: Copyright text "© 2026 Apex Lab. All rights reserved." + social icons (Facebook, Instagram, TikTok)

---

## 10. Technical Requirements

### 10.1 Frontend Stack
- Pure HTML5, CSS3, vanilla JavaScript (no frameworks)
- Font Awesome 6.5.1 via CDN
- Google Fonts: Inter (system fallback)

### 10.2 Assets Required
| Asset | Type | Usage |
|-------|------|-------|
| `logo.png` | Image | Navigation bar logo |
| `0628.mp4` | Video | Hero section background |
| `detailing.webp` | Image | Car Wash service card |
| `interior.webp` | Image | Interior Cleaning service card |
| `paint correction.webp` | Image | Polish service card |
| `ceramic coating.webp` | Image | Coating service card |

### 10.3 Functional Requirements
- Interactive pricing switcher updates all 4 price cards and their labels dynamically
- Booking form validates required fields before submission
- WhatsApp integration opens in new tab with pre-filled message
- Video hero auto-plays muted with loop
- Smooth scroll to anchored sections
- Responsive layout at 1024px and 768px breakpoints

### 10.4 Performance Considerations
- Lazy-loaded Google Maps iframe
- Backdrop-filter blur on nav (with `-webkit-` prefix)
- `overflow-x: hidden` on body to prevent horizontal scroll
- WebP images for service cards

---

## 11. Social Media Links

| Platform | URL |
|----------|-----|
| Instagram | https://www.instagram.com/9xautospa_studio/ |
| TikTok | https://tiktok.com |
| Facebook | https://facebook.com |

*(Placeholder URLs — to be updated with actual brand profiles)*

---

## 12. SEO & Meta

- **Title:** "9X Autospa - Premium Care Studio"
- **Charset:** UTF-8
- **Viewport:** `width=device-width, initial-scale=1.0`
- **Language:** English (`lang="en"`)
