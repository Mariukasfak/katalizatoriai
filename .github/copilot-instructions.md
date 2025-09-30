# Copilot instructions for `katalizatoriai`

### Project snapshot
- Static Lithuanian landing page for catalytic converter buyback. No build system—everything lives in `index.html`, `assets/css/styles.css`, and the small `/assets/img` set.
- Keep copy in Lithuanian unless the request explicitly says otherwise; headings, ARIA labels, and metadata are tuned for local SEO.

### Architecture & content flow
- `index.html` is the single entry point. Major sections are ordered hero → benefits → process → pricing → service-quality → locations → testimonials → FAQ → CTA. Additions should follow this narrative and reuse existing section classes.
- Reusable utility/shared classes (e.g., `.container`, `.section`, `.btn`) already handle layout and typography—prefer extending them instead of redefining layout rules inline.
- Section markup follows an accessible pattern: semantic headings, `aria-labelledby`, and descriptive list/figure elements. Preserve this structure when editing or creating new blocks.

### Styling patterns
- Global theme variables live at the top of `assets/css/styles.css`; reuse or extend those tokens (`--color-*`, `--radius-*`, `--shadow-*`) for visual consistency.
- Class naming is BEM-influenced (`hero__content`, `section-benefits`). Stick to that scheme and co-locate new styles near related blocks in the CSS file.
- Responsive tweaks use `@media (max-width: 768px)` and `@media (min-width: 1024px)` breakpoints. When adding components, mirror these breakpoints.

### JavaScript & embeds
- The page relies on two third-party scripts: Google Analytics (`gtag.js`) and Tawk.to chat. Do not remove or rename their script tags without explicit instruction.
- Custom JS is inline at the bottom of `index.html` and currently only manages header scroll states and footer year. New behavior should be wrapped in an IIFE and be defensive against missing DOM nodes.

### SEO & structured data
- Critical meta tags (canonical, OG, Twitter) plus two JSON-LD blocks (`LocalBusiness`, `FAQPage`) live in `index.html`. If you change contact info or FAQ content, update both the visible copy and the corresponding JSON-LD entries.
- `robots.txt` and `sitemap.xml` are manually curated. When publishing new pages, add URLs to `sitemap.xml` and keep the `Sitemap` directive accurate.

### Assets & media
- Logos exist as both PNG and WebP; serve WebP inside `<picture>` with PNG fallback. Provide matching resolutions when adding new imagery to maintain performance.
- Optimize new images for dark backgrounds and keep alt text descriptive (Lithuanian preferred).

### Local workflows
- No package manager is required. Preview locally with any static server, for example:
  ```bash
  cd /workspaces/katalizatoriai && python3 -m http.server 8000
  ```
- Before delivery, manually scan in-browser for responsive breakpoints (mobile ≤768px, desktop ≥1024px) and verify sticky header, sticky CTA, and chat widget still behave as expected.

### Key files to know
- `index.html` – main page structure, metadata, inline scripts.
- `assets/css/styles.css` – global theme tokens, layout, responsive rules.
- `assets/img/` – logo assets used in `<picture>` elements.
- `sitemap.xml`, `robots.txt` – SEO configuration you must keep in sync with content.
