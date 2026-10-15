# P1. Benchmarks and budget model for Endless Parks (A$30 a day)

Written 15 Oct 2026. Builds on `google-ads/PLAN.md` and `06-launch-and-optimise.md`: it replaces the two column "What to expect" table with a three case model and corrects the target ROAS. Direct page loads are blocked here, so quotes come from search extracts of the pages named. USD converted at A$1.50 per US$1 (assumed, not verified).

## 1. Findings

1. **Standard Shopping, global (Store Growers data via Foundry CRO and The Ad Spend, 2026).** CPC US$0.66, CTR 0.86 per cent, CVR 1.91 per cent, CPA US$38.87. https://foundrycro.com/blog/google-shopping-benchmarks-by-category-2026/ Med (one dataset, secondary citations).
2. **Shopify and DTC accounts (CorePPC, 500+ accounts, 2026).** Shopping CPC US$0.68, CTR 1.2 per cent, Shopping ROAS 5.1, Search 3.4; Google CPA US$43 to 51 against Meta US$32 to 38. https://coreppc.com/blog/google-ads-benchmarks-ecommerce-2026/ Low to Med (one agency).
3. **Triple Whale (21,000+ brands, 1 Aug 2025 to 31 Jul 2026).** Median Google CPA US$28.14 (up 10 per cent), ROAS 3.27 (down 3.5 per cent), CTR 1.65 per cent, CVR 3.11 per cent; Apparel CPA US$25.40, CVR 2.78 per cent; Sports and Outdoors CPA US$30.42; Home and Garden CPA US$38.94. https://www.triplewhale.com/blog/google-ads-benchmarks Med (blended across brand, non brand and campaign types).
4. **WordStream and LocaliQ 2026 (13,474 US Search campaigns, Apr 2025 to Mar 2026).** E-commerce Search CPC US$1.16, CTR 4.10 per cent, CVR 2.81 per cent. "Shopping, Collectibles and Gifts" CPC US$4.14 (US$3.49 in 2025), CTR 8.28 per cent, CVR 4.01 per cent. https://www.digitalapplied.com/blog/google-ads-benchmarks-2026-cpc-ctr-cvr-industry Med. Gift terms are the dear end of the non brand list.
5. **Apparel Shopping (2026 vendor tables).** CPC US$0.62 to 0.89, CVR 1.2 to 2.8 per cent, ROAS 3.8 to 6.1. https://www.storegrowers.com/google-ads-benchmarks/ Low (four fold spread). No drinkware benchmark exists; Keyword Planner is the only source for bottle CPCs.
6. **Australia.** DNHQ Australian Click Price Index, May 2026: e-commerce median Search CPC A$2.04, clicks up 31 per cent Jan to May 2026. https://digitalnomadshq.com.au/blog/how-much-does-google-ads-cost/ Agencies quote Search A$1.50 to 2.50, Shopping A$0.30 to 2.50. https://www.whitepeakdigital.com/blog/google-ads-cost-australia/ Low (one index, no Australian Shopping dataset).
7. **Cost trend, changed 2025 to 2026.** Channable (10,000+ European e-commerce advertisers, 12 Jul 2026): Shopping and PMax CPC up 15 per cent June 2025 to June 2026, ROAS down 46 per cent on PMax and 43 per cent on Standard Shopping. https://ppc.land/channable-data-shows-advertisers-lose-46-roas-as-google-clicks-cost-more/ Alphabet Q2 2026: Search CPC up 3 per cent. Med. Plan on CPC up 10 to 15 per cent a year and 20 to 30 per cent in the gift season.
8. **Smart Bidding thresholds (Google Ads Help, read Oct 2026).** Target ROAS, answer 6268637: "Search and Shopping campaigns: at least 15 conversions in the past 30 days at the conversion tracking level", values above zero. Shopping setup, answer 6309035: "at least 15 conversions per Merchant Center ID in the last 30 days". Google suggests a target "based on your actual ROAS over the last few weeks". Display guidance (answer 10285843): "at least 30 conversions per month" for consistent results. https://support.google.com/google-ads/answer/6268637 High. The threshold is account level; the plan's per campaign reading is the safer practitioner one.
9. **Label change, June 2026.** Help 15099424: "Maximise conversion value with a Target ROAS" is now "Target ROAS", "Maximise conversions with a Target CPA" is "Target CPA", behaviour unchanged. https://support.google.com/google-ads/answer/15099424 High. `06` should use the new labels.
10. **Practitioner thresholds.** Jyll Saskin Gales: "30 days, 30 conversions" before changing strategy; fund at least 10 clicks a day per campaign. https://learn.jyll.ca/blog/when-and-how-should-you-change-bid-strategies-in-google-ads Store Growers: Manual CPC until 50 conversions, then Target ROAS. https://www.storegrowers.com/target-roas/ Med.
11. **Conversion value the Shopify app sends.** Merchant Center Help 16031492 (2025): the app uses Shopify's `subtotalPrice`, discounts subtracted since a fix around end of April 2025. https://support.google.com/merchants/answer/16031492 From September 2025 EU merchants saw values jump about 21 per cent as tax inclusive totals arrived, with the app managed action's tax setting locked. https://community.shopify.com/t/google-youtube-app-conversion-value-suddenly-includes-vat-august-vs-september/568656 FeedArmy: "total sales value, including VAT or tax, but excluding shipping". https://feedarmy.com/kb/google-youtube-app-for-shopify-now-includes-vat-in-conversion-tracking/ Med. With GST inclusive prices a bottle reports 87.00 either way; only shipping could differ, and the `02` test order (15.00, not 17.50) settles it.
12. **Branded search incrementality.** Stella 2025 DTC benchmarks (225 geo tests, Aug 2024 to Dec 2025): median incremental ROAS branded search 0.70 (lowest), non brand search 1.46 (n=31), Shopping 1.86 (n=16), PMax 2.98, Meta 2.92 (n=63), all channel 2.31. https://www.stellaheystella.com/blog/2025-dtc-digital-advertising-incrementality-benchmarks Google's 390 pause studies (2012): 50 per cent of ad clicks incremental at organic rank 1, 82 per cent at ranks 2 to 4, 96 per cent below 4. eBay (2015): brand substitution near complete, smaller for less known brands. https://ecommercefastlane.com/branded-search-cannibalization-google-ads-roas/ Med (US, vendor data).
13. **Meta feeds Google search.** Brainlabs: across nine Meta lift studies, 31 per cent of incremental search traffic was branded. https://www.brainlabsdigital.com/paid-social-measurement-meta-incrementality-search-lift/ iProspect: Meta exposure lifted search volume 10.4 per cent and paid search 11 per cent. https://www.iprospect.com/en-us/insights/meta-search-lift-to-drive-stronger-media-performance Med (agency run). Meta at A$150 a day creates "endless parks" searches that Google captures or hands to Tiny Treasures Denmark, Amazon or US sellers.
14. **Meta's own incrementality.** Lebesgue geo holdout: pausing Meta cut revenue by about a third of what Meta claimed. https://lebesgue.io/facebook-ads/meta-ads-incrementality-geo-holdout-test Low (one brand). Blended MER is the honest number for both channels.
15. **Geo lift is out of reach.** Google geo Conversion Lift covers Shopping and PMax but needs a rep and, since November 2025, about US$5,000. https://www.cometly.com/post/incrementality-testing-for-paid-advertising A manual state holdout needs comparable orders per state; at about 65 retail orders a month with Perth over indexed, no state is readable. High.

