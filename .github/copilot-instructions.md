# Copilot Instructions – Katalizatoriai Website

## Project Overview

**Katalizatoriai** is a single-page, static marketing website for a Lithuanian catalytic converter and DPF filter buying service. The site uses semantic HTML, a dark-theme design system with gold accents, and responsive layouts optimized for mobile-first viewing.

- **Language**: Lithuanian (lang="lt")
- **Tech Stack**: Vanilla HTML, CSS Grid/Flexbox, vanilla JavaScript
- **Key Files**: `index.html` (main page), `assets/css/styles.css`, `assets/img/` (graphics)
- **Hosting**: Static file delivery (no backend)

## Architecture & Components

### Page Structure (Semantic Sections)

1. **Header (`<header class="site-header">`)** – Sticky, responsive navigation bar
   - Logo with picture element (WebP fallback)
   - Company branding and contact links (phone, WhatsApp, Viber)
   - Compact mode triggered at 120px scroll, hidden at 200px scroll

2. **Hero Section (`#hero`)** – Main call-to-action
   - Responsive grid: 2 columns on desktop, 1 column on mobile
   - Left: Headline, badge, CTAs, bullets, trust metrics
   - Right: Price ticker (hidden on mobile, display: none at breakpoint)
   - Background: Dual radial gradients for depth

3. **Benefits Section (`#benefits`)** – 4 cards in grid
   - Desktop: 4 columns; Mobile: 1 column
   - Key messaging on service quality

4. **Process Section (`#process`)** – 3-step numbered flow
   - Desktop: 3 columns; Mobile: 1 column
   - Step numbers positioned absolutely on mobile, static on desktop

5. **Pricing Section (`#pricing`)** – Pricing table + FAQ note
   - Table: Single column on mobile, 3 columns (1.2fr 0.8fr 1.2fr) on desktop
   - Responsive font sizing and padding

6. **Design/Service Quality (`#service-quality`)** – 4 feature cards
   - Desktop: 4 columns; Mobile: 1 column
   - Cards with accent gradient overlay

7. **Locations (`#locations`)** – City list for service coverage
   - Desktop: 5 columns; Mobile: 1 column; Tablet: 2 columns

8. **Testimonials (`#testimonials`)** – Client quotes
   - Desktop: 3 columns; Mobile: 1 column

9. **FAQ (`#faq`)** – Collapsible details/summary elements
   - SEO-optimized with structured data

10. **Guide (`#gidas`)** – 3 detailed articles with tables
    - Responsive table with horizontal scroll on mobile
    - Articles: padding 24px on mobile → 32px on desktop

11. **CTA Section (`#cta`)** – Final call-to-action

12. **Footer** – Contact info, partners, links

### Fixed UI Elements

- **Sticky CTA Bar** (`.sticky-cta`) – Visible only on mobile (<640px), bottom of viewport
  - 3 links: Call, WhatsApp, Viber
  - Disappears on desktop (display: none @640px+)
  - Min-height: 60px to prevent overlap with floating buttons

- **Floating Contact Buttons** (`.floating-contact`)
  - Positioned: fixed right 16px, bottom calc(80px + 16px) on mobile
  - Desktop: bottom 24px, gap 12px
  - 3 icon buttons with gradient backgrounds

## Responsive Design Breakpoints

```css
Mobile-first defaults: 1 column, padding 12px, smaller fonts
@media (min-width: 640px): 2–4 columns, padding 14–30px, increased fonts
@media (min-width: 960px): 4 columns, enhanced spacing
```

### Key Mobile Fixes (Applied)

- Button sizes: 12px 24px on mobile → 14px 30px on desktop
- Section padding: 60px on mobile → 80px on desktop
- Header padding: 12px on mobile → 18px on desktop
- Font sizes use `clamp()` for smooth scaling
- Images: `loading="lazy"`, `decoding="async"`
- No horizontal scroll; overflow-x: hidden on body

## CSS Design System

### Color Variables (Dark Theme)

```css
--color-background: #0b131d (deep navy)
--color-surface: #111b29 (dark blue-gray)
--color-accent: #ffb400 (gold)
--color-accent-dark: #f49500
--color-text: #f4f7fb (off-white)
--color-text-muted: #b8c4d7 (soft gray)
--color-border: rgba(255, 255, 255, 0.08)
```

### Typography

- **Font Family**: Inter (system fallbacks: -apple-system, BlinkMacSystemFont, sans-serif)
- **Line Height**: 1.6 (body), 1.1–1.2 (headings)
- **Weights**: 400 (normal), 600 (semi-bold), 700 (bold)
- **Heading Sizes**: Responsive using `clamp()`
  - H1: clamp(1.8rem, 5vw, 3rem)
  - H2: clamp(1.6rem, 4vw, 2.5rem)

### Spacing & Shadows

```css
--radius-lg: 20px
--radius-md: 14px
--radius-sm: 10px
--shadow-soft: 0 26px 54px -26px rgba(15, 24, 35, 0.72)
--shadow-card: 0 22px 44px -28px rgba(0, 0, 0, 0.7)
--transition: 0.3s cubic-bezier(0.4, 0, 0.2, 1)
```

## SEO & Metadata

