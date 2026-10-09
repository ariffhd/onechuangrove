# Fork status — One Chuan Grove (Chuan Grove GLS)

Forked from [ariffhd/thomsonreserve](https://github.com/ariffhd/thomsonreserve) on 2026-09-15,
per `new-launch-site-shell-checklist-TEMPLATE.md`. This file tracks what's done vs. still
pending so nobody mistakes a partial pass for a finished, publish-ready site.

## ✅ Done

**Section 1 — mechanical rename pass**
- Fresh git history (no Thomson Reserve commits carried over)
- Domain: `thomson-reserves.sg` → `onechuangrove.sg` (~2,900 text replacements across 27 files)
- Brand name: "Thomson Reserve(s)" → "One Chuan Grove" (all case variants, incl. URL-encoded)
- Developer's registered address → **96 Robinson Road, #10-01 SIF Building, Singapore 068899**
  (Chuan Grove Pte. Ltd.'s actual address per URA Developer's Licence C1558 — verified, not guessed)
- Phone number, WhatsApp links, Facebook handle → neutralized to `[TBC]` / `#tbc-facebook-handle`
- Geo coordinates → Lorong Chuan MRT's public coordinates (1.35167, 103.86389) as an
  **approximate stand-in only** — replace once the GBP listing exists
- `staged-articles/chuan-grove-gls/` created (empty, per Section 1.3–1.4)
- `.github/workflows/deploy.yml` deploy path updated to `onechuangrove.sg/public_html/`

**index.html — Background Story section**
- Rewritten with real GLS facts: two-site tender (8 Jul 2025 $703.6M/$1,376psf ppr; 4 Sep 2025
  $623.9M/$1,331psf ppr), same Sing Holdings/Sunway JV, licence C1558 issued 31 Jul 2026.

**index.html — Hero, factsheet strip, sticky bar, header tagline, head metadata**
- `<title>`, meta description, og:*, twitter:* — District 19 / Lorong Chuan / Sing Holdings ·
  Sunway / 1,056 units, no fabricated preview date
- Hero `<h1>` (`One Chuan<em>Grove</em>`), subhead, description, 4 factsheet stat badges
  (Developer, Land Price $1,331–$1,376 psf ppr range, Nearest MRT Lorong Chuan (CCL), Nearby
  School — St. Gabriel's Primary, labelled generically, not claiming an unverified 1km zone)

**index.html — JSON-LD structured data (Section 3)**
- WebSite / ApartmentComplex / AboutPage / LocalBusiness: description, address (District 19,
  Lorong Chuan — no invented street address or postal code), numberOfAccommodationUnits (1056)
- `developer` array → Chuan Grove Pte. Ltd. (licensed SPV) + Sing Holdings Residential +
  Sunway Developments, with verified real org URLs
- Removed: fabricated `amenityFeature` list (Thomson's own named facilities), fabricated
  `openingHours`, `sameAs` links to Thomson's Google Maps pin / wrong developer sites
- Removed the `VideoObject` node **and disabled the live `<iframe>` embed** in the Artist's
  Impression gallery — it was playing Thomson Reserve's real teaser video (YouTube id
  `zFBQQVLWHvs`) under the One Chuan Grove name. Replaced with a labelled placeholder block.
- `ImageObject` nodes: URLs kept (still pending real asset swap — see below) but `name`/`caption`
  now explicitly say PLACEHOLDER instead of presenting them as real
- `FAQPage`: all 9 Q&As rewritten with verified facts; the "former Thomson View Condominium"
  question replaced with a GLS-vs-en-bloc clarifying FAQ; no invented TOP year or 1km-school claim
- Validated as parseable JSON (7 `@graph` nodes) — still needs a live Rich Results Test once deployed

**index.html — Project Core section & developer.html — full rewrite**
- Both now describe the real 2-way JV (Sing Holdings Residential 65% / Sunway Developments 35%)
  with sourced track records, instead of Thomson's fabricated 3-way UOL/SingLand/CapitaLand
  consortium. Fabricated Consultant Team (P&T Consultants, Eco Plan Asia, 2nd Edition, Lian Beng
  Construction) replaced with honest "TBC" language rather than invented/misattributed firms.
- **Found and fixed a landmine**: `developer.html`'s footer had its own hard-coded, DIFFERENT
  fake licence number (C1555, issued 08 Jun 2026) and project account (762-333-930-4) — not the
  same fake data as elsewhere, and not caught by the Section 1 mechanical pass since it's numbers,
  not "Thomson Reserve" text. Now corrected to the real C1558 / 761-352-363-8. **This means every
  other untouched page should be individually checked for its own hard-coded licence/account
  numbers, not assumed safe just because the brand-name pass touched it.**

**pricing.html — full rewrite**
- Recomputed indicative launch PSF floor (\$2,230–\$2,390) from Chuan Grove's real land cost
  run through the same generic RCR cost/margin methodology the page already used
- Removed the "vs Jadescape & AMO Residence" comparison table/info-cards (wrong district — D20,
  not D19) and the "Estimated Pricing by Unit Type" table (used another real project's actual
  confirmed floor-plan sizes) — both replaced with honest "pending/not released" placeholders,
  keeping the section slots per the checklist's own instruction

**faq.html — full rewrite (23 Q&As + duplicate JSON-LD FAQPage)**
- All visible Q&As and their JSON-LD duplicates rewritten with real facts; removed unverified
  claims (Ai Tong 1km zone, wrong MRT line/CRL interchange, fabricated 2032 TOP)
- Renamed "Comparisons with Other D20 Launches" category → "Government Land Sales Background"
  with real GLS tender facts, since Jadescape/AMO Residence (D20) don't apply to a D19 GLS site

**🔴 Security finding — real third-party API key was live in 6 files**
- `index.html`, `faq.html`, `review.html`, `showflat.html`, and both `thomson-reserve-vs-*.html`
  pages had Thomson Reserve's actual working Web3Forms `access_key` hard-coded into their lead
  capture forms. Any registration submitted on this site would have delivered the buyer's name/
  phone/email to Thomson Reserve's Web3Forms account, not ours. Replaced in all 6 files with
  `TBC-REPLACE-WITH-YOUR-OWN-WEB3FORMS-ACCESS-KEY`. **A real Web3Forms account + key must be
  created for One Chuan Grove before any registration form goes live** — this was not caught by
  the original Section 1 pass since it's a credential, not brand text.

**showflat.html — full rewrite**
- Head metadata, JSON-LD, sticky bar, hero, location/hours info cards, visible FAQ, and 3
  bottom info-cards all updated. Removed fabricated amenityFeature/openingHours/sameAs from
  JSON-LD. Unit Type dropdown used Thomson's real confirmed floor plan codes/sizes (BPS1/CP1/
  DP1(L)/E1(L)) — replaced with generic bedroom-count options. Fixed a stray
  `thomson-reserve-showflat` URL left in a JSON-LD answer.

**contact.html — full rewrite**
- JSON-LD dates, sticky bar, footer: standard fixes. Operating Hours block asserted specific
  confirmed daily hours as fact — replaced with honest "to be confirmed".
- **Found another landmine**: the embedded Google Maps iframe still pointed to Thomson Reserve's
  actual real location (a specific Google Place ID + Upper Thomson coordinates) — the mechanical
  pass had only swapped the URL's display-label text to "One Chuan Grove", not the underlying
  pin. Replaced with a simple coordinate-based embed centred on Lorong Chuan MRT, explicitly
  titled as approximate. **Any other page with an embedded map should be checked for the same
  wrong-pin-right-label issue.**

**location-map.html — full rewrite**
- Same wrong-pin Google Maps embed found here too (identical URL to contact.html's) — fixed
  identically. Replaced fabricated "3 MRT lines / TEL x CRL interchange 2030" claims with the
  single confirmed fact (Lorong Chuan MRT, Circle Line, ~10 min walk); removed a fabricated
  travel-time table (Orchard/CBD/Changi minute figures) in favour of a "pending research" note.
  Schools table: replaced Ai Tong 1km/SAP claims with the reported-nearby school list, no
  unverified distance/priority claims. Nature & Lifestyle section (MacRitchie, Windsor Nature
  Park, Thomson Nature Park, Thomson Plaza, Upper Thomson Road) — entirely wrong-location,
  replaced with an honest placeholder; removed the link to macritchie-reservoir-condo.html.

**site-plan.html — full rewrite**
- Replaced fabricated "developer-confirmed" masterplan claims (6 towers, 80 facilities, 2
  entry/exits, 540,000 sqft, plot ratio 2.8, named clubs, colour palettes, PES buffer, carpark
  count) with the real sourced facts (326,640 sqft combined GLS site, licence C1558, reported
  five blocks up to 27 storeys — flagged as reported not confirmed) and honest "not yet
  announced" cards for everything unconfirmed. Removed the Stack Analysis section's Upper
  Thomson nature-reserve-view narrative and wrong-district comps (Jadescape, Sky Habitat),
  replaced with a "pending official site plan" placeholder. Flagged the masterplan image as an
  inherited placeholder rather than presenting it as a real render.

**floor-plan.html — full rewrite (biggest confirmed-vs-fake gap found yet)**
- This page presented four of Thomson Reserve's real, officially-released show unit floor plans
  (Type BPS1/CP1/DP1(L)/E1(L) — exact sizes, appliance brands, marble finishes, a downloadable
  PDF) as if they were One Chuan Grove's own confirmed floor plans. Chuan Grove's floor plans
  have not been released. Removed all 4 detailed floor plan cards, the PDF download link, and
  the "4 Show Unit Floor Plans Released" badge; removed the matching JSON-LD `ImageObject`/
  `DigitalDocument` nodes; removed the "Full Unit Mix" table's fabricated confirmed-sizes/prices
  (same fix already applied to pricing.html); kept the generic buyer-education info-cards but
  stripped Thomson-specific claims (UOL layout quality, nature-reserve views). og:image/
  twitter:image also pointed to one of the same real Thomson floor plan photos — swapped to the
  generic placeholder image used elsewhere.
- **Not visually verified this pass** — the browser tool hit a persistent "file may be missing
  or unreadable" error specific to this file (the file itself is valid, confirmed via `file`,
  UTF-8 decode, and JSON-LD parse). Content changes follow the exact same patterns already
  visually confirmed on 8 other pages, but a visual check is still worth doing when convenient.

**gallery.html — full rewrite (same pattern as floor-plan.html, at full-page scale)**
- The entire page presented 23 of Thomson Reserve's real artist's impressions (facade, Grand
  Arrival, function rooms, pools, gyms, kids' zones — Grand Clubhouse, Cedar Room, Golf
  Simulator, etc.) as One Chuan Grove's own official gallery, with a fabricated release date
  (27 Aug 2026). Removed the featured hero image, category nav, all 5 photo-grid sections, and
  the dead JS that populated them (photo array + lightbox) — replaced with an honest "gallery
  coming soon" placeholder explaining what was removed and why. Removed the JSON-LD
  `ImageGallery` node (23 `ImageObject` entries). og:image/twitter:image swapped to the shared
  generic placeholder image, consistent with other pages.
- **Not visually verified this pass either** — same browser-tool hiccup as floor-plan.html (file
  confirmed structurally valid via `file`/UTF-8/JSON checks); content follows patterns already
  visually confirmed elsewhere.

**review.html — full rewrite (opinion article)**
- Rewrote the Verdict, Strengths/Risks lists, Location, Developer, Pricing and buy/don't-buy
  sections plus the full visible FAQ block and its JSON-LD twin (4 Q&As). Reframed the whole
  piece around the one real, verifiable signal (same JV winning both GLS tenders) instead of
  the fabricated \$810M/3-developer/Ai Tong School/Bright Hill CRL narrative. Removed links to
  the still-unrewritten thomson-reserve-vs-*.html and new-launch-vs-resale-district-20.html
  pages. Also fixed a copy-paste bug in the lead form's hidden subject field (same pattern as
  the one found in faq.html: tagged with the pre-rename filename).
