# Prompts — Mahtaj Skinland Design Breakdown Carousel (Day 4)

Revised per Owner Review: 7 slides (down from 8), copy made fully
observational. All slides using a screenshot are compositing prompts
(real image + text overlay), not generative-from-scratch prompts. Only
Slide 7 is purely generative (text-only).

## MASTER VISUAL PROMPT (Slides 1–6, compositing)
```
Composite each slide as 4:5 (1080x1350), using the real Mahtaj Skinland
homepage screenshot [IMAGE: mahtaj-homepage.png] as source, cropped per
slide:
Slide 1: full hero banner (ANUBIS sunscreen), dark gradient scrim, lower-
  third headline "فروشگاه چندبرندی روی موبایل چطور دیده می‌شه؟"
Slide 2: crop to the 4-category grid, top headline "دسته‌های اصلی از
  ابتدای صفحه در دسترسن." + supporting line "پا و ناخن، بدن، مو، صورت."
Slide 3: crop to one brand showcase section, headline "برای هر برند، بخش
  جدا با تصویر و محصولات همون برند دیده می‌شه." + supporting line "ANUBIS،
  TANURA، TIBERM."
Slide 4: crop to a product carousel row within a brand section, headline
  "محصولات هر برند داخل همون صفحه به‌صورت کاروسل نمایش داده می‌شن."
Slide 5: crop to the "درباره Mahtaj Skinland" section, headline "بخش
  درباره ما و راه‌های ارتباطی هم در ادامه صفحه قرار گرفتن."
Slide 6: full screenshot framed to emphasize mobile-viewport format,
  headline "در نمای موبایل، بخش‌ها به‌صورت عمودی و پشت‌سرهم دیده می‌شن."
All slides: Persian-capable sans-serif, white text, RTL alignment, no
logo lock-in, no fabricated UI elements beyond what the screenshot shows,
no claimed rationale — headline text states only what's observably true.
```

## MASTER PROMPT (Slide 7, text-only, generative)
```
Vertical 4:5 (1080x1350) carousel end-card. Solid dark navy background
(#0f1b2d), no imagery. Centered Persian RTL text, white:
Line 1 (bold): "برای مشاوره طراحی سایت:"
Line 2: "۰۹۱۲۶۸۹۵۰۰۱"
No logo, generous margins.
```

## ALTERNATIVE PROMPT
For Slide 7: same text on a warm-gray (#2a2a2a) background variant,
matching the alternative used elsewhere in Week 1.

## REGENERATION / REVISION PROMPT
```
Regenerate [Slide N] keeping the same crop/layout system, replacing text
with "<new text>" or adjusting the crop to [new region of the screenshot].
```

## NEGATIVE / AVOID INSTRUCTIONS
- No fabricated "before" screenshot
- No claimed design rationale/intent beyond what's visible (e.g. do not
  say a section exists "for" a particular visitor need, or that a layout
  was "designed for" mobile — state only that it appears/exists)
- No business-result numbers or client-satisfaction claims
- No generic AI graphics, 3D objects, neon/glow, fake browser UI, or
  glassmorphism clutter
- No permanent brand color/logo treated as final

## Status
7 slides are speced; none are rendered yet, since the real screenshot is
not currently stored as a file in this session (see
`source-assets/README.md`). Once stored, Slides 1–6 can be composited
directly; Slide 7 can be generated immediately via the same local
rendering method used for other Week 1 text-only assets, or a
professional design pass per the Visual Quality Note applied elsewhere
in Week 1.