## 2. Exactly what to do for Endless Parks

### 2.1 Unit economics (Google reports value GST inclusive, shipping excluded)

| | Bottle | Tee, A$25 landed | Tee, A$30 landed | Two bottles (A$139.20, free shipping) |
|---|---|---|---|---|
| Google reported value | 87.00 | 69.00 | 69.00 | 139.20 |
| Ex GST revenue | 79.09 | 62.73 | 62.73 | 126.55 |
| Landed cost | 16.00 | 25.00 | 30.00 | 32.00 |
| Card fees, 2 per cent of inc GST price | 1.74 | 1.38 | 1.38 | 2.78 |
| Postage absorbed | 0 (customer pays A$14) | 0 | 0 | about 12.00 |
| Contribution before ads | 61.35 | 36.35 | 31.35 | 79.76 |
| Break even CPA | A$61 | A$36 | A$31 | A$80 |
| Break even ROAS | 1.42 | 1.90 | 2.20 | 1.75 |
| CPA leaving A$10 to 16 profit | A$45 | A$26 | A$21 | A$48 |
| Target ROAS at that CPA | 1.93 | 2.65 | 3.25 | 2.90 |

Blended for a plausible mix (75 per cent single bottle, 15 per cent two bottle, 10 per cent tee): value A$93.03, contribution A$61.36, break even ROAS 1.52, target ROAS 2.02 at a A$46 CPA.

