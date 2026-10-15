# R02 to R07: Shopify Google & YouTube channel, conversion tracking and measurement (Oct 2026)

Prepared 15 Oct 2026 for Endless Parks (endlessparks.com, Shopify f8dc9c-2.myshopify.com, AUD, GST inclusive). Builds on R01; does not repeat campaign architecture.

Method note: in this research environment every direct page fetch (Google Ads Help, Merchant Center Help, Shopify Help Center, Triple Whale KB, Shopify Community) was blocked at the network layer, so findings come from search-engine extracts of those pages (33 queries, extended mode) rather than full page reads. Quotes are as returned by the search tool. Where a claim rests on a vendor blog or forum post rather than Google or Shopify documentation, confidence is marked Med or Low and the verification checklist in section 2 is written so Jake can confirm it in the UI in minutes.

Confidence key: High = stated in Google or Shopify documentation, Med = consistent practitioner sources or a single official extract, Low = single vendor or forum claim.

---

## 1. Findings

### A. What the Google & YouTube channel sets up, and Merchant Center naming

1. The channel (Shopify admin > Sales channels > Google & YouTube) links one Google account (for Endless Parks this is endlesspks@gmail.com) and from it creates or connects a Merchant Center account (5382740922 exists), optionally a Google Ads account, and a GA4 property. Product sync is one way: Shopify is the source of truth and overwrites Merchant Center product data (titles, descriptions, categories), which is why R01 says to make feed fixes in Shopify. A Shopify Community thread from 2026 describes titles reverting and attributes disappearing after sync; replies attribute part of it to Merchant Center "automatic improvements". Source: https://community.shopify.com/t/shopify-google-merchant-center-sync-disaster-191-skus-wiped-attributes-overwritten-nothing-updating-losing-my-mind/589194 (2026). Confidence High on the overwrite direction, Med on the thread specifics.

2. Naming change: "Merchant Center Next" is now just "Merchant Center". Google's July 2026 notice says the "Next" qualifier is being dropped with no action needed. All merchants were migrated to the Next platform by 1 October 2024. Two renames from that migration stand: "Destinations" are now "Marketing methods" and "Feeds" are now "Data sources". Sources: https://support.google.com/merchants/answer/17252069 (Jul 2026), https://support.google.com/merchants/answer/15285007 (2024), https://searchengineland.com/google-drops-next-from-merchant-center-next-481882 (Jul 2026). Confidence High.

3. The channel's product sync had an API migration on 18 August 2026. Channable and Search Engine Roundtable report that reinstalling the app after the change can rewrite product IDs (losing Merchant Center performance history) and that the migration changed the country code segment in some IDs. Practical rule: do not uninstall or reinstall the Google & YouTube app; check the product ID format in Merchant Center > Products once and keep it. Sources: https://www.seroundtable.com/google-youtube-shopify-app-sync-merchant-concerns-41627.html (Aug 2026), https://www.channable.com/blog/shopify-google-youtube-app-migration (2026). Confidence Med.

4. GA4 via the channel: the app connects a GA4 property (Settings tab > Google Analytics) and fires GA4 ecommerce events (view_item, add_to_cart, begin_checkout, purchase) from its own web pixel. The G-M3LTBNJ7H4 tag on endlessparks.com is consistent with this. A March 2026 community post notes the GA4 tag can no longer be added directly to themes; tracking has to go through Shopify web pixels. If a second GA4 tag (custom pixel or GTM) also fires purchase, GA4 double counts; the test is whether a transaction_id appears twice in GA4. Sources: https://community.shopify.com/t/enabling-all-events-in-ga4/583880 (2026), https://support.google.com/analytics/answer/12183125 (undated). Confidence High.

5. Google pushed a 2025 "migrate your tags to the Google & YouTube app" programme for Shopify stores that still had a hand-pasted Google tag or GA4 snippet in theme.liquid. The help pages for it tell merchants to verify the upgrade and remove legacy tags to avoid duplicate measurement. Sources: https://support.google.com/google-ads/answer/16030792 (2025), https://support.google.com/google-ads/answer/16138144 (2025), https://support.google.com/merchants/answer/16031492 (FAQ, 2025). Confidence High.

### B. Conversion tracking options and which to use

6. The channel's own conversion tracking is the recommended single primary. When a Google Ads account is linked, the app lists Shopify events (purchase, add_to_cart, begin_checkout) and creates conversion actions for them. Google's doc: a Purchase action "is created automatically and set as the account default"; add to cart and begin checkout are "created as secondary actions, included for observation only, which don't affect bidding". Google tells merchants to verify campaigns bid to the new action, that it is primary, and to remove legacy tags. Sources: https://support.google.com/merchants/answer/13494537 (current), https://support.google.com/merchants/answer/15457737 (current). Confidence High. Historic naming: older installs show "Google Shopping App Purchase" (the two-tags thread below uses that name); newer installs may show a plain "Purchase" action with the Google & YouTube app as source. Confidence Med on names.

