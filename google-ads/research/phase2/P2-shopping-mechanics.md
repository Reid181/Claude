# P2: Standard Shopping mechanics for a one hero product account (Oct 2026)

Builds on `/home/user/Claude/google-ads/PLAN.md`, `04-campaign-build.md` and `06-launch-and-optimise.md`. Page loads were blocked, so quotes come from search extracts; confirm labels on screen. Numbers are `support.google.com/google-ads/answer/N`, or MC for `support.google.com/merchants/answer/N`.

## 1. Findings

1. **Standard Shopping is still a subtype beside Performance Max.** "Create a Shopping campaign" (3455481) still describes choosing Shopping, the Merchant Center account and country of sale, then the subtype. Google "suggests Performance Max campaigns instead" (6275296), so PMax is offered first. No source shows the Oct 2026 subtype screen. Confidence: High it exists, Med on label positions.

2. **AI Max for Shopping is a beta, opt-in bundle, not a default.** "About AI Max for Shopping campaigns (beta)" (17091277): it "bundles two main settings, text customization and Final URL expansion"; text customisation "rewrites product titles using Merchant Center feed content" and "Final URL expansion requires text customization to be turned on". Practitioners call it "a suite of opt-in AI features" enabled with "one click in campaign settings" (commonthreadco.com Jul 2026, tsvik.com 2026); the 30 Apr 2026 launch date rests on one secondary source. Bigflare (2026) names the real change: "the campaign can show search text ads instead of only Shopping ads". The Sep 2026 AI Max auto upgrade hit Search campaigns only (witscode.com). Confidence: High that it is opt-in; Med on whether the toggle shows in every account (adstack.com and bigflare.com call it a closed beta).

3. **Campaign priority unchanged: Low (default), Medium, High.** It "determines which campaign should participate in the auction for that product" only when a product sits in several Standard Shopping campaigns; "if the highest priority campaign runs out of budget, the lower priority campaign bids" (6275296). With one campaign it does nothing. Confidence: High.

4. **Custom labels lag; product type is the safe fallback.** "It may take up to 24-48 hours for newly created or edited custom labels to appear in Google Ads" (6275295). Shopify Help: "initial product syncing can take up to 24 hours. After the initial sync, changes to your products typically sync within a few hours", and "Google reviews new products within 3-5 business days" (help.shopify.com, syncing-products). Shopify's docs say the channel ignores the legacy "Custom Label 0 to 4" CSV columns (storesteady.com quoting Shopify); one Shopify Community thread (2024) reports a "Custom label 0" column in the Google & YouTube app's bulk editor. Confidence: High on lag, Low on the app exposing labels.

5. **Bid strategies for Shopping, Oct 2026.** Enhanced CPC was "retired from Search and Display campaigns on March 31, 2025, after its earlier removal from Shopping in October 2023" (stackmatix.com; Bidding FAQ 10286469 confirms). Left for Standard Shopping: Manual CPC; Maximise clicks with an optional cap ("Setting a maximum CPC bid limit can help you to control costs", 6268626); Maximise conversions; Maximise conversion value with or without a target; Target CPA; Target ROAS. The one published minimum: "at least 15 conversions per Merchant Center ID in the last 30 days" for Target ROAS (6309035); an older Google PDF's 20 in 45 days is superseded. "Setting bid limits for Target ROAS isn't recommended" (6268637). Confidence: High.

6. **Negatives: 10,000 per campaign, lists still documented at 5,000.** Per campaign "10,000 | Help 637265, verified September 2026" (hustlemarketers.com). Google (7102995) still says 20 shared lists of 5,000, while practitioners "reported successfully adding up to 10,000 per list since September 2025". Account level negatives (1,000 max) "apply to all search and shopping inventory". Shopping search terms: campaign > Insights and reports > Search terms. Confidence: High on scope, Med on list cap.

7. **Product diagnostics live inside Google Ads.** "Go to Products within the Campaigns menu, then select the Diagnostics tab"; statuses "Eligible, Eligible (limited), and Not eligible"; Not eligible can mean "out of stock" or "the accounts aren't linked" (12097493; ZATO, 2025). "About Product Reporting" (17035334): "starting June 2026, product reporting has expanded" across campaign types; Products columns include "Item ID, Title, Channel, Brand, Price, Custom label, Product status, Impressions, Clicks". "Limited by budget" is a campaign Status value, not a product status. Confidence: High.

