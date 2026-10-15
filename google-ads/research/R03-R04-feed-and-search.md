# R03 and R04: Merchant Center feed and Search campaigns for Endless Parks

Research date: 15 Oct 2026. Author: Google Ads research pass (Lens A feed, Lens B Search). Builds on R01 (architecture) and the brief; does not repeat R01 conclusions.

Method note: 29 WebSearch (extended) passes against Google Ads Help, Merchant Center Help, Shopify Help Center, Search Engine Land, Optmyzr, Store Growers, ZATO, Haus, JumpFly and Shopify Community. All 14 attempts to fetch pages directly (support.google.com, help.shopify.com, zatomarketing.com, judge.me, searchengineland.com) were blocked by this session's egress proxy (403 on CONNECT, DNS failure in WebFetch), so quotes below come from search-engine extracts of those pages rather than full page reads. Where that limits confidence I say so. Nothing below should be executed without Jake confirming the live UI label, which can differ from the extract.

## 1. Findings

### Lens A: Merchant Center and product feed

1. **identifier_exists = no (false) is correct for every Endless Parks product, and brand = "Endless Parks" stays in.** Google's identifier_exists page: "If your product is new ... and it doesn't have assigned product identifiers that meet the requirements, you should submit the identifier exists attribute with a value of no or false." Google's data-quality page says a manufacturer or own-brand seller "can submit the store name as the brand", and that placeholder GTINs ("0000") and SKUs used as MPNs cause disapprovals. Submit no GTIN and no MPN. Setting identifier_exists = no on a product that really has a GTIN is treated as a quality issue, which does not apply here. Source: support.google.com/merchants/answer/6324478 and /13693497 via search extract; spaceads.agency 2025. Confidence: High on the rule, Med on brand retention (third-party sources conflict; Google's own text supports keeping brand).

2. **"Limited performance" can persist on bottles and tees even after identifier_exists = no, and that is acceptable.** Google's data-quality page: "products with identification issues, such as a missing GTIN or MPN, have limited performance" and "custom-made products ... don't need a GTIN". Practitioners (FeedArmy, Store Growers) note a category-based check since June 2021 that flags categories where most products carry GTINs (water bottles and tees both qualify). Products still serve; they are just deprioritised against GTIN-bearing competitors. Fix list for other causes: invalid google_product_category, missing apparel attributes (colour, size, age_group, gender), image quality, price or availability mismatch with the landing page. Re-evaluation takes 24 to 48 hours after a feed update. Source: support.google.com/merchants/answer/13693497; feedarmy.com; storegrowers.com/google-merchant-center-errors. Confidence: High.

3. **Where to set it in Shopify.** The Google & YouTube channel stores Google-specific fields as product metafields in the `mm-google-shopping` namespace (keys include `google_product_category`, `custom_label_0` to `_4`, `condition`, `age_group`, `gender`, `mpn`, and `custom_product`, which is the Shopify name for identifier_exists). Path in Oct 2026: Shopify admin > Sales channels > Google & YouTube > Products (product status list) > Bulk editor, which exposes the Google columns 25 products at a time with no search. Fallback: Shopify admin > Products > bulk editor, add columns by appending `metafields.mm-google-shopping.custom_label_0` (etc.) to the bulk editor URL (community workaround, unofficial). Shopify's native Product category (standard taxonomy) is auto-mapped to google_product_category by the channel; set it on every product as a baseline. Third-party feed apps are not needed for a 25-product catalogue. Source: community.shopify.com threads 414075, 2443584, 12481; surfient.com; ecomposer.io; help.shopify.com product-category page. Confidence: Med (no 2026 Shopify doc retrieved; community posts from 2024 and 2025 agree).

4. **Shopify is the source of truth and overwrites Merchant Center.** Shopify Help Center: "If you already have a product feed set up, then it's overwritten to avoid conflicts between your Shopify store and your Merchant Center account." Google's "Syncing your products" page: products "continue to sync automatically when any information changes" and product data edits should be made "through the individual product pages or the bulk editor" in Shopify. Community reports conflict on whether manual edits in the Merchant Center product editor survive: one Shopify staff-style answer says they persist until the product is removed and re-added; a Feb 2026 thread reports titles reverting. My read: never edit products inside Merchant Center; edit in Shopify, or layer changes on top via attribute rules or a supplemental data source (which sit above the Shopify data source and survive syncs). Source: help.shopify.com/en/manual/online-sales-channels/google/requirements; support.google.com/merchants/answer/13693394; community.shopify.com 589194, 316079. Confidence: High on overwrite rule, Med on editor persistence.

5. **Merchant Center Next renamed everything and gated rules behind an add-on.** "Feeds" are "data sources", "feed rules" are "attribute rules", supplemental feeds are "supplemental data sources". Both attribute rules and supplemental sources require the "Advanced data source management" add-on: Merchant Center Next > Settings (gear) > Add-ons > Advanced data source management > Add. Then Products > Data sources > Add supplemental data source (Google Sheet is fine; needs an `id` column matching the Shopify item id, format `shopify_AU_<productid>_<variantid>`). Legacy Content API for Shopping was shut down in Aug 2026 (dates conflict: 18 Aug per one source); irrelevant to the Shopify channel, which already uses the Merchant API. Source: zatomarketing.com (MC Next supplemental feeds), storegrowers.com/google-merchant-center-feed-rules, jumpfly.com, datafeedwatch.com. Confidence: Med-High.

6. **Title rules.** 150 characters maximum, truncated beyond that; "users will usually notice only the first 70 or fewer characters of your title, depending on screen size"; no promotional text (price, sale, shipping), no all-caps, no extra spaces. Front-load product type and the matching keywords; brand at the end for an unknown brand (the brand attribute carries it anyway); for apparel the conventional order is Brand, Gender, Product type, Attributes (colour, size), which is third-party convention not a Google rule. Source: support.google.com/merchants/answer/6324415 extract; storegrowers.com/product-title-attribute; zatomarketing.com title options. Confidence: High.

