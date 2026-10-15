# Strategist review of the Endless Parks Google Ads launch plan

Reviewed 15 Oct 2026. Files read in full: `PLAN.md`, `00` to `09`, `05-keywords.csv`, `05-negatives.txt`, `RUNBOOK.md`, plus the phase 2 research `P1-budget-model.md` and `P2-shopping-mechanics.md` that the bids and thresholds derive from. Ten extended web searches were run on the claims I doubted; what they confirmed and what they could not is in section 7.

Short verdict: the structure (one Standard Shopping campaign at A$22, brand Search at A$3, non brand Search at A$5, Manual CPC, nothing else) is the right shape for A$30 a day and an A$87 hero product, the ladder thresholds match Google's published 15 in 30 days rule, and the credit sequencing is more careful than most agencies manage. The plan would still launch with four things that lose money or block execution: the negative keyword lists block the product's own best queries, the pre launch conversion check expects a status that cannot occur before the first paid click, the credit Step A adds a payments profile to the old account before it knows whether an offer exists (which can poison the fallback), and the feed title rewrite would change the storefront and the Meta catalogue that funds the business. Everything below is split into what would break results and what is nice to have.

---

## 1. Would break results or block execution (fix before launch)

### 1.1 Park names as negatives block the buyers the bottle exists for

`05-negatives.txt` lines 52 to 69 and 126 to 142, and `01-account-setup.md` Step 3.5 (which pastes the Shopping list to account level, so it hits every campaign). Seventeen park names (kakadu, uluru, blue mountains, royal national park, great barrier reef, ningaloo, karijini and so on) are broad negatives on both lists and at account level.

- A negative matches any query containing the term. "kakadu water bottle", "blue mountains water bottle", "great barrier reef gift", "ningaloo gifts", "royal national park gift" are exactly the long tail a bottle that maps those parks should win, and they are the queries most likely to convert because the searcher already has a park in mind.
- The stated reason ("so kakadu national park queries do not spend budget") does not hold for Search: every live keyword is exact or phrase and contains "bottle" or "gifts", so a query like "kakadu national park weather" cannot match any keyword in the first place. For Shopping, Google only shows product ads on queries with product intent, and the feed title already carries "Water Bottle"; a stray "kakadu national park" impression is a search terms fix on day 3, not a reason to pre block every park.
- Fix: remove all park names from both lists and from the account level list. Replace with intent negatives that cannot collide with the keywords: weather, closures, closure, accommodation, campground, camping ground, caravan park, map, maps, entry, fees, tour, tours, walks, trail, trails, directions, hotel, booking, bookings, "visitor centre", "things to do". Do not add "camping", "hiking" or "hike" anywhere in the non brand campaign: "camping gifts for dad", "gifts for hikers australia" and "hiking t shirt australia" are live keywords and would be blocked by their own negatives.

### 1.2 Broad "free" and "plastic" block "bpa free" and "plastic free" bottle queries

`05-negatives.txt` lines 7, 47, 72, 107. "free" as a broad negative blocks "bpa free water bottle", "plastic free water bottle", "leak free bottle", "free shipping water bottle australia". "plastic" blocks "plastic free". These are stainless bottle buyers. Fix: replace "free" with the phrase negatives "free printable", "free download", "free pdf", "for free", "free map", "free stickers"; replace "plastic" with the phrase negatives "plastic bottle" and "plastic water bottle". Keep "printable", "pdf", "template", "clipart", "svg", "png".

### 1.3 The pre launch conversion check expects a status that cannot occur, and the runbook then forbids launch

`02-conversion-tracking.md` Step 5.2 ("Within 24 hours ... Purchase as Recording conversions"), `06-launch-and-optimise.md` checklist item 2 ("status is Recording conversions after the test order"), `RUNBOOK.md` 5.9 and Failure handling ("No conversion recorded 72 hours after the test order ... Do not launch until it records").

