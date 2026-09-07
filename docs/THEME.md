# Theme

The reference site runs **Concept** (Shopify theme store ID 2412), a paid theme. It can't be
installed on this practice store, so the look was rebuilt on **Horizon** — the free theme already on
the store — by matching Concept's design tokens.

## Where the design came from

Sampled directly from lxpforged.com's rendered CSS custom properties:

| Token | lxpforged (Concept) | Practice store (Horizon) |
|---|---|---|
| Background | `--color-background: 23 23 23` | `#171717` |
| Foreground | `--color-foreground: 250 250 250` | `#FAFAFA` |
| Accent | `--color-highlight: 224 165 128` | `#E0A580` |
| Border | — | `#2E2E2E` |
| Sale badge | `--badge-background: #bf0303` | `#BF0303` |
| Button border | `--buttons-border-width: 2px` | `2px` |
| Body font | Inter | Inter (Horizon's default) |

Horizon derives its entire palette from four colours, so setting those four gets most of the way
there. On top of that:

- **Headings** uppercase with normal tracking (h1–h3) and loose tracking on the small
  eyebrow/label styles (h5, h6) — the automotive-luxury signature.
- **Square corners** everywhere: buttons, cards, product images, inputs, badges, variant pickers.
- **Accent buttons** — bronze fill with dark text, 2px border.
- **Page width** set to wide; product card hover does a slow image zoom.

## The theme is NOT live yet

It's installed as an **unpublished** theme called **“LXP Forged — Practice”**. Publishing a theme is
blocked for the API integration used to build this, so the last step is manual:

> **Online Store → Themes → “LXP Forged — Practice” → … → Publish**

Preview it first with the **Preview** (eye) button next to it. The live theme is still stock Horizon
until you publish, so nothing is at risk — and you can always publish the untouched `Horizon` theme
to roll back.

## Homepage

`templates/index.json` was rebuilt to mirror the reference site's section order:

| # | Section | Content |
|---|---|---|
| 1 | Hero (full-screen) | `lxp-hero.png`, "Performance without Compromise", CTA to all products |
| 2 | Marquee | Scrolling brand names on the bronze accent — Novitec, Spofec, TechArt, FI Exhaust, Liberty Walk… |
| 3 | Collection list | **Shop by marque** — Ferrari, Lamborghini, McLaren, Rolls-Royce |
| 4 | Product list | Featured from **Brand - Novitec** |
| 5 | Collection list | **Shop by category** — Exhaust, Aerodynamic, Wheels, Suspension, Collectibles, LXP Used |
| 6 | Hero (medium) | "Professional installation in Dubai" |
| 7 | Product list | **Category - Collectibles** |
| 8 | Marquee | Free UAE shipping · Authorised partner · WhatsApp consultation · Installation |

## Navigation

`main-menu` was rebuilt as a three-group dropdown structure, mirroring the reference site:

- **Shop by marque** → Ferrari, Lamborghini, McLaren, Rolls-Royce, Porsche, Koenigsegg, Aston Martin
- **Shop by category** → Exhaust, Aerodynamic & Styling, Wheels, Suspension, Engine, Collectibles
- **Brands** → Novitec, Spofec, Collectibles
- **LXP Used**
- **All products**

Footer menu: Search, All products, Novitec, Spofec, LXP Used.

## Images

Four files were pulled into **Content → Files** and are referenced by the theme:

| File | Used for |
|---|---|
| `lxp-logo.png` | Header logo (theme setting `logo`, height 44px) |
| `lxp-hero.png` | Homepage hero |
| `lxp-feature-1.png` | Installation band |
| `lxp-feature-2.png` | Spare |

All 17 main collections also got cover images, picked from the flagship product in each — that's what
fills the "Shop by marque" and "Shop by category" grids.

## Still manual

A few things the API can't set, if you want them:

- **Store name** — still "My Store". Settings → Store details.
- **Storefront password** — the store is password-protected (default for a new store). Online Store
  → Preferences → remove the password to browse it as a customer would.
- **Announcement bar** text — Theme editor, header group.
- **Favicon** — theme settings.