**Number to type in later: Target ROAS 200 per cent** on Shopping (PLAN.md says 190; bundles carry absorbed postage and tees carry thinner margin). Floor 150, ceiling 250. If Google's suggested target is above 250, type 200 anyway. Tees alone would need 265 to 325 and will never earn the volume, so they stay in the campaign on a lower max CPC.

Manual CPC maths (max CPC = CVR times allowed CPA): bottle at 1.3 per cent CVR and A$55 allowed CPA is A$0.72; at 2.0 per cent it is A$1.10. The A$1.10 launch bid in `04` is a bet on 2 per cent CVR; keep it 14 days to buy impression share, then reset bottle max CPC = observed Shopping CVR times A$55 each fortnight. Tee: 1.2 per cent times A$30 = A$0.36, so A$0.40, not A$0.60.

### 2.2 Model at A$30 a day (A$669 Shopping, A$91 brand, A$152 non brand per 30.4 day month)

Month 1 = 27 Oct to 26 Nov (no history), Month 2 = 27 Nov to 26 Dec (gift season: CPC up 15 to 25 per cent, CVR up), Month 3 = 27 Dec to 26 Jan (road trips, cheaper clicks). Spend held flat so cases compare; the November budget lift in `07` scales orders in proportion. Google reported AOV A$87, 90, 95 by case. All platform reported; incrementality adjustment is in 2.5.

| Campaign and case | CPC M1, M2, M3 / CVR M1, M2, M3 | M1 clicks / orders / CPA / ROAS | M2 | M3 |
|---|---|---|---|---|
| Shopping, conservative | 1.05, 1.10, 1.00 / 0.7, 0.9, 0.8 per cent | 637 / 4.5 / A$150 / 0.58 | 608 / 5.5 / A$122 / 0.71 | 669 / 5.4 / A$125 / 0.70 |
| Shopping, base | 0.90, 1.05, 0.85 / 1.1, 1.7, 1.3 | 743 / 8.2 / A$82 / 1.10 | 637 / 10.8 / A$62 / 1.46 | 787 / 10.2 / A$65 / 1.38 |
| Shopping, optimistic | 0.70, 0.85, 0.65 / 1.6, 2.4, 2.0 | 955 / 15.3 / A$44 / 2.17 | 787 / 18.9 / A$35 / 2.68 | 1,029 / 20.6 / A$32 / 2.92 |
| Brand, conservative | 0.50 / 4 per cent, A$35 spent | 70 / 2.8 / A$12.50 / 7.2 | 90 / 3.6 / A$12.50 / 7.2 | 70 / 2.8 / A$12.50 / 7.2 |
| Brand, base | 0.40 / 7, A$52 spent | 130 / 9.1 / A$5.70 / 15.8 | 170 / 11.9 / A$5.70 / 15.8 | 130 / 9.1 / A$5.70 / 15.8 |
| Brand, optimistic | 0.35 / 10, A$70 to 91 spent | 200 / 20 / A$3.50 / 25.7 | 260 / 26 / A$3.50 / 25.7 | 200 / 20 / A$3.50 / 25.7 |
| Non brand, conservative | 1.00, 1.00, 0.95 / 0.8, 1.2, 1.0 | 152 / 1.2 / A$125 / 0.72 | 152 / 1.8 / A$83 / 1.08 | 160 / 1.6 / A$95 / 0.95 |
| Non brand, base | 0.85, 0.95, 0.80 / 1.6, 2.3, 1.8 | 179 / 2.9 / A$53 / 1.69 | 160 / 3.7 / A$41 / 2.18 | 190 / 3.4 / A$44 / 2.02 |
| Non brand, optimistic | 0.70, 0.85, 0.65 / 2.5, 3.5, 2.8 | 217 / 5.4 / A$28 / 3.21 | 179 / 6.3 / A$24 / 3.71 | 234 / 6.5 / A$23 / 3.88 |

