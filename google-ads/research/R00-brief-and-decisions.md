# Endless Parks: brief for the Google Ads setup research (15 Oct 2026)

Read this before doing anything. Every fact below is verified from the store, memory or Jake unless marked "assumed".

## The business
- Endless Parks (endlessparks.com), Shopify store f8dc9c-2.myshopify.com, Perth based (warehouse 4/16 Ledgar Rd, Balcatta WA 6021). Currency AUD, prices GST inclusive. Australian spelling in all copy.
- Founders Jake (photography, parks list) and Joce (hand-draws every design); a mate Mitch digitises. Launched 2024 from a granny flat in Cairns, bottles sold out faster than they could restock. Monthly "Adventure Club" hikes. Supports Co-Exist Australia.
- Core idea: products that show off Australia's National AND Marine Parks (always say "National and Marine Parks", never "national parks" alone) and get people out there. Customers tick off parks with stickers as they visit.
- Also sells wholesale to park visitor centres (Kalbarri Visitor Centre, Freycinet National Park). Wholesale orders are draft orders in Shopify and must never be counted as ad-driven.

## Catalogue (live products.json, 15 Oct 2026; all AUD)
- HERO: "Australian National Parks Bottle" (store title; customer-facing "Parks Bottle" / "Ultimate Adventure Bottle"), /products/ultimate-adventure-bottle, $87, colours Deep ocean / Forest / Sand. 1.2 L (PDP says 1180 ml), 304 stainless, keeps hot/cold 12 h, straw lid is the standout in reviews. Ships with the park sticker pack included. Judge.me 4.89 from 99 reviews, 91% five star. Automatic discounts: 2 bottles 20% off, 3 bottles 30% off (store "3x Bottle Bundle" = The Mates Pack).
- State Adventure Mugs $45 each: Western Australia's Adventure Mug, New South Wales Adventure Mug, Victorian Adventure Mug (3 colours each). Magnetic lid and mug sticker sheet included.
- Stickers: State Bundle weatherproof park stickers $16 to $29 (7 state variants), The Iconic 45 National and Marine Park stickers $65, Aus National & Marine Park Stickers $20, mug sticker sheets WA/NSW/VIC $15 each.
- Lids: BIG Chug Lid $15, Chug Lid $15, Straw $15, State mug magnetic lid $12.
- Apparel: 4 "Aussie Made" tees $69 (Stirling Stamps, Our Backyard, Bluff Knoll, Adventure Club), Australian Made certified, sizes XS to XXL. Drop 01 launched 19 Aug 2026.
- Pages: /pages/the-parks-map (interactive parks map with bundle card), bundles page, /pages/drop-01.
- Collections: adventure-mugs, aus-park-stickers, australias-ultimate-adventure-bottle, best-sellsers (sic), shop-all, show-new, featured.
- No GTINs: everything is own-brand custom product (identifier_exists should be false in Merchant Center). product_type is only set on the bottle and mugs ("Water Bottle"), blank elsewhere; no tags.

## Shipping (verified 25 Sep 2026)
- AU Standard $14 (2 to 8 business days), Express $19 (1 to 4). Sticker-only carts $2.50 letter rate. Free standard shipping automatic over $120 (checkout discount).
- NZ $18; US/UK $26 stickers / $45 bottle. Primary market is Australia only.
- Refund policy: 30 day returns. Shipping policy live at /policies/shipping-policy.

## Numbers (Triple Whale + Shopify, 1 to 22 Sep 2026, wholesale excluded)
- Retail: A$5.3k sales, 62 orders, 94 units, retail AOV about A$70 (TW definition) to A$85 (total sales / orders). 77% new customers. Month before (17 Aug to 16 Sep): 4,008 sessions, 65 orders, CVR about 1.6%, Shopify AOV A$143 incl. wholesale.
- Blended new customer CPA A$40, blended ROAS 2.75, MER 36%.
- Email: Klaviyo list 7,720, welcome flow (10% unique codes) and abandoned checkout flow live. Popup offers 10% off.
- Analytics stack: Shopify, GA4 (property tag G-M3LTBNJ7H4 found on the storefront, almost certainly installed by the Shopify Google & YouTube channel), Microsoft Clarity, Triple Whale (pixel + Summary), Judge.me reviews, Klaviyo.

## Meta ads (the paid channel that already runs)
- Account 480054024556299, pixel 2194882384209371 with CAPI. Live campaign ep_asc_bottle_broad_2026q4: one Advantage+ sales campaign, one broad AU 18+ ad set, A$150/day, 8 to 10 ads, all to the bottle PDP.
- Lifetime Meta (Aug 2023 to Sep 2026): A$175,873 spend, 3,863 purchases, CPA A$45.53, ROAS 2.10. Best evergreen CPA A$39. Sep 2026 is running worse: 7 day CPA about A$84, ROAS 1.2 (wholesale excluded).
- Working CPA target A$39 to A$50; break-even CPA not yet given by Jake (margin table pending). Assume gross margin on the $87 bottle is healthy (own brand, direct) but unknown.
- Creative learnings: video and static convert the same; founder-voice "No more USA" (Aussie alternative to US bottle brands) and meme "this doesn't exist" statics are historical winners; UGC hooks well but loses carts.
- UTM convention on every Meta ad: utm_source=facebook&utm_medium=paid_social&utm_campaign={{campaign.name}}&utm_id={{campaign.id}}&utm_content={{ad.name}}&utm_term={{adset.name}}. Google should mirror the pattern with ValueTrack.
- Mugs ads planned from about 20 Oct; Black Friday sale ad set planned 25 Nov to 1 Dec (the only time sale creative is allowed).

