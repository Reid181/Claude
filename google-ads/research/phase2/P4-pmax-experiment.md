# P4: Performance Max experiment specification for month 3 (January 2027)

Written 15 Oct 2026 for Endless Parks. Builds on PLAN.md (Standard Shopping A$22 + Brand Search A$3 + Non-brand Search A$5) and R01 (PMax and Standard Shopping compete on Ad Rank; practitioner floor about 30 conversions in 30 days). One question: if Shopping reaches target by late December, how to test PMax against it without breaking what works. Direct page loads were blocked, so findings rest on search extracts; Google Help pages are undated and were read 15 Oct 2026. Confirm menu labels on screen.

## 1. Findings

1. **Asset minimums are official.** Headlines 3 to 15 at 30 characters (one 15 or under); long headlines 1 to 5 at 90; descriptions 2 to 5 at 90; one business name; square logo 1200x1200 required, 4:1 logo 1200x300 optional; landscape 1.91:1 at 1200x628 (min 600x314) required; square 1200x1200 (min 300x300) required; portrait 4:5 at 960x1200 optional; 5 MB each; up to 20 images; content inside the centre 80 per cent. Google Ads Help 17091269, 14530211. High.
2. **Video: 10 seconds or more, one per orientation, auto-generated if none uploaded.** The spec page allows 15 per orientation; the Ad Strength page says 5 total. Help 14528532, 14143250. API docs: "upload your own video so auto-generated videos stop serving". High on specs, Medium on the 15 versus 5 conflict.
3. **Creative automation has campaign controls; 2026 added two default-on AI features.** Help 15290858: "campaign-level controls now let you turn creative applications off or remove individual system-generated assets"; text customisation "was formerly called Automatically created assets". Generated videos carry Source "Automatically created" in Asset group details (Logical Position). AI voice-over on silent videos: opt-out closed 20 Mar 2026, still switchable in video enhancement controls (ALM Corp). Generative resizing into missing aspect ratios: default on, opt-out deadline 4 Sep 2026, still changeable in account (Common Thread Co, Sep 2026; Relevant Audience). Changed 2026. Medium: both rest on practitioner posts.
4. **Brand guidelines are default for all new UI-built PMax campaigns since Jul 2025.** Business name and logos live at campaign level (Help 14934472; ppc.land, Jul 2025). A "text guidelines" beta constrains generated text (Help 16489313). "AI Brief" was previewed at GML 2026 (Jordan Digital, one source). High; Low for AI Brief.
5. **Search themes: 50 per asset group (was 25), hints not keywords.** Store Growers, DataFeedWatch and AdNabu (2026) all say 50; none cite a Google post I could see. Exact match keywords in a Search campaign still win the query (R01). Changed late 2025. Medium.
6. **Audience signals stay hints; 2026 added first-party exclusions.** Google Business Accelerate, "New Performance Max steering and reporting updates coming in 2026": "You can now exclude specific customer lists from your Performance Max campaigns". High.
7. **Brand exclusions use brand lists, and one checkbox decides whether Shopping ads still show.** Help 14505308: campaign Settings > Additional settings > Brand exclusions > pick list or "+ New brand list"; optional "Allow Shopping ads on searches that mention excluded brands". Missing brands can be requested (Help 13721847). Matching is entity based, so misspellings are covered only for library brands (Hustle Marketers, 2026). High.
8. **Campaign level negative keywords are generally available in PMax.** Rolled out early 2025 (groas: 23 Jan 2025); limit raised from 100 to 10,000 in Mar 2025 (groas, DataFeedWatch, AdNabu). They apply to Search and Shopping queries, not YouTube, Display or Gmail (LeadUp, 2026). Negative keyword lists: one source says supported since Aug 2025, another (Oct 2025) says not. Changed 2025. High; Low on lists.
9. **Final URL expansion is on by default and tied to text customisation.** Help 14337539, 14670793: switch off in setup or campaign settings. API docs: you "cannot opt out of text customization if final URL expansion is active". Exclusions: Settings > Asset optimisation > Text customisation > Final URL > "Exclude some URLs". SA360 Help: opting out "isn't recommended". High.
10. **Channel prioritisation and budget allocation launched 14 Oct 2026.** Google blog (14 Oct 2026), Search Engine Land 495946, ppc.land: mark a channel High or Low; a Low channel gets a cap as a percentage of average daily budget, not of actual spend; in PMax, Search partners and Display Network get their own tiers while Google's own surfaces are bundled; progressive rollout from 15 Oct; a separate alpha of finer PMax network controls continues. New this week. High on announcement, Medium on availability in a new AU account by January.
11. **New customer acquisition has two modes.** Help 12080169: "New customer value" (bid higher; Purchase goal required) and "New customer only". Help 14005157 recommends the value mode because it "will not limit the reach of your campaign". New customers come from past purchase conversions and Customer Match lists. The 540 day lookback rests on one source (Lunio). High; Low on lookback.
12. **Experiments has a dedicated "Performance Max vs Shopping" type.** Help 13825980: Experiments > Campaign types > Performance Max vs Shopping; control is a Standard Shopping campaign not in another experiment; treatment an existing or new PMax "with similar settings"; Bidding pre-fills a budget from the Shopping budget and split; the split locks once scheduled and applies "at the eligible auction level"; results show conversions, value, CPA, ROAS and spend; applying makes PMax primary and auto-pauses the control. Google states no minimum duration. Third parties: 50/50 and one month by default (Store Growers); 4 to 6 weeks and 50 to 100 conversions per arm (Benly, ALM Corp, 2026); under 50 a month "will take six months to reach significance" (one source). PMax asset A/B experiments went live Oct 2026 (Help 16807329). High on setup, Medium on duration.
13. **Practitioner floors.** Adgenix (Perth, 2026): under about $3,000 a month start with Standard Shopping. Store Growers (2026): 30 to 50 conversions a month; under $100 a day PMax "often spends too much on Discovery (Display/YouTube)". Google's "18 per cent more conversions when PMax runs beside Shopping" appears only via vendors. Medium.
14. **Feed only PMax.** API docs: without creative assets "reach and performance will be limited"; it serves Shopping and product based Display only, no Search text ads (StatBid, SKU Analyzer). Store Growers (2026) recommends it to force spend into Shopping; DataFeedWatch (2023) saw feed image ads reach YouTube anyway. For Endless Parks it is Standard Shopping with Smart Bidding only, no manual bids, and none of the extra channels the experiment exists to test. Medium.
15. **Reports.** Channel performance report rolled out Jan 2026 (Search, Search partners, Gmail, YouTube, Display, Discover, Maps) at campaign level; asset group level was API only at launch (ppc.land, one source). Search terms: campaign > Insights and reports > Search terms, real queries flagged by theme match (George Tsiros, DataSlayer, 2026). Asset reports carry impressions, clicks, cost, conversions and value. Changed 2025 to 2026. Medium.
16. **Failure modes for a small brand.** Brand cannibalisation without a brand list; Display and YouTube drift under $100 a day; generated text and video off brand (Store Growers; Smarter Ecommerce, 2026; Digitelia). Smarter Ecommerce: a fall in Shopping spend after PMax launches "does not automatically prove cannibalisation"; judge on the account total. Medium.