A conversion is only recorded when Google can attribute it to an ad interaction. All three campaigns are paused until launch day, so the test order has no gclid and no conversion will be recorded, no matter how well the tag works. The status after a successful test is "No recent conversions" (tag detected, nothing attributed), with Diagnostics showing the tag as active. Written as it stands, the runbook's failure rule blocks launch indefinitely.

Fix: the pre launch pass line is (a) Tag Assistant shows one Google Ads conversion hit with transaction_id, value 15.00, currency AUD and user_data present, and one GA4 purchase, and (b) Goals > Conversions > Summary shows the Purchase action at "No recent conversions" or Diagnostics "Tag active", not "Unverified". "Recording conversions" and the enhanced conversions match rate (checklist item 3) are post launch checks after the first paid click order; move them to the day 7 read. Also update `02` Step 5.3: the enhanced conversions Diagnostics band needs attributed conversions and will not show before launch.

### 1.4 Launch checklist item 4 cannot be executed as written

`06-launch-and-optimise.md` checklist item 4: "A test click from a Google ad preview lands on the site with gclid". Ads shown in the Ad Preview and Diagnosis tool are not clickable, so there is no gclid to test. `RUNBOOK.md` already has the correct check at 7.6 (a real click from a phone on mobile data after launch) and 2.11 (manual URL with gclid=TEST before launch). Replace item 4 with those two and the URL suffix Test button (`02` Step 3.3).

### 1.5 Credit Step A adds a payments profile to the old account before knowing whether an offer exists

`00-new-account-and-credit.md` Step A, steps 4 and 5 in that order, and `RUNBOOK.md` 4.1 before 4.2. The plan's own "What kills it" row says reusing a payments profile that touched another Ads account invalidated a US$3,200 credit in September 2026. Step A step 4 creates a payments profile on the old account, and only then (step 5) looks for an offer. If none exists (the likely outcome, since Help 6388096 says the account must be under 14 days old at redemption and the old account is almost certainly older), the plan moves to Step B, a new account, where that freshly created profile is now a profile that "touched another Ads account". Step B's instruction to "use a card that was never on the old account" does not cover this: the invalidation trigger in the plan's own sources is the payments profile, not the card.

Fix: reorder Step A to look first, pay later. 1) Billing > Promotions and the Gmail search. 2) Campaigns > Change history for the creation date. 3) Only if an offer is listed on the Promotions page, or a code is in the inbox and the account is under 14 days old, add the payments profile and redeem. Otherwise do not touch billing on the old account at all; go straight to Step B and create a new payments profile (new profile, not just a new card) in the new account. Also: if the old account is older than 14 days and shows no offer, do not enter any code in it even to "see if it attaches"; an attached code that is later invalidated at the 35 day check is the worst outcome because the whole calendar is built around the credit landing on 21 Dec.

### 1.6 The internal contradiction on support chat

`00-new-account-and-credit.md` line 25 and `RUNBOOK.md` 4.2 say "Do not ask support for a code"; `00` sequence table row "20 to 22 Oct" says "code from the AU offer page or from Google Ads support chat". One of these is wrong; the sources say support cannot provide offers. Delete the support chat clause from the sequence table.

### 1.7 Turning off Merchant Center automatic item updates invites price mismatch disapprovals

`03-feed-fixes.md` Step 4.5 and `RUNBOOK.md` 3.3: "turn off automatic title and price improvements so Google does not rewrite the titles above". Automatic item updates (price, availability, condition) do not touch titles; they correct the feed from the landing page's structured data when the two disagree, which is the only thing standing between a Shopify sync lag and a "price mismatch" disapproval. The exposure is highest exactly where the plan needs Shopping most: BFCM (25 Nov to 1 Dec) when the sale price changes on the site, and any price edit in December. Keep automatic item updates on. Only switch off automatic title improvements if that toggle exists on screen (it may not; verify rather than hunt).

### 1.8 Rewriting the Shopify product title changes the storefront and the Meta catalogue

