# 10. Landing pages and site hygiene for Google traffic

Where Google clicks land, what can break tracking or approval before launch, and what the bottle page needs for cold traffic. Full research in `research/phase2/P5-landing-pages.md`. Order: A and B this week, C and G before the conversion test, D and E before launch, F by 15 Nov.

Facts that drive this: Shopping ads land on the feed's own link (the product page with ?variant=), never a URL chosen in Google Ads, and Google compares that page's price with the feed; Shopify URL redirects only fire from URLs that would otherwise 404, so a stale page must be deleted or hidden before it can be redirected; Shopify's country redirection fires on the first page a visitor opens, which is the ad landing page, and nobody documents whether it keeps gclid, so it is tested rather than trusted.

## A. Lock the landing URL (30 minutes)

| Step | Where | Pass |
|---|---|---|
| A1 | Merchant Center > Products > a bottle variant > Final attributes > link | https://www.endlessparks.com/products/ultimate-adventure-bottle?variant=<id>, no stray currency or ref parameter |
| A2 | Open the three variant links in an incognito window | https, matching colour pre selected, A$87.00, Add to cart enabled, no redirect, no popup over the price |
| A3 | search.google.com/test/rich-results on the PDP | One Product entity, one Offer per variant, price 87.00 AUD, InStock. Two Product blocks (theme plus Judge.me) means switch off one schema source, not both |
| A4 | Every Search ad, sitelink and asset final URL | The canonical PDP without ?variant=; never /pages/adventurebottle or /collections/all |

## B. Kill the stale prices (45 minutes, then 3 to 10 days for Google)

| Step | Where | Pass |
|---|---|---|
| B1 | Load /pages/adventurebottle, /collections/all and /collections/australias-ultimate-adventure-bottle in incognito | Record price, sold out state, buy button |
| B2 | If the page is stale (Jake decides, it may be a Meta destination): Online Store > Pages > adventurebottle > hide or delete, then Online Store > Navigation > View URL redirects > Create: from /pages/adventurebottle to /products/ultimate-adventure-bottle | The old URL lands on the PDP at A$87 in one hop |
| B3 | If worth keeping: edit the page so price, stock and button match the PDP | Same price and availability |
| B4 | /collections/all cannot be redirected. Confirm A$87, then Search Console > URL Inspection > Test live URL > Request indexing for it, the homepage and the old collection (about 10 requests a day) | "Indexing requested"; snippets re checked in 5 to 10 days |
| B5 | Search Console > Removals > Clear cached URL for the stale URLs | Processed; the old price snippet disappears within days |

Merchant Center does not check these pages (it checks the feed link), so this is about brand searchers and Search ads, not a launch blocker.

## C. Prove gclid survives (20 minutes, before the conversion test)

| Step | Where | Pass |
|---|---|---|
| C1 | Shopify > Online Store > Preferences > Automatic redirection | Country/region redirection off, or on with every market on the primary domain. Screenshot |
| C2 | Settings > Markets > each market > Domains and languages | All on endlessparks.com; no subfolder or subdomain for NZ or International |
| C3 | Settings > Apps and sales channels | No geolocation or redirect app; if one exists, find its keep URL parameters option or remove it |
| C4 | Phone on mobile data, incognito: https://www.endlessparks.com/products/ultimate-adventure-bottle?gclid=TEST123&utm_source=google&utm_medium=cpc | Both parameters still in the address bar after the page settles |
| C5 | Repeat C4 through a VPN exit in New Zealand or the US | Same URL, parameters intact; a currency switch is fine, a URL change or a dropped parameter is the March 2026 failure |

## D. Speed, only what a theme can fix (1 hour)

