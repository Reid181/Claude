# P6. Automation and reporting for a small account (Oct 2026)

Scope: automation and reporting for a three campaign, A$30 a day account beside Meta at A$150 a day. Builds on `01-account-setup.md` Step 3, `02-conversion-tracking.md` (`EP weekly` columns, Triple Whale) and `06-launch-and-optimise.md` (weekly routine, kill and scale rules); nothing there is repeated. Page loads are blocked in this session, so findings rest on search extracts read 15 Oct 2026; confirm menu labels on screen.

## 1. Findings

1. Disapproved ads script. Nils Rooijmans' "Report Disapproved Ads" lists disapproved ads with the reason, writes to a Sheet and emails; v2.0 moved from AWQL to GAQL and added policy findings. Google emails disapprovals natively, so the script adds detail and a record. https://nilsrooijmans.com/google-ads-script-disapproved-ads-alerts/ (undated, about mid 2025). Confidence High on function, Med on running unchanged in Oct 2026 (finding 9).

2. Disapproved products script. Rooijmans' version emails when products "that got a significant number of clicks are disapproved", with a configurable minimum click threshold and date range, run daily. https://nilsrooijmans.com/google-ads-script-disapproved-products-alerts/ (undated). Acuto's writes reasons and fixes to a sheet; chiliad's writes newly disapproved products to a sheet. Confidence Med. At A$22 a day across seven variants the click threshold must be 0.

3. Budget pacing script. Acuto's Monthly Budget Pacing Script "tracks monthly budget VS spend month to date" and "sends email alerts when account has spent over 50% within first 10 days of the month or when account has reached 90% of the spend". https://acuto.io/blog/monthly-budget-pacing-script/ (in Lunio's 2026 roundup). Cypress North's daily monitor is the lighter option. Confidence High on function, Med on compatibility.

4. Monthly cap and the June 2026 pacing change. Monthly spending limit is average daily budget times 30.4, so A$30 a day caps at A$912. https://support.google.com/google-ads/answer/10486536. Four vendor pages say that from 1 June 2026 scheduled campaigns are paced to the full monthly limit regardless of hours off (https://hush.digital/google-ads-budget-pacing-update-june-2026/); no Google page found. Confidence High on 30.4, Low on the June change. An ad schedule can never serve as a spend cap.

5. Budget report. Three figures: monthly spending limit, monthly forecast, cost to date; forecast "based on historical campaign performance as well as other relevant signals" with a shaded confidence band. Only for average daily budgets. https://support.google.com/google-ads/answer/9962086. Confidence High.

6. Search term n-gram. Mike Rhodes' free repo https://github.com/mikerhodesideas/free holds `ngram`, `pmax-search-terms-v4`, `search-term-alert`, `search-term-alert-evolution`. The free `ngram` is for Performance Max product titles and search categories ("2 bubble charts ... single-word nGrams", https://mikerhodes.circle.so/c/free-scripts/ngram, about 900 days old), not Search terms; the 1 to 3 word negative finder is his paid script. Free search term n-gram scripts: Brainlabs, and Ayima at https://github.com/rjfingilby/google-ads-ngrams. Confidence High, Med on freshness.

7. Zero impressions products cannot be found by a script filter. Scripts forum advisor: the runtime now uses Google Ads API reporting, which "by default, omits rows with zero impressions" when segmented. https://groups.google.com/g/adwords-scripts/c/iS-nSdOO-PM. The API's shopping_performance_view reports by product_item_id. Confidence High. A zero impressions report must be a set difference against an expected ID list, or a UI check.

8. Automated rules. Help covers alerts by setting a condition and choosing Send email. https://support.google.com/google-ads/answer/2497710. Practitioners add: no OR, so one check per rule, and "only if there are changes or errors" stops repeats (https://ppcrebels.com/en/google-ads-automated-rules-2026/). Confidence High.