7. Enhanced conversions for web are not on by default via the channel in Google's current documentation. Both the Google Ads and Merchant Center pages say: on the Settings page of the app find "Google Ads settings", find "Enhanced conversions" and select Turn on, and accept the Customer Data Terms in Google Ads (Goals > Conversions > Settings). One 2026 vendor guide (tagassists.com) claims the toggle was removed in April 2026 and the feature became automatic; no official page or other guide published as late as 26 April 2026 supports that. Sources: https://support.google.com/google-ads/answer/15496063 (current), https://support.google.com/merchants/answer/13494537 (current), https://tagassists.com/blog/google-ads-shopify-conversion-tracking/ (2026), https://attribuly.com/blogs/google-enhanced-conversions-shopify-setup/ (26 Apr 2026). Confidence High that it must be checked, Med that a toggle still exists.

8. Enhanced conversions verification lives in Google Ads under Goals > Conversions > Summary > (the Purchase action) > Diagnostics tab, which shows the enhanced conversions status, match rate band (High, Average, Low) and implementation warnings. Source: https://support.google.com/google-ads/answer/11956168 (current). Confidence High.

9. Google Ads Data Manager has a direct Shopify connection (Tools > Data manager > Connect product > Shopify). The current Data Manager page says it "supports importing customer match lists from Shopify" and "doesn't support importing conversion data from Shopify to Google Ads"; an older Google Ads copy of the same page described a server-to-server purchase import deduplicated against the tag. Read: the server-side purchase import was trialled and withdrawn or folded into the app; treat the Data Manager Shopify connector as Customer Match only in Oct 2026. Sources: https://support.google.com/google-ads-data-manager/answer/15496063 (current), https://support.google.com/google-ads/answer/15496063 (older copy). Confidence Med.

10. Custom pixel (Settings > Customer events > Add custom pixel) running gtag with the Google Ads conversion ID is the fallback if the channel's tracking is unreliable. Shopify's own GTM tutorial maps checkout_completed to a purchase payload with totalPrice as value and shipping and tax as separate fields; the order ID must be sent as transaction_id so Google can deduplicate. Custom pixels are sandboxed and run on the storefront, checkout and thank you page; "Additional scripts" on the order status page are deprecated and should not be used. Sources: https://help.shopify.com/en/manual/promoting-marketing/pixels/custom-pixels/gtm-tutorial (current), https://help.shopify.com/en/manual/promoting-marketing/pixels/custom-pixels/code (current), https://stape.io/blog/google-ads-conversion-tracking-for-shopify (2026). Confidence High.

