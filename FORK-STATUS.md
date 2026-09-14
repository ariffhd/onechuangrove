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

## ⚠️ NOT done — needs manual content work, not find-replace

1. **Same "$810M en bloc" / "1,268 units / 6 towers" narrative still appears in OTHER sections of
   index.html**: Latest Updates feed, Artist's Impression intro, Timeline to Launch, Project
   Details table, Connectivity intro, Investment Thesis section, Family & Lifestyle intro, Live
   Inventory Monitor, Resource Hub — none of these have been touched yet.
2. **All images/PDFs** (`thomson-reserve-*.jpg/.png`, floor plan PDF, 3 developer logos) are
   Thomson Reserve's real marketing photos and competitors' real logos, still referenced by
   filename (now confusingly under the `onechuangrove.sg` domain). **Do not deploy with these
   assets in place.** Full list: `find . -iname "thomson-reserve-*"` plus the 3 developer logo PNGs.
3. **8 inherited content pages** (`ai-tong-school-1km-condo.html`, `bright-hill-drive.html`,
   `macritchie-reservoir-condo.html`, `upper-thomson-mrt.html`, `balance-units-chart.html`,
   `new-launch-vs-resale-district-20.html`, `thomson-reserve-vs-amo-residence.html`,
   `thomson-reserve-vs-jadescape.html`) are Thomson Reserve's topical-map cluster articles — real
   facts about a different location, each with their own JSON-LD still untouched. Per Section 5,
   Chuan Grove needs its own fresh topical map. Left in place, unlinked from anywhere new.
4. **16 other HTML pages** (`stamp-duty.html`, `payment-scheme.html`,
   `housing-loan-information.html`, `latest-updates.html`, `review.html`, `disclaimer.html`,
   `privacy-policy.html`, `sitemap.html`, etc.) — only `index.html`, `developer.html`,
   `pricing.html`, `faq.html`, `showflat.html`, `contact.html`, `location-map.html`,
   `site-plan.html`, `floor-plan.html` and `gallery.html` have been touched so far. Each has its
   own body copy, sticky top bar (still says "D20"/old preview date on every untouched page),
   footer, and JSON-LD still carrying Thomson Reserve facts — and each should be checked for its
   own hard-coded licence/account numbers, its own Web3Forms access_key if it has a lead-capture
   form, any embedded Google Maps iframe (see the wrong-pin finding above), and any real
   confirmed-looking data (floor plan sizes, photos) inherited from Thomson's actual releases.
5. **YouTube channel link** in the footer (`youtube.com/@thomson-reserve`) — still points to
   Thomson Reserve's real channel; needs a real Chuan Grove channel or removal.
6. Everything still marked `TBC`: TOP/launch date, GBP Place ID, social handles, NAP phone
   number, full NAP block (street address/postal code — the GLS site doesn't have a public civic
   address yet), brand colors/logo.

## Suggested next step

`review.html` is a natural next target — it's linked from the homepage and likely repeats the
en bloc/$810M narrative and 3-developer consortium claims already fixed on index.html's
Background Story and Project Core sections, plus its own footer landmines.