- Visually verified — renders correctly, two-column Strengths/Risks and Buy/Don't-Buy grids intact.

**latest-updates.html — full rewrite (entire fabricated en bloc timeline replaced)**
- The whole page was built around a fictional dated sequence: 2007/2018 en bloc attempts, Oct
  2024 \$810M deal, 1 Jul 2025 High Court order, 2 Oct 2025 acquisition, 26 Mar 2026 naming, Apr
  2026 VVIP registration, a 14 Aug 2026 "firm project update" with fabricated masterplan/
  facility/consultant-team details, and a 14 Sep 2026 floor plan release — none of it happened
  to Chuan Grove, a GLS site with a real, different history.
- Replaced the 10-item updates feed with the 3 real dated events (8 Jul 2025 and 4 Sep 2025 GLS
  tender wins, 31 Jul 2026 Developer's Licence C1558) plus one honest "VVIP preview — TBC" entry
  — no invented milestones for the gap between licence issuance and today.
- Sidebar stats and milestone tracker: same real-facts-only treatment, remaining stages marked
  TBC instead of estimated dates. "The Thomson View En Bloc Story" section renamed and rewritten
  as "The Chuan Grove GLS Story" with 3 real dated cards.
- Visually verified — stats grid and milestone tracker render correctly.

**stamp-duty.html — full rewrite (light pass, mostly generic content)**
- Standard head/sticky-bar/footer fixes. Softened an SSD section claim that asserted "TOP of
  2032" as fact. BSD/ABSD/SSD rate tables and the stamp duty calculator are generic Singapore
  tax law, unrelated to any project — left as-is, verified accurate. Visually confirmed.

**payment-scheme.html — full rewrite (light pass, mostly generic content)**
- Standard head/sticky-bar/footer fixes. The NPS milestone table had a fully fabricated
  year-by-year construction schedule (Launch Day 2026 → CSC 2033, tied to the fake 2032 TOP) —
  replaced every post-booking milestone's estimated year with "TBC" rather than invent a
  schedule Chuan Grove hasn't announced. Softened a "6-7 years to completion" claim derived from
  the same fake schedule. NPS stage percentages, CPF rules, and the calculator are generic
  Singapore regulatory content — left as-is. Visually confirmed the table renders correctly.

**housing-loan-information.html — full rewrite (light pass, last of the 3 Financing pages)**
- Standard head/sticky-bar/footer fixes. Fixed/floating rate section asserted a fabricated
  "foundation stage (est. 2027)... 6-year construction timeline to TOP (2032)" — softened to
  describe the general mortgage disbursement mechanism without inventing dates. LTV limits,
  TDSR rules, HDB upgrader guidance and the loan calculator are generic Singapore regulatory
  content — left as-is. Visually confirmed. **All 3 Financing pages (stamp-duty, payment-scheme,
  housing-loan-information) now done.**

**disclaimer.html — full rewrite (confirmed worth checking closely, not pure boilerplate)**
- Standard head/sticky-bar/footer fixes. Found real entity-specific content that would have been
  missed by a purely mechanical pass: the Intellectual Property clause named "UOL Group Limited,
  Singapore Land Group and CapitaLand Development" as trademark holders (corrected to Sing
  Holdings Residential + Sunway Developments), and the Governing Law section's Enquiries contact
  named "Tamarind Development Pte. Ltd." as the entity to contact (corrected to the real licensed
  entity, Chuan Grove Pte. Ltd.). The general legal boilerplate (pricing/renderings/timeline/
  financial/no-contract/third-party/IP/governing-law clauses) is generic and left as-is.