`03-feed-fixes.md` Step 2 sets the Shopify title to a 110 character feed title ("Australian National and Marine Parks Water Bottle 1.2L Insulated Stainless Steel, Straw Lid, Park Sticker Pack"). Shopify's title is the product page H1, the cart and order email line, the default SEO title, and the title Meta's catalogue ads use. Meta is the main channel at A$150 a day and runs Advantage+ catalogue ads from the same Shopify catalogue; a feed style title in a Meta catalogue card looks like a marketplace listing and will hurt the channel that pays for everything. `RUNBOOK.md` 2.2 lets the browser agent make this change without a JAKE marker.

Fix: leave the storefront title alone. Set the Google title in Merchant Center through a supplemental data source (Merchant Center > Data sources > Add supplemental source, keyed on the Shopify offer id, which looks like shopify_AU_<product_id>_<variant_id>) with a title column. A supplemental source overrides the Shopify sync and survives every resync, which is not true of the product editor the plan rightly warns against. If a supplemental source is not available for the Shopify sourced data, a shorter compromise title in Shopify ("Parks Bottle 1.2L, Australian National and Marine Parks Water Bottle") keeps the brand name first for Meta and still front loads the park words for Google. Either way mark 2.2 as JAKE approves.

### 1.9 Products must be enrolled in Shopping ads, not only free listings

Nothing in `03`, `04` or the runbook checks that the Shopify data source's Marketing methods (formerly Destinations) include Shopping ads. An account that has only ever used free listings can have products enrolled in free listings alone, and the campaign then shows every product as Not eligible with no obvious cause. Add to `RUNBOOK.md` Session 3: Merchant Center > Products > a bottle variant > Marketing methods shows Shopping ads and Free listings; if not, Shopify > Google & YouTube > Products or Merchant Center > Data sources > the Shopify source > Marketing methods > tick Shopping ads.

### 1.10 Brand negatives in the non brand campaign do not cover variants