7. **google_product_category IDs.** Water bottle: `3809` (Home & Garden > Kitchen & Dining > Food & Beverage Carriers > Water Bottles). Tees: `212` (Apparel & Accessories > Clothing > Shirts & Tops). Mugs (excluded from ads but in feed): `2169` (Home & Garden > Kitchen & Dining > Tableware > Drinkware > Mugs) [Med, from taxonomy memory, verify in taxonomy.en-AU.txt]. Stickers: `5083`? Not verified; use the full path "Arts & Entertainment > Hobbies & Creative Arts > Arts & Crafts > Art & Crafting Materials > Embellishments & Trims > Decorative Stickers" or Shopify's auto-map. Submit either ID or full path, never both. Source: productcategory.net (3809), developers.facebook.com GPC mapping (212), google.com/basepages/producttype/taxonomy.en-AU.txt. Confidence: High for 3809 and 212, Med for the rest.

8. **custom_label.** Five labels (0 to 4), 100 characters each, up to 1,000 unique values per label per account. For this catalogue: `custom_label_0` = campaign role (`hero`, `apparel`, `excluded`), `custom_label_1` = season (`xmas-gift`, `evergreen`), `custom_label_2` = price band (`under50`, `50to100`), `custom_label_3` = margin tier when Jake's table lands (`high`, `mid`), `custom_label_4` free. Source: support.google.com/merchants/answer/6324473 (not fetched; limits are long-standing). Confidence: High.

9. **Exact way to exclude mugs, stickers and lids from Standard Shopping while keeping them in free listings.** In Google Ads: Campaigns > (Shopping campaign) > Ad groups > Product groups > click the "+" on "All products" > Subdivide by "Custom label 0" > add `hero` and `apparel` as units > the auto-created "Everything else in All products" row: set bid column to "Excluded". Google's note: "Everything else product groups ... can only be removed by deleting their parent subdivisions", which is why you exclude rather than delete. Product group exclusions are campaign-scoped and do not touch Merchant Center destinations, so free listings continue. Do NOT untick the Google & YouTube channel on the product in Shopify: that removes it from the feed entirely, including free listings. If you ever need a feed-level exclusion from ads only, the attribute is `excluded_destination = Shopping_ads` (values: Shopping_ads, Display_ads, Free_listings, Free_local_listings, Local_inventory_ads, Youtube_merchandise, etc.), applied by attribute rule or supplemental source; it keeps Free_listings live and "excluded destination value will always take precedence over the included destination value". `feed_label` is not a practical exclusion tool here: the Shopify channel sets it to the target country and a second label needs a second data source. Source: support.google.com/google-ads/answer/6275322 extract; support.google.com/merchants/answer/6324486; feedarmy.com exclusion guide; community.shopify.com 1555958. Confidence: High.

10. **Images.** Minimums today: 100 x 100 px non-apparel, 250 x 250 px apparel; a universal 500 x 500 px minimum applies from 31 Jan 2027 with warnings in Merchant Center since 14 Apr 2026 (single source, Low). Main image rules: no promotional text, overlays, watermarks, borders or placeholder graphics; product must be the clear subject. For apparel, on-model shots are acceptable and often preferred as the main image. Lifestyle shots are allowed as `image_link` in Google's policy as long as the product is clearly visible, but the common disapprovals are "Promotional overlay on image", "Image too small", "Generic image" and text baked into the image (Meta-style statics with headlines will be disapproved). Put lifestyle and in-use shots in `additional_image_link` (up to 10) and keep a clean product-on-plain-background as the main image for the bottle. Google's "Automatic image improvements" (Merchant Center Next > Settings > Automatic improvements) can crop minor overlays and avoid disapproval. Source: support.google.com/merchants/answer/6324350 extract; nightjar.so 2026 guide; skuanalyzer.com 2026; gmccheck.com 2026. Confidence: Med-High.

11. **Shipping for AU.** Two paths. (a) Shopify channel: Google & YouTube app > Settings > Product feed section > Shipping information > "Automatically import shipping information". Only the General shipping profile syncs; custom profiles "will sync incorrectly ... and cause errors"; AU is supported for carrier-calculated rates. The free-over-A$120 rule is a checkout discount, not a shipping rate, so it will not sync; the A$2.50 sticker letter rate is a conditional rate that may also not sync cleanly. (b) Manual: Merchant Center Next > Settings > Shipping and returns > Add shipping service > Australia > "Flat rate" A$14 standard, add "Free shipping over a specific order value" at A$120, handling time 0 to 1 business days, transit 2 to 8 business days; optionally a second service "Express" A$19, transit 1 to 4 days. Recommendation: choose (b) manual and set the app to "Manually set up shipping settings in Google Merchant Center", because the threshold is the thing Google needs to show the "Free delivery" annotation and overstating sticker shipping at A$14 is allowed (overstating is fine, understating is misrepresentation). A community workaround (custom_label plus shipping label filter under the Advanced data source add-on) exists if stickers ever get advertised. Source: help.shopify.com/en/manual/online-sales-channels/google/requirements; support.google.com/merchants/answer/14232591 and /12577710 extracts; ilanadavis.com; community.shopify.com 579441. Confidence: High on paths, Med on threshold not syncing (no official line found either way).

12. **Tax.** For Australia, "the price attribute should include any VAT or GST, and the landing page price must match the price in your product data". Merchant Center tax settings only apply to the US; nothing to configure for AU. In Shopify keep Settings > Taxes and duties > "Include tax in prices" on and the Australia market "tax included" on so the crawler sees the GST-inclusive price. Source: support.google.com/merchants/answer/7052209 extract; community.shopify.com 98158 and 401893. Confidence: High.

13. **Product ratings (Judge.me to Google).** Google requires "a minimum of 50 reviews across all of their products" in the ratings feed, a full feed at least monthly, and "ratings can take up to 2 weeks to appear" after onboarding. A per-product minimum of 3 reviews to show stars is widely repeated but only third-party. Judge.me is an approved Google review partner; its API feed (Awesome plan) sends reviews through Judge.me's aggregator account, so Jake does not submit a feed himself. Prerequisites: product feed already in Merchant Center, at least 50 eligible product reviews (the bottle's 99 clears it). Steps: Judge.me admin > Settings > Integrations > Google Shopping > enable, select API feed, confirm Merchant Center ID 5382740922; Merchant Center Next > Settings > Add-ons > Product ratings (or "Your business" > Manage programs on older accounts) > Get started. Seller ratings are a separate program (100 reviews, 3.5 stars) and are not in scope. Source: support.google.com/merchants/answer/14549080, /14620705, /6098512 extracts; judge.me/help/en/articles/13845576; stampedsupport. Confidence: High.

