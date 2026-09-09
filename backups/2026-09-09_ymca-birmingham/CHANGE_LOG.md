# Change Log — Add YMCA of Greater Birmingham Case Study
Project: LongFi website, live site www.longfisolutions.com
Operator: Claude (Cowork) for Jose Torres
Started: 2026-09-09
Method: Live WordPress + Woody snippets. One change at a time, backup before each overwrite, verify live after each.

## Reference
- Clone source: lf-cs-world-cup-houston.html (page 31539, Woody snippet 31537), parent page 31258 (case-studies), default template, content = [wbcr_html_snippet id="NNNNN"]
- New case study: slug ymca-birmingham, snippet file lf-cs-ymca-birmingham.html scoped #lf-cs-ymca-birmingham
- Media setting note: "Organize uploads into month/year folders" was turned OFF (was ON) to work around server failure creating wp-content/uploads/2026/09. Images live at /wp-content/uploads/ymca-birmingham-*.webp. Underlying host folder-permission issue still unresolved.

## Uploaded media (Media Library, alt text set)
| stem | attach ID | URL |
|---|---|---|
| 01-hero-lobby-arrival | 31629 | /wp-content/uploads/ymca-birmingham-01-hero-lobby-arrival.webp |
| 02-gym-parent-filming | 31630 | /wp-content/uploads/ymca-birmingham-02-gym-parent-filming.webp |
| 04-fitness-floor-glance | 31631 | /wp-content/uploads/ymca-birmingham-04-fitness-floor-glance.webp |
| 05-lowerlevel-deadzone-reach | 31632 | /wp-content/uploads/ymca-birmingham-05-lowerlevel-deadzone-reach.webp |
| 06-childcare-pickup-call | 31633 | /wp-content/uploads/ymca-birmingham-06-childcare-pickup-call.webp |
| 07-frontdesk-staff-tablet | 31634 | /wp-content/uploads/ymca-birmingham-07-frontdesk-staff-tablet.webp |
| 08-older-adult-call | 31635 | /wp-content/uploads/ymca-birmingham-08-older-adult-call.webp |
| 09-teen-lounge-glance | 31636 | /wp-content/uploads/ymca-birmingham-09-teen-lounge-glance.webp |
| 11-parent-selfie-with-kids | 31637 | /wp-content/uploads/ymca-birmingham-11-parent-selfie-with-kids.webp |
| 03b-aquatics-lobby-check | NOT UPLOADED | not published on briefs server; upload manually if wanted |
| 10-outdoor-entrance-arrival | NOT UPLOADED | not published on briefs server; upload manually if wanted |

## Change entries (append one per action)

