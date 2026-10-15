# P5. Landing pages, site hygiene and conversion rate for Google traffic (15 Oct 2026)

Lens: where Google clicks land on endlessparks.com, what can break tracking or approval before launch, and what the bottle PDP needs for cold traffic. Builds on `02-conversion-tracking.md` (gclid), `03-feed-fixes.md` Step 4 (business information) and `06-launch-and-optimise.md` item 12 (stale pages). Method: 20 extended web searches on 15 Oct 2026. Direct page loads are blocked here, so Help wording is quoted from search extracts and single-source claims are marked. The live store could not be loaded: every "current state" item is a check for Jake.

## 1. Findings

1. **The Shopping landing page is fixed by the feed link, not chosen in Google Ads.** The link must open the exact item at the feed price; a product page with an unselected colour is "a leading cause of disapprovals" and the price tolerance is "exactly the same" (Store Growers link attribute guide, 2026; Merchant Center product data specification 7052112). The Shopify Google & YouTube channel builds one row per variant with a `?variant=<id>` link (GoDataFeed documents the pattern). Confidence High on the rule, Medium on the channel's link format (verify one row in Merchant Center).

2. **Google crawls each feed link and corrects or disapproves a price that differs from the page.** Automations are "enabled by default", read price, availability and condition from structured data, and "updates only happen when Google crawls your landing page" (Merchant Center Help 12157888; fix page 14916353). Single secondary sources add that frequently changing prices can be disapproved rather than corrected (ecommerceparadise.com) and that one cent of rounding is enough (GMC Guardian). Confidence High on the mechanism, Low on both.

3. **The stale A$58 and A$63 pages are a Search and trust problem more than a Merchant Center one.** Google checks the feed link, not every page on the domain, so an old marketing page cannot disapprove the bottle. The risks: a Search ad, sitelink or theme link pointing at /pages/adventurebottle; brand searchers seeing "$58.00" or "$63.00 sold out" in a snippet and arriving at A$87; and the PDP's structured data disagreeing with its visible price (finding 10). Confidence High that the index is inconsistent (R09 finding 6), Medium on the live state.

4. **Shopify redirects only fire from URLs that would otherwise 404.** Shopify Help: "you can redirect only from broken URLs", and the fixed /products and /collections roots cannot be redirected. Path: Online Store > Navigation > View URL redirects > Create URL redirect (LOGEIX, byRadiant; one guide routes through Settings > Apps and sales channels). Only 301s are issued (one source). So /pages/adventurebottle must be deleted or hidden first, and /collections/all cannot be redirected at all. Confidence High on the rule, Medium on the label.

5. **Re-indexing is URL Inspection plus a sitemap, with a daily cap.** Search Console Help: for many pages "submit a sitemap, with the updated pages marked by lastmod"; for a few, URL Inspection > Test live URL > Request indexing (Help 9012289). Quota about 10 to 12 URLs a day, turnaround three to five days (IndexVero, 2026, secondary). Removals > Clear cached URL drops the snippet until the next crawl (practitioner knowledge). Confidence High on the tool, Medium on quota and timing.

6. **Shopify's country redirect lives in Online Store > Preferences, and nobody documents whether it keeps gclid.** Shopify Help: "Country/region" under "Automatic redirection"; a dedicated domain, subdomain or subfolder market redirects to that market's URL, a shared domain only switches currency; "automatic redirection only applies to the first page that a customer visits", which is the ad landing page. The 2026 guides disagree: missinglinkz.io says Markets geo-routing "may drop query strings"; sherocommerce.com says native redirects preserve UTMs and blames apps and custom Liquid. Neither mentions gclid. Confidence High on the setting, Low on parameter behaviour: test it (section C).

7. **Core Web Vitals on a Shopify PDP: LCP and INP fail, and only some causes are in Jake's hands.** Thresholds LCP 2.5 s, INP 200 ms, CLS 0.1 at the 75th percentile of field data; field and lab "can disagree" (corewebvitals.io, 1Digital, webvitals.tools, 2026). The LCP element "is the hero banner or the primary product photo"; INP comes from app JavaScript on "variant switchers, cart drawers, collection filters and product forms"; audit by "disabling apps one at a time". Not fixable: server response, checkout, core theme JS. Landing page experience still scores relevance, transparency, navigation and speed, with no announced Quality Score change by June 2026 (3-prime.com, myleadsfactory.com, secondary). Confidence High on thresholds, Medium on the rest.