## 2. Exactly what to do for Endless Parks

### 2a. Gate (decide 29 Dec 2026 on data to 27 Dec)

Run only if all four hold: (1) ep_shop_bottle-tees_au_2026q4 CPA inside A$39 to A$50 over weeks 5 to 8; (2) at least 20 purchases account wide in the trailing 30 days (below the 30 floor, so the kill criteria carry the risk); (3) Purchase conversion with enhanced conversions firing, wholesale excluded; (4) ep_srch_brand_au_2026q4 live on exact match. If any fails, defer to March.

### 2b. Prep in November and December

| # | Step | Where |
|---|---|---|
| 1 | custom_label_0 = bottle on the bottle, = tee on the four tees | Shopify > Google & YouTube channel product fields, or Merchant Center > Products > feed rules |
| 2 | Request "Endless Parks" into Google's brand library; create brand list "EP brand" | Tools > Shared library > Brand lists > + > search, then "Request a brand". Allow weeks |
| 3 | Upload Customer Match list (Shopify customers plus Klaviyo 7,720); check eligibility | Tools > Audience manager > Your data segments > + > Customer list |
| 4 | Cut three videos from Meta winners ("No more USA", meme static with motion): 16:9, 1:1, 9:16, 15 to 30 seconds, no price or offer on screen | Upload unlisted to the EP YouTube channel |
| 5 | Per asset group: 3 landscape 1200x628, 3 square 1200x1200, 2 portrait 960x1200; logo 1200x1200 and 1200x300 | Bottle on the parks map, lifestyle at a National and Marine Park, sticker close-up |
| 6 | Write text assets (2c); confirm none contain price, discount, "free" or "sale" | 05-ad-copy.md |

### 2c. Campaign build (5 to 9 Jan 2027, saved paused)

