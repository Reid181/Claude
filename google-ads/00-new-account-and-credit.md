# 00. The account and the new advertiser credit

Decision (Jake, 15 Oct 2026): use the existing Google Ads account, which has never run ads, and claim Google's new advertiser credit in it. Create a new account only if Google refuses to attach the offer to the existing one. This file is the sequence that protects the credit. Read it before `01-account-setup.md`.

## The one condition that matters

Google defines a new advertiser as "a business that has never advertised with Google Ads", not a new account or a new login. The credit is checked after the spend, in an "up to 35 day verification period that confirms an advertiser is new to Google", and an account "found to be advertising for a business that was already advertising with Google Ads" gets nothing. Google's own example of a promotional offers violation is setting up several accounts for the same website and applying a code to each; the penalty is losing access to promotions, not losing the Ads account.

So a new account only earns the credit if no Google ad has ever served for endlessparks.com from any account: endlesspks@gmail.com, any agency, anyone who once clicked Create Campaign in the Shopify channel's Performance Max module. Free listings in Merchant Center do not count as advertising.

Before creating anything, run the four checks in `01-account-setup.md` Step 1. The outcome decides the path:

- Nothing found: create a new account and claim the credit at sign up.
- An account exists but never served an impression (Jake's position on 15 Oct): the business is still new, so the credit is available. Which account can take it is where Google's own pages disagree, read in full on 15 Oct 2026. The Australian promotional credit terms (google.com/intl/en-AU_AU/ads/coupons/terms) say a new advertiser qualifies when "your first ad impression was served from your first Google Ads account no more than 14 days before you enter your promotional code", which an account with no impressions satisfies. Google Ads Help 6388096 (en-AU) says "your account must be less than 14 days old at the time of redemption". Two more facts narrow the options: offers are "selectively distributed through marketing communications or the Promotions page" and "aren't available by request", and Help 2393021 says "Google support can't provide promotional offers upon request". So the existing account can only take the credit if an offer is already sitting on its Promotions page or a promotional code reached the endlesspks inbox (codes expire three months after issue). Step A checks both. If neither exists, the only route to the credit is a new account, where the offer attaches at sign up (Step B); Help 2393021's own example says a second account for a business that has never advertised qualifies, and the old empty account must simply never use a promotion ("one promotional credit per customer").
- An account that served ads for Endless Parks at any time: the business is not new. Build the plan in that account (dormant path in `01-account-setup.md`) and forget the credit. A second account would spend the same A$30 a day, be invalidated at the 35 day check, and risk promotions access.

### Step A: look first, pay later (five minutes on 16 Oct, repeated 20 Oct)

Look before anything touches billing. A payments profile added to the old account and then reused is exactly what invalidated a credit in September 2026, so the old account gets a payments profile only if it is going to carry the offer.

Signed in as the account's owner (expected endlesspks@gmail.com):

1. Billing > Promotions: is an offer listed as available for this account? Read its terms if so. Screenshot.
2. Gmail, query `from:(ads-noreply@google.com OR googleads-noreply@google.com) (promo OR promotional OR code OR credit)`: any code issued to this account in the last three months? Screenshot.
3. Campaigns > Change history, earliest entry, or the welcome email date: account creation date. Admin > Account settings: currency and time zone.
4. Campaigns (date range All time, or Billing > Documents if the account has never had a campaign and opens on the campaign builder): zero impressions, zero cost, no invoice. Screenshot.

Decision, made on 16 Oct:

- An offer is listed on the Promotions page, or a code was emailed for this account and the account is under 14 days old, and the currency is AUD: Step A continues on 20 to 22 Oct. Add the payments profile then (business, legal entity name and ABN as on the ABR, Balcatta address, GST registered, automatic payments, card), accept the offer or enter the code, confirm a Redeemed row with its spend by and expiry dates, screenshot. Never switch to monthly invoicing afterwards.
- Anything else (no offer listed, no code, account older than 14 days with only a generic code, currency not AUD): Step B. Do not add billing to the old account, do not enter any code in it "to see if it attaches" (an attached code invalidated at the 35 day check is the worst outcome, because the calendar assumes the credit lands before Christmas), and leave it paused and untouched. Expect this outcome: the account has been linked to Shopify for some time, so it is almost certainly older than 14 days.

Do not ask support for a code: Google's pages say offers are not available by request and support cannot provide them.

### Step B: new account (20 to 22 Oct)

1. Sign in to Chrome as jakereidmedia@gmail.com, which has no Google Ads account, so the offer page's sign up flow runs clean and the offer attaches at sign up. (Signed in as endlesspks, "Start now" opens the existing account instead; the account picker's "New Google Ads account" route exists but nothing confirms the offer attaches on it.)
2. Open the Google Ads Australia offer page (ads.google.com/intl/en_au/home or business.google.com/aunz/google-ads), screenshot the tiers and the terms link, choose the lowest tier at or above A$600 and nothing with a spend requirement above about A$900.
3. Start now > "Are you a professional marketer? Switch to Expert Mode" > "Create an account without a campaign" > billing country Australia, time zone (GMT+08:00) Perth, currency Australian Dollar > Submit.
4. Same sitting: Billing > Settings > a NEW payments profile (Business, the family trust's registered name and ABN with trustee ENDLESS PARKS PTY LTD, since the trust is the GST registered entity, 4/16 Ledgar Rd Balcatta WA 6021, GST registered ticked, see `PLAN.md` question 1), automatic payments, a card that has never been on any Google Ads payments profile. Then Billing > Promotions: a row in Redeemed status with spend by and expiry dates. Screenshot. If no row, enter the offer page code with the blue plus. Day 14 from creation is the last day it can attach.
5. Admin > Access and security > Users: invite endlesspks@gmail.com as Admin. The Shopify channel connection must be made by a Google account that is Admin on the Ads account, and the channel is signed in as endlesspks.
6. Shopify admin > Google & YouTube > Settings > Google Ads card: disconnect the old account (inside the card, never by uninstalling the app), then connect the new customer ID. Decline any Performance Max prompt.
7. The old account: never enter a code in it; one business, one promotion. Cancel it later (Admin > Account settings) once the credit on the new account is Active, or leave it paused.

The spend is planned either way, so the worst case of a failed check is the lost credit, not wasted money.

## Verified terms (Google Ads Help, read 15 Oct 2026)

| Term | What Google says | Source |
|---|---|---|
| Who | A business that has never advertised with Google Ads, or an existing business expanding to a new country with a new billing address. Google's example: a second account for a different business of the same owner qualifies | Help 16324294, 2393021 (full page) |
| When to redeem | Help 6388096: the account must be less than 14 days old at redemption, with a valid payment method, and the business must not have advertised through a different account. AU terms: first ad impression from your first account no more than 14 days before the code is entered. Nothing is applied retroactively | Help 6388096, AU terms, policy 1396257 (full pages) |
| How it attaches | Most new advertiser promotions are redeemed at sign up; otherwise an offer shown on Billing > Promotions, or a code from Google's own marketing emails entered with the blue plus. Not available by request and support cannot provide one | Help 16324294, 2393021, policy 1396257 (full pages) |
| Spend window | The qualifying spend must be completed within 60 days of redemption. Only spend after redemption counts. Paying A$600 in is not the same as spending it on ads | Help 16323427, 2393021 |
| Spend basis | "Payment of any taxes or other fees by Advertisers will not count towards earning any promotional credit", so about A$660 of card charges clears a A$600 threshold. Credit cannot be used to pay GST either | AU terms (full page) |
| What counts | No restriction by campaign type on the new advertiser offer, so Standard Shopping and Search both count | Help 2393021 |
| Verification | After the threshold, status moves Redeemed, Processing (up to 35 days), then Active, Expired or Invalidated. Chase support if nothing has moved after 35 days | Help 16323427 |
| The credit | Applied "typically within 35 days" of the qualifying spend to the Billing summary, covers future costs only, cannot cover the spend requirement itself, and "expires 60 days after it is applied". Unused credit is forfeited. Google Australia Pty Ltd may revoke the offer at any time | Help 6388096, AU terms (full pages) |
| What kills it | Switching to monthly invoicing after redeeming, changing the payments profile, a payment failure, or reusing a payments profile that touched another Ads account (a September 2026 case had a US$3,200 credit invalidated for exactly that) | Help 16324294, 15628336; Search Engine Land 11 Sep 2026 |
| Amount in Australia | Google's Australian page shows a tiered chooser ("spend a set amount in the first 60 days", some tiers 2X). Agencies quote A$600 for A$600, A$540 for A$540 and a ladder up to A$4,500 for A$9,000. The screen on creation day is the only truth | business.google.com/aunz; secondary AU sources |
| Shopify | The Shopify channel cannot create an Ads account and has no separate credit; its "$500 USD" page is the 2022 version of the same Google offer. Create the account at ads.google.com | Shopify Help Center; shopify.com/au/google |
| Google Partners | If an agency ever offers a Partner code: 20 days from account creation, applied by the partner, one offer per account. Pick one route, never both | Help 15329625 (en-AU) |

Which tier: at A$30 a day the account spends about A$900 a month, so pick the lowest tier at or above A$600 and nothing with a requirement above about A$900. A A$600 requirement is met in 20 spending days. A A$2,900 tier cannot be met in 60 days at this budget and would simply expire.

## The sequence

Account creation sits in the week before launch, not earlier: the 14 day redemption clock runs from creation and the 60 day spend clock from redemption, so every idle day between creation and the first ad shortens the spend window for nothing.

| Date | Action |
|---|---|
| 16 Oct | Step A look (Promotions page, inbox, creation date, impressions ever) and the A or B decision. Confirm legal entity name and ABN. Confirm payments.google.com for endlesspks holds no payments profile that was ever used for Google Ads. |
| 16 to 19 Oct | Feed fixes, site hygiene, Merchant Center and conversion prep that need no Ads account (`02`, `03`, `10`). If the decision was Step A, the hygiene settings in `01` Step 3 can also be done now in the existing account; if Step B, build nothing in the old account. |
| 20 to 22 Oct | Step A continues (payments profile, accept the listed offer, Redeemed row) or Step B (new account from the AU offer page as jakereidmedia, Expert Mode, new payments profile, Redeemed row, invite endlesspks as Admin, reconnect the Shopify channel). Screenshot the Redeemed row and write down the spend by date and the expiry date. |
| 22 to 26 Oct | Hygiene settings, Merchant Center link, Shopify channel connection, campaign builds (`01` Step 3 onward, `02`, `04`). All campaigns paused. No spend. |
| 27 Oct | Launch at A$30 a day. First impressions. |
| 3 Nov | Day 14 from a 20 Oct redemption or creation: last possible day to redeem if the offer did not attach. Check Billing > Promotions again. |
| 16 to 18 Nov | A$600 ex GST reached (about 20 spending days). Status should move to Processing. If pacing is under A$25 a day, lift the budget so the threshold lands before 10 Dec. |
| 18 Dec | Promotions must show Processing or Active. If it still shows Redeemed with a shortfall, spend the gap that day; the window closes on day 60. |
| 23 Dec | Latest date for the credit to land (35 days after a threshold reached about 18 Nov). If absent on 24 Dec, contact Google Ads support with the screenshots. |
| Late Dec to Feb | The credit draws down automatically ahead of the card. Keep campaigns live through January; the calendar's post Christmas pull back goes to A$26 a day, never to zero. A January pause wastes the credit. |
| About 21 Feb 2027 | Worst case expiry (credit added 23 Dec plus 60 days). Confirm the promotional balance is zero. |

## Do not

- Do not create the account from inside Shopify or Merchant Center. That route is a Performance Max builder that spends from day one and nothing shows the offer surfacing there.
- Do not enter a code on more than one account, and do not create a second account for the same website unless Step A failed.
- Do not request monthly invoicing, change the payments profile, or move billing to a manager account on this account.
- Do not let advertiser verification lapse: a verification pause inside the 60 days stops spend but not the clock. Start it on day one (`04-campaign-build.md`) and make the documents match the payments profile name exactly.
- Do not count on a specific amount until the sign up screen shows it.
