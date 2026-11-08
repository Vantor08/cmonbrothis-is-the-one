# Vallore SuperBalance — Shopify Theme

A complete, upload-ready Shopify theme. The entire storefront design lives in one
section (`sections/main-page.liquid`); the templates are thin pointers that render it,
which is standard Shopify structure.

---

## Step 1 — Folder structure (all 7 required folders present)

These sit at the **root** of the zip (not inside a subfolder), exactly as Shopify requires:

```
vallore-theme/
├── assets/      CSS, JavaScript, images
├── config/      settings_data.json, settings_schema.json
├── layout/      theme.liquid (main wrapper), password.liquid
├── locales/     en.default.json (translations)
├── sections/    main-page.liquid  ← the whole store design (67 KB)
├── snippets/    price.liquid (reusable money formatting)
└── templates/   one file per Shopify page (see Step 2)
```

---

## Step 2 — Each template corresponds to a Shopify admin page

| Shopify admin page              | File                                   | Renders                                   |
| ------------------------------- | -------------------------------------- | ----------------------------------------- |
| Home page                       | `templates/index.liquid`               | → `{% section 'main-page' %}` (home view) |
| Products                        | `templates/product.liquid`             | → `{% section 'main-page' %}` (buy box)   |
| Collections                     | `templates/collection.liquid`          | Collection product grid                   |
| Collections list                | `templates/list-collections.liquid`    | All-collections page                      |
| Gift card                       | `templates/gift_card.liquid`           | Gift card                                 |
| Cart                            | `templates/cart.liquid`                | Cart page                                 |
| Checkout and customer accounts  | `templates/customers/*.liquid`         | login, register, account, order, addresses, reset, activate |
| Pages                           | `templates/page.liquid`                | Static pages (About, Contact, etc.)       |
| Blogs                           | `templates/blog.liquid`                | Blog index                                |
| Blog posts                      | `templates/article.liquid`             | Single blog post                          |
| Search                          | `templates/search.liquid`              | Search results                            |
| Password                        | `templates/password.liquid` + `layout/password.liquid` | Coming-soon page          |
| (not-found)                     | `templates/404.liquid`                 | 404 page                                  |

**How the design loads:** `layout/theme.liquid` wraps every page, loads
`assets/theme.css` + `assets/theme.js`, and drops in the template. Both the home and
product templates call the same `main-page` section — that's why they're one line each.

---

## Install

**Option A — Upload zip**
Online Store → Themes → Add theme → Upload zip file → select this zip → Publish.

**Option B — GitHub**
Put the **contents** of this folder at the repo root (so `assets/`, `config/`, etc.
are top-level), then Online Store → Themes → Add from GitHub.

> The folders must be at the root. If you see `vallore-theme/assets/...` instead of
> `assets/...` at the top level, re-zip from *inside* the folder.

---

## Ritual videos (not included in the zip)

The 5 ritual-video slots stay hidden until you add URLs:
1. Shopify admin → Content → Files → upload each video.
2. Copy each file URL.
3. Paste into the `ritual_video_1 … ritual_video_5` variables at the top of
   `sections/main-page.liquid`.

---

## Notes

- Prices, reviews, ratings and lab claims in the design are **placeholders** — wire them
  to real data before going live.
- Flavor color theming (plum for Red Strawberry, berry-pink for Blue Raspberry) is
  CSS-driven via the `body.theme-blue` class — no extra setup needed.