Why these CVRs: site CVR is 1.6 per cent on warm Meta traffic; cold Shopping clicks on an A$87 bottle inside a A$29 to 80 grid convert below that at first (global Shopping 1.9 per cent, apparel 1.2 to 2.8). Brand clicks are capped by brand searches (about 100 to 300 a month), so the A$3 underspends most days; that is correct. Account totals: conservative about 9 orders a month, base about 20, optimistic about 41. In the base case Google adds about 20 reported orders to the store's 62 to 65 at a reported CPA near A$45 and ROAS near 2.0, only because brand drags the average down.

### 2.3 Time to the Smart Bidding thresholds (rolling 30 days)

- Shopping at A$22 a day. 15 conversions: conservative never; base not inside 3 months unless Shopping rises to A$32 a day in December (then about day 55 to 65); optimistic about day 30 to 40. 30 conversions: conservative and base never at this budget (base needs about A$65 a day); optimistic about day 75 to 90, after the A$10 scale step in `06`.
- Brand. 15: conservative never, base about day 50, optimistic about day 22. 30: base never, optimistic about day 35 in December.
- Non brand at A$5 a day: never reaches 15 in any case (maximum 6.5 a month). Manual CPC permanently.
- Account level, which is Google's real eligibility test (Finding 8): 15 at about day 55, 22 and inside month 1 for the three cases; 30 never, about day 50 to 60, and about day 25.

Consequence: Google will offer Target ROAS on Shopping once the account passes 15, mostly on brand conversions. Do not take it. Switch Shopping only when Campaigns > Conversions column, Last 30 days, shows 15 on that campaign: December in the optimistic case, February or never at A$22 a day in the base case. Manual CPC for the whole first quarter is the base case plan, not a failure.

### 2.4 Steps

1. Google Ads > Goals > Conversions > Summary > Purchase > Details: confirm "Use different values", currency AUD; the tax setting will be locked (Finding 11). After the `02` test order, the value must equal the subtotal (15.00). If it reads 17.50, the app sends totals: as a last resort add Goals > Conversions > Value rules > New rule > all conversions > multiply by 0.86, and restate every ROAS target in the plan.
2. Before 27 Oct, record the baseline in Triple Whale > Summary (wholesale tag filtered): 15 Sep to 26 Oct new customer orders, blended new customer CPA, MER, Meta CPA, plus 27 Oct to 21 Dec 2025 for the year on year read. Write both into `07-calendar.md`.
3. Campaigns > ep_shop_bottle-tees_au_2026q4 > Product groups: bottle A$1.10, tees A$0.40. Day 14 and every second Monday: bottle max CPC = Shopping CVR (Last 30 days) times A$55, rounded to 5 cents, between A$0.60 and A$1.30.
4. Day 30: fewer than 8 Shopping orders and CPA above A$90: do not raise bids, cut tees to A$0.30. 15 or more orders with CPA under A$60: campaign > Settings > Bidding > Change bid strategy > Maximise conversion value, no target; two weeks later same path > Target ROAS > 200.
5. Brand stays Manual CPC A$0.50 until the January on and off test. Never Maximise conversions on brand; it overbids the cheapest clicks in the account.
6. Non brand stays Manual CPC, A$1.00 cap, for as long as it runs. Gift terms will show about A$2 in Tools > Planning > Keyword Planner; keep the cap and accept low impression share rather than a A$130 CPA (A$2 at 1.5 per cent).
7. Judge Google in Triple Whale > Summary, comparing Last 30 days with the pre launch 30 days and with the same dates last year, never in the Google Ads conversions column.

