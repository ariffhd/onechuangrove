# Fork status — One Chuan Grove (Chuan Grove GLS)

Forked from [ariffhd/thomsonreserve](https://github.com/ariffhd/thomsonreserve) on 2026-09-15,
per `new-launch-site-shell-checklist-TEMPLATE.md`. This file tracks what's done vs. still
pending so nobody mistakes a mechanical rename for a finished, publish-ready site.

## ✅ Done (mechanical Section 1 pass)

- Fresh git history (no Thomson Reserve commits carried over)
- Domain: `thomson-reserves.sg` → `onechuangrove.sg` (~2,900 text replacements across 27 files)
- Brand name: "Thomson Reserve(s)" → "One Chuan Grove" (all case variants, incl. URL-encoded)
- Developer's registered address → **96 Robinson Road, #10-01 SIF Building, Singapore 068899**
  (Chuan Grove Pte. Ltd.'s actual address per URA Developer's Licence C1558 — verified, not guessed)
- Phone number, WhatsApp links, Facebook handle → neutralized to `[TBC]` / `#tbc-facebook-handle`
  (Thomson Reserve's real contact details must never appear live on this site)
- Geo coordinates → set to Lorong Chuan MRT's public coordinates (1.35167, 103.86389) as an
  **approximate stand-in only** — replace with the actual site coordinates once the GBP listing exists
- `staged-articles/chuan-grove-gls/` created (empty, per Section 1.3–1.4)
- `.github/workflows/deploy.yml` deploy path updated to `onechuangrove.sg/public_html/`
  (FTP secrets not configured — no remote/CI set up yet)

## ⚠️ NOT done — needs manual content work, not find-replace

These are flagged rather than guessed, per the checklist's explicit instruction not to invent facts:

1. **Background story (index.html)** — still tells Thomson Reserve's *en bloc* story (former
   Thomson View Condominium collective sale). Chuan Grove is a **GLS** site — this section needs
   a full rewrite using the real GLS facts (two-site tender: 8 Jul 2025 & 4 Sep 2025 closings,
   $703.6M/$1,376psf ppr and $623.9M/$1,331psf ppr, JV of Sing Holdings + Sunway Developments).
2. **Address locality/region fields in JSON-LD** — several files still say `"Upper Thomson"` /
   `District 20` inside schema blocks and body copy (my text pass caught the literal brand name
   and one logo subtext string, not every embedded location reference).
3. **Hero `<h1>`** in index.html — markup is `Thomson<em>Reserve</em>` (no space, styled split);
   needs hand-editing to `One Chuan<em> Grove</em>` or similar, not a plain string swap.
4. **Developer / Project Core section** — Thomson Reserve is a 3-way JV (CapitaLand, UOL,
   Singapore Land — 3 logo files + 3 sub-cards). Chuan Grove is a **2-way JV** (Sing Holdings +
   Sunway Developments). This needs a structural edit (remove a sub-card, swap logos), not text
   substitution.
5. **All images/PDFs** (`thomson-reserve-*.jpg/.png`, floor plan PDF, 3 developer logos) are
   Thomson Reserve's real marketing photos and competitors' real logos. They are still referenced
   by filename throughout the site (now under the `onechuangrove.sg` domain, which is misleading —
   these are NOT Chuan Grove's real photos). **Do not deploy this site with these assets in place.**
   Full list: see `find . -iname "thomson-reserve-*"` and the 3 developer logo PNGs.
6. **8 inherited content pages** (`ai-tong-school-1km-condo.html`, `bright-hill-drive.html`,
   `macritchie-reservoir-condo.html`, `upper-thomson-mrt.html`, `balance-units-chart.html`,
   `new-launch-vs-resale-district-20.html`, `thomson-reserve-vs-amo-residence.html`,
   `thomson-reserve-vs-jadescape.html`) are Thomson Reserve's topical-map cluster articles —
   real facts about a different location. Per Section 5 of the checklist, Chuan Grove needs its
   own fresh topical map, not these find-replaced. Left in place (unlinked from nowhere new) —
   decide whether to delete or repurpose as structural templates only.
7. **YouTube channel links** (`youtube.com/@thomson-reserve`) — still point to Thomson Reserve's
   channel; need a real Chuan Grove channel or removal.
8. Everything still marked `TBC` in Section 0: TOP/launch date, GBP Place ID, social handles,
   NAP phone number, full NAP block, brand colors/logo.

## Suggested next step

Rewrite `index.html`'s Background Story section with the real GLS facts (already gathered),
since it's the highest-visibility section and the facts are on hand. Then tackle the Developer/
Project Core JV restructuring (3 cards → 2 cards).