| Setting | Value | Menu path |
|---|---|---|
| Name | ep_pmax_bottle-tees_au_2027q1 | Campaigns > + > Sales > Performance Max |
| Conversion goals | Purchase only, primary; remove Add to cart, Begin checkout, Page view | Settings > Goals > "Use campaign-specific goal settings" |
| Merchant Center | 5382740922, Australia | Setup step 1 |
| Budget | A$22 a day | Override the pre-fill at experiment creation |
| Bidding | Mirror Shopping: Maximise conversion value, target ROAS 190 per cent if Shopping is on tROAS 1.9; no target if Shopping has none | Bidding |
| Customer acquisition | Tick "Bid higher for new customers", value A$20 (placeholder). Not "Only bid for new customers" at this volume | Bidding > Customer acquisition |
| Locations, language | Australia, "Presence: people in or regularly in"; English | Settings > Locations > Location options |
| Final URL expansion | Off; confirm Text customisation shows off after saving | Settings > Asset optimisation |
| Video automation | Untick any "Allow Google to create videos" and video enhancement options shown | Settings > Asset optimisation; Asset group > Videos |
| Brand exclusions | Apply "EP brand"; leave "Allow Shopping ads on searches that mention excluded brands" unticked | Settings > Additional settings > Brand exclusions |
| Campaign negatives | Paste 05-negatives.txt plus [endless parks], [endless parks bottle], [endless parks water bottle], [endlessparks] while the library request is pending | Audiences, keywords and content > Search keywords > Negative keywords > select campaign |
| Channel controls | If visible: Display Network Low, 10 per cent cap; Search partners Low, 10 per cent cap. If not, add account-level placement exclusions for mobile app categories and parked domains | Settings > Channel controls (new 14 Oct 2026) |
| Ad schedule, devices, URL suffix | None; none; inherits the PLAN.md account suffix | |

**Asset group 1: Bottle.** Listing group custom_label_0 = bottle; final URL /products/ultimate-adventure-bottle. Headlines (15), examples: "Parks Bottle 1.2 L", "National and Marine Parks Bottle", "Tick Off Parks With Stickers", "Perth Designed, Hand Drawn", "Keeps Cold 12 Hours", "Straw Lid Included", "4.89 Stars, 99 Reviews", "Gift for Road Trippers"; the rest in 05-ad-copy.md. Long headline lead: "The 1.2 L bottle that maps Australia's National and Marine Parks, with stickers to tick off each one you visit". Descriptions (5, one under 60): "Hand drawn in Perth. Ships from Balcatta WA."; others on sticker pack, reviews, 30 day returns; "Free standard shipping over $120" only if PLAN.md question 8 is cleared. Search themes (20 to 25, written as customers type them, not as ad copy): national parks water bottle, marine parks water bottle, road trip water bottle australia, 1.2l insulated bottle with straw, gifts for grey nomads, gifts for 4wd lovers, hiking bottle australia, camping gifts australia, parks sticker bottle, big lap gifts. Audience signals: Customer Match purchasers, 30 day site visitors, custom segment of the same queries, in-market Outdoor Recreation Equipment. Videos: all three orientations.

**Asset group 2: Tees.** Listing group custom_label_0 = tee; final URL /pages/drop-01 until a tees collection exists. Headlines: "Australian Made Tees", "Hand Drawn Parks Tees", "Stirling Stamps Tee", "Bluff Knoll Tee", "Our Backyard Tee", "Adventure Club Tee", "Sizes XS to XXL", "Designed in Perth", plus brand variants. "Australian Made certified" only if PLAN.md question 5 is cleared. Search themes (as typed): australian made t shirts, parks t shirt australia, hiking t shirt australia, bluff knoll shirt, stirling range tee, gifts for hikers australia. Expect little: tees have no Shopping history.

### 2d. Experiment setup (Monday 12 Jan 2027)

1. Campaigns > Experiments > + > Campaign types > Performance Max vs Shopping.
2. Control ep_shop_bottle-tees_au_2026q4; treatment ep_pmax_bottle-tees_au_2027q1.
3. Split 50/50; set the PMax budget to A$22, ignoring the pre-fill. Each arm enters half the eligible auctions, so combined spend sits near A$22 to A$30 with spikes to A$44; the new advertiser credit landing about 21 Dec covers the overage, which is why January fits.
4. Start 12 Jan, end 22 Feb 2027 (6 weeks). Freeze bids, budgets, assets and negatives in both arms except for kill criteria.
5. Tick "View results with comparable campaigns". Judge on the two arms' CPA, ROAS and total purchases, cross-checked against Shopify new customer orders (wholesale excluded) and Triple Whale MER, never on PMax's own column alone.

### 2e. Weekly reads

Campaign > Insights and reports > Channel performance (spend share by channel); Search terms (brand terms and the negatives list; add a campaign negative only when a term wastes over A$10); Assets filtered to Source "Automatically created" (remove any); Listing groups (bottle versus tee spend); Reports > Predefined > Other > Performance Max campaigns placement.