### 2.5 A fair test of Google (8 weeks, MER based, no geo holdout)

1. Window 27 Oct to 21 Dec 2026. Meta held at A$150 a day, mugs and BFCM ad sets run on the same dates as 2025, so Google is the only new variable. Use gross spend; ignore the new advertiser credit.
2. Primary read, year on year: pass if (new customer orders 27 Oct to 21 Dec 2026 divided by the same dates 2025) exceeds (total ad spend 2026 divided by 2025) by at least 5 points, and blended new customer CPA stays inside A$40 to 50 with Google included. Secondary: Shopify > Orders, Conversion summary "google / cpc", at least 10 a month by week 6.
3. Incrementality adjusted CPA: weight reported orders by Finding 12 (brand 0.4, Shopping 0.7 because the store ranks below 4 organically for bottle and gift terms, non brand on park bottle queries 0.9). Base case month 2: 0.4 times 11.9 plus 0.7 times 10.8 plus 0.9 times 3.7 = 15.6 incremental orders for A$912, CPA A$58, just inside break even. Judge against that, not Google's A$36.
4. Brand on and off, 5 to 18 Jan 2027: Campaigns > tick ep_srch_brand > Edit > Pause. Search Console > Performance > Queries filtered "endless parks": organic brand clicks up by at least 80 per cent of the paused ad clicks means cannibalisation, move the A$3 to non brand; up less than 50 per cent, re enable.
5. Search Console > Performance, filter Australia: brand impressions in the window against the pre window. Rising brand searches on flat Meta spend is the Finding 13 demand Google exists to capture.

## 3. Where sources disagree

- Shopping CPC: global US$0.66 (Finding 1) against Australian bands to A$2.50 and a A$2.04 Search median (Finding 6). The model uses A$0.65 to 1.10 because the max CPC caps it; the cap costs impression share, not CPC.
- Shopping CVR: 0.7 to 1.2 per cent (The Ad Spend), 1.91 (Store Growers), 2.81 (one vendor), 3.11 blended (Triple Whale). The three cases span it.
- Target ROAS threshold: Google 15 at account level; Jyll 30 per campaign; Store Growers 50. The plan's 15 then 30 sits between.
- Conversion value: Merchant Center Help (subtotal, no shipping) against September 2025 EU reports (tax inclusive totals) and FeedArmy (tax inclusive, no shipping). All three read 87.00 for GST inclusive pricing; one test order resolves shipping.
- Brand search value: Stella 0.70 iROAS against Google's 50 per cent at rank 1 and the small brand exception. Treated as 40 per cent until the January test.
- Google against Meta: CorePPC has Google dearer per order; Triple Whale has Google at US$28.14 with Meta elsewhere near US$39. Direction only: Google clicks cost more, Shopping ROAS reads higher, Meta reaches more people.
- CPC trend: LocaliQ and Alphabet about 3 per cent; Channable 15 per cent for European Shopping; DNHQ 31 per cent in Australia in five months (single source).

## 4. Open questions for Jake

1. Does the A$16 landed cost include outbound postage, and is import GST claimed? If postage is inside it, bottle contribution is about A$71 and break even ROAS 1.23.
2. Carrier cost per parcel on free shipping orders over A$120 (assumed A$12).
3. Exact tee landed cost, so the tee max CPC comes from margin, not an assumption.
4. Repeat purchase: share of bottle buyers ordering stickers, lids or mugs within 12 months, and the value. A$20 of repeat contribution drops blended break even ROAS from 1.52 to about 1.15 and justifies a 150 target.
5. Will Meta hold A$150 a day from 27 Oct to 21 Dec, and did the 2025 BFCM and mug campaigns run on comparable dates?
6. Is month 1 Shopping at about ROAS 1.1 and CPA A$80 (base case, roughly A$20 lost an order) acceptable as the price of data, or should Shopping open at A$15 a day and non brand at A$10?
7. Search Console access for the brand query export and the January read.

