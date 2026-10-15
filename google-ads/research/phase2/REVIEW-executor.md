# Executability review of the Google Ads launch plan

Reviewer lens: could Claude in Chrome, with Jake watching, execute each numbered step using only what is written? Files read: PLAN.md, RUNBOOK.md, 00 to 09, 05-keywords.csv, 05-negatives.txt, plus research/R00-brief-and-decisions.md for Jake's rules. Mechanical checks run: every headline, description, sitelink, callout and snippet counted; CSV parsed; weekdays computed; em dash and US spelling scans.

What passed: all 60 headlines are 30 characters or under, all 16 descriptions 90 or under, sitelink names and lines inside 25/35, callouts inside 25. No em dashes anywhere. No US spelling except the deliberate negative keyword "personalized". CSV has 8 columns on every row, no duplicate keyword and match type pairs, all CPCs numeric. 27 Oct 2026 is a Tuesday as stated. Australia Post weekdays in 07 are right.

## A. Blocking issues (would break execution, lose the credit, or violate a rule)

### A1. 05-negatives.txt, EP_Negatives_Search, line 125: a prose line that an agent will paste as a phrase negative
Line 125 reads `"water bottle" is NOT a negative; the park qualified bottle queries are the point. ...` with no `#` prefix, inside the list block. The file header says `#` marks comments and quotes mark phrase negatives. An agent copying the block, or parsing line by line, adds `"water bottle"` as a phrase negative to both Search campaigns and to the account level list, which blocks every bottle keyword in the plan. Fix: prefix the line with `#`.

### A2. 05-ad-copy.md, Bottle ad, headline 1: "National Parks Water Bottle" pinned to position 1 breaks the "National and Marine Parks" rule
PLAN.md and the brief say never "national parks" alone. This headline is pinned to position 1 so it shows on every impression of the non brand bottle ad. The keyword can stay (keywords are not copy); the headline cannot. Replace with "National and Marine Parks Bottle" (31, too long) or "Nat and Marine Parks Bottle" (27) or "Australia's Parks Bottle 1.2L" as the only pin 1.

### A3. 05-ad-copy.md, Tees ad: display path "aussie-made-tees" is 16 characters, limit is 15 per path field
Google rejects it. Use path 1 "aussie-made" and path 2 "tees".

### A4. 05-ad-copy.md, Sitelinks: the Reviews sitelink has no URL
"Reviews: product page reviews anchor" is not a URL. Every sitelink needs a final URL. Give the actual anchor, for example https://www.endlessparks.com/products/ultimate-adventure-bottle#judgeme_product_reviews (confirm the anchor id on the live page), or drop the sitelink.

### A5. 05-ad-copy.md, Price asset: required fields missing and the type does not exist
A price asset needs a type (Brands, Events, Locations, Neighbourhoods, Product categories, Product tiers, Services, Service categories, Service tiers; "Products" is not one), a price qualifier (From, Up to, Average), and for each item a header (25), a description (25), a price, a currency and a final URL. The plan gives four headers and prices only. The agent cannot complete the form. Provide: type Product tiers, qualifier none except "From" on the sticker bundle, and per item description plus URL (bottle /products/ultimate-adventure-bottle, mug /collections/adventure-mugs, tee /pages/drop-01, stickers /collections/aus-park-stickers).

### A6. 00-new-account-and-credit.md Step A and RUNBOOK.md Session 4: billing is added before anyone checks whether an offer exists, which burns the card the Step B fallback needs
Step A.4 adds a payments profile and card to the existing account; A.5 then looks for an offer on Billing > Promotions or in Gmail; if none, Step B says create a new account "with a card that was never on the old account's payments profile". RUNBOOK 4.1 (billing) precedes 4.2 (promotions) the same way. Seeing whether an offer is listed needs no payment method. If A.5 fails after A.4, Jake's business card is already attached to the old account and 00's own table says a reused payments profile invalidated a credit in September 2026. Reorder: check Promotions page and inbox first (Session 1.5 and 1.9 already do this on 16 Oct); add billing to the existing account only if an offer is present; otherwise go straight to Step B with the untouched card.

### A7. 00-new-account-and-credit.md, "The sequence" table, 20 to 22 Oct row: contradicts Step A.5 and RUNBOOK 4.2
The row says attach the offer with a "code from the AU offer page or from Google Ads support chat". Step A.5, the Verified terms table and RUNBOOK 4.2 all say do not ask support (Help 2393021) and that the AU offer attaches at sign up, not by code. An agent following the table opens a support chat the plan forbids. Rewrite the row to match Step A.

