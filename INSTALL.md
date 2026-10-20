# Installing the VERA Atelier kit in Elementor

Three ways to use the kit. Way 1 works with **Elementor Free** and needs no plugins.

---

## Way 1 — HTML widgets (recommended, Free & Pro)

### 1. Upload the assets once

Copy `vera-kit.css`, `vera-kit.js` and the `images/` folder into your site, for example:

```
/wp-content/uploads/vera-kit/
├── vera-kit.css
├── vera-kit.js
└── *.jpg
```

(You can upload them with **Media → Add New → Folder**, or with an FTP/SFTP client.
WordPress ignores `.css` / `.js` in the media library visually but still stores them fine.)

> **No server access?** Host the three items on any static host (GitHub Pages, your existing
> GitHub Pages site, Cloudflare Pages) and use the absolute URL in step 2.

### 2. Add the loader widget

1. Edit the page in Elementor.
2. Add an **HTML** widget at the very top of the page.
3. Paste the contents of `widgets/00-loader.html`.
4. Edit the two paths so they point at where you uploaded the files:

```html
<link rel="stylesheet" href="https://your-site.com/wp-content/uploads/vera-kit/vera-kit.css" />
<script src="https://your-site.com/wp-content/uploads/vera-kit/vera-kit.js" defer></script>
```

### 3. Paste the sections

Add another **HTML** widget for each section you want, in this order, and paste the matching file:

| Order | File | What you get |
|---|---|---|
| 1 | `00-loader.html` | design system + fonts + JS (once, at the top) |
| 2 | `01-header-nav.html` | sticky header, hamburger, bag button |
| 3 | `02-hero.html` | hero, two buttons, stats, image |
| 4 | `03-marquee.html` | scrolling strip |
| 5 | `04-category-cards.html` | six category cards |
| 6 | `05-products-grid.html` | featured products |
| 7 | `06-editorial-split.html` | image + text block (paste again, keep both halves) |
| 8 | `07-values-stats.html` | value props |
| 9 | `08-quotes.html` | testimonials |
| 10 | `09-newsletter.html` | newsletter |
| 11 | `10-footer.html` | footer |
| 12 | `11-bag-drawer-tabbar.html` | bag drawer + mobile tab bar (once, at the end) |

For the shop page use `12`, `13` and `14` instead of 4–6, and for the contact page use `15`.

**Tips**

- Keep each HTML widget in a **Section / Container with no padding** — the kit controls its own spacing.
- Set the page layout to **Elementor Full Width** so the header and footer stretch properly.
- `11-bag-drawer-tabbar.html` must appear **once** per page; the bag depends on it.

---

## Way 2 — Elementor Pro: Custom Code (cleanest)

1. Upload the assets as in step 1.
2. **Elementor → Custom Code → Add New**:
   - Location: `<head>` (end) → paste the `<link rel="stylesheet" …>` and the font `<link>`.
   - Location: `</body>` (end) → paste the `<script src="…vera-kit.js">`.
   - Set it to display on the whole site.
3. Save. Now every HTML widget on any page works without its own loader.

---

## Way 3 — Quick offline check

Open `index.html` from this folder in a browser: the whole demo (home, filtered shop, about,
contact, cart) runs locally with no server, no build, no dependencies.

---

## Images

Every widget references photographs with **relative paths**:

```html
<img src="images/women.jpg" alt="Women's collection" />
```

After pasting into Elementor:

1. Upload the photos from `images/` to your Media Library.
2. Select the image in the HTML widget and replace the `src` with the Media Library URL, e.g.
   `src="https://your-site.com/wp-content/uploads/2026/09/women.jpg"`.

That is a search-and-replace of `images/` → your upload folder. All 20 photos are CC0, so they can
be used commercially without attribution.

---

## Configuration

Open `vera-kit.js` (top of the file, inside the `CONFIG` object) and set your own values:

```js
const CONFIG = {
  supportEmail: "hkay7645@gmail.com",  // orders + contact form land here
  wallet: "0xE1E3…",                          // optional USDT address shown at checkout
};
```

- **Order / contact forms** use `mailto:` — no backend needed. If you prefer a real endpoint,
  replace the two `window.location.href = mailto:…` lines with a `fetch()` to your form service.
- **Newsletter** shows a success toast; hook it to Mailchimp/Brevo by adding a real `<form action>`.

---

## Category filtering

`14-products-filtered-grid.html` contains all 19 products with `data-cat` attributes:

```
women · men · shoes · accessories · kids   (+ data-new="1" for the "New in" view)
```

- Chips in `12-…` call `apply(category)` and write `?cat=men` to the URL.
- Your own links: `your-page/?cat=women` opens that category directly.
- To add a product, duplicate an `<article class="product reveal" …>` block and change
  `data-id`, `data-name`, `data-price`, `data-img` and `data-cat`.
- Counts shown on the chips are plain text in the markup — update them by hand.

---

## Troubleshooting

| Symptom | Fix |
|---|---|
| Nothing is styled | The loader widget is missing or `vera-kit.css` path is wrong — check the browser console (F12). |
| Buttons do nothing | `vera-kit.js` path is wrong, or the widget is pasted before the DOM finished loading (keep `defer`). |
| Bag is empty after refresh | Another script is clearing `localStorage`, or the page is served from a different origin (http vs https). |
| A section stays invisible | Content is hidden by the scroll-reveal. Scroll once, or remove the `reveal` class from that element. |
| Two headers / two footers | You pasted the widget twice — delete the duplicate. |
| Filter shows nothing | The grid needs the exact id `productGrid`; Elementor sometimes rewrites ids — re-check the HTML widget. |
| Products overlap at odd widths | Set the parent Container's Content Width to 1200 px and gap to 0. |
