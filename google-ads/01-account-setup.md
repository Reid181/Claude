# 01. Account setup

Goal: one Google Ads account in AUD, owned by endlesspks@gmail.com, linked to Merchant Center 5382740922 and to the Shopify Google & YouTube channel, with every default trap switched off. Google renames menus often; if a label is missing, type the setting name into the search box at the top of Google Ads.

## Step 1: find out whether an account already exists (15 minutes)

Check in this order. A customer ID is 10 digits, written 123-456-7890.

1. ads.google.com signed in as endlesspks@gmail.com. An existing account opens straight away with the customer ID under the profile picture (top right). Several accounts show a picker. No account shows the sign up flow: stop before submitting anything.
2. Merchant Center (merchants.google.com, account 5382740922) > Settings (gear) > Access and services > Apps and services. Any linked Google Ads account is listed with its customer ID and link status. Since June 2026 Google has been auto linking some Ads accounts here, so a link Jake never made is possible.
3. Shopify admin > Sales channels > Google & YouTube > Settings > Google services. Shows which Google account connected the channel and which Ads account, if any.
4. Search the endlesspks Gmail for "ads-noreply@google.com" and "customer ID". payments.google.com lists every Google service attached to the payments profile.

Earlier check on 15 Oct: neither jake.reid181@gmail.com nor jakereidmedia@gmail.com has an Ads account.

### If an account exists (dormant account path)
1. Before touching anything: install Google Ads Editor 2.13 (older than 2.11 stops working 19 Oct 2026), Account > Export > whole account. Campaigns > Change history > export. Billing > Documents > download old invoices. Note total past spend and the last date an ad served: any past impressions make the business ineligible for the new account credit in Step 2.
2. Admin > Account settings: currency must be AUD and time zone Perth. If the currency is anything else, abandon this account and create a new one (currency cannot change).
3. Campaigns > select all > Edit > Pause, before adding billing or reactivating. Reactivation re enables anything left Enabled.
4. Remove (not just pause) any Smart campaign and any Performance Max campaign the Shopify channel created. Build the new campaigns fresh.
5. Goals > Conversions > Summary > Remove inactive conversions (archives anything with no data for 13 months). Every remaining purchase style action becomes Secondary; `02-conversion-tracking.md` sets the single Primary.
6. Campaigns > Change history > filter User = Auto-applied: reverse anything Google changed while the account sat idle.
7. Admin > Linked accounts: confirm Merchant Center 5382740922 is the only Merchant Center link. Remove any other.
8. Go to Step 3.

### If no account exists
Go to Step 2.

## Step 2: create the account (20 minutes)

1. ads.google.com > Start now, signed in as endlesspks@gmail.com.
2. Google opens the guided (Smart) flow. At the bottom of the goal screen click "Are you a professional marketer? Switch to Expert Mode". On the campaign type screen click "Create an account without a campaign" (lower left). Never build the first campaign in the guided flow.
3. Business information: billing country Australia, time zone (GMT+08:00) Perth, currency Australian Dollar. Time zone and currency are permanent.
4. Submit. Admin > Account settings: copy the customer ID into this file.
5. Billing > Settings > Payments profile: account type Business, legal entity name and ABN exactly as on the ABR, address 4/16 Ledgar Rd, Balcatta WA 6021, tick registered for GST. Automatic payments, add the card. Google Australia Pty Ltd adds 10 per cent GST; the monthly tax invoice is at Billing > Documents > Tax and statutory documents by the fifth business day of the next month.
6. New account credit: the Australian offer in circulation is spend A$600 (ex GST) in the first 60 days, get A$600 credit. Conditions: new to Google Ads, Australian billing address, card added at sign up, code entered within 14 days of the first ad impression, credit lands within about 35 days and expires 60 days later. Enter it at Billing > Promotions > Manage promotional codes if a code was offered at sign up or by email. At A$30 a day the A$600 is reached in 20 days. Ignore any third party offering a "A$600 match" in exchange for manager access to the account; that is not a Google offer.

Customer ID: ______________ (fill in)

## Step 3: hygiene settings (30 minutes)