8. **Destination policy: the page must work on common devices, be reachable by AdsBot, and not be thin or a placeholder.** Destination requirements (adspolicy 6368661) disapproves pages that "don't function properly or have been set up incorrectly". Insufficient original content is now its own page (adspolicy 16427718) covering scraped and template pages plus "under construction" placeholders, moved there in 2025 (Search Engine Journal). A sold out marketing page with no buy button is the nearest risk. Confidence High, Medium on the 2025 move.

9. **Merchant Center's site checks are "Editorial and professional requirements" in three areas** (Help 6150244): functionality ("free of broken links or placeholders, accessible without login requirements"), transparency ("clear contact information, business details and a complete return and refund policy") and purchase integrity (customers "can complete a purchase and checkout without technical blocks"). Misrepresentation suspends "upon detection and without prior warning" (Metricfixer quoting the policy). Practitioners add that address, phone and email must match Merchant Center > Business information exactly and that a domain email beats Gmail (adreinstate.com, anowave.com). Advertiser verification moved in January 2026 to an "Account" hub under Admin with no status change (PPC News Feed). Confidence High on Google wording, Medium on the rest.

10. **PDP elements for cold traffic rest on practitioner consensus, not controlled studies.** Consistent advice: star rating and count beside title and price; shipping cost or free threshold, delivery estimate and return window "next to the Add to Cart button, not at checkout"; price above the fold (Shopify blog, Yotpo, mgroupweb, 2026). Figures such as "10 plus reviews convert 52 per cent higher" are uncited vendor claims; no 2025 or 2026 Baymard report surfaced. Duplicate Product schema (theme plus Judge.me plus an SEO app) is the usual Shopify cause of a page crawl mismatch, and theme updates reintroduce it (vitalitynode.com, Shopify community 269961). Confidence Medium on elements, Low on numbers.

11. **Dedicated landing pages: no for Shopping, no for bottle Search, maybe for gift Search.** Shopping must land on the item at the feed price (finding 1). The only near first-party Search evidence is Practical Ecommerce: "conversion rates were significantly higher when the product mix on the page immediately matched the shopper's query"; agency tables put product-specific search on the product page and "comparing options" on a category page (thegood.com, checkoutchamp.com); the case for custom pages comes only from landing page vendors. A gift guide "works well for paid traffic because it shows several products at different price points" and should be a manual collection (Sutton Commerce, Growth Suite, 2026). Confidence Medium.

12. **Australia Post 2026 cut-offs.** Parcel Post 21 Dec interstate, 22 Dec same state; Express 23 Dec most states, 22 to 23 Dec WA; "a few extra days" to or from WA and regional areas (SBS and Yahoo quoting Australia Post, Oct 2026; auspost.com.au). Shipping from Perth to east coast customers, `07-calendar.md` already uses 16 Dec standard and 20 Dec Express; those are the banner dates. Confidence High.

## 2. Exactly what to do for Endless Parks

Order: A and B this week, C and G before the conversion test (22 to 24 Oct), D and E before launch, F by 15 Nov.

### A. Lock the landing URL (30 minutes)

| Step | Where | Pass |
|---|---|---|
| A1 | Merchant Center 5382740922 > Products > a bottle variant > Final attributes > link | `https://www.endlessparks.com/products/ultimate-adventure-bottle?variant=<id>`, claimed domain, no `currency=` or other stray parameter (strip with Products > Attribute rules > link) |
| A2 | Open the three variant links in incognito | https, matching colour pre-selected, A$87.00, Add to cart enabled, no redirect, no popup over the price |
| A3 | Rich Results Test (search.google.com/test/rich-results) on the PDP | One Product entity, one Offer per variant, price 87.00 AUD, InStock. Two Product blocks: switch off Judge.me's schema (Judge.me > Settings > Integrations) or the theme's, not both |
| A4 | Google Ads > every Search ad, sitelink and asset final URL | Canonical PDP without `?variant=`; never /pages/adventurebottle or /collections/all |

### B. Kill the stale prices (45 minutes, then 3 to 10 days for Google)

