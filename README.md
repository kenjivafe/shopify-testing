# LXP Practice Store

A practice Shopify store modelled on **lxpforged.com** (Luxury Performance Parts, Dubai) so you can
rehearse product operations — adding products one at a time and in bulk — without touching the live store.

| | |
|---|---|
| **Practice store** | `07jxvv-ym.myshopify.com` |
| **Admin** | https://admin.shopify.com/store/07jxvv-ym |
| **Plan / currency / market** | Basic · AED · United Arab Emirates |
| **Seeded** | 38 products (62 variants), 30 collections |

> This is a sandbox. Nothing here is connected to the live lxpforged.com store. Product copy has been
> rewritten and the catalogue is a representative sample, not a mirror.

## What's already in the store

**38 products**, all `ACTIVE`, published to the Online Store, inventory tracked at the *Al Furjan*
location, priced in AED. Coverage:

| Car | Products | | Category | Products |
|---|---|---|---|---|
| Ferrari | 8 | | Exhaust | 10 |
| Lamborghini | 10 | | Aerodynamic | 8 |
| McLaren | 8 | | Wheels | 8 |
| Rolls-Royce | 8 | | Suspension | 8 |
| Koenigsegg | 2 | | Collectibles | 3 |
| Porsche | 1 | | Engine | 1 |
| Aston Martin | 1 | | | |

**30 collections**, all *smart* (automated) collections driven by tags — see
[`docs/TAXONOMY.md`](docs/TAXONOMY.md). Because they're rule-based, a correctly tagged new product
lands in the right collections automatically; you never add products to a collection by hand.

## What's in this repo

| Path | What it's for |
|---|---|
| `data/bulk-import-practice.csv` | **33 products / 99 rows.** Not yet in the store — import this yourself to practise the CSV flow. |
| `data/practice-catalog-seeded.csv` | The 38 products already seeded, in Shopify CSV format. Reference, or re-seed a fresh store. |
| `data/seeded-catalog.json` | The same 38 products as structured JSON (titles, tags, variants, image URLs). |
| `data/bulk-products.jsonl` | JSONL of `ProductSetInput` payloads — the shape the Admin API bulk path expects. |
| `docs/TAXONOMY.md` | The tag scheme and how collections map to it. **Read this before adding products.** |
| `docs/PRACTICE-GUIDE.md` | Step-by-step drills: one-by-one, CSV bulk, and API bulk. |

## Start here

1. Read [`docs/TAXONOMY.md`](docs/TAXONOMY.md) — the tags are the whole system.
2. Work through [`docs/PRACTICE-GUIDE.md`](docs/PRACTICE-GUIDE.md), Drill 1 → 5.
3. Check your work at https://07jxvv-ym.myshopify.com — the storefront reflects the collections live.