14. **Merchant promotions are available in Australia** (current list of 13: Australia, Brazil, Canada, France, Germany, India, Italy, Japan, South Korea, Spain, Netherlands, UK, US). Path: Merchant Center Next > Marketing > Promotions > Add promotion. Use only for BFCM 25 Nov to 1 Dec 2026 (percent off), and consider an evergreen "Free shipping over A$120" promotion, which is a shipping condition not a discount and is consistent with Jake's rule; a shipping service with a free threshold already produces a free-delivery annotation without a promotion. Review can take 24 hours or more; submit the BFCM promotion by 20 Nov. Source: support.google.com/merchants/answer/2906014 extract; storegrowers.com promotions guide; nextflow.biz BFCM 2026 checklist. Confidence: High.

15. **Free listings.** On by default once Merchant Center is set up; products need the same policy compliance as ads plus shipping and returns information. Keep all 25 products in the feed so mugs, stickers and lids earn free clicks. Source: Merchant Center programs overview (storegrowers.com/google-merchant-center-programs; mbadv.agency 2026). Confidence: Med-High.

16. **Misrepresentation and "needs attention" fixes.** Google reviews the site for: business identity (ABN, trading name, physical address 4/16 Ledgar Rd, Balcatta WA 6021, phone or email on a contact page), clear shipping policy, refund policy (30 days is good; make it reachable from the footer), prices and availability matching the feed, secure checkout, no untrustworthy claims. Merchant Center Next > Settings > Business information must carry the address and phone; Settings > Shipping and returns must carry a return policy. "Limited visibility" or account warnings usually resolve within 7 days of fixing and requesting review (one request per 7 days). Source: support.google.com/merchants/answer/6150127 (not fetched; standing policy); simprosys suspension FAQ; datafeedwatch 40 errors. Confidence: Med-High.

### Lens B: Search campaigns

17. **AI Max for Search is on by default for every new Search campaign in Oct 2026, and it can be switched off.** Google Ads Help: "New Search campaigns have the AI Max feature turned on by default ... the setup option is preselected". To disable: Campaigns > Settings > select the campaign > "AI Max" section > toggle "opt out of all AI Max settings". Components: search term matching (ad group level, Ad groups > Search term matching), text customisation and final URL expansion (campaign level, under Asset optimisation; turning off text customisation also disables final URL expansion). Pinned RSA assets are ignored when final URL expansion picks a different URL. Timeline from Search Engine Land 14 Aug 2026: campaign-level broad match and automatically created assets could no longer be created from 3 Aug 2026; existing ones auto-migrated to AI Max 1 to 30 Sep 2026; Dynamic Search Ads migrate Feb 2027. Plain keyword campaigns were not force-migrated. Source: support.google.com/google-ads/answer/15909989 and /15910187 extracts; searchengineland.com/google-sets-ai-max-migration-timeline-for-search-campaigns-485006; ppc.io. Confidence: High.

18. **Brand campaign decision: run it at A$2 to A$3 a day for 30 days as a measurement and protection line, then keep it only on evidence.** Evidence against blanket brand spend: Haus (June 2026) reports a median branded-search incremental ROAS of 0.70x across DTC geo tests and that 50 to 80% of branded paid conversions happen anyway; Two Squares (2026) says brand bidding is defensible mainly when competitors bid, the SERP is crowded, or the brand is emerging. Practitioner thresholds for small brands: under about 50 monthly brand searches, or no competitor in Auction Insights, brand bidding is "lower priority" (stackmatix, JumpFly). Evidence for: cost is tiny (brand CPCs A$0.10 to A$0.50), Search Console hides most brand queries so the campaign is the only clean read on brand demand, and Standard Shopping will show the bottle on "endless parks bottle" queries anyway, so the text ad adds sitelinks (Parks Map, Reviews, Tees) above it. What to do if nobody bids: cap Manual CPC at A$0.40, exact match only (`[endless parks]`, `[endless parks bottle]`, `[endless parks water bottle]`, `[endless parks tee]`, `[endlessparks]`), Presence only, run 30 days, then check Auction Insights. Keep if any competitor domain appears or brand clicks convert above 5% at under A$0.30; if the SERP is uncontested and organic plus free listings already hold it, drop the budget to A$1 (it will underspend) or pause and move the A$3 to non-brand. Never let brand terms leak into the non-brand campaign (add brand negatives there). Source: haus.io "When is branded search worth the investment"; twosquares.co.uk brand search strategy 2026; jumpfly.com; stackmatix.com. Confidence: Med (vendor data is directional; no AU-specific small-brand study found).

19. **Keyword volumes could not be retrieved from any tool in this session** (Semrush, Ahrefs, Ubersuggest and Keywords Everywhere public pages return no AU numbers for these terms; Google Trends is not fetchable here). The figures in the keyword table are practitioner estimates and are marked Low reliability. Keyword Planner inside the new account (set location Australia, last 12 months, "Get search volume and forecasts") is the authoritative free source; it shows exact monthly averages once the account has any spend history, otherwise ranges. One AU SEO agency notes Semrush is more accurate than Ahrefs for low-volume AU terms. Source: seoservices.com.au; neuraplus 2026 AU keyword tools review. Confidence: High that no numbers were retrievable; Low on the estimates.

20. **Match types in 2026.** Exact and phrase both match "same meaning" close variants (misspellings, plurals, reordering, function words, implied intent) with no opt-out. Broad match is Google's recommended default and should only be paired with Smart Bidding; practitioner matrix: broad is "avoid" on Manual CPC, "tolerate" on Maximise conversions, "use" on tCPA or tROAS once a campaign has 30 or more monthly conversions. Brand inclusions (a broad-match-only control that restricts broad keywords to queries containing listed brands) and brand exclusions (PMax, AI Max) remain; irrelevant at launch because the plan uses exact and phrase. Source: storegrowers.com/keyword-match-types (2026); infrontmarketing.ca 2026; lionelz.com 2026. Confidence: High.

21. **Responsive search ads.** Limits unchanged: up to 15 headlines (30 characters), 4 descriptions (90 characters), up to 3 headlines and 2 descriptions shown, pinning to positions 1 to 3 allowed. Optmyzr's 2026 study of about 20,000 accounts: Ad Strength "doesn't predict performance"; partial pinning (one or two positions) beat unpinned and fully pinned ads on CPA, CTR, ROAS and conversion rate; fully pinned ads had the worst CPA. Optmyzr's 2022 study had found unpinned ads slightly better on conversion rate, so treat the direction as "pin lightly, not fully". Google's claim that moving Ad Strength from Poor to Excellent yields 15% more conversions could not be verified. Practical rule: pin one brand or product headline to position 1, pin the key benefit description to position 1, leave the rest free, and ignore "Average" strength. Source: optmyzr.com/blog/google-rsa-performance-study (2026); optmyzr.com/blog/google-ad-strength-study. Confidence: High on limits, Med on study findings.