8. **Annotations, and what Australia gets.** The MC table (table/15696143) lists shipping speed, return policy and minimum order value annotations; "Google dynamically decides which annotations and badges to display". Fast shipping ("Free 3-day", "Get it by [Date]") is available in Australia with a 3 day threshold (MC 15914918, about Feb 2025). Google "will verify whether your shipping speed and cost meet the requirements" first (MC 14264257). Adding a return policy makes ads "eligible to show return annotations" (MC 15254380). No "ships from Australia" annotation exists; the Australian signal is country of sale, AUD pricing and an Australian shipping service. Confidence: High.

9. **Product ratings: the bottle qualifies and Judge.me is now direct.** Google needs "a minimum of 50 reviews in your Product Ratings feed" across all products, uploaded at least monthly (MC 6098512, 14549080). Judge.me's help article (updated about 9 Oct 2026) says Judge.me "is now an approved Google review partner", reviews flow via an "API Product Ratings feed" (XML users must switch "by January 15, 2027"), and they go to "a centralized Judge.me account, so you won't see them inside your own Google Merchant Center". A 3 reviews per product floor is secondary (webappick.com). Without GTINs matching relies on brand plus SKU or MPN. Confidence: High on the rule, Med on no GTIN matching.

10. **Promotions work in Australia; BFCM only.** Australia is one of 13 promotion countries (litcommerce.com citing MC 13422697, verified 30 Jun 2026). Needs an active product and claimed URL; whole number discounts; 183 day maximum; "submitting expired, invalid, or misleading offers triggers a Misrepresentation suspension" (gmcunbanned.com, 2025). From 12 Oct 2026 AI Mode reportedly shows promotion badges (ecommercefastlane.com, single source). Confidence: High.

11. **"Marketing methods" replaced Destinations.** "Marketing methods (previously known as Destinations) refer to how and where your products are shown on Google", options "free listings, Shopping ads, YouTube store, YouTube affiliate, and dynamic remarketing", editable per data source or product (MC 15130232). ZenoX (Oct 2026) says the "Next" name was dropped in Jul 2026; single source. Image minimum rises to 500x500 px from 31 Jan 2027 (MC 16989427). Confidence: High.

12. **Auction insights for Shopping: three metrics.** "Impression share, overlap rate, and outranking share"; nothing shows under 10 per cent impression share; "search partner traffic is excluded" (2579754). Product group level is not confirmed. Confidence: High.

13. **Local inventory ads default on since 31 Aug 2026; "Local products" setting removed.** Ads Developer Blog, 20 Jul 2026 (via ppc.land, seroundtable.com): the setting is "replaced with the Inventory filter, using Channel = Local or Channel = Online". Only accounts with the local inventory add on are affected. Sources disagree on PMax scope. Confidence: High for Shopping.

14. **Channel prioritisation card, announced 14 to 15 Oct 2026** (18385152; searchengineland.com, blog.google). "Shopping campaigns can only group Google Search and Search partners"; channels are "High or Low priority"; Low channels take "a desired daily budget allocation percentage" on a best effort basis; it works "at both account and campaign level"; rollout is progressive "over the coming months". Until the card appears, the Networks checkbox is the control. Confidence: High on scope, Med on timing.

15. **Landing page rules.** "Google Ads uses product URLs in the Google Merchant Center feed as the final URLs" (Adobe Experience League); Shopping "Campaign URL options" hold only a tracking template and Final URL suffix (3455481), and lower level suffixes override higher ones (9054021). "You may not use cross-domain redirects in your final URL" (6080568). Price and availability "must match your landing and checkout page" or the item takes a critical error; "if the price mismatch happens frequently, Google will no longer use automatic updates" (adnabu.com, datafeedwatch.com, 2025). Variants need their own link (Shopify `?variant=`) and structured data with "a unique URL and unique product identifier for each variant" (ilanadavis.com). Confidence: High.

16. **Apparel attributes for the tees.** colour, size, gender, age_group are hard requirements in "Brazil, France, Germany, Japan, the UK, and the US" and "strongly recommended" elsewhere, but "if products in an item group differ by color or size, both attributes are required in every market" (gmccheck.com, 2026; MC 14916941). The tees vary by size, so size and colour are mandatory, with gender unisex and age_group adult. Confidence: Med on the country list (one secondary source), High on the item group rule.

## 2. Exactly what to do for Endless Parks

