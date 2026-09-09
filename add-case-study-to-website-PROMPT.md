# Add a Case Study to the LongFi Website — Execution Prompt

Reusable playbook. This copy is filled in for **YMCA Birmingham**. To reuse for a future case
study, swap the values in the "INPUTS & PATHS" block (brief URL, slug, images folder + filenames,
vertical, and which page to clone) and re-run. Everything else stays the same.

Paste everything below the line into a fresh **Opus 4.8** chat with WordPress open in Chrome.

---

You are helping LongFi Solutions publish a new case study — YMCA Birmingham — and wire it across
longfisolutions.com exactly like the existing nine case studies. Use our established WordPress +
Woody snippet + GitHub workflow. This is LIVE-site work: verify each change on the live site before
moving on. Chrome is already logged into WordPress as Jose Torres (admin). Model: Opus 4.8.

════════ INPUTS & PATHS ════════
• Source brief (open in the logged-in Chrome; robots blocks plain fetchers):
  https://briefs.longfisolutions.com/ymca-birmingham
• Content/testimonial is APPROVED (Andrew, 2026-09-08) — clear to publish. We are NOT using
  Andrew's MD instructions file; follow the existing repo pattern instead.
• Images (on my Mac, 11 PNGs, numbered to the brief's image order, scene-captioned by filename):
  "/Users/josemt-mbp/Mis Documentos/AI KB/LongFi-OS/99_Projects/5. Marketing Collateral Generator/05. Staged Images/01. Photos/YMCA - Community Centers"
    01-hero-lobby-arrival.png        07-frontdesk-staff-tablet.png
    02-gym-parent-filming.png        08-older-adult-call.png
    03b-aquatics-lobby-check.png     09-teen-lounge-glance.png
    04-fitness-floor-glance.png      10-outdoor-entrance-arrival.png
    05-lowerlevel-deadzone-reach.png 11-parent-selfie-with-kids.png
    06-childcare-pickup-call.png
• Website repo snippets folder (on my Mac):
  "/Users/josemt-mbp/Mis Documentos/AI KB/LongFi-OS/08_website_design/LongFi-Website-Work/snippets/"
• Clone this existing case study for structure: lf-cs-world-cup-houston.html
  (live page /case-studies/world-cup-houston/ = page-id-31539; live Woody snippet ID 31537)

Slug: ymca-birmingham | Page: /case-studies/ymca-birmingham/
New snippet file: lf-cs-ymca-birmingham.html scoped to #lf-cs-ymca-birmingham | Vertical: gyms/wellness.

════════ LIVE WOODY SNIPPET IDs (edit via admin CodeMirror) ════════
  Home – July 2026 ............ 30861   (homepage case-study section → CAROUSEL, approved)
  Case Studies index .......... 31331
  Header/Nav (Case Studies) ... 30835
  Footer ...................... 30842
  Gyms – July 2026 ............ 30822   (feature YMCA in its #lfcs proof band; swap out SILO)

════════ STEP 0 — Access check ════════
Confirm admin bar present + wpApiSettings.nonce works. If logged out, ask me to log in.

════════ STEP 1 — Content ════════
Pull the full brief from the brief URL in Chrome: headline, venue, location, challenge, solution,
results/metrics, testimonial + attribution, and which image sits in each slot. Apply GP-09 to ALL
copy: spell "Wi-Fi" (never WiFi); no em/en dashes (use commas); no absolutes
(every/only/always/never/zero/guaranteed); connection counts are session counts; keep YMCA metrics
tied to YMCA (do NOT merge into the network-wide proof block). GP-04: never place the logo over a photo.

════════ STEP 2 — Images (WEBP → WP media) ════════
• Stage the 11 PNGs from the Mac path above into the container (device_stage_files).
• Convert each to WEBP with Pillow (quality ~82, cap longest edge ~1600px); keep the numeric
  filename stems (e.g. ymca-birmingham-01-hero-lobby-arrival.webp).
• Upload each to the WordPress media library via REST POST /wp/v2/media (Content-Type image/webp,
  Content-Disposition filename=...), passing the WEBP as a base64→Blob into the browser JS with the
  nonce. Capture each returned source_url. Set descriptive alt text per image. Use these WP URLs in
  the snippet (never hotlink the briefs domain). Map by filename number/description; 01-hero is the hero.

════════ STEP 3 — Build the case-study page ════════
• Create lf-cs-ymca-birmingham.html by cloning lf-cs-world-cup-houston.html's structure/CSS, scoped
  to #lf-cs-ymca-birmingham, with YMCA content + the uploaded WEBP URLs.
• Create the WP page /case-studies/ymca-birmingham/ by replicating exactly how page-id-31539 is built
  (same parent "case-studies", same template, snippet injected the same way). Deploy the snippet to a
  new Woody snippet and wire it in.

════════ STEP 4 — Wire across all surfaces (match existing card/link style) ════════
• Case Studies index (31331): add a YMCA card.
• Nav Case Studies dropdown (Header 30835): add a link.
• Footer Case Studies column (30842): add a link.
• Homepage (30861): add the card AND convert the case-studies section into a CAROUSEL (APPROVED by
  Jose) — self-contained, no external libraries, auto-advance + arrows + swipe, matching the existing
  card design. Build it, then screenshot it for me so I can see the result.
• Gyms page (30822): feature YMCA Birmingham in its #lfcs proof band. KEEP THE BAND AT 3 CARDS and
  swap out SILO (the least relevant for gyms). Final three: YMCA Birmingham + JazzFest + Sunset Rooftop.

════════ STEP 5 — WordPress mechanics (learned patterns) ════════
• Woody snippets: set BOTH the CodeMirror value and #post_content, then submit with
  form.requestSubmit(#publish) (a plain click didn't always submit).
• Elementor pages: edits go into _elementor_data via REST; AFTER any change, clear Elementor cache
  (admin-ajax action=elementor_clear_cache with the tools-page button's data-nonce) or the front end
  serves stale HTML. Avoid backslashes in injected HTML (escaping hazard) — use backslash-free JS.
• javascript_tool output is content-filtered: return only numeric/boolean summaries, never raw HTML,
  and don't return URLs with query strings.

════════ STEP 6 — Verify ════════
Reload each surface with a cache-buster; confirm the YMCA card/link renders and the new page returns
200. Screenshot: the new case-study page, the homepage carousel, and the gyms band, for me.

════════ STEP 7 — Save to repo + git ════════
Write the new + every changed snippet back to the snippets/ folder. Give me exact git add/commit/push
commands (I run them). If git complains about .git/index.lock, tell me to run `rm -f .git/index.lock`
first. Commit message co-authored by Claude.

Ask me before anything that would change an existing published URL. The carousel and the SILO swap are
already approved — proceed with those and report per surface.