### A8. 00 Step B and 01 Step 2: no instruction for creating a second account under a login that already has one
ads.google.com "Start now" while signed in as endlesspks@gmail.com opens the existing account, not the sign up flow. The agent needs the explicit route: profile picture > account picker > New Google Ads account (or ads.google.com/nav/selectaccount > plus), then Expert Mode and "Create an account without a campaign". Also state whether the AU offer still attaches on that route, since the offer page CTA may not be what the picker uses.

### A9. RUNBOOK.md 6.1 vs 04-campaign-build.md Campaign 1 step 3: Shopping campaign priority Medium vs Low
Two different instructions for the same field. 04 says leave Low (correct, it only matters with a second Shopping campaign). Change 6.1 to Low.

### A10. 06-launch-and-optimise.md "Days 1 to 14: do not touch bids" contains a Day 7 bid change
The heading says no bid changes for 14 days; the Day 7 bullet says raise the bottle bid to A$1.30 if lost IS (rank) is above 70 per cent. The ladder then has a different threshold (week 3, 60 per cent). Pick one: either the Day 7 rule exists (and the heading is wrong) or it moves to Day 14.

### A11. Launch gate on "limited performance" cannot be passed as written
06 checklist item 1 requires "No 'limited performance' warnings" on bottle and tees; 04 step 12 and RUNBOOK 7.1 require "Eligible, not Eligible (limited)". 03 Step 1 says to expect "limited performance" to remain on bottles and tees after setting Custom product = Yes and that they still serve. If 03 is right, the launch checklist fails forever. Decide which is true and align: the usual outcome after identifier_exists = no is that the GTIN warning clears; if a warning for another reason remains, the gate should read "no limited performance warning whose cause is not the missing GTIN".

### A12. Pre launch conversion gate "Recording conversions" is unreachable before an ad click
02 Step 5.2, RUNBOOK 5.9, 06 checklist item 2 and RUNBOOK Failure handling ("Do not launch until it records") all require the Purchase action status Recording conversions after the test order. Google Ads only records a conversion that follows an ad interaction; a Tag Assistant test purchase with no gclid verifies the tag (status moves from Unverified to No recent conversions, Diagnostics shows tag Active) but does not record a conversion. The gate as written blocks launch indefinitely. Change the pre launch pass to: Tag Assistant shows the single Google Ads conversion hit with value and user_data, and Diagnostics shows tag Active and Enhanced conversions set up; "Recording conversions" is the check after the first real ad click order (RUNBOOK 7.7 or weekly).

### A13. Christmas keywords: three versions across CSV, 06 and 07, and no instruction to pause them at build
05-keywords.csv puts four "christmas gifts for ..." phrase keywords inside gifts_outdoors with status "enable 15 Nov". 06 "Month 3 and beyond" says "Consider a Christmas gift ad group in non-brand Search from 15 Nov" with "gifts for campers" and "gifts for hikers" (both already launch keywords in gifts_outdoors). 07 says 17 Nov "Add the Christmas gift ad group to non-brand Search". Pick one structure and one date. Separately, 04 Campaign 3 and RUNBOOK 6.5 never tell the builder to add those four keywords paused; an agent adds them enabled and they run from 27 Oct.

### A14. bottle_generic_test ad group exists in the CSV, RUNBOOK 6.5 and 06 but not in 04, and has no ad in 05
04 Campaign 3 step 2 lists only bottle_nationalparks, gifts_outdoors and tees_aussiemade; 01 naming conventions also omit it. 05-ad-copy.md has no ad for it, so when 06 says enable it in week 3 the group has keywords and no ad and cannot serve. Add it to 04 (built paused) and state which ad it uses (the Bottle ad is the obvious choice).

### A15. 03-feed-fixes.md tee description contains a literal placeholder and unknown values; RUNBOOK 2.3 cannot be completed
The pattern reads "<Fabric and weight once confirmed>", "Colour per variant: the actual tee colour", "Material: Cotton (confirm)". An agent either pastes the angle bracket text into the live storefront or stops. Give a description that stands without the fabric line, and mark 2.3 JAKE for colours, fabric and weight (open question 9).