- **Found and fixed a bug from the previous two pages**: the "Sing Holdings [logo pending]"
  footer badge was missing its color style on this page, rendering as invisible dark-on-dark
  text — checked payment-scheme.html and housing-loan-information.html for the same issue (both
  were already correct) and fixed it here. Visually confirmed both badges now render correctly.

**privacy-policy.html — full rewrite (confirmed the pattern from disclaimer.html again)**
- Standard head/sticky-bar/footer fixes. Same category of real entity-specific content found:
  the Introduction's legal-highlight and the Disclosure of Personal Data section both named
  "Tamarind Development Pte. Ltd. — a joint venture of UOL Group, Singapore Land Group and
  CapitaLand Development" as the site operator / data recipient (corrected to Chuan Grove Pte.
  Ltd. / Sing Holdings Residential / Sunway Developments). The Data Protection Officer contact
  block named the wrong entity and asserted specific confirmed showflat hours
  ("Monday-Sunday, 10:00am-7:00pm") as fact — corrected entity, replaced hours with honest [TBC].
  General PDPA clauses (data collected, retention, rights, cookies, security) are generic and
  accurate — left as-is.
- **Repeated the footer dev-badge color-style mistake from disclaimer.html, then caught and
  fixed it inline before committing** — worth noting as a pattern to watch for on any remaining
  page using this same footer edit sequence. Visually confirmed both badges and the DPO contact
  block render correctly.