## 5. Sources

- Google Ads Help, About Target ROAS bidding, answer 6268637 (read Oct 2026). https://support.google.com/google-ads/answer/6268637
- Google Ads Help, Set up Target ROAS for Shopping campaigns, answer 6309035. https://support.google.com/google-ads/answer/6309035
- Google Ads Help, Smart Bidding using value based bidding, answer 15099424 (June 2026 label change). https://support.google.com/google-ads/answer/15099424
- Google Ads Help, Smart Bidding for a Display campaign, answer 10285843. https://support.google.com/google-ads/answer/10285843
- Google Merchant Center Help, Migrating to the Google and YouTube app FAQ, answer 16031492 (2025). https://support.google.com/merchants/answer/16031492
- Shopify Community, conversion value suddenly includes VAT (Sep 2025). https://community.shopify.com/t/google-youtube-app-conversion-value-suddenly-includes-vat-august-vs-september/568656
- FeedArmy, Google and YouTube app now includes VAT (2025). https://feedarmy.com/kb/google-youtube-app-for-shopify-now-includes-vat-in-conversion-tracking/
- Triple Whale, Google Ads benchmarks by industry (Aug 2025 to Jul 2026). https://www.triplewhale.com/blog/google-ads-benchmarks
- WordStream and LocaliQ 2026 benchmarks, via Digital Applied. https://www.digitalapplied.com/blog/google-ads-benchmarks-2026-cpc-ctr-cvr-industry
- Foundry CRO, Google Shopping benchmarks by category 2026. https://foundrycro.com/blog/google-shopping-benchmarks-by-category-2026/
- The Ad Spend, Google Shopping benchmarks 2026. https://theadspend.com/blog/google-shopping-overall
- Store Growers, 27 Google Ads benchmarks 2026; Target ROAS guide. https://www.storegrowers.com/google-ads-benchmarks/ https://www.storegrowers.com/target-roas/
- CorePPC, Google Ads ecommerce benchmarks 2026. https://coreppc.com/blog/google-ads-benchmarks-ecommerce-2026/
- PPC Land on Channable's benchmark (12 Jul 2026). https://ppc.land/channable-data-shows-advertisers-lose-46-roas-as-google-clicks-cost-more/
- Digital Nomads HQ, Australian Click Price Index (May 2026). https://digitalnomadshq.com.au/blog/how-much-does-google-ads-cost/
- White Peak Digital, Google Ads cost Australia 2026. https://www.whitepeakdigital.com/blog/google-ads-cost-australia/
- Jyll Saskin Gales, 30 days 30 conversions; budget rule. https://learn.jyll.ca/blog/when-and-how-should-you-change-bid-strategies-in-google-ads https://learn.jyll.ca/blog/how-much-do-i-need-to-spend-on-google-ads
- Stella, 2025 DTC incrementality benchmarks (Aug 2024 to Dec 2025). https://www.stellaheystella.com/blog/2025-dtc-digital-advertising-incrementality-benchmarks
- Ecommerce Fastlane, branded search cannibalisation 2026 (Google 2012 pause studies, eBay 2015). https://ecommercefastlane.com/branded-search-cannibalization-google-ads-roas/
- Brainlabs, Meta conversion lift and search lift. https://www.brainlabsdigital.com/paid-social-measurement-meta-incrementality-search-lift/
- iProspect, Meta Search Lift. https://www.iprospect.com/en-us/insights/meta-search-lift-to-drive-stronger-media-performance
- Lebesgue, Meta geo holdout test. https://lebesgue.io/facebook-ads/meta-ads-incrementality-geo-holdout-test
- Cometly, incrementality testing guide 2026 (Google geo lift pricing, Nov 2025). https://www.cometly.com/post/incrementality-testing-for-paid-advertising