| Step | Where | Pass |
|---|---|---|
| B1 | Load /pages/adventurebottle, /collections/all and /collections/australias-ultimate-adventure-bottle in incognito | Record price, sold out state, buy button |
| B2 | If stale: Online Store > Pages > adventurebottle > Delete (or Visibility: Hidden). Then Online Store > Navigation > View URL redirects > Create URL redirect: from `/pages/adventurebottle`, to `/products/ultimate-adventure-bottle` > Save | Old URL lands on the PDP at A$87 in one hop (one 301, then 200) |
| B3 | If worth keeping: edit the page so price, stock and button match the PDP | Same price and availability |
| B4 | /collections/all cannot be redirected. Confirm A$87, then Search Console > URL Inspection > Test live URL > Request indexing; repeat for the homepage and the old collection | "Indexing requested"; snippet re-checked in 5 to 10 days; under 10 requests a day |
| B5 | Search Console > Removals > Clear cached URL for the two stale URLs; Sitemaps shows /sitemap.xml read this week | Status Processed; old price snippet gone within days |

### C. Prove gclid survives (20 minutes)

| Step | Where | Pass |
|---|---|---|
| C1 | Shopify > Online Store > Preferences > Automatic redirection | Country/region off, or on with every market on the primary domain. Screenshot |
| C2 | Shopify > Settings > Markets > each market > Domains and languages | All on endlessparks.com, no subfolder or subdomain (a subfolder for NZ or International fires the first-page redirect for anyone geolocated outside Australia) |
| C3 | Shopify > Settings > Apps and sales channels | No geolocation or redirect app; if one exists, find its "keep URL parameters" option or remove it |
| C4 | Phone on mobile data, incognito: `https://www.endlessparks.com/products/ultimate-adventure-bottle?gclid=TEST123&utm_source=google&utm_medium=cpc` | Both parameters still in the address bar after the page settles |
| C5 | Repeat C4 through a VPN exit in NZ or the US | Same URL, parameters intact. A currency switch is fine; a URL change or dropped parameter is the March 2026 failure (R02-R07 finding 30) |

### D. Speed, only what a theme can fix (1 hour)

| Step | Where | Pass |
|---|---|---|
| D1 | pagespeed.web.dev > PDP URL > Mobile | Field LCP under 2.5 s, INP under 200 ms, CLS under 0.1. Record lab LCP and Total Blocking Time as baseline |
| D2 | Search Console > Experience > Core Web Vitals > Mobile | No Poor URLs. If the site is too small for field data, use D1 lab: LCP under 3 s, TBT under 600 ms |
| D3 | Shopify > Products > bottle > Media | First image per colour under 200 KB, at most 1600 px wide; theme image preload on if offered |
| D4 | Online Store > Themes > Customise > App embeds, and Settings > Apps | Switch off every embed not used on the PDP; re-run D1 after each; keep only changes that cut TBT or INP |
| D5 | Judge.me widget and Klaviyo popup | Widget below the fold with reserved height; popup after 8 seconds or on exit, never over the price on load |

### E. PDP elements for cold Google traffic (2 hours in the theme editor)

| Element | Set to | Why |
|---|---|---|
| Price | A$87.00 beside the title on a 390 px phone, same number as the feed, no "from" price | 1, 2 |
| Shipping line | "Ships from Perth. Standard A$14, 2 to 8 business days. Free standard shipping on orders over A$120. Express A$19." A shipping condition, not sale language (`PLAN.md` question 8) | 10 |
| Returns line | "30 day returns", linked to /policies/refund-policy | 9, 10 |
| Review stars | Judge.me badge "4.89 from 99 reviews" under the title; full widget lower | 10 |
| Colour swatches | Deep Ocean, Forest, Sand with names and per-swatch stock; the feed variant pre-selects (A2) | 1 |
| Bundle pricing | If Jake allows it on site: "Buy 2, 20 per cent off. Buy 3, 30 per cent off, applied in the cart." Keep the schema Offer price at 87.00; never show a discounted unit price | 2 |
| Above the fold copy | "1.2 L insulated bottle showing Australia's National and Marine Parks. 45 park stickers included. Hand drawn in Perth." Matches `05-ad-copy.md` | 11 |
| Trust block | Australian owned, Perth warehouse address; Australian Made logo on tee pages only once the licence is confirmed | 9 |
| December banner | From 20 Nov: "Order by Wed 16 Dec for standard delivery before Christmas (east coast metro), Sun 20 Dec for Express" | 12 |

### F. Gift collection page for the gifts ad group (1 hour, live by 15 Nov)