9. Scripts platform changes. Documentation refreshed September 2025 (https://ads-developers.googleblog.com/2025/09/google-ads-scripts-documentation-upgrade.html). A November 2025 forum thread reports "Environment Locked to Legacy API" blocking some builder calls (anecdotal). Developer tokens sunset 9 Sep 2026 affects the API, not scripts. One roundup says a July 2026 Terms update covers third party automation scripts (https://commonthreadco.com/blogs/coachs-corner/google-ads-changes-2026, single source). Confidence Med. Preview before scheduling, re preview monthly.

10. Data retention from 1 June 2026. Five sources agree: hourly, daily and weekly data kept 37 months, monthly and coarser 11 years, in UI, API and scripts (https://calibrate-analytics.com/insights/2026/05/05/Google-Ads-Announces-37-Month-Limit-for-Historical-Data-Retention/, 5 May 2026). One site lists 18 and 13 month tiers, uncorroborated. Confidence Med. Bites a new account in 2029; export monthly anyway.

11. Looker Studio. The native Google Ads connector is free, with "Overall Account Fields" (https://support.google.com/looker-studio/answer/7020275). Third party field lists include Search Impr. Share and Search Top IS. 360om reports Google removed Auction Insights fields and that "entities such as AdGroup or Campaign, with zero impressions will not appear in Google Ads data sources" (https://www.360om.agency/news-insights/google-removes-auction-insights-from-looker-studio-what-you-need-to-know, single source). Confidence High on the connector, Med on fields.

12. GA4. Session key event rate is in Traffic acquisition by default; switch the primary dimension to Session campaign or Session source / medium. The Landing page report is session scoped; filter it to one campaign (https://www.orbitmedia.com/blog/measure-landing-page-performance-ga4/). Google Ads attributes to click date, GA4 to event date. 2026 changes, consultancies only: per key event attribution settings (April), one merged Attribution report, acquisition lookback cut from 90 days, and from June ad_storage alone governs ads data on linked properties (https://almcorp.com/blog/ga4-attribution-model-restructure-april-2026/). Confidence Med. With no Australian banner ad_storage stays granted, so June is neutral.

13. Triple Whale. Platform reported metrics ("Channel's reported Cost Per Acquisition") are separate from Pixel metrics; Pixel New Customer CPA is spend divided by Pixel new customer purchases (https://kb.triplewhale.com/en/articles/6855429-attribution-dashboard-metrics-library). Total Impact spreads credit across all pre purchase touchpoints. Each connected channel adds spend to blended MER on Summary. The BFCM 2026 guide recommends sending Triple Whale attributed conversions back to Google (https://www.triplewhale.com/blog/google-ads-black-friday). Confidence High on definitions, Med on UI.

14. Shopify reconciliation. Sales attributed to marketing counts only sales "that can be directly tied to marketing efforts" via Shopify campaigns or UTM traffic (https://help.shopify.com/en/manual/reports-and-analytics/shopify-reports/report-types/default-reports/marketing-reports, old page). Order level UTM source, medium and campaign show in the order's Conversion summary, last touch, no spend. Free listings and organic land in Shopify's google bucket but never in paid conversions (https://weltpixel.com/blogs/news/why-google-ads-reports-fewer-conversions-than-shopify). One consultancy suggests a 5 per cent audit target and a 70 per cent enhanced conversions match rate (single source). Confidence Med.

15. Auto apply. Untick under Auto-apply on the Recommendations page and save; the History tab tracks what is on (https://support.google.com/google-ads/answer/10276359). No master switch; earlier auto applied ad suggestions stay active after opting out. Confidence High.

## 2. Exactly what to do for Endless Parks

Install in this order: notifications, rules, scripts, reports. Alerts go to endlesspks@gmail.com with jakereidmedia@gmail.com in copy unless Jake says otherwise.

### A. Native notifications (5 minutes)
1. Google Ads > bell icon > gear > Notification preferences: Email on for Disapproved ads and policy, Billing, Account access; off for Recommendations and Marketing.
2. Merchant Center 5382740922 > Settings > Preferences > Email notifications: tick product disapprovals and account issues (label to confirm).

### B. Automated rules (Tools > Bulk actions > Rules > +; all Send email, never Pause). Replaces plan Step 3.11.

| Rule | Type | Condition | Frequency |
|---|---|---|---|
| EP_limited_budget | Campaign | Status = Limited by budget; Campaign status Enabled | Daily 7am Perth, only if changes or errors |
| EP_ad_disapproved | Ad | Approval status = Disapproved; Ad status Enabled (second rule for Eligible (limited)) | Daily, only if changes or errors |
| EP_spend_no_sales | Ad group | Cost > A$40 and Conversions = 0, Last 14 days | Weekly Monday |
| EP_overspend | Campaign | Cost > A$50, Yesterday | Daily |
| EP_zero_impr | Campaign | Impressions < 20, Yesterday, status Enabled | Daily; catches outages |
| EP_cpa_breach | Campaign | Cost / conv. > A$70 and Conversions >= 5, Last 14 days | Weekly Monday |

Rules cannot see Merchant Center products; hence script C2.

### C. Scripts (Tools > Bulk actions > Scripts > + > paste > Authorise > Preview > Save > Frequency)
1. Disapproved ads: skip at launch; native email plus EP_ad_disapproved covers three ads. Add Rooijmans' script only if the native email proves slow.
2. Disapproved products: Rooijmans' script. At the top set the email, minimum clicks 0, date range LAST_7_DAYS, spreadsheet URL if asked. Enable Shopping Content API under Advanced APIs only if its notes require it. Daily 6am Perth. Fallback: chiliad's script.
3. Budget pacing: Acuto's script, MONTHLY_BUDGET 912, email, keep both alerts. Daily 6am. Raise the figure when the credit lands (`00`).
4. Zero impressions products. UI: Campaigns > Products (Shopping campaign > Products tab) > Last 7 days > add Impressions and Status > sort ascending. Script: a 40 line bespoke script Claude writes that queries shopping_performance_view for LAST_7_DAYS, collects segments.product_item_id, compares against a hard coded array of the seven expected IDs (three colours of the Australian National and Marine Parks bottle, four tees, from Merchant Center > Products) and emails the missing ones. Weekly Monday; Preview on day one.
5. Search terms: nothing at launch; 300 to 500 clicks a fortnight is readable in Campaigns > Insights and reports > Search terms. From month 2 install Rhodes' free `search-term-alert` and run the Brainlabs or Ayima n-gram script monthly to a Sheet. Not his `ngram`; it is Performance Max only.

### D. Budget report (2 minutes weekly)
Campaigns table > click the Budget figure > View budget report. Shopping limit should read A$669 (A$22 times 30.4) with the forecast within 10 per cent of it. Under 70 per cent means bids or feed are throttling spend; over 105 is front loading, allowed up to twice the daily budget.

### E. Looker Studio one page weekly (45 minutes once)
lookerstudio.google.com > Create > Data source > Google Ads > customer ID > Overall Account Fields > Connect > Create report. Date range control Last 7 days, comparison Previous period.

| Block | Element | Fields | Settings |
|---|---|---|---|
| 1 | Six scorecards | Cost, Conversions, Conv. value, Cost / conv., Conv. value / cost, Search impr. share | Change vs previous period as percentage |
| 2 | Table by campaign | Campaign; Cost, Impr., Clicks, CTR, Avg. CPC, Conversions, Cost / conv., ROAS, Search impr. share, Search lost IS (budget), Search lost IS (rank) | Sort by Cost; comparison on Cost, Conversions, Cost / conv. |
| 3 | Time series | Date at Week (ISO) by Cost and Conversions, two axes | Fixed last 12 weeks |
| 4 | Small table | Campaign; Conversions (by conv. time), Conv. value (by conv. time) | Feeds reconciliation H |
| 5 | Text box | The week's three decisions, typed | The page is the record |

A zero impression campaign vanishes from the source (finding 11), so a missing row is itself an alert. Share > Schedule delivery > Monday 7am Perth.

### F. GA4 (Google traffic only)
1. Reports > Acquisition > Traffic acquisition > primary dimension Session source / medium > search google / cpc > secondary dimension Session campaign. Columns: Sessions, Engagement rate, Key events (purchase only), Session key event rate, Total revenue. Read beside Meta's paid_social row.
2. Reports > Engagement > Landing page > filter Session source / medium exactly matches google / cpc. The bottle PDP should sit near the site's 1.6 per cent; under 0.8 for two weeks means the page, not the ads.
3. Advertising > Performance (Google Ads report) for GA4 side attribution; confirm labels, the workspace was rebuilt in 2026. Admin > Data display > Attribution settings: note the lookback window.

### G. Triple Whale and the MER logic
1. Integrations > Google Ads connected (plan Step 4.3). Summary > Global filter > Order tag does not contain wholesale.
2. Weekly on Summary: Ad spend (Meta plus Google), MER, Pixel New Customer CPA. Triple Whale's MER is spend divided by sales as a percentage, lower is better; 36 per cent equals blended ROAS 2.78.
3. The arithmetic. Baseline Meta about A$4,560 a month, retail sales about A$12,500, MER 36 per cent. Add Google at A$912 reporting ROAS 2.0 (A$1,824), about 70 per cent incremental (A$1,277): MER becomes 5,472 / 13,777 = 40 per cent. Rules: MER at or under 40 with new customer orders up, keep and scale per `06`; 40 to 42, hold; above 42 for six straight weeks, the `06` stop rule fires.
4. Attribution page: Last click for Google, Total Impact 7 day average for the blended view. Leave "send conversions back to Google" off; the one purchase source rule in `02` stands.

### H. Reconciling Google conversions with Shopify orders (monthly, 15 minutes)
1. Google Ads > Campaigns > last full month > columns Conversions (by conv. time) and Conv. value (by conv. time); these count on order date like Shopify.
2. Shopify > Analytics > Reports > Sales attributed to marketing > same month > group by UTM source and medium > source google, medium cpc. Exclude orders tagged wholesale. Spot check five orders' Conversion summary for google / cpc and the campaign ID.
3. Pass: Shopify google / cpc orders within 10 per cent of Google's by conv. time count; Triple Whale Google last click within 20 per cent of both. Google much higher: cross device credit, weight Google's column down. Shopify higher: the tag is missing orders, re run `02` Step 5.
4. Goals > Conversions > Purchase > Diagnostics: Recording, match rate above 70 per cent.

### I. Weekly 20 minute checklist (Monday, Perth morning)
1. (3 min) Looker page or Campaigns with `EP weekly`, last 7 vs previous 7: spend, orders, CPA, ROAS, Search IS per campaign.
2. (2 min) Budget report (D).
3. (5 min) Search terms, all three campaigns, last 7 days: negatives to the shared lists, converting queries to exact keywords.
4. (3 min) Campaigns > Products: every advertised variant has impressions. Merchant Center > Products: no new disapprovals.
5. (3 min) Triple Whale Summary: MER, new customer CPA, Google spend present.
6. (2 min) Recommendations: read, dismiss, apply nothing.
7. (2 min) Type the three decisions into the Looker text box.

### J. Monthly 60 minute checklist (first Monday)
1. (15 min) Reconciliation H.
2. (10 min) Change history > User: Auto-applied and Google Ads system, last 30 days; reverse anything. Recommendations > Auto-apply: every box unticked.
3. (10 min) Traps: Campaigns > Assets > Account-level automated assets (Automated promotions, Dynamic images, Longer headlines off); each campaign's Settings for Search partners, Display Network, AI Max, Broad match, Automatically created assets; Goals > Conversions for a new Primary action; any Performance Max or Smart campaign the Shopify app created. Dismiss the late 2026 pushes: Upgrade to AI Max, Add broad match keywords, Set a target ROAS, Expand to search partners, Upgrade to Performance Max, Raise your budgets.
4. (10 min) Scripts: Preview each, last run has no errors. Rules: each ran.
5. (5 min) Auction insights on both Search campaigns (UI only).
6. (5 min) GA4 F1 and F2 for the month.
7. (5 min) Export Campaigns and Search terms to a Sheet (finding 10).

## 3. Where sources disagree
- Rhodes' free n-gram: a roundup credits him with a search term n-gram; his page shows the free `ngram` is Performance Max only. Trust his page.
- June 2026 pacing for scheduled campaigns: four vendor blogs, no Google page. Probable, irrelevant at launch.
- Retention: 37 months and 11 years (five sources) versus 18 and 13 month tiers (one). Majority.
- Looker impression share: field lists keep Search Impr. Share; 360om says Auction Insights shares went. Both true.
- GA4 lookback: 90 to 30 (one source) versus "changed from 90" with no figure. Read it in Admin.
- Reconciliation tolerance: 5 per cent (one consultancy) versus the plan's 10. Keep 10; at 20 Google orders a month one order is 5 per cent.

## 4. Open questions for Jake
1. Which inbox gets alerts, and is jakereidmedia@gmail.com in copy?
2. Triple Whale plan: does it include the Google Ads integration and Attribution page, and is "send conversions back to Google" off?
3. Looker Studio or a Google Sheet for the weekly page? Looker needs a Google login with Read access on the Ads account.
4. Are wholesale draft orders consistently tagged `wholesale`?
5. Which attribution model is set in Shopify's Sales attributed to marketing report?
6. Is there GA4 admin access to read Attribution settings and link the Ads account?
7. Daily or weekly pacing email?

## 5. Sources
- https://support.google.com/google-ads/answer/9962086 About your budget report
- https://support.google.com/google-ads/answer/10486536 Budgets overview (30.4)
- https://support.google.com/google-ads/answer/2497710 Common ways to use automated rules
- https://support.google.com/google-ads/answer/10276359 Manage auto-apply recommendations
- https://support.google.com/looker-studio/answer/7020275 Connect to Google Ads
- https://developers.google.com/google-ads/api/docs/shopping-ads/reporting
- https://developers.google.com/google-ads/api/docs/deprecations
- https://ads-developers.googleblog.com/2025/09/google-ads-scripts-documentation-upgrade.html
- https://help.shopify.com/en/manual/reports-and-analytics/shopify-reports/report-types/default-reports/marketing-reports
- https://nilsrooijmans.com/google-ads-script-disapproved-ads-alerts/
- https://nilsrooijmans.com/google-ads-script-disapproved-products-alerts/
- https://acuto.io/blog/ad-disapproval-alert-script/
- https://acuto.io/blog/product-disapproval-alert-script-2/
- https://acuto.io/blog/monthly-budget-pacing-script/
- https://cypressnorth.com/paid-search-marketing/improve-daily-budget-monitoring-in-google-ads-with-this-simple-script/
- https://adsapp.report/solutions/newly-disapproved-products
- https://github.com/samlalonde/google-ads-account-budget-pacer-mcc
- https://github.com/mikerhodesideas/free
- https://mikerhodes.circle.so/c/free-scripts/ngram
- https://mikerhodes.com.au/scripts/neg
- https://github.com/rjfingilby/google-ads-ngrams
- https://groups.google.com/g/adwords-scripts/c/iS-nSdOO-PM
- https://groups.google.com/g/adwords-scripts/c/YRv60YGXxxQ
- https://groups.google.com/g/adwords-scripts/c/5YM1XycUUao
- https://www.lunio.ai/blog/google-ads-scripts-to-increase-performance-save-time
- https://ppcrebels.com/en/google-ads-automated-rules-2026/
- https://www.klientboost.com/google/google-ads-automated-rules/
- https://cypressnorth.com/paid-search-marketing/how-to-opt-out-of-auto-applied-recommendations-in-google-ads/
- https://hawksem.com/blog/google-ads-auto-apply/
- https://www.360om.agency/news-insights/google-removes-auction-insights-from-looker-studio-what-you-need-to-know
- https://adstralis.agency/en/blog/looker-studio-google-ads-templates/
- https://twominutereports.com/google-ads-to-looker-studio
- https://adnanagic.com/blog/ga4-reports-for-google-ads-advertisers/
- https://www.orbitmedia.com/blog/measure-landing-page-performance-ga4/
- https://www.analyticsmania.com/post/conversion-rate-in-google-analytics-4/
- https://almcorp.com/blog/ga4-attribution-model-restructure-april-2026/
- https://www.orr-consulting.com/post/ga4-attribution-changes-june-2026
- https://kingdatalab.com/blog/ga4-attribution-changes-2026/
- https://kb.triplewhale.com/en/articles/6855429-attribution-dashboard-metrics-library
- https://kb.triplewhale.com/en/articles/5960333-understanding-and-utilizing-attribution-models
- https://www.triplewhale.com/blog/google-ads-black-friday
- https://www.globenewswire.com/news-release/2026/06/18/3314106/0/en/Shirofune-Integrates-with-Triple-Whale-to-Automate-Attribution-Driven-Ad-Optimization-Across-Meta-Google-and-other-Platforms.html (18 Jun 2026)
- https://www.newmotionit.com/blog/shopify/setup-triple-whale-shopify-dtc-profit-tracking-attribution
- https://weltpixel.com/blogs/news/why-google-ads-reports-fewer-conversions-than-shopify
- https://www.convertmax.io/blog/shopify-google-ads-conversion-mismatch/
- https://www.ecorn.agency/blog/google-ads-for-shopify
- https://sherocommerce.com/blogs/insights/shopify-utm-tracking-standards
- https://calibrate-analytics.com/insights/2026/05/05/Google-Ads-Announces-37-Month-Limit-for-Historical-Data-Retention/ (5 May 2026)
- https://www.relevantaudience.com/google-ads-en/google-ads-2026-data-retention-policy-explained/
- https://yositeup.com/blog/google-ads-reporting-data-deleted-june-2026
- https://hush.digital/google-ads-budget-pacing-update-june-2026/
- https://prudentdigital.com/blog/google-ads-budget-pacing-change-2026/
- https://commonthreadco.com/blogs/coachs-corner/google-ads-changes-2026
