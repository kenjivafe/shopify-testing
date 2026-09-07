# LXP Practice Store

A practice Shopify store modelled on **lxpforged.com** (Luxury Performance Parts, Dubai) so you can
rehearse product operations — adding products one at a time and in bulk — without touching the live store.

| | |
|---|---|
| **Practice store** | `07jxvv-ym.myshopify.com` |
| **Admin** | https://admin.shopify.com/store/07jxvv-ym |
| **Plan / currency / market** | Basic · AED · United Arab Emirates |
| **Loaded** | 50 products · 31 collections · restyled theme (unpublished) |
| **Waiting to import** | 238 more products in `data/remaining-catalogue.csv` |

> This is a sandbox. Nothing here touches the live lxpforged.com store. Product copy has been
> rewritten rather than copied.

## Two things to do

**1. Publish the theme.** The dark, Concept-style look is built but sitting as an unpublished theme:

> Online Store → Themes → **“LXP Forged — Practice”** → Preview, then **Publish**

Publishing is a manual step by design (see [`docs/THEME.md`](docs/THEME.md)). The live theme stays
stock Horizon until you click it, and publishing the untouched `Horizon` theme rolls it back.

**2. Import the rest of the catalogue.**

> Products → Import → `data/remaining-catalogue.csv` → Upload and preview → Import products

That's 238 products / 704 rows with full descriptions and up to 3 images each. This is also Drill 3
in the practice guide — read [`docs/PRACTICE-GUIDE.md`](docs/PRACTICE-GUIDE.md) first so you know
what the file is doing.

## What's already in the store

**50 products**, all `ACTIVE`, published to the Online Store, inventory tracked at *Al Furjan*,
priced in AED. Three were added one at a time by hand; the rest in batches — so both flows are
demonstrated.

**31 collections**, all *smart* (automated), driven by tags — see [`docs/TAXONOMY.md`](docs/TAXONOMY.md).
Because they're rule-based, a correctly tagged product lands in the right collections automatically;
you never add products to a collection by hand. 17 of them have cover images.

Marques covered: Ferrari, Lamborghini, McLaren, Rolls-Royce, Porsche, Koenigsegg, Aston Martin.
Categories: Exhaust, Aerodynamic, Wheels, Suspension, Engine, Collectibles, plus LXP Used.

## What's in this repo

| Path | What it's for |
|---|---|
| `data/remaining-catalogue.csv` | **238 products / 704 rows.** Not yet in the store — import this. |
| `data/loaded-catalogue.csv` | The 50 already loaded, in Shopify CSV format. Reference, or re-seed a fresh store. |
| `data/catalogue-full.json` | All 288 products as structured JSON (titles, tags, variants, image URLs). |
| `docs/TAXONOMY.md` | The tag scheme and tag→collection map. **Read before adding products.** |
| `docs/PRACTICE-GUIDE.md` | Five drills: one-by-one, bulk edit, CSV import, collections, inventory. |
| `docs/THEME.md` | How the look was rebuilt, what's still manual. |

## Known gaps

- **Store name** is still "My Store" (Settings → Store details).
- **Storefront is password-protected** — the default for a new store. Online Store → Preferences to
  lift it. Everything works in the admin regardless.
