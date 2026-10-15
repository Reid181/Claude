# Chrome runbook: Endless Parks Google Ads launch

This is the execution script for Claude in Chrome, with Jake watching. It sequences every step in the plan into browser sessions. Each step has the URL or menu path, the inputs, the check that proves it worked, and what to do if it fails. Steps marked JAKE need Jake's hands (card details, support chat, anything that costs money or needs a decision). Everything else the browser agent can do.

Conventions:

- Store: Shopify admin is https://admin.shopify.com/store/f8dc9c-2/. Merchant Center account 5382740922. GA4 property G-M3LTBNJ7H4 (web UI path a350464798p483603169). Site https://www.endlessparks.com.
- Google Ads URLs below use the left navigation path. Google Ads rewrites URLs with the account id, so when a URL does not land, use the path or type the setting name into the search box at the top of Google Ads.
- Chrome profile: signed in to endlesspks@gmail.com for Google properties (Ads, Merchant Center, GA4, Search Console). If a page shows the account picker, pick the Endless Parks account every time.
- Screenshot every "Check" line and keep the screenshots in a folder named for the session. They are the audit trail if the credit or a conversion action is ever disputed.
- Never click Create campaign inside Shopify or Merchant Center. Never turn on anything labelled AI Max, automatically created assets, broad match, search partners or Display Network.

## Session 0: Jake's prep (10 minutes, no browser)

Have ready: legal entity name and ABN exactly as on the ABR; a business card for Google Ads billing that has never been on another Google Ads account; tee variant data (colours per design, fabric, weight); the answers to the open questions in `PLAN.md` that are ready. Confirm Chrome is signed in to endlesspks@gmail.com.

## Session 1: discovery (20 minutes, any day from 16 Oct)

| # | Where | Do | Check |
|---|---|---|---|
| 1.1 | https://admin.shopify.com/store/f8dc9c-2/apps/google/settings | Read the Google services card: connected Google account, Merchant Center id, Google Ads account id or Connect button, Google Analytics property | Screenshot. Note the Ads customer id if shown |
| 1.2 | https://merchants.google.com/mc/overview?a=5382740922 then Settings (gear) > Access and services > Apps and services | List linked Google Ads accounts and their status | Screenshot. Note any customer id, including one Jake never linked (Google auto links since June 2026) |
| 1.3 | https://ads.google.com/aw/overview as endlesspks@gmail.com | Does an account open (customer id under the profile picture, top right), an account picker, or the new sign up flow? If the sign up flow: stop, do not submit | Screenshot. Customer id: ______ |
| 1.4 | In that account: Campaigns, date range All time, columns Impressions and Cost | Confirm zero impressions and zero cost ever | Screenshot. Non zero means the credit is off (`00`) |
| 1.5 | Billing > Documents, Billing > Promotions, Billing > Settings | No invoice, no promotion ever redeemed, note whether a payments profile and card exist | Screenshot each |
| 1.6 | Admin > Account settings | Currency and time zone | Must be AUD and Perth. Any other currency means Step B in `00` (new account) |
| 1.7 | Campaigns > Change history, oldest entry | Account creation date | Note it. Under 14 days old makes every reading of the credit rule safe |
| 1.8 | https://payments.google.com as endlesspks | Any Google Ads payments profile and card on file | Screenshot |
| 1.9 | Gmail search `from:ads-noreply@google.com` | Welcome email date, any past promo code emails | Note |

Outcome: fill in the Account row of `PLAN.md` and the customer id in `01-account-setup.md`.

## Session 2: Shopify feed and site hygiene (60 to 90 minutes, 16 to 19 Oct)

Follows `03-feed-fixes.md` and the site items in `02-conversion-tracking.md`.