## Jake's hard rules
- No sale, discount or "SALE NOW ON" hooks in evergreen ads (BFCM window excepted). The 10% welcome offer is email-only.
- Keep deliverables short; no em dashes anywhere; Australian spelling; "National and Marine Parks".
- Small budget for Google. The exact figure is not confirmed; evaluate three tiers A$15/day, A$30/day and A$50/day (about A$450, A$900, A$1,500 a month) and recommend one. Meta stays the main channel.
- Jake does the hands-on in Google Ads with Claude driving Chrome when needed, so the plan must be executable step by step inside the Google Ads UI, Merchant Center and Shopify admin.

## Google state (what is known and unknown)
- Known: GA4 tag on site; Search Console verified (two google-site-verification metas); Shopify Google & YouTube channel presumably installed because the GA4 tag is served Shopify-side; Jake says a Google Ads account is linked into Shopify.
- Unknown (being checked separately in Shopify admin / Google Ads / Merchant Center): Google Ads customer ID, past Google spend and campaigns, Merchant Center ID and product approval status, conversion actions configured, whether the Google channel's conversion tracking is on, consent mode state, free listings status, GA4 property linkage.
- Search Console organic query data (brand vs non-brand volume) is unknown; treat brand search volume as small (a two year old brand with ~4k monthly sessions).

## Seasonality
- Christmas gifting is the big window for bottles and mugs (gifts for dads, travellers, grey nomads, campers). Shipping cut-offs for AU Christmas delivery matter. BFCM sale 25 Nov to 1 Dec 2026.
- Australian summer holidays (Dec to Jan) and Easter are road-trip peaks. Winter is slower.

## Audience
- Aussies who love their backyard: campers, 4WD and road-trippers, hikers, grey nomads, young couples doing the lap, gift buyers for those people. Broad AU 18+ works best on Meta; narrow interests lost every test.
- Comparable brands: Let's Wander (US national parks sticker bottle), Awesome Maps, MagiqueGift Journey Bottle, The Quest Maps, Go-Roadtrip, Lord of Maps; drinkware incumbents Frank Green, Stanley, Yeti, Hydro Flask, Camelbak; AU outdoor retailers Kathmandu, Macpac, Anaconda, BCF, Snowys, Wild Earth.

## Decisions Jake made on 15 Oct 2026 (after the brief above was written)
- Budget: A$30/day (about A$900/month).
- Google Ads account: unknown whether one exists under endlesspks@gmail.com (the Google account the Shopify channel uses). Neither jake.reid181 nor jakereidmedia has one. Merchant Center account 5382740922 exists. Plan must cover both cases: existing account found, or a new one created.
- Margin: landed cost on the A$87 bottle is about A$16 (product, packaging, shipping). So contribution before ad cost is roughly A$71 per bottle at full price, and about A$57 if the customer pays the A$14 standard shipping (the customer pays shipping under A$120 so shipping is roughly neutral).
- Products at launch: bottle and tees only. Mugs, stickers and lids are excluded from Google at launch.
- Jake does hands-on execution in the Google Ads UI / Merchant Center / Shopify admin, so every step must be executable in those UIs with menu paths.

## Research already completed (R01 architecture, 15 Oct 2026) - key conclusions to build on, do not redo
- Standard Shopping is fully available and not deprecated in Oct 2026 (Google Ads Help 2454022). Since Oct 2024 PMax no longer automatically beats Standard Shopping; highest Ad Rank serves.
- Exact match keyword in a Search campaign beats PMax for that exact query; a brand Search campaign plus a PMax brand exclusion list is the only full brand protection.
- New on 14 to 15 Oct 2026: channel prioritisation and budget allocation controls (Shopping can demote search partners; PMax can set Display and search partners to Low with a percentage cap), rolling out progressively.
- Practitioner thresholds: PMax wants about US$50/day and 30 conversions in 30 days; under about A$3,000/month start with Standard Shopping plus high intent Search (Adgenix, Perth; Store Growers; SavvyRevenue; ZATO).
- Demand Gen is wrong for this budget. AI Max for Search auto-migrated campaigns using campaign-level broad match from 1 Sep 2026; leave AI Max off at launch.
- The Shopify Google & YouTube channel can only create PMax campaigns, auto-creates conversion actions, and Shopify data overwrites Merchant Center; build every campaign inside Google Ads and use the app only for feed sync and conversion tags.
- Recommended at A$30/day: Standard Shopping A$22 (one campaign, product groups by type) + Brand Search A$3 (exact/phrase on endless parks variants, AI Max off) + Non-brand Search A$5 (10 to 15 exact/phrase queries, Manual CPC capped about A$1.00).
- Bidding ladder: Manual CPC or Maximise Clicks with A$1.30 cap for 2 to 4 weeks; Maximise Conversion Value with no target at 15 conversions/30 days; Target ROAS at 30.
- Account settings: location Australia, Presence only; search partners off; no ad schedule or device adjustments at launch; account-level final URL suffix utm_source=google&utm_medium=cpc&utm_campaign={campaignid}&utm_id={campaignid}&utm_content={creative}&utm_term={keyword}.
- Day-one negatives on Shopping and Search: free, printable, wallpaper, map pdf, jobs, camping ground, and each state park name on its own.
- Seasonality: launch Shopping before 1 Nov; raise budgets 20 to 30% from 20 Nov to 15 Dec; Merchant Center promotion only for 25 Nov to 1 Dec; pull back the week before the AU Christmas shipping cut-off.
- Feed fixes needed in Shopify: set product_type on tees (and others), set identifier_exists false on every product, move bottle titles to the "Australian National and Marine Parks Water Bottle 1.2L" pattern.
