# Canva Production Test — Mahtaj Skinland Carousel (Day 4)

First test of the Production Connector's Canva workflow
(`.claude/agents/production-connector.md`), run against the existing
approved Mahtaj Skinland carousel package at
`content/carousels/week-01-revival/case-study-problem-solution-01/`.
This is a production brief, not a new creative direction — copy,
structure, and design-direction are unchanged from that package.

## 1. Production Connector Review

Reviewed:
- `copy.md` — 7 lines, fully observational, unchanged.
- `design-direction.md` — 4:5 frame, screenshot-composite Slides 1–6,
  text-only end card Slide 7, no permanent brand lock-in.
- `prompts.md` — MASTER VISUAL PROMPT (Slides 1–6, compositing) and
  MASTER PROMPT (Slide 7, generative).
- `structure.md` — per-slide purpose, headline, crop direction.
- Quality requirements — `delivery/output-standard.md`,
  `delivery/asset-delivery-rules.md`.

**Blocking fact found:** `source-assets/README.md` confirms the one
real Mahtaj Skinland homepage screenshot this package is built on is
still not stored as an image file in this repository (viewed and
described only, after two supply attempts). Slides 1–6 all require that
real screenshot as a compositing background per `prompts.md`. Slide 7 is
the only slide with no image dependency — text-only end card.

## 2. Canva Production Brief

**Canvas size:** 1080×1350 (Instagram Carousel, 4:5) — matches
`delivery/asset-delivery-rules.md`'s Carousel guidance.

**Slide count:** 7 slides.

**Typography (per this test's explicit instruction):**
- Headline: Peyda ExtraBold
- Body: IRANSans
- CTA: Peyda Bold

Per `brand/visual-identity.md` (status: PENDING REDESIGN) and the Visual
Identity Rule in `delivery/output-standard.md`, this typography is
applied for this production test only — it is not a locked-in permanent
brand choice. If the exact fonts aren't available in the connected tool,
use a clean Persian-capable fallback while preserving correct RTL
rendering.

**Layout direction (per `design-direction.md` / `structure.md`):**
- Slides 1–6: real homepage screenshot (cropped per slide) full-bleed,
  gradient scrim for text legibility, one headline + at most one
  supporting line, per-slide crop per `structure.md`.
- Slide 7: solid dark navy background (#0f1b2d), no imagery, centered
  Persian RTL text, generous margins — the one CTA-forward slide.

**Image requirements:**
- 1 real Mahtaj Skinland homepage screenshot (mobile viewport,
  1080px+ width) — required for Slides 1–6. **Not currently available
  in this repository/session** (see Blocking fact above).
- Slide 7 needs no image.

**Brand requirements:**
- `BRAND VISUAL STATUS: FLEXIBLE — FINAL IDENTITY PENDING`.
- No permanent logo, color, or font treated as final.
- No generic AI graphics, 3D objects, neon/glow, fake browser UI, or
  glassmorphism clutter (per `design-direction.md`).
- No fabricated "before" version of the site; no claimed design
  rationale beyond what the real screenshot shows.

**Export settings:**
- Format: PNG
- Resolution: 1080×1350 per slide
- Naming: per `delivery/file-naming-convention.md`
  (`<date>-carousel-mahtaj-skinland-slide-0N-v01.png`)

## 3. Canva Integration Status

Canva integration **is** available in this session.

**Slide 7 (text-only, no missing-asset dependency):** prepared for real.
4 Canva design candidates were generated
(job `04fee2fc-8aa0-4070-93c0-d5444949cfa3`) matching the exact approved
Slide 7 copy and layout:
- https://design.canva.ai/KtbDA_lNyVT7VLh
- https://design.canva.ai/pJBJga_VVvJhHe_
- https://design.canva.ai/Z_liICzLcrcU4ja
- https://design.canva.ai/GBKcg3Jo2MsWXh1

None of these has been converted to an editable Canva design yet — that
happens only after the owner picks a candidate (see owner review file).

**Slides 1–6:** NOT prepared in Canva. Compositing them would require
either (a) the real homepage screenshot as source material, or (b)
generating a substitute image — and (b) is forbidden by the REAL ASSET
PRESERVATION RULE (`.claude/agents/media-producer.md`) and Production
Connector Rule 1 ("never create fake final files"). No Canva design was
created for Slides 1–6.

## 4. CANVA ACTION REQUIRED

```
CANVA ACTION REQUIRED

Slides affected: 1, 2, 3, 4, 5, 6 (of 7)
Blocking reason: the real Mahtaj Skinland homepage screenshot is not
present as an image file in this repository/session — only described in
source-assets/README.md.

Manual steps needed:
1. Owner supplies the real homepage screenshot (mobile viewport,
   1080px+ width) through a method that results in a stored file — e.g.
   uploading it directly into a Canva design, or placing the file where
   this session's tools can access it (pasting/attaching in this chat
   has not worked for this project after two attempts).
2. Once the file exists, production-connector re-runs this Canva
   Production Brief for Slides 1-6, preparing the compositing
   instructions (crop per structure.md) with that real image as
   background.
3. media-producer (or the owner directly in Canva) composites the text
   overlays per prompts.md's MASTER VISUAL PROMPT.
4. Export each slide as PNG 1080x1350 per
   delivery/file-naming-convention.md.
```

## Status

- Slide 7: 4 real Canva candidates ready for owner selection.
- Slides 1–6: blocked on the real source screenshot — `CANVA ACTION
  REQUIRED` above.
- No final-assets/ files exist yet for this package. Nothing here has
  been claimed as produced beyond what is actually true.
