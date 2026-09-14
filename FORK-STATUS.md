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
4. **24 other HTML pages** (`pricing.html`, `floor-plan.html`, `faq.html`, `contact.html`,
   `showflat.html`, `site-plan.html`, `gallery.html`, `location-map.html`, `stamp-duty.html`,
   `payment-scheme.html`, `housing-loan-information.html`, `latest-updates.html`, `review.html`,
   `disclaimer.html`, `privacy-policy.html`, `sitemap.html`, etc.) — only `index.html` and
   `developer.html` have been touched so far. Each has its own body copy, sticky top bar (still
   says "D20"/old preview date on every untouched page), footer, and JSON-LD still carrying
   Thomson Reserve facts — and each should be checked for its own hard-coded licence/account
   numbers per the finding above, not assumed identical to the other pages.
5. **YouTube channel link** in the footer (`youtube.com/@thomson-reserve`) — still points to
   Thomson Reserve's real channel; needs a real Chuan Grove channel or removal.
6. Everything still marked `TBC`: TOP/launch date, GBP Place ID, social handles, NAP phone
   number, full NAP block (street address/postal code — the GLS site doesn't have a public civic
   address yet), brand colors/logo.

## Suggested next step

`pricing.html` and `faq.html` are natural next targets — both reference the fabricated land
price ($1,178 psf ppr) and unit/tower breakdown that pricing analysis and buyer FAQs depend on.
Check each new page's footer for its own hard-coded licence/account numbers as you go (see the
C1555/762-333-930-4 finding above).