- **Title & Description**: Optimized for "katalizatorių supirkimas" + geo-terms
- **Keywords**: Includes city names (Vilnius, Kaunas, Panevėžys, etc.)
- **Open Graph**: og:title, og:description, og:image (logotipas.png)
- **Twitter Card**: summary_large_image
- **Canonical**: https://katalizatoriu-supirkimas.lt/
- **Robots Meta**: index, follow, max-snippet:-1, max-image-preview:large
- **Structured Data**: JSON-LD for FAQPage and AutomotiveBusiness schema

### Critical Fix Applied

- Removed emoji (✅) from meta description (was causing encoding issues)
- Added proper lang="lt" with Lithuanian locale in OG tags

## JavaScript Patterns

### Header Scroll Behavior

```javascript
// Sticky header compact/hidden states
- Compact: padding reduced at 120px scroll
- Hidden: transform translateY(-100%) at 200px scroll
- Passive scroll listener for performance
```

### Tawk Chat Integration

```javascript
// Deferred loading (3s timeout)
// Custom branding: replaces chat bubble icon with logotipas.png
// Callback chains: onLoad, onChatMaximized, onChatMinimized
```

### Dynamic Year in Footer

```javascript
document.getElementById('year').textContent = new Date().getFullYear()
```

## Common Maintenance Tasks

### Updating Contact Information

1. **Phone Links**: `href="tel:+37063655055"` (appears in 4 places: header, hero CTA, sticky bar, floating buttons)
2. **WhatsApp**: `href="https://wa.me/37063655055"`
3. **Viber**: `href="viber://contact?number=%2B37063655055"`

Update all three in:
- Header contact links
- Hero CTA buttons
- Sticky CTA bar (mobile)
- Floating contact buttons

### Updating Pricing Table

Edit `.pricing-row` divs in `#pricing` section. Row structure:
```html
<div class="pricing-row" role="row">
  <div class="pricing-cell">Type</div>
  <div class="pricing-cell">Price</div>
  <div class="pricing-cell">Note</div>
</div>
```

### Adding/Removing Cities

Edit `.cities` list in `#locations`. Displays as:
- Mobile: 1 column
- Tablet: 2 columns
- Desktop: 5 columns

### Adding New Guide Article

1. Create `<article id="straipsnis-NEW" class="guide-article">`
2. Add `<h2 id="straipsnis-NEW-title">` with title
3. Add footer link: `<a href="#straipsnis-NEW">`
4. Use `.guide-article__subheading` for subsections
5. Use `.guide-table-wrapper` + `.guide-table` for data tables

## Performance & Accessibility

### Optimizations Applied

- CSS custom properties for theming (single source of truth)
- No runtime compilation; pure CSS Grid/Flexbox
- Image lazy loading: `loading="lazy"` + `decoding="async"`
- WebP with PNG fallback via `<picture>`
- Sticky positioning for header (GPU-accelerated)
- Minimal JavaScript (scroll detection, chat integration)

### Accessibility Enhancements

- Semantic HTML: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`
- ARIA labels on all major sections (`aria-label`, `aria-labelledby`)
- Focus states: `outline: 2px solid rgba(255, 180, 0, 0.5)` on buttons
- Keyboard navigation: all links and buttons are focusable
- Color contrast: text meets WCAG AA standards (off-white on dark)
- Details/Summary for FAQ (native browser expand/collapse)

## Development Workflow

### Adding a New Component

1. **HTML**: Add semantic section with ID and aria labels
2. **CSS**: Create mobile-first base styles, then @media queries for larger breakpoints
3. **Responsive**: Test at 375px (mobile), 768px (tablet), 1024px+ (desktop)
4. **Focus**: Ensure focus-visible states on interactive elements

### Testing Checklist

- [ ] Mobile (<640px): No horizontal scroll, buttons don't overlap
- [ ] Tablet (640–960px): 2-column grids display correctly
- [ ] Desktop (960px+): Full 4-column grids, hero image visible
- [ ] Sticky header: Compact at 120px, hidden at 200px
- [ ] Floating buttons: No overlap with sticky CTA on mobile
- [ ] Contact buttons: All three (phone, WhatsApp, Viber) functional
- [ ] Forms/CTAs: Links use tel:, https://wa.me/, viber:// protocols
- [ ] Images: Load with correct srcset, alt text present
- [ ] Links: All internal anchors (#hero, #process, etc.) work
- [ ] SEO: Meta tags, structured data, canonical URL correct

## Notes & Gotchas

1. **Hero Highlight (Price Ticker)** is hidden on mobile (<640px) with `display: none` to preserve viewport space.
2. **Sticky CTA Bar** only appears on mobile; floats above footer with bottom: 0. Disappears on desktop.
3. **Floating Contact Buttons** positioned slightly above sticky CTA to avoid overlap.
4. **Color Theme**: Gold (#ffb400) is reserved for accents, hover states, and CTAs. Never use for body text.
5. **Font Loading**: Google Fonts with `display=swap` ensures text renders while fonts load.
6. **Tawk Chat**: Integrated via deferred script injection. Custom branding replaces default bubble.
7. **Lithuanian Language**: Content is 100% Lithuanian. Ensure all updates maintain this.

---

**Last Updated**: December 1, 2025  
**Maintained By**: Mariukasfak (GitHub owner)