### A16. 07-calendar.md 8 Dec and 17 Dec: Christmas callout and sitelink lines exceed the limits
"Order by 16 Dec for Christmas delivery" is 38 characters; "Express Post for Christmas, order by 20 Dec" is 43. Callouts allow 25, sitelink description lines 35. Replace with, for example, callout "Order by 16 Dec for Xmas" (24) and sitelink lines "Order by 16 Dec for Christmas" (29) / "Express Post by 20 Dec" (22).

### A17. Customer Match timing: 02 says later, 09 and RUNBOOK say before launch
02 Step 4.5: "Later, not at launch: Customer Match from Shopify". 09 step 6 and RUNBOOK 5.10 do it in Session 5 before launch, and 09 "At launch" excludes EP purchasers on non brand Search, which needs the list. Align 02 with 09.

### A18. 07 brand pause test (5 to 18 Jan) overlaps the PMax experiment (from 12 Jan) that 08 gate 4 says needs the brand campaign live
08 gate 4: brand campaign live on exact match. 07 pauses it 5 to 18 Jan and starts the experiment 12 Jan. The PMax arm also changes Shopping traffic, which contaminates the Search Console brand read. Move the brand test to 19 Jan to 1 Feb, or run it in December, or start the experiment 19 Jan.

### A19. PMax gate differs between 06, 08 and PLAN
06 "Month 3": PMax "only if Shopping is at Stage 4 of the ladder" (30 conversions and Target ROAS). 08 gates: Shopping CPA inside A$39 to A$50 over weeks 5 to 8 and 20 account conversions in 30 days, no Stage 4. PLAN: "only after 8 weeks if Shopping holds a CPA inside A$39 to A$50". On 29 Dec the agent has three different tests. Make 08 the single source and point 06 and PLAN at it.

### A20. 08 and 07: "Monday 12 Jan 2027" is a Tuesday
12 Jan 2027 is a Tuesday. 08 says "Experiment (Monday 12 Jan to 22 Feb 2027)"; 07 says 12 Jan. The Monday is 11 Jan. Six weeks from 12 Jan is 23 Feb, not 22 Feb. Also 00 and 07 say credit worst case expiry "about 17 Feb" (21 Dec plus 60 days is 19 Feb); harmless but inconsistent.

### A21. Merchant Center link direction: 01 Step 4 vs RUNBOOK 4.12 and 4.13
01 initiates from Merchant Center (Settings > Apps and services > Add service > Google Ads > customer ID) then approves in Google Ads. RUNBOOK 4.12 initiates from Google Ads Admin > Linked accounts and 4.13 only confirms in Merchant Center. The current Merchant Center flow is the one 01 describes; Google Ads often cannot initiate. Make 4.12 the Merchant Center step and 4.13 the Google Ads approval.

### A22. Scripts step is not executable: no code, no source URL, needs Jake's authorisation, not marked JAKE
01 Step 3.12 and RUNBOOK 4.11 name "Nils Rooijmans' disapproved ads alert", "disapproved products alert" and "Cypress North or Acuto pacing script" with no URL or code, and the cloud session could not fetch them. Google Ads Scripts also require the signed in user to authorise each script, which is Jake's hand. Either paste the script code into the plan (with the alert email filled in) or mark 4.11 JAKE and defer it to week 2.

### A23. RUNBOOK 4.14 Step B path: the Shopify channel may already hold the old Ads account
The brief says Jake believes an Ads account is linked into Shopify. If Step B created a new account, 4.14 "Connect this customer id" must first disconnect the old account inside Google & YouTube > Settings > Google Ads (without uninstalling the app, which 02 forbids). The runbook does not say so, and the agent is told never to uninstall, so it stalls.

### A24. Tee Search bids contradict the tee economics in PLAN.md
PLAN line 29: tee break even CPA about A$31 to A$36, "Tee max CPC A$0.40 (1.2 per cent conversion rate times a A$30 allowed CPA)". 05-keywords.csv tees_aussiemade bids are A$0.60 to A$1.00; at 1.2 per cent a A$1.00 click is a A$83 CPA. Either the CSV bids drop to about A$0.40 to A$0.50 or PLAN states that the A$0.40 applies to Shopping only and accepts the Search loss as a test.

## B. Steps that need information Jake has not provided (agent stops without it)

