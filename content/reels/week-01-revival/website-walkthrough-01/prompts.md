# Prompts — Carlin Ladies Website Walkthrough Reel (Day 1)

Built from 3 real supplied screenshots (see `source-assets/README.md`),
animated via pan/zoom — not AI-generated imagery. These are
editing/compositing prompts for a human motion designer or an AI video
tool that accepts real images as input.

## MASTER VIDEO PROMPT
```
Assemble a 9:16, ~30-second vertical Reel using 3 real supplied
screenshots as input images (no generated imagery):
[IMAGE 1: carlin-homepage.png] — Carlin Ladies homepage, mobile viewport
[IMAGE 2: carlin-product-page.png] — "کت کرپ صدف" product page, mobile viewport
[IMAGE 3: carlin-shop-page.png] — shop/category listing page with filter sidebar, mobile viewport

Scene plan (per storyboard.md, revised per owner review):
1. 0–2s: IMAGE 1, hero section, slow zoom-in. Text: "از دسته‌بندی تا تکمیل ست؛ یه نگاه به جزئیات فروشگاه Carlin Ladies."
2. 2–6s: IMAGE 1, pan down through Top Categories + On Sale/New In/Most Loved. Text: "دسته‌بندی‌ها از همون ابتدای صفحه در دسترسن"
3. 6–11s: IMAGE 2, pan across gallery/price/size chart. Text: "اطلاعات محصول، قیمت و راهنمای سایز کنار هم"
4. 11–17s: IMAGE 2, crop-zoom into the "این آیتم‌ها را می‌توانید همراه این محصول ست کنید" cross-sell block. Text: "پیشنهاد تکمیل ست، زیر همون محصول"
5. 17–23s: IMAGE 3, pan from category icon row to the filter sidebar. Text: "فیلترهای مختلف برای مرور محصولات"
6. 23–27s: IMAGE 2 (trust badges) and/or IMAGE 1 (Our Story section), gentle zoom. Text: "بخش‌های معرفی و اطلاعات تکمیلی برند"
7. 27–30s: static end card. Text: "نمونه‌کارهای بیشتر رو تو آراز سیستم ببینید"

Motion: slow pans/zooms only, max ~8% scale change, no spins/glitches.
Text placement: top or bottom safe-zone gradient scrim, never covering
key UI elements (price, buttons, filters).
Typography: modern, minimal, Persian-capable sans-serif, white, short
lines (~6 words max).
Aspect ratio: 9:16, 1080×1920 export.
Audio: calm modern instrumental, low volume (mood/style only, no
confirmed track).
Exclude: fake browser UI, invented interface elements, 3D objects, neon/
glow effects, gradients not present in the real screenshots, any
permanent brand color/logo treated as final.
```

## MASTER COVER PROMPT
```
Use IMAGE 1 (Carlin Ladies homepage hero — woman in brown coat set) as
the 9:16 (1080×1920) cover background, full-bleed, no crop distortion.
Overlay the headline "از دسته‌بندی تا تکمیل ست؛ یه نگاه به جزئیات فروشگاه
Carlin Ladies." in the lower third, white Persian-capable bold sans-serif,
RTL alignment, on a subtle dark gradient scrim. No logo lock-in.
```

## ALTERNATIVE VIDEO PROMPT
```
Same 3 real images and scene plan, but present Scenes 2–3 as a single
continuous "scroll simulation" pan (one uninterrupted top-to-bottom
motion across IMAGE 1 into IMAGE 2, treated as if it were one long page)
rather than a hard cut between them — testing a more continuous-feeling
edit style.
```

## REGENERATION / REVISION PROMPT
```
Re-edit Scene [N]: [describe change, e.g. "crop tighter on the size chart
in Scene 3" / "replace headline text with: <new text>" / "extend Scene 4
by 2s"]. Keep all other scenes, images, and exclusions from the Master
Video Prompt unchanged.
```

## NEGATIVE / AVOID INSTRUCTIONS
- No fake browser chrome or fabricated UI not present in the real
  screenshots
- No generic AI graphics, 3D renders, glow/neon effects, meaningless
  gradients, random icons, or glassmorphism
- No stock photography substituting for the real product photos
- No permanent/final brand color, logo, or font treated as locked
- No exaggerated on-screen claims (no "#1", "guaranteed", conversion %)
- No covering the real UI's price, buttons, or filter controls with text

## Portability Note
These prompts describe composition, motion, and exclusions explicitly
enough for any video-editing AI tool or human motion designer to execute
— but they require the 3 real image files, which are supplied-but-not-yet-
stored (see `brief.md` for the file-upload request).
