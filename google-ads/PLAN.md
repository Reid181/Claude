# Endless Parks: Google Ads launch plan

Written 15 Oct 2026. Budget A$30 a day. Products at launch: the Parks Bottle and the four Aussie Made tees. Meta stays the main channel at A$150 a day; Google's job is to catch the intent Meta creates and the gift and bottle searches that already exist.

Read this file top to bottom, then work through the numbered phases in order. Each phase lists the exact screen to open. `RUNBOOK.md` is the same work sequenced into browser sessions for Claude in Chrome, with URLs, inputs and checks per step. Companion files:

- `00-new-account-and-credit.md`: which account to use, the new advertiser credit terms and the dated sequence that protects it.
- `01-account-setup.md`: eligibility check, account creation, hygiene settings, Merchant Center link.
- `02-conversion-tracking.md`: one primary purchase conversion, enhanced conversions, how to verify.
- `03-feed-fixes.md`: Shopify product edits so Shopping ads match the right searches.
- `04-campaign-build.md`: click by click build of the three campaigns.
- `05-keywords.csv`, `05-negatives.txt`, `05-ad-copy.md`: what goes into the Search campaigns.
- `06-launch-and-optimise.md`: launch checklist, first 14 days, bidding ladder, weekly routine.
- `07-calendar.md`: dated actions from now to the end of January 2027.
- `08-pmax-experiment.md`: the only sanctioned way to test Performance Max, in January and only if four gates pass.
- `09-audiences.md`: GA4 and Customer Match lists to build now, Observation at launch, the purchaser exclusion, day 30 and day 60 rules.
- `10-landing-pages.md`: feed link, stale pages, the gclid redirect test, speed, the bottle page for cold traffic, the gift collection, policy checks.
- `11-automation-reporting.md`: notifications, the six rules, the two scripts, budget report, the Looker page, GA4, Triple Whale MER logic, reconciliation, weekly and monthly checklists.
- `research/`: the reports behind every number, including two adversarial reviews of this plan (`research/phase2/REVIEW-*.md`) whose findings are folded in.

## The decisions this plan is built on