1. RUNBOOK 4.1 and 4.7, 01 Step 2.5: legal entity name, ABN, GST registration (open questions 1 and 11). JAKE marked, but nothing else in Session 4 can proceed on the Step B path without 4.1, and Step B needs a card never used on any Google Ads account.
2. RUNBOOK 2.3, 03 Step 2 tees: colours per design, fabric, weight, SKUs (open question 9; see A15).
3. 03 Step 5 and RUNBOOK 2.13: whether every variant has a SKU in Shopify (Judge.me matches on brand plus SKU with no GTIN). No runbook step checks or sets SKUs.
4. RUNBOOK 3.1 and 03 Step 4.4: the phone number and customer service email to enter in Merchant Center Business information. Not in any file.
5. RUNBOOK 2.16 and 09 step 3: the privacy policy sentence is described, not written. Provide the exact sentence and the opt out email address so JAKE only approves.
6. 05 assets: logo files (1:1 and 4:1) and 4 to 6 image assets. No file locations. RUNBOOK 6.4 and 6.5 say "image assets" as if they exist.
7. 05 "Free Shipping Over $120" (open question 8): it is in one headline and one description of all four ads and in a callout. If Jake says no, nine lines need replacements that the plan does not supply. Give fallback lines now.
8. RUNBOOK 2.10: "if that page is stale" is Jake's call (open question 3). The agent cannot judge whether /pages/adventurebottle is stale or in use by Meta ads.
9. 07 20 Nov and 25 Nov, 03 Step 6: the BFCM offer (type, amount, code, title) and the BFCM ad copy are not defined anywhere; "Pause evergreen ads that would clash with sale creative" has no list of which ads or what replaces them.
10. RUNBOOK 6.9 and 09: the EP purchasers exclusion on non brand Search is "Jake's call" and unresolved.
11. 01 Step 3.11 and 3.12, RUNBOOK 4.10 and 4.11: the email address for rules and script alerts.
12. 09 step 2 and 02 Step 4.4: the wholesale tag must already be on every stockist customer and every wholesale order; nobody has confirmed it is.
13. 02 Step 4.2: Search Console link needs Owner; whether endlesspks@gmail.com is an Owner is unknown.
14. 03 Step 2 and RUNBOOK 2.2: changing the bottle title to the 110 character feed title changes the storefront H1 and SEO title. 03 itself says to check whether the channel exposes a feed title column; the Shopify Google & YouTube bulk editor does not, so this is a storefront change Jake must approve. Same for the four tee titles.
15. RUNBOOK 2.12: publishing the Balcatta warehouse address on a contact page is a business decision.
16. 08 step 4: an Endless Parks YouTube channel is assumed to exist (January, not blocking now).

## C. Ambiguities for an agent driving Chrome

1. 05-ad-copy.md intro says pin "one product headline to position 1" and "description 1 to position 1"; every ad pins two headlines to position 1 and no description carries a pin mark. The agent cannot tell which instruction wins.
2. 04 Campaign 1 step 5 and RUNBOOK Session 6 preamble ask for "Languages English" on the Shopping campaign. Standard Shopping has no language setting; the agent will search for a field that does not exist.
3. 03 tees title: the Bluff Knoll exception in brackets does not show the complete title. Write all four titles out in full.
4. RUNBOOK 6.6 and 04 "After all three are built": Keyword Planner volumes are read after the keywords are already built, then "drop zero volume keywords". The dependency runs the other way. Also a new account with no spend sees ranges, not numbers, so "replace the estimated volumes with real numbers" (06 item 14) cannot be done literally.
5. 05-keywords.csv is not an import format and the match type column is a word, not Google notation. The agent types 52 keywords by hand. A paste ready block per ad group in bracket and quote notation would remove retyping errors.
6. RUNBOOK 4.12 "auto approves if endlesspks is admin on both" and 01 Step 4.2 "(some accounts: Tools > Data manager > Connected products)" give two locations; see A21.
7. 06 checklist item 4 asks for a test click from Ad Preview before launch; paused campaigns do not appear in Ad Preview and preview clicks are not real clicks. RUNBOOK 7.6 does it live after launch, which is right; delete the 06 version.
8. RUNBOOK 5.10 "Next day ... both above 100" versus 09 "24 to 48 hours". Say 48 hours so the check is not failed early.
9. RUNBOOK Session 3 is "17 to 19 Oct, after Session 2 has synced for 24 hours" while Session 2 runs "16 to 19 Oct". If Session 2 finishes on 19 Oct, Session 3 cannot. Give Session 2 a hard end of 18 Oct.
10. 09 at launch: audiences on a Standard Shopping campaign are added at ad group level in most accounts; RUNBOOK 6.9 says "Each campaign > Audiences". Say "campaign, or ad group for Shopping".
11. 00 Step A.5 and RUNBOOK 4.2: "search the endlesspks Gmail for a Google Ads promotional code" has no query string. Give one, for example `from:(ads-noreply@google.com OR googleads-noreply@google.com) (promo OR promotional OR code OR credit)`.
12. Brand negatives for the non brand campaign: 04 step 6 lists two (`"endless parks"`, `[endless park]`), 05-negatives.txt lists three (adds `endlesspks`). Use the file as the source.
13. RUNBOOK 1.4 on an account that never had a campaign shows the first campaign builder, not a Campaigns table; tell the agent to close it and read Billing instead.
14. RUNBOOK 1.6: the plan says only a non AUD currency forces Step B. A non Perth time zone is also a one time change; say "change it once, then continue".
15. 04 Campaign 1 step 8 and RUNBOOK 6.2: if custom labels have not synced, the Product type fallback is "Water Bottle" and "T-Shirt"; the T-Shirt product type is set in Session 2 so it will exist, but lids share "3809" with the bottle in RUNBOOK 2.5 while 03 Step 3 gives lids their own product type "Lid". Confirm lids are excluded in the fallback tree (Product type "Lid" is not "Water Bottle", so yes, but say so).
16. 02 line 36 suffix uses `gadid={creative}` and `tw_kwdid={targetid}` as Triple Whale parameters. The plan could not verify them. Have Jake confirm the parameter names in Triple Whale's Google Ads integration help before 4.5, or the suffix spends a quarter mis-keyed.

