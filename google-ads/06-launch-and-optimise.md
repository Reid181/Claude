# 06. Launch and optimise

## Launch checklist (all must pass)

1. Merchant Center: bottle (3 colours) and 4 tees show Approved. No "limited performance" warnings on them. Shipping and tax show Australia with the A$14 standard, A$19 express, free over A$120 rules.
2. Google Ads > Goals > Conversions: exactly one Purchase action is Primary, with value and AUD, and its status is Recording conversions after the test order in `02-conversion-tracking.md`.
3. Enhanced conversions: on and verified for the Purchase action.
4. Auto tagging: on. Final URL suffix saved at account level. A test click from a Google ad preview lands on the site with gclid and the utm parameters in the URL.
5. Billing: payment method saved, GST details and ABN entered, tax invoice emails on.
6. Auto apply recommendations: all off.
7. Each campaign: locations Australia Presence only, search partners off, Display off, AI Max off, broad match off, correct daily budget.
8. Negative lists attached. Brand terms are negatives in the non-brand campaign.
9. Product groups: bottle A$1.10, tees A$0.40, everything else excluded. Campaigns > Products > Diagnostics shows every advertised variant Eligible.
10. Ads approved (status Eligible), not Limited or Disapproved.
11. Triple Whale: Google Ads connected so Google spend shows in the MER view.
12. Landing pages: the bottle product page shows A$87 and in stock. Old pages still indexed at A$58 and A$63 (the /pages/adventurebottle marketing page and an old collection snapshot) are fixed or redirected, so Merchant Center never sees a price mismatch.
13. Automated rules and scripts from `01-account-setup.md` are live and have run once in preview.
14. Keyword Planner check: Tools > Planning > Keyword Planner > Get search volume and forecasts, location Australia, paste every keyword in `05-keywords.csv`. Replace the estimated volumes in the competition notes with real numbers and drop any keyword showing zero volume.
15. Baseline recorded: Triple Whale > Summary with the wholesale tag filtered, new customer orders, blended new customer CPA, MER and Meta CPA for 15 Sep to 26 Oct 2026, and the same for 27 Oct to 21 Dec 2025. Google is judged against these.

Then set the three campaigns to Enabled on a Monday to Wednesday morning Perth time so there are a few weekdays of data before the weekend.

## Days 1 to 14: do not touch bids

- Day 1 and 2: check spend is happening (A$25 to A$35 a day total), ads are Eligible, no disapprovals, clicks land on the right pages with the suffix intact.
- Day 3: Search terms report for both Search campaigns and the Shopping campaign. Add negatives for anything irrelevant (other brands, free, printable, map pdf, jobs). Do not add negatives for queries that are merely broad; two weeks of data first.
- Day 7: check Search impression share. If Shopping lost IS (budget) is above 30 per cent, that is fine at launch. If lost IS (rank) is above 70 per cent on the bottle group, raise the bottle bid to A$1.30.
- Day 14: first real read. Expect 300 to 500 clicks across the account and 3 to 8 orders. If zero orders and more than 300 clicks, stop and recheck conversion tracking before changing anything else.

## Bidding ladder

| Stage | Trigger | Shopping | Search |
|---|---|---|---|
| 1 Launch | Day 0 | Manual CPC, bottle A$1.10, tees A$0.40 | Manual CPC, cap A$1.00 (brand A$0.50) |
| 2 Tune | Day 14, then every second Monday | Bottle max CPC = Shopping conversion rate (last 30 days) times A$55, between A$0.60 and A$1.30. Week 3: if CPC is under A$1 and lost IS (rank) is above 60 per cent, go to A$1.30 | Raise the best 5 keywords by 20 per cent |
| 3 Smart bidding | 15 conversions in the last 30 days on that campaign (Campaigns view, Conversions column, Last 30 days) | Maximise conversion value, no target | Non brand: stays Manual CPC for good at A$5 a day (it cannot reach 15). Brand: stays Manual CPC; never Maximise conversions on brand |
| 4 Targets | 30 conversions in the last 30 days on that campaign, and two weeks after stage 3 | Target ROAS 200 per cent (Google renamed "Maximise conversion value with a target ROAS" to "Target ROAS" in June 2026) | not applicable |