`05-negatives.txt` lines 150 to 153 and `04-campaign-build.md` Campaign 3 step 6. Negative keywords do not take close variants (confirmed against Google's guidance, section 7). `"endless parks"` phrase does not block "endless park bottle" or "endlessparks"; `[endless park]` exact blocks only that two word query. Fix: phrase negatives "endless parks", "endless park", "endlessparks", "endlesspks", "ultimate adventure bottle", "parks bottle" in the non brand campaign.

### 1.11 A prose line inside the negatives file would be pasted as a keyword

`05-negatives.txt` line 125 (`"water bottle" is NOT a negative; ...`) sits inside the EP_Negatives_Search block without a `#`. A browser agent copying the block into the shared list pastes it as a negative, and a careless reader concludes "water bottle" is a negative. Prefix with `#` or move it to the header comment. Same file: the `##` section headers and the `# each state park name` comment also need stripping before paste; say so explicitly in the header.

### 1.12 BFCM has no ad copy, no swap procedure and no sale price mechanics

`07-calendar.md` rows 20 Nov and 25 Nov to 1 Dec say "sale language allowed in ads this week only" and "submit the Merchant Center promotion", but `05-ad-copy.md` has no sale RSA, nothing says whether the evergreen RSAs are paused or a second RSA is added, and nothing covers the feed. Ad review takes about a business day, so a sale ad written on 25 Nov serves on 26 Nov at best. Add: a BFCM RSA per ad group drafted now and saved paused (headlines and descriptions needing Jake's offer wording), submitted 22 Nov; evergreen RSAs stay live and the sale RSA is added beside them (Google rotates), then removed 2 Dec; the sale price goes into Shopify as a compare at price so the channel syncs price and sale_price and Shopping shows the strike through, which also keeps the feed price matching the page without a manual edit.

### 1.13 The brand pause in January collides with the PMax experiment

`07-calendar.md` 5 Jan ("pause the brand campaign 5 to 18 Jan") and 12 Jan ("start the PMax versus Shopping experiment"); `08-pmax-experiment.md` gate 4 ("brand campaign live on exact match, so brand queries have an owner") and kill criterion day 7 ("brand queries exceed 5 per cent of PMax clicks"). If the experiment starts on 12 Jan the brand campaign is paused for its first week, gate 4 is failed by the plan's own calendar, and the first brand leakage read is meaningless. Pick one: run the brand on and off test 5 to 18 Jan and start the experiment Monday 19 Jan (ending 2 Mar), or run the brand test in March after the experiment. The first is better: the credit funds January either way.

### 1.14 Customer Match timing is stated two ways

`02-conversion-tracking.md` Step 4.5: "Later, not at launch: Customer Match from Shopify". `09-audiences.md` and `RUNBOOK.md` 5.10: connect the Shopify customer lists on the build days and exclude `EP purchasers` from non brand at launch. The runbook follows `09`; update `02` so a reader of only that file does not skip it.

---

## 2. Correctness and currency of specific claims

| Claim in the plan | Status | Note |
|---|---|---|
| Enhanced CPC no longer exists for Shopping (`04` Campaign 1 step 3) | Correct | Retired from Shopping October 2023, from Search and Display March 2025 |
| Target ROAS needs 15 conversions in 30 days, checked per Merchant Center ID for Shopping (`06` ladder, `P1` finding 8) | Correct | Google Help 6268637 and 6309035 still say 15 in 30. The "20 in 45 days" figure in some guides is outdated |
| Maximise conversion value with no target is available on Standard Shopping (`06` stage 3) | Correct, recent | Added in 2026. Note it has no ROAS floor and will spend the full budget; with Manual CPC already spending A$22, the practical change is small, but see 3.4 |
| "Maximise conversion value with a target ROAS" renamed "Target ROAS" in June 2026 (`06` stage 4) | Not verifiable from here | Harmless either way; the bidding screen will show whichever label is current |
| Channel prioritisation launched 14 Oct 2026, rolling out progressively, Display change February 2027 (`01` Step 3.6) | Correct | Announced 14 Oct, rollout from 15 Oct over "coming months". Cannot be set from a manager account; Editor and API support pending. The per campaign Networks boxes remain the control until the card appears |
| Automated promotions default on from 12 Oct 2026, switch at account level automated assets (`01` Step 3.2) | Correct | Eligibility needs location assets and no promotion assets, so this account is probably not even eligible; switching it off is still right |
| AI Max pre selected on every new Search campaign (`04` Campaign 2 step 3) | Single source, plausible | September 2026 migration covered campaigns with legacy broad match or automatically created assets. Opt out path (Settings > AI Max) is confirmed. Keep the instruction as "confirm on screen" |
| AI Max for Shopping (`04` Campaign 1 step 6) | Opt in beta | Not a default; the "do not turn on" instruction is right and costs nothing |
| Customer Match lists need 100 users on Search since May 2025 (`09`) | Correct | Applies to Customer Match only; GA4 and tag based lists still need 1,000 for Search |
| Account level negatives (1,000 cap) apply to Search, Shopping and PMax search and shopping inventory (`01` Step 3.5) | Correct | They do not touch PMax Display, YouTube or Gmail |
| Negative keywords do not match close variants (`04` relies on this implicitly) | Correct | Hence 1.10 |
| Google product categories 3809 Water Bottles, 212 Shirts & Tops, 2169 Mugs (`03`) | Correct | |
| Shopify channel sends subtotal, GST inclusive, shipping excluded (`02`, `PLAN`) | Mostly supported, conflicting reports | Help 16031492 says subtotalPrice; 2025 EU reports show tax inclusive totals. With GST inclusive pricing both read 87.00. The test order settles shipping; keep that step |
| Enhanced conversions toggle inside the Shopify channel (`02` Step 1.3) | Sources disagree on location | Some put it in the channel settings, some in Google Ads customer data terms. The plan's fallback ("carry on and confirm user_data in Tag Assistant") is right |
| New advertiser credit: account under 14 days old at redemption, spend within 60 days, credit expires 60 days after it is applied, up to 35 days to land (`00`) | Consistent with every source found | The A$600 for A$600 Australian tier is not confirmed by any Google page found; agency pages quote A$540 and A$600 tiers. "Screen on creation day is the truth" is the right posture |
| Attribution menu offers only Data driven or Last click (`02` Step 2.2) | Correct | |
| Campaign priority only matters with two Shopping campaigns (`04`) | Correct | But `04` says leave Low and `RUNBOOK` 6.1 says Medium; harmless now, fix for consistency |
| "Local products" setting (`04` Campaign 1 step 6) | Removed August 2026 per `P2` | Tell the agent not to look for it; Inventory filter stays off |
| Old A$58 and A$63 pages cause Merchant Center price mismatch (`03` Step 8, `06` item 12, `PLAN`) | Overstated | Merchant Center compares the feed's own link (the PDP with ?variant=) against the feed price; a stale marketing page is not checked. Still redirect it for brand consistency and because a Search ad could never land there, but it is not a launch blocker |

---

## 3. Strategy: structure, budgets, bids, ladder

### 3.1 Structure (keep)

Three campaigns, 73 / 10 / 17 split, Standard Shopping on Manual CPC, no PMax, no partners, no Display: correct for A$30 a day with one hero product and a new account. Keeping brand separate as a measurement line with a January on and off test is better practice than most agencies apply. Standard Shopping over feed only PMax is right at this budget for the reasons `08` gives (brand leakage, no channel control, no search terms).

### 3.2 Non brand Search is too wide for A$5 a day (nice to have, but worth doing before launch)

At A$5 a day and about A$0.85 a click the campaign gets roughly 5 clicks a day across 32 enabled keywords in two ad groups (15 bottle, 17 gift). No keyword will reach a readable sample inside 30 days and the day 14 instruction "raise the best 5 keywords by 20 per cent" has nothing to act on. The gift group is also the weakest fit for a bottle: "4wd gifts", "gifts for 4wd lovers", "caravan gifts" and "australian made gifts" (exact, A$0.80) are broad intent queries where BCF, Anaconda and Kmart show, and Keyword Planner will put most of them at A$2 or more, so a A$1 cap buys low impression share and the worst remaining auctions.

Recommendation: launch non brand with the bottle cluster only (the nine park and sticker keywords plus "road trip water bottle"), hold `gifts_outdoors` paused until 15 Nov when the seasonal keywords switch on and the credit threshold is in sight, and trim the gift list to the six with a plausible bottle fit (gifts for grey nomads, grey nomad gifts, gifts for road trippers, road trip gifts, national parks gifts, gifts for hikers australia). Move "4wd gifts", "gifts for 4wd lovers", "caravan gifts" and "australian made gifts" to a paused test with the same 150 clicks no sale rule as tees. If Jake wants gifts live from day one, fund it: non brand to A$8 and Shopping to A$19 for the first two weeks, then back.

### 3.3 Bids (keep, two notes)

Bottle A$1.10 (a 2 per cent conversion rate bet for 14 days of impression share), tees A$0.40, brand A$0.50, non brand cap A$1.00: all defensible and internally consistent with `P1`. Two notes:

- The day 7 rule in `06` ("lost IS rank above 70 per cent, raise to A$1.30") and the ladder's week 3 rule ("CPC under A$1 and lost IS rank above 60 per cent, go to A$1.30") use different thresholds for the same action. Pick 60 and say it once.
- `P2` still carries tees at A$0.60 and Target ROAS 190; the plan files all say A$0.40 and 200. The plan files are the ones that execute, so this only matters if someone reads `P2` as the spec.

### 3.4 Ladder (keep, one caution)

Stage 3 at 15 conversions on the Shopping campaign itself, then Target ROAS 200 at 30 and two weeks later, with a refusal of Google's account level prompt: correct and more conservative than Google's own rule. One caution now that Maximise conversion value without a target exists on Standard Shopping: it has no ROAS floor and spends the whole budget on whatever converts cheapest, which on this account means two bottle colours and the tees. At 15 conversions the safer two step is Target ROAS set at the trailing 30 day observed ROAS minus about 15 per cent (so if Shopping is at 1.7, type 145), then raise toward 200 every two weeks. Google's "set it near your actual ROAS" guidance supports this and it avoids a fortnight of unconstrained spend at the moment the account is just becoming readable. Either path is acceptable; the no target step is not wrong, just looser.

### 3.5 Mugs have three different triggers

`06` Month 3 ("once the bottle group is on Smart Bidding and Christmas gift searches start, about 20 Nov", which is impossible in the base case where Smart Bidding is February), `07` 2 to 15 Dec ("if bottle CPA is under A$50") and `07` 31 Jan ("Month 3 plan: mugs in Shopping"). Pick one rule: add mugs as their own product group at A$0.70 from 20 Nov if Shopping CPA on the last 30 days is under A$60, regardless of bid strategy; remove 24 Dec. Mugs at A$45 are the natural gift price point and the 20 Nov to 15 Dec window is when they would work.

### 3.6 Expectation setting (keep)

The three case table and the explicit "Manual CPC for the quarter is the plan, not a failure" line are the most useful sentences in the plan. Add one: Google can spend up to twice the daily budget on any day, so the day 1 and 2 check "A$25 to A$35" should read "A$20 to A$60 on any day, A$25 to A$35 on average over the first week".

---

## 4. Keywords: what converts, what burns

### 4.1 Brand (add four)

Missing: `[ultimate adventure bottle]` and `"ultimate adventure bottle"` (the product's actual name on the PDP, in 99 reviews and in the URL), `[parks bottle]`, `[the parks bottle]`. Anyone who saw a Meta ad and remembers the product name rather than the brand name searches these.

### 4.2 Bottle cluster (keep, with negatives)

"national parks water bottle" and its variants are the right core: nobody Australian competes, CPCs will be low, intent is high. Three keywords need protection or a short leash:

- `"parks water bottle"` phrase will match "parks project water bottle" (US brand that owns the national parks bottle category on Amazon), "south park water bottle", "parks and rec water bottle", "jurassic park water bottle", "water park bottle". Add negatives: parks project, south park, parks and rec, parks and recreation, jurassic, theme park, water park.
- `"adventure water bottle"` phrase will match "adventure time water bottle" (cartoon) and risks "adventure quencher" (Stanley's product name; "stanley" is a negative but "adventure quencher 40oz" is not). Add negatives: adventure time, quencher.
- `"sticker water bottle"` phrase and `[water bottle with stickers]` are mostly people wanting sticker packs for a bottle they already own. Keep `[water bottle with stickers]` at A$0.60 as a test with the 100 clicks no sale rule; drop `"sticker water bottle"` phrase or add it to the paused test group.

Add negatives for the US and Canadian park ecosystem beyond the four listed: zion, grand canyon, banff, parks canada, nps, pendleton. Add the brands missing from both lists: owala, hydrapeak, thermos, klean kanteen, contigo, sigg, cheeki, montiico, bbox, sttoke, ever eco. Add replacement part queries: replacement, spare, parts, "lid only", "straw only".

### 4.3 Tees (hold, then tighten)

Pausing until 17 Nov is right. When enabled: `"australian made t shirts"` phrase and `[australian made clothing]` will pull blank, plain, printing, custom, supplier, manufacturer and wholesale queries from print on demand buyers. Add to the tees ad group negatives: blank, plain, printing, print, custom, supplier, manufacturer, bulk, wholesale, "for printing". Keep the 150 clicks no sale rule.

### 4.4 The paused generic group has no ad

`04-campaign-build.md` Campaign 3 lists ads for three ad groups; `bottle_generic_test` (three keywords in the CSV) has none. If it is ever enabled it serves nothing. Assign the Bottle RSA to it now.

### 4.5 Negatives lists are inconsistent with each other

The Shopping list carries kathmandu, macpac, anaconda, bcf; the Search list does not, although the gift keywords are where those retailers compete. The Search list carries cheap, cheapest, wholesale, bulk, amazon, ebay, temu; the Shopping list does not, although "cheap water bottle" is the query where an A$87 bottle loses on sight. Add each set to the other list. Also "flask" in the bottle ad group negatives: in Australian usage a flask is an insulated bottle ("national parks flask", "hiking flask"); remove it.

---

## 5. Conversion tracking, feed, credit: remaining notes

### 5.1 Tracking (sound apart from 1.3 and 1.4)

One source, Primary and Secondary set correctly, Data driven, Count Every, enhanced conversions, auto tagging, account level suffix, redirect checks: this is the right setup and the "one purchase source" rule prevents the most common Shopify double count. Three small notes:

- The test order is refunded in Shopify but the Tag Assistant hit is still a real tag event; that is fine and the refund does not need to reach Google.
- `tw_kwdid={targetid}` and `gadid={creative}` as Triple Whale parameters could not be verified; Triple Whale's own Google template is the reference. If Triple Whale's integration page offers its own parameter string, prefer theirs for those two keys and keep the six UTM keys as written.
- Weekly report "Impr. (Abs. Top) %" is a Search metric; on the Shopping row it reads blank. Harmless.

### 5.2 Feed (sound apart from 1.7, 1.8, 1.9)

Custom product Yes, vendor as brand, apparel attributes, manual shipping in Merchant Center, product ratings via Judge.me API feed, promotions only for BFCM, images without text: all right. The custom label fallback to product type is the right hedge given `P2`'s low confidence that the Shopify bulk editor exposes custom labels. Note for later: "Everything else: Excluded" means any new product (a fifth tee) is excluded from paid until its label or product type is set; add that to the monthly routine.

### 5.3 Credit (sound apart from 1.5 and 1.6)

The terms table in `00` matches every source found (14 days, 60 day spend window, 35 day verification, 60 day credit expiry, taxes excluded, monthly invoicing and payments profile changes as invalidation triggers). The threshold timing holds: brand underspends so real spend is about A$28 a day, A$600 lands around 18 Nov, inside a window that closes about 20 Dec. Two refinements:

- Default to Step B. The old account is almost certainly older than 14 days; Step A succeeds only if an offer is already on its Promotions page. Write Step A as a five minute look, not a half day of setup.
- The plan assumes the credit lands 21 Dec. If the threshold is met 18 Nov, "typically within 35 days" is 23 Dec at the latest; the calendar's 21 Dec row should say "by 23 Dec, chase on 24 Dec".

---

## 6. Nice to have

- Two Shopping ad groups (bottle, tees) instead of one, so ad group negatives can differ ("shirt", "tee" on the bottle group; "bottle" on the tees group) and search terms read cleanly per product. Same campaign, same budget.
- Sitelink "Reviews" uses an anchor on the PDP, which is the same URL as the "The Parks Bottle" sitelink and the ad's final URL; Google rejects duplicate sitelink destinations. Point it at a reviews page or drop it.
- Image assets: the "not eligible until about 60 days" note may be stale; upload them and see.
- Brand campaign inherits the Search list, so "endless parks free shipping" and "endless parks pdf" are blocked. Acceptable, but after 1.2 the "free" block disappears anyway.
- `01` Step 3.11 automated rule "ad group cost over A$40 and 0 conversions in 14 days" will fire on the tees group by design; fine, but say so or the email becomes noise.
- The `EP weekly` column set is defined in `02` and again in `04` with fewer columns; keep one definition.
- `05-keywords.csv` status values ("enabled", "paused", "paused until 17 Nov", "enable 15 Nov") need a one line mapping in the header: anything not "enabled" is created paused, with the label in the note.
- `07` 8 Dec callout "Order by 16 Dec for Christmas delivery" is right for east coast metro from Perth; add "Express available" to the same callout so WA and Express buyers are not scared off.
- After the January brand test, if brand is cut to A$1, move the A$2 to Shopping, not non brand; Shopping is the campaign with the readable CPA.

---

## 7. What the searches confirmed and could not

Confirmed (Google Help plus trade coverage): Target ROAS 15 conversions in 30 days for Search and Shopping, per Merchant Center ID for Shopping (Help 6268637, 6309035); Maximise conversion value without a target now selectable on Standard Shopping; Enhanced CPC gone from Shopping since October 2023; Channel prioritisation announced 14 Oct 2026 with progressive rollout and the February 2027 Display change; Automated promotions default on from 12 Oct 2026 with an account level switch; Customer Match Search minimum 100 users since May 2025; account level negatives apply to Search and Shopping inventory including PMax; negative keywords do not match close variants; taxonomy IDs 3809, 212, 2169; new advertiser offer terms (14 days, 60 days, 35 day verification, 60 day expiry).

Not confirmable from here: the Australian tier amounts (agency pages quote A$540 and A$600); the June 2026 bid strategy relabel; AI Max being pre selected on new Search campaigns (one source); where the Shopify channel's enhanced conversions toggle lives (sources disagree); whether the Shopify channel's value is subtotal or tax inclusive total in October 2026 (irrelevant for GST inclusive prices, the test order settles shipping); Judge.me plan tier requirement; Google Ads Editor version cutoff; the Triple Whale parameter names.

Sources used: Google Ads Help 6268637, 6309035, 11396330, 18385152, 15329625, 7474166; Search Engine Land (eCPC deprecation; Customer Match 100 users); Search Engine Journal, PPC Land, MediaPost, Search Engine Roundtable (channel prioritisation, 14 to 15 Oct 2026); PPC Land and Relevant Audience (automated promotions, 12 Oct 2026); Stackmatix and WordStream (eCPC timeline); Techwyse and Gromerce (Maximise conversion value on Standard Shopping); Shopify Community and FeedArmy (channel conversion value); Merchant Center Help 16031492; productcategory.net (taxonomy IDs); Overt Digital, Online Road, Eleven54 (Australian credit terms, secondary).

---

## 8. Ambiguities a Chrome agent could not resolve alone

1. The pre launch conversion status to expect (section 1.3): as written, the agent waits for "Recording conversions" that never comes.
2. The "test click from a Google ad preview" (1.4): not possible; needs the replacement steps.
3. `05-negatives.txt` has prose and headers inside the paste blocks (1.11); the agent needs an explicit "paste only lines without # or ##, and not line 125".
4. Whether the Shopify Google & YouTube bulk editor shows Custom label 0 and Custom product columns; the fallback is written but the agent needs to know to try product type immediately rather than wait 48 hours.
5. Whether "Automatic title improvements" exists as a Merchant Center toggle; the agent should not turn off automatic item updates while looking for it (1.7).
6. The Shopify title change (1.8) is a storefront and Meta catalogue change with no JAKE marker.
7. Credit Step A ordering (1.5): the agent would add a payments profile before looking for the offer.
8. `04` tells the agent to switch off "Local products", which no longer exists; the agent should skip it.
9. `bottle_generic_test` has keywords but no ad; the agent cannot build the ad group completely (4.4).
10. Which RSA headlines to pin when two are marked "pin position 1": both are pinned to position 1 and Google rotates them; the agent should not pick one.
11. The CSV status values need a mapping to Enabled or Paused plus label (section 6).
12. The test order needs a real card, the specific A$15 sticker product handle, and a refund in Shopify (JAKE in the runbook already, but the product is not named).
13. Merchant Center Marketing methods check (1.9) is absent, so the agent has no step to run if products show Not eligible for an unexplained reason.
14. January: brand paused or live on 12 Jan (1.13) decides whether the agent builds the PMax experiment that week.
