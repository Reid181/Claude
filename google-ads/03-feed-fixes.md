# 03. Feed fixes in Shopify

Shopping ads match on the feed, mostly the title and the Google product category. Shopify is the source of truth: the Google & YouTube channel overwrites Merchant Center on every sync, so every fix is made in Shopify, never in the Merchant Center product editor. Allow 24 to 48 hours after saving for Merchant Center to re-evaluate, and 3 to 5 days for approvals to settle.

Where the Google fields live in Shopify (Oct 2026):

- Products > a product: title, description, product type, vendor, images, variants (colour, size), price, and Shopify's standard Product category (set it on every product; the channel maps it to a Google category as a baseline).
- Sales channels > Google & YouTube > Products > Bulk editor: the Google specific columns (Google product category, Custom product, Condition, Age group, Gender, Custom label 0 to 4), 25 products a page, no search. These are stored as product metafields in the `mm-google-shopping` namespace.
- Do not uninstall or reinstall the Google & YouTube app (see `02-conversion-tracking.md`).

## Step 1: identifiers on every product (20 minutes)

All 25 products are own brand with no GTIN. In the channel bulk editor set Custom product = Yes on every product (this sends identifier_exists = no). Vendor = Endless Parks on every product so brand fills. GTIN and MPN stay blank. Never type a placeholder GTIN. Every variant needs a SKU in Shopify (Products > variant > SKU), because the Judge.me ratings feed matches on brand plus SKU when there is no GTIN.

A "limited performance" note may remain on bottles and tees even after this, because Google flags categories where most products carry GTINs. The products still serve, and the launch gate accepts that one note. Only fix further if the warning names another cause (category, apparel attributes, image, price mismatch).

## Step 2: the two advertised products

### Parks Bottle (3 colour variants)

| Field | Set to |
|---|---|
| Google title (not the storefront title, see below) | Australian National and Marine Parks Water Bottle 1.2L Insulated Stainless Steel, Straw Lid, Park Sticker Pack |
| Description, first 160 characters | 1.18L double walled insulated stainless steel water bottle showing Australia's National and Marine Parks, with a straw lid and 45 weatherproof park stickers included. Keeps drinks cold 24 hours and hot 18 hours. Tick off every park you visit. Hand drawn in Australia by Endless Parks, shipped from Perth. 30 day returns. (Claims match the live product page, read 15 Oct 2026: 1.18L, 45 stickers on 3 sheets, straw lid with handle, 24 hours cold, 18 hours hot) |
| Shopify product category | Home & Garden > Kitchen & Dining > Food & Beverage Carriers > Water Bottles |
| Google product category | 3809 (same path) |
| Product type | Water Bottle |
| Custom product | Yes |
| Condition | New |
| Colour per variant | Deep ocean, Forest, Sand as the variants are named in Shopify (the colour attribute carries it, so the title does not need it) |
| Material | Stainless steel |
| Custom label 0 / 1 / 2 | hero / xmas-gift / 50to100 |

Only the first 70 or so characters of a title show, so the park words and "Water Bottle 1.2L" come first. No price, shipping or promo words in titles. Keep "Parks Bottle" and "Ultimate Adventure Bottle" in the description so brand queries still match.

Do not rename the Shopify product itself. The Shopify title is the page heading, the cart and order email line, the SEO title and the title Meta's catalogue ads use, and Meta at A$150 a day runs off the same catalogue. Set the Google title one of two ways, Jake's choice:

- Preferred: a supplemental data source in Merchant Center (Settings > Add-ons > Advanced data source management, then Products > Data sources > Add supplemental data source, a Google Sheet). `feed/supplemental-feed.csv` is ready to paste into that sheet: one row per live variant (52 rows, built from the store's product IDs on 15 Oct 2026) with id in the channel's offer id form shopify_AU_<productid>_<variantid>, the Google title, custom labels 0 to 2, product type, Google product category and identifier_exists. Before uploading, open one row in Merchant Center > Products and confirm the id format matches exactly; if the channel uses a different prefix, replace it in the sheet. A supplemental source sits above the Shopify sync and survives every resync, which also means the custom labels and product types do not depend on whether the Shopify bulk editor exposes them.
- Fallback if the add on is not available: a shorter compromise Shopify title that keeps the brand name first for Meta and the park words early for Google: "Parks Bottle 1.2L, Australian National and Marine Parks Water Bottle". Jake approves this before it is saved.

Tee titles get the same treatment: supplemental source rows, or the compromise form "<Design> Tee, Australian Made, National and Marine Parks".

### Aussie Made tees (4 designs, sizes XS to XXL)

| Field | Set to |
|---|---|
| Google titles (one per design) | Stirling Stamps T-Shirt, Australian Made Unisex Tee, National and Marine Parks Print, Endless Parks. Our Backyard T-Shirt, Australian Made Unisex Tee, National and Marine Parks Print, Endless Parks. Bluff Knoll T-Shirt, Australian Made Unisex Hiking Tee, Stirling Range Print, Endless Parks. Adventure Club T-Shirt, Australian Made Unisex Tee, National and Marine Parks Print, Endless Parks |
| Description (per design, swap the first words) | Stirling Stamps T-Shirt by Endless Parks. Australian made, 100% raw cotton, oversized crew neck, celebrating Australia's National and Marine Parks. Unisex fit, sizes XS to XXL. Part of Drop 01. Shipped from Perth, 30 day returns. (The live tee pages say "Australian-made 100% raw cotton" and "oversized crew neck"; "certified" stays out until the Australian Made licence is confirmed) |
| Shopify product category | Apparel & Accessories > Clothing > Shirts & Tops |
| Google product category | 212 |
| Product type | T-Shirt |
| Custom product | Yes |
| Age group | Adult |
| Gender | Unisex |
| Size per variant | XS, S, M, L, XL, XXL |
| Colour per variant | the tee colour, which Jake supplies (the live products have a Size option only, so colour is one value per design) |
| Material | Cotton (the live pages say 100% raw cotton) |
| SKU | Every tee variant needs one; the live store has none on the tees (the bottle, mugs and lids have SKUs) |
| Custom label 0 / 1 / 2 | apparel / evergreen / 50to100 |

Apparel needs colour, size, age group and gender on every variant or Merchant Center disapproves it.

## Step 3: products that stay out of paid ads

Mugs (category 2169), stickers (Decorative Stickers path) and lids (leave Shopify's own category mapping, the drinkware accessories path, not 3809) stay in the feed for free listings. Set Custom label 0 = excluded on each, give each a product type (Mug, Stickers, Lid). The Shopping campaign excludes them through its product groups (`04-campaign-build.md`), which is campaign scoped and leaves free listings running. Never untick the Google & YouTube channel on a product to exclude it: that removes it from free listings too.

Trap found on the live store (15 Oct 2026): the three State Adventure Mugs currently carry the product type "Water Bottle", the same as the bottle, and the tees, stickers and lids have no product type at all. If the campaign is built on the product type fallback before this is fixed, the Water Bottle group advertises nine mug variants at the bottle's A$1.10 bid. Change the mugs to "Mug" in Session 2 before anything else.

One more product to handle: "Shipping protection + free returns" (/products/shipping-protection-free-returns) is a cart add on, not a product. Untick the Google & YouTube channel on that one product so it never reaches Merchant Center; Google disapproves service style items.

## Step 4: shipping, tax and business settings (15 minutes)

1. Shipping: the free standard shipping over A$120 is a checkout discount in Shopify and does not sync, so set shipping manually. Shopify > Google & YouTube > Settings > Shipping: choose manual set up in Merchant Center. Then Merchant Center > Settings > Shipping and returns > Add shipping service > Australia: flat rate A$14, free shipping over A$120, handling 0 to 1 business days, transit 2 to 8 business days. Add a second service Express A$19, transit 1 to 4 days. Stickers alone ship for A$2.50 but are not advertised; overstating their shipping at A$14 is allowed, understating is not.
2. Returns: Merchant Center > Settings > Shipping and returns > return policy 30 days, linked to the refund policy page.
3. Tax: nothing to set. Merchant Center tax settings are US only. Keep Shopify > Settings > Taxes and duties > Include tax in prices on, so the feed price and the page price both show GST inclusive A$87.
4. Merchant Center > Settings > Business information: address 4/16 Ledgar Rd, Balcatta WA 6021, phone, customer service email, logo, website claimed and verified. Make sure the contact details, shipping policy and refund policy are reachable from the site footer. These are the misrepresentation checks.
5. Merchant Center > Settings > Automatic improvements (or Automations): leave automatic item updates ON. They correct price and availability from the page's structured data when the feed lags, which is what stands between a Shopify sync delay and a price mismatch disapproval, and matters most at BFCM when the sale price changes. Leave image improvements on. Only if a separate automatic title improvements toggle exists on screen, switch that one off; do not hunt for it.
6. Merchant Center > Products > a bottle variant > Marketing methods: Shopping ads and Free listings both ticked. An account that only ever used free listings can have products enrolled in free listings alone, and the campaign then shows everything Not eligible with no obvious cause. If Shopping ads is missing, tick it on the Shopify data source (Products > Data sources > the Shopify source > Marketing methods).

## Step 5: product ratings (15 minutes)

Google needs at least 50 reviews across the account to show stars (Merchant Center Help 14549080, read in full), the data source must be refreshed at least monthly, and the review domain must match the Merchant Center domain; the bottle's 99 reviews clear the threshold. Judge.me is an approved partner but only on its Awesome plan via API feed (its help article updated 9 Oct 2026 says XML feed users must switch to the API feed by 15 Jan 2027, and that reviews flow through Judge.me's central account, so they will not show inside Merchant Center itself). Judge.me admin > Settings > Integrations > Google Shopping > enable, API feed, Merchant Center ID 5382740922. With no GTINs the match runs on brand plus SKU, so every product needs a SKU in Shopify. Then Merchant Center > Settings > Add-ons > Product ratings > Get started. Google's own page says onboarding review takes a few weeks and stars go live 2 to 4 weeks after approval, so start this in the first week to have stars before the Christmas window.

## Step 6: promotions (later)

Merchant promotions are available in Australia. Use one only for 25 Nov to 1 Dec: Merchant Center > Marketing > Promotions > Add promotion, submitted by 20 Nov because review can take more than a day. A free shipping threshold is not a discount and already shows as a free delivery annotation from the shipping service in Step 4, so no evergreen promotion is needed.

## Step 7: images

Main image per variant: the bottle on a plain background, no text, badge, watermark or border, at least 800 by 800 pixels (a universal 500 by 500 minimum arrives on 31 Jan 2027). Lifestyle and in use shots go in the additional images (up to 10). Tees: an on model shot is fine as the main image. Meta style statics with headline text baked in will be disapproved.

## Step 8: check in Merchant Center before building campaigns

Products > All products > filter Approved. Required: 3 bottle variants and every tee variant Approved. Also fix:

- Price or availability mismatch: compare the feed with the product page after 24 hours; old pages still showing A$58 or A$63 must be fixed or redirected (see `PLAN.md` open questions).
- Missing apparel attribute: fill colour, size, age group, gender.
- Promotional overlay or image too small: replace the main image.
- Needs attention on the account: Business information or policies missing. One review request per 7 days.
