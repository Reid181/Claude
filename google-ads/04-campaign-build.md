# 04. Campaign build

Do this only after `01-account-setup.md`, `02-conversion-tracking.md` and `03-feed-fixes.md` are done and Merchant Center shows the bottle and the tees as Approved. Build all three campaigns inside Google Ads (ads.google.com), never from the Shopify Google & YouTube channel, which can only create Performance Max.

If a label differs from what is written here, use the search box at the top of Google Ads and type the setting name.

## Before you start

- Sign in as the Google account that owns the Ads account (expected: endlesspks@gmail.com). Top right, confirm the account is Endless Parks and the currency is AUD.
- Have `05-keywords.csv`, `05-negatives.txt` and `05-ad-copy.md` open.
- Settings every campaign shares unless stated: Locations Australia with Location options set to Presence (people in or regularly in your targeted locations), not the default Presence or interest; Languages English; search partners unticked; Display Network unticked; no ad schedule; no device bid adjustments; start date today, no end date; AI Max off; automatically created assets off at campaign level (campaign level On overrides account level Off).
- The campaign builder starts with a goal screen. Choosing Sales is fine, but if it forces settings you do not want, use the link "Create a campaign without a goal's guidance".

## Campaign 1: ep_shop_bottle-tees_au_2026q4 (A$22 a day)

1. Campaigns > plus > New campaign > Sales > Shopping. If Google offers Performance Max first, find the link for a Standard Shopping campaign. Merchant Center account: Endless Parks (5382740922). Country of sale: Australia. Continue.
2. Name: `ep_shop_bottle-tees_au_2026q4`.
3. Bidding: Manual CPC (Enhanced CPC no longer exists for Shopping). Budget A$22 per day. Campaign priority: leave the default Low; it only matters once a second Shopping campaign exists.
4. Networks: untick Search partners. Untick YouTube, Discover and Gmail if listed. If the campaign shows the new Channel prioritisation card instead, set search partners Low with 0 per cent.
5. Devices all. Locations Australia, Location options Presence. Languages English.
6. Local products and Inventory filter: off. Do not turn on AI Max for Shopping, text customisation or final URL expansion if offered.
7. Ad group `all_products`, default bid A$0.80. Save.
8. Ad group > Product groups > subdivide All products by Custom label 0 (set in `03-feed-fixes.md`):
   - hero: bid A$1.10 (the bottle). This bets on a 2 per cent conversion rate to buy impression share for 14 days; from day 14 reset it every second Monday to the observed Shopping conversion rate times A$55, rounded to 5 cents, between A$0.60 and A$1.30.
   - apparel: bid A$0.40 (the tees; 1.2 per cent conversion rate times a A$30 allowed CPA).
   - Everything else: Exclude. Mugs, stickers and lids stay out of paid ads but keep their free listings.
   Custom labels take 24 to 48 hours after the Shopify sync to appear in the product group picker. If they are not there yet, subdivide by Product type instead (Water Bottle A$1.10, T-Shirt A$0.40, everything else excluded) and switch to labels later.
9. Campaign > Keywords > Negative keywords: attach the shared list `EP_Negatives_Shopping`.
10. Campaign settings > Campaign URL options: leave the final URL suffix empty so the account level suffix applies.
11. Settings > Automatically created assets (if present at campaign level): off.
12. Campaigns > Products > Diagnostics tab: the 3 bottle variants and every tee variant must read Eligible, not Eligible (limited) or Not eligible, before launch.
13. Set to Paused until `06-launch-and-optimise.md` says launch.

## Campaign 2: ep_srch_brand_au_2026q4 (A$3 a day)

1. New campaign > Sales > Search. Results you want: Website visits, https://www.endlessparks.com. Conversion goals: keep only the Purchase action from `02-conversion-tracking.md`.
2. Name `ep_srch_brand_au_2026q4`. Bidding: Manual CPC, default A$0.50. Budget A$3 per day. This campaign is a 30 day measurement line as much as protection: brand clicks cost A$0.10 to A$0.50 and most brand buyers would have found the store anyway, so after 30 days check Auction insights and keep the campaign only if a competitor shows up or brand clicks convert above 5 per cent (`06-launch-and-optimise.md`).
3. AI Max: off. It is pre selected on every new Search campaign; untick it on the first settings screen, and confirm afterwards at Settings > AI Max > opt out of all AI Max settings (this covers search term matching, text customisation and final URL expansion together).
4. Networks: untick Search partners and Display Network. Locations Australia, Presence. Language English.
5. Automatically created assets: off. Brand settings: leave empty. Ad rotation: leave on Optimise.
6. Ad group `brand`, keywords from `05-keywords.csv` (exact and phrase on endless parks variants).
7. Responsive search ad: the Brand ad in `05-ad-copy.md`. Final URL https://www.endlessparks.com.
8. Assets: sitelinks, callouts, structured snippet, price, business name and logo, image assets, as listed in `05-ad-copy.md`.
9. Negative keywords: attach `EP_Negatives_Search`. Do not add "review" or "reviews" as negatives; people searching reviews are buyers.
10. Paused until launch.

## Campaign 3: ep_srch_nonbrand_au_2026q4 (A$5 a day)

1. New campaign > Sales > Search, same settings as the brand campaign. Name `ep_srch_nonbrand_au_2026q4`. Manual CPC. Budget A$5 per day. AI Max off, automatically created assets off.
2. Ad groups from `05-keywords.csv`: `bottle_nationalparks` and `gifts_outdoors` enabled at launch; `tees_aussiemade` built but paused until 17 Nov. Tees cannot afford A$1 clicks until the bottle groups have data.
3. Max CPC per keyword from the CSV. Nothing above A$1.00.
4. Ads: the Bottle ad in `bottle_nationalparks`, the Gifts ad in `gifts_outdoors`, the Tees ad in `tees_aussiemade`. Bottle and gifts land on https://www.endlessparks.com/products/ultimate-adventure-bottle. Tees land on https://www.endlessparks.com/pages/drop-01.
5. Assets as for brand, plus the bottle price asset.
6. Negative keywords: attach `EP_Negatives_Search` and add the brand terms as campaign negatives (`"endless parks"`, `[endless park]`) so brand searches serve only from the brand campaign.
7. Labels: `launch-oct26` on the two live ad groups, `xmas26` on the Christmas keywords.
8. Paused until launch.

## After all three are built

- Tools > Shared library > Exclusion lists: `EP_Negatives_Shopping` is on the Shopping campaign, `EP_Negatives_Search` on both Search campaigns.
- Admin > Account settings: auto tagging on, final URL suffix saved.
- Each campaign > Settings: AI Max off, automatically created assets off, networks unticked, Presence. Google sometimes re enables defaults when a campaign is saved from a different screen.
- Campaigns view: add columns Conversions, Conv. value, Cost / conv., Conv. value / cost, Search impr. share, Search lost IS (budget), Search lost IS (rank). Save the column set as `EP weekly`.
- Google Ads Editor 2.13: Account > Export whole account as the day one backup.
- Admin > Advertiser verification: start it now. Business name and logo assets cannot serve until it passes.
- Tools > Planning > Keyword Planner > Get search volume and forecasts, location Australia, last 12 months: paste every keyword from `05-keywords.csv`. No tool outside Google Ads could give Australian volumes for these niche queries, so this is the first real read. Drop anything showing zero volume and note the rest in the CSV.
