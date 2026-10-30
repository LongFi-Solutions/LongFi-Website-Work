# Change Log: Kiva Dunes case study + blog post (2026-10-30)
Operator: Claude for Jose Torres. Live WordPress, Chrome logged in as Jose. Approved by Josh (all content).
Numbers re-run in Metabase on publish day (through 2026-10-29): 570+ GB, 5,800+ connections, Sep 323 GB / 2,968, Oct 1-29 252+ GB / 2,552, busiest day 168.

## Media (uploaded via WP REST, files pulled from GitHub branch stage/kiva-dunes, _upload_stage/2026-10-30_kiva-dunes)
32059 kiva-dunes-01 hero | 32060 -02 | 32061 -03 | 32062 -04 | 32063 -05 | 32064 -06 | 32065 -07 | 32066 -08 | 32067 network topology | 32068 omada-logo.png | 32069 kiva-dunes-logo.png. All at /wp-content/uploads/<file>, alt text set.

## DONE + live
1. Case study snippet 32070 "Case Study – Kiva Dunes" (HTML, scope shortcode) + page 32072 "Kiva Dunes, Gulf Shores", slug kiva-dunes, parent 31258, content [wbcr_html_snippet id="32070"], featured 32059. Verified 200, scope + styles, all images, stats, quote, no dashes.
2. Blog snippet 32073 "Blog – Kiva Dunes Omada" + post 32075 /kiva-dunes-omada-guest-connectivity/, author Josh Heller (25), categories Case Studies + Technical, 10 tags, featured 32062 (04), Yoast focus kw/title/metadesc set. Snippet hero removed after first render (template already shows featured image + title); Josh's dek moved to the article lead.
3. Footer 30842: Kiva link added above YMCA. Saved, live content == sent. Revision history holds prior version.
4. Nav 30835: Kiva link (tree-palm icon) added above YMCA in desktop + mobile dropdowns. Saved, live == sent.
5. LinkedIn (Josh's personal brand 7209579): scheduled 2026-11-04 10:52 CT, Metricool id 411269190, image 03 bar call (JPG). Tags for CBI and Kiva to be added in the Metricool editor (API has no mention field).

## BLOCKED by Cloudflare WAF (403 on POST /wp-admin/post.php, even unchanged saves)
Index 31331, Home 30861, Hotels 31009, Restaurants 30898, MSPs 31117. Browser egress was BOG/Colombia (cdn-cgi/trace), not Preston's WiFiMan network. Nothing changed on these. Prepared anchored edits (dry-run verified):
- Index: Kiva cs-card (cs-blue) inserted before YMCA card.
- Home: Kiva hcard before YMCA hcard; Kiva case-card (logo) before both YMCA strip cards (visible + aria-hidden copy).
- Hotels + MSPs: SILO hcard replaced by Kiva hcard. Restaurants: JazzFest hcard replaced by Kiva hcard.
Unblock: connect Chrome through WiFiMan (trace colo should not read BOG) or Preston adds a temporary WAF Skip rule for POST /wp-admin/post.php.

## After deploy
Cloudflare edge cache may serve stale nav/footer/home to visitors until purged (Preston: Purge Everything or the changed URLs).
Delete GitHub branch stage/kiva-dunes once everything is live (Metricool already copied the LinkedIn image).

## RESUMED 2026-10-30 09:45 COT on WiFiMan (cdn-cgi/trace colo DFW, US): all five WAF-blocked saves went through
6. Index 31331: Kiva cs-card (cs-blue) added first. Saved, live == sent (20,693 -> 21,703).
7. Home 30861: Kiva hcard first in the case-study rail; Kiva logo case-card in the strip (visible + aria-hidden copies). Saved, live == sent (89,946 -> 91,164). Verified: hero image 1536px loaded, logo cards 300x56 loaded.
8. Hotels 31009: SILO hcard -> Kiva. Band now World Cup / Kiva / JazzFest / Sunset links. Saved, live == sent.
9. MSPs 31117: SILO hcard -> Kiva. Saved, live == sent.
10. Restaurants 30898: JazzFest hcard -> Kiva. Saved, live == sent.
Canonical URLs return cf-cache-status DYNAMIC and already show Kiva; no Cloudflare purge needed.
Rollback for any of the above: the snippet's WordPress Revisions screen (prior version saved automatically), or the PREEDIT repo copies in this folder.
