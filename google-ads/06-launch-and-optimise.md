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
9. Product groups: bottle A$1.10, tees A$0.60, everything else excluded.
10. Ads approved (status Eligible), not Limited or Disapproved.
11. Triple Whale: Google Ads connected so Google spend shows in the MER view.
12. Landing pages: the bottle product page shows A$87 and in stock. Old pages still indexed at A$58 and A$63 (the /pages/adventurebottle marketing page and an old collection snapshot) are fixed or redirected, so Merchant Center never sees a price mismatch.
13. Automated rules and scripts from `01-account-setup.md` are live and have run once in preview.
14. Keyword Planner check: Tools > Planning > Keyword Planner > Get search volume and forecasts, location Australia, paste every keyword in `05-keywords.csv`. Replace the estimated volumes in the competition notes with real numbers and drop any keyword showing zero volume.

Then set the three campaigns to Enabled on a Monday to Wednesday morning Perth time so there are a few weekdays of data before the weekend.

## Days 1 to 14: do not touch bids

- Day 1 and 2: check spend is happening (A$25 to A$35 a day total), ads are Eligible, no disapprovals, clicks land on the right pages with the suffix intact.
- Day 3: Search terms report for both Search campaigns and the Shopping campaign. Add negatives for anything irrelevant (other brands, free, printable, map pdf, jobs). Do not add negatives for queries that are merely broad; two weeks of data first.
- Day 7: check Search impression share. If Shopping lost IS (budget) is above 30 per cent, that is fine at launch. If lost IS (rank) is above 70 per cent on the bottle group, raise the bottle bid to A$1.30.
- Day 14: first real read. Expect 300 to 500 clicks across the account and 3 to 8 orders. If zero orders and more than 300 clicks, stop and recheck conversion tracking before changing anything else.

## Bidding ladder

| Stage | Trigger | Shopping | Search |
|---|---|---|---|
| 1 Launch | Day 0 | Manual CPC, bottle A$1.10, tees A$0.60 | Manual CPC, cap A$1.00 (brand A$0.60) |
| 2 Volume | Week 3, if CPC is under A$1 and lost IS (rank) above 60 per cent | Raise bottle to A$1.30 | Raise best 5 keywords by 20 per cent |
| 3 Smart bidding | 15 conversions in the last 30 days in that campaign | Maximise conversion value, no target | Maximise conversions, no target |
| 4 Targets | 30 conversions in the last 30 days | Target ROAS 190 per cent | Target CPA A$45 |

Never switch a campaign to Smart Bidding on fewer than 15 conversions; it will spend the budget learning on nothing. Never set a target on the same day you switch strategy; wait two weeks.

## Weekly routine (20 minutes, Monday)

1. Campaigns view, column set `EP weekly` (defined in `02-conversion-tracking.md`), last 7 days against the previous 7, and last 30 days. Conversions lag up to 72 hours, so re read last week's numbers too.
2. Search terms: add negatives, move any converting query to its own exact keyword.
3. Product groups: compare bottle vs tees cost per conversion. Cut tees bid 20 per cent if tees CPA is above A$40 after 100 clicks.
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
- Generic bottle test (ad group `bottle_generic_test`): enable only if the Shopping search terms report shows generic "water bottle" queries converting in weeks 1 to 3. The Shopping grid for those queries is A$29 to A$80, so expect it to fail; 150 clicks with no sale and it goes back to paused.
- Stop Google entirely: blended new customer CPA worse than A$55 for 6 straight weeks with Google included, and Google reporting fewer than 10 orders a month at A$30 a day.

## Month 3 and beyond

- Add the mugs back into Shopping as their own product group (bid A$0.70) once the bottle group is on Smart Bidding and Christmas gift searches start (about 20 Nov).
- Test one full asset Performance Max only as a Google Ads experiment against Shopping, never alongside it on the same products, and only if Shopping is at Stage 4 of the ladder.
- Consider a Christmas gift ad group in non-brand Search from 15 Nov: "gifts for campers", "gifts for hikers", "christmas gifts for dad who loves camping".
