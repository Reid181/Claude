# C2: Eligibility traps when creating a new Google Ads account for the new advertiser credit

Prepared 15 Oct 2026 for Endless Parks (Perth, AUD, A$30/day). Builds on R10 finding 10 and section 2. Method: 24 extended web searches; the fetch of google.com/intl/en_au/ads/coupons/terms was blocked. Quotes are from search extracts, not full page reads. Single secondary sources are marked.

## 1. Findings

1. **"New" is defined per business, not per Google Ads account, login or payments profile.** Help 2393021 (Different types of promotional offers): "You're considered a new advertiser if you're creating an account for a business that has never advertised with Google Ads or if you're expanding an existing business to a different country (with a new billing address)." Help 6388096 (About Google Ads promotional offers): "These offers are for businesses new to Google Ads. To be eligible: Your account must be less than 14 days old at the time of redemption", a valid payment method is added, and the advertiser "cannot have advertised with Google Ads before using a different account for the same business." Accessed 15 Oct 2026. Confidence High. A jakereidmedia login passes the account-age test and does nothing for the business test.

2. **The business-level check runs after the spend, and a failed check means no credit.** Help 2393021: "After completing the required spend, there is an up to 35-day verification period that confirms an advertiser is new to Google before they are eligible to receive their earned credit." Help 15329625 (Partners offers, en-AU): "If the account is found to be advertising for a business that was already advertising with Google Ads, it won't receive the ad credit"; "If a client meets the spend requirement, but isn't a new advertiser to Google, the credit won't be applied." Help 7624810: "The advertiser is new to Google Ads (20 days from their account creation)." Accessed 15 Oct 2026. Confidence High. Jake would spend the full A$600 before learning the answer.

3. **Promotion statuses, including "Invalidated", are documented.** Help 16323427 lists Redeemed (currently earning), Processing ("the system is validating the account's eligibility and the reward credit will show up if all criteria is met. This process may take up to 35 days."), Expired, and Invalidated ("This can happen if the promotional offer requirements aren't met."). Contact support if no credit after 35 days. Accessed 15 Oct 2026. Confidence High.

4. **Two accounts pointed at one website with a code on each is Google's own example of a promotional offers violation.** Help 9027742 (About disabled promotional offers): "setting up multiple Google Ads accounts to drive traffic to the same website, and then applying a promotional code to each of these Google Ads accounts". Consequences: "Google may email you with a warning and a chance to fix the problem. If you don't correct the problem in the given time period, Google may suspend your access to promotional offers"; serious violations bring "immediate suspension of your access to promotional offers without prior notification." The penalty is loss of offer access, not closure of the Ads account. Accessed 15 Oct 2026. Confidence High on wording, Med on application to a dormant plus new pair.

5. **The circumventing systems policy does not, on its text, ban a second account for an unsuspended business, but it is enforced without warning.** Advertising Policies Help 15938075 (en-AU): "you can't create multiple Google Ads accounts after getting suspended to try to get around Google Ads' policies"; "spreading ads that violate Google Ads' policies across 2 or more accounts"; egregious violations mean "your Google Ads accounts will be suspended upon detection and without prior warning"; "if you have multiple advertising accounts, make sure that each account is connected to a real business." Agencies (Rankite 2026, Kampaio, Sendwin) say Google links accounts "through shared payment methods, IP addresses, browser fingerprints, device identifiers, or billing addresses"; secondary only. Confidence High on policy text, Med on linking signals.

6. **September 2026 reports of credits invalidated after the qualifying spend, with no appeal route.** Search Engine Land (11 Sep 2026), Search Engine Roundtable, ppcnewsfeed and Techwyse report consultant David Melamed's two cases: a US$3,200 credit "marked 'Invalidated' more than a month after the spend had occurred", and a credit "invalidated because the billing profile from Melamed's manager account had been used to set up the client's account initially." He "was not aware of a way for advertisers to appeal"; Google Ads Liaison Ginny Marvin "would escalate the issue" and "offered no fix." Confidence High on the reports, Med on causes (one consultant, no Google explanation).

