# 04. Campaign build

Do this only after `01-account-setup.md`, `02-conversion-tracking.md` and `03-feed-fixes.md` are done and Merchant Center shows the bottle and the tees as Approved. Build all four campaigns inside Google Ads (ads.google.com), never from the Shopify Google & YouTube channel, which can only create Performance Max.

If a label differs from what is written here, use the search box at the top of Google Ads and type the setting name.

## Before you start

- Sign in as the Google account that owns the Ads account (expected: endlesspks@gmail.com). Top right, confirm the account is Endless Parks and the currency is AUD.
- Have `05-keywords.csv`, `05-negatives.txt` and `05-ad-copy.md` open.
- Settings every campaign shares unless stated: Locations Australia with Location options set to Presence (people in or regularly in your targeted locations), not the default Presence or interest; Languages English on the Search campaigns (Shopping has no language setting); search partners unticked; Display Network unticked; no ad schedule; no device bid adjustments; start date today, no end date; AI Max off; automatically created assets off at campaign level (campaign level On overrides account level Off).
- Keyword Planner runs before the build, not after: Tools > Planning > Keyword Planner > Get search volume and forecasts, location Australia, last 12 months, paste every keyword from `05-keywords.csv`. A new account sees ranges rather than exact numbers; that is fine. Drop a keyword only if it shows no volume at all. Record the ranges in the CSV note column.
- The campaign builder starts with a goal screen. Choosing Sales is fine, but if it forces settings you do not want, use the link "Create a campaign without a goal's guidance".

## Campaign 1: ep_shop_bottle_au_2026q4 (A$22 a day, the bottle only)

1. Campaigns > plus > New campaign > Sales > Shopping. If Google offers Performance Max first, find the link for a Standard Shopping campaign. Merchant Center account: Endless Parks (5382740922). Country of sale: Australia. Continue.
2. Name: `ep_shop_bottle_au_2026q4`.
3. Bidding: Manual CPC (Enhanced CPC no longer exists for Shopping). Budget A$22 per day. Campaign priority: leave the default Low on both Shopping campaigns; they never compete for a product because each one excludes the other's products.
4. Networks: untick Search partners. Untick YouTube, Discover and Gmail if listed. If the campaign shows the new Channel prioritisation card instead, set search partners Low with 0 per cent.
5. Devices all. Locations Australia, Location options Presence.
6. Inventory filter: off (the old "Local products" box was removed in August 2026; do not look for it). AI Max for Shopping is an opt in beta: do not turn it on, nor text customisation or final URL expansion, if offered.
7. Ad group `all_products`, default bid A$0.80. Save.
8. Ad group > Product groups > subdivide All products by Custom label 0 (set in `03-feed-fixes.md`):
   - hero: bid A$1.10 (the bottle). This bets on a 2 per cent conversion rate to buy impression share for 14 days; from day 14 reset it every second Monday to the observed Shopping conversion rate times A$55, rounded to 5 cents, between A$0.60 and A$1.30.
   - Everything else: Exclude. The tees (custom label 0 = apparel) belong to Campaign 2; mugs, stickers and lids stay out of paid ads but keep their free listings.
   Custom labels take 24 to 48 hours after the Shopify sync to appear in the product group picker. If they are not there yet, subdivide by Product type instead (Water Bottle A$1.10, everything else excluded) and switch to labels later.
9. Campaign > Keywords > Negative keywords: attach the shared list `EP_Negatives_Core`.
10. Campaign settings > Campaign URL options: leave the final URL suffix empty so the account level suffix applies.
11. Settings > Automatically created assets (if present at campaign level): off.
12. Campaigns > Products > Diagnostics tab: the 3 bottle variants read Eligible, or Eligible (limited) where the only note is the missing GTIN. Not eligible means a feed or Marketing methods problem (`03` Step 4.6).
13. Set to Paused until `06-launch-and-optimise.md` says launch.

## Campaign 2: ep_shop_tees_au_2026q4 (A$5 a day, the tees only)

Jake's call, 15 Oct: the tees get their own budget line so the bottle's A$1.10 bids never starve them. Same build as Campaign 1 with these differences.

1. Campaigns > plus > New campaign > Sales > Shopping (Standard Shopping, not Performance Max). Merchant Center 5382740922, country of sale Australia. Name `ep_shop_tees_au_2026q4`.
2. Manual CPC, budget A$5 per day, priority Low (the default; see Campaign 1 step 3). Networks, devices, locations and Inventory filter as in Campaign 1 steps 4 to 6.
3. Ad group `tees`, default bid A$0.40. Save.
4. Product groups: subdivide All products by Custom label 0. apparel: bid A$0.40 (1.2 per cent conversion rate times a A$30 allowed CPA; hold between A$0.30 and A$0.50 until Jake confirms the tee landed cost). Everything else: Exclude, which keeps the bottle in Campaign 1. Fallback while labels are missing: Product type T-Shirt A$0.40, everything else excluded.
5. Negative keywords: attach `EP_Negatives_Core`, then type the tees ad group negatives from `05-negatives.txt` (bottle, hoodie, workwear and the rest) as campaign negatives here, so a bottle search never pulls a tee listing.
6. Campaign URL options empty; automatically created assets off. Diagnostics: every tee variant Eligible, or Eligible (limited) for the missing GTIN only.
7. Paused until launch. Kill rule in `06`: 150 clicks across this campaign and the tees Search ad group with no sale pauses both and moves the A$5 to Campaign 1.