### Build spec: ep_shop_bottle-tees_au_2026q4

| Setting | Value | Where |
|---|---|---|
| Type and subtype | Shopping, then "Standard Shopping campaign", never Performance Max | Campaigns > plus > New campaign > Sales > Shopping > Merchant Center 5382740922 > Country of sale Australia |
| Budget | A$22 a day, individual | Settings > Budget |
| Bidding | Manual CPC (Enhanced CPC no longer exists for Shopping) | Settings > Bidding |
| Campaign priority | Low (default); only matters with a second Shopping campaign | Settings > Campaign priority |
| Networks | Untick "Include Google search partners". If the Channel prioritisation card shows instead, Search partners Low at 0 per cent | Settings > Networks, or Settings > Channel prioritisation |
| Local inventory | "Local products" box is gone. Leave Inventory filter off; no local feed, so LIA default on changes nothing | Settings > Inventory filter |
| AI Max for Shopping | Off. If present, text customisation and Final URL expansion both off; re check after every save | Settings > AI Max |
| Automatically created assets | Off at campaign level | Settings > Automatically created assets |
| Locations, languages | Australia, Presence only; English | Settings > Locations > Location options |
| Devices, schedule | All, none | Defaults |
| URL options | Empty; the account level suffix in PLAN.md applies | Settings > Campaign URL options |
| Ad group | `all_products`, default bid A$0.80 | Ad groups |
| Product groups | Subdivide by Custom label 0: `hero` A$1.10, `apparel` A$0.60, Everything else Excluded. Fallback until labels reach Google Ads (24 to 48 hours after sync): Product type, Water Bottle A$1.10, T-Shirt A$0.60, Everything else Excluded | Ad group > Product groups > pencil > Subdivide |
| Negatives | Attach `EP_Negatives_Shopping`, kept under 5,000 terms | Campaign > Keywords > Negative keywords > Use negative keyword list |
| Gate to enable | 3 bottle variants and 4 tees show Eligible, not Eligible (limited) | Campaigns > Products > Diagnostics |

### Feed and Merchant Center steps before launch

1. Shopify admin > Sales channels > Google & YouTube > Products > bulk editor: look for a "Custom label 0" column. If present, set `hero` on the bottle and `apparel` on the tees. If absent, set Product type "T-Shirt" on the tees (bottle is already "Water Bottle"). Allow a few hours for Shopify to push and 24 to 48 hours before the value appears in the Google Ads product group picker.
2. Tees in the same editor: Colour and Size per variant, Gender unisex, Age group adult, Google product category Apparel & Accessories > Clothing > Shirts & Tops.
3. Merchant Center: website claimed; the data source's Marketing methods include Shopping ads and Free listings.
4. Merchant Center > Shipping and returns: Australia service A$14 standard 2 to 8 business days, A$19 express 1 to 4, free over A$120, plus the 30 day return policy. A single bottle shows A$14 shipping; a 2 bottle cart earns "Free delivery".
5. Judge.me > Settings > Integrations > Google Shopping: enable the API Product Ratings feed (needs 50 reviews; the bottle has 99). Confirm it maps on SKU or MPN since there are no GTINs. Allow 1 to 2 weeks for stars.
6. Landing pages: each bottle colour's feed link is the `?variant=` URL; load each, confirm A$87 and In stock, and run one through the Rich Results Test. Redirect any page still showing A$58 or A$63.
7. Promotions: none now. Build the BFCM promotion in Merchant Center > Marketing > Promotions on 20 Nov for 25 Nov to 1 Dec only.

### First 30 day routine

| Day | Bottle group (`hero`) | Tees group (`apparel`) |
|---|---|---|
| 1 to 2 | Products > Diagnostics: 3 variants Eligible. Expect A$15 to A$25 a day | 4 tees Eligible, every size present. Expect A$2 to A$6 a day |
| 3 | Search terms: negate other brands, "free", "printable", state park names, sticker only queries. Keep generic bottle queries for now | Negate non apparel ("hoodie", "kids", "dress") |
| 7 | Columns Search impr. share, Search lost IS (rank), Click share. Lost IS (rank) above 70 per cent with CPC under A$1: bid to A$1.30 | Zero impressions: check Products status, then bid to A$0.75 |
| 10 | Auction insights (campaign level): note overlap (expect Amazon AU, Kathmandu, Frank Green, Awesome Maps). No action | Same report |
| 14 | Expect 150 to 300 clicks, 2 to 6 orders. Zero orders on 200 clicks: recheck tracking before bids. Split search terms into "parks" and generic "water bottle"; record CTR and CVR for each | 60 to 120 clicks expected. Zero sales on 100 clicks: bid to A$0.45 |
| 21 | CPA under A$50: bid up 15 per cent. Generic queries at 100 clicks with no sale: phrase match negatives | 150 clicks, no sale: pause the group |
| 28 to 30 | 15 conversions on the Merchant Center ID in 30 days: Maximise conversion value, no target. Target ROAS 190 per cent only at 30 conversions and two weeks later. Under 15: stay Manual CPC, or Maximise clicks with a A$1.30 bid limit if impressions are the problem | Tees inherit any strategy switch; check tee CPA weekly after it |

