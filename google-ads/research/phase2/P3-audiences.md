# P3 Audiences: Endless Parks Google Ads at A$30 a day

Written 15 Oct 2026. Builds on `PLAN.md` (Manual CPC ladder, Shopping A$22, Brand Search A$3, Non-brand Search A$5) and R02-R07 finding 28. Direct page loads were blocked, so every claim rests on search extracts of the cited pages; confirm menu labels on screen. 24 searches run.

Short version: at this budget audiences are for reporting, exclusion and new customer detection, not bidding. Build the lists this week so they accumulate, run everything in Observation at 0% for 30 days, exclude past purchasers from non-brand Search, and spend nothing on Display, YouTube or Demand Gen before day 60.

## 1 Findings

1. Observation is the default and the right mode. Google Ads Help (https://support.google.com/google-ads/answer/7365594, current): a new Search or Shopping campaign defaults to Observation, which keeps full reach and uses the segment for reporting and bid adjustments; Targeting narrows reach. The API docs (https://developers.google.com/google-ads/api/docs/targeting/targeting-settings) recommend Observation for Search and Shopping. Standard Shopping supports segments (https://support.google.com/google-ads/answer/2497941). High.

2. Bid adjustments only bite under Manual CPC or Maximise Clicks. Bidding FAQ (https://support.google.com/google-ads/faq/10286469, current): audience adjustments run -90% to +900%; Google's example is +25% for 30 day visitors. Under Target ROAS, Target CPA, Maximise Conversions and Maximise Conversion Value the percentages are ignored while exclusions and targeting still bind, and the numbers stay visible in the UI (ZATO, https://zatomarketing.com/blog/google-ads-bid-adjustments-when-they-work-when-they-dont-and-when-to-just-let-go; Bigeye 2026; PPC Mastery TPE 145). Adalysis (https://adalysis.com/blog/how-audience-bid-adjustments-work-with-target-cpa-target-roas-bidding/) says they shift serving priority instead; one source. Here adjustments matter only in the Manual CPC phase, about weeks 1 to 8. High on range and Smart Bidding, Med on priority.

3. Customer Match lists on Search need 100 users, a May 2025 change. Search Engine Land (https://searchengineland.com/google-slashes-customer-match-list-minimums-in-search-campaigns-to-100-users-455912): cut from 1,000 to 100 for Customer Match lists only, not remarketing lists. Google Ads Help (https://support.google.com/google-ads/answer/7474166): "All files submitted must have a minimum of 100 user records"; ads serve on active users, fewer than the total; a list stays eligible while 100 members were added or refreshed in 540 days. High.

4. A new account gets Customer Match in observation and exclusion only. Policy (https://support.google.com/adspolicy/answer/6299717, current): good policy and payment history required; "All policy-compliant advertisers can use Customer Match and similar audiences in the Observation setting and for exclusions." Secondary sources quoting the page (Relevant Audience, https://www.relevantaudience.com/google-ads-en/google-ads-customer-match-guide/; Ranking Co AU 2025, https://www.rankingco.com.au/google-ads-customer-match) say Targeting and manual bid adjustments need 90 days of history and over US$50,000 lifetime spend, about six years away at A$900 a month. High on observation and exclusion, Med on thresholds.

5. Two build routes from Shopify. Route A, Data Manager (https://support.google.com/google-ads-data-manager/answer/15496063): Tools > Data manager > Connect product > Shopify; needs the Google & YouTube app and a non-manager account; "Once the account is connected, Customer Match is turned on automatically"; every Shopify segment is preselected, 25 lists maximum; an announcement (https://support.google.com/google-ads-data-manager/announcements/13761680) says Shopify alone does not feed enhanced conversions. Route B, file upload (https://support.google.com/google-ads/answer/10589050): UTF-8 CSV, headers Email, Phone, First Name, Last Name, Country, Zip; Google hashes plain text or accepts SHA-256. Shopify's export carries those fields plus Accepts Email Marketing (https://help.shopify.com/en/manual/customers/import-export-customers). PPC Rebels (2026, one source): API uploads closed to new adopters 1 Apr 2026; irrelevant to UI use. Shopify Audiences is US and Canada Plus only (changelog May 2022). High on routes, Med on Shopify Audiences in 2026.

6. Website remarketing lists on Search still appear to need 1,000 active users. The Help page (https://support.google.com/google-ads/answer/7068417) did not carry the number in extract; OnePPC, Linear Design and Store Growers (https://www.storegrowers.com/remarketing-lists-for-search-ads-rlsa/) all say 1,000 in 30 days. Surfside PPC (2026, https://surfsideppc.com/blogs/google-ads/google-ads-remarketing) alone claims 100 everywhere. Display needs 100. The Audience manager size columns settle it. Med.

7. GA4 audiences fill from creation day only. Adnan Agic (https://adnanagic.com/blog/ga4-audiences-build-and-export-to-google-ads/), BlueFrog 2026 and Stackmatix 2026 agree: link GA4 Admin > Product links > Google Ads links with personalised advertising on; sync takes 24 to 48 hours; "the audience only populates going forward for Google Ads export"; a "no purchase within X days" step qualifies users only after the window closes; cart abandoners are add_to_cart at least once and purchase 0 times, 7 to 14 day membership; membership caps at 540 days. Med, no Analytics Help page retrieved.

8. 15 June 2026 change: Google Signals no longer gates Ads data. Dataslayer (https://www.dataslayer.ai/blog/ga4-google-ads-data-controls-june-15-2026), Seresa, Elsop and Kickstart Digital NZ (all 2026): Consent Mode ad_storage is now the single switch for ad cookies, exported audiences hold only ad_storage granted users, and ad_personalization control moves to Google Ads later in 2026. An Australian store with no consent banner grants ad_storage by default. Med, secondary only.

9. Segments available for Observation: in-market Sports & Fitness > Outdoor Recreational Equipment > Camping & Hiking Equipment; affinity Outdoor Enthusiasts and Travel Buffs (Venture Stream, https://venturestream.co.uk/blog/definitive-list-google-analytics-affinity-categories-market-segments/; Jerweejee 2024). "Gifts & Occasions" is a top level in-market category from memory, unconfirmed in extract. Nothing covers drinkware. Custom segments built from search terms are not available on Search or Shopping. Med.

10. New customer acquisition goal. Help (https://support.google.com/google-ads/answer/14005157): Performance Max, Search or Demand Gen; Accelerate with Google (early Sep 2026, https://business.google.com/us/accelerate/resources/articles/best-practices-for-new-customer-acquisition-goals/) adds Shopping for the two standard modes plus a High Value mode. New Customer Value needs tROAS or Maximise Conversion Value and a Purchase goal; New Customer Only runs on tCPA (https://support.google.com/sa360/answer/12455468). Detection (https://support.google.com/google-ads/answer/14005876): auto detection from up to 540 days of purchase tracking is default and "less comprehensive"; Customer Match lists complete it. With no history every buyer looks new and the uplift inflates every conversion. Google prefers "bid higher" over "only new customers". High.

11. PMax data exclusions arrived in 2026. Search Engine Land (https://searchengineland.com/google-new-pmax-exclusions-expanded-reporting-features-472695): Customer Match and website visitor lists can be excluded under Campaign settings > Your data exclusions; dated Jan to Apr 2026 by different sources, most say March; covers Search, Display, Shopping, Video and Discover inventory inside PMax, not a hard wall (Eddie Cheng 2026). Med to High.

12. Demand Gen is out on Google's numbers. Help (https://support.google.com/google-ads/answer/17122651): daily budget at least 10 times target CPA, or US$100 a day on Maximise strategies; API docs (https://developers.google.com/google-ads/api/docs/demand-gen/create-campaign) say 15 times tCPA. At a A$45 target that is A$450 to A$675 a day. Search Engine Land calls it "a money suck" for small budgets (https://searchengineland.com/google-demand-gen-campaigns-migration-and-best-practices-433014). Lookalike seeds need 1,000 matched people. High.

13. Display remarketing to cart abandoners: thin evidence. MSI Report 21-133 (2021, https://www.msi.org/wp-content/uploads/2021/09/MSI_Report_21-133-1.pdf), a retailer field experiment: lift follows an inverted U in time since abandonment, is higher for recent single category carts, and retargeting too soon can backfire. Vendor figures: up to 75% of retargeting conversions non incremental (Webtonic 2026); 20% incremental at usual frequency, 40% when limited to cart abandoners (Metricuno). Nothing covers A$2 to A$5 a day. Klaviyo's abandoned checkout flow and Meta Advantage+ already reach the same people. Med on direction, Low on numbers.

14. Australian privacy, Oct 2026. OAIC Nov 2024 guidance: pixels are lawful if APP compliant. June 2026 determinations against Medmate Australia and Monash IVF found breaches of APPs 3.3, 5.1 and 7.1 for pixels feeding targeted ads; the Commissioner adopted "individuation" as the test for reasonably identifiable and treated behaviour based retargeting as direct marketing under APP 7.1; ad tech is a 2025-26 priority (Allens Jul 2026, https://www.allens.com.au/insights-news/insights/2026/07/tracking-pixels-targeted-advertising-and-compliance-lessons-from-recent-oaic-determinations/; Clayton Utz Jul 2026; ADMA). Tranche 2 exposure draft released 31 Aug 2026, consultation closed 18 Sep 2026, not law; it keeps the A$3 million small business exemption (Gadens Sep 2026, https://www.gadens.com/insights/tranche-2-privacy-reforms-key-changes; ComplianceKit; 4IT), requires consent to "trade" personal information including list exchanges, and covers group level targeting (Bird & Bird; Corrs). Nothing from OAIC on hashed lists. The APPs do not bind Endless Parks today, but Google's policy contractually requires lawful first party collection and notice. Med.

15. Practitioners agree for small accounts: Observation first, wait 2 to 4 weeks, first adjustment +15 to +30% for recent visitors (Store Growers; Linear Design); exclude converters for one off products (Datafeedwatch); upload Customer Match even when small (Jyll Saskin Gales, https://learn.jyll.ca/blog/should-you-upload-your-customer-list-in-google-ads-customer-match). Low to Med, opinion not tests.

## 2 Exactly what to do for Endless Parks

Volume reality: 4,000 sessions a month gives an "all users 30 days" list near 3,000, Search eligible within weeks. Cart without purchase over 14 days is perhaps 100 to 200 users: Display eligible only. A GA4 purchasers list grows about 65 a month from creation and will not reach 1,000 before 2028, so the purchaser role goes to the Shopify Customer Match list (thousands of buyers, 100 user rule), which on a new account can only observe and exclude. That is its one job anyway.

### This week, before the account exists

| # | Where | Do | Why |
|---|---|---|---|
| 1 | GA4 > Admin > Data display > Audiences > New audience > Create a custom audience | `EP All users 30d` (session_start, 30 days); `EP Product viewers 30d` (view_item, 30 days); `EP Cart no purchase 14d` (Include add_to_cart; Exclude permanently purchase; 14 days); `EP Purchasers 540d` (purchase, 540 days) | Lists fill from creation day only. Wholesale draft orders never fire storefront GA4 purchase |
| 2 | Shopify admin > Customers > Segments > Create segment | `EP purchasers`: `number_of_orders > 0 AND customer_tags NOT CONTAINS 'wholesale'`; `EP subscribers`: `email_subscription_status = 'SUBSCRIBED'` | Data Manager imports segments as Customer Match lists |
| 3 | Shopify admin > Settings > Policies > Privacy policy | One sentence: hashed contact details may be shared with advertising platforms (Google, Meta) to show or suppress ads, with an opt out email | Customer Match policy requires notice; OAIC individuation test |
| 4 | Shopify admin > Settings > Customer privacy | Confirm no banner or data sale opt out applies to Australia | Since 15 Jun 2026 only ad_storage granted users enter audiences |

### Account build days, 22 to 24 Oct, after `02-conversion-tracking.md`

5. GA4 link with "Enable personalised advertising" ticked (Step 4 of 02). Next day, Tools > Audience manager > Your data segments should list the four GA4 audiences with Search, Display and YouTube sizes.

6. Customer Match, Route A: Tools > Data manager > Connect product > Shopify > sign in as endlesspks > untick every segment except `EP purchasers` and `EP subscribers` > Connect. Check Audience manager in 24 to 48 hours; both should read above 100 for Search. Route B if A fails: Customers > Export > All customers > CSV for Excel; keep Email, First Name, Last Name, Country (AU), Zip with Google's exact headers; Tools > Audience manager > Your data segments > + > Customer list > Upload plain text data > tick the policy box. Delete the CSV afterwards.

7. Check Tools > Audience manager > Your data sources for a Google Ads tag fed by the Shopify channel. If active, Google auto creates All visitors, All converters and dynamic lists (Product viewers, Shopping cart abandoners, Past buyers); add them in Observation too. Low confidence the channel installs it; check, do not assume.

8. Observation segments on all three campaigns at launch, 0% on every one. Campaigns > campaign > Audiences, keywords and content > Audiences > Edit audience segments > Add to: Campaign > Observation > Browse:
   - In-market: Sports & Fitness > Outdoor Recreational Equipment > Camping & Hiking Equipment; Gifts & Occasions (top level plus any gift sub segment); Travel.
   - Affinity: Outdoor Enthusiasts; Travel Buffs.
   - Your data: the four GA4 lists plus Customer Match `EP purchasers` and `EP subscribers`.
   - Demographics: Age, Gender and Household income (available in Australia) in Observation, no adjustments.
   Shopping takes the same list at campaign level, or on its single ad group if that is all the UI offers.

9. Exclusions at launch: non-brand Search only. Audiences > Exclusions > Add exclusion > Campaign > Customer Match `EP purchasers`. Not on Brand: a purchaser typing "endless parks" is navigating, and a cheap brand click beats losing them to a stockist listing. Not on Shopping: tees are new to every bottle buyer and a repeat order at A$61 contribution is profitable at A$1 a click.

10. New customer acquisition: off at launch, until the Customer Match purchasers list is live and the campaign runs Maximise Conversion Value.

### Day 30 review, about 24 to 27 Nov, still Manual CPC

11. Campaign > Audiences table, last 30 days. Adjust only segments with 100 or more clicks or 5 or more conversions; otherwise leave 0% and wait to day 60.

| Segment | Where | Day 30 action |
|---|---|---|
| EP All users 30d (or Google Ads All visitors) | Non-brand Search, Shopping | +20% if the Search size column shows eligible; otherwise nothing |
| EP Cart no purchase 14d | Non-brand Search, Shopping | +30% if Search eligible; expect it not to be |
| EP Purchasers 540d (GA4) | Brand Search | +15% once Search eligible, not before 2028; until then the Customer Match list observes and a new account cannot adjust it |
| Camping & Hiking Equipment, Outdoor Enthusiasts | Shopping, Non-brand | +15% if CVR is 1.5 times the campaign on 100+ clicks; -20% on 100+ clicks and zero conversions |
| Gifts & Occasions | Shopping | Watch until 20 Nov; 20 Nov to 15 Dec +20% if CVR holds at campaign average |
| Age 18 to 24 | All | -20% on 100+ clicks and no conversions; Meta says broad wins, so no harder |

12. When a campaign moves to Maximise Conversion Value (15 conversions in 30 days per PLAN.md) its percentages stop working; leave them for reporting. Exclusions keep working.

### Day 60 and later

13. New customer acquisition on Shopping, once it runs Maximise Conversion Value and `EP purchasers` is live. Goals > Conversions > Settings > Customer acquisition: tick the Customer Match lists as existing customers, new customer value A$20 (about 25% of the A$87 bottle; repeat rate is low, so a larger uplift overstates value). Then Campaign settings > Bidding > Customer acquisition > "Bid higher for new customers than existing customers". Never "Only bid for new customers". Judge new versus returning in Shopify, because Google's value column now carries the A$20 uplift.

14. Display remarketing test only if all four hold: `EP Cart no purchase 14d` above 500 users; Google gross CPA inside A$39 to A$50; Klaviyo abandoned checkout flow recovering under 10% of abandoners; Meta reach to site visitors confirmed low. Then one Display campaign, A$3 a day, Manual CPC A$0.40, Targeting mode on `EP Cart no purchase 14d`, exclusion `EP purchasers`, frequency cap 3 a day, sensitive content excluded, responsive display ads with bottle and sticker pack imagery, headline "Tick off every National and Marine Park", no discount language. Kill after 30 days unless Shopify shows a lift in recovered carts. Expect it not to be worth it.

15. YouTube and Demand Gen: no. Floors are 10 to 20 times target CPA (finding 12).

16. If PMax is ever added (week 8 or later): Campaign settings > Your data exclusions > `EP purchasers`; Brand exclusions list with "endless parks"; audience signals from `EP All users 30d` and the Customer Match lists.

## 3 Where sources disagree

- Search minimum for website remarketing lists: 1,000 (Store Growers, OnePPC, Linear, Search Engine Land 2025) versus 100 everywhere (Surfside PPC 2026, alone). Plan assumes 1,000; the size column settles it.
- Customer Match targeting tier: the policy extract gives observation and exclusions for all compliant advertisers; the 90 day and US$50,000 figures are secondary only. Unreachable here either way.
- Audience adjustments under Smart Bidding: ignored (ZATO, Bigeye, PPC Mastery) versus serving priority (Adalysis). No practical difference, adjustments are edited only under Manual CPC.
- PMax data exclusions launch: Jan, Mar or Apr 2026; all agree it exists now.
- Demand Gen floor: 10 times tCPA (Help) versus 15 times (API docs). Both exclude it.
- Data Manager Shopify connector: Help says Customer Match supported; the announcement excludes Shopify from enhanced conversions only.
- Small business exemption: retained in the Aug 2026 draft (Gadens, ComplianceKit, 4IT) versus "removal expected 2026-27" (commentary from about Apr 2026). Treat as retained, comply anyway.

## 4 Open questions for Jake

1. Which tag marks wholesale customers in Shopify, and is it on every stockist account? The purchasers segment depends on it.
2. Does Settings > Customer privacy show a consent banner or data sale opt out for Australia?
3. How many Shopify customers have an order, and what is the returning customer rate (Analytics > Customers)? Sets the A$20 new customer value.
4. Is excluding past purchasers from non-brand Search acceptable given tees are a cross sell? The alternative is Observation only.
5. Does the privacy policy already mention sharing hashed contact data with advertising platforms?
6. Does endlesspks hold Editor on the GA4 property? Audience creation needs it.
7. Should the 7,720 Klaviyo subscribers go up as a separate Customer Match list, or is the Shopify subscribers segment enough?

## 5 Sources

Google and Shopify documentation (current unless dated):
- https://support.google.com/google-ads/answer/7365594 Targeting and Observation
- https://support.google.com/google-ads/answer/2497941 About audience segments
- https://support.google.com/google-ads/answer/7068417 Data segments for Search
- https://support.google.com/google-ads/faq/10286469 Bidding FAQ, adjustment range
- https://support.google.com/adspolicy/answer/6299717 Customer Match policy
- https://support.google.com/google-ads/answer/7474166 Customer Match list size issues
- https://support.google.com/google-ads/answer/10589050 Customer Match file upload
- https://support.google.com/google-ads-data-manager/answer/15496063 Data Manager, Shopify
- https://support.google.com/google-ads-data-manager/announcements/13761680 Data Manager announcements
- https://support.google.com/google-ads/answer/14005157, /14005876 and https://support.google.com/sa360/answer/12455468 New customer acquisition
- https://business.google.com/us/accelerate/resources/articles/best-practices-for-new-customer-acquisition-goals/ (Sep 2026)
- https://support.google.com/google-ads/answer/17122651 Demand Gen budget guidance
- https://developers.google.com/google-ads/api/docs/demand-gen/create-campaign and /docs/targeting/targeting-settings and /docs/remarketing/audience-segments/lookalike-audiences
- https://help.shopify.com/en/manual/customers/import-export-customers
- https://changelog.shopify.com/posts/shopify-audiences-launches-to-help-merchants-find-new-buyers (May 2022)

Trade press and practitioners:
- https://searchengineland.com/google-slashes-customer-match-list-minimums-in-search-campaigns-to-100-users-455912 (May 2025)
- https://searchengineland.com/google-new-pmax-exclusions-expanded-reporting-features-472695 (2026)
- https://searchengineland.com/google-demand-gen-campaigns-migration-and-best-practices-433014
- https://zatomarketing.com/blog/google-ads-bid-adjustments-when-they-work-when-they-dont-and-when-to-just-let-go
- https://adalysis.com/blog/how-audience-bid-adjustments-work-with-target-cpa-target-roas-bidding/
- https://www.bigeyeagency.com/insights/google-ads-bid-adjustments-in-2026-what-still-works-whats-changed-and-where-most-campaign-managers-get-it-wrong (2026)
- https://www.ppcmastery.com/newsletter/tpe-145-why-bid-adjustments-are-dead-and-what-to-do-instead
- https://www.storegrowers.com/remarketing-lists-for-search-ads-rlsa/, /google-customer-match/, /demand-gen-audiences/
- https://learn.jyll.ca/blog/should-you-upload-your-customer-list-in-google-ads-customer-match
- https://www.relevantaudience.com/google-ads-en/google-ads-customer-match-guide/
- https://www.rankingco.com.au/google-ads-customer-match (2025)
- https://adnanagic.com/blog/ga4-audiences-build-and-export-to-google-ads/
- https://bluefroganalytics.com/blog/ga4-audiences-remarketing-lists/ (2026) and https://www.stackmatix.com/blog/ga4-audiences (2026)
- https://www.dataslayer.ai/blog/ga4-google-ads-data-controls-june-15-2026 and https://seresa.io/blog/attribution-measurement/google-signals-loses-ad-authority-june-15-remarketing-lists-shrink (2026)
- https://surfsideppc.com/blogs/google-ads/google-ads-remarketing (2026, lone 100 user claim)
- https://venturestream.co.uk/blog/definitive-list-google-analytics-affinity-categories-market-segments/
- https://www.eddiecheng.com/blog/paid-acquisition-systems/pmax-demand-gen-youtube-exclusion-strategy (2026)
- https://ppcrebels.com/en/data-manager-first-party-data-google-ads-2026/ (2026)

Retargeting evidence:
- https://www.msi.org/wp-content/uploads/2021/09/MSI_Report_21-133-1.pdf (2021)
- https://www.webtonic.io/blog/retargeting (2026) and https://www.metricuno.com/cart-recovery-retargeting

Australian privacy:
- https://www.allens.com.au/insights-news/insights/2026/07/tracking-pixels-targeted-advertising-and-compliance-lessons-from-recent-oaic-determinations/ (Jul 2026)
- https://www.claytonutz.com/insights/2026/july/oaic-determines-the-use-of-tracking-pixels-did-not-track (Jul 2026)
- https://adma.com.au/resources/privacy-series-oaic-targets-marketing-practices-2025-26-regulatory-priorities
- https://www.gadens.com/insights/tranche-2-privacy-reforms-key-changes (Sep 2026)
- https://www.twobirds.com/en/insights/2026/australia/tranche-2-privacy-reforms-are-here and https://www.corrs.com.au/insights/australias-privacy-act-reforms-fundamental-changes-proposed-in-new-exposure-draft (2026)
- https://compliancekit.co/blog/oaic-small-business-exemption-removed (2026)