7. **Payments profile rules that can kill the credit.** Help 15628336: "if you have a promotional credit, it won't be transferred or refunded." Help 16324294: set up monthly invoicing before entering the offer, "Otherwise, the offer will be invalidated and the amount lost when you switch to invoicing." Reproduced AU terms (alexandriatoday.com.au, undated): "a payment profile and a valid payment method... during the initial signup process"; the account "must be successfully billed by Google Ads and remain in good standing in order to remain eligible to use the credit." No Google page says a repeated ABN or billing address blocks the offer; the Melamed case shows a reused payments profile is a documented trigger. Confidence High on Help pages, Med on the AU terms (single reproduction).

8. **The Shopify Google & YouTube channel does not create a Google Ads account.** Shopify Help Center (connect page): "To set up Google Ads, you must have an existing Google Ads account. The connected Google account must be an administrator on the Google Ads account." Only the Merchant Center step offers "Create new". BlueTuskr says the dropdown lets you "create a new one"; single secondary source, contradicted by Shopify. Shopify's marketing page still shows "enjoy $500 USD in ad credit when you spend $500 USD within 60 days. Terms and Conditions apply", about four years old. Confidence High on the existing-account rule, Low that the US$500 wording is current for AU.

9. **The current Australian offer could not be confirmed from a Google page.** Reproduced AU terms (alexandriatoday.com.au): "Offer available only to advertisers which are new to Google Ads, with a billing address in Australia. One promotional code per advertiser"; applied "to your first Google Ads account within 14 days of your first ad impression being served"; spend within 60 days, and "making a payment of the required amount is not sufficient." All Marketing (Perth, 2026): tiers $540, $1,500 and $4,500, "offer ends 30/9/26 or as amended by Google's promotional terms", "qualifying spend within 60 days of code application." Overt Digital (Feb 2026) also reported A$540; Online Road (2026) says "often $600"; ppcnewsfeed's 2026 offers are US or unspecified. Confidence Low to Med on amount; only the sign-up flow is authoritative.

10. **GST treatment of the spend threshold is undocumented this pass.** No source states whether the threshold is before or after the 10% GST Google Australia Pty Ltd adds (Help 2375370 en-AU). R10 read the reproduced AU terms as ex GST; not re-confirmed. Confidence Low. Plan for A$600 of ad cost before GST (about A$660 billed).

11. **Advertiser verification and payment holds do not cancel the credit by rule, but they stop spend inside the 60-day window and can breach the good standing clause.** Advertising Policies Help 15577076: Google notifies "via an in-account notification or an email"; the account is paused if not verified by the deadline shown in the account; "Advertisers with no deadline can still run ads"; review takes "up to five working days", "in rare cases... up to 30 days"; "Bank transfer payments take longer, so your account may be paused until the payment comes through". AU documents (Help 9872280, co=AU) depend on account type "Organisation" or "Individual" and must "exactly match your payments profile info, including the organisation name." Confidence High on mechanics, Med on the credit interplay (inference).

12. **Dormant account: Google's definition has no minimum spend, so a few impressions years ago is still "has advertised".** No Google page sets a threshold. A 2015 Google sales addendum (SEC filing) defined a New Advertiser as one without "a Google AdWords account that has been active, as determined by Google, in the 90 calendar day period before activation"; an old partner contract, not the consumer offer. Anecdotes (all secondary): Blind, "since you already had an account they wouldn't give you the sign up bonus"; doublebricks, "using an account with a pre-existing Google Ads history will invalidate the offer"; Google Ads Community thread 339363277, "Only newly setup account have eligibility". No r/PPC, r/googleads or Shopify Community thread on a deliberate second account surfaced in 24 searches. Confidence Med.

## 2. What this means for Endless Parks

The decision turns on one unchecked fact: has endlessparks.com ever had a paid Google ad served, from any account, by anyone (including a past agency MCC)? The login is irrelevant to Google's test.

Case A, no prior advertising for the business (no account, or one with zero impressions and no billing): Endless Parks is a new advertiser. Create one account only. The endlesspks login is cleanest because it already administers Merchant Center 5382740922 and the Shopify channel; jakereidmedia works for the credit but adds admin friction. Redeem and add the card at sign-up, create a fresh payments profile with the ABR entity name and Balcatta address, and do not reuse a payments profile from another Google product. At A$30/day the A$600 is reached in 20 to 22 days; budget A$660 billed with GST; expect the credit up to 35 days after the threshold, then 60 days to use it. Change nothing in billing or account structure in that period.