22. **Assets.** Sitelinks: text 25 chars, two 35-char description lines, at least 2 to serve, Google recommends 4 or more per campaign; callouts: 25 chars, minimum 2, up to 4 show; structured snippets: header plus at least 3 values of 25 chars; price assets: 3 to 8 items with currency (third-party, Med); image assets: account open more than 60 days, good policy history and recent Search spend are needed for automatic images and historically for manual ones too, 1:1 (1200 x 1200) and 1.91:1 (1200 x 628), no text or logo overlays; business name and logo: require Advertiser Verification (Google Ads > Billing/Admin > Advertiser verification, takes days to weeks), name 25 chars and must match the verified legal or domain name, logo 1:1 PNG or JPG, 128 x 128 minimum, 1200 x 1200 recommended, under 5120 KB, must read in light and dark mode and renders in a circle at about 28 px. Source: support.google.com/google-ads/answer/9566341 and /12073962 extracts; support.google.com/adspolicy/answer/12499303; twosquares.co.uk sitelinks 2026; lovesdata.com. Confidence: High for text asset limits, Med for image eligibility (Google page is three years old).

23. **Negative keywords.** Account-level negatives: up to 1,000 per account (Google Ads > Admin > Account settings > Negative keywords); they apply to Search and Shopping. Shared lists: 20 per account, 5,000 per list (some report 10,000 since Sep 2025, unconfirmed). Build one shared list "EP Core Negatives" applied to Shopping and Search, plus "EP Brand" applied only to non-brand. Source: support.google.com/google-ads/answer/2453983 and /7102995 extracts; optmyzr.com negative keywords 2026; adscockpit.io limits 2026. Confidence: High.

24. **Bidding at low volume.** Consensus: start Manual CPC or Maximise clicks with a max CPC cap (traffic and data, not conversions); move to Maximise conversions once conversion tracking is proven, then tCPA when CPA under Max conversions has been stable for a few weeks and the campaign has 20 to 30 conversions a month (Jyll Saskin Gales says 20 to 30; growmyads says 30 in 30 days); tROAS needs at least 15 conversions in 30 days per Google but practically more. One source reports a 17 Aug 2026 change where budget-limited target-based strategies now "optimise more consistently toward the target", meaning a tight tCPA on a small budget throttles entry into auctions harder than before (single source, Low). For Endless Parks: non-brand Search on Manual CPC A$1.00 cap (R01 said about A$1.00) with a watch on "limited by budget"; Shopping follows the R01 ladder. Source: jyll.ca/insidegoogleads/50 and /71; growmyads.com; blackpropeller.com 2026; relevantaudience.com 2026. Confidence: Med-High.

25. **Geo targeting.** Setting lives at Campaign > Settings > Locations > expand "Location options" (labelled "Advanced search" in some views) > Target: choose "Presence: People in or regularly in your targeted locations". Default is "Presence or interest", which lets overseas searchers interested in Australia see ads. Exclusions always use presence. PMax has the same control; Demand Gen splits it. Source: Google Ads Help 1722043 (not fetched); benly.ai 2026; stackmatix 2026; thebrightclick.co.uk. Confidence: High on behaviour, Med on exact label in Oct 2026 UI.

26. **Networks.** Google Ads Help: "When you create a campaign for the Search Network, search partners are included by default. You can opt out ... through your campaign settings." Display Network on Search campaigns (Display Expansion) is no longer pre-ticked in most accounts (Search Engine Land reported Google stopped auto-opting Search campaigns into Display, possibly as a limited test) but the box still exists; untick both at creation: Campaign > Settings > Networks. Context: standalone Display campaigns are being folded into Demand Gen (announced May 2026); channel prioritisation and budget-allocation controls (search partners and Display as "Low" priority with a percentage cap) announced 14 Oct 2026 and rolling out from 15 Oct 2026, as R01 noted; one blog claims Display Expansion on Search ends Feb 2027 (unverified). Google also removed parked domains from the search partner network on 10 Feb 2026. Source: support.google.com/google-ads/answer/1722047 extract; searchengineland.com/google-ads-stops-auto-opting-search-campaigns-into-display-network-457274; ppc.land Jul 2026; relevantaudience.com channel prioritisation. Confidence: High on defaults, Low on the Feb 2027 claim.

27. **Ad schedule.** No practitioner source supports day-parting at under 30 conversions a month; set none at launch. The account time zone is permanent once chosen: pick Australia/Perth so reports align with Jake's day (east-coast customers shift the curve by 2 to 3 hours in reports, which is cosmetic). Review Hour of day after 60 days. Confidence: Med (judgment).

28. **AU Christmas cut-offs 2026 (for the seasonal pull-back).** Australia Post metro last-send dates: Parcel Post 21 Dec interstate, 22 Dec same state; Express Post 23 Dec; WA, NT, TAS and regional need extra days. Endless Parks ships standard 2 to 8 business days from Perth, so the realistic "order by" for east-coast standard delivery is about 14 Dec; express about 20 Dec. Confirm on auspost.com.au/christmas. Source: region.com.au (Oct 2026); sbs.com.au 2026 cut-off article. Confidence: Med.

## 2. Per-product feed table

Brand attribute = "Endless Parks" on every row. GTIN and MPN blank on every row. condition = new. All prices GST inclusive, AUD. Item ids follow the channel format `shopify_AU_<productid>_<variantid>`.

