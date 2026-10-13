# Change Log: Relay integration on longfisolutions.com
Operator: Claude (Cowork) for Jose Torres. Started 2026-09-30.
Method: live WordPress + Woody snippets. Backup before every overwrite. Nothing goes live without Jose.

## Entry 1, 2026-09-30: WordPress-side backups (draft clones, inactive)

| Source snippet | Title | Live length | Backup draft | Exact copy? |
|---|---|---|---|---|
| 30835 | Header - June 2026 | 27,640 | 31736 | yes |
| 30842 | Footer - July 2026 | 10,748 | 31735 | yes |
| 30861 | Home - July 2026 | 78,603 | 31737 | yes |
| 30872 | Longfi Connect - July 2026 | 61,582 | 31738 | one character off (see note) |
| 30883 | How It Works - July 2026 | 44,106 | 31739 | one character off (see note) |
| 30889 | Connectivity Value - June 2026 | 44,743 | 31740 | yes |
| 31117 | partners-MSPs - July 2026 | 54,482 | 31741 | yes |
| 31124 | Portfolio Owners - July 2026 | 54,776 | 31742 | yes |
| 31106 | partner's hub - July 2026 | 27,608 | 31743 | yes |

All backups are titled "ZZ BACKUP 20260930 <page> (pre Relay, src <id>)", status Draft.

Note: Woody's Clone strips backslashes. In 31738 and 31739 the CSS rule `.more::after{content:"\2192"}` became `content:"2192"`. To restore from those two backups, put the backslash back before 2192 (one occurrence each). A corrective Save Draft was attempted and Cloudflare returned "Attention Required" (WAF 403), so saves from wp-admin need Jose on the WiFiMan network.

Page to snippet map (from wp/v2/pages content): home 30859 -> 30861, longficonnect 30870 -> 30872, how-it-works 30881 -> 30883, connectivity-value 30892 -> 30889, msps 30526 -> 31117, portfolio-owners 30536 -> 31124, partners-hub 29775 -> 31106. Header 30835, Footer 30842.

Local repo mirrors in snippets/ do NOT match live for any of these nine files (live is newer). Edits are applied to live content in the browser, anchored, not from the local mirror.

## Entry 2, 2026-09-30: backups corrected
On the WiFiMan network, Save Draft on 31738 and 31739 restored the exact source text. All nine backups now match their sources exactly.

## Entry 3, 2026-09-30: DEPLOYED (Jose approved in chat)
- New Woody snippet 31758 "Relay, Sept 2026" (lf-relay.html, published, shortcode scope). Created from a clone of State & National Parks, then fully replaced.
- New page 31760 "Relay" at /relay/, content [wbcr_html_snippet id="31758"], default template.
- Saved with edits.json (each save only after confirming the live snippet still matched its backup): 30861 Home, 30872 LongFi Connect, 30883 How It Works, 30889 Connectivity Value, 31117 MSPs, 31124 Portfolio Owners, 31106 Partners Hub, 30842 Footer, 30835 Header (last).
- Verified on the public site with cache busters: Relay module present on all seven pages, nav "Sign in to Relay" plus 6 Relay nav links, 2 footer links, accent bar overrides present, /relay/ demo renders.
- Note: the editor shows HTML entities decoded (&nbsp; appears as a real non-breaking space). Stored content keeps the entities; rendering is identical.
- Rollback: copy the matching ZZ BACKUP 20260930 draft content into each source snippet; trash page 31760 and snippet 31758.

## Entry 4, 2026-09-30: Relay v2 revisions (Jose feedback)
- Backups before overwrite (exact): 31770 Relay page v1, 31796 Relay page v1.1, 31772 Home, 31774 Connect, 31776 How It Works, 31778 Connectivity Value, 31780 MSPs, 31782 Portfolio Owners, 31784 Partners Hub (titles "ZZ BACKUP 20260930b/c").
- /relay/ (31758): breaks out of the theme's 1140px content box to full width (demo and bleed screens no longer cropped), page title header hidden, "Book a short call" removed from the section nav, no horizontal scroll.
- New screenshots (media 31790 to 31795): Locations window, Locations laptop, location page, leaderboard, Filter Metrics, Submit a Site.
- Each page's Relay block replaced with a distinct angle (edits_v2.json, replaceModule): Home fleet summary; LongFi Connect dashboard plus floating Locations window with Submit a Site; How It Works site page; Connectivity Value full block with leaderboard (was a slim band); MSPs Filter Metrics; Portfolio Owners My Submissions; Partners Hub Submit a Site.