Case B, the endlesspks account ever served an ad: a jakereidmedia account passes the 14-day age test but fails the business test at Processing, after the A$600 is spent, with the documented outcome "Invalidated" and no appeal. If both accounts point at endlessparks.com with a code applied, Help 9027742's example applies and offer access can be suspended. Account suspension under circumventing systems is not supported by the policy text absent a prior suspension, but the expected value of the credit is near zero. The honest route is to reactivate the existing account (R10 section 2C), forgo the credit, and watch Billing > Promotions for the codeless offers Google selectively sends existing advertisers (Help 2393021).

Case C, an account only ever linked by the Shopify channel: Shopify cannot create an Ads account, so a person did; apply Case A or B by its impression history.

Either way, complete advertiser verification immediately with documents matching the payments profile name exactly; a pause inside the 60-day window stops spend and the good standing clause bites.

## 3. Where sources disagree

- Redemption deadline: 14 days account age (Help 6388096), 14 days from first impression (reproduced AU terms), 20 days from creation (Partners, Help 7624810). Redeem at sign-up and it is moot.
- Second account as circumvention: Google's text limits it to post-suspension and spreading violating ads; Rankite, Sendwin and Kampaio say one account per business and promo abuse triggers suspension. My read: the credit, not the account, is at risk, unless both accounts run ads.
- Shopify creating an Ads account: Shopify Help says existing account required; BlueTuskr says create new. Shopify is right.
- Current AU amount: $600 (Online Road, Alexandria Today), $540/$1,500/$4,500 ending 30 Sep 2026 (All Marketing, Overt Digital), US 2x offers (ppcnewsfeed). Trust the sign-up flow on the day.
- "One promotional code per advertiser": reproductions only, not Help pages. Consistent with the business-level definition, treat as real.
- 35 days: Help 16324294 omits it; Help 2393021, 15329625 and 16323427 state it.
- GST: R10 read ex GST; nothing this pass. Assume ex GST.

## 4. Open questions for Jake

1. Does ads.google.com as endlesspks@gmail.com open an account, and what do Campaigns (All time) and Billing > Documents show? Any impression puts Endless Parks in Case B.
2. Has any agency, freelancer or Mitch ever run Google Ads for endlessparks.com from their own manager account? That also counts as the business having advertised.
3. What does the sign-up flow offer today: amount, days to redeem, 60-day window, terms link? Screenshot it before submitting.
4. Does a Google payments profile for the trading entity already exist (Workspace, Merchant Center)? If so, create a new one rather than reusing it.
5. Is Jake willing to commit A$600 plus GST inside 60 days whether or not the credit lands?
6. Account type Organisation or Individual for verification, and who is the authorised representative with matching ID?

## 5. Sources