Weekly on Monday: Campaigns > Products, last 7 days by Impressions, for any variant at zero; Campaign Status for "Limited by budget" (fine in week 1; from week 3 raise Shopping by A$5 if it persists with CPA under A$50); Merchant Center > Products > Needs attention; Change history filtered to Auto applied.

## 3. Where sources disagree

- **AI Max for Shopping availability.** Common Thread and Tsvik: live, one click. Adstack and Bigflare: closed beta. Google labels it beta. Check per account after every save.
- **Enhanced CPC dates.** Google: week of 24 Mar 2025 for Search and Display; xwork.my says 31 Aug 2026 (outlier). Shopping: Oct 2023 everywhere.
- **Negative list cap.** Google 5,000 per list; practitioners report 10,000 since Sep 2025. Stay under 5,000.
- **Custom labels from Shopify.** Docs say CSV columns are ignored; a community thread says the bulk editor exposes Custom label 0. Product type is the fallback.
- **Ratings per product floor.** Google documents 50 across the feed; 3 per product is third party only.
- **LIA scope.** Priority Pixels includes PMax; ppc.land says Shopping only. Moot without a local feed.
- **Target ROAS minimum.** Google: 15 in 30 days. Practitioners: 30 to 50 a month.
- **Channel reporting.** Search versus partner splits exist for PMax (2026); Shopping has only the partner placement report (Aug 2025).

## 4. Open questions for Jake

1. Does the Google & YouTube app's bulk editor show a "Custom label 0" column? The product group design depends on it.
2. Judge.me plan tier, and does Settings > Integrations show "Google Shopping (API feed)"? Which identifier does it map on without GTINs?
3. Do the feed links carry `?variant=` for each bottle colour and tee size? Check one row in Merchant Center > Products.
4. Does the Shopping settings page show an AI Max section, a Channel prioritisation card, or the old Networks checkbox?
5. Tee colours per design, and are sizes XS to XXL the only variant axis?
6. Return policy for Merchant Center: 30 days, free or customer paid?
7. Does Merchant Center > Settings > Add-ons show a local inventory add on? Expected no.

## 5. Sources

- Google Ads Help answers: 3455481, 6275296, 17091277, 15909989, 6275295, faq/10286469, 6268626, 6268637, 6309035, 7102995, 12097493, 17035334, 6275319, 2579754, 18385152, 9054021, 6080568
- Merchant Center Help answers: 15130232, 16989427, table/15696143, 15914918, 14264257, 15254380, 6098512, 14549080, 14620160, 14916941, 13422697 (via litcommerce)
- Shopify Help Center: Syncing your products (Google & YouTube). Judge.me Help: Syncing product reviews to Google Shopping (Oct 2026)
- Channel prioritisation: searchengineland.com, searchenginejournal.com, blog.google (15 Oct 2026). LIA: ppc.land, seroundtable.com (Jul 2026)
- AI Max for Shopping: commonthreadco.com, tsvik.com, bigflare.com, adstack.com, riverstonemarketingsolutions.com, witscode.com, bearded.digital (2026)
- Bidding and negatives: stackmatix.com, bigeyeagency.com, storegrowers.com, hustlemarketers.com, optmyzr.com (2025 to 2026)
- Diagnostics: zatomarketing.com (2025), digitalapplied.com (30 Jul 2026)
- Feed and landing pages: storesteady.com, Shopify Community, adnabu.com, datafeedwatch.com, ilanadavis.com, gmccheck.com
- Promotions and naming: litcommerce.com, gmcunbanned.com, ecommercefastlane.com, zenoxmedia.com (2025 to 2026)