| # | Where | Do | Check |
|---|---|---|---|
| 2.1 | https://admin.shopify.com/store/f8dc9c-2/products | Export all products to CSV as the backup before editing | File saved |
| 2.2 | Products > Australian National Parks Bottle | Title, description first 160 characters, product type Water Bottle, Shopify product category Water Bottles, vendor Endless Parks, variants colour Deep Ocean / Forest / Sand | Save. Screenshot |
| 2.3 | Products > each of the 4 tees | Title pattern, description, product type T-Shirt, category Shirts & Tops, vendor, variants with colour and size | Save each |
| 2.4 | Products > mugs, stickers, lids | Product type Mug / Stickers / Lid | Save |
| 2.5 | Sales channels > Google & YouTube > Products > Bulk editor (https://admin.shopify.com/store/f8dc9c-2/apps/google/products) | For every product: Custom product Yes, Condition New, Google product category (3809 bottle and lids, 212 tees, Mugs for mugs, Decorative Stickers for stickers), Custom label 0 (hero / apparel / excluded), Custom label 1 (xmas-gift / evergreen), Custom label 2 (50to100 / under50); tees also Age group Adult, Gender Unisex | 25 per page; screenshot each page after save |
| 2.6 | Google & YouTube > Settings > Shipping | Set to manual in Merchant Center (not automatic import) | Screenshot |
| 2.7 | https://admin.shopify.com/store/f8dc9c-2/settings/customer_events | Only one Google pixel: Google & YouTube. No custom Google Ads or GTM pixel | Screenshot |
| 2.8 | https://admin.shopify.com/store/f8dc9c-2/settings/customer_privacy | Cookie banner off for Australia; privacy opt out page enabled | Screenshot |
| 2.9 | https://admin.shopify.com/store/f8dc9c-2/settings/markets | No automatic country redirection that would strip URL parameters | Screenshot. If redirection is on, note it for Jake |
| 2.10 | Online Store > Navigation > URL redirects | Redirect /pages/adventurebottle to /products/ultimate-adventure-bottle if that page is stale; check any page still showing A$58 or A$63 | Open each old URL in a new tab afterwards and confirm it lands on the PDP at A$87 |
| 2.11 | https://www.endlessparks.com/products/ultimate-adventure-bottle?utm_source=test&gclid=TEST123 | Load it | Address bar keeps the parameters, page shows A$87 and in stock, no redirect |
| 2.12 | Settings > Policies and the site footer | Shipping policy, refund policy (30 days) and a contact page with the Balcatta address and an email are linked from the footer | Screenshot |
| 2.13 | Judge.me app > Settings > Integrations > Google Shopping | Enable, API feed, Merchant Center id 5382740922 | Screenshot. JAKE if the plan tier blocks it |

## Session 3: Merchant Center (30 minutes, 17 to 19 Oct, after Session 2 has synced for 24 hours)

| # | Where | Do | Check |
|---|---|---|---|
| 3.1 | Merchant Center > Settings > Business information | Address 4/16 Ledgar Rd Balcatta WA 6021, phone, customer service email, logo, website claimed and verified | Screenshot |
| 3.2 | Settings > Shipping and returns | Add shipping service Australia: flat A$14, free over A$120, handling 0 to 1 day, transit 2 to 8 days. Second service Express A$19, 1 to 4 days. Return policy 30 days with the policy URL | Screenshot |
| 3.3 | Settings > Automatic improvements | Image improvements on, automatic title and price improvements off | Screenshot |
| 3.4 | Settings > Add-ons > Product ratings | Get started, confirm the Judge.me feed is recognised (may take days) | Screenshot |
| 3.5 | Products > All products, filter Status | 3 bottle variants and every tee variant Approved. Read every warning on them | Screenshot. Fix list goes back to Session 2 |
| 3.6 | Products > any excluded product (mugs, stickers, lids) | Still in the feed, approved for free listings | Screenshot |

## Session 4: account, credit and hygiene (60 to 90 minutes, 20 to 22 Oct)

Follows `00-new-account-and-credit.md` Step A and `01-account-setup.md` Steps 3 and 4. Do not start this session before 20 Oct.

| # | Where | Do | Check |
|---|---|---|---|
| 4.1 | Google Ads > Billing > Settings | JAKE: payments profile (Business, legal name and ABN, Balcatta address, GST registered), automatic payments, card | Screenshot without the card number |
| 4.2 | Billing > Promotions, then Gmail | Accept any offer listed on the Promotions page after reading its terms. If none: search the endlesspks Gmail for a Google Ads promotional code issued in the last three months and enter it with the blue plus. Do not ask support (Google states offers are not available by request) | Row in Redeemed status with spend by and expiry dates. Screenshot. If nothing attaches: Step B in `00`, new account from the AU offer page, same session |
| 4.3 | Campaigns > Recommendations > Auto-apply > Manage | Untick every box in both bundles, save | Screenshot |
| 4.4 | Campaigns > Assets > More (three dots) > Account-level automated assets > More > Advanced settings | Automated promotions off, Dynamic images off, Longer ad headlines off, Dynamic callouts off, Dynamic structured snippets off; Seller ratings on, Dynamic sitelinks on | Screenshot |
| 4.5 | Admin > Account settings | Auto-tagging on; Tracking > Final URL suffix pasted from `02`; Negative keywords: paste the Shopping list from `05-negatives.txt`; Channel prioritisation card if present: search partners Low 0 per cent, Display Low 0 per cent | Screenshot each card |
| 4.6 | Admin > Access and security | Require 2-step verification; invite jakereidmedia@gmail.com as Admin | Screenshot |
| 4.7 | Admin > Advertiser verification | JAKE: start verification with the legal entity documents | Status Pending |
| 4.8 | Tools > Shared library > Exclusion lists > Negative keyword lists | Create EP_Negatives_Shopping and EP_Negatives_Search from `05-negatives.txt` | Screenshot both lists |
| 4.9 | Tools > Shared library > Brand lists | Create Endless Parks (endless parks, endlesspks, endless parks bottle) | Screenshot |
| 4.10 | Tools > Bulk actions > Rules | Three email only rules: campaign Limited by budget; ad disapproved; ad group cost over A$40 with 0 conversions in 14 days | Screenshot |
| 4.11 | Tools > Bulk actions > Scripts | Install disapproved ads alert, disapproved products alert, monthly pacing script; preview each, then schedule daily | Screenshot the schedule |
| 4.12 | Admin > Linked accounts > Google Merchant Center | Link 5382740922 (auto approves if endlesspks is admin on both) | Status Linked |
| 4.13 | Merchant Center > Settings > Access and services > Apps and services | Confirm the Ads account shows Linked | Screenshot |
| 4.14 | https://admin.shopify.com/store/f8dc9c-2/apps/google/settings > Google Ads | Connect this customer id. Decline any Performance Max campaign prompt | Screenshot. Next day: Google Ads > Campaigns shows nothing created by Shopify |
| 4.15 | Google Ads Editor (desktop) | JAKE: install 2.13, Account > Export whole account | File saved |

## Session 5: conversion tracking (30 minutes, 22 to 24 Oct)

Follows `02-conversion-tracking.md`.

| # | Where | Do | Check |
|---|---|---|---|
| 5.1 | Shopify > Google & YouTube > Settings > Google Ads settings | Conversion tracking on; Enhanced conversions on | Screenshot |
| 5.2 | Google Ads > Goals > Conversions > Summary | Shopify Purchase action: Primary, value per conversion, AUD, count Every, 30 day click, 3 day engaged view, Data driven. Every other action Secondary | Screenshot the list showing one Primary |
| 5.3 | Goals > Conversions > Settings | Customer data terms accepted; Enhanced conversions on, Google tag | Screenshot |
| 5.4 | Admin > Account settings > Tracking > Final URL suffix > Test | Loads the PDP with every parameter, no redirect | Screenshot |
| 5.5 | GA4 Admin > Product links > Google Ads links (https://analytics.google.com/analytics/web/#/a350464798p483603169/admin) | Link the customer id, personalised advertising on | Screenshot |
| 5.6 | Google Ads > Tools > Data manager > Search Console | Link https://www.endlessparks.com | Status Linked |
| 5.7 | Triple Whale > Integrations > Google Ads | JAKE: connect; leave "automatically add tracking parameters" off; Summary global filter Order tag does not contain wholesale | Screenshot |
| 5.8 | https://tagassistant.google.com > Add domain > endlessparks.com | JAKE: buy a A$15 mug sticker sheet at the A$2.50 letter rate, then refund it in Shopify | Tag Assistant: one Google Ads conversion hit (transaction_id = order number, value 15.00, AUD, user_data present) and one GA4 purchase. Screenshot |
| 5.9 | Goals > Conversions > Summary, next day | Purchase status Recording conversions | Screenshot |

## Session 6: campaign build (90 minutes, 22 to 24 Oct)

Follows `04-campaign-build.md`. Every campaign is saved Paused. Before each save, re read the settings page for: AI Max off, automatically created assets off, search partners and Display unticked, Locations Australia with Presence, English, no ad schedule.

| # | Where | Do | Check |
|---|---|---|---|
| 6.1 | Campaigns > plus > New campaign > Sales > Shopping > Standard Shopping | ep_shop_bottle-tees_au_2026q4, Merchant Center 5382740922, Australia, Manual CPC, A$22 a day, priority Medium, networks unticked, ad group all_products default A$0.80 | Screenshot settings |
| 6.2 | The ad group > Product groups | Subdivide by Custom label 0: hero A$1.10, apparel A$0.40, Everything else Excluded (Product type fallback if labels have not reached Google Ads yet) | Screenshot the tree |
| 6.3 | Campaign > Negative keywords | Attach EP_Negatives_Shopping | Screenshot |
| 6.4 | New campaign > Sales > Search | ep_srch_brand_au_2026q4, Manual CPC A$0.50, A$3 a day, AI Max off, networks unticked, ad group brand with the brand keywords from `05-keywords.csv`, the Brand ad from `05-ad-copy.md`, sitelinks, callouts, snippet, price, business name and logo, image assets | Ad strength shown, ad status Eligible or Under review. Screenshot |
| 6.5 | New campaign > Sales > Search | ep_srch_nonbrand_au_2026q4, Manual CPC, A$5 a day, AI Max off, ad groups bottle_nationalparks and gifts_outdoors enabled, bottle_generic_test and tees_aussiemade paused, keywords and max CPCs from the CSV, the Bottle, Gifts and Tees ads, assets, EP_Negatives_Search plus brand negatives | Screenshot each ad group |
| 6.6 | Tools > Planning > Keyword Planner > Get search volume and forecasts, Australia, 12 months | Paste every keyword from the CSV | Export the volumes; drop zero volume keywords; note the rest in the CSV |
| 6.7 | Campaigns view > Columns | Save the EP weekly column set from `02` | Screenshot |
| 6.8 | Each campaign > Settings | Final re read of the trap settings | Screenshot each |

## Session 7: launch (27 Oct, Tuesday morning Perth time, 30 minutes)

Follows `06-launch-and-optimise.md` launch checklist.

| # | Where | Do | Check |
|---|---|---|---|
| 7.1 | Merchant Center > Products, then Google Ads > Campaigns > Products > Diagnostics | Bottle variants and tees Approved in Merchant Center and Eligible (not limited) in Google Ads | Screenshot both |
| 7.1a | Triple Whale > Summary (wholesale tag filtered) | Record the baseline: new customer orders, blended new customer CPA, MER, Meta CPA for 15 Sep to 26 Oct 2026 and for 27 Oct to 21 Dec 2025 | Write the numbers into `07-calendar.md` |
| 7.2 | Google Ads > Goals > Conversions | One Primary Purchase, Recording conversions | Screenshot |
| 7.3 | Billing > Promotions | Offer still Redeemed, spend by date noted | Screenshot |
| 7.4 | Campaigns | Set all three to Enabled | Screenshot the list with budgets |
| 7.5 | Two hours later: Campaigns | Impressions appearing; ads Eligible; no disapprovals | Screenshot |
| 7.6 | JAKE: one click on a live ad from a phone on mobile data, then check the landing URL | gclid and utm parameters present | Screenshot |
| 7.7 | Next morning: Campaigns, Search terms, Merchant Center products | Spend A$25 to A$35, no disapprovals, search terms sane | Screenshot |

## Weekly session (20 minutes, Mondays)

`06-launch-and-optimise.md` weekly routine, plus: Billing > Promotions status until the credit is Active, and the calendar actions due that week in `07-calendar.md`.

## Failure handling

- A Google page shows a different label from this runbook: search the setting name in the Google Ads search box, then record the new label here.
- Promotions rejects the offer: `00` Step B, new account, and this runbook's Session 4 restarts in the new account with 4.1 first.
- Products not approved by 24 Oct: launch Search only on 27 Oct, Shopping the day approvals land.
- No conversion recorded 72 hours after the test order: `02` Step 5 fallbacks. Do not launch until it records.
- Anything Google offers to create for you (Smart campaign, Performance Max from Shopify, broad match, AI Max): decline and note it.
