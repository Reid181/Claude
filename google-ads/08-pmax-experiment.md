# 08. Performance Max experiment (month 3, only if the gates pass)

Performance Max is not part of the launch. This file is the one controlled way to test it later, against Standard Shopping, without breaking what works. Full research in `research/phase2/P4-pmax-experiment.md`.

## Gates (decide 29 Dec 2026 on data to 27 Dec)

Run the experiment only if all four hold. If any fails, defer to March and keep Shopping.

1. ep_shop_bottle-tees_au_2026q4 CPA inside A$39 to A$50 over weeks 5 to 8.
2. At least 20 purchase conversions on the account in the trailing 30 days (below the 30 practitioners want, so the kill criteria below are strict).
3. The Purchase action records with enhanced conversions firing and wholesale orders excluded.
4. ep_srch_brand_au_2026q4 live on exact match, so brand queries have an owner.

## Prepare in November and December

| # | Step | Where |
|---|---|---|
| 1 | Custom label 0 already splits hero and apparel; nothing to add | Feed |
| 2 | Request "Endless Parks" into Google's brand library and keep the brand list `Endless Parks` current | Tools > Shared library > Brand lists > plus > search > Request a brand if absent. Allow weeks |
| 3 | Customer Match list from Shopify customers (Tools > Data manager > Connect product > Shopify, or a CSV at Tools > Audience manager); needed for new customer detection and exclusions | Google Ads |
| 4 | Cut three videos from the Meta winners (founder voice "No more USA", the meme static with motion): 16:9, 1:1, 9:16, 15 to 30 seconds, no price or offer on screen. Upload unlisted to the Endless Parks YouTube channel | YouTube |
| 5 | Images per asset group: 3 landscape 1200 by 628, 3 square 1200 by 1200, 2 portrait 960 by 1200; logo 1200 by 1200 and 1200 by 300; product kept inside the centre 80 per cent, no text overlays | Assets |
| 6 | Text assets drafted from `05-ad-copy.md`; nothing with price, discount or "sale" | Copy |

## Build

Build 12 to 15 Jan 2027, saved paused.

| Setting | Value |
|---|---|
| Name | ep_pmax_bottle-tees_au_2027q1 |
| Goals | Purchase only, campaign specific goal settings; remove add to cart, begin checkout, page view |
| Merchant Center | 5382740922, Australia |
| Budget | A$22 a day (override Google's pre filled recommendation) |
| Bidding | Mirror Shopping exactly: Target ROAS 200 per cent if Shopping is on it, otherwise Maximise conversion value with no target |
| Customer acquisition | "Bid higher for new customers", new customer value A$10 to A$20 (Jake to set). Not "only bid for new customers" at this volume |
| Locations, language | Australia, Presence; English |
| Final URL expansion and text customisation | Off (Settings > Asset optimisation). Confirm after saving |
| Automatically created assets, video enhancements, AI voice over, AI resizing | Off wherever the toggles appear (Settings > Asset optimisation and asset group > Videos) |
| Brand exclusions | Brand list `Endless Parks`; leave "Allow Shopping ads on searches that mention excluded brands" unticked |
| Campaign negatives | Paste `05-negatives.txt` plus [endless parks], [endless parks bottle], [endless parks water bottle], [endlesspks] as insurance while the brand library request is pending |
| Channel prioritisation | If the card shows: Display Network Low 10 per cent, search partners Low 10 per cent. If not: account level placement exclusions for mobile app categories and parked domains |
| Ad schedule, devices | None |
| URL suffix | Inherit the account suffix |

Asset group 1, Bottle: listing group custom label 0 = hero, final URL /products/ultimate-adventure-bottle, 15 headlines, 5 long headlines, 5 descriptions drawn from `05-ad-copy.md`, 20 to 25 search themes (national parks water bottle, australian national parks bottle, road trip water bottle australia, gifts for grey nomads, gifts for 4wd lovers, hiking bottle australia, parks sticker bottle, adventure bottle, big lap gifts and so on), audience signals (Customer Match purchasers, 30 day visitors, custom segment of the same queries, in market outdoor recreation, affinity outdoor enthusiasts), the three videos.

Asset group 2, Tees: listing group custom label 0 = apparel, final URL /pages/drop-01, tee headlines from `05-ad-copy.md`, search themes australian made t shirts, national parks t shirt australia, hiking t shirt australia, bluff knoll shirt, stirling range tee. Lower expectations; one asset group (bottle only) is the lower risk option if Jake prefers a cleaner read.

## Experiment (Tuesday 19 Jan to 2 Mar 2027)

The brand on and off test in `06` runs 5 to 18 Jan and the brand campaign must be live again before this starts (gate 4), which is why the experiment begins 19 Jan, not earlier.

1. Campaigns > Experiments > plus > Campaign types > Performance Max vs Shopping.
2. Control ep_shop_bottle-tees_au_2026q4, treatment ep_pmax_bottle-tees_au_2027q1, split 50/50, PMax budget A$22. Both arms enter half the eligible auctions, so the pair spends about A$22 to A$30 a day with peaks near A$44; the new advertiser credit landing in late December covers the overage, which is why January is the month.
3. Six weeks, no changes to bids, budgets, assets or negatives in either arm except for the kill criteria.
4. Tick "View results with comparable campaigns". Judge on the two arms' combined CPA and ROAS plus total purchases, cross checked with Shopify new customer orders (wholesale excluded) and Triple Whale MER, never on PMax's own conversion column.

Weekly reads: campaign > Insights and reports > Channel performance (share of spend by channel), Search terms (brand leakage, waste over A$10 a term), Assets filtered to Source "Automatically created" (remove any), Listing groups (bottle versus tee spend).

## Kill criteria

| When | Kill if | Action |
|---|---|---|
| Day 7 | Any auto generated text or video asset is serving, or brand queries exceed 5 per cent of PMax clicks | Fix the setting the same day; if it recurs, end the experiment |
| Day 14 | Display plus YouTube plus Discover above 40 per cent of PMax spend with zero purchases | End, keep Shopping |
| Day 21 | PMax spend above A$450 with 2 or fewer purchases, or PMax CPA above A$90 | End, keep Shopping |
| Day 42 | PMax arm CPA above A$50 or ROAS below 2.0, or fewer than 12 purchases in the arm, or blended Shopify new customer CPA worse than December | End without applying; retest at A$3,000 a month or after Christmas 2027 |
| Day 42 | PMax CPA at or under Shopping CPA with at least 12 purchases and blended new customer orders up | Apply (PMax becomes primary, Shopping pauses). Keep both Search campaigns and the brand list. Re check brand leakage 14 days later |

Not worth testing: feed only PMax (Standard Shopping with less control), Demand Gen, YouTube, Display remarketing at this budget.
