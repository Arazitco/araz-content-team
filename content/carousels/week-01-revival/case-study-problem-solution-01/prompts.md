# Prompts — Mahtaj Skinland Design Breakdown Carousel (Day 4)

All slides using a screenshot are compositing prompts (real image +
text overlay), not generative-from-scratch prompts. Only Slide 8 is
purely generative (text-only).

## MASTER VISUAL PROMPT (Slides 1–7, compositing)
```
Composite each slide as 4:5 (1080x1350), using the real Mahtaj Skinland
homepage screenshot [IMAGE: mahtaj-homepage.png] as source, cropped per
slide:
Slide 1: full hero banner (ANUBIS sunscreen), dark gradient scrim, lower-
  third headline "چطور یه فروشگاه چندبرندی رو خوب می‌چینیم؟"
Slide 2: crop to the 4-category grid, top headline + supporting line
Slide 3: crop to one brand showcase section, minimal text overlay
Slide 4: crop to a product carousel row within a brand section
Slide 5: crop to the "درباره Mahtaj Skinland" section
Slide 6: wide crop spanning multiple sections to show color consistency,
  no text
Slide 7: full screenshot framed to emphasize mobile-viewport format
All slides: Persian-capable sans-serif, white text, RTL alignment, no
logo lock-in, no fabricated UI elements beyond what the screenshot shows.
```

## MASTER PROMPT (Slide 8, text-only, generative)
```
Vertical 4:5 (1080x1350) carousel end-card. Solid dark navy background
(#0f1b2d), no imagery. Centered Persian RTL text, white:
Line 1 (bold): "برای مشاوره طراحی سایت:"
Line 2: "۰۹۱۲۶۸۹۵۰۰۱"
No logo, generous margins.
```

## ALTERNATIVE PROMPT
For Slide 8: same text on a warm-gray (#2a2a2a) background variant,
matching the alternative used elsewhere in Week 1.

## REGENERATION / REVISION PROMPT
```
Regenerate [Slide N] keeping the same crop/layout system, replacing text
with "<new text>" or adjusting the crop to [new region of the screenshot].
```

## NEGATIVE / AVOID INSTRUCTIONS
- No fabricated "before" screenshot
- No claimed design rationale/intent beyond what's visible
- No business-result numbers or client-satisfaction claims
- No generic AI graphics, 3D objects, neon/glow, fake browser UI, or
  glassmorphism clutter
- No permanent brand color/logo treated as final

## Status
All 8 slides are speced; none are rendered yet, since the real
screenshot is not currently stored as a file in this session (see
`source-assets/README.md`). Once uploaded, Slides 1–7 can be composited
directly; Slide 8 can be generated immediately via the same local
rendering method used for other Week 1 text-only assets.