1. Shopify > Products > Collections > Create collection, manual, handle `gifts-for-adventurers`, title "Gifts for Campers, Hikers and Road Trippers". Order: bottle (three colours), the three State Adventure Mugs, The Iconic 45 sticker pack, one tee. Mugs and stickers are out of paid Shopping, but a Search landing page can show them.
2. Description, first two lines visible on mobile: "Gifts for people who love Australia's National and Marine Parks. Ships from Perth, free standard shipping over A$120, 30 day returns." December banner below it; price, swatches and Judge.me stars on each card.
3. Final URL for the gift ad group in `ep_srch_nonbrand_au_2026q4` ("gifts for grey nomads", "gifts for campers", "road trip gifts australia"). Bottle queries keep the PDP.
4. GA4 > Reports > Engagement > Landing page, google / cpc: if the collection's purchase rate trails the PDP's after 200 gift clicks, send the gift group back to the PDP.

### G. Policy checks on the site (30 minutes)

| Check | URL | Pass |
|---|---|---|
| Contact | /pages/contact and the footer | Business name, domain email (not Gmail), phone, 4/16 Ledgar Rd, Balcatta WA 6021, matching Merchant Center > Settings > Business information exactly |
| Shipping policy | /policies/shipping-policy in the footer | A$14 standard 2 to 8 days, A$19 express 1 to 4, free over A$120, A$2.50 sticker letters, NZ and overseas rates; same as Merchant Center > Shipping and returns |
| Refund policy | /policies/refund-policy in the footer | 30 day window, how to start a return, who pays return postage, refund timing, contact method |
| Privacy and terms | /policies/privacy-policy, /policies/terms-of-service | Published from Shopify > Settings > Policies, in the footer |
| Checkout | Add the bottle, checkout as an AU guest, stop before paying | No login wall, https, AU address accepted, shipping options and GST inclusive total shown |
| Crawlability | /robots.txt | Shopify default; nothing blocks AdsBot-Google or Googlebot |
| No placeholders | Every footer and menu link | No "coming soon", empty or sold out marketing pages |
| Verification | Google Ads > Admin > Account (was Advertiser verification before Jan 2026) | Started day one, documents matching the payments profile name |

## 3. Where sources disagree

- **Redirects and query strings.** missinglinkz.io says Markets geo-routing may drop query strings; sherocommerce.com says native redirects preserve UTMs and only apps strip them. Neither tests gclid; Shopify Help is silent. C4 and C5 decide it.
- **Where the settings live.** The lens says Settings > Markets; Shopify Help puts Automatic redirection under Online Store > Preferences, with domains under Settings > Markets. URL redirects: Online Store > Navigation (most guides) versus Settings > Apps and sales channels (one guide). Check both.
- **Automations default.** Help says on by default; one guide says switch it on. Confirm under Merchant Center > Settings > Automations.
- **Parcel Post date.** 21 Dec interstate and 22 Dec same state versus one SBS line saying 21 Dec for all. The banner uses 16 Dec, so it does not matter.
- **Dedicated landing pages and PDP statistics.** Landing page vendors say product pages under-convert paid traffic; CRO consultancies put product intent on the product page. No controlled test, and every PDP conversion number found is an uncited vendor claim; the plan follows intent and ignores the numbers.

## 4. Open questions for Jake

1. What does /pages/adventurebottle show today? Delete and redirect (B2) or update (B3)?
2. Do the NZ and International markets use the primary domain or a subfolder (C2)? Any geolocation app (C3)?
3. Which Judge.me plan, and does the theme already print Product schema (A3)?
4. Is the "Buy 2, 20 per cent off, buy 3, 30 per cent off" line acceptable on the PDP? Feed and ads stay at A$87 regardless.
5. Is there a domain email and phone for the footer and Merchant Center, matching the payments profile?
6. Which theme and version is live, and what does Online Store > Themes show as the speed score?
7. Are mugs and stickers allowed on the gift collection page, and does the 16 Dec and 20 Dec banner also go on the homepage?

## 5. Sources