1. Campaigns > Recommendations > Auto-apply (top right) > Manage: untick every box in both bundles (Maintain your ads, Grow your business) > Save. There is no master switch. Dismissing a recommendation gives the same optimisation score as applying it.
2. Campaigns > Assets > More (three dots) > Account-level automated assets > More > Advanced settings: Automated promotions Off (new from 12 Oct 2026, it lifts on site coupons such as the 10 per cent welcome popup into ad copy, which breaks the no sale hooks rule), Dynamic images Off, Longer ad headlines Off, Dynamic callouts Off, Dynamic structured snippets Off. Leave Seller ratings On (Judge.me is a licensed review partner and the store is at 99 reviews) and Dynamic sitelinks On until manual sitelinks exist. Campaign level settings override account level, so re check inside each campaign after building.
3. Admin > Account settings > Auto-tagging: On. Adds gclid to every click, which Shopify, GA4 and Triple Whale need.
4. Admin > Account settings > Tracking > Final URL suffix: paste the suffix from `02-conversion-tracking.md`.
5. Admin > Account settings > Negative keywords: add the account level list from `05-negatives.txt` (1,000 limit; applies to Search, Shopping and any future PMax search inventory).
6. Admin > Account settings > Channel prioritisation (launched 14 Oct 2026, rolling out progressively, may not show yet): Shopping, search partners Low with 0 per cent cap (or the lowest allowed). Search, search partners Low 0 per cent and Display Network Low 0 per cent. If the card is absent, the per campaign network boxes in `04-campaign-build.md` do the same job. From February 2027 Google changes how Search campaigns with Display on allocate spend, so keeping Display off avoids that change entirely.
7. Admin > Access and security > Security: Require 2-step verification. Users: add jakereidmedia@gmail.com as Admin so Jake can work without the shared login. Nobody else at launch.
8. Notifications (bell icon > settings): on for disapproved ads, billing issues, account suspension. Marketing emails off.
9. Tools > Shared library > Exclusion lists > Negative keyword lists: create `EP_Negatives_Shopping` and `EP_Negatives_Search` from `05-negatives.txt`.
10. Tools > Shared library > Brand lists: create `Endless Parks` (endless parks, endlesspks, endless parks bottle). Not used at launch; needed if a PMax experiment ever runs.
11. Tools > Bulk actions > Rules (email only, no auto pause at launch): email when any campaign is Limited by budget; email when an ad is disapproved; email when an ad group has cost over A$40 and 0 conversions in 14 days.
12. Tools > Bulk actions > Scripts: install Nils Rooijmans' free disapproved ads alert and disapproved products alert, plus a monthly budget pacing script (Cypress North or Acuto). Preview each once, then schedule daily.
13. Campaigns > Change history: bookmark. Check monthly with filter User = Auto-applied or Google Ads system. Anything there is automation to switch off.
14. No shared budgets. Each campaign keeps its own.

## Step 4: link Merchant Center and Shopify (15 minutes)

1. Merchant Center 5382740922 > Settings > Access and services > Apps and services > Add service > Google Ads > enter the customer ID > link to Merchant Center only (not Business Manager).
2. Google Ads > Admin > Linked accounts (some accounts: Tools > Data manager > Connected products) > Google Merchant Center > approve. If endlesspks@gmail.com is admin on both, it approves itself.
3. Shopify admin > Google & YouTube > Settings > Google services: connect the same customer ID. The connecting Google account needs Admin on the Ads account. If Shopify offers to create a Performance Max campaign, decline. The channel's job is feed sync and the conversion tag only.
4. Merchant Center > Settings > Business information: website https://www.endlessparks.com claimed and verified, business name Endless Parks, customer service email and phone filled in, logo uploaded. Missing contact details trigger misrepresentation holds.
5. Also link GA4 (property G-M3LTBNJ7H4) and Search Console under Admin > Linked accounts. Details in `02-conversion-tracking.md`.

## Naming conventions

Mirror the Meta pattern (ep_asc_bottle_broad_2026q4):

- `ep_shop_bottle-tees_au_2026q4` (Standard Shopping)
- `ep_srch_brand_au_2026q4` (brand Search)
- `ep_srch_nonbrand_au_2026q4` (non brand Search)
- Ad groups by product or intent: `bottle_nationalparks`, `gifts_outdoors`, `tees_aussiemade`, `brand`.
- Labels: `launch-oct26`, `xmas26` (seasonal keywords, easy to pause in January), `bfcm26`.

## Still unknown after this file

- Whether an account exists, its customer ID and whether it ever served ads (decides promo eligibility).
- Exact legal entity name and ABN for the payments profile, and whether Endless Parks is GST registered.
- Whether the Channel prioritisation card has reached this account yet.
