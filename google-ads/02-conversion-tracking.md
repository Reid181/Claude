# 02. Conversion tracking

Goal: exactly one Purchase conversion action, created by the Shopify Google & YouTube channel, set as the only Primary action, with order value in AUD and enhanced conversions on. Everything else is Secondary. Smart Bidding later bids on this one number, so it has to be right before launch.

Two rules that prevent most of the known 2025 to 2026 problems:

- One purchase source. The channel's tag is the only thing that may send a purchase to Google Ads. No custom pixel, no Tag Manager, no hand pasted Google tag in the theme. Two sources means double counting.
- Never uninstall or reinstall the Google & YouTube app. Since its August 2026 API change a reinstall can rewrite product IDs and wipe Merchant Center history.

## Step 1: the channel's conversion tracking (10 minutes)

1. Shopify admin > Sales channels > Google & YouTube > Settings. Pass: Google account endlesspks@gmail.com, Merchant Center 5382740922, Google Ads showing the customer ID from `01-account-setup.md`, Google Analytics showing the property that owns G-M3LTBNJ7H4. Any card still saying Connect is a fail.
2. Same page > Google Ads settings > conversion tracking: on. The app creates a Purchase action in Google Ads (set as the account default) and Add to cart and Begin checkout as secondary. If the Ads account already had a purchase action from an older setup, the app offers "Don't measure in linked account" for Checkout completed; do not choose that, instead make the old action Secondary in Step 2 and let the app's Purchase be the one that counts.
3. Same page > Google Ads settings > Enhanced conversions: Turn on. It is not on by default. If the toggle is missing (one vendor reports it was removed in April 2026), carry on and confirm enhanced data is arriving in Step 5.
4. Shopify admin > Settings > Customer events: the only Google pixel should be Google & YouTube. If a custom pixel for Google Ads, GTM or a hand built gtag exists, disable it. Klaviyo, Triple Whale, Clarity, Meta and others are fine.
5. Shopify admin > Settings > Customer privacy > Cookie banner: off for Australia. Google consent mode is only required for the EEA, UK and Switzerland, and there is no Australian cookie consent law in force. The June 2026 OAIC pixel determinations (Medmate, Monash IVF) turned on sensitive health data; the action for a retail store is disclosure. Add Google Ads, Meta, Triple Whale and Microsoft Clarity to the privacy policy, name retargeting, and keep the Shopify privacy opt out page enabled.

How the data flows (Google Ads Help, Shopify data source page, read in full 15 Oct 2026): once the channel is linked, Shopify's "Checkout completed" purchases reach Google Ads two ways, the browser tag and a server to server feed through Google Ads Data Manager that "is set to activate automatically" for stores already using the app. Google deduplicates the two, then uses the server side event for attribution, which recovers purchases the browser tag misses. Nothing to build, but two things to expect: an exclamation mark next to the bell icon in Google Ads announcing the integration, and that the enhanced conversions terms must be accepted at Goals > Conversions > Settings (Step 2) for the server side data to carry customer matching. Only the purchase event is covered; add to cart and begin checkout stay browser only.

## Step 2: Primary and Secondary in Google Ads (10 minutes)

1. Google Ads > Goals > Conversions > Summary.
2. Open the Purchase action whose source is the Google & YouTube app. Edit settings: Goal Purchase; Action optimisation Primary; Value: Use different values for each conversion, default currency Australian Dollar; Count: Every; Click through window 30 days; Engaged view 3 days; Attribution: Data driven (the menu only offers Data driven or Last click; data driven has no volume threshold); Include in Conversions: yes.
3. Every other action (Add to cart, Begin checkout, View item, Page view, Sign up, any GA4 imported purchase, any old manual purchase action): Edit settings > Secondary. Remove any old manual Purchase action after 30 days of zero conversions.
4. Goals > Conversions > Settings: accept Customer data terms, then Enhanced conversions > Turn on > method Google tag.
5. Status will read Unverified until the first order, then Recording conversions.

Conversion value basis: the app sends Shopify's subtotal after discounts, shipping excluded, GST included. An A$87 bottle reports 87.00, not 79.09. Every ROAS target in this plan is on that basis.

## Step 3: tagging and the URL suffix (5 minutes)

1. Admin > Account settings > Auto-tagging: tick "Tag the URL that people click through from my ad". This adds gclid, which Shopify's Conversion summary, GA4 and Triple Whale all read.
2. Admin > Account settings > Tracking > Final URL suffix, paste exactly:

```
utm_source=google&utm_medium=cpc&utm_campaign={campaignid}&utm_id={campaignid}&utm_content={creative}&utm_term={keyword}&gadid={creative}&tw_kwdid={targetid}&pid={product_id}
```