**index.html — remaining sections rewritten (Latest Updates through Resource Hub + footer)**
- Hero sidebar "Latest Updates" card: replaced the fabricated 8-item timeline with the same 3
  real dated events used in latest-updates.html (8 Jul 2025 and 4 Sep 2025 GLS tender wins, 31
  Jul 2026 Licence C1558) plus one honest "VVIP Preview — TBC" entry.
- Gallery section: intro no longer claims "1,268-unit/6 towers/23 official photos" (was
  inconsistent with gallery.html's already-fixed "coming soon" state); both artist's-impression
  `<figure>` blocks swapped from real Thomson image files to labelled "not yet released"
  placeholder blocks (same treatment as the teaser video block already had), consistent with the
  floor-plan.html/gallery.html pattern.
- Project Core "Architectural Vision" → renamed "Site & Masterplan", rewritten around the real
  two-GLS-parcel amalgamation (Lots 19037L/19064A MK18) instead of the fabricated 540,000 sq ft/
  5-hectare/6-tower/SICC-view/Jadescape-comp narrative.
- "Timeline to Launch" → 3 real dated milestones (same as Latest Updates card) plus TBC entries
  for showflat/preview/booking/TOP, replacing the fabricated Nov 2024–2032 sequence.
- "Project Details Table" → rebuilt with real facts (site, JV developer, District 19, 1,056
  units, combined $1.33B land price, Licence C1558, Project Account 761-352-363-8) and explicit
  `[TBC]` for every unconfirmed field (tenure, blocks/storeys, unit types, facilities, carpark,
  site area, plot ratio, consultant team, TOP) instead of Thomson's fabricated values.
- Connectivity & Transit (silo-2): replaced the fabricated "3 MRT lines" narrative (TEL/Upper
  Thomson, CRL/Bright Hill 2030, NSC 2027 — none apply to Lorong Chuan) with the single real fact
  (Lorong Chuan MRT, Circle Line CC15) and a travel-time table marked `[TBC]` pending confirmed
  data, instead of inventing new stop-by-stop times. Section h2 heading ("...at Bright Hill
  Drive") also fixed — missed in an earlier pass, caught by this section's re-read.
- Investment Thesis (silo-3): "$810 Million En Bloc Record" → "$1.33 Billion Land Cost Basis",
  rebuilt the cost-basis breakdown and PSF range off the real blended land cost, converging on
  the same $2,230–$2,390 psf estimate already established in pricing.html/review.html/etc.
  Removed the fabricated "vs Jadescape & AMO Residence" comparison table (wrong district) in
  favour of an honest note that no reliable comparable data exists yet — same treatment already
  applied to pricing.html's Market Comparison section.
- Family & Lifestyle (silo-4): removed the fabricated "Ai Tong School 1km / Phase 2C(S) priority"
  claim and its 7-row school table, and the "Nature Living" MacRitchie/Windsor/Thomson Nature
  Park/Lower Peirce/Rail Corridor list (all wrong-location, already removed from location-map.html
  in an earlier pass) — replaced both with honest "schools/amenities not yet verified for this
  site" placeholders rather than inventing Lorong Chuan-specific claims with no source.
- Live Inventory Monitor: unit count corrected to 1,056; milestone list rebuilt around the 3 real
  dated events instead of the fabricated en bloc/floor-plan-release sequence; removed the
  "Early-Mid October 2026" preview-date claim (now "TBC").
- Registration section: removed a fabricated "Early-Mid October 2026" VVIP preview date claim
  that had leaked into the reg-desc copy (not on the original NOT-done list, but directly
  adjacent and clearly false — fixed while in the area).
- Resource Hub: rewrote all 5 neighbourhood-guide card taglines to stop asserting false specifics
  (CRL 2030, D20, P1 priority zone, nature-reserve premium, Jadescape/AMO comparison) about pages
  that are still Thomson's real inherited content — same "content pending update" honesty pattern
  used for these same links in sitemap.html. Card hrefs/order left unchanged (tied to the future
  topical-map rewrite, not today's scope).
- **Found a significant gap the earlier index.html passes had missed: the page's own `<footer>`
  had never been touched.** It still had Thomson's fabricated developer name ("Tamarind
  Development Pte. Ltd. (UOL · SingLand · CapitaLand)"), a THIRD different fake licence number
  (C1555, issued 08 Jun 2026 — distinct from both developer.html's old fake C1555/762-333-930-4
  and the real C1558), unit count 1,268, "Early-Mid October 2026" preview date, "2032" TOP, the
  3-logo UOL/SingLand/CapitaLand `<img>` badge block, a hardcoded Bright Hill Drive address, fake
  "Mon–Sun 10am–7pm" hours, and a live link to Thomson's real YouTube channel
  (`youtube.com/@thomson-reserve`). Fixed identically to the pattern used on all 18 other pages:
  developer name/licence/account/unit-count/TBC-preview, 2 text-placeholder dev-badges (with the
  color style included correctly this time), address/hours → TBC, YouTube → `#tbc-youtube-handle`,
  copyright line → Chuan Grove Pte. Ltd. **This means the footer fix should be independently
  double-checked on any page where it wasn't the very first thing verified.**
- JSON-LD (single `@graph` block, unchanged by this pass) re-validated as parseable JSON; HTML tag
  balance (div/section/table/tr/td/ul/li/figure/a) checked programmatically — all balanced.
- **Visually verified** — worked around the browser tool's transient file:// access error (same
  one seen on floor-plan.html/gallery.html) by serving the directory over a temporary local HTTP
  server instead. Confirmed the Latest Updates card, Timeline/Project Details table, Gallery
  placeholder blocks, and footer (including both dev-badge labels rendering with correct color
  styling this time) all render correctly.

**index.html is now fully rewritten — this closes out item 1 from the NOT-done list below and
completes the "18 non-inherited pages" scope (now 19, counting index.html's full completion).**

**sitemap.html — full rewrite (last of the generic pages — all 18 now done)**
- Standard head/sticky-bar/footer fixes. Not purely a link list as guessed — the "Main Pages"/
  "Project Information" taglines had fixable developer-name/district/fabricated-masterplan-size
  claims. The bigger find: the "Neighbourhood Guides" category links to all 8 inherited content
  pages under taglines making specific false claims (CRL 2030 interchange, District 20, P1
  registration zone, MacRitchie premium, "vs Jadescape/AMO Residence" comparisons). Replaced each
  with an honest "Neighbourhood guide — content pending update for One Chuan Grove" rather than
  either leave the false claims or invent new ones for content that doesn't exist yet — link
  labels/hrefs left unchanged since renaming them is tied to the eventual topical-map rewrite
  (item 3 below), not today's scope. Got the dev-badge color-style right on the first attempt
  this time. Visually confirmed.
- **All 18 "regular" site pages are now fully rewritten** (everything except the 8 inherited
  content pages, which need a genuine new topical map, not a find-replace pass).

**New topical map — all 8 inherited content pages replaced (Section 5 of the checklist)**

Researched real, sourced facts (LTA station data, MOE/school addresses, GLS tender records, and
public property-portal listings for genuine nearby projects) via web search, then built a fresh
8-page topical map for Lorong Chuan / District 19 — not a find-replace pass, genuine new content
per the checklist's Section 5 instruction. All 8 old files removed (`git rm`) and replaced:

- **`upper-thomson-mrt.html` → `lorong-chuan-mrt.html`** — Lorong Chuan MRT (CC14) Circle Line
  guide. Corrected a real error introduced earlier in this project: I had written the station code
  as **CC15 across index.html** (that's actually Bishan's code) — fixed there too as part of this
  pass. Real facts used: opened 28 May 2009 (CCL Stage 3), one stop to Serangoon (CC13/NEL) and
  Bishan (CC15/NSL), and the Circle Line's Stage 6 completion (12 Jul 2026) closing the loop to
  Marina Bay (CC33) and HarbourFront (CC29) — verified via LTA's published station sequence, not
  estimated. Replaced invented minute-by-minute travel times with verified stop counts instead.
- **`bright-hill-drive.html` → `lorong-chuan-gls-site.html`** — the real GLS site-history story:
  two adjoining parcels (170,409 + 156,231 = ~326,640 sq ft, already sourced in site-plan.html),
  won by the same JV in 2025, explicitly framed as "why this isn't an en bloc story."
- **`ai-tong-school-1km-condo.html` → `schools-near-lorong-chuan.html`** — led with the one
  precisely verifiable fact (St. Gabriel's Primary School, 220 Lorong Chuan, ~5 min walk from the
  MRT), explicitly declined to claim a 1km/2km priority-registration zone for One Chuan Grove since
  the site has no confirmed civic address yet, and listed other reported-nearby schools (Zhonghua
  Primary, Kuo Chuan Presbyterian, CHIJ Our Lady of Good Counsel, Nanyang JC, Australian
  International School, Stamford American International School) as "reported, distance TBC" rather
  than inventing distances.
- **`macritchie-reservoir-condo.html` → `nex-serangoon-lifestyle.html`** — real, sourced amenities
  actually near Lorong Chuan: NEX mall + Serangoon Public Library + Serangoon Bus Interchange (one
  MRT stop away), two small real neighbourhood parks (Chiltern Drive Interim Park, Kampong Park @
  Serangoon), and Serangoon Garden's hawker scene — replacing the entirely wrong-location MacRitchie
  Reservoir/Windsor Nature Park content.
- **`new-launch-vs-resale-district-20.html` → `new-launch-vs-resale-district-19.html`** — found a
  genuine resale comparable directly in the area: **The Scala @ Lorong Chuan** (120 Serangoon
  Avenue 3, 99-yr leasehold, TOP 2013, 468 units, developer Circle Line Pte. Ltd./Hong Leong/Hong
  Realty/TID, current resale PSF ~$1,858–$2,544) — a real, sourced comparison instead of Thomson's
  fabricated Jadescape/AMO Residence framing.
- **`thomson-reserve-vs-amo-residence.html` → `one-chuan-grove-vs-chuan-park.html`** — found a
  genuine, directly relevant comparable: **Chuan Park**, a real, unrelated new launch also at
  Lorong Chuan (opposite the MRT), by Kingsford Huray Development + MCC Land, en bloc-acquired for
  $890M in Jul 2022, 916 units across 5 blocks. Explicitly flagged that the two projects share
  nothing but a similar name and address — worth a dedicated FAQ answer given the real risk of
  buyer confusion between them.
- **`thomson-reserve-vs-jadescape.html` → `district-19-new-launch-price-guide.html`** — rather than
  force a second weak head-to-head (the only other nearby project found, Jansen House, is a
  21-unit/5-storey 999-year-leasehold boutique development — too different in scale/type for a
  meaningful comparison), built a broader District 19 PSF benchmark page: the reported $2,100–
  $2,600 psf district-wide range, One Chuan Grove's own $2,230–$2,390 estimate in context, and a
  summary table referencing The Scala and Chuan Park with links to their dedicated pages.
- **`balance-units-chart.html`** — kept its filename (linked from 8+ other pages as a functional
  feature page) since its content was already mostly generic/evergreen "how balance units charts
  work" material; targeted edits only, removing the fabricated 1,268-unit count and "Mid-October
  2026" dates rather than a full rewrite.

All 8 pages follow the established page pattern (head/JSON-LD/topbar/nav/footer identical
structure to every other page, footer using the same developer/licence/units/TBC fixes applied
sitewide). Every page's JSON-LD validated as parseable; HTML tag balance checked programmatically
across the whole site (not just these 8) — all balanced. Sitewide internal-link check confirms
every `href` to an `onechuangrove.sg/*.html` page resolves to a file that actually exists.

**Also fixed while sweeping for cross-references:**
- `index.html`'s Resource Hub cards now link to the 8 new pages with accurate taglines (previously
  linked to the old inherited filenames with generic "content pending" placeholders).
- `sitemap.html`'s "Neighbourhood Guides" category updated to the new filenames and real
  descriptions.
- `sitemap.xml` updated to the new filenames — and a **pre-existing broken link found and fixed**:
  it referenced `thomson-reserve-review.html`, which has never existed under that name in this
  fork (the real file is `review.html`) — a leftover from the original Section 1 mechanical pass
  that nothing had caught until this sweep.

**Repositioning — the site now speaks as the developer, not an agency marketing the project (2026-09-21)**

The site is meant to represent the developer (Chuan Grove Pte. Ltd. — Sing Holdings Residential /
Sunway Developments), not a third-party agency. The Thomson Reserve scaffold and my earlier passes
had a lot of agent/analyst-style copy, which this pass removed sitewide. The voice rule going
forward: "we" = the developer; unknown facts read "to be announced", never "reported" / "not yet
verified"; no analyst estimates, no competitor comparisons, no buyer-coaching.

- **Removed 4 third-party-style pages** (recoverable from git history): `review.html` (independent
  "is it worth buying?" review), `one-chuan-grove-vs-chuan-park.html`,
  `new-launch-vs-resale-district-19.html`, `district-19-new-launch-price-guide.html`. Removed from
  sitemap.html / sitemap.xml and the homepage hub. This supersedes the topical-map notes above for
  those four pages; the other four topical-map pages (MRT, site, schools, lifestyle) were kept and
  rewritten in developer voice.
- **`pricing.html` rewritten** — it was publishing the developer's own margin (20–25%), a
  breakeven table and an "analyst" PSF estimate ($2,230–$2,390). Now a plain "pricing to be
  announced at the VVIP preview" page. The PSF estimate is gone from every page (index, FAQ,
  showflat, JSON-LD).
- **Homepage**: removed the Investment Thesis section; hero "Land Price" badge → "Total Units";
  land price / psf ppr / bid-margin details removed everywhere; "Resource Hub" → "Location";
  press-style "GLS Story" section → developer-voice "About the Site"; removed the misleading
  auto-updating "Last Updated" date and Thomson og:image/JSON-LD image references.
- **Removed agent-style pitches sitewide**: "no commission payable", "direct developer price",
  "1-hour response", "first-come first-served", "request a specific sales consultant",
  buyer-coaching content (floor-plan "how to evaluate", balance-units "pre-launch checklist",
  site-plan "stack analysis"), and "What the consortium means for buyers" on developer.html.
- **Removed leaked fork notes from public pages** ("PLACEHOLDER — inherited from Thomson Reserve
  scaffold", "previous version of this page displayed…", "removed rather than left in place…").
  These now read as normal "coming soon" copy.
- **Caught inherited falsehoods that earlier passes missed**: showflat.html still said "4 show unit
  floor plans are out now" and showed the PSF/breakeven card; contact.html had a leftover broken
  fragment; sitemap.xml pointed at `thomson-reserve-showflat.html` (real file: `showflat.html`) and
  omitted `gallery.html`/`faq.html` — regenerated from the real page list. faq.html also had a
  pre-existing unclosed `<section>`/`<div>` around the registration form, now fixed.
- FAQ regenerated (visible list + JSON-LD from one source, 19 Q&As); en-bloc/land-price/tender
  competitiveness/"what was it called before" questions dropped.
- Unverified claims removed rather than restated: "10-minute walk", "one street from the CTE",
  "99-year leasehold" (tenure is not confirmed), "five blocks up to 27 storeys".
- **Voice-check needs a human**: facts only the developer knows (tenure, blocks/storeys, unit mix,
  TOP, walking time to the MRT, address, showflat hours, phone) now read "to be announced". Fill
  these in once known. Also worth deciding: the FORK-STATUS.md file itself documents the Thomson
  Reserve fork — consider keeping it out of a public repo.

**Contact number + new colour scheme (2026-10-09)**
- Mobile/WhatsApp set to **+65 8075 5946** everywhere (`tel:`, `wa.me/6580755946`, JSON-LD `telephone`,
  visible text on all 22 pages). The phone number is no longer a TBC item.
- Colour scheme changed because the inherited dark-green + gold on cream was too close to
  thomson-reserves.sg. New palette: **deep navy** (`#17243f` / `#0b1526`) + **copper** accent
  (`#c0714a`, light `#f0b793`) on a **cool off-white** (`#f4f6f8` / `#e5eaf0`), with cool-grey text.
  Applied by mapping the CSS variables and every hardcoded rgba/hex; green is kept only where it is
  semantic (WhatsApp button, "live"/success status).
- Header logo mark changed from "TR" (Thomson Reserve's initials) to "OC".
- Still shared with the Thomson Reserve site: fonts (Cormorant Garamond + Jost) and the overall page
  layout. If it still feels too similar, changing the typeface is the next lever.
- Also cleaned up the remaining visible "[TBC: full address]" / "[TBC: showflat hours]" footer text on
  14 pages (now "address to be announced" / "opening hours: to be announced").

**Official address + structured-data cleanup (2026-10-09)**
- Address is now **1 Chuan Grove, Singapore 556860** — in every schema `PostalAddress` (13 business
  entities: ApartmentComplex + LocalBusiness), every page footer, the homepage details table, and the
  copy that previously said "address to be announced / once the site's address is assigned" (those
  walking-time/distance lines now say "closer to launch" — no distances have been measured yet).
- Schema `telephone` = `+6580755946` on every LocalBusiness; `contact.html` previously had no business
  entity at all, so one was added (same `@id` as the homepage's).
- Removed the `geo` coordinates (they were the Lorong Chuan **MRT's** coordinates, a stand-in that no
  longer matches the real address). Add the site's exact coordinates once known.
- Rich Results Test showed `thomson-reserve-*.jpg` as the page `image`: those references were already
  gone from the code (removed in the developer-voice pass) — the test was reading a stale cached copy
  of the live homepage (`x-proxy-cache`), not a code problem. Needs a SiteGround cache flush after deploy.
- The embedded Google Map still shows the Lorong Chuan MRT area (OneMap/Google could not resolve the
  new postal code 556860 at the time); switch it to the address once it resolves.

## ⚠️ NOT done — needs manual content work, not find-replace

1. **All images/PDFs** (`thomson-reserve-*.jpg/.png`, floor plan PDF, 3 developer logos) are
   Thomson Reserve's real marketing photos and competitors' real logos, still referenced by
   filename (now confusingly under the `onechuangrove.sg` domain). **Do not deploy with these
   assets in place.** Full list: `find . -iname "thomson-reserve-*"` plus the 3 developer logo PNGs.
2. **Zero pages left with fabricated or inherited-wrong-location content.** All 27 HTML pages
   (19 previously-done pages + the 8 topical-map pages, now genuinely rewritten) use real, sourced
   or explicitly-TBC facts. Every page passes JSON-LD validation, tag-balance checks, and
   internal-link resolution.
3. Everything still marked `TBC`: TOP/launch date, GBP Place ID, social handles, NAP phone
   number, full NAP block (street address/postal code — the GLS site doesn't have a public civic
   address yet), brand colors/logo, YouTube handle (was previously Thomson's real channel — now
   neutralized to `#tbc-youtube-handle` across every page including index.html's footer).

## Suggested next step

Every page on the site — all 27 of them — is now rewritten with real, verified or explicitly-TBC
One Chuan Grove facts. There is no more find-replace or fact-correction work left to do. What
remains depends on information only the user/developer can supply:
1. **Real marketing assets** (item 1 above) — artist's impressions, floor plans, gallery photos,
   developer logos, and a teaser video, none of which exist yet for the real One Chuan Grove.
2. **The TBC fields** (item 3 above) — TOP/launch date, GBP Place ID, social handles, phone number,
   full civic address, tenure, brand colors/logo. Most of these can only be filled in once the
   developer makes an official announcement or the site is issued a civic address.
3. Consider a live Rich Results Test pass across all pages once deployed, and a NAP consistency
   check against the eventual GBP listing (per checklist Sections 3 and 8) — both require a live
   domain to run against, so not actionable in local development.
