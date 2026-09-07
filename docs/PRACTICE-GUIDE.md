# Practice guide

Five drills, easiest first. Admin: https://admin.shopify.com/store/07jxvv-ym

Before you start, read [`TAXONOMY.md`](TAXONOMY.md). The tags are what make this store work.

---

## Drill 1 — Add one product by hand

The everyday task. Do it three or four times until the field order is muscle memory.

**Products → Add product.** Fill in, in this order:

1. **Title** — follow the convention: `<Part> - <Car + model> - <Part numbers> - <Brand>`.
2. **Description** — a `<p>` summary, then `<h4>Key Features</h4>` and a bullet list. Use the
   `<>` (Show HTML) button in the rich-text editor to paste HTML directly.
3. **Media** — drag in photos. First image becomes the featured image. Set alt text on each.
4. **Pricing** — AED. Leave *Compare-at price* empty unless it's genuinely discounted.
5. **Inventory** — tick **Track quantity**, set a SKU (the manufacturer part number), set the
   quantity at *Al Furjan*.
6. **Variants** — if the part comes in materials or fitments, add option **Variant** with values
   like `Stainless Steel` / `Inconel` / `Inconel Gold 999`. Each variant gets its own SKU and price.
7. **Product organisation** — Vendor, Type, and then **Tags** from the taxonomy. This is the step
   people skip; it's the one that matters.
8. **Status: Active**, and confirm *Online Store* is ticked under Publishing.

**Check it worked:** open **Collections** and confirm the product appeared in its car, category and
brand collections without you touching them. If it didn't, a tag is wrong.

Try one of each shape:
- a single-variant part (e.g. a sport spring set)
- a multi-variant part (an exhaust in three materials)
- a used OEM part (`condition_used` → it should land in **LXP Used**)

---

## Drill 2 — Edit and bulk-edit

1. **Products → select several → Bulk edit.** Add a tag to all of them at once, change status,
   adjust prices. This is the fastest way to fix a batch of miscategorised products.
2. Use the **Bulk editor** columns feature to add e.g. *Variant Price* and edit inline like a spreadsheet.
3. Change one product's tags so it *leaves* a collection; watch the collection count drop. Change it
   back. This proves to you that smart collections are live, not a one-time snapshot.

---

## Drill 3 — Bulk import from CSV

The real skill. `data/bulk-import-practice.csv` holds **33 products / 99 rows** that are *not* yet in
the store, so you'll see them actually appear.

1. **Products → Import → Add file →** choose `data/bulk-import-practice.csv`.
2. Leave *"Overwrite any current products that have the same handle"* **unticked** for a first run.
3. **Upload and preview**, check the preview table, then **Import products**.
4. Shopify emails you when it finishes and reports any skipped rows.

**Read the file first** so the format stops being mysterious — open it in Excel or Sheets:

- **Handle** is the identity. Rows sharing a handle are *the same product*.
- The **first row** of a handle carries Title, Body, Vendor, Type, Tags, Status.
- **Subsequent rows** for the same handle leave those blank and carry only the next variant
  (`Option1 Value`, `Variant SKU`, `Variant Price`, …) or an extra image
  (`Image Src` + `Image Position`, everything else blank).
- **Tags** is one comma-separated cell — that's why the whole cell is quoted.
- **Image Src** must be a public HTTPS URL. Shopify downloads it and re-hosts it.

**Things to try deliberately:**
- Re-run the same import with *overwrite* ticked. Nothing duplicates — handles matched, rows updated.
- Change a price in the CSV, re-import with overwrite, confirm the product updated in place.
- Break a row on purpose (delete a `Variant Price`, misspell a tag) and read what the import
  warning tells you. Learning to read the error is the point.
- **Products → Export** your own catalogue and compare it to the file you imported. Export/import
  round-tripping is how you'd do a mass price change on the real store.

---

## Drill 4 — Collections

1. **Products → Collections → Create collection → Automated.** Make
   *"Ferrari - SF90"* with the condition `Product tag is equal to model_sf90`.
2. Import or tag a product with `model_sf90` and watch it populate.
3. Compare with a **Manual** collection: create one, add products by hand, then notice it does *not*
   update itself when you add a matching product later. That difference is why this store uses
   automated collections throughout.
4. Set **Sort order** to *Price: high to low* — the convention used on the seeded collections.

---

## Drill 5 — Inventory and everything after

- **Products → Inventory** — adjust quantities, filter by location, use the bulk quantity editor.
- **Products → Inventory → Export/Import** for a stock-take workflow.
- **Discounts → Create discount** — make a percentage code and test it on the storefront.
- Place a test order using Shopify's **Bogus Gateway** (Settings → Payments) so you can see how an
  order, a fulfilment and an inventory decrement actually behave end to end.

---

## Reference: rebuilding from scratch

If you want to wipe and re-seed, `data/practice-catalog-seeded.csv` reproduces the 38 seeded
products, and `data/bulk-products.jsonl` is the same catalogue as Admin API `ProductSetInput`
payloads if you'd rather do it through the API than the CSV importer.

To empty the store first: **Products → select all → Actions → Delete products.** Collections are
smart, so they empty themselves; delete them separately if you want a truly blank store.
