# 00. The account and the new advertiser credit

Decision (Jake, 15 Oct 2026): use the existing Google Ads account, which has never run ads, and claim Google's new advertiser credit in it. Create a new account only if Google refuses to attach the offer to the existing one. This file is the sequence that protects the credit. Read it before `01-account-setup.md`.

## The one condition that matters

Google defines a new advertiser as "a business that has never advertised with Google Ads", not a new account or a new login. The credit is checked after the spend, in an "up to 35 day verification period that confirms an advertiser is new to Google", and an account "found to be advertising for a business that was already advertising with Google Ads" gets nothing. Google's own example of a promotional offers violation is setting up several accounts for the same website and applying a code to each; the penalty is losing access to promotions, not losing the Ads account.

So a new account only earns the credit if no Google ad has ever served for endlessparks.com from any account: endlesspks@gmail.com, any agency, anyone who once clicked Create Campaign in the Shopify channel's Performance Max module. Free listings in Merchant Center do not count as advertising.

Before creating anything, run the four checks in `01-account-setup.md` Step 1. The outcome decides the path:

- Nothing found: create a new account and claim the credit at sign up.
- An account exists but never served an impression (Jake's position on 15 Oct): the business is still new, so the credit is available. Which account can take it is where Google's own pages disagree. Google's promotional credit terms (google.com/ads/coupons/terms) say the code must be applied to "your first Google Ads account" no more than 14 days after the first ad impression served from it, which an account with no impressions satisfies, and which a second account would not. Google Ads Help 6388096 instead says the account must be under 14 days old at redemption. The offer's own terms govern, and the cheap way to find out is to try: attach the offer to the existing account first (Step A below). If Google's system accepts it, the account shows a Redeemed row and the 35 day check after the spend only asks whether the business ever advertised, which it has not. If Google refuses, create a new account (Step B) and accept the residual "first account" risk.
- An account that served ads for Endless Parks at any time: the business is not new. Build the plan in that account (dormant path in `01-account-setup.md`) and forget the credit. A second account would spend the same A$30 a day, be invalidated at the 35 day check, and risk promotions access.

### Step A: confirm the existing account and attach the offer (30 minutes, 20 to 22 Oct)

Signed in as the account's owner (expected endlesspks@gmail.com):

1. Campaigns, date range All time: zero impressions, zero cost. Billing > Documents: no invoice ever. Billing > Promotions: nothing ever redeemed. Screenshot all three.
2. Admin > Account settings: currency AUD and time zone Perth. If the currency is not AUD, stop and use Step B; currency cannot be changed.
3. Campaigns > Change history, earliest entry (or the welcome email from ads-noreply@google.com): note the creation date. Under 14 days old means both readings of the rule are satisfied.
4. Billing > Settings: if no payments profile exists, add one now (business, legal entity name and ABN as on the ABR, Balcatta address, GST registered, automatic payments, card). A valid payment method must be on the account before redemption. Never switch to monthly invoicing afterwards.
5. Billing > Promotions: look for an offer listed as available and accept it, or click the blue plus and enter a code. To get a code: open the Google Ads Australia offer page (ads.google.com/intl/en_au/home) signed in as the same account and follow its claim flow; if it only offers sign up for a new account, open Google Ads support (the help icon, top right, then Contact us, chat) and ask for a new advertiser promotional code for this customer ID, stating that the account has never served an impression. Support can apply new advertiser codes to eligible accounts.
6. Pass: Billing > Promotions shows a row in Redeemed status with its spend by date and expiry. Screenshot it. Fail: the code is rejected as not eligible for this account, or support says the account is too old. Go to Step B.

### Step B: new account, only if Step A fails

Follow `01-account-setup.md` Step 2 (the AU offer page, Expert Mode, create without a campaign, billing and offer in one sitting). Pause the empty old account and never enter a code in it: one business, one promotion. Use a card that was never on the old account's payments profile.

The spend is planned either way, so the worst case of a failed check is the lost credit, not wasted money.

## Verified terms (Google Ads Help, read 15 Oct 2026)

| Term | What Google says | Source |
|---|---|---|
| Who | A business that has never advertised with Google Ads, or an existing business expanding to a new country with a new billing address | Help 16324294, 2393021 |
| When to redeem | At sign up, or within 14 days of account creation; the account must be under 14 days old at redemption with a valid payment method added. Nothing is applied retroactively | Help 6388096, policy 1396257 |
| How it attaches | Chosen on the Google Ads Australia offer page before sign up and applied when billing is entered; otherwise a code goes in at Billing > Promotions (blue plus) | Help 16324294, 7646208 |
| Spend window | The qualifying spend must be completed within 60 days of redemption. Only spend after redemption counts. Paying A$600 in is not the same as spending it on ads | Help 16323427, 2393021 |
| Spend basis | Excluding taxes and fees, so about A$660 of card charges clears a A$600 threshold | AU terms reproduction, single secondary source |
| What counts | No restriction by campaign type on the new advertiser offer, so Standard Shopping and Search both count | Help 2393021 |
| Verification | After the threshold, status moves Redeemed, Processing (up to 35 days), then Active, Expired or Invalidated. Chase support if nothing has moved after 35 days | Help 16323427 |
| The credit | Covers future costs only, is used before the card is charged, and normally expires 60 days after it is added. Unused credit is forfeited | Help 6388096, 16915411 |
| What kills it | Switching to monthly invoicing after redeeming, changing the payments profile, a payment failure, or reusing a payments profile that touched another Ads account (a September 2026 case had a US$3,200 credit invalidated for exactly that) | Help 16324294, 15628336; Search Engine Land 11 Sep 2026 |
| Amount in Australia | Google's Australian page shows a tiered chooser ("spend a set amount in the first 60 days", some tiers 2X). Agencies quote A$600 for A$600, A$540 for A$540 and a ladder up to A$4,500 for A$9,000. The screen on creation day is the only truth | business.google.com/aunz; secondary AU sources |
| Shopify | The Shopify channel cannot create an Ads account and has no separate credit; its "$500 USD" page is the 2022 version of the same Google offer. Create the account at ads.google.com | Shopify Help Center; shopify.com/au/google |
| Google Partners | If an agency ever offers a Partner code: 20 days from account creation, applied by the partner, one offer per account. Pick one route, never both | Help 15329625 (en-AU) |

Which tier: at A$30 a day the account spends about A$900 a month, so pick the lowest tier at or above A$600 and nothing with a requirement above about A$900. A A$600 requirement is met in 20 spending days. A A$2,900 tier cannot be met in 60 days at this budget and would simply expire.

## The sequence

Account creation sits in the week before launch, not earlier: the 14 day redemption clock runs from creation and the 60 day spend clock from redemption, so every idle day between creation and the first ad shortens the spend window for nothing.

| Date | Action |
|---|---|
| 16 to 19 Oct | Eligibility checks (`01-account-setup.md` Step 1). Confirm legal entity name and ABN. Confirm payments.google.com for endlesspks holds no payments profile that was ever used for Google Ads. Finish the feed fixes and conversion prep that need no Ads account (`02`, `03`). |
| 20 to 22 Oct | Step A in the existing account: confirm zero impressions ever, AUD, billing set up, then attach the offer at Billing > Promotions (code from the AU offer page or from Google Ads support chat). Confirm a row in Redeemed status and write down the spend by date and the expiry date. Only if refused: Step B, create a new account from the AU offer page in Expert Mode with billing and the offer in one sitting. |
| 22 to 26 Oct | Hygiene settings, Merchant Center link, Shopify channel connection, campaign builds (`01` Step 3 onward, `02`, `04`). All campaigns paused. No spend. |
| 27 Oct | Launch at A$30 a day. First impressions. |
| 3 Nov | Day 14 from a 20 Oct redemption or creation: last possible day to redeem if the offer did not attach. Check Billing > Promotions again. |
| 16 to 18 Nov | A$600 ex GST reached (about 20 spending days). Status should move to Processing. If pacing is under A$25 a day, lift the budget so the threshold lands before 10 Dec. |
| 18 Dec | Promotions must show Processing or Active. If it still shows Redeemed with a shortfall, spend the gap that day; the window closes on day 60. |
| 21 Dec | Latest date for the credit to land (35 days after 16 Nov). If absent, contact Google Ads support with the screenshots. |
| 21 Dec to mid Feb | The credit draws down automatically ahead of the card. Keep campaigns live through January; the calendar's post Christmas pull back goes to A$26 a day, never to zero. A January pause wastes the credit. |
| About 17 Feb 2027 | Worst case expiry (credit added 21 Dec plus 60 days). Confirm the promotional balance is zero. |

## Do not

- Do not create the account from inside Shopify or Merchant Center. That route is a Performance Max builder that spends from day one and nothing shows the offer surfacing there.
- Do not enter a code on more than one account, and do not create a second account for the same website unless Step A failed.
- Do not request monthly invoicing, change the payments profile, or move billing to a manager account on this account.
- Do not let advertiser verification lapse: a verification pause inside the 60 days stops spend but not the clock. Start it on day one (`04-campaign-build.md`) and make the documents match the payments profile name exactly.
- Do not count on a specific amount until the sign up screen shows it.