Why: the first six mirror the Meta convention key for key. ValueTrack has no campaign name parameter, so utm_campaign carries the ID and Shopify and GA4 still show the name through gclid. `gadid` is one of the two ad ID parameters Triple Whale recognises (utm_content is not). `tw_kwdid={targetid}` gives Triple Whale keyword level attribution on Search and the product partition (pla-...) on Shopping. `pid={product_id}` gives product level attribution on Shopping and is empty on Search, which is harmless. `{keyword}` is empty on Shopping; that is fine. Shopping URLs already carry ?variant= and Google joins the suffix with an ampersand correctly. A campaign level suffix replaces the account one entirely, so leave every campaign's suffix blank.
3. Click Test next to the suffix. Pass: the product page loads with every parameter in the address bar and no redirect.
4. Redirects kill gclid (a March 2026 Shopify case lost 90 per cent of attribution to a homepage redirect). Check: Shopify > Settings > Markets, no automatic country redirection; no redirect app that drops query strings; every ad lands on the canonical https://www.endlessparks.com/products/ultimate-adventure-bottle, never on /pages/adventurebottle.

## Step 4: GA4, Search Console and Triple Whale (15 minutes)

1. GA4 > Admin > Product links > Google Ads links > Link > choose the customer ID > enable personalised advertising and auto tagging. Reporting only. Do not import GA4 purchase into Google Ads as a Primary action.
2. Google Ads > Tools > Data manager > Search Console > link https://www.endlessparks.com (needs Owner on Search Console). Enables the Paid and organic report, which shows brand search volume.
3. Triple Whale > Integrations > Google Ads: connect with a Google login that has at least Standard access to the Ads account, choose the customer ID. Do not switch on Triple Whale's "automatically add tracking parameters"; it would fight the suffix above.
4. Triple Whale wholesale exclusion: the Pixel already excludes Shopify draft orders and A$0 orders. The Summary dashboard does not, so tag every wholesale draft order `wholesale` in Shopify and set Summary > Global filter > Order tag does not contain `wholesale`.
5. Customer Match from Shopify (Tools > Data manager > Connect product > Shopify) is connected on the build days as `09-audiences.md` describes. A new account can use the lists for Observation and exclusions only, which is all the plan needs (the purchaser exclusion on non brand Search).
6. Triple Whale parameter names: before pasting the suffix, open Triple Whale's Google Ads integration page and confirm it still lists gadid and tw_kwdid as recognised parameters. If Triple Whale shows its own parameter string, use theirs for those two keys and keep the six UTM keys as written.

## Step 5: verify end to end (two days)

1. Tag Assistant: open tagassistant.google.com > Add domain > https://www.endlessparks.com > Connect. In the connected tab, buy the cheapest item (a A$15 mug sticker sheet qualifies for the A$2.50 letter rate) with a real card, then refund it in Shopify. Pass: one Google Ads conversion hit with transaction_id equal to the Shopify order number, value 15.00, currency AUD, user_data present (hashed email, which proves enhanced conversions), and one GA4 purchase event. Fail: two purchase hits (a second source exists), value 17.50 (something is sending shipping included), no hit (sandbox or privacy block). If the value does read 17.50 and cannot be fixed in the app, the last resort is Goals > Conversions > Value rules > a rule multiplying all conversion values by 0.86, and every ROAS target in the plan is then restated.
2. Within about 30 minutes: Goals > Conversions > Summary shows the Purchase action as No recent conversions or Tag active, not Unverified. A test order with no ad click cannot produce a recorded conversion (Google only records conversions that follow an ad interaction, and every campaign is still paused), so "Recording conversions" is not a pre launch test.
3. Goals > Conversions > Purchase > Diagnostics: tag Active, enhanced conversions set up, no missing consent signal warning for Australian traffic. The enhanced conversions match rate band only appears after attributed conversions, so it is a day 7 check.
4. After the first real ad click order (day 1 to 7): Purchase status Recording conversions; Shopify > Orders > the order > Conversion summary shows google / cpc with the campaign ID; GA4 > Acquisition > Traffic acquisition shows google / cpc with the campaign name.
5. Triple Whale > Pixel shows the order under Google within an hour.
6. Only one Primary action exists. Campaigns view segmented by Conversion action shows only Purchase in the Conversions column.

Whole setup pass line: Shopify orders tagged google / cpc for a week equal Google Ads Purchase conversions for the same click dates within about 10 per cent, and Triple Whale's Google attributed orders sit within 20 per cent of both. Google's number is normally the highest; Triple Whale's is the one that decides budget.

If step 2 fails: Shopify > Google & YouTube > Settings > Google Ads settings, turn conversion tracking off and on, wait an hour, repeat the test order. If it still fails, check Customer events for a blocked pixel and Customer privacy for a banner accidentally active in Australia.

## Weekly report view

Campaigns > Columns > Modify columns > save as `EP weekly`: Campaign, Campaign type, Budget, Cost, Impr., Clicks, CTR, Avg. CPC, Conversions, Conv. value, Cost / conv., Conv. value / cost, Search impr. share, Search lost IS (budget), Search lost IS (rank), Click share, Impr. (Abs. Top) %. Segment by Week, then by Conversion action once a month to prove only Purchase is counted. Read on Monday for the last 7 days against the previous 7, and re read two weeks later because conversions lag. Impression share data lags one to two days and is per campaign, not account wide.