- Google Ads Help, Different types of Google Ads promotional offers (2393021): https://support.google.com/google-ads/answer/2393021?hl=en-AU
- Google Ads Help, About Google Ads promotional offers (6388096): https://support.google.com/google-ads/answer/6388096
- Google Ads Help, About Google Partners promotional offers (15329625, en-AU): https://support.google.com/google-ads/answer/15329625?hl=en-AU
- Google Ads Help, How to check eligibility and apply Google Partners promotional offers (7624810): https://support.google.com/google-ads/answer/7624810
- Google Ads Help, About disabled Google Ads promotional offers (9027742): https://support.google.com/google-ads/answer/9027742
- Google Ads Help, How to redeem your Google Ads promotional offer (16324294): https://support.google.com/google-ads/answer/16324294
- Google Ads Help, Check the progress of your Google Ads promotions (16323427): https://support.google.com/google-ads/answer/16323427
- Google Ads Help, How promotional offers work with different payment settings (16915411): https://support.google.com/google-ads/answer/16915411
- Google Ads Help, Change the payment profile (15628336): https://support.google.com/google-ads/answer/15628336
- Google Ads Help, Enter a promotional code (7646208, en-AU): https://support.google.com/google-ads/answer/7646208?hl=en-AU
- Google Ads Help, Taxes in your country (2375370, en-AU): https://support.google.com/google-ads/answer/2375370?hl=en-AU
- Google Ads Help, Shopify (15496063, en-AU): https://support.google.com/google-ads/answer/15496063?hl=en-AU
- Advertising Policies Help, Circumventing systems (15938075, en-AU): https://support.google.com/adspolicy/answer/15938075?hl=en-AU
- Advertising Policies Help, Promotional offers policy (1396257): https://support.google.com/adspolicy/answer/1396257
- Advertising Policies Help, Tasks required for advertiser verification (15577076): https://support.google.com/adspolicy/answer/15577076
- Advertising Policies Help, Document requirements, Australia (9872280): https://support.google.com/adspolicy/answer/9872280?co=GENIE.CountryCode%3DAU
- Advertising Policies Help, About Google Ads account pausing (9872152): https://support.google.com/adspolicy/answer/9872152
- Google Ads Community, Applying promotional credit (thread 339363277): https://support.google.com/google-ads/thread/339363277
- Shopify Help Center, Connect Google & YouTube: https://help.shopify.com/en/manual/online-sales-channels/marketplaces/google/getting-setup/connect
- Shopify, Sell on Google and YouTube: https://www.shopify.com/google
- Search Engine Land, Advertisers report Google Ads credits being revoked after spending (11 Sep 2026): https://searchengineland.com/advertisers-report-google-ads-credits-being-revoked-after-spending-488330
- Search Engine Roundtable, Google Ads credit revoked (Sep 2026): https://www.seroundtable.com/google-ads-credit-revoked-42049.html
- ppcnewsfeed, Advertisers upset as promotional credits get invalidated (Sep 2026): https://ppcnewsfeed.com/ppc-news/2026-09/google-ads-revokes-free-credits-after-use/
- Techwyse, Google Ads credits revoked after qualifying spend (Sep 2026): https://www.techwyse.com/news/platform-updates/google-ads-promotional-credits-invalidated-after-qualifying-spend
- Bushletter, Google voids ad credits after businesses spend to qualify (Sep 2026): https://www.bushletter.com/google-voids-ad-credits-after-businesses-spend-to-qualify/
- Alexandria Today, Google Ads AU terms reproduction: https://alexandriatoday.com.au/google-ads-tcs
- All Marketing (Perth), Google Ads promo eligibility (2026): https://www.allmarketing.com.au/google-ads-promo-eligibility/
- Overt Digital, Google Ads credit tiers in Australia (Feb 2026): https://overtdigitalmarketing.com.au/understanding-google-ads-credits-tiers-in-australia/
- Online Road, Claim your $600 Google Ads credit (2026): https://onlineroad.com.au/blog/boost-your-business-with-google-ads-and-claim-a-600-credit/
- ppcnewsfeed, 2x ads credit for new accounts (May 2026): https://ppcnewsfeed.com/ppc-news/2026-05/get-2-ads-credit-new-google-ads-accounts/
- almcorp, Google Partners promotional offers 2026: https://almcorp.com/blog/google-partners-promotional-offers/
- Rankite, Google Ads suspended (2026): https://rankite.com/blog/google-ads-suspended
- Sendwin, Suspended for circumventing systems: https://blog.send.win/google-ads-suspended-for-circumventing-systems-what-to-do-next/
- Kampaio, Why is my Google Ads account suspended: https://www.kampaio.com/blog/why-is-my-google-ads-account-suspended
- BlueTuskr, Connect Shopify with Google Ads: https://blog.bluetuskr.com/how-to/connect-shopify-google-ads
- Doublebricks, How to claim the Google Ads offer: https://www.doublebricks.com/blog/google-ads-offer-a-step-by-step-guide
- Teamblind thread, Google takes advantage of small business: https://www.teamblind.com/post/google-takes-advantage-of-small-business-rjo7j6p0
- SEC filing, Google sales addendum (2015) defining New Advertiser: https://www.sec.gov/Archives/edgar/data/1297336/000143774915004966/ex10-33.htm
- Google Ads Australia coupon terms (fetch blocked, not read): https://www.google.com/intl/en_au/ads/coupons/terms/
