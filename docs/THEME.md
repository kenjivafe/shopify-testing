# Theme

The reference site runs **Concept** (Shopify theme store ID 2412), a paid theme that can't be
installed here. Rather than bend a free theme's settings into an approximation, the storefront UI is
**hand-written**: a own design-system stylesheet plus six custom Liquid sections, so the markup and
CSS are ours rather than Horizon's.

Horizon is still the installed theme — it supplies the header, footer, cart drawer, search and the
product/collection templates. The homepage is entirely custom.

## Design tokens

Read off lxpforged.com's live computed CSS. Concept ships several colour schemes; the **base**
scheme paints the page, and it is light.

| Token | lxpforged (Concept) | Ours (`--lxp-*`) |
|---|---|---|
| Background | `--color-base-background: 255 255 255` | `#ffffff` |
| Text | `--color-base-text: 23 23 23` | `#171717` |
| Button fill / text | `23 23 23` on `255 255 255` | same |
| Highlight | `--color-base-highlight: 255 221 191` | `#e0a580` accent |
| Border | `--color-border: foreground / 0.1` | `rgb(23 23 23 / .1)` |
| Sale badge | `#bf0303` | `#bf0303` |
| Page width | `--page-width: 1900px` | `1900px` |
| Page padding | `--page-padding: var(--sp-12)` (3rem) | `3rem`, `1.25rem` under 1024px |
| Button radius | `--rounded-button: 3.75rem` | `calc(infinity * 1px)` — pill |
| Input radius | `--rounded-input: 0.375rem` | `0.375rem` |
| Font | Inter | Inter |

Concept's fluid type ramps (`clamp()` on a 0.25rem `--sp-*` scale) are mirrored as
`--lxp-title-xl / -lg / -md` and `--lxp-body`.

## Files

| File | What it is |
|---|---|
| `assets/lxp-base.css.liquid` | The whole design system — tokens, layout, type, buttons, grids, cards, tiles |
| `sections/lxp-hero.liquid` | Full-bleed image hero with gradient scrim and pill CTA |
| `sections/lxp-marquee.liquid` | Scrolling text band, light or dark |
| `sections/lxp-collections.liquid` | Collection tile grid — `cover` for photography, `contain`-on-panel for cut-outs |
| `sections/lxp-products.liquid` | Product card grid — contained product shot, vendor, title, price, sale badge |
| `sections/lxp-split.liquid` | Image + text, image left or right, optional dark ground |
| `sections/lxp-statement.liquid` | Centred statement block |
| `templates/index.json` | Homepage, built only from the above |

Every section carries a `{% schema %}` with presets, so they're editable in the theme editor and can
be reused on any other template.

> **Note on the stylesheet name.** The CSS lives in `assets/lxp-base.css.liquid`, which Shopify
> compiles to `lxp-base.css`. A static `assets/lxp-base.css` also exists but is shadowed by the
> generated one and is unreachable — the API used here can't delete theme files, so it was left in
> place. Delete it from the admin if you want to tidy up; nothing references it.

## Homepage

| # | Section | Content |
|---|---|---|
| 1 | `lxp-hero` | Showroom photograph, "Performance without Compromise", pill CTA |
| 2 | `lxp-marquee` (dark) | Novitec · Spofec · TechArt · FI Exhaust · Liberty Walk · … |
| 3 | `lxp-collections` | **Shop by marque** — Ferrari, Lamborghini, McLaren, Rolls-Royce |
| 4 | `lxp-products` | **Novitec**, 8 products |
| 5 | `lxp-collections` | **Shop by category** — Exhaust, Aerodynamic, Wheels, Suspension, Collectibles, LXP Used |
| 6 | `lxp-split` | "Fitted in-house, in Dubai" |
| 7 | `lxp-products` | **Scale models & art pieces**, 4 products |
| 8 | `lxp-marquee` (light) | Free UAE shipping · Authorised partner · WhatsApp consultation · … |

Collection tiles trim the `Category - ` / `Car - ` / `Brand - ` prefix for display, so the grid reads
"Exhaust" while the collection keeps its full name.

## Navigation

Rebuilt to match the reference site exactly: **Shop · Brands · Installation · About · Contact**.
Shop and Brands are dropdowns; Installation, About and Contact are real pages (Installation and
About were created, Contact already existed).

## Images

In **Content → Files**:

| File | Used for |
|---|---|
| `lxp-logo.png` | Header logo |
| `lxp-hero-showroom.png` | Homepage hero |
| `lxp-install.png` | Installation split |
| `cover-ferrari.jpg` / `cover-lamborghini.jpg` / `cover-mclaren.jpg` | Marque tiles |

**Known gap:** the source catalogue has no Rolls-Royce photography, only white-background product
renders — so that one marque tile reads lighter than its three neighbours. Drop a real photo onto
the *Car - Rolls-Royce* collection and it will match.

## How it was verified

The storefront is password-protected, so it can't be fetched. Instead the CSS was rendered against
real catalogue data in headless Chromium at 1600px and 420px and inspected. That caught three things
worth knowing about:

1. The first dark palette was wrong — see the note below.
2. Collection tiles mixed photography with white cut-outs and looked unfinished; hence the
   `image_fit` setting and the grey panel treatment.
3. The original "installation" image was the LXP wordmark, not a workshop photo.

## The theme is NOT live yet

It's an **unpublished** theme, **“LXP Forged — Practice”**. Publishing is blocked for the API
integration used here, so the last step is manual:

> **Online Store → Themes → “LXP Forged — Practice” → Preview, then Publish**

The live theme stays stock Horizon until you click it; republishing `Horizon` rolls everything back.

### Why the first pass was dark

The initial build used `#171717` as the page ground. Those values come from Concept's *dark* scheme,
which the reference site uses only for photo-overlay sections. The logo settles it: `lxp-logo.png` is
black artwork on a **solid white background with zero transparency** (66% of its pixels are pure
white), so it can only sit on a light page.

## Still manual

- **Store name** — still "My Store". Settings → Store details.
- **Storefront password** — Online Store → Preferences.
- **Announcement bar** text — theme editor, header group.
- **Favicon** — theme settings.
