# C4: Sequencing and timing that protects the new advertiser credit (A$30 a day account)

Prepared 15 Oct 2026 for Endless Parks. Builds on R10 finding 10. Method: 31 extended web searches; page fetches are blocked, so quotes are search extracts. Google Help pages are undated, accessed 15 Oct 2026.

## 1. Findings

1. **The 14 day clock runs from account creation in Google's current wording, not first impression.** Google Ads Help 6388096: new advertiser offers apply only if "the account is under 14 days old when the offer is redeemed", with "a valid payment method added to your account" and "no prior Google Ads advertising for the same business through a different account". Advertising Policies 1396257: "most offers need to be applied at sign up, while others need to be applied within 14 days after you first create your Google Ads account"; Google "can't provide promotional offers retroactively". Older AU terms (Alexandria Today, undated; Justia, 8 Aug 2024) say "applied to your first Google Ads account within 14 days of your first ad impression being served". Plan to account creation: stricter, and current. https://support.google.com/google-ads/answer/6388096, https://support.google.com/adspolicy/answer/1396257. Confidence: High.

2. **The standard offer is chosen on the offer page before sign-up and attaches automatically; no emailed code is needed.** Google Ads AU home page: "Select an offer that fits your monthly budget and sign up when ready", "Spend {target amount} with Google Ads in the first 60 days to unlock the credit", "Sign up and complete payment setup to apply the offer to your account". Help 16324294: "Sign up to claim your offer. Some entry channels require you to choose your promotional offer value before beginning the sign-up process", then check Billing > Promotions. Emailed codes are periodic (Shopify Community: "no promo code was active on the account"). https://ads.google.com/intl/en_au/home/. Confidence: High on mechanism, Med on labels.

3. **A payment method must exist before redemption, and monthly invoicing must never be switched on later.** Help 16324294: "Before you begin: you'll need to enter a payment method. If you'd like to use monthly invoicing, set it up before you enter your offer. Otherwise, the offer will be invalidated and the amount lost when you switch to invoicing." AU terms: "Offer applies only if a payment profile and a valid payment method are added during initial signup." https://support.google.com/google-ads/answer/16324294. Confidence: High.

4. **Expert Mode "Create an account without a campaign" does not itself break the offer, but it defers the payment setup that applies it.** No source covers the combination. Google's AU page ties the offer to "complete payment setup"; Help 7646208 (en-AU) says non Smart mode advertisers "can still apply and track promotional codes, but the process might be slightly different". So: enter via the offer page, switch to Expert Mode, create without a campaign, add billing in the same session, confirm a Redeemed row under Billing > Promotions. If absent, enter a code (blue plus) or claim the codeless offer before day 14. https://support.google.com/google-ads/answer/7646208?hl=en-AU. Confidence: Med (inference).

5. **Only spend after redemption counts; the window is 60 days.** Help 16323427: "Only the amount spent after redeeming the promotional offer is counted. Spend made before redeeming the offer won't count toward it." Help 2393021 (en-AU): "New advertisers promotions typically require spend to be completed within 60 days". AU terms: "accrue costs of at least $600 (excluding any taxes or applicable fees) within 60 days"; "making a payment of $600 is not sufficient". Start event differs: redemption (self-serve pages), "first impression" (Partners 7624810), "first 60 days" (AU home page). Plan to the earliest. https://support.google.com/google-ads/answer/16323427, https://support.google.com/google-ads/answer/2393021?hl=en-AU. Confidence: High on rule, Med on start event.

6. **Verification runs after the threshold, up to 35 days, and can end in Invalidated.** Help 16323427 statuses: Redeemed (spend not met), Processing ("The spend requirement has been met. Our system is currently validating the account's eligibility ... may take up to 35 days"), Active (granted), Expired ("expired after redemption and before the spend requirement was met"), Invalidated ("if the promotional offer requirements aren't met"); "If your credit hasn't appeared after 35 days, contact Google Ads support." Help 2393021 (en-AU): "an up to 35-day verification period that confirms an advertiser is new to Google". Sep 2026 reports (Search Engine Land 488330, Search Engine Roundtable, ppcnewsfeed, Bushletter): a US$3,200 credit marked Invalidated a month after qualifying spend, and a new account voided "because the billing profile from Melamed's manager account had been used to set up the account". Confidence: High on statuses, Med on the reports.