## Campaign 3: ep_srch_brand_au_2026q4 (A$3 a day)

1. New campaign > Sales > Search. Results you want: Website visits, https://endlessparks.com. Conversion goals: keep only the Purchase action from `02-conversion-tracking.md`.
2. Name `ep_srch_brand_au_2026q4`. Bidding: Manual CPC, default A$0.50. Budget A$3 per day. This campaign is a 30 day measurement line as much as protection: brand clicks cost A$0.10 to A$0.50 and most brand buyers would have found the store anyway, so after 30 days check Auction insights and keep the campaign only if a competitor shows up or brand clicks convert above 5 per cent (`06-launch-and-optimise.md`).
3. AI Max: off. It is pre selected on every new Search campaign; untick it on the first settings screen, and confirm afterwards at Settings > AI Max > opt out of all AI Max settings (this covers search term matching, text customisation and final URL expansion together).
4. Networks: untick Search partners and Display Network. Locations Australia, Presence. Language English.
5. Automatically created assets: off. Brand settings: leave empty. Ad rotation: leave on Optimise.
6. Ad group `brand`, keywords from `05-keywords.csv` (exact and phrase on endless parks variants).
7. Responsive search ad: the Brand ad in `05-ad-copy.md`. Final URL https://endlessparks.com.
8. Assets: sitelinks, callouts, structured snippet, price, business name and logo, image assets, as listed in `05-ad-copy.md`.
9. Negative keywords: attach `EP_Negatives_Core`. Do not add "review" or "reviews" as negatives; people searching reviews are buyers.
10. Paused until launch.

## Campaign 4: ep_srch_nonbrand_au_2026q4 (A$5 a day)

1. New campaign > Sales > Search, same settings as the brand campaign. Name `ep_srch_nonbrand_au_2026q4`. Manual CPC. Budget A$5 per day. AI Max off, automatically created assets off.
2. Ad groups from `05-keywords.csv`, built exactly as the status_at_build column says: `bottle_nationalparks` and `tees_aussiemade` enabled; `gifts_outdoors`, `gifts_test` and `bottle_generic_test` created with every keyword paused and the label from the label column. At A$5 a day the campaign buys about five to eight clicks a day, so it launches on the bottle cluster and the Aussie made tees group (Jake's call, 15 Oct: tee spend from day one); gifts switch on 17 Nov when the gift season and the credit threshold are both in sight (`07-calendar.md`); the two test groups only on the rules in the CSV notes.
3. Max CPC per keyword from the CSV. Nothing above A$1.00.
4. Ads: the Bottle ad in `bottle_nationalparks` and in `bottle_generic_test`; the Gifts ad in `gifts_outdoors` and `gifts_test`; the Tees ad in `tees_aussiemade`. Bottle and gift groups land on https://endlessparks.com/products/ultimate-adventure-bottle. Tees land on https://endlessparks.com/pages/drop-01?view=ep-drop-01 (the view parameter is required; without it the page is the founders' story with no tees). Never use the navigation's /pages/about-us?view=ep-drop-01&cb=...&_kx=... form: the Klaviyo parameter would be pasted into every ad click.
5. Assets as for brand, plus the bottle price asset.
6. Negative keywords: attach `EP_Negatives_Core` and `EP_Negatives_Brand` (the brand list keeps brand searches in the brand campaign), then type the ad group negatives from `05-negatives.txt` into each ad group.
7. Labels: `launch-oct26` on the two live ad groups, `gifts`, `test` and `xmas26` as the CSV says.
8. Paused until launch.

## After all four are built

- Tools > Shared library > Exclusion lists: `EP_Negatives_Core` on all four campaigns, `EP_Negatives_Brand` on the non brand campaign only.
- Admin > Account settings: auto tagging on, final URL suffix saved.
- Each campaign > Settings: AI Max off, automatically created assets off, networks unticked, Presence. Google sometimes re enables defaults when a campaign is saved from a different screen.
- Audiences: the Observation segments and the purchaser exclusion from `09-audiences.md` (campaign level on Search; ad group level on Shopping if the campaign level option is absent).
- Campaigns view: save the `EP weekly` column set defined in `02-conversion-tracking.md`.
- Google Ads Editor 2.13: Account > Export whole account as the post build backup.
- Admin > Account (the Advertiser verification hub): started on the account creation day. Business name and logo assets cannot serve until it passes.
