# Chrome runbook: Endless Parks Google Ads launch

This is the execution script for Claude in Chrome, with Jake watching. It sequences every step in the plan into browser sessions. Each step has the URL or menu path, the inputs, the check that proves it worked, and what to do if it fails. Steps marked JAKE need Jake's hands (card details, business decisions, anything that costs money). Everything else the browser agent can do.

Conventions:

- Store: Shopify admin is https://admin.shopify.com/store/f8dc9c-2/. Merchant Center account 5382740922. GA4 property G-M3LTBNJ7H4 (web UI path a350464798p483603169). Site https://endlessparks.com.
- Google Ads URLs below use the left navigation path. Google Ads rewrites URLs with the account id, so when a URL does not land, use the path or type the setting name into the search box at the top of Google Ads.
- Chrome profile: signed in to endlesspks@gmail.com for Google properties, except Session 4 Step B which uses jakereidmedia@gmail.com. If a page shows the account picker, pick the Endless Parks account every time.
- Screenshot every "Check" line and keep the screenshots in a folder named for the session. They are the audit trail if the credit or a conversion action is ever disputed.
- Never click Create campaign inside Shopify or Merchant Center. Never turn on anything labelled AI Max, automatically created assets, broad match, search partners or Display Network. Never uninstall or reinstall the Google & YouTube app.
- Negative keyword lists: paste only the keyword lines under the relevant heading in `05-negatives.txt`, never the lines starting with #. Keywords: the paste ready blocks in `05-keywords-paste.txt` are in Google's bracket and quote notation.

## Session 0: Jake's prep (10 minutes, no browser)

Have ready: confirmation of GST registration (ABN Lookup says ENDLESS PARKS PTY LTD, ABN 28 675 105 316, is not registered); a business card never used on any Google Ads payments profile; tee colours and SKUs; logo and image files for the Search assets; the BFCM offer; answers to the open questions in `PLAN.md` that are ready. Confirm Chrome is signed in to endlesspks@gmail.com and that jakereidmedia@gmail.com is available for Session 4.

## Session 1: discovery and the credit decision (20 minutes, Friday 16 Oct)

| # | Where | Do | Check |
|---|---|---|---|
| 1.1 | https://admin.shopify.com/store/f8dc9c-2/apps/google/settings | Read the Google services card: connected Google account, Merchant Center id, Google Ads account id or Connect button, Google Analytics property | Screenshot. Note the Ads customer id if shown |
| 1.2 | https://merchants.google.com/mc/overview?a=5382740922 then Settings (gear) > Access and services > Apps and services | List linked Google Ads accounts and their status | Screenshot. Note any customer id, including one Jake never linked (Google auto links since June 2026) |
| 1.3 | https://ads.google.com/aw/overview as endlesspks@gmail.com | Does an account open (customer id under the profile picture, top right), an account picker, or the new sign up flow? If the sign up flow: stop, do not submit | Screenshot. Customer id: ______ |
| 1.4 | In that account: Campaigns, date range All time, columns Impressions and Cost. An account that never had a campaign opens on the campaign builder: close it and use Billing > Documents instead | Zero impressions and zero cost ever, no invoice | Screenshot. Non zero means the credit is off (`00`) |
| 1.5 | Billing > Promotions | Any offer listed as available? Read its terms. Nothing ever redeemed | Screenshot |
| 1.6 | Billing > Settings | Does a payments profile or card exist? Note it; do not add one | Screenshot |
| 1.7 | Admin > Account settings | Currency and time zone | Must be AUD. A wrong time zone can be changed once; a wrong currency means Step B |
| 1.8 | Campaigns > Change history, oldest entry, or the Gmail welcome email | Account creation date | Under 14 days old satisfies every reading of the credit rule; older makes Step B the likely path |
| 1.9 | Gmail, query `from:(ads-noreply@google.com OR googleads-noreply@google.com) (promo OR promotional OR code OR credit)` | Any code issued to this account in the last three months? | Screenshot |
| 1.10 | https://payments.google.com as endlesspks | Any Google Ads payments profile and card | Screenshot |
| 1.11 | Decision per `00` Step A: offer listed or a code in the inbox with the account under 14 days old, and AUD: path A. Otherwise path B | Write the decision into `PLAN.md` | JAKE confirms |