7. **Credit covers future costs only and expires 60 days after it lands.** Help 6388096: credits "cannot be used to pay for costs accrued before the credit was applied, and cannot cover the spend requirement itself"; "automatically applied to future ad spend until it runs out or expires"; "advertisers normally have 60 days to spend their earned promotional credit after it has been added"; on cancellation or expiry "the remaining balance can't be refunded"; after a billing transfer "your promotional credits will expire". Help 16915411 (en-AU), postpay (formerly automatic payments): "Costs accrued before you get a credit, and costs accrued after you use up the credit, are charged to the payment method". AU terms: "expires 60 days after being applied to the account". https://support.google.com/google-ads/answer/16915411?hl=en-AU. Confidence: High.

8. **Pausing stops neither clock and forfeits nothing by itself.** Help 2424604: "Paused campaigns won't accrue any extra costs." Comrade Web (undated, single secondary source): "if you pause your ads for a week, the 60-day clock does not stop." AU terms let Google remove the offer "if a payment fails ... or your account otherwise falls out of good standing" and "nullify that credit". Confidence: Med.

9. **Spend must sit in the one account holding the offer; every campaign type there counts.** Terms: "applied to your first Google Ads account". Help 16324294: "Manager account users can't enter a promotional offer from the manager level." Help 2393021 reserves "spend ... on a specific campaign type" for existing advertiser offers only, so Standard Shopping and Search costs count. No source names Shopping explicitly. Confidence: Med.

10. **AU tier amounts are unconfirmed by Google extracts; the sign-up screen is the source of truth.** Reported: A$600 for A$600 (Online Road 2026; Alexandria Today); A$540 for A$540, A$650 for A$720, A$2,000 for A$4,000 (Overt Digital, Feb 2026); A$540 for A$540, A$1,500 for A$2,900, A$4,500 for A$9,000, "Offer Ends 30/9/26" (All Marketing, Perth); "Up to $1,800" (Bang Media). A US 2x offer (US$500 earns US$1,000) entered the sign-up flow in May 2026 (almcorp, ppcnewsfeed); no source places it in Australia. Confidence: Low on amounts.

11. **Google Partners variant: 20 days from account creation, applied by the partner.** Help 15329625 (en-AU): credits are "available for eligible accounts for 20 days after the advertiser's account was created. After that, the credit disappears from the Promotional offers menu"; advertiser "must be new to Google Ads"; partner cap "15% of the manager account's rolling 90-day spend". Help 7624810: "New client accounts will have 60 days (from first impression) to spend $500 USD to qualify"; verification "will shift from before the offer is applied to after the client reaches the required spend value. It will take up to 35 days"; partners now "choose from several credit values to apply manually". https://support.google.com/google-ads/answer/15329625?hl=en-AU. Confidence: High.

12. **The Shopify route is USD and stale.** shopify.com/au/google: "enjoy $500 USD in ad credit when you spend $500 USD within 60 days"; Shopify's 2022 fine print required "a US billing address" and "one code per advertiser". Do not claim it; it would conflict with the direct AU offer. Confidence: Med.

## 2. What this means for Endless Parks