| Product (variant) | Proposed title (chars) | google_product_category | product_type | custom_label_0 / 1 / 2 | identifier_exists | Notes |
|---|---|---|---|---|---|---|
| Parks Bottle, Deep Ocean | Australian National and Marine Parks Water Bottle 1.2L Insulated Stainless Steel, Straw Lid, Park Sticker Pack, Deep Ocean (119) | 3809 | Drinkware > Insulated Water Bottles | hero / xmas-gift / 50to100 | no | colour = Deep Ocean; material = stainless steel; size (capacity) in title |
| Parks Bottle, Forest | same pattern ending ", Forest" (115) | 3809 | Drinkware > Insulated Water Bottles | hero / xmas-gift / 50to100 | no | colour = Forest |
| Parks Bottle, Sand | same pattern ending ", Sand" (113) | 3809 | Drinkware > Insulated Water Bottles | hero / xmas-gift / 50to100 | no | colour = Sand |
| Stirling Stamps tee (per size) | Stirling Stamps T-Shirt, Australian Made Unisex Tee, National and Marine Parks Print, [Colour], Size [XS to XXL], Endless Parks (about 118) | 212 | Apparel > T-Shirts > Australian Made | apparel / evergreen / 50to100 | no | age_group = adult; gender = unisex; colour and size required per variant |
| Our Backyard tee | Our Backyard T-Shirt, Australian Made Unisex Tee, National and Marine Parks Print, [Colour], Size [S], Endless Parks | 212 | Apparel > T-Shirts > Australian Made | apparel / xmas-gift / 50to100 | no | as above |
| Bluff Knoll tee | Bluff Knoll T-Shirt, Australian Made Unisex Hiking Tee, Stirling Range Print, [Colour], Size [S], Endless Parks | 212 | Apparel > T-Shirts > Australian Made | apparel / evergreen / 50to100 | no | "hiking tee" supports the hiking t shirt cluster |
| Adventure Club tee | Adventure Club T-Shirt, Australian Made Unisex Tee, Endless Parks Hikes Print, [Colour], Size [S], Endless Parks | 212 | Apparel > T-Shirts > Australian Made | apparel / evergreen / 50to100 | no | as above |
| State Adventure Mugs (WA, NSW, VIC x 3 colours) | Western Australia National and Marine Parks Adventure Mug, Magnetic Lid and Sticker Sheet, [Colour] | 2169 (verify) | Drinkware > Mugs | excluded / xmas-gift / under50 | no | free listings only at launch |
| Sticker bundles, Iconic 45, Aus stickers, mug sheets | e.g. Western Australia National and Marine Parks Weatherproof Sticker Bundle | Decorative Stickers path | Stickers > Park Stickers | excluded / evergreen / under50 | no | free listings only |
| BIG Chug Lid, Chug Lid, Straw, mug magnetic lid | e.g. BIG Chug Lid for the Endless Parks 1.2L Bottle | 3809 (bottle accessories) or Shopify auto-map | Drinkware > Lids & Accessories | excluded / evergreen / under50 | no | free listings only |

Bottle description (first 160 characters carry the weight): "1.2L insulated stainless steel water bottle showing Australia's National and Marine Parks, with a straw lid and the weatherproof park sticker pack included. Keeps drinks cold for 12 hours and hot for 12 hours. 304 stainless, 1180 ml. Tick off every park you visit with the included stickers. Hand drawn in Australia by Endless Parks and shipped from Perth. 30 day returns." (no price, no shipping cost, no promo language; description limit is 5,000 characters.)

Tee description pattern: "[Design] T-Shirt by Endless Parks. Australian Made certified, hand drawn design celebrating Australia's National and Marine Parks. Unisex fit, sizes XS to XXL. [Fabric and weight once confirmed]. Part of Drop 01. Shipped from Perth, 30 day returns."

## 3. Keyword table

Volumes are AU monthly averages estimated from practitioner experience, not tool data (see Finding 19); CPCs are AU estimates for Search. Reliability is Low on every row until Keyword Planner is run inside the account. Ad groups: BOT-Parks (parks and sticker bottle intent), BOT-Generic (big bottle), GIFT (gift intent), TEE-AusMade, TEE-Parks, BRAND.