Google's own threshold for Target ROAS is 15 conversions in 30 days at the account level (per Merchant Center ID for Shopping), so Google will start recommending it once brand conversions push the account past 15. Decline until the Shopping campaign itself shows 15. In the base case that is February or later at A$22 a day; in the optimistic case December. Never switch on fewer than 15; never set a target on the same day you switch strategy.

## Weekly routine (20 minutes, Monday)

1. Campaigns view, column set `EP weekly` (defined in `02-conversion-tracking.md`), last 7 days against the previous 7, and last 30 days. Conversions lag up to 72 hours, so re read last week's numbers too.
2. Search terms: add negatives, move any converting query to its own exact keyword.
3. Product groups: compare bottle vs tees cost per conversion. Tees at 100 clicks with no sale: bid to A$0.30. Tees at 150 clicks with no sale: pause the group. Campaigns > Products, last 7 days by impressions: any advertised variant at zero impressions means a feed or eligibility problem.
4. Budget: Shopping limited by budget and CPA under A$50 for two weeks running: raise Shopping by A$5 a day. CPA above A$70 for two weeks after week 4: lower bottle bid 15 per cent, not the budget.
5. Merchant Center > Products: any new disapprovals or warnings.
6. Triple Whale: blended CPA and MER with Google included, wholesale tag filtered out. This is the number that decides if Google stays.
7. Recommendations tab: read, then dismiss. Never auto apply.
8. Monthly: Auction insights on both Search campaigns (who is bidding on the brand and on park bottle terms), Change history filtered to Auto-applied, and the Purchase action's Diagnostics tab for enhanced conversions.

## Kill and scale rules

- Scale (add A$10 a day to Shopping): 4 weeks in, Google CPA inside A$39 to A$50 on 15 or more conversions, blended CPA not worse than before launch.
- Hold: Google CPA A$50 to A$70. Keep optimising, no budget change.
- Cut non-brand Search to A$2 a day: non-brand CPA above A$80 after 300 clicks.
- Pause the tees ad group: 150 clicks with no sale.
- Brand campaign at day 30: open Auction insights. Keep it if any competitor domain appears or brand clicks convert above 5 per cent at under A$0.30 a click. If the brand search page is uncontested and organic plus free listings already hold it, drop the budget to A$1 and move the A$2 to non brand.
- Brand on and off test, 5 to 18 Jan 2027: pause the brand campaign for two weeks and watch Search Console > Performance > Queries filtered "endless parks". If organic brand clicks rise by at least 80 per cent of the paused ad clicks, the ads were cannibalising: move the A$3 to non brand. If they rise by less than half, re enable.
- Day 30 on Shopping: fewer than 8 orders and CPA above A$90, do not raise bids, cut tees to A$0.30. 15 or more orders with CPA under A$60, go to stage 3 of the ladder.
- Generic bottle test (ad group `bottle_generic_test`): enable only if the Shopping search terms report shows generic "water bottle" queries converting in weeks 1 to 3. The Shopping grid for those queries is A$29 to A$80, so expect it to fail; 150 clicks with no sale and it goes back to paused.
- Stop Google entirely: blended new customer CPA worse than A$55 for 6 straight weeks with Google included, and Google reporting fewer than 10 orders a month at A$30 a day.

## Month 3 and beyond

- Add the mugs back into Shopping as their own product group (bid A$0.70) once the bottle group is on Smart Bidding and Christmas gift searches start (about 20 Nov).
- Test one full asset Performance Max only as a Google Ads experiment against Shopping, never alongside it on the same products, and only if Shopping is at Stage 4 of the ladder.
- Consider a Christmas gift ad group in non-brand Search from 15 Nov: "gifts for campers", "gifts for hikers", "christmas gifts for dad who loves camping".