- **Create the account in the week before launch, not earlier.** The 14 day window runs from creation and the offer is redeemed at sign-up, so a creation to launch gap only eats the 60 day spend window. A 7 day gap is cheap: A$600 needs 20 spending days at A$30, leaving a 33 day buffer.
- **Enter through the AU offer page signed in as endlesspks@gmail.com.** Pick the lowest tier at or above A$600 (a A$900 a month account cannot safely hit a A$2,900 tier in 60 days). Switch to Expert Mode, create without a campaign, then immediately Billing > Settings: business payments profile with ABN and Balcatta address, card, postpay. Then Billing > Promotions: screenshot the Redeemed row with its T&C link and dates.
- **Fresh billing identity, postpay only.** Never reuse a card or payments profile that has touched another Google Ads account (that caused the Sep 2026 invalidation). Never request monthly invoicing.
- **Pre-check "new to Google Ads".** If endlesspks, the Shopify channel or an agency ever served a Google ad for Endless Parks, Processing can end in Invalidated after the A$600 is spent. The spend is planned anyway, so the downside is the credit, not wasted money.
- **Keep spending through the credit window.** The credit lands between early December and 21 Dec 2026 and expires 60 days later. A$600 is 20 days at A$30 a day, fewer with the R01 Christmas uplift. A January pause wastes it.

Dated checklist (creation 20 Oct, launch 27 Oct, A$30 a day):

| Date | Day | Action |
|---|---|---|
| 16 to 19 Oct | pre | R10 finding 12 checks: no Endless Parks Google ad ever served; ABN and legal name; no payments profile tied to another Ads account. |
| Tue 20 Oct | 0 | AU offer page, sign in as endlesspks, choose tier, sign up, Expert Mode, create without campaign, Australia, Perth time zone, AUD. Same session: payments profile, card, postpay. Promotions: screenshot Redeemed row, note spend-by and expiry dates. |
| 20 to 26 Oct | 0 to 6 | R10 hygiene steps. No spend. |
| Tue 27 Oct | 7 | Launch Shopping A$22, brand Search A$3, non-brand Search A$5. First impressions. |
| Tue 3 Nov | 14 | Last day to redeem if the offer did not attach on day 0. Re-check Promotions. |
| 16 to 18 Nov | 27 to 29 | A$600 ex GST reached (20 spend days). Status should move to Processing. If pacing under A$25 a day, lift budget so A$600 lands before 10 Dec. |
| Fri 18 Dec | 59 | Promotions must show Processing or Active, not Redeemed. If Redeemed with a shortfall, spend the gap today; day 60 turns it Expired. |
| Sat 19 Dec | 60 | Spend window closes (earliest reading). |
| Mon 21 Dec | 62 | Latest date for the credit (35 days after 16 Nov). If absent, contact Google Ads support with screenshots. |
| 21 Dec to 17 Feb | 62 to 120 | Credit draws down automatically. Keep campaigns live through January. Check Billing > Summary monthly for the promotional credit line. |
| Wed 17 Feb 2027 | 120 | Worst case expiry is 19 Feb (21 Dec plus 60). Confirm balance is zero; unused credit is forfeited. |

## 3. Where sources disagree

- **14 day trigger:** Google 6388096 and policy 1396257 say account age at redemption; older AU terms and agency guides say first impression. Plan to account age.
- **60 day start:** self-serve Help says after redemption; Partners page says first impression; AU home page says "first 60 days"; Overt says "account creation or promotion activation". Plan to redemption.
- **Tier amounts:** A$600, A$540, A$1,800 and A$4,500 all circulate; one Perth page ends 30 Sep 2026. Read the screen.
- **One offer per advertiser:** only in reproduced T&Cs and agency pages; Google's pages instead bar prior advertising "through a different account".
- **Invalidation response:** Bushletter says no remedy; ppcnewsfeed says the Ads Liaison would escalate. No fix by 15 Oct 2026.
- **Pause and the clock:** one secondary source; Google is silent.

## 4. Open questions for Jake

1. Has any Google ad ever served for Endless Parks (endlesspks login, Shopify channel, any agency)?
2. Does payments.google.com for endlesspks already hold a payments profile, and was it ever used for Google Ads?
3. What tiers and end date does the AU offer page show on 20 Oct when signed in as endlesspks? Screenshot the offer and T&C link.
4. Exact legal entity name and ABN for the business payments profile.
5. Will spend stay at or above A$30 a day from 27 Oct to mid February 2027, including January?
6. Is an agency or Google Partner involved? Pick one route, Partners (20 days) or direct, never both, and keep billing on Jake's own profile.

## 5. Sources

