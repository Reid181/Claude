# 11. Automation and reporting

Install in this order: notifications, rules, scripts, reports. Alerts go to endlesspks@gmail.com with jakereidmedia@gmail.com in copy unless Jake says otherwise. Full research in `research/phase2/P6-automation-reporting.md`.

## A. Native notifications (5 minutes)

1. Google Ads > bell icon > gear > Notification preferences: email on for Disapproved ads and policy, Billing, Account access; off for Recommendations and Marketing.
2. Merchant Center > Settings > Preferences > Email notifications: product disapprovals and account issues on.
3. Tax invoices: Billing > Settings > Document delivery options (or the payments profile's email preferences): monthly tax invoice by email.

## B. Automated rules (Tools > Bulk actions > Rules > plus; all Send email, never Pause)

Rules cannot use OR, so one check per rule. Set each to "only if there are changes or errors" where offered so the inbox stays quiet.

| Rule | Type | Condition | Frequency |
|---|---|---|---|
| EP_limited_budget | Campaign | Status = Limited by budget; campaign Enabled | Daily 7am Perth |
| EP_ad_disapproved | Ad | Approval status = Disapproved; a second rule for Eligible (limited) | Daily |
| EP_spend_no_sales | Ad group | Cost > A$40 and Conversions = 0, last 14 days | Weekly Monday. It will fire on the tees campaign's ad group and the tees Search ad group by design; that is the early warning for the 150 click kill rule in `06` |
| EP_overspend | Campaign | Cost > A$50 yesterday (Google may spend up to twice the daily budget on a day) | Daily |
| EP_zero_impr | Campaign | Impressions < 20 yesterday, campaign Enabled | Daily; catches outages and disapprovals |
| EP_cpa_breach | Campaign | Cost / conv. > A$70 and Conversions >= 5, last 14 days | Weekly Monday |

## C. Scripts (JAKE, week 2: scripts need the signed in user to authorise them)

Tools > Bulk actions > Scripts > plus > paste > Authorise > Preview > Save > Frequency. Preview before scheduling and re preview monthly; the scripts platform changed in 2025 and some older scripts break.

1. Disapproved products: Nils Rooijmans' script, https://nilsrooijmans.com/google-ads-script-disapproved-products-alerts/. Set the email, minimum clicks 0 (the account advertises 27 variants: 3 bottle colours and 24 tee size variants), date range LAST_7_DAYS, Sheet URL if asked. Daily 6am Perth. Fallback: the chiliad newly disapproved products script.
2. Budget pacing: Acuto's monthly pacing script, https://acuto.io/blog/monthly-budget-pacing-script/. MONTHLY_BUDGET 1064 (A$35 times 30.4), email, both alerts on. Daily 6am. Raise the figure when the credit lands. Lighter option: Cypress North's daily budget monitor.
3. Disapproved ads: skip at launch; the native email plus EP_ad_disapproved covers three ads. Add Rooijmans' disapproved ads script only if the native email proves slow.
4. Zero impression products: no script filter can find them (the reporting API omits zero rows). Use the UI weekly: Campaigns > each Shopping campaign > Products tab > last 7 days > sort by impressions ascending. Optional later: a short bespoke script that compares shopping_performance_view item IDs against the 27 expected IDs and emails the missing ones.
5. Search term mining: nothing at launch; 300 to 500 clicks a fortnight is readable by hand in Insights and reports > Search terms. From month 2, Mike Rhodes' free search-term-alert (github.com/mikerhodesideas/free) and a monthly n gram script (Brainlabs or github.com/rjfingilby/google-ads-ngrams) to a Sheet. Not his "ngram" script, which is Performance Max only.

## D. Budget report (2 minutes weekly)

Campaigns table > click the Budget figure > View budget report. The bottle Shopping campaign's monthly limit should read A$669 (A$22 times 30.4) and the tees campaign's A$152 (A$5 times 30.4), each with the forecast within 10 per cent. Under 70 per cent means bids or the feed are throttling spend; over 105 is front loading, allowed up to twice the daily budget on any day.

## E. Looker Studio one page weekly (45 minutes once)

lookerstudio.google.com > Create > Data source > Google Ads > the customer ID > Overall Account Fields > Connect > Create report. Date range control Last 7 days, comparison Previous period.

| Block | Element | Fields |
|---|---|---|
| 1 | Six scorecards with change versus previous period | Cost, Conversions, Conv. value, Cost / conv., Conv. value / cost, Search impr. share |
| 2 | Table by campaign, sorted by Cost | Cost, Impr., Clicks, CTR, Avg. CPC, Conversions, Cost / conv., Conv. value / cost, Search impr. share, Search lost IS (budget), Search lost IS (rank) |
| 3 | Time series, last 12 weeks, two axes | Week by Cost and Conversions |
| 4 | Small table for reconciliation | Campaign; Conversions (by conv. time), Conv. value (by conv. time) |
| 5 | Text box | The week's three decisions, typed in. The page is the record |

A campaign with zero impressions vanishes from the data source, so a missing row is itself an alert. Share > Schedule delivery > Monday 7am Perth. A Google Sheet is the fallback if Looker is not wanted.

## F. GA4, Google traffic only

1. Reports > Acquisition > Traffic acquisition > primary dimension Session source / medium > search google / cpc > secondary dimension Session campaign. Columns: Sessions, Engagement rate, Key events (purchase), Session key event rate, Total revenue. Read beside Meta's paid_social row.
2. Reports > Engagement > Landing page > filter Session source / medium exactly matches google / cpc. The bottle PDP should sit near the site's 1.6 per cent; under 0.8 for two weeks means the page, not the ads.
3. Admin > Data display > Attribution settings: note the lookback window (shortened in 2026). Google Ads attributes to click date, GA4 to event date, so the two never match exactly.

## G. Triple Whale and the MER logic

1. Integrations > Google Ads connected (`02`). Summary > Global filter > Order tag does not contain wholesale.
2. Weekly on Summary: ad spend (Meta plus Google), MER, Pixel new customer CPA. Triple Whale's MER is spend divided by sales as a percentage; lower is better; 36 per cent equals a blended ROAS of 2.78.
3. The arithmetic. Baseline Meta about A$4,560 a month, retail sales about A$12,500, MER 36 per cent. Add Google at A$1,064 reporting ROAS 2.0 (A$2,128), about 70 per cent incremental (A$1,490): MER becomes 5,624 / 13,990 = 40 per cent. Rules: MER at or under 40 with new customer orders up, keep and scale per `06`; 40 to 42, hold; above 42 for six straight weeks, the stop rule in `06` fires.
4. Attribution page: Last click for Google, Total Impact 7 day average for the blended view. Leave "send conversions back to Google" off; the one purchase source rule in `02` stands.

## H. Reconciling Google conversions with Shopify orders (monthly, 15 minutes)

1. Google Ads > Campaigns > last full month > columns Conversions (by conv. time) and Conv. value (by conv. time); these count on order date like Shopify.
2. Shopify > Analytics > Reports > Sales attributed to marketing > same month > group by UTM source and medium > google / cpc, wholesale excluded. Spot check five orders' Conversion summary for google / cpc and the campaign ID.
3. Pass: Shopify google / cpc orders within 10 per cent of Google's by conv. time count; Triple Whale Google last click within 20 per cent of both. Google much higher: cross device credit, weight Google's column down. Shopify higher: the tag is missing orders, re run `02` Step 5.
4. Goals > Conversions > Purchase > Diagnostics: Recording, enhanced conversions match rate above 70 per cent.

## I. Weekly 20 minute checklist (Monday, Perth morning)

1. (3 min) Looker page, or Campaigns with the `EP weekly` column set, last 7 versus previous 7: spend, orders, CPA, ROAS, Search impression share per campaign.
2. (2 min) Budget report (D).
3. (5 min) Search terms, all four campaigns, last 7 days: negatives to the shared list, converting queries to exact keywords.
4. (3 min) Campaigns > Products: every advertised variant has impressions. Merchant Center > Products: no new disapprovals.
5. (3 min) Triple Whale Summary: MER, new customer CPA, Google spend present.
6. (2 min) Recommendations: read, dismiss, apply nothing.
7. (2 min) Type the three decisions into the Looker text box. Billing > Promotions until the credit is Active.

## J. Monthly 60 minute checklist (first Monday)

1. (15 min) Reconciliation (H).
2. (10 min) Change history > User: Auto-applied and Google Ads system, last 30 days; reverse anything. Recommendations > Auto-apply: every box still unticked.
3. (10 min) Traps: Campaigns > Assets > Account-level automated assets (Automated promotions, Dynamic images, Longer headlines off); each campaign's Settings for search partners, Display Network, AI Max, broad match, automatically created assets; Goals > Conversions for any new Primary action; any Performance Max or Smart campaign the Shopify app created; any new product that the "Everything else" exclusion has kept out of Shopping. Dismiss the late 2026 pushes: Upgrade to AI Max, Add broad match keywords, Set a target ROAS, Expand to search partners, Upgrade to Performance Max, Raise your budgets.
4. (10 min) Scripts: preview each, last run without errors. Rules: each ran.
5. (5 min) Auction insights on both Search campaigns.
6. (5 min) GA4 F1 and F2 for the month.
7. (5 min) Export Campaigns and Search terms to a Sheet (Google keeps daily data 37 months from June 2026; the export is the long record).