## Session 2: Shopify feed, audiences and site hygiene (90 minutes, 16 to 18 Oct, hard end 18 Oct)

Follows `03-feed-fixes.md`, `09-audiences.md` week one and `10-landing-pages.md` A to C and G.

| # | Where | Do | Check |
|---|---|---|---|
| 2.1 | https://admin.shopify.com/store/f8dc9c-2/products | Export all products to CSV as the backup before editing | File saved |
| 2.2 | Products > Australian National Parks Bottle | Description first 160 characters from `03`, product type Water Bottle (already set), Shopify product category Water Bottles, vendor Endless Parks (already set), variants Deep ocean / Forest / Sand (SKUs UABDeepOcean, UABForest, UABSand already set). Do NOT change the product title (Meta's catalogue uses it); the Google title goes in via 3.7 or, JAKE, the compromise title in `03` | Save. Screenshot |
| 2.3 | Products > each of the 4 tees | JAKE supplies the colour per design and SKUs (the live tees have none). Description from `03`, product type T-Shirt (currently blank), category Shirts & Tops, vendor, a SKU on every size variant | Save each |
| 2.4 | Products > the 3 State Adventure Mugs, stickers, lids | Mugs: product type from "Water Bottle" to Mug (they currently share the bottle's type, which would put nine mug variants in the bottle's product group). Stickers: Stickers, add SKUs (currently blank). Lids: Lid (SKUs exist). Shipping protection + free returns: untick the Google & YouTube channel on that product | Save. Screenshot the mugs' product type |
| 2.5 | Sales channels > Google & YouTube > Products > Bulk editor (https://admin.shopify.com/store/f8dc9c-2/apps/google/products) | For every product: Custom product Yes, Condition New, Google product category (3809 bottle, 212 tees, Mugs for mugs, Decorative Stickers for stickers, leave the lids on Shopify's own mapping), Custom label 0 (hero / apparel / excluded), Custom label 1 (xmas-gift / evergreen), Custom label 2 (50to100 / under50); tees also Age group Adult, Gender Unisex. If the bulk editor has no Custom label column, rely on product type and note it | 25 per page; screenshot each page after save |
| 2.6 | Products > bottle > Media and each tee | First image per variant on a plain background, no text, at least 800 by 800; lifestyle shots second | Screenshot |
| 2.7 | Google & YouTube > Settings > Shipping (Delivery information) | Set to manual in Merchant Center (not automatic import) | Screenshot |
| 2.8 | https://admin.shopify.com/store/f8dc9c-2/settings/customer_events | Only one Google pixel: Google & YouTube. No custom Google Ads or GTM pixel | Screenshot |
| 2.9 | https://admin.shopify.com/store/f8dc9c-2/settings/customer_privacy | Cookie banner off for Australia; privacy opt out page enabled | Screenshot |
| 2.10 | Online Store > Preferences > Automatic redirection, and https://admin.shopify.com/store/f8dc9c-2/settings/markets > each market > Domains | Country redirection off, or every market on the primary domain; no subfolder or subdomain markets; no geolocation app under Settings > Apps | Screenshot. Anything else is noted for JAKE |
| 2.11 | https://endlessparks.com/products/ultimate-adventure-bottle?gclid=TEST123&utm_source=google&utm_medium=cpc on a phone on mobile data, then through a NZ or US VPN exit | Load it | Both parameters still in the address bar after the page settles; a currency switch is fine, a URL change is not |
| 2.12 | Load /pages/adventurebottle, /collections/all and the bottle collection in incognito | Record price, sold out state, buy button | JAKE decides whether /pages/adventurebottle is still used by Meta. If stale: Online Store > Pages > hide it, then Online Store > Navigation > View URL redirects > from /pages/adventurebottle to /products/ultimate-adventure-bottle |
| 2.13 | Settings > Policies and the site footer | Shipping policy, refund policy (30 days, /policies/refund-policy) and a contact page with a domain email, phone and (JAKE) the Balcatta address, all linked from the footer | Screenshot |
| 2.14 | Settings > Policies > Privacy policy | Add: "We may share hashed contact details (such as an email address) with advertising platforms including Google and Meta to show or suppress advertising. To opt out, email <address>." JAKE approves the wording and the address | Screenshot |
| 2.15 | Judge.me app > Settings > Integrations > Google Shopping | Enable, API feed, Merchant Center id 5382740922. The bottle page currently has no Product structured data at all (read 15 Oct): turn on exactly one source, Judge.me's JSON-LD option or the theme's, then check search.google.com/test/rich-results shows one Product with Offer price 87.00 AUD | Screenshot. JAKE if the plan tier blocks it |
| 2.16 | GA4 > Admin > Data display > Audiences (https://analytics.google.com/analytics/web/#/a350464798p483603169/admin) | Create the four audiences in `09-audiences.md` | Screenshot the list |
| 2.17 | https://admin.shopify.com/store/f8dc9c-2/customers/segments | Create segments EP purchasers (orders > 0, tag not wholesale) and EP subscribers | Screenshot both counts |
| 2.18 | https://pagespeed.web.dev on the PDP, Mobile | Record LCP, INP, CLS and Total Blocking Time as the baseline (`10` D) | Screenshot |

## Session 3: Merchant Center (30 minutes, 19 Oct, after Session 2 has synced for 24 hours)

| # | Where | Do | Check |
|---|---|---|---|
| 3.1 | Merchant Center > Settings > Business information | Business name Endless Parks, address 4/16 Ledgar Rd Balcatta WA 6021, phone +61 432 760 206, customer service email info@endlessparks.com (all as published on the site's Contact information page), logo, website claimed and verified | Screenshot |
| 3.2 | Settings > Shipping and returns | Shipping service Australia: flat A$14, free over A$120, handling 0 to 1 day, transit 2 to 8 days. Second service Express A$19, 1 to 4 days. Return policy 30 days, URL /policies/refund-policy | Screenshot |
| 3.3 | Settings > Automatic improvements (or Automations) | Automatic item updates ON (price and availability from the page), image improvements on. Only if a separate automatic title improvements toggle exists, turn that off | Screenshot |
| 3.4 | Settings > Add-ons > Product ratings | Get started; confirm the Judge.me feed is recognised (may take days) | Screenshot |
| 3.5 | Products > a bottle variant > Marketing methods | Shopping ads and Free listings both ticked. If Shopping ads is missing: Products > Data sources > the Shopify source > Marketing methods > tick it | Screenshot |
| 3.6 | Products > a bottle variant > Final attributes > link | https://endlessparks.com/products/ultimate-adventure-bottle?variant=<id>, no stray parameters; open all three variant links in incognito: colour pre selected, A$87, Add to cart enabled | Screenshot |
| 3.7 | Products > Data sources > Add supplemental data source (needs Settings > Add-ons > Advanced data source management) | Google Sheet with the 52 rows of `feed/supplemental-feed.csv` (id, title, custom labels, product type, category, identifier_exists). First confirm the id format against one row in Merchant Center > Products. If the add on is not available: JAKE decides on the compromise storefront title | Screenshot the source status and the first processed row |
| 3.8 | Products > All products, filter Status | 3 bottle variants and every tee variant Approved. The only acceptable "limited performance" note is the missing GTIN one | Screenshot. Other warnings go back to Session 2 |
| 3.9 | Products > any excluded product (mugs, stickers, lids) | Still in the feed, approved for free listings | Screenshot |

## Session 4: account, credit and hygiene (60 to 90 minutes, 20 to 22 Oct)

Follows `00-new-account-and-credit.md` and `01-account-setup.md` Steps 3 and 4. Do not start before 20 Oct.

Path A (an offer is listed on the existing account's Promotions page, decided in Session 1):

| # | Where | Do | Check |
|---|---|---|---|
| 4A.1 | Billing > Promotions | Re read the listed offer and its terms | Screenshot |
| 4A.2 | Billing > Settings | JAKE: payments profile (Business, legal name and ABN, Balcatta address, GST registered), automatic payments, card | Screenshot without the card number |
| 4A.3 | Billing > Promotions | Accept the listed offer (or enter the emailed code with the blue plus) | Row in Redeemed status with spend by and expiry dates. Screenshot |

Path B (no offer; expected):

| # | Where | Do | Check |
|---|---|---|---|
| 4B.1 | Chrome signed in as jakereidmedia@gmail.com, https://ads.google.com/intl/en_au/home | Screenshot the tiers and the terms link; choose the lowest tier at or above A$600 and nothing above about A$900 | Screenshot |
| 4B.2 | Start now > "Are you a professional marketer? Switch to Expert Mode" > "Create an account without a campaign" | Billing country Australia, time zone Perth, currency AUD > Submit | Admin > Account settings shows the new customer id: ______ |
| 4B.3 | Billing > Settings | JAKE: a NEW payments profile (Business, ENDLESS PARKS PTY LTD, ABN 28 675 105 316, Balcatta address, GST registered only if it is), automatic payments, a card never used on any Google Ads payments profile | Screenshot without the card number |
| 4B.4 | Billing > Promotions | Row in Redeemed status with spend by and expiry dates; if none, enter the offer page code with the blue plus | Screenshot |
| 4B.5 | Admin > Access and security > Users | Invite endlesspks@gmail.com as Admin; accept the invitation from the endlesspks inbox | Both users listed as Admin |
| 4B.6 | https://admin.shopify.com/store/f8dc9c-2/apps/google/settings > Google Ads card (as endlesspks) | Disconnect the old account inside the card, connect the new customer id. Decline any Performance Max prompt | Screenshot. Next day: Campaigns shows nothing created by Shopify |
| 4B.7 | The old account | Leave it. No code, no billing, no campaigns | |

Both paths continue (in the account that carries the offer; sign in as endlesspks from here):

| # | Where | Do | Check |
|---|---|---|---|
| 4.1 | Campaigns > Recommendations > Auto-apply > Manage | Untick every box in both bundles, save | Screenshot |
| 4.2 | Campaigns > Assets > More (three dots) > Account-level automated assets > More > Advanced settings | Automated promotions off, Dynamic images off, Longer ad headlines off, Dynamic callouts off, Dynamic structured snippets off; Seller ratings on, Dynamic sitelinks on | Screenshot |
| 4.3 | Admin > Account settings | Auto-tagging on; Tracking > Final URL suffix pasted from `02` (after 5.0 below); Negative keywords: paste the EP_Negatives_Core keyword lines; Channel prioritisation card if present: Shopping search partners Low 0 per cent, Search partners and Display Low 0 per cent | Screenshot each card |
| 4.4 | Admin > Access and security | Require 2-step verification; jakereidmedia@gmail.com and endlesspks@gmail.com both Admin | Screenshot |
| 4.5 | Admin > Account (the Advertiser verification hub) | JAKE: start verification with the legal entity documents matching the payments profile name | Status Pending |
| 4.6 | Tools > Shared library > Exclusion lists > Negative keyword lists | Create EP_Negatives_Core and EP_Negatives_Brand from `05-negatives.txt` (keyword lines only) | Screenshot both lists |
| 4.7 | Tools > Shared library > Brand lists | Create Endless Parks (endless parks, endlesspks, endless parks bottle) | Screenshot |
| 4.8 | Tools > Bulk actions > Rules | The six email only rules in `11-automation-reporting.md` B, to the alert inbox Jake named | Screenshot |
| 4.9 | Bell icon > gear > Notification preferences; Billing > Settings > Document delivery options | Disapprovals, billing and access emails on, marketing off; monthly tax invoice by email | Screenshot |
| 4.10 | Merchant Center > Settings > Access and services > Apps and services > Add service > Google Ads | Enter the customer id, link to Merchant Center only | Request sent |
| 4.11 | Google Ads > Admin > Linked accounts (or Tools > Data manager > Connected products) > Google Merchant Center | Approve the link (auto approves if endlesspks is admin on both) | Status Linked in both places. Screenshot |
| 4.12 | https://admin.shopify.com/store/f8dc9c-2/apps/google/settings > Google Ads card | Path A: confirm this customer id is the one connected. Path B: done at 4B.6 | Screenshot |
| 4.13 | Tools > Planning > Keyword Planner > Get search volume and forecasts, Australia, last 12 months | Paste every keyword from `05-keywords.csv`. A new account shows ranges; that is fine. Drop only keywords with no volume at all; write the ranges into the CSV note column | Export saved |

## Session 5: conversion tracking and audiences (45 minutes, 22 to 24 Oct)

Follows `02-conversion-tracking.md` and `09-audiences.md` build days.

| # | Where | Do | Check |
|---|---|---|---|
| 5.0 | Triple Whale > Integrations > Google Ads help page | JAKE: confirm gadid and tw_kwdid are still the parameters Triple Whale recognises; if Triple Whale shows its own string, use theirs for those two keys. Then paste the suffix in 4.3 | Screenshot |
| 5.1 | Shopify > Google & YouTube > Settings > Google Ads settings | Conversion tracking on; Enhanced conversions on | Screenshot |
| 5.2 | Google Ads > Goals > Conversions > Summary | Shopify Purchase action: Primary, value per conversion, AUD, count Every, 30 day click, 3 day engaged view, Data driven. Every other action Secondary | Screenshot the list showing one Primary |
| 5.3 | Goals > Conversions > Settings | Customer data terms accepted; Enhanced conversions on, Google tag | Screenshot |
| 5.4 | Admin > Account settings > Tracking > Final URL suffix > Test | Loads the PDP with every parameter, no redirect | Screenshot |
| 5.5 | GA4 Admin > Product links > Google Ads links | Link the customer id, personalised advertising on | Screenshot |
| 5.6 | Google Ads > Tools > Data manager > Search Console | Link https://endlessparks.com (needs Owner on Search Console) | Status Linked |
| 5.7 | Triple Whale > Integrations > Google Ads | JAKE: connect; leave "automatically add tracking parameters" off; Summary global filter Order tag does not contain wholesale | Screenshot |
| 5.8 | Tools > Data manager > Connect product > Shopify | Sign in as endlesspks, keep only EP purchasers and EP subscribers, Connect | After 48 hours Tools > Audience manager shows both above 100 for Search and the four GA4 audiences. Screenshot |
| 5.9 | https://tagassistant.google.com > Add domain > endlessparks.com | JAKE: buy a A$15 mug sticker sheet at the A$2.50 letter rate with a real card, then refund it in Shopify | Tag Assistant: one Google Ads conversion hit (transaction_id = order number, value 15.00, AUD, user_data present) and one GA4 purchase. Screenshot. Value 17.50 means shipping is included: `02` Step 5 fallback |
| 5.10 | Goals > Conversions > Summary, 30 minutes later | Purchase status No recent conversions or Tag active, not Unverified; Diagnostics shows the tag Active. "Recording conversions" cannot appear before the first paid click | Screenshot |

## Session 6: campaign build (90 minutes, 22 to 24 Oct)

Follows `04-campaign-build.md`. Every campaign is saved Paused. Before each save, re read the settings page for: AI Max off, automatically created assets off, search partners and Display unticked, Locations Australia with Presence, English on the Search campaigns, no ad schedule.

| # | Where | Do | Check |
|---|---|---|---|
| 6.1 | Campaigns > plus > New campaign > Sales > Shopping > Standard Shopping | ep_shop_bottle-tees_au_2026q4, Merchant Center 5382740922, Australia, Manual CPC, A$22 a day, priority Low (default), search partners unticked, Inventory filter off, ad group all_products default A$0.80 | Screenshot settings |
| 6.2 | The ad group > Product groups | Subdivide by Custom label 0: hero A$1.10, apparel A$0.40, Everything else Excluded. Labels not visible yet (24 to 48 hours after sync): subdivide by Product type instead, Water Bottle A$1.10, T-Shirt A$0.40, Everything else Excluded, and switch later | Screenshot the tree |
| 6.3 | Campaign > Negative keywords | Attach EP_Negatives_Core | Screenshot |
| 6.4 | New campaign > Sales > Search | ep_srch_brand_au_2026q4, Manual CPC A$0.50, A$3 a day, AI Max off, networks unticked, ad group brand with the brand block from `05-keywords-paste.txt`, the Brand ad from `05-ad-copy.md`, sitelinks, callouts, snippet, price asset, business name and logo (JAKE supplies files), image assets | Ad status Eligible or Under review. Screenshot |
| 6.5 | New campaign > Sales > Search | ep_srch_nonbrand_au_2026q4, Manual CPC, A$5 a day, AI Max off. Ad groups from the paste file: bottle_nationalparks enabled; gifts_outdoors, gifts_test, bottle_generic_test and tees_aussiemade with every keyword paused and labelled as the CSV says. Bottle ad in both bottle groups and Gifts ad in both gift groups, all landing on the bottle page; Tees ad in tees landing on https://endlessparks.com/pages/drop-01?view=ep-drop-01 (with the view parameter, never the bare page and never the navigation's _kx link). Attach EP_Negatives_Core and EP_Negatives_Brand; type the ad group negatives | Screenshot each ad group |
| 6.6 | Each campaign > Audiences, keywords and content > Audiences (ad group level on Shopping if campaign level is absent) | Observation segments from `09-audiences.md` at 0 per cent; on the non brand campaign the exclusion EP purchasers unless JAKE chose observation only | Screenshot |
| 6.7 | Campaigns view > Columns | Save the EP weekly column set from `02` | Screenshot |
| 6.8 | Each campaign > Settings | Final re read of the trap settings | Screenshot each |
| 6.9 | Google Ads Editor (desktop) | JAKE: install 2.13, Account > Export whole account as the post build backup | File saved |
| 6.10 | Triple Whale > Summary (wholesale tag filtered) | Record the baseline: new customer orders, blended new customer CPA, MER, Meta CPA for 15 Sep to 24 Oct 2026 and for 27 Oct to 21 Dec 2025 | Numbers written into `07-calendar.md` |
| 6.11 | lookerstudio.google.com | Build the one page weekly report in `11` E, scheduled Monday 7am Perth | Screenshot |
| 6.12 | `05-ad-copy.md` BFCM section | Build the BFCM ad in each non brand ad group and the Shopping promotion draft, saved paused (JAKE fills the offer) | Screenshot |

## Session 7: launch (27 Oct, Tuesday morning Perth time, 30 minutes)

Follows `06-launch-and-optimise.md` launch checklist.

| # | Where | Do | Check |
|---|---|---|---|
| 7.1 | Merchant Center > Products, then Google Ads > Campaigns > Products > Diagnostics | Bottle variants and tees Approved in Merchant Center and Eligible in Google Ads (Eligible (limited) only for the missing GTIN note) | Screenshot both |
| 7.2 | Google Ads > Goals > Conversions | One Primary Purchase, status not Unverified | Screenshot |
| 7.3 | Billing > Promotions | Offer still Redeemed, spend by date noted | Screenshot |
| 7.4 | Campaigns | Set all three to Enabled (non brand runs on bottle_nationalparks only) | Screenshot the list with budgets |
| 7.5 | Two hours later: Campaigns | Impressions appearing; ads Eligible; no disapprovals | Screenshot |
| 7.6 | JAKE: one click on a live ad from a phone on mobile data, then check the landing URL | gclid and utm parameters present | Screenshot |
| 7.7 | Next morning: Campaigns, Search terms, Merchant Center products | Spend A$20 to A$60 on the day (Google may spend up to twice the daily budget), no disapprovals, search terms sane | Screenshot |
| 7.8 | Day 7: Goals > Conversions > Summary and the Purchase action's Diagnostics | Recording conversions after the first paid click order; enhanced conversions match rate band showing | Screenshot |

## Weekly session (20 minutes, Mondays)

`11-automation-reporting.md` I, plus Billing > Promotions until the credit is Active, and the calendar actions due that week in `07-calendar.md`. Monthly: `11` J.

## Failure handling

- A Google page shows a different label from this runbook: search the setting name in the Google Ads search box, then record the new label here.
- No offer on the existing account (Session 1): path B. Nothing is built in the old account.
- Products not approved by 24 Oct: launch Search only on 27 Oct, Shopping the day approvals land.
- Tag Assistant shows no conversion hit, or two, after the test order: `02` Step 5 fallbacks. Do not launch until one clean hit shows. "Recording conversions" is not expected before launch.
- Custom labels missing from the product group picker: build on product type and switch within the week.
- Anything Google offers to create for you (Smart campaign, Performance Max from Shopify or Merchant Center, broad match, AI Max): decline and note it.