11. Duplicate pitfalls, three distinct ones: (i) the same event fired by the channel and by a custom pixel or GTM into the same conversion action, which transaction_id deduplicates only if both send the same order ID; (ii) two separate primary purchase actions (for example the channel's Purchase plus an imported GA4 purchase key event), which Google adds together because transaction ID dedupe only works within one action; (iii) a reported channel bug where Tag Assistant shows two identical "Google Shopping App Purchase" tags to different URLs for one order. Google's own guidance: "check that you don't have duplicate tags if you have conversions in the Google & YouTube app and in the storefront or custom pixel". Fix for all three: one purchase source, one primary action, everything else secondary or deleted. Sources: https://support.google.com/merchants/answer/13494537, https://weltpixel.com/blogs/news/running-a-tracking-app-alongside-shopifys-google-and-youtube-channel (2026), https://community.shopify.com/t/the-google-youtube-app-is-firing-two-identical-purchase-tags-to-different-urls-why/553720 (2025 to 2026). Confidence High on (i) and (ii), Med on (iii).

12. GA4 key events imported into Google Ads arrive as secondary by default and must be promoted to primary to drive bidding. Counts will not match the tag because GA4 reports on event date with its own attribution while Google Ads reports on click date within the conversion window. Use the import as a secondary cross-check only. Source: https://weltpixel.com/blogs/news/ga4-key-events-vs-conversions-on-shopify-what-the-2024-rename-changed (2026), https://petersutarik.com/blog/import-ga4-conversions-google-ads/ (2025). Confidence Med.

13. Consent mode. Shopify's help says event data sent to Google from EEA visitors will not be used for personalised advertising unless Google Consent Mode v2 is active and consent is obtained, and that the Google & YouTube app handles this while a custom pixel needs a manually inserted snippet. A Shopify developer forum thread reports the app's web pixel pushes consent "default granted" where no banner applies, and another that the native GA4 integration uses basic rather than advanced consent mode. Shopify's automated privacy settings only configure the cookie banner for the UK and EEA; "the cookie banner will not be active in these regions by default" elsewhere, including Australia. Sources: https://help.shopify.com/en/manual/privacy-and-security/privacy/customer-privacy-settings/understanding-customer-privacy-settings (current), https://help.shopify.com/en/manual/privacy-and-security/privacy/customer-privacy-settings/privacy-settings (current), https://community.shopify.dev/t/web-pixel-google-youtube-app-always-pushing-default-granted/23016 (2025), https://community.shopify.dev/t/shopify-pixels-shopify-consent-banner-and-google-consent-mode-v2/2123 (2024). Confidence High on Shopify defaults, Med on what the app sends.

14. Australia and the Privacy Act. There is no Australian cookie consent law in force on 15 Oct 2026. What has changed: the OAIC issued tracking pixel guidance in November 2024, and in June 2026 made determinations against Medmate and Monash IVF (health providers) finding that pixel use breached APP 3.3 (sensitive information without consent) and that behavioural retargeting is direct marketing under APP 7. A draft Privacy Act bill published around 31 August 2026 proposes consent before disclosing personal information for direct marketing and names cookies and pixels in programmatic advertising; it is not law and Tranche 2 has no timetable. Read for Endless Parks (non-sensitive retail): no banner required for AU visitors at launch, but the privacy policy must disclose Google Ads, Meta, Triple Whale and Clarity pixels and name retargeting, and the Shopify Customer Privacy opt-out page should be enabled. Sources: https://www.allens.com.au/insights-news/insights/2026/07/tracking-pixels-targeted-advertising-and-compliance-lessons-from-recent-oaic-determinations/ (Jul 2026), https://www.claytonutz.com/insights/2026/july/oaic-determines-the-use-of-tracking-pixels-did-not-track (Jul 2026), https://privacymatters.dlapiper.com/2026/06/australia-pixel-perfect-the-regulator-addresses-use-of-tracking-pixels/ (Jun 2026), https://ppc.land/australia-would-force-ad-tech-to-get-consent-before-sharing-pixels/ (Sep 2026). Confidence High on the determinations, Med on the draft bill detail.

15. Auto-tagging (gclid) is on by default for new Google Ads accounts and is switched on automatically when a conversion action is created. Path: Admin (gear) > Account settings > Auto-tagging > tick "Tag the URL that people click through from my ad". A March 2026 community thread shows the main failure mode: a redirect on the landing page (homepage redirect, country or www redirect) stripping the gclid so only about 10% of sales attributed. Sources: https://support.google.com/google-ads/answer/3095550 (current), https://community.shopify.com/t/google-ads-and-shopify-not-picking-up-conversion-data-gclid-issue/591677 (Mar 2026). Confidence High.

16. Verification tooling: a new action shows "Unverified" until Google sees the tag, then "Recording conversions" once it has recorded in the last 7 days; "No recent conversions" and "Tag inactive" are the other statuses. From Goals > Conversions > Summary you can launch Tag Assistant for any action showing Unverified, Tag inactive or Needs attention, trigger the conversion on the site, then refresh; verified status updates in about 30 minutes, while reported conversions can lag 24 to 72 hours. Sources: https://support.google.com/google-ads/answer/10989978 (current), https://support.google.com/google-ads/answer/1722022 (current). Confidence High.

### C. Value, currency, primary and secondary, attribution, windows

17. The channel sends Shopify's subtotalPrice as the conversion value, that is line items after discounts, excluding shipping. Google's migration FAQ confirms the field and notes Shopify fixed a bug at the end of April 2025 so order-level discounts are now reflected. Because Endless Parks prices are GST inclusive, subtotalPrice includes GST: an $87 bottle reports 87, not 79.09. A Shopify Community thread reports the value appearing tax inclusive from September (year not shown) and a January 2026 App Store review complains the app sends subtotal only with no setting to switch to order total. Sources: https://support.google.com/merchants/answer/16031492 (2025), https://community.shopify.com/t/google-youtube-app-conversion-value-suddenly-includes-vat-august-vs-september/568656, https://feedarmy.com/kb/google-youtube-app-for-shopify-now-includes-vat-in-conversion-tracking/. Confidence High on subtotalPrice, Med on GST handling.

18. Implication for targets: a Google Ads ROAS computed on GST inclusive, shipping exclusive value sits about 10% above an ex-GST figure and below Shopify "total sales". The conversion action currency should be AUD (set in the action's Value settings: "Use different values for each conversion", default currency Australian Dollar). Triple Whale and Shopify report differently again (R01 brief AOV A$70 TW vs A$85 total sales), so state which basis every target uses. Confidence High.

19. Primary versus secondary: only the channel's Purchase is primary (bidding). Add to cart, Begin checkout, any GA4 import and any Microsoft or Clarity style events are secondary (observation). Source: https://support.google.com/merchants/answer/15457737. Confidence High.

20. Attribution models in Oct 2026: only Data-driven and Last click exist for a conversion action. Google Ads Help states first click, linear, time decay and position based "are no longer supported" and actions on them were upgraded to data-driven; the staged removal began mid July 2023 with a September 2023 cutoff. A cluster of July 2026 vendor posts describes the same four models being removed "by September 2026" with forced migration to data-driven. Either way the menu today offers two choices. Data-driven has no eligibility threshold ("All conversion actions are eligible for data-driven attribution, regardless of conversion or interaction volume") but Google suggests about 200 conversions and 2,000 ad interactions in 30 days for precision; an older page still cites 300 conversions and 3,000 interactions. Sources: https://support.google.com/google-ads/answer/6259715 (current), https://support.google.com/google-ads/answer/6394265 (current), https://support.google.com/google-ads/answer/10762625 (older), https://www.seroundtable.com/google-ads-deprecate-rule-attribution-35194.html (2023), https://rawsoft.com/blog/google-ads-attribution-models-removed-2026 (Jul 2026). Confidence High on the two-model menu, Low on a separate 2026 removal event.

21. Conversion windows: click-through default 30 days, range 1 to 90, Google recommends at least 7; engaged-view default 3 days for web conversions (1 day for Video action, Demand Gen and Performance Max); view-through default 1 day, Display and Video only. Source: https://support.google.com/google-ads/answer/3123169 (current). Confidence High. Recommendation: leave 30 days click-through, 3 days engaged-view; Jake's purchase cycle is short but Christmas gift research runs longer.

### D. ValueTrack and the final URL suffix

22. ValueTrack behaviour by campaign type (Google's table plus practitioner tests): {campaignid}, {adgroupid}, {device} and {network} populate in Search and Shopping. {keyword} populates only in Search; in Shopping and PMax it is empty. {product_id} populates in Shopping (the item ID from the Merchant Center feed, for Shopify "shopify_AU_<productid>_<variantid>"); {product_partition_id} and {targetid} (pla-xxxx) populate in Shopping. {creative} returns the ad ID in Search and Shopping. {matchtype} is Search only. Google states some parameters are "fully supported" in Performance Max and others "limited support" by channel; a 2024 practitioner test found almost nothing populates in PMax except {network} and recommended campaign-level custom parameters as the workaround, while a 2026 guide lists {campaignid}, {adgroupid}, {creative}, {device}, {network} as usable in PMax. Sources: https://support.google.com/google-ads/answer/6305348 (current), https://developers.google.com/google-ads/api/docs/reporting/valuetrack-mapping (current), https://nilsrooijmans.com/daily/performance-max-valuetrack-and-custom-parameters-for-improved-tracking (2024), https://adbrains.ai/resources/valuetrack-parameters-using-dynamic-url-parameters-in-google-ads-2026 (2026). Confidence High for Search and Shopping, Low for PMax.

23. Precedence: a final URL suffix set lower (ad, keyword, ad group, campaign) replaces, not appends to, a higher one (account). So an account-level suffix covers every campaign unless Jake sets a campaign-level one, in which case that campaign must carry the full string. Source: https://developers.google.com/google-ads/api/docs/ads/upgraded-urls/fields, https://support.google.com/google-ads/answer/9054021. Confidence High.

24. Shopping and the channel: Shopping ads take the final URL from the Merchant Center link attribute (Shopify's product URL with ?variant=), and Google appends the suffix with & correctly, so an account-level suffix is the standard way to add UTMs to Shopping. No source shows the Google & YouTube app writing a tracking template or suffix, or stripping one; the gclid thread above shows the real breakage comes from on-site redirects, not from the suffix. One guard: do not include a "variant" or "ref" parameter in the suffix. Sources: https://experienceleague.adobe.com/en/docs/advertising/search-social-commerce/tracking/click-tracking/click-tracking-components/click-tracking-formats/formats-click-tracking-google, https://knowledge.digtective.com/adding-final-url-suffix-to-google-shopping-ads. Confidence Med.

### E. Triple Whale, wholesale exclusion, linking, Customer Match

25. Triple Whale's Google Ads integration connects under Integrations with a Google login holding at least Standard access to the Google Ads account; it pulls campaign spend and conversions by API and attributes site traffic through the Triple Pixel using URL parameters. A valid URL needs one source parameter (utm_source or tw_source), one ad ID parameter (gadid or tw_adid) and one campaign parameter (utm_campaign or tw_campaign). Triple Whale's own template uses tw_source=google&tw_adid={creative}&tw_campaign={campaignid}, and keyword-level attribution adds tw_kwdid={targetid}. Its "automatically add tracking parameters" feature writes to the account; a third-party guide warns it should manage only the final URL suffix and not fight a manual tracking template. Sources: https://kb.triplewhale.com/en/articles/9507702-google-ads-integration, https://kb.triplewhale.com/en/articles/6589378-automatically-add-triple-whale-tracking-parameters-to-your-google-ads, https://kb.triplewhale.com/en/articles/11320696-keyword-level-attribution-search-term-insights, https://clicksambo.com/support-detail/how-to-use-click-sambo-if-you-re-already-using-triple-whale. Confidence High on required parameters, Med on the auto-add behaviour.

26. Wholesale: Triple Whale's Pixel already excludes Shopify draft orders, $0 orders and recurring subscription charges from attribution ("Shopify draft orders, and $0 orders are excluded to avoid inflating performance metrics"), visible under Pixel > All > Excluded. Summary dashboard revenue is separate: use Global Filters (Summary > Business section > filter > Order Tag Name > Does Not Contain "wholesale") which needs a consistent order tag applied to every wholesale draft order in Shopify. Sources: https://triplewhale.readme.io/docs/why-are-some-orders-missing-or-marked-as-excluded-in-the-pixel, https://kb.triplewhale.com/en/articles/11386505-global-filters, https://kb.triplewhale.com/en/articles/9713302-filter-data-on-the-summary-dashboard. Confidence High.

27. GA4 to Google Ads link: GA4 Admin > Product links > Google Ads links > Link > choose the account > enable personalised advertising and auto-tagging. Search Console to Google Ads: Google Ads > Tools > Data manager > Search Console (under Featured products) > Proceed > Link the site; both www and non-www entries; needs Admin on Google Ads and Owner on Search Console. The link enables the Paid and organic report. Sources: https://support.google.com/google-ads/answer/7529561 (current), https://docs.analyzify.com/link-ga4-google-ads-search-console. Confidence High.

28. Customer Match: for Search campaigns a customer list now needs only 100 active matched users in the last 30 days (down from 1,000, change reported 2025), while other Search audiences still need 1,000. Two routes from Shopify: (a) Google Ads > Tools > Data manager > Connect product > Shopify (direct connection, up to 25 lists, Customer Match only), (b) Shopify admin > Customers > Export > CSV, keep Email, First Name, Last Name, Country, Zip columns in Google's header names, upload at Tools > Audience manager > Your data segments > Customer list. Shopify Audiences is not an option (Shopify Plus only). Sources: https://searchengineland.com/google-slashes-customer-match-list-minimums-in-search-campaigns-to-100-users-455912 (2025), https://www.seroundtable.com/google-ads-100-customer-lists-39472.html (2025), https://support.google.com/google-ads-data-manager/answer/15496063, https://support.google.com/google-ads/answer/7361372, https://support.google.com/google-ads/answer/6276125. Confidence High on 100, Med on Data Manager steps. Open point: a brand new Google Ads account may be limited to observation use of Customer Match until it has history; check the policy page at setup.

### F. Known bugs and complaints 2025 to 2026, with fixes

29. Double purchase tags from the app (community 553720): two identical purchase tags per order in Tag Assistant. Fix: confirm there is no second Google tag (theme, custom pixel, GTM), confirm transaction_id is present, raise with Shopify support if it persists; conversions dedupe inside the action if the ID matches. Confidence Med.
30. GCLID stripped by redirect, Mar 2026 (community 591677): only 10% of sales attributed. Fix: land every ad on the canonical URL (https://endlessparks.com/products/ultimate-adventure-bottle), no homepage redirect, check any geolocation or Markets redirect preserves query strings. Confidence High.
31. Conversions dropping after January 2026, Apr 2026 (community 608395, UK): consent banner not passing Google's required signals. Fix for banner regions: certified CMP or correct consent mode defaults; for Australia with no banner, confirm the Customer Privacy API returns all purposes allowed. Confidence Med.
32. Value basis change (community 568656; FeedArmy): conversion value jumped about 21% when the app began sending tax inclusive values. For Endless Parks, prices already include GST, so expect value = GST inclusive subtotal from day one and set targets on that basis. Confidence Med.
33. GA4 ecommerce events missing while page_view works, 2026 (community 583880): GA4 must be connected inside the app, not by a separate tag; in banner regions the app only sends after consent. Confidence Med.
34. Product data overwritten by sync and automatic improvements (community 589194, 2026): edit product data in Shopify (including the Google & YouTube app's product fields for Google category and custom labels) and review Merchant Center > Settings > Automatic improvements. Confidence Med.
35. 18 Aug 2026 app API migration (SERoundtable 41627; Channable): ID rewrites on reinstall. Do not reinstall. Confidence Med.
36. Enhanced conversions via the app reported as intermittent in older threads (community 351258, 2024 to 2025): verify monthly in Diagnostics. Confidence Low.
37. Checkout sandboxing and the end of Additional scripts: GTM tags cannot run on the order confirmation page; purchase tracking must use Customer events. Any legacy Google Ads script pasted into Additional scripts has stopped running. Source: https://stape.io/blog/google-ads-conversion-tracking-for-shopify, https://community.shopify.com/t/enabling-all-events-in-ga4/583880. Confidence High.

### G. Weekly reporting view

38. Google Ads has no native "weekly report" preset; the practical view is a saved column set at campaign level with impression share metrics, which Google reports per campaign type (not account aggregated) with a 1 to 2 day lag. "Search lost IS (budget)" is campaign level only. Columns > Modify columns > Competitive metrics holds Search impr. share, Search lost IS (rank), Search lost IS (budget), Click share (Shopping). Sources: https://support.google.com/google-ads/answer/7103314, https://support.google.com/google-ads/answer/2454071, https://support.google.com/google-ads/answer/11306973. Confidence High. The recommended set is in section 2, step 12.

---

## 2. Step by step verification checklist (pass criteria and menu paths)

Do these in order on the day the Google Ads account is created or found. Each step has a pass line.

1. Channel state. Shopify admin > Sales channels > Google & YouTube > Settings. Pass: Google account shows endlesspks@gmail.com; Merchant Center shows 5382740922; Google Ads shows a customer ID (write it down); Google Analytics shows the property that owns G-M3LTBNJ7H4. Fail: any "Connect" button still showing.

2. Conversion tracking in the app. Same Settings page > Google Ads settings. Pass: conversion tracking is on and the event list shows Purchase mapped to a Google Ads action, with Add to cart and Begin checkout listed. If asked to "Add custom conversion ID/label", do not; use the linked account route.

3. Enhanced conversions. Same page > Google Ads settings > Enhanced conversions > Turn on. Then Google Ads > Goals > Conversions > Settings > Customer data terms > accept, and Enhanced conversions > Turn on > method Google tag. Pass: both sides show on. If the toggle is absent in the app (the April 2026 claim), note it and rely on the Google Ads diagnostics in step 7 to confirm enhanced data is arriving.

4. One primary purchase action. Google Ads > Goals > Conversions > Summary. Pass: exactly one action in the Purchase category is marked Primary and its source is the Google & YouTube app; Add to cart, Begin checkout, Page view, View item and any GA4 import are Secondary; no second Purchase action exists. Fix: open the extra action > Edit settings > Action optimisation > Secondary, or Remove it.

5. Action settings. Open the Purchase action > Edit settings. Pass: Value = Use different values for each conversion, default currency Australian Dollar; Count = Every; Click-through window 30 days; Engaged-view 3 days; Attribution model Data-driven (or Last click if Jake wants Shopify-like reporting); Include in "Conversions" = yes.

6. Auto-tagging. Google Ads > Admin (gear) > Account settings > Auto-tagging. Pass: ticked. Also Merchant Center > Settings > Conversion settings: auto-tagging for free listings on (harmless, helps GA4).

7. Diagnostics. Goals > Conversions > Summary > Purchase > Diagnostics tab. Pass after the test order and 24 hours: tag status Active or Recording conversions; Enhanced conversions status Recording enhanced conversions with a match rate band; Consent section shows no "missing consent signals" warning for AU traffic. Within the first hours "Unverified" is normal.

8. Tag Assistant test order. Open https://tagassistant.google.com > Add domain > https://endlessparks.com > Connect. In the new tab, add a Chug Lid ($15) to cart, check out with the $2.50 letter rate, pay with a real card (refund it afterwards in Shopify; refunds do not reverse the conversion but one test is noise-level). Pass in Tag Assistant: one conversion hit to the Google Ads account with transaction_id equal to the Shopify order number, value 15.00, currency AUD, and user_data present (hashed email) for enhanced conversions; one GA4 purchase event, not two. Fail: two purchase hits (duplicate source), value 17.50 (shipping included, meaning a custom pixel is sending total), or no hit (consent or sandbox issue).

9. UTM and gclid landing test. Google Ads > Admin > Account settings > Final URL suffix > paste the suffix from section 3 > Test. Pass: the test loads the PDP with all parameters and no redirect (address bar still shows the exact URL plus suffix). Then open Shopify admin > Analytics > Sessions by referrer or Online store > Preferences and confirm no country or www redirect exists; if a geolocation app is installed, confirm it keeps query strings.

10. Shopify attribution check. After the first real ad click order: Orders > open order > Conversion summary. Pass: shows google / cpc with the campaign ID in the campaign field. GA4 > Reports > Acquisition > Traffic acquisition also shows google / cpc with the campaign name (from gclid).

11. Triple Whale. Integrations > Google Ads connected to the correct customer ID; Pixel > All > Excluded shows draft orders being filtered; Summary filter set to exclude order tag "wholesale" (and Jake tags every wholesale draft order). Pass: a test order from a Google UTM link appears in Pixel under Google within an hour.

12. Weekly view. Google Ads > Campaigns > Columns > Modify columns, then Save your column set as "EP weekly". Columns: Campaign, Campaign type, Budget, Cost, Impr., Clicks, CTR, Avg. CPC, Conversions, Conv. value, Cost / conv., Conv. value / cost, Search impr. share, Search lost IS (budget), Search lost IS (rank), Click share, Impr. (Abs. Top) %. Segments: Week, then Conversion action to confirm only Purchase sits in the Conversions column. Date range: last 7 days compared with previous period, read on Monday, and reread two weeks later because conversions lag. Every week also open Search terms (Search campaigns) and Products (Shopping) for negatives and zero-impression products, and monthly Auction insights.

Pass criteria for the whole setup: Shopify orders tagged google / cpc for the week equals Google Ads Purchase conversions for the same click dates within about 10%, and Triple Whale Google attributed orders sit within 20% of both.

---

## 3. Exact final URL suffix recommendation

Set at Google Ads > Admin > Account settings > Final URL suffix (one place covers Search, Shopping and PMax):

utm_source=google&utm_medium=cpc&utm_campaign={campaignid}&utm_id={campaignid}&utm_content={creative}&utm_term={keyword}&gadid={creative}&tw_kwdid={targetid}&pid={product_id}

Reasoning:

- It mirrors the Meta pattern key for key (source, medium, campaign, id, content, term). ValueTrack has no campaign name parameter, so utm_campaign carries the ID; GA4 and Shopify still show the campaign name via gclid auto-tagging, and Triple Whale matches on the ID (its own template uses tw_campaign={campaignid}). If Jake wants readable names in Shopify's Conversion summary, override at campaign level with the full string and the literal name, for example utm_campaign=ep_shop_bottle_au&utm_id={campaignid}&utm_content={creative}&utm_term={keyword}&gadid={creative}&tw_kwdid={targetid}&pid={product_id}; remember a campaign-level suffix replaces the account one entirely.
- gadid={creative} is one of the two ad ID parameters Triple Whale recognises; utm_content alone is not in its list. tw_kwdid={targetid} enables Triple Whale keyword-level attribution on Search and returns pla-ids on Shopping. pid={product_id} gives product-level attribution on Shopping and is empty on Search, which is harmless.
- {keyword} is empty on Shopping and PMax, so utm_term will be blank there; that is acceptable and avoids inventing a value.
- No tracking template is needed; parallel tracking means landing-page parameters belong in the suffix. Do not enable Triple Whale's "automatically add tracking parameters" feature; it would write its own parameters and can conflict with this suffix.
- For PMax (not at launch per R01) expect {creative} and {targetid} to be blank in some placements; if a PMax campaign is ever added, set a campaign-level suffix with literal utm_campaign and utm_content values.
- Shopping safety: Shopify product URLs already carry ?variant=; Google joins the suffix with &. The suffix contains no variant, ref, discount or redirect parameter, so Shopify's URL handling is unaffected.

---

## 4. Where sources disagree

1. Enhanced conversions toggle in the app: Google Ads Help and Merchant Center Help (current) say turn it on under Google Ads settings; tagassists.com (2026) says the toggle was removed in April 2026 and the feature is automatic. My read: trust Google's pages, check the app, and in either case verify via Diagnostics.
2. Attribution model removal date: Google Ads Help and 2023 trade press say the four rule-based models were removed in 2023; a cluster of July 2026 vendor posts says July to September 2026. My read: the 2026 posts are recycled or describe a final sweep of stragglers; the menu today shows only Data-driven and Last click, which is what matters.
3. Data-driven attribution thresholds: current help says no threshold with 200 conversions and 2,000 interactions suggested; an older help page says 300 and 3,000 for some action types. My read: no threshold applies; at A$30/day data-driven will run but behave close to last click.
4. Data Manager Shopify purchase import: the current Data Manager page says conversions are not supported; an older Google Ads copy says purchases from "Checkout completed" are imported and deduplicated. My read: Customer Match only in Oct 2026; the app is the purchase source.
5. Conversion value basis: Google's FAQ says subtotalPrice (post discount, pre shipping); a community thread says the value became tax inclusive; a January 2026 review says subtotal only. These are consistent for a tax inclusive store: subtotal includes GST and excludes shipping.
6. PMax ValueTrack: 2024 test says nothing populates; 2026 guide says {campaignid}, {adgroupid}, {creative}, {device}, {network} work. My read: untested in 2026 primary docs; irrelevant at launch.
7. Consent mode in the app: Shopify says the app activates Consent Mode v2 for EEA; a developer forum says the app pushes "default granted" everywhere without a banner, and one vendor says the app has no consent mode at all. My read: the app sets defaults and updates them from Shopify's Customer Privacy API; with no AU banner the state is granted, which is the intended outcome for Endless Parks.
8. Customer Match minimum: 100 (current, Search customer lists) versus 1,000 (older pages). My read: 100.

---

## 5. Open questions for Jake

1. Does a Google Ads account already exist under endlesspks@gmail.com, and does the Google & YouTube app Settings page show conversion tracking on today? (Determines whether steps 2 to 5 are "verify" or "create".)
2. Are there any custom pixels under Settings > Customer events (Google, GTM, Klaviyo, Clarity, Triple Whale) and do any of them send a Google Ads conversion? Needed to rule out duplicates before the test order.
3. Is the Shopify cookie banner active in any region (Settings > Customer privacy > Cookie banner > Regions)? Recommended: off for Australia, on only for EEA and UK if those markets are active.
4. Do wholesale draft orders carry a consistent order tag (for example "wholesale")? Triple Whale's Summary filter and any Shopify report depend on it.
5. Does the Triple Whale account already have the Google Ads integration connected, and is "automatically add tracking parameters" switched on? If on, turn it off before setting the suffix.
6. Does Jake want conversion value reported GST inclusive (what the app sends) or ex GST? This sets the ROAS and tROAS numbers in R01 (A$87 bottle reports 87.00, ex GST would be 79.09).
7. Any redirect apps or Markets settings that redirect visitors by country? These are the known gclid killers.
8. Has the privacy policy page been updated to list Google Ads, Meta, Triple Whale and Clarity, and retargeting, in line with the OAIC pixel guidance?

---

## 6. Sources

Google and Shopify documentation
- https://support.google.com/merchants/answer/13494537 Set up conversion tracking with the Google & YouTube app on Shopify
- https://support.google.com/merchants/answer/15457737 Understand the conversion actions tracked in Google Ads
- https://support.google.com/google-ads/answer/15496063 Shopify (Google Ads Help, enhanced conversions steps)
- https://support.google.com/google-ads-data-manager/answer/15496063 Shopify (Data Manager Help)
- https://support.google.com/merchants/answer/16031492 FAQ about migrating to the Google & YouTube app (subtotalPrice, April 2025 discount fix)
- https://support.google.com/google-ads/answer/16030792 Install and migrate your tags with the Google & YouTube app
- https://support.google.com/google-ads/answer/16138144 Verify your upgrade to the Google & YouTube app
- https://support.google.com/analytics/answer/12183125 Shopify: set up your Google tag
- https://support.google.com/merchants/answer/17252069 Merchant Center Next is now Merchant Center (Jul 2026)
- https://support.google.com/merchants/answer/15285007 Upgrading all retailers to Merchant Center Next (2024)
- https://support.google.com/google-ads/answer/6305348 ValueTrack parameters
- https://developers.google.com/google-ads/api/docs/reporting/valuetrack-mapping ValueTrack to report fields
- https://developers.google.com/google-ads/api/docs/ads/upgraded-urls/fields Upgraded URL fields (precedence)
- https://support.google.com/google-ads/answer/9054021 Add a final URL suffix
- https://support.google.com/google-ads/answer/3095550 About auto-tagging
- https://support.google.com/google-ads/answer/10989978 Tag Assistant for unverified or inactive conversion actions
- https://support.google.com/google-ads/answer/1722022 About conversion measurement (statuses)
- https://support.google.com/google-ads/answer/11956168 Enhanced conversions for web tag diagnostics report
- https://support.google.com/google-ads/answer/6259715 About attribution models
- https://support.google.com/google-ads/answer/6394265 About data-driven attribution
- https://support.google.com/google-ads/answer/10762625 About Switch to DDA
- https://support.google.com/google-ads/answer/3123169 About conversion windows
- https://support.google.com/google-ads/answer/7529561 Link Search Console and Google Ads
- https://support.google.com/google-ads/answer/7361372 Use a partner to create a Customer Match list
- https://support.google.com/google-ads/answer/6276125 Create a customer list
- https://support.google.com/google-ads/answer/7103314 Get impression share data
- https://support.google.com/google-ads/answer/2454071 About columns in your statistics table
- https://support.google.com/google-ads/answer/11306973 Custom column examples
- https://help.shopify.com/en/manual/privacy-and-security/privacy/customer-privacy-settings/understanding-customer-privacy-settings
- https://help.shopify.com/en/manual/privacy-and-security/privacy/customer-privacy-settings/privacy-settings
- https://help.shopify.com/en/manual/promoting-marketing/pixels/custom-pixels/gtm-tutorial
- https://help.shopify.com/en/manual/promoting-marketing/pixels/custom-pixels/code
- https://shopify.dev/docs/api/customer-privacy
- https://shopify.dev/docs/api/web-pixels-api/pixel-privacy
- https://changelog.shopify.com/posts/customer-data-collection-update

Triple Whale
- https://kb.triplewhale.com/en/articles/9507702-google-ads-integration
- https://kb.triplewhale.com/en/articles/6589378-automatically-add-triple-whale-tracking-parameters-to-your-google-ads
- https://kb.triplewhale.com/en/articles/11320696-keyword-level-attribution-search-term-insights
- https://kb.triplewhale.com/en/articles/11386505-global-filters
- https://kb.triplewhale.com/en/articles/9713302-filter-data-on-the-summary-dashboard
- https://triplewhale.readme.io/docs/why-are-some-orders-missing-or-marked-as-excluded-in-the-pixel

Community and press (2025 to 2026)
- https://community.shopify.com/t/google-ads-and-shopify-not-picking-up-conversion-data-gclid-issue/591677 (Mar 2026)
- https://community.shopify.com/t/google-ads-conversions-dropping-disappearing-after-january-shopify-tracking-issue/608395 (Apr 2026)
- https://community.shopify.com/t/the-google-youtube-app-is-firing-two-identical-purchase-tags-to-different-urls-why/553720
- https://community.shopify.com/t/google-youtube-app-conversion-value-suddenly-includes-vat-august-vs-september/568656
- https://community.shopify.com/t/enabling-all-events-in-ga4/583880 (2026)
- https://community.shopify.com/t/shopify-google-merchant-center-sync-disaster-191-skus-wiped-attributes-overwritten-nothing-updating-losing-my-mind/589194 (2026)
- https://community.shopify.com/t/enhanced-conversion-tracking-for-google-and-youtube-app/351258
- https://community.shopify.dev/t/web-pixel-google-youtube-app-always-pushing-default-granted/23016
- https://community.shopify.dev/t/shopify-pixels-shopify-consent-banner-and-google-consent-mode-v2/2123
- https://www.seroundtable.com/google-youtube-shopify-app-sync-merchant-concerns-41627.html (Aug 2026)
- https://www.channable.com/blog/shopify-google-youtube-app-migration (2026)
- https://searchengineland.com/google-drops-next-from-merchant-center-next-481882 (Jul 2026)
- https://searchengineland.com/google-slashes-customer-match-list-minimums-in-search-campaigns-to-100-users-455912 (2025)
- https://www.seroundtable.com/google-ads-100-customer-lists-39472.html (2025)
- https://www.seroundtable.com/google-ads-deprecate-rule-attribution-35194.html (2023)
- https://rawsoft.com/blog/google-ads-attribution-models-removed-2026 (Jul 2026)
- https://www.allens.com.au/insights-news/insights/2026/07/tracking-pixels-targeted-advertising-and-compliance-lessons-from-recent-oaic-determinations/ (Jul 2026)
- https://www.claytonutz.com/insights/2026/july/oaic-determines-the-use-of-tracking-pixels-did-not-track (Jul 2026)
- https://privacymatters.dlapiper.com/2026/06/australia-pixel-perfect-the-regulator-addresses-use-of-tracking-pixels/ (Jun 2026)
- https://ppc.land/australia-would-force-ad-tech-to-get-consent-before-sharing-pixels/ (Sep 2026)

Practitioner guides (secondary)
- https://weltpixel.com/blogs/news/running-a-tracking-app-alongside-shopifys-google-and-youtube-channel (2026)
- https://weltpixel.com/blogs/news/google-ads-conversion-tracking-on-shopify-complete-2026-guide (2026)
- https://weltpixel.com/blogs/news/ga4-key-events-vs-conversions-on-shopify-what-the-2024-rename-changed (2026)
- https://attribuly.com/blogs/google-enhanced-conversions-shopify-setup/ (26 Apr 2026)
- https://tagassists.com/blog/google-ads-shopify-conversion-tracking/ (2026)
- https://stape.io/blog/google-ads-conversion-tracking-for-shopify (2026)
- https://nilsrooijmans.com/daily/performance-max-valuetrack-and-custom-parameters-for-improved-tracking (2024)
- https://adbrains.ai/resources/valuetrack-parameters-using-dynamic-url-parameters-in-google-ads-2026 (2026)
- https://clicksambo.com/support-detail/how-to-use-click-sambo-if-you-re-already-using-triple-whale
- https://feedarmy.com/kb/google-youtube-app-for-shopify-now-includes-vat-in-conversion-tracking/
- https://petersutarik.com/blog/import-ga4-conversions-google-ads/ (2025)
- https://docs.analyzify.com/link-ga4-google-ads-search-console
