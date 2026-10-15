# 06. Launch and optimise

## Launch checklist (all must pass)

1. Merchant Center: bottle (3 colours) and 4 tees show Approved, with Shopping ads ticked under Marketing methods. The only acceptable "limited performance" note is the missing GTIN one (`03` Step 1). Shipping shows Australia with the A$14 standard, A$19 express, free over A$120 rules.
2. Google Ads > Goals > Conversions: exactly one Purchase action is Primary, with value and AUD. After the test order in `02-conversion-tracking.md` its status reads No recent conversions or Tag active, not Unverified, and Tag Assistant showed one conversion hit with value and user_data. "Recording conversions" cannot appear before the first paid click; it is the day 7 check.
3. Enhanced conversions: on, with the customer data terms accepted. The match rate band is also a day 7 check.
4. Auto tagging: on. Final URL suffix saved at account level and its Test button loads the PDP with every parameter. The manual URL test in `10-landing-pages.md` C4 and C5 kept gclid through any redirect. The real ad click test happens on launch day from a phone (`RUNBOOK.md` 7.6); preview ads cannot be clicked.
5. Billing: payment method saved, GST details and ABN entered, tax invoice delivery set under Billing > Settings > Document delivery options.
6. Auto apply recommendations: all off.
7. Each campaign: locations Australia Presence only, search partners off, Display off, AI Max off, broad match off, correct daily budget.
8. `EP_Negatives_Core` on all four campaigns and at account level; `EP_Negatives_Brand` on the non brand campaign; ad group negatives typed in, and the tees negatives on the tees Shopping campaign.
9. Product groups: bottle campaign hero A$1.10 with everything else excluded; tees campaign apparel A$0.40 with everything else excluded. Campaigns > Products > Diagnostics shows every advertised variant Eligible in its own campaign.
10. Ads approved (status Eligible), not Limited or Disapproved.
11. Triple Whale: Google Ads connected so Google spend shows in the MER view.
12. Landing pages: the bottle product page shows A$87 and in stock. Old pages still indexed at A$58 and A$63 (the /pages/adventurebottle marketing page and an old collection snapshot) are fixed or redirected, so Merchant Center never sees a price mismatch.
13. Automated rules and scripts from `01-account-setup.md` are live and have run once in preview.
14. Keyword Planner check: Tools > Planning > Keyword Planner > Get search volume and forecasts, location Australia, paste every keyword in `05-keywords.csv`. Replace the estimated volumes in the competition notes with real numbers and drop any keyword showing zero volume.
15. Baseline recorded: Triple Whale > Summary with the wholesale tag filtered, new customer orders, blended new customer CPA, MER and Meta CPA for 15 Sep to 26 Oct 2026, and the same for 27 Oct to 21 Dec 2025. Google is judged against these.

Then set the four campaigns to Enabled on a Monday to Wednesday morning Perth time so there are a few weekdays of data before the weekend.

## Days 1 to 14: no bid changes

- Day 1 and 2: check spend is happening (A$25 to A$70 on any single day, since Google may spend up to twice the daily budget; A$30 to A$40 a day on average over the first week), ads are Eligible, no disapprovals, clicks land on the right pages with the suffix intact.
- Day 3: Search terms report for all four campaigns. Add negatives for anything irrelevant (other brands, printable, map pdf, jobs, sticker only queries). Do not add negatives for queries that are merely broad; two weeks of data first.
- Day 7: read Search impression share and lost IS (rank) for the bottle group, and the Purchase action's status (Recording conversions after the first paid click order) and enhanced conversions match rate. Note, do not act.
- Day 14: first real read and the first bid change (ladder stage 2). Expect 300 to 500 clicks across the account and 3 to 8 orders. If zero orders and more than 300 clicks, stop and recheck conversion tracking before changing anything else.

## Bidding ladder

| Stage | Trigger | Shopping | Search |
|---|---|---|---|
| 1 Launch | Day 0 | Manual CPC, bottle campaign A$1.10, tees campaign A$0.40 | Manual CPC, cap A$1.00 (brand A$0.50) |
| 2 Tune | Day 14, then every second Monday | Bottle max CPC = Shopping conversion rate (last 30 days) times A$55, between A$0.60 and A$1.30. Week 3: if CPC is under A$1 and lost IS (rank) is above 60 per cent, go to A$1.30 | Raise the best 5 keywords by 20 per cent |
| 3 Smart bidding | 15 conversions in the last 30 days on that campaign (Campaigns view, Conversions column, Last 30 days) | Target ROAS set at the trailing 30 day observed ROAS minus about 15 per cent, never below 150 (if Shopping is at 1.7, type 145 rounded to 150). Google's own advice is to start near the actual ROAS. Not Maximise conversion value with no target: that has no floor and spends the whole budget on whatever converts cheapest for a fortnight at the moment the account is just becoming readable. The tees campaign stays Manual CPC at A$5 a day; it cannot reach 15 | Non brand: stays Manual CPC for good at A$5 a day (it cannot reach 15). Brand: stays Manual CPC; never Maximise conversions on brand |
| 4 Raise the target | 30 conversions in the last 30 days on that campaign, and two weeks after stage 3 | Raise Target ROAS by 15 to 20 points every two weeks toward 200 per cent while conversions hold (Google renamed "Maximise conversion value with a target ROAS" to "Target ROAS" in June 2026) | not applicable |