## D. Improvements (not blocking)

1. 05-negatives.txt: "free" as a broad negative on Shopping and Search also blocks "bpa free water bottle" and "endless parks free shipping"; "plastic" blocks "plastic free water bottle". Use `"free printable"`, `"for free"` and keep "plastic" only in the tees group, or accept the loss and say so.
2. EP_Negatives_Shopping lacks usa, us national parks, yellowstone, yosemite, new zealand, national park service, which EP_Negatives_Search has. Shopping is where "yellowstone water bottle" would show the bottle.
3. Shopping list has "pass" (broad); Search list does not. Align.
4. 01 Step 3 hygiene (auto apply off, automated assets, rules, lists, brand list) does not start any credit clock and could be done 16 to 19 Oct in whichever account Session 1 identifies, freeing Session 4 for billing and the offer only. Only do this once Session 1.5 and 1.9 make the Step A versus B decision, so nothing is built in an account that gets abandoned.
5. Given the existing account was linked to Shopify some time ago and is almost certainly older than 14 days, Help 6388096's reading makes Step A's credit fragile at the 35 day check. Make the Step A versus B decision on 16 Oct from Session 1.7 (creation date) and 1.5 (Promotions page), not on 20 Oct.
6. PLAN line 28 says Target ROAS 2.0 "when Smart Bidding starts"; 06 ladder starts Smart Bidding with Maximise conversion value and no target, Target ROAS at 30 conversions. Say so in PLAN.
7. 03 Step 7 (images: plain background, no text, 800 by 800) has no runbook step. Add it to Session 2 with a check per variant main image.
8. RUNBOOK 3.2 return policy URL is /policies/refund-policy; write it.
9. RUNBOOK 4.15 exports an empty account; keep only the post build export in Session 6.
10. 06 item 5 "tax invoice emails on" has no path (Billing > Settings > Document delivery options, or the payments profile's email preferences). Give one.
11. Write BFCM RSA copy and the Merchant promotion fields now (title 60, promotion ID, dates 25 Nov to 1 Dec, percent off or code), so the 20 Nov step is paste and submit.
12. RUNBOOK 7.1a records a baseline in the launch session; 07 dates it 26 Oct and 06 lists it as a pre launch item. Put it in Session 6 so launch day is just enabling.
13. 05 headline "4.9 Stars From 99 Reviews" appears in all four ads, one sitelink line and one description; note the single place to update monthly and that Judge.me reads 4.89.
14. The Reviews sitelink and the review headlines depend on Judge.me stars being visible on the landing page; if the Judge.me widget is below the fold Google can still approve, but the count must match.
15. Add the lids Google product category explicitly in 03 Step 3 (RUNBOOK 2.5 reuses 3809 Water Bottles for lids, which is wrong for a lid; use the drinkware accessories path or leave the Shopify category to map).
16. 00 and 07: Session 1 already checks the Promotions page on 16 Oct; say in Step A that the 20 Oct check is a repeat, so the agent does not read a missing offer on 16 Oct as a Step A failure before billing exists.