- Google Ads Help 6388096, About Google Ads promotional offers: https://support.google.com/google-ads/answer/6388096
- Google Ads Help 16324294, How to redeem your Google Ads promotional offer: https://support.google.com/google-ads/answer/16324294
- Google Ads Help 16323427, Check the progress of your Google Ads promotions: https://support.google.com/google-ads/answer/16323427
- Google Ads Help 16915411 (en-AU), Promotional offers with different payment settings: https://support.google.com/google-ads/answer/16915411?hl=en-AU
- Google Ads Help 2393021 (en-AU), Different types of promotional offers: https://support.google.com/google-ads/answer/2393021?hl=en-AU
- Google Ads Help 7646208 (en-AU), Enter a promotional code: https://support.google.com/google-ads/answer/7646208?hl=en-AU
- Google Ads Help 15329625 (en-AU), About Google Partners promotional offers: https://support.google.com/google-ads/answer/15329625?hl=en-AU
- Google Ads Help 7624810, Check eligibility and apply Partners offers: https://support.google.com/google-ads/answer/7624810
- Google Ads Help 2424604, Cancelling your account: https://support.google.com/google-ads/answer/2424604
- Google Ads Help 2375432, Payment settings (postpay, prepay): https://support.google.com/google-ads/answer/2375432
- Advertising Policies 1396257, Promotional offers policy: https://support.google.com/adspolicy/answer/1396257
- Google Ads AU home page (offer selector): https://ads.google.com/intl/en_au/home/ and https://business.google.com/aunz/google-ads/
- Search Engine Land, credits revoked after spending (Sep 2026): https://searchengineland.com/advertisers-report-google-ads-credits-being-revoked-after-spending-488330
- Search Engine Roundtable (Sep 2026): https://www.seroundtable.com/google-ads-credit-revoked-42049.html
- ppcnewsfeed, credits invalidated (Sep 2026): https://ppcnewsfeed.com/ppc-news/2026-09/google-ads-revokes-free-credits-after-use/
- Bushletter (Sep 2026): https://www.bushletter.com/google-voids-ad-credits-after-businesses-spend-to-qualify/
- TechWyse (2026): https://www.techwyse.com/news/platform-updates/google-ads-promotional-credits-invalidated-after-qualifying-spend
- almcorp, 2x credit for new accounts (May 2026): https://almcorp.com/blog/google-ads-2x-credit-new-accounts/
- ppcnewsfeed, 2x credit (May 2026): https://ppcnewsfeed.com/ppc-news/2026-05/get-2-ads-credit-new-google-ads-accounts/
- almcorp, Partners offers 2026: https://almcorp.com/blog/google-partners-promotional-offers/
- Alexandria Today, AU offer T&Cs (undated): https://alexandriatoday.com.au/google-ads-tcs
- Justia, new advertiser credit terms (8 Aug 2024): https://onward.justia.com/new-advertisers-get-up-to-1500-google-ads-credit/
- Overt Digital, AU credit tiers (Feb 2026): https://overtdigitalmarketing.com.au/understanding-google-ads-credits-tiers-in-australia/
- All Marketing, Perth, offer page (ends 30/9/26): https://www.allmarketing.com.au/google-ads-promo-eligibility/
- Online Road, A$600 credit (2026): https://onlineroad.com.au/blog/boost-your-business-with-google-ads-and-claim-a-600-credit/
- Bang Media, up to $1,800: https://www.bangmedia.com.au/google-ads-credit
- Little Dragon, coupon guide (Sep 2026, Canada): https://littledragon.ca/how-to-claim-your-600-google-ad-credit-coupon/
- Comrade Web, contractor credit guide (undated): https://comradeweb.com/blog/how-to-get-600-of-google-ads-credit/
- Shopify Australia, Google & YouTube: https://www.shopify.com/au/google
- Shopify Community, "Is the Google $500 discount a scam?": https://community.shopify.com/t/is-the-google-500-discount-a-scam/127451
- Shopify Community, $500 Google Ads credit (Sep 2025): https://community.shopify.com/t/500-google-ads-credit/566190