| Keyword | Intent | Est AU vol/mo | Est CPC A$ | Match | Ad group | Reliability |
|---|---|---|---|---|---|---|
| national parks water bottle | high, product | 20 to 60 | 0.60 to 1.20 | exact + phrase | BOT-Parks | Low |
| national park bottle | high | 10 to 40 | 0.60 to 1.20 | exact | BOT-Parks | Low |
| national parks bottle australia | high, local | 10 to 30 | 0.60 to 1.20 | phrase | BOT-Parks | Low |
| sticker bottle / water bottle with stickers | mid, product | 50 to 150 | 0.50 to 1.00 | phrase | BOT-Parks | Low |
| travel bottle with stickers | mid | 10 to 40 | 0.50 to 1.00 | phrase | BOT-Parks | Low |
| adventure bottle / adventure water bottle | mid, generic | 100 to 300 | 0.70 to 1.50 | phrase | BOT-Parks | Low |
| road trip water bottle | mid | 20 to 60 | 0.60 to 1.20 | phrase | BOT-Parks | Low |
| 1.2l water bottle | mid, spec | 100 to 300 | 0.70 to 1.50 | exact + phrase | BOT-Generic | Low |
| 1.2 litre water bottle | mid, spec | 50 to 150 | 0.70 to 1.50 | phrase | BOT-Generic | Low |
| big water bottle with straw | mid, spec | 150 to 400 | 0.80 to 1.60 | phrase | BOT-Generic | Low |
| large insulated water bottle | mid | 300 to 800 | 0.90 to 1.80 | phrase (watch spend) | BOT-Generic | Low |
| insulated water bottle with straw lid | mid | 200 to 500 | 0.90 to 1.80 | phrase | BOT-Generic | Low |
| stainless steel water bottle australia | mid, broad competition | 500 to 1,500 | 1.00 to 2.00 | exact only, test | BOT-Generic | Low |
| gifts for campers | gift | 300 to 1,000 (Nov peak 3x) | 0.60 to 1.30 | phrase | GIFT | Low |
| gifts for hikers | gift | 300 to 800 (Nov peak) | 0.60 to 1.30 | phrase | GIFT | Low |
| gifts for grey nomads | gift, AU-specific | 50 to 200 (Nov peak) | 0.50 to 1.00 | phrase | GIFT | Low |
| road trip gifts | gift | 100 to 300 | 0.60 to 1.20 | phrase | GIFT | Low |
| gifts for dad who loves camping | gift, long tail | 20 to 100 (Aug/Sep Father's Day, Dec) | 0.60 to 1.20 | phrase | GIFT | Low |
| camping gifts for dad | gift | 100 to 300 | 0.60 to 1.20 | phrase | GIFT | Low |
| christmas gifts for campers / for hikers | gift, seasonal | 50 to 200 each (Nov to Dec only) | 0.70 to 1.40 | phrase, pause Jan | GIFT | Low |
| gifts for 4wd lovers / 4wd gifts | gift | 100 to 300 | 0.60 to 1.20 | phrase | GIFT | Low |
| australian made gifts | gift, values | 500 to 1,500 (Nov peak) | 0.70 to 1.50 | phrase | GIFT | Low |
| australian made t shirts | high, apparel | 300 to 800 | 0.80 to 1.80 | exact + phrase | TEE-AusMade | Low |
| australian made tees | high | 50 to 150 | 0.80 to 1.60 | phrase | TEE-AusMade | Low |
| aussie made clothing / australian made clothing | mid, broad | 1,000 to 3,000 | 0.90 to 2.00 | exact only | TEE-AusMade | Low |
| australian made mens t shirts | high | 100 to 300 | 0.80 to 1.80 | phrase | TEE-AusMade | Low |
| national park t shirt / national parks t shirt | mid | 50 to 200 | 0.60 to 1.20 | phrase | TEE-Parks | Low |
| hiking t shirt australia / hiking tee | mid | 100 to 300 | 0.70 to 1.50 | phrase | TEE-Parks | Low |
| bluff knoll t shirt / stirling range shirt | low vol, exact intent | under 20 | 0.40 to 0.80 | exact | TEE-Parks | Low |
| endless parks (and bottle, water bottle, tee, stickers, endlessparks) | brand | 100 to 400 (guess from 4k sessions) | 0.10 to 0.40 | exact | BRAND | Low |

Launch set (R01 said 10 to 15 queries at A$5/day): take the exact and phrase rows in BOT-Parks, 1.2l water bottle, big water bottle with straw, gifts for campers, gifts for hikers, gifts for grey nomads, australian made t shirts, australian made tees, national park t shirt. Add the GIFT seasonal rows from 10 Nov. Hold the generic bottle rows over 300 volume until Shopping shows which generic queries convert.

## 4. Negative keyword list

Shared list "EP Core Negatives" (apply to Shopping and all Search):
free, printable, pdf, map pdf, wallpaper, download, template, clipart, svg, png, vector, drawing, colouring, coloring, jobs, careers, employment, volunteer, ranger, camping ground, campground, campsite, caravan park, holiday park, booking, bookings, book a site, entry fee, pass, parks pass, permit, weather, map, maps, directions, how to get to, hours, opening hours, walk, walks, trail map, track notes, cheap, cheapest, wholesale, bulk, custom, personalised, personalized, engraved, logo, promotional, kids, baby, toddler, plastic, glass, 500ml, 750ml, 1l, 2l, 2 litre, bpa, filter, filtered, bottle only lid (if lids excluded), replacement, warranty, repair, review, reviews, vs, versus, stanley, yeti, frank green, hydro flask, camelbak, kmart, big w, target, amazon, ebay, temu, shein, redbubble, etsy, uniqlo, bonds, as colour, kathmandu, macpac, anaconda, bcf.
Each state and territory park name on its own (per R01): "kakadu", "uluru", "freycinet", "cradle mountain", "blue mountains", "grampians", "daintree", "karijini", "ningaloo", "wilsons prom", "royal national park", and so on, added as phrase negatives so informational park searches do not trigger the bottle.

Shared list "EP Brand" (apply to non-brand Search only): endless parks, endlessparks, endless park, "endless parks bottle".

Apparel-only negatives on TEE ad groups: hoodie, jumper, singlet, polo, long sleeve, womens dress, hat, cap, workwear, hi vis, uniform, school.

Bottle-only negatives on BOT ad groups: shirt, tee, t shirt, mug, cup, tumbler, flask, thermos (test), kettle.

Account-level negatives (Admin > Account settings): the competitor and marketplace names above, plus "jobs" and "free".

## 5. RSA copy

All headlines 30 characters or fewer, descriptions 90 or fewer (counted). No sale or discount language. "National & Marine Parks" uses the ampersand where 30 characters force it; Jake to confirm he accepts "&" in place of "and" in headlines.

### Bottle ad group (BOT-Parks, BOT-Generic, GIFT share this with headline swaps)

Headlines:
1. Australia's Parks Bottle 1.2L (29) pin 1
2. National & Marine Parks Bottle (30) pin 1 (alternate)
3. Endless Parks Official Store (28) pin 3
4. Tick Off Parks With Stickers (28)
5. 1.2L Insulated, Straw Lid (25)
6. Keeps Cold 12 Hours (19)
7. Park Sticker Pack Included (26)
8. Rated 4.9 From 99 Reviews (25) update monthly
9. Hand Drawn Aussie Designs (26)
10. The Ultimate Adventure Bottle (29)
11. Gift For Campers & Hikers (26) GIFT ad group: pin 2
12. Free Shipping Over $120 (24) Jake to confirm this is allowed as a shipping condition
13. 304 Stainless Steel, 1.2L (25)
14. Ships From Perth, Australia (27)
15. Road Trip & Camping Essential (29)
Spares: Deep Ocean, Forest Or Sand (26); 30 Day Returns (14); Shop Endless Parks (18).

Descriptions:
1. 1.2L insulated bottle showing Australia's National and Marine Parks. Stickers included. (87) pin 1
2. Keeps drinks cold for 12 hours. Straw lid, 304 stainless steel, hand-drawn park designs. (88)
3. Tick off every park you visit with the included weatherproof stickers. Ships from Perth. (88)
4. Rated 4.9 stars by 99 Aussie adventurers. Designed in Australia, 30 day returns. (80)

### Tees ad groups (TEE-AusMade, TEE-Parks)

Headlines:
1. Australian Made T-Shirts (24) pin 1 (TEE-AusMade)
2. Aussie Made Park Tees (20) pin 1 (TEE-Parks alternate)
3. Endless Parks Official Store (28) pin 3
4. Australian Made Certified (25)
5. Hand Drawn Park Designs (23)
6. National & Marine Parks Tees (28)
7. Bluff Knoll & Stirling Tees (27)
8. Sizes XS To XXL (15)
9. Made In Australia, Certified (28)
10. Drop 01: Four New Designs (25)
11. Gift For Hikers & Campers (25)
12. Our Backyard Tee (16)
13. Free Shipping Over $120 (24) same caveat
14. Ships From Perth, Australia (27)
15. Wear Your Favourite Park (24)
Spares: Adventure Club Tee (18); 30 Day Returns (14).

Descriptions:
1. Australian Made certified tees, hand-drawn National and Marine Parks designs, XS to XXL. (88) pin 1
2. Four designs from Drop 01: Stirling Stamps, Our Backyard, Bluff Knoll and Adventure Club. (89)
3. Drawn by hand and made in Australia. Tees for hikers, campers and road trippers. (80)
4. Ships from Perth, 30 day returns. Wear the parks you love and support Co-Exist Australia. (89)

### Brand ad group

Headlines: Endless Parks (13) pin 1; Official Endless Parks Store (28) pin 1 alt; Australia's Parks Bottle 1.2L (29); Australian Made Park Tees (25); Park Stickers & Adventure Mugs (30); Rated 4.9 From 99 Reviews (25); Ships From Perth, Australia (27); Free Shipping Over $120 (24); The Parks Map (13); 30 Day Returns (14); Adventure Club Hikes (20); Hand Drawn In Australia (23). Descriptions: reuse bottle 1 and tee 1, plus "Bottles, tees, mugs and stickers that celebrate Australia's National and Marine Parks." (85) and "Supporting Co-Exist Australia. Ships from Perth with 30 day returns." (67).

## 6. Assets list

- Sitelinks (campaign level, 6): The Parks Bottle (/products/ultimate-adventure-bottle), Aussie Made Tees (/pages/drop-01), The Parks Map (/pages/the-parks-map), Reviews (bottle PDP #judgeme anchor), Shipping & Returns (/policies/shipping-policy), Adventure Mugs (/collections/adventure-mugs, free listings only but fine as a sitelink). Each with two 35-char lines, no promo text.
- Callouts (account level, 6): Australian Made Tees; Keeps Cold 12 Hours; Park Stickers Included; Ships From Perth; 30 Day Returns; Hand Drawn Designs. Add "Free Shipping Over $120" if Jake approves.
- Structured snippets (campaign): header "Styles": Deep Ocean, Forest, Sand; header "Types": Water Bottles, T-Shirts, Mugs, Stickers.
- Price assets (campaign, type "Products"): Parks Bottle A$87, Aussie Made Tee A$69, Adventure Mug A$45, Park Stickers from A$16. Four items clears the 3-item minimum; prices must match the site.
- Image assets: upload 4 square and 4 landscape clean product and lifestyle photos with no text; expect "not eligible" until the account passes the 60-day and spend history checks; Google will also offer dynamic images from the landing page.
- Business name and logo: start Advertiser Verification on day one; business name "Endless Parks" (13 chars); logo 1200 x 1200 PNG, mark centred within a circle-safe area, tested on dark background.
- Lead form, call, app: none. Location asset: none (online only).
- Account-level final URL suffix per R01 (utm_source=google&utm_medium=cpc&utm_campaign={campaignid}&utm_id={campaignid}&utm_content={creative}&utm_term={keyword}).

## 7. Where sources disagree

- Brand attribute with identifier_exists = no: one guide (spaceads 2025) says keep brand and optional MPN; a 2022 Shopify thread says strip brand, MPN and GTIN. Google's own text supports keeping brand for a manufacturer. Read: keep brand, strip GTIN and MPN.
- Lifestyle images as the main image: nightjar (2026) says on-model is preferred for apparel; gmcsuspension (2026) says a lifestyle image where a product-only image is required will be disapproved. Read: clean product shot as image_link for the bottle, on-model for tees, lifestyle in additional images.
- Merchant Center editor edits surviving Shopify syncs: a Shopify community answer says they persist until the product is re-added; a Feb 2026 thread reports reversion. Read: do not rely on it; use attribute rules or a supplemental source.
- Shopify free-shipping threshold syncing to Merchant Center: no source confirms it syncs; one ecommercecircle.com.au guide says configure it in Merchant Center as well. Read: set shipping manually in Merchant Center.
- AI Max September migration: most sources call it mandatory for campaign-level broad match and ACA; one older blog calls AI Max opt-in. Search Engine Land (14 Aug 2026) is the authoritative timeline and confirms the forced scope was narrow.
- Pinning: Optmyzr 2026 favours partial pinning; Optmyzr 2022 found unpinned slightly better on conversion rate. Read: pin positions 1 and 3 only.
- tCPA threshold: 15 (Google), 20 to 30 (Jyll), 30 to 50 (agencies). Read: 20 to 30 per campaign.
- Display Network default on Search: Search Engine Land says Google stopped pre-ticking it (possibly a test); the older help page still describes it as a checkbox under Networks. Read: untick it manually either way.
- Water bottle category ID: 5939 appears in some third-party guides; 3809 is confirmed by productcategory.net and Wikidata against Google's taxonomy. Use 3809.
- Negative keyword list cap: 5,000 official versus 10,000 reported. Irrelevant at this scale.

## 8. Open questions for Jake

1. Tee variant data: colours per design, fabric and weight, fit (unisex or men's), so titles and descriptions can be finalised and `color`, `size`, `gender`, `age_group` set on every variant.
2. Is "Free Shipping Over $120" acceptable in evergreen headlines and callouts (it is a shipping condition, not a discount)? If not, it still shows automatically as a Merchant Center annotation once the shipping service is set.
3. Is "&" acceptable in place of "and" in 30-character headlines ("National & Marine Parks Bottle")?
4. Confirm the Judge.me plan tier (Awesome needed for the Google integration) and whether Judge.me's product IDs match the Shopify channel item ids.
5. Confirm the Google & YouTube channel's current shipping setting (automatic or manual) and whether a Merchant Center shipping service already exists for Australia; and whether a returns policy is set in Merchant Center.
6. Account time zone preference (Australia/Perth recommended; cannot be changed later).
7. Advertiser Verification: which legal entity name and ABN to use, since the business name asset must match it.
8. Whether any competitor currently shows on a Google search for "endless parks" (quick manual check in an incognito window from Perth and from Sydney, which decides the brand campaign size).
9. Run Keyword Planner (Australia, last 12 months) on the 30 keywords in section 3 once the Google Ads account exists and paste the volumes back so the table can be upgraded from Low reliability.
10. Mug category ID (2169) and sticker category path need a one-minute check in taxonomy.en-AU.txt.

## 9. Sources

Accessed 15 Oct 2026 via search extracts (direct fetch blocked in this session).

Google and Shopify primary:
- Identifier exists: https://support.google.com/merchants/answer/6324478
- Fixing data quality violations: https://support.google.com/merchants/answer/13693497
- Title: https://support.google.com/merchants/answer/6324415
- Google product category: https://support.google.com/merchants/answer/6324436 and https://www.google.com/basepages/producttype/taxonomy.en-AU.txt
- Custom label: https://support.google.com/merchants/answer/6324473
- Image link: https://support.google.com/merchants/answer/6324350
- Excluded destination: https://support.google.com/merchants/answer/6324486
- Tax information: https://support.google.com/merchants/answer/7052209
- Shipping for Shopify users: https://support.google.com/merchants/answer/14232591 and account shipping https://support.google.com/merchants/answer/12577710
- Syncing your products (Shopify): https://support.google.com/merchants/answer/13693394
- Product Ratings eligibility, basics, policies: https://support.google.com/merchants/answer/14549080, /14620705, /6098512
- Promotions data specification: https://support.google.com/merchants/answer/2906014
- Misrepresentation: https://support.google.com/merchants/answer/6150127
- Shopify Google & YouTube requirements: https://help.shopify.com/en/manual/online-sales-channels/google/requirements
- Shopify product category: https://help.shopify.com/en/manual/products/details/product-category
- Judge.me Google Shopping integration: https://judge.me/help/en/articles/13845576
- AI Max set up and how it works: https://support.google.com/google-ads/answer/15909989 and /15910187
- Final URL expansion: https://support.google.com/google-ads/answer/16230205
- Search Network and partners: https://support.google.com/google-ads/answer/1722047
- Display Expansion on Search: https://support.google.com/google-ads/answer/7193800
- Image assets for Search: https://support.google.com/google-ads/answer/9566341
- Use as many asset types as possible: https://support.google.com/google-ads/answer/12073962
- Business information requirements: https://support.google.com/adspolicy/answer/12499303
- Negative keyword lists and campaign negatives: https://support.google.com/google-ads/answer/2453983 and /7102995
- Bulk changes to Shopping campaigns (Everything else note): https://support.google.com/google-ads/answer/6275322

Practitioner and press:
- Search Engine Land, AI Max migration timeline (14 Aug 2026): https://searchengineland.com/google-sets-ai-max-migration-timeline-for-search-campaigns-485006
- Search Engine Land, Google stops auto-opting Search into Display: https://searchengineland.com/google-ads-stops-auto-opting-search-campaigns-into-display-network-457274
- Search Engine Land, AI Max explainer: https://searchengineland.com/ai-max-for-search-everything-you-need-to-know-462923
- Optmyzr RSA performance study (2026): https://www.optmyzr.com/blog/google-rsa-performance-study/ and Ad Strength study https://www.optmyzr.com/blog/google-ad-strength-study/
- Optmyzr negative keywords 2026: https://www.optmyzr.com/blog/negative-keywords/
- Haus, when is branded search worth it: https://www.haus.io/blog/when-is-branded-search-worth-the-investment
- Two Squares brand search strategy 2026: https://twosquares.co.uk/blog/brand-search-strategy and sitelinks https://twosquares.co.uk/blog/google-ads-sitelinks
- JumpFly brand bidding: https://www.jumpfly.com/blog/why-you-should-bid-on-your-brand-name-and-when-you-shouldnt/ and MC Next supplemental feeds https://www.jumpfly.com/blog/setting-up-supplemental-feeds-in-google-merchant-center-next-part-2-of-3/
- Stackmatix branded search: https://www.stackmatix.com/blog/branded-search-campaigns
- ZATO, supplemental feeds and rules in MC Next: https://zatomarketing.com/blog/how-to-add-supplemental-feeds-and-feed-rules-in-google-merchant-center-next
- Store Growers: attribute rules https://www.storegrowers.com/google-merchant-center-feed-rules/, errors https://www.storegrowers.com/google-merchant-center-errors/, match types 2026 https://www.storegrowers.com/keyword-match-types/, promotions https://www.storegrowers.com/google-merchant-center-promotions/, product ratings https://www.storegrowers.com/product-ratings-in-google-shopping/
- Jyll Saskin Gales, Inside Google Ads ep 50 and 71: https://jyll.ca/insidegoogleads/50 and https://jyll.ca/insidegoogleads/71
- FeedArmy, exclude products and limited performance: https://feedarmy.com/kb/how-do-i-remove-products-in-google-shopping-adwords-campaigns/ and https://feedarmy.com/kb/fix-limited-performance-due-to-missing-value-gtin-in-google-merchant-center/
- Space Ads, GTIN and identifier_exists: https://www.spaceads.agency/blog/gtin-identifier-exists-google-merchant-center
- Nightjar image requirements 2026: https://nightjar.so/blog/google-shopping-image-requirements; SKU Analyzer overlays: https://skuanalyzer.com/guides/google-shopping/image-overlays/
- Ilana Davis, Google channel shipping sync: https://www.ilanadavis.com/blogs/articles/new-google-sales-channel-settings-for-shipping-sync-in-shopify
- Shopify Community threads: 12481 (identifier_exists), 414075 (bulk editor for Google fields), 2443584 (custom labels missing), 579441 (custom shipping profiles), 589194 (sync overwrites), 316079 (Content API overwriting), 1555958 (exclude from feed), 98158 (GST inclusive)
- Surfient, Google product category metafield: https://www.surfient.com/guides/shopify-google-product-category
- Product category 3809: https://productcategory.net/finder/home-and-garden/kitchen-and-dining/food-and-beverage-carriers/water-bottles/; 212: https://developers.facebook.com/documentation/ads-commerce/commerce-platform/catalog/categories/google-product-category-to-facebook-product-category
- ppc.io AI Max controls: https://ppc.io/blog/ai-max-google-ads
- Relevant Audience, channel prioritisation (Oct 2026): https://www.relevantaudience.com/google-ads-en/google-ads-channel-prioritization-budget-allocation/; bidding 2026: https://www.relevantaudience.com/google-ads-en/google-ads-bidding-strategies-guide/
- PPC Land, PMax partner and Display opt-out (Jul 2026): https://ppc.land/google-lets-some-pmax-advertisers-switch-off-search-partners-and-display/
- Grow My Ads, Max conversions to tCPA: https://growmyads.com/switch-from-maximize-conversions-to-target-cpa/
- NextFlow, Merchant promotions BFCM 2026: https://www.nextflow.biz/insights/google-merchant-center-promotions-black-friday-2026
- Region Media, Australia Post 2026 cut-offs: https://region.com.au/sending-a-parcel-for-christmas-the-final-countdown-has-already-begun/1005693/
- SEO Services AU, Semrush vs Ahrefs for AU data: https://www.seoservices.com.au/ahrefs-semrush-australian-smes-local-data/
