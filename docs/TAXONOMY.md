# Tag taxonomy

Every collection in this store is a **smart (automated) collection** with a single rule:
`Product tag is equal to <tag>`. Nothing is added to a collection manually.

That means **the tags you type when creating a product decide where it appears.** Get the tags right
and the product files itself into the car page, the category page, and the brand page at once. Get
them wrong and the product exists but is invisible to shoppers browsing.

This mirrors how lxpforged.com is organised.

## The five namespaces

| Prefix | Answers | Example |
|---|---|---|
| `car_` | Which marque? | `car_ferrari` |
| `model_` | Which model? | `model_purosangue` |
| `category_` | What kind of part? | `category_exhaust` |
| `brand_` | Who makes the part? | `brand_novitec` |
| `condition_` | New or used? | `condition_used` |

Plus two flat flags used by the reference store: `install_available` (fitting offered in Dubai) and
`pricing_buy_now` (priced, not enquiry-only).

## Allowed values

**`car_`** — `car_ferrari`, `car_lamborghini`, `car_mclaren`, `car_rolls_royce`, `car_porsche`,
`car_koenigsegg`, `car_aston_martin`

**`model_`** — `model_purosangue`, `model_12cilindri`, `model_812_superfast`, `model_812_gts`,
`model_sf90`, `model_f8`, `model_urus`, `model_urus_s`, `model_urus_performante`, `model_revuelto`,
`model_750s`, `model_senna`, `model_cullinan`, `model_cullinan_series_ii`, `model_spectre`, `model_911`

**`category_`** — `category_exhaust`, `category_aerodynamic`, `category_wheels`,
`category_suspension`, `category_engine`, `category_collectibles`

**`brand_`** — `brand_novitec`, `brand_spofec`, `brand_collectibles`, `brand_porsche`,
`brand_lamborghini`

**`condition_`** — `condition_new`, `condition_used`

> `brand_spofec` is Novitec's Rolls-Royce division — Rolls-Royce parts are tagged `brand_spofec`,
> not `brand_novitec`. Used OEM parts take the *car maker* as the brand (`brand_porsche`,
> `brand_lamborghini`) plus `condition_used`, which puts them in **LXP Used**.

## Tag → collection map

| Tag | Collection |
|---|---|
| `category_exhaust` | Category - Exhaust |
| `category_aerodynamic` | Category - Aerodynamic |
| `category_wheels` | Category - Wheels |
| `category_suspension` | Category - Suspension |
| `category_engine` | Category - Engine |
| `category_collectibles` | Category - Collectibles |
| `car_ferrari` | Car - Ferrari |
| `car_lamborghini` | Car - Lamborghini |
| `car_mclaren` | Car - McLaren |
| `car_rolls_royce` | Car - Rolls-Royce |
| `car_porsche` | Car - Porsche |
| `car_koenigsegg` | Car - Koenigsegg |
| `car_aston_martin` | Car - Aston Martin |
| `brand_novitec` | Brand - Novitec |
| `brand_spofec` | Brand - Spofec |
| `brand_collectibles` | Brand - Collectibles |
| `condition_used` | LXP Used |
| `model_purosangue` | Ferrari - Purosangue |
| `model_12cilindri` | Ferrari - 12Cilindri |
| `model_812_superfast` | Ferrari - 812 Superfast |
| `model_812_gts` | Ferrari - 812 GTS |
| `model_urus` **or** `model_urus_s` **or** `model_urus_performante` | Lamborghini - Urus *(OR rule)* |
| `model_urus_s` | Urus - S |
| `model_urus_performante` | Urus - Performante |
| `model_revuelto` | Lamborghini - Revuelto |
| `model_750s` | McLaren - 750S |
| `model_senna` | McLaren - Senna |
| `model_cullinan` **or** `model_cullinan_series_ii` | Rolls-Royce - Cullinan *(OR rule)* |
| `model_cullinan_series_ii` | Cullinan - Series II |
| `model_911` | Porsche - 911 |

Two collections use OR logic (*Lamborghini - Urus*, *Rolls-Royce - Cullinan*) so a parent page picks
up every sub-model. Everything else is a single-tag AND rule.

## Product fields, by convention

- **Title** — `<Part name> - <Car + model> - <Part numbers> - <Brand>`
  e.g. `Rear Diffusor - McLaren 750S Coupé & Spider - C6 750 67 - Novitec`
- **Vendor** — the parts brand (`Novitec`, `Spofec`, `Collectibles`) or the car maker for used OEM.
- **Type** — `Exhaust`, `Aerodynamics`, `Wheels`, `Suspension`, `Scale Model / Art Piece`,
  `Exhaust / Muffler`.
- **Option name** — `Variant` when there are real choices (material or fitment:
  *Stainless Steel / Inconel / Inconel Gold 999*, *With Tyres / Without Tyres*,
  *Ready for painting / Visible Carbon*). Leave the default `Title` when there's only one version.
- **SKU** — the manufacturer part number (`F1 666 10`) for new parts; the internal
  `LXP<supplier>-<category>-<seq>` code for used stock.
- **Body** — `<p>` summary, then an `<h4>Key Features</h4>` bullet list. Used parts add a condition
  paragraph and a "confirm the part number before ordering" line.
- **Price** — AED, no decimals in practice (`27900.00`).