### 2f. Kill criteria

| When | Kill if | Action |
|---|---|---|
| Day 7 | Any generated text or video asset serving, or brand queries over 5 per cent of PMax clicks | Fix same day; if it recurs, end |
| Day 14 | Display plus YouTube plus Discover over 40 per cent of PMax spend with zero purchases | End, keep Shopping |
| Day 21 | PMax spend over A$450 with 2 or fewer purchases, or PMax CPA over A$90 | End, keep Shopping |
| Day 42 | PMax CPA over A$50 or ROAS under 1.9, or under 12 purchases in the arm, or blended new customer CPA worse than December | End without applying; retest at A$3,000 a month |
| Day 42 | PMax CPA at or under Shopping's with 12 or more purchases and blended new customer orders up | Apply (PMax primary, Shopping pauses); keep both Search campaigns and the brand list; recheck brand exposure after 14 days |

## 3. Where sources disagree

- **Duration.** Google sets none for this type; practitioners range from 2 to 3 weeks to 12 weeks. At 20 to 30 conversions a month the test cannot reach formal significance; 6 weeks plus kill criteria is a practical compromise.
- **Feed only.** Store Growers says right for most stores; Google says reach is limited; StatBid treats it as a Shopping clone. For five products already on Standard Shopping it is not worth a test.
- **Video limits.** 15 per orientation versus 5 total. Three uploads satisfy both.
- **Negative keyword lists.** Supported (Aug 2025) versus not (Oct 2025). Pasting negatives into the campaign sidesteps it.
- **Channel controls.** Announced 14 Oct 2026, progressive rollout; a new AU account may not see them in January, hence the placement exclusion fallback.
- **Final URL expansion.** Google (SA360 Help) advises against opting out; small catalogue practitioners say off. With a parks map page that converts poorly, off.

## 4. Open questions for Jake

1. New customer value: is A$20 extra per first order right when 77 per cent of orders are already new? A$10 keeps the bias gentle.
2. Can the Klaviyo list go into Customer Match under the privacy policy, and will the account be eligible by January?
3. Tees landing page: /pages/drop-01 or a new /collections/tees?
4. Which Meta videos can be re-cut to 9:16 and 1:1 with no price or offer on screen?
5. Confirm the brand library request was submitted and approved before 5 Jan.
6. Is A$44 a day combined Shopping plus PMax acceptable on peak days for 6 weeks, funded by the credit?
7. Bottle only, or bottle and tees? Two asset groups is the brief; bottle only gives a cleaner read.

## 5. Sources

- Google Ads Help (support.google.com/google-ads/answer/<id>, undated, read 15 Oct 2026): 17091269 specs; 14530211 images; 14528532 video; 14143250 Ad Strength; 15290858 creative video automation controls; 14934472 brand guidelines; 16489313 text guidelines beta; 14505308 apply brand exclusions; 13721847 brand settings; 14337539 and 14670793 final URL expansion; 12080169 customer lifecycle goals; 14005157 NCA troubleshooting; 13825980 Standard Shopping vs PMax experiments; 13826584 Experiments FAQ; 16807329 PMax asset experiments.
- Google Ads API: developers.google.com/google-ads/api/performance-max/assets, /optimizations, /retail.
- blog.google/products/ads-commerce/channel-prioritization-budget-allocation, 14 Oct 2026; searchengineland.com/...-495946 and ppc.land, Oct 2026.
- business.google.com/en-all/accelerate/resources/articles/new-performance-max-steering-and-reporting-updates-coming-in-2026.
- storegrowers.com/performance-max-campaigns and /google-ads-experiments, 2026; smarter-ecommerce.com, Shopping alongside PMax in 2026; adgenix.com.au/blog/performance-max-vs-standard-shopping, 2026.
- commonthreadco.com AI video resize (Sep 2026) and asset experiments (Oct 2026); relevantaudience.com AI reframe opt out, 2026; almcorp.com AI voice-over, Mar 2026.
- ppc.land brand guidelines rollout, Jul 2025; searchengineland.com/...-480802 NCA; groas.ai PMax negatives, 2025; analyzify.com PMax negatives, 2025; datafeedwatch.com PMax updates 2025 and feed-only (2023); leadup-marketing.com, 2026.
- hustlemarketers.com brand exclusions, 2026; statbid.com and skuanalyzer.com feed-only; blog.adnabu.com, 2026; georgetsiros.gr, dataslayer.ai, benly.ai, 2026; lunio.ai; logicalposition.com; jordandigitalmarketing.com GML 2026.
