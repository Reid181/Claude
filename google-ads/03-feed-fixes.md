# 03. Feed fixes in Shopify

Shopping ads match on the feed, mostly the title and the Google product category. Shopify is the source of truth: the Google & YouTube channel overwrites Merchant Center on every sync, so every fix is made in Shopify, never in the Merchant Center product editor. Allow 24 to 48 hours after saving for Merchant Center to re-evaluate, and 3 to 5 days for approvals to settle.

Where the Google fields live in Shopify (Oct 2026):

- Products > a product: title, description, product type, vendor, images, variants (colour, size), price, and Shopify's standard Product category (set it on every product; the channel maps it to a Google category as a baseline).
- Sales channels > Google & YouTube > Products > Bulk editor: the Google specific columns (Google product category, Custom product, Condition, Age group, Gender, Custom label 0 to 4), 25 products a page, no search. These are stored as product metafields in the `mm-google-shopping` namespace.
- Do not uninstall or reinstall the Google & YouTube app (see `02-conversion-tracking.md`).

## Step 1: identifiers on every product (20 minutes)

All 25 products are own brand with no GTIN. In the channel bulk editor set Custom product = Yes on every product (this sends identifier_exists = no). Vendor = Endless Parks on every product so brand fills. GTIN and MPN stay blank. Never type a placeholder GTIN.

Expect "limited performance" to remain on bottles and tees even after this: Google flags categories where most products carry GTINs. The products still serve. Only fix it further if the warning names another cause (category, apparel attributes, image, price mismatch).

## Step 2: the two advertised products

### Parks Bottle (3 colour variants)

| Field | Set to |
|---|---|
| Title | Australian National and Marine Parks Water Bottle 1.2L Insulated Stainless Steel, Straw Lid, Park Sticker Pack |
| Description, first 160 characters | 1.2L insulated stainless steel water bottle showing Australia's National and Marine Parks, with a straw lid and the weatherproof park sticker pack included. Keeps drinks cold 12 hours. 304 stainless, 1180 ml. Tick off every park you visit. Hand drawn in Australia by Endless Parks, shipped from Perth. 30 day returns. |
| Shopify product category | Home & Garden > Kitchen & Dining > Food & Beverage Carriers > Water Bottles |
| Google product category | 3809 (same path) |
| Product type | Water Bottle |
| Custom product | Yes |
| Condition | New |
| Colour per variant | Deep Ocean, Forest, Sand (the colour attribute carries it, so the title does not need it) |
| Material | Stainless steel |
| Custom label 0 / 1 / 2 | hero / xmas-gift / 50to100 |

Only the first 70 or so characters of a title show, so the park words and "Water Bottle 1.2L" come first. No price, shipping or promo words in titles. Keep "Parks Bottle" and "Ultimate Adventure Bottle" in the description so brand queries still match. If the long title is wrong for the storefront, check whether the channel bulk editor exposes its own Title column; if it does, set the feed title there and leave the storefront title alone.

### Aussie Made tees (4 designs, sizes XS to XXL)

| Field | Set to |
|---|---|
| Title pattern | <Design> T-Shirt, Australian Made Unisex Tee, National and Marine Parks Print, Endless Parks (Bluff Knoll: "Australian Made Unisex Hiking Tee, Stirling Range Print") |
| Description pattern | <Design> T-Shirt by Endless Parks. Australian Made certified, hand drawn design celebrating Australia's National and Marine Parks. Unisex fit, sizes XS to XXL. <Fabric and weight once confirmed>. Part of Drop 01. Shipped from Perth, 30 day returns. |
| Shopify product category | Apparel & Accessories > Clothing > Shirts & Tops |
| Google product category | 212 |
| Product type | T-Shirt |
| Custom product | Yes |
| Age group | Adult |
| Gender | Unisex |
| Size per variant | XS, S, M, L, XL, XXL |
| Colour per variant | the actual tee colour |
| Material | Cotton (confirm) |
| Custom label 0 / 1 / 2 | apparel / evergreen / 50to100 |

Apparel needs colour, size, age group and gender on every variant or Merchant Center disapproves it.

## Step 3: products that stay out of paid ads

Mugs (category 2169, verify in Google's taxonomy), stickers (Decorative Stickers path) and lids stay in the feed for free listings. Set Custom label 0 = excluded, give each a product type (Mug, Stickers, Lid). The Shopping campaign excludes them through its product groups (`04-campaign-build.md`), which is campaign scoped and leaves free listings running. Never untick the Google & YouTube channel on a product to exclude it: that removes it from free listings too.

## Step 4: shipping, tax and business settings (15 minutes)

1. Shipping: the free standard shipping over A$120 is a checkout discount in Shopify and does not sync, so set shipping manually. Shopify > Google & YouTube > Settings > Shipping: choose manual set up in Merchant Center. Then Merchant Center > Settings > Shipping and returns > Add shipping service > Australia: flat rate A$14, free shipping over A$120, handling 0 to 1 business days, transit 2 to 8 business days. Add a second service Express A$19, transit 1 to 4 days. Stickers alone ship for A$2.50 but are not advertised; overstating their shipping at A$14 is allowed, understating is not.
2. Returns: Merchant Center > Settings > Shipping and returns > return policy 30 days, linked to the refund policy page.
3. Tax: nothing to set. Merchant Center tax settings are US only. Keep Shopify > Settings > Taxes and duties > Include tax in prices on, so the feed price and the page price both show GST inclusive A$87.
4. Merchant Center > Settings > Business information: address 4/16 Ledgar Rd, Balcatta WA 6021, phone, customer service email, logo, website claimed and verified. Make sure the contact details, shipping policy and refund policy are reachable from the site footer. These are the misrepresentation checks.
5. Merchant Center > Settings > Automatic improvements: leave image improvements on (crops minor overlays), turn off automatic title and price improvements so Google does not rewrite the titles above.

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
