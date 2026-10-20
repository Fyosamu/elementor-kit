# VERA Atelier — Elementor Kit

A complete, production-ready fashion store you can rebuild inside **Elementor (Free or Pro)**
by pasting section-by-section HTML widgets. No page builder add-ons, no shortcodes, no jQuery —
just clean HTML, one CSS design system and one vanilla-JS behaviour file.

Live demo of everything included: open `index.html` in this folder (works offline, no build step).

---

## What's inside

```
elementor-kit/
├── vera-kit.css .............. the whole design system (25 KB, unminified, commented)
├── vera-kit.js ............... bag, filter, forms, reveals (10 KB, vanilla JS, self-guarding)
├── images/ ................... 20 CC0 photographs (JPEG/WebP, optimised, ~1.7 MB total)
├── screenshots/ .............. 5 ready-made store shots for your marketplace listing
├── widgets/ .................. 16 paste-ready HTML snippets
│   ├── 00-loader.html ........ loads CSS + JS + fonts  ← paste ONCE per page
│   ├── 01-header-nav.html .... sticky header + top bar + hamburger menu
│   ├── 02-hero.html .......... hero with stats and image
│   ├── 03-marquee.html ....... CSS-only scrolling strip
│   ├── 04-category-cards.html 6 deep-linking category cards
│   ├── 05-products-grid.html . featured products with "Add to bag"
│   ├── 06-editorial-split.html image + text split (reversible)
│   ├── 07-values-stats.html .. 4 value props
│   ├── 08-quotes.html ........ 3 testimonial cards
│   ├── 09-newsletter.html .... dark email capture block
│   ├── 10-footer.html ........ 4-column footer
│   ├── 11-bag-drawer-tabbar.html  slide-in bag + mobile tab bar + toast
│   ├── 12-category-page-head-chips.html  dynamic title + chip filter row
│   ├── 13-category-blocks.html 6 category editorial blocks
│   ├── 14-products-filtered-grid.html  19 products filtered by ?cat=
│   └── 15-contact-form.html .. contact form + info cards
├── index.html / categories.html / about.html / contact.html ... full working demo site
├── README.md ................. this file
├── INSTALL.md ................ step-by-step Elementor instructions
├── LISTING.md ................ ready-to-paste marketplace listing copy
└── VERA-Atelier-Elementor-Kit.zip  the packaged product (2.5 MB, folder-wrapped)
```

## Features

- **Category filtering that actually works** — clicking *Women* / *Men* / *Shoes* shows only that
  category's products, updates the headline, breadcrumb, count and URL (`?cat=men`), and works
  with browser back/forward.
- **Working cart** — add / remove / quantity / total, persisted in `localStorage`, slide-in drawer,
  mobile checkout that composes an order email.
- **Fully responsive** — verified at 320, 360, 390, 414, 768, 1024 and 1440 px with zero
  horizontal overflow. Two-column product grid on phones, app-style bottom tab bar,
  scrollable category chips.
- **Accessible by default** — content is visible without JavaScript (`.reveal` only hides after JS
  is confirmed active), with observers, scroll/resize listeners and a 9-second safety net.
- **White, gentle palette** — warm off-white paper, soft clay accent, Fraunces + Inter typography.
- **Self-contained JS** — wrapped in an IIFE with an idempotency guard, so it can never clash with
  Elementor, jQuery or itself.

## Requirements

- WordPress + Elementor 3.x (Free is enough; Pro only needed for Theme Builder / Custom Code).
- Any theme (Hello Elementor recommended).
- No WooCommerce required — the bag is a lightweight vanilla-JS cart.

## Customisation

Everything is token-based at the top of `vera-kit.css`:

```css
:root {
  --paper: #fdfcfa;   /* page background */
  --paper-2: #f6f3ee;  /* tinted sections */
  --ink: #16151a;      /* headings */
  --ink-2: #3c3a44;    /* body text */
  --clay: #b4674d;     /* accent */
  --radius: 18px;
}
```

Change the values above and the whole kit re-skins.

## Licensing

- Code: MIT — use it for client projects, resell inside your own builds.
- Photographs: CC0 / public-domain stock (Openverse, StockSnap, rawpixel) — commercial use allowed,
  no attribution required.
- Brand names, copy and prices are fictional placeholders — replace them with your own.

## Support

`INSTALL.md` covers setup, image replacement, changing the support email and troubleshooting.