- Merchant Center product data specification: https://support.google.com/merchants/answer/7052112
- Merchant Center Automations: https://support.google.com/merchants/answer/12157888
- Fix: Automatic updates, mismatched price: https://support.google.com/merchants/answer/14916353
- Editorial and professional requirements: https://support.google.com/merchants/answer/6150244
- Destination requirements: https://support.google.com/adspolicy/answer/6368661
- Insufficient original content: https://support.google.com/adspolicy/answer/16427718
- Search Console URL Inspection: https://support.google.com/webmasters/answer/9012289
- Shopify URL redirects: https://help.shopify.com/en/manual/online-store/menus-and-links/url-redirect
- Shopify automatic redirection: https://help.shopify.com/en/manual/international/automatic-redirection
- Shopify directing customers by region: https://help.shopify.com/en/manual/markets/international-domains/directing-customers
- Store Growers link attribute (2026): https://www.storegrowers.com/link-attribute/
- GoDataFeed Shopify variant URLs: https://help.godatafeed.com/hc/en-us/articles/115002065588
- Shopify community, mismatched value page crawl: https://community.shopify.com/t/how-to-resolve-mismatched-value-page-crawl-issue-on-google-merchant-centre/269961
- GMC Guardian price discrepancy: https://gmcguardian.com/en/fix/price-discrepancy/
- ecommerceparadise fast-changing prices: https://ecommerceparadise.com/google-may-disapprove-fast-changing-prices/
- LOGEIX Shopify redirects: https://logeix.com/blog/shopify-redirects
- byRadiant Shopify redirects: https://byradiant.com/blog/shopify-redirects-guide
- IndexVero URL Inspection (2026): https://indexvero.com/blog/indexing-basics/url-inspection-tool/
- missinglinkz UTM tracking for Shopify (2026): https://missinglinkz.io/blog/utm-builder-shopify/
- Shero Commerce UTM standards (2026): https://sherocommerce.com/blogs/insights/shopify-utm-tracking-standards
- corewebvitals.io Shopify guide (2026): https://www.corewebvitals.io/core-web-vitals/shopify-guide
- 1Digital Shopify CWV benchmarks (2026): https://www.1digitalagency.com/blog/core-web-vitals-for-shopify-stores-2026-benchmarks-and-optimization-playbook-33932/
- webvitals.tools checklist (2026): https://webvitals.tools/blog/shopify-core-web-vitals-checklist-2026/
- 3-prime landing page experience (Mar 2026): https://www.3-prime.com/2026/03/improving-landing-page-experience-and-quality-score-for-google-ads/
- myleadsfactory Quality Score 2026: https://myleadsfactory.com/blog/google-ads-quality-score-2026
- Search Engine Journal destination policy update: https://www.searchenginejournal.com/google-ads-updates-destination-requirements-policy/439612/
- Metricfixer misrepresentation audit: https://metricfixer.com/publications/online-advertising/merchant-center-misrepresentation-audit-guide
- AdReinstate checklist: https://adreinstate.com/blog/merchant-center-misrepresentation-checklist
- Anowave misrepresentation: https://www.anowave.com/quicks/fixing-google-merchant-center-misrepresentation-suspension/
- PPC News Feed, verification renamed (Jan 2026): https://ppcnewsfeed.com/ppc-news/2026-01/advertiser-verification-renamed-as-account-in-google-ads/
- Shopify blog product pages (2026): https://www.shopify.com/blog/product-page
- Yotpo Shopify conversion (2026): https://www.yotpo.com/blog/increase-shopify-conversion-rate/
- mgroupweb PDP optimisation (2026): https://mgroupweb.com/blogs/shopify-product-page-optimization/
- The Good, landing vs product page: https://thegood.com/insights/landing-page-vs-product-page/
- Checkout Champ, landing vs product page: https://checkoutchamp.com/media/when-to-use-a-landing-page-vs-a-product-page-and-why-it-matters-186
- Practical Ecommerce listing match: https://www.practicalecommerce.com/?p=3452
- Sutton Commerce gift guide: https://www.suttoncommerce.co.uk/blog/how-to-create-a-shopify-gift-guide-that-drives-seasonal-traffic
- Growth Suite gift guide (2026): https://www.growthsuite.net/resources/shopify-holiday-campaigns/christmas-holiday-season/gift-guide-that-converts
- Australia Post Christmas dates: https://auspost.com.au/sending/christmas-sending-dates
- SBS Australia Post cut-offs 2026: https://www.sbs.com.au/news/article/australia-post-christmas-cut-off-dates-2026/54hwr4304
- vitalitynode Shopify JSON-LD errors: https://vitalitynode.com/gmc-fixes/shopify-json-ld-schema-errors-google-shopping/