Google's own threshold for Target ROAS is 15 conversions in 30 days at the account level (per Merchant Center ID for Shopping), so Google will start recommending it once brand conversions push the account past 15. Decline until the Shopping campaign itself shows 15. In the base case that is February or later at A$22 a day; in the optimistic case December. Never switch on fewer than 15; never set a target on the same day you switch strategy.

## Weekly routine (20 minutes, Monday)

1. Campaigns view, column set `EP weekly` (defined in `02-conversion-tracking.md`), last 7 days against the previous 7, and last 30 days. Conversions lag up to 72 hours, so re read last week's numbers too.
2. Search terms: add negatives, move any converting query to its own exact keyword.
3. The two Shopping campaigns: compare bottle and tees cost per conversion. Tees at 100 clicks (Shopping plus the Search ad group) with no sale: bids to A$0.30. Tees at 150 clicks with no sale: pause the tees campaign and the tees ad group and move the A$5 to the bottle campaign. Campaigns > Products, last 7 days by impressions: any advertised variant at zero impressions means a feed or eligibility problem.
4. Budget: the bottle Shopping campaign limited by budget and CPA under A$50 for two weeks running: raise it by A$5 a day. CPA above A$70 for two weeks after week 4: lower bottle bid 15 per cent, not the budget.
5. Merchant Center > Products: any new disapprovals or warnings.
6. Triple Whale: blended CPA and MER with Google included, wholesale tag filtered out. This is the number that decides if Google stays.
7. Recommendations tab: read, then dismiss. Never auto apply.
8. Monthly: Auction insights on both Search campaigns (who is bidding on the brand and on park bottle terms), Change history filtered to Auto-applied, and the Purchase action's Diagnostics tab for enhanced conversions.

## Kill and scale rules

- Scale (add A$10 a day to the bottle Shopping campaign): 4 weeks in, Google CPA inside A$39 to A$50 on 15 or more conversions, blended CPA not worse than before launch.
- Hold: Google CPA A$50 to A$70. Keep optimising, no budget change.
- Cut non-brand Search to A$2 a day: non-brand CPA above A$80 after 300 clicks.
- Pause the tees: 150 clicks across the tees Shopping campaign and the tees Search ad group with no sale. Pause both, move the A$5 to the bottle Shopping campaign, and re test the tees with the next drop.
- Brand campaign at day 30: open Auction insights. Keep it if any competitor domain appears or brand clicks convert above 5 per cent at under A$0.30 a click. If the brand search page is uncontested and organic plus free listings already hold it, drop the budget to A$1 and move the A$2 to Shopping, the campaign with the readable CPA.
- Brand on and off test, 5 to 18 Jan 2027 (before the PMax experiment, which needs the brand campaign live): pause the brand campaign for two weeks and watch Search Console > Performance > Queries filtered "endless parks". If organic brand clicks rise by at least 80 per cent of the paused ad clicks, the ads were cannibalising: move the A$3 to Shopping. If they rise by less than half, re enable.
- Day 30 on Shopping: fewer than 8 orders and CPA above A$90, do not raise bids, cut the tees campaign bid to A$0.30. 15 or more orders with CPA under A$60, go to stage 3 of the ladder.
- Generic bottle test (ad group `bottle_generic_test`): enable only if the Shopping search terms report shows generic "water bottle" queries converting in weeks 1 to 3. The Shopping grid for those queries is A$29 to A$80, so expect it to fail; 150 clicks with no sale and it goes back to paused.
- Stop Google entirely: blended new customer CPA worse than A$55 for 6 straight weeks with Google included, and Google reporting fewer than 10 orders a month at A$35 a day.

## Later changes, each with one trigger

- Mugs: from 20 Nov, if Shopping's last 30 day CPA is under A$60 (whatever the bid strategy), add the mugs as their own product group at A$0.70 (custom label 0 = mugs, set in the feed first). Remove the group on 24 Dec. Mugs at A$45 are the gift price point and 20 Nov to 15 Dec is their window.
- Gifts Search ad group: enabled 17 Nov per `07-calendar.md`, with the xmas26 keywords; xmas26 paused 24 Dec. The tees Search ad group is live from launch (Jake, 15 Oct).
- Performance Max: only through `08-pmax-experiment.md`, whose four gates are the single test; decide on 29 Dec.
- Rules, scripts and the weekly report: `11-automation-reporting.md`.
