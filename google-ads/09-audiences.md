# 09. Audiences

At A$35 a day audiences are a reporting, exclusion and new customer detection tool, not a bid lever. Build the lists in the first week so they accumulate, run everything in Observation at 0 per cent for 30 days, exclude past purchasers from non brand Search, and spend nothing on Display, YouTube or Demand Gen before day 60. Full research in `research/phase2/P3-audiences.md`.

Three facts that shape this (Google Ads Help, read 15 Oct 2026):

- Audience bid adjustments only work under Manual CPC or Maximise clicks. Under Target ROAS or Maximise conversion value they are ignored while exclusions still bind. So adjustments matter in weeks 1 to 8 only.
- Customer Match lists on Search need 100 users since May 2025, but a new account can use Customer Match for Observation and exclusions only; targeting and bid adjustments on those lists need 90 days of history and a lifetime spend this account will not reach for years.
- GA4 audiences fill from the day they are created, and a GA4 purchasers list grows about 65 a month, so it will not reach Search eligibility (1,000) for years. The purchaser role belongs to the Shopify Customer Match list.

## This week (before the Ads account work)

| # | Where | Do |
|---|---|---|
| 1 | GA4 > Admin > Data display > Audiences > New audience > custom | `EP All users 30d` (session_start, 30 days); `EP Product viewers 30d` (view_item, 30 days); `EP Cart no purchase 14d` (include add_to_cart, exclude permanently purchase, 14 days); `EP Purchasers 540d` (purchase, 540 days). Wholesale draft orders never fire the storefront purchase event, so purchasers stay retail |
| 2 | Shopify admin > Customers > Segments > Create segment | `EP purchasers`: number_of_orders > 0 AND customer_tags NOT CONTAINS 'wholesale' (needs the wholesale tag on every stockist account); `EP subscribers`: email_subscription_status = 'SUBSCRIBED' |
| 3 | Shopify > Settings > Policies > Privacy policy | Add one sentence: hashed contact details may be shared with advertising platforms (Google, Meta) to show or suppress ads, with an opt out email. Google's Customer Match policy requires notice and the OAIC's 2026 determinations treat retargeting as direct marketing |
| 4 | Shopify > Settings > Customer privacy | Confirm no consent banner applies to Australia. Since 15 June 2026 only visitors with ad storage granted enter exported audiences; with no banner that is everyone |

## Account build days (after `02-conversion-tracking.md`)

5. GA4 link with personalised advertising on (already in `02`). Next day, Google Ads > Tools > Audience manager > Your data segments lists the four GA4 audiences with Search, Display and YouTube size columns.
6. Customer Match: Tools > Data manager > Connect product > Shopify > sign in as endlesspks > untick every segment except `EP purchasers` and `EP subscribers` > Connect. Check Audience manager in 24 to 48 hours; both should read above 100 for Search. Fallback: Customers > Export > CSV with only Email, First Name, Last Name, Country, Zip under Google's exact headers, uploaded at Tools > Audience manager > Your data segments > plus > Customer list. Delete the CSV afterwards.
7. Tools > Audience manager > Your data sources: if the Shopify channel's Google Ads tag shows as active, Google auto creates All visitors, All converters and Shopping cart abandoners lists; add them in Observation too.

## At launch: Observation on all four campaigns, 0 per cent everywhere

Campaign > Audiences, keywords and content > Audiences > Edit audience segments > Add to campaign > Observation:

- In market: Sports & Fitness > Outdoor Recreational Equipment > Camping & Hiking Equipment; Gifts & Occasions (and any gift sub segment shown); Travel.
- Affinity: Outdoor Enthusiasts; Travel Buffs.
- Your data: the four GA4 lists, `EP purchasers`, `EP subscribers`.
- Demographics (age, gender, household income) stay in Observation with no adjustments.

Exclusion at launch, non brand Search only: Audiences > Exclusions > `EP purchasers`. Not on brand (a purchaser typing "endless parks" is navigating and a cheap click beats losing them to a stockist listing). Not on Shopping (tees are new to every bottle buyer and a repeat order is profitable). Jake's call: if tees as a cross sell matter more than clean new customer numbers, skip the exclusion and observe only.

Customer acquisition goal: off at launch. Every buyer looks new to a fresh account, so New customer value would inflate every conversion.

## Day 30 review (about 24 to 27 Nov, still Manual CPC)

Campaign > Audiences table, last 30 days. Adjust only segments with 100 or more clicks or 5 or more conversions; otherwise leave 0 per cent until day 60.

| Segment | Campaigns | Day 30 action |
|---|---|---|
| EP All users 30d (or Google's All visitors) | Non brand Search, Shopping | plus 20 per cent if the Search size column shows eligible; otherwise nothing, the adjustment is ignored |
| EP Cart no purchase 14d | Non brand Search, Shopping | plus 30 per cent if Search eligible; expect it not to be |
| Camping & Hiking Equipment, Outdoor Enthusiasts | Shopping, non brand | plus 15 per cent if conversion rate is at least 1.5 times the campaign on 100 or more clicks; minus 20 per cent on 100 clicks with zero conversions |
| Gifts & Occasions | Shopping | watch only until 20 Nov; 20 Nov to 15 Dec plus 20 per cent if conversion rate holds at campaign average |
| Age 18 to 24 | all | minus 20 per cent on 100 clicks with no conversions; no harder, Meta says broad wins |

When a campaign moves to Maximise conversion value, its percentages stop working. Leave them for reporting and stop editing them. Exclusions keep working.

## Day 60 and later

- New customer acquisition on Shopping, once it runs Maximise conversion value and `EP purchasers` is live: Goals > Conversions > Settings > Customer acquisition, tick the Customer Match lists as existing customers, new customer value A$20; then the campaign's Bidding > Customer acquisition > "Bid higher for new customers". Never "Only bid for new customers". Read new versus returning in Shopify afterwards, because Google's value column then carries the A$20 uplift.
- Display remarketing to cart abandoners: default no. Klaviyo's abandoned checkout flow and the Meta campaign already reach these people, and the evidence for incremental lift at A$2 to A$5 a day is thin. Test only if the cart list passes 500 users, Google CPA is inside A$39 to A$50 and Klaviyo recovers under 10 per cent of abandoners: one Display campaign, A$3 a day, Manual CPC A$0.40, targeting the cart list, excluding purchasers, frequency cap 3 a day, no discount language, killed after 30 days without a visible lift in recovered carts.
- YouTube and Demand Gen: no. Google's own floors are 10 to 20 times target CPA a day.
- If Performance Max is ever tested (`08-pmax-experiment.md`): Campaign settings > Your data exclusions > `EP purchasers`; brand exclusions; audience signals from `EP All users 30d` and the Customer Match lists.