| Step | Where | Pass |
|---|---|---|
| D1 | pagespeed.web.dev, the PDP, Mobile | Field LCP under 2.5 s, INP under 200 ms, CLS under 0.1; record lab LCP and Total Blocking Time |
| D2 | Search Console > Experience > Core Web Vitals > Mobile | No Poor URLs. Too little field data: lab LCP under 3 s, TBT under 600 ms |
| D3 | Products > bottle > Media | First image per colour under 200 KB and at most 1600 px wide |
| D4 | Online Store > Themes > Customise > App embeds | Switch off every embed not used on the PDP, re run D1 after each, keep only changes that cut TBT or INP |
| D5 | Judge.me widget and Klaviyo popup | Widget below the fold with reserved height; popup after 8 seconds or on exit, never over the price on load |

## E. PDP elements for cold Google traffic (2 hours in the theme editor)

| Element | Set to |
|---|---|
| Price | A$87.00 beside the title on a 390 px phone, the same number as the feed, no "from" price |
| Shipping line | "Ships from Perth. Standard A$14, 2 to 8 business days. Free standard shipping on orders over A$120. Express A$19." |
| Returns line | "30 day returns", linked to /policies/refund-policy |
| Review stars | Judge.me badge "4.89 from 99 reviews" under the title; the full widget lower |
| Colour swatches | Deep Ocean, Forest, Sand, named, per swatch stock; the feed variant pre selects |
| Bundle pricing | Only if Jake allows it on site: "Buy 2, 20 per cent off. Buy 3, 30 per cent off, applied in the cart." The schema Offer price stays 87.00 |
| Above the fold copy | "1.2 L insulated bottle showing Australia's National and Marine Parks. Park stickers included. Hand drawn in Perth." |
| Trust block | Australian owned, Perth warehouse; Australian Made logo on tee pages only once the licence is confirmed |
| December banner | From 20 Nov: "Order by Wed 16 Dec for standard delivery before Christmas (east coast metro), Sun 20 Dec for Express" |

## F. Gift collection page for the gifts ad group (1 hour, live by 15 Nov)

1. Products > Collections > Create collection, manual, handle `gifts-for-adventurers`, title "Gifts for Campers, Hikers and Road Trippers". Order: bottle (three colours), the three State Adventure Mugs, The Iconic 45 sticker pack, one tee. Mugs and stickers are out of paid Shopping, but a Search landing page can show them.
2. Description, first two lines visible on mobile: "Gifts for people who love Australia's National and Marine Parks. Ships from Perth, free standard shipping over A$120, 30 day returns." December banner below it from 20 Nov.
3. This becomes the final URL for the `gifts_outdoors` ad group when it is enabled on 17 Nov. Bottle keywords keep the PDP.
4. GA4 > Reports > Engagement > Landing page, filtered to google / cpc: if the collection's purchase rate trails the PDP after 200 gift clicks, send the gift group back to the PDP.

## G. Policy checks on the site (30 minutes)

| Check | URL | Pass |
|---|---|---|
| Contact | /pages/contact and the footer | Business name, a domain email (not Gmail), phone, 4/16 Ledgar Rd Balcatta WA 6021, matching Merchant Center > Business information exactly. Publishing the warehouse address is Jake's call |
| Shipping policy | /policies/shipping-policy in the footer | A$14 standard 2 to 8 days, A$19 express 1 to 4, free over A$120, A$2.50 sticker letters, NZ and overseas rates; same numbers as Merchant Center |
| Refund policy | /policies/refund-policy in the footer | 30 day window, how to start a return, who pays return postage, refund timing, contact method |
| Privacy and terms | /policies/privacy-policy, /policies/terms-of-service | Published and in the footer; privacy policy carries the advertising platforms sentence from `09-audiences.md` |
| Checkout | Add the bottle, check out as an AU guest, stop before paying | No login wall, https, AU address accepted, shipping options and GST inclusive total shown |
| Crawlability | /robots.txt | Shopify default; nothing blocks AdsBot-Google or Googlebot |
| No placeholders | Every footer and menu link | No "coming soon", empty or sold out marketing pages |
| Verification | Google Ads > Admin > Account (the Advertiser verification hub since January 2026) | Started on day one with documents matching the payments profile name |