| Decision | Value | Why |
|---|---|---|
| Daily budget | A$30 (about A$900 a month) | Enough for Shopping plus a small Search layer and to reach learning volume in 6 to 8 weeks |
| Account | The existing account (never run ads) if an offer is already on its Promotions page or a Google code is in the inbox; otherwise a new account created from the Australian offer page on 20 to 22 Oct, where the offer attaches at sign up | The business is new to Google Ads, so the credit (about A$600 matched) is available. Google's full pages say offers are not available on request, so an older empty account only qualifies if Google already pushed it an offer (`00-new-account-and-credit.md`). The credit lands around 21 Dec and funds most of January |
| Products | Bottle (hero) and tees | Jake's call. Mugs, stickers and lids stay in the feed for free listings but are excluded from paid |
| Landing pages | Bottle and gift ads: https://endlessparks.com/products/ultimate-adventure-bottle. Tees: https://endlessparks.com/pages/drop-01?view=ep-drop-01 | Jake's call, 15 Oct. The view parameter matters: the bare /pages/drop-01 is the "We're Jake and Joce" story page with no tees on it, and the site navigation reaches the drop content through /pages/about-us?view=ep-drop-01 with a Klaviyo _kx parameter that never goes into an ad URL. A gift collection page is an optional later test, not part of launch |
| Bottle economics | A$87 inc GST, landed cost about A$16 | Ex GST revenue A$79, minus cost and card fees leaves about A$61 contribution per bottle |
| Break-even CPA | About A$60 per bottle order | Spend more than this per order and the order loses money |
| Target CPA | A$39 to A$50 | Same working target as Meta. At A$45 each bottle order nets about A$16 |
| Target ROAS | 2.0 (200 per cent) is the destination; the first target typed in is the observed ROAS minus 15 per cent (never below 150), then raised toward 200 in steps; break-even 1.4 on a single bottle, 1.5 blended | A$87 divided by A$45 is 1.93 on a single bottle; two bottle bundles carry absorbed postage and tees carry thinner margin, so the blended target is 2.0. Google reports value GST inclusive and shipping excluded (the app sends Shopify's subtotal). Ladder in `06` |
| Tees | A$69, landed cost not confirmed | Assume A$25 to A$30 landed, so break-even CPA about A$31 to A$36. Tee max CPC A$0.40 (1.2 per cent conversion rate times a A$30 allowed CPA), not the bottle's A$1.10 |

## Campaign structure (A$30 a day)

| Campaign | Type | Budget | Bidding at launch | Job |
|---|---|---|---|---|
| ep_shop_bottle-tees_au_2026q4 | Standard Shopping, one ad group, product groups by custom label | A$22 | Manual CPC: bottle A$1.10, tees A$0.40 | Show the bottle on every relevant product search |
| ep_srch_brand_au_2026q4 | Search, exact and phrase, AI Max off | A$3 | Manual CPC A$0.50 | Own every "endless parks" search, block conquesting, measure brand demand for 30 days |
| ep_srch_nonbrand_au_2026q4 | Search, exact and phrase, AI Max off | A$5 | Manual CPC, A$1.00 cap | Launch on the park bottle cluster only (A$5 buys about five clicks a day); gifts and tees switch on 17 Nov |

Names mirror the Meta convention (ep_asc_bottle_broad_2026q4).

Not at launch: Performance Max, Demand Gen, YouTube, Display, Smart campaigns, search partners. Revisit PMax only after 8 weeks if Shopping holds a CPA inside A$39 to A$50.

## What to expect

Month 1 is a learning period. Three cases at A$30 a day (Shopping A$22, brand A$3, non brand A$5), Google reported numbers, whole account, from the budget model in `research/phase2/P1-budget-model.md`:

| Month 1 (27 Oct to 26 Nov) | Conservative | Base | Optimistic |
|---|---|---|---|
| Shopping CPC and conversion rate | A$1.05, 0.7 per cent | A$0.90, 1.1 per cent | A$0.70, 1.6 per cent |
| Shopping orders | 4 to 5 | 8 | 15 |
| Brand orders (A$3 a day underspends, that is normal) | 3 | 9 | 20 |
| Non brand orders | 1 | 3 | 5 |
| Account orders | about 9 | about 20 | about 41 |
| Shopping CPA | A$150 | A$82 | A$44 |
| Account ROAS (brand drags it up) | under 1 | about 2.0 | about 3 |

Month 2 (gift season) improves conversion rate but raises CPC 15 to 25 per cent; month 3 (road trips) has cheaper clicks. Base case: Google adds about 20 reported orders a month to the store's 62 to 65 at a reported CPA near A$45, and Shopping on its own sits near a ROAS of 1.1 in month 1 and 1.4 to 1.5 by month 2. Smart Bidding will not be reachable on Shopping inside the first quarter in the base case; Manual CPC for the quarter is the plan, not a failure.

Judge Google on blended Shopify and Triple Whale numbers after 6 to 8 weeks, not on month 1 alone and not on Google's own conversion column. Weight reported orders for incrementality (brand about 0.4, Shopping about 0.7, park bottle Search about 0.9); on that basis the base case month 2 is about 16 incremental orders for A$912, a CPA near A$58, just inside break-even. The real test is whether total new customer orders rise while blended new customer CPA stays inside A$40 to A$50, read year on year against 27 Oct to 21 Dec 2025 with Meta held at A$150 a day.

## Phases and timing

1. Credit decision and feed (16 to 19 Oct): `00` Step A look and the A or B call on 16 Oct; `03-feed-fixes.md`, `10-landing-pages.md` A to C and G, `09-audiences.md` week one steps. Then 3 to 5 days for Merchant Center to re-approve.
2. Account (20 to 22 Oct): `00` Step A continues or Step B, then `01-account-setup.md` Steps 3 and 4. Half a day. Not earlier, so the credit's clocks are not wasted.
3. Tracking (22 to 24 Oct): `02-conversion-tracking.md` and the Customer Match connection. Two hours plus a test order.
4. Build (by 24 Oct): `04-campaign-build.md`, then the rules and the Looker page in `11`. Three hours.
5. Launch (by 27 Oct, no later than 1 Nov): `06-launch-and-optimise.md`. Shopping needs data before the Christmas gift window opens around 20 Nov.
6. Optimise (weekly): same file.

## What the competition research changes

- Nobody Australian competes on "national parks water bottle" and its variants; the organic results are US sellers (Let's Wander at US$44.95 "50% off", Etsy, Amazon US) whose bottles only cover US parks. Those queries are cheap and winnable and the Search campaign is built around them.
- Generic bottle queries ("1.2l water bottle", "insulated water bottle with straw") sit in a A$29 to A$80 Shopping grid against Amazon AU, Stanley, Yeti and Frank Green. An A$87 bottle loses on price, so they are left to Shopping with a park qualified title and never bid on in Search.
- Gift queries are owned by BCF, Anaconda, Snowys, Paddy Pallin and Macpac and get 2 to 3 times more expensive from mid November. "gifts for grey nomads" and road trip gifts have no big box owner and are the gift angle to own.
- Awesome Maps (world map sticker bottle, about A$105, ships from an AU warehouse) is the one direct rival likely to advertise in Australia. Add it as a negative only if it shows up in search terms.
- Tiny Treasures Denmark lists the bottle at A$85, A$2 under the store. If they ever run Shopping they undercut brand queries. Google's index also still holds A$58 and A$63 prices from old pages; fix or redirect those pages before Shopping goes live so feed price matches every landing page.

## Open questions for Jake (answer when convenient, none block the build)

1. GST entity for the payments profile. Jake (15 Oct): GST is paid under the family trust that owns the Pty Ltd, so the ex GST economics in the table stand. ABN Lookup shows ENDLESS PARKS PTY LTD (ABN 28 675 105 316) itself as not registered for GST, so the Google Ads payments profile should be in the trust's name and ABN (trustee ENDLESS PARKS PTY LTD), with GST registered ticked, so the 10 per cent GST on Google's invoices is creditable to the entity that lodges the BAS. Needed from Jake or the accountant: the trust's exact registered name and ABN, and which name Advertiser verification documents should carry (the business name asset can still read "Endless Parks").
2. Is the wholesale stockist Tiny Treasures Denmark allowed to list the bottle online at A$85? Is there a minimum advertised price in the wholesale terms?
3. Are the old A$58 and A$63 bottle prices still live on any page (/pages/adventurebottle, /collections/all)? Redirect /pages/adventurebottle to the product page if it is stale.
4. Is "2 for 20% off, 3 for 30% off" acceptable in evergreen Search ad copy, or is it website only? The plan keeps it out of ads until you say.
5. Do the tees carry an Australian Made logo licence, so "Australian Made certified" can be used in ads and the feed?
6. Landed cost of a tee, to set the tee break-even CPA properly.
7. Search Console: export the last 16 months of queries (filter Australia) so brand versus non brand volume stops being a guess.
8. Is "Free Shipping Over $120" acceptable as an evergreen headline and callout? It is a shipping condition the site already states, not a discount. Replacement lines are ready in `05-ad-copy.md` if not.
9. Tee variant data: colours per design, fabric and weight, and a SKU on every variant (Judge.me matches ratings on SKU without GTINs).
10. Judge.me plan tier: the Google product ratings feed needs the Awesome plan.
11. Advertiser verification: Google verifies the legal entity on the payments profile, which will be the trust (question 1), so the documents are the trust's ABN record and the trustee company details. The business name asset reads "Endless Parks", the registered business name.
12. Google title route: the Merchant Center supplemental data source (needs the Advanced data source management add on; `feed/supplemental-feed.csv` is ready) or the shorter compromise Shopify title. The storefront title is not changed without your say so because Meta's catalogue uses it.
13. Contact details are already public on the footer's Contact information page (phone +61 432 760 206, info@endlessparks.com, Balcatta address, ABN), so Merchant Center can use them. Only decision left: add the email and phone to the contact page itself?
14. The BFCM offer (percentage, code, sitewide or bottle only), so the BFCM ads and the Merchant Center promotion can be finished.
15. Logo files (1200 by 1200 and 1200 by 300) and four to six bottle images without text, for the Search image assets.
16. Alert inbox for rules and scripts, and whether jakereidmedia is in copy.
17. Is the `wholesale` tag on every stockist customer and every wholesale order? Triple Whale filtering and the purchaser list depend on it.
18. Does endlesspks@gmail.com hold Owner on the Search Console property and Editor on the GA4 property?
19. Exclude past purchasers from non brand Search (cleaner new customer numbers) or observe only (tees as a cross sell)?
20. /pages/adventurebottle already returns 404 (read 15 Oct 2026), so nothing is live there; the redirect to the product page can be created without a decision. The old A$58 and A$63 prices only survive in Google's index.
21. The bottle page has no Product structured data (only an Organization block). Which should add it: the theme's setting or Judge.me's JSON-LD option? One source, not both.
22. The three State Adventure Mugs carry the product type "Water Bottle" in Shopify. The plan changes them to "Mug"; shout if that type is used elsewhere (collections, theme filters).

## What was verified, and what still needs a browser

The research agents worked from search engine extracts because the environment blocked page loads at first. After Jake widened network access on 15 Oct, the claims the plan leans on hardest were re read from Google's full pages: the new advertiser credit rules (Help 6388096, 2393021, 16324294, 16323427, the Australian promotional terms and the policy page), AI Max defaults and the opt out path, account level automated assets, auto apply, channel prioritisation, the Shopping campaign creation page, the Shopify conversion and Data Manager pages, identifier_exists, the channel's shipping sync page, product ratings, and Australia Post's 2026 table. Shopify Help Centre and Search Engine Land pages were still blocked, so those claims rest on extracts. Menu labels should still be confirmed on screen. Three things need Jake in a browser:

- Google Ads Transparency Center (adstransparency.google.com, region Australia) for Frank Green, Stanley, Yeti, Hydro Flask, Kathmandu, Macpac, Anaconda, BCF, Snowys, Wild Earth, Awesome Maps and Let's Wander, and an incognito google.com.au search for "endless parks" and "national parks water bottle" with the Shopping carousel visible.
- Keyword Planner inside the new account for real Australian volumes (step listed in `04-campaign-build.md`).
- The live state of the Shopify Google & YouTube channel (connected Ads account, conversion tracking toggle, shipping sync mode).

The earlier chat's research reports R02 to R08 are on the Mac under the Claude scratchpad folder for the Claude project (gads/research); R09 and R10 never completed there and were redone in this session, and a second pass (`research/phase2/`) added the budget model, Shopping mechanics, audiences, the PMax experiment, landing pages, automation and two adversarial reviews.

## Jake's rules that apply to every ad

- No sale, discount or "sale now on" language in evergreen ads. The only exception is 25 Nov to 1 Dec. The 10 per cent welcome offer stays email only.
- Say "National and Marine Parks", never "national parks" alone.
- Australian spelling. No em dashes.
- Wholesale draft orders are never counted as ad driven.