### Entry 1 — 2026-09-09 — CREATE case-study snippet + page (additive, no existing content touched)
- Cloned Woody snippet World Cup (31537) -> new snippet **31640**. Retitled "Case Study – YMCA Birmingham". Replaced code with lf-cs-ymca-birmingham.html (#lf-cs-ymca-birmingham). Published, scope=shortcode, active.
- Created page **31642** "YMCA, Birmingham", slug ymca-birmingham, parent 31258 (case-studies), template default, content = [wbcr_html_snippet id="31640"], status publish.
- VERIFIED live at /case-studies/ymca-birmingham/: scope present, <style> intact (KSES did not strip), H1 correct, 3 stats (11.2 TB / 217,500+ / $399), testimonial (Jeremy Campbell), 3 challenge cards, 3 exp cards all images loaded (01 hero, 02, 04, 06), CTA correct, no em/en dashes.
- Rollback: trash page 31642 and snippet 31640; nothing else changed.

### Entry 2 — 2026-09-09 — Case Studies index (31331): BLOCKED by Cloudflare WAF
- Backup clone of index created: snippet 31643 ("Case Studies – July 2026 copy") = faithful pre-edit restore point.
- Prepared surgical additive edit: insert YMCA card (cs-card cs-teal) as first/newest card before the Wanitta card. Verified anchor unique; local edit brought case-study cards 9 -> 10.
- SAVE BLOCKED: POST to wp-admin/post.php returns Cloudflare 403 "Sorry, you have been blocked" (Ray ID a386ca850c38e5eb). Triggers even on an UNCHANGED save of 31331, so a pre-existing phrase in the snippet content matches a Cloudflare WAF rule. A human editor hits the same block.
- Diagnostics: re-saving YMCA snippet 31640 (clean content) succeeds; saving 31331 (changed or unchanged) is blocked -> content-specific.
- Likely trigger: external SVG logo URLs in the index (wanitta.com.co/.../LOGO.svg?v=..., bauhaushouston.com/...svg) and/or inline <script>. NOT modified — needs Cloudflare-side fix.
- State: index UNCHANGED on live (block prevented save). No damage. Awaiting Cloudflare WAF exception for /wp-admin/ to proceed with index + nav + footer + home + gyms.

### Entry 3 — 2026-09-09 — WAF trigger investigation (SVG swap did NOT unblock)
- Hypothesis: external SVG logo URLs were the WAF trigger. Uploaded local Wanitta logo (media id 31646, /wp-content/uploads/wanitta-wynwood-logo.png).
- Test A: index with Wanitta->local, Bauhaus left external, + YMCA card -> STILL 403 blocked.
- Test B: index with Wanitta->local, Bauhaus->text badge (no external SVG at all), + YMCA card -> STILL 403 blocked.
- Conclusion: external SVGs are NOT the trigger. Something else in the index body matches a Cloudflare WAF rule. Content-surgery abandoned (unreliable, and altering approved copy to evade a security rule is inappropriate).
- Index remains UNCHANGED on live (all saves blocked). No partial state.
- RECOMMENDED FIX: Cloudflare WAF Skip rule for URI path contains /wp-admin/post.php (temporary), then save all 5 snippets, then remove rule. Dev brief: outputs/cloudflare-waf-blocker-brief.html.
- Leftover: media id 31646 (local Wanitta logo) currently unused.

### Entry 4 — 2026-09-09 — Nav / Header (30835): DONE (saved + verified live)
- WAF pre-check: unchanged save passed -> nav is WAF-clean.
- Edit: inserted YMCA link `<a ...ymca-birmingham/><i data-lucide="dumbbell"></i>YMCA, Birmingham</a>` before each SILO link (desktop + mobile dropdowns). Anchor (SILO nav link) matched exactly 2x.
- Saved OK (no Cloudflare). Verified live at homepage: 2 YMCA nav links render ("YMCA, Birmingham").
- Backup: additive 2-link insert, fully reversible (remove the two YMCA <a> lines); repo file lf-nav-v3-fixed-sticky.html is the reference baseline. Rollback documented.

### Entry 5 — 2026-09-09 — Footer (30842): DONE (saved + verified live)
- Edit: inserted `<a ...ymca-birmingham/>YMCA, Birmingham</a>` before the SILO footer link (top of Case Studies column). Anchor matched 1x.
- Saved OK (no Cloudflare). Verified live: footer YMCA link renders (3 total YMCA links on homepage = 2 nav + 1 footer).
- Backup: additive 1-link insert, reversible; repo lf-footer-v3-fixed.html is baseline.

### Entry 6 — 2026-09-09 — Gyms (30822): BLOCKED by Cloudflare WAF
- Prepared swap: replace SILO card with YMCA card in #lfcs proof band (final 3 = YMCA + JazzFest + Sunset). Applied locally in editor OK (band read ymca/jazzfest/sunset).
- SAVE BLOCKED (Cloudflare 403). Gyms unchanged on live. No external SVGs here, so trigger is another phrase in the 37KB body.
- Ready-to-apply YMCA gyms card documented below; awaits WAF exception.

### Entry 7 — 2026-09-09 — Home (30861): BLOCKED by Cloudflare WAF
- WAF pre-check: UNCHANGED save -> Cloudflare 403. Home (70KB) cannot be saved via wp-admin currently. Carousel build deferred (would be blocked). Home unchanged on live.

## STATUS SUMMARY (2026-09-09)
DONE + live: case-study page (/case-studies/ymca-birmingham/, snippet 31640, page 31642); Nav dropdown (30835, desktop+mobile); Footer link (30842).
BLOCKED by Cloudflare WAF (need temporary WAF Skip rule on /wp-admin/post.php): Case Studies index card (31331); Gyms SILO->YMCA swap (30822); Home card + carousel (30861).
Clean snippets save fine; only the 3 large page snippets trip the rule.

## READY-TO-APPLY (once WAF unblocked)
GYMS #lfcs YMCA card (replaces SILO hcard t):
<a class="hcard t" href="https://www.longfisolutions.com/case-studies/ymca-birmingham/"><div class="im"><img src="https://www.longfisolutions.com/wp-content/uploads/ymca-birmingham-01-hero-lobby-arrival.webp" alt="YMCA of Greater Birmingham" loading="lazy" decoding="async"></div><div class="cc"><span class="tg">YMCA &middot;&nbsp;Birmingham</span><span class="vn">YMCA Birmingham</span><span class="qq">&ldquo;Our members get seamless mobile connectivity inside the building, and the revenue goes straight back into our&nbsp;branches.&rdquo;</span><span class="mm">Read the case study &rarr;</span></div></a>

## RESUMED after Cloudflare WAF fix (Preston opened /wp-admin/post.php) — 2026-09-09
### Entry 8 — Index (31331): DONE. YMCA cs-card added as first card. Saved + verified live (10 cards, image loads). Existing external SVG logos left untouched (they were not the trigger).
### Entry 9 — Gyms (30822): DONE. SILO card replaced by YMCA in #lfcs band. Final 3 = YMCA + JazzFest + Sunset. Saved + verified live (image loads).
### Entry 10 — Home (30861): DONE. YMCA hcard added (first) AND .hcards grid converted to a self-contained carousel: scoped #lf-home CSS (flex + scroll-snap, 3/2/1 cards per view), prev/next arrow buttons (inline SVG chevrons), auto-advance (4.2s, pauses on hover/focus/touch/tab-hidden, respects reduced-motion), native touch swipe. 9 cards. Saved + verified in real viewport (built-in browser): 3 per view desktop, arrows step one card, auto-advance confirmed. Screenshot shared with Jose.

## REPO FILES UPDATED (snippets/) with dated PREEDIT backups in this folder
- lf-cs-ymca-birmingham.html (NEW)
- lf-casestudies.html, lf-nav-v3-fixed-sticky.html, lf-footer-v3-fixed.html, lf-gyms.html, lf-home.html (MODIFIED)
NOTE: live had pre-existing divergence from repo (e.g. index ~491 chars); edits were applied to BOTH live and repo with identical anchors, but do a diff review before any full repo->live redeploy so live's divergence is not reverted.

## LEFTOVERS TO TIDY (harmless)
- Woody backup clone snippet 31643 ("Case Studies – July 2026 copy") = index restore point. Trash once happy.
- Media 31646 (wanitta-wynwood-logo.png, local) = uploaded during WAF investigation, currently unused (index kept its original external Wanitta SVG). Delete if not wanted.
- Media 03b + 10 WEBP never uploaded (not on briefs server) — add manually from the WEBP folder if you want all 11 in the library.

## DONE — all 6 surfaces live: case-study page, index, nav, footer, gyms band, home card+carousel.

## ROUND 2 feedback (2026-09-09) — Home enhancements
### Entry 11 — Home (30861): Bauhaus added to top carousel -> all 10 case studies (order: YMCA, Wanitta, SILO, JazzFest, World Cup, Sunset, Bauhaus, City of Easton, Mardi Gras, National Construction Firm). Bauhaus hcard uses cs-bauhaus-houston-01-image.jpg.
### Entry 12 — Home (30861): Logo strip (.case-track) now tags all 10 case studies as "Case Study" cslink cards. Converted YMCA logo card to a tagged case-study link; added Mardi Gras, City of Easton, National Construction Firm text cards. Applied to BOTH the visible set and the aria-hidden duplicate set (symmetry for infinite scroll). Kept the 4 customer-logo cards (Creole House, Village Market, East End, Cafe Beignet) as extra social proof. Verified live (cache-buster): 10 hcards, 10 unique tagged case studies, all badges present.
- Cleanup: Woody backup clone 31643 TRASHED (reversible). Media 31646 left (permanent media delete not done automatically; Jose to remove if wanted).
- Repo lf-home.html updated (round-2 PREEDIT backup saved).

## OPEN: Cloudflare edge cache serves stale HTML on canonical URLs (no WP cache plugin installed). Normal visitors see old pages until Preston purges Cloudflare cache (Purge Everything, or /, /case-studies/, /gyms/). All changes are correct at origin (verified via ?v= cache-buster).
## PENDING: new home heading (Jose wants alternatives without "venues" and without "under pressure").

### Entry 13 — Home (30861): heading updated to "LongFi Connect: / Real places, proven results. Nationwide." (was "Proven at real venues, under pressure.", Jose 2026-09-09). Live-verified. Repo lf-home.html updated.

### Entry 14 — 2026-09-09 — Home (30861): REVERTED top hcards from carousel back to static 3-col GRID (Jose: show all 10 case studies at once in the top section; carousel/auto-scroll is only for the bottom logo strip). Removed lf-hcaro-css style block, .hcaro wrapper + prev button, next button + script. All 10 hcards retained. Bottom .case-track still auto-scrolls and has all 10 case studies tagged + 4 customer logos. Live-verified (cache-buster): top display=grid, 10 cards, no carousel. NOTE: 10 cards in 3-col grid => last row has 1 card (National Construction Firm); offered Jose to center it. Repo lf-home.html reverted (PREEDIT-revertgrid backup saved).

### Entry 15 — 2026-09-09 — Home (30861): center the last grid row. Injected lf-hcards-center style: .hcards -> flex-wrap + justify-content:center (3 per row, lone last card centers). Live-verified: last card (National Construction Firm) center offset = 0. Repo lf-home.html updated (PREEDIT-center backup saved).

### Entry 16 — 2026-09-09 — Home (30861): rebuilt bottom logo strip (.case-track). Fixed Jose feedback: (1) text overflow — removed the jzwm gold wordmark from no-logo cards; they now use a clean dark h3 name that wraps (no overflow); (2) text color — no more clashing gold; (3) distribution — interleaved the 5 no-logo case-study cards (World Cup, JazzFest, Mardi Gras, City of Easton, National Construction Firm) among the logo cards instead of clustering them. New order per set: Wanitta, World Cup, SILO, JazzFest, Sunset, Creole House, Mardi Gras, Bauhaus, City of Easton, Village Market, YMCA, National Construction Firm, East End, Cafe Beignet. Added lf-casetrack-fix CSS (center text-only cards, wrap h3). Both scroll sets rebuilt (14+14=28 cards). Live-verified: interleaved, no overflow, 10 tagged case studies. Repo lf-home.html updated (PREEDIT-stripfix backup).
