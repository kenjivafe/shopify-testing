# Theme

The reference site runs **Concept** (Shopify theme store ID 2412), a paid theme. It can't be
installed on this practice store, so the look was rebuilt on **Horizon** — the free theme already on
the store — by matching Concept's design tokens.

## Where the design came from

Sampled from lxpforged.com's rendered CSS custom properties. Concept ships several colour
schemes; the **base** scheme is what paints the page ground, and it is light:

| Token | lxpforged (Concept base) | Practice store (Horizon) |
|---|---|---|
| Background | `--color-base-background: 255 255 255` | `#FFFFFF` |
| Text | `--color-base-text: 23 23 23` | `#171717` |
| Button fill | `--color-base-button: 23 23 23` | `#171717` |
| Button text | `--color-base-button-text: 255 255 255` | `#FFFFFF` |
| Highlight | `--color-base-highlight: 255 221 191` | `#E0A580` (accent) |
| Border | `--color-border: foreground / 0.1` | `#E5E5E5` |
| Sale badge | `--badge-background: #bf0303` | `#BF0303` |
| Body font | Inter | Inter (Horizon's default) |

Shape tokens, also read off the live site:

| | lxpforged | Practice store |
|---|---|---|
| Buttons | `--rounded-button: 3.75rem` (`data-rounded-button="round"`) | radius 60 — pill |
| Inputs | `--rounded-input: 0.375rem` (`round-slight`) | radius 6 |
| Cards | `data-rounded-card="round"` | radius 8 |

Horizon derives its whole palette from four colours, so setting those four gets most of the way
there. On top of that:

- **Light ground, dark pill buttons** — white page, near-black buttons with white text.
- **Uppercase only on the small styles** (h5/h6 eyebrows and labels) with loose tracking. h1–h3
  stay sentence case, because on the reference site the capitalisation is written into the copy
  rather than forced by a global text-transform.
- **Photography sections stay dark** — the two heroes keep a dark gradient overlay with white
  text on top, which is how the reference site handles its imagery.
- Page width wide; product cards zoom their image slowly on hover.

### A note on why this changed

The first pass had this dark (`#171717` ground). That was wrong: those values come from
Concept's *dark* scheme, which the reference site uses for photo-overlay sections, not for the
page itself. The giveaway is the logo — `lxp-logo.png` is black artwork on a **solid white
background with zero transparency** (66% of its pixels are pure white), so it can only sit on a
light page without showing as a white slab.

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
| 2 | Marquee | Scrolling brand names in a dark band — Novitec, Spofec, TechArt, FI Exhaust, Liberty Walk… |
| 3 | Collection list | **Shop by marque** — Ferrari, Lamborghini, McLaren, Rolls-Royce |
| 4 | Product list | Featured from **Brand - Novitec** |
| 5 | Collection list | **Shop by category** — Exhaust, Aerodynamic, Wheels, Suspension, Collectibles, LXP Used |
| 6 | Hero (medium) | "Professional installation in Dubai" |
| 7 | Product list | **Category - Collectibles** |
| 8 | Marquee | Free UAE shipping · Authorised partner · WhatsApp consultation · Installation (plain, on white) |

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
fills the "Shop by marque" and "Shop by category" grids. Card titles sit *below* the image in dark
text, rather than over it, now that the page ground is light.

## Still manual

A few things the API can't set, if you want them:

- **Store name** — still "My Store". Settings → Store details.
- **Storefront password** — the store is password-protected (default for a new store). Online Store
  → Preferences → remove the password to browse it as a customer would.
- **Announcement bar** text — Theme editor, header group.
- **Favicon** — theme settings.
