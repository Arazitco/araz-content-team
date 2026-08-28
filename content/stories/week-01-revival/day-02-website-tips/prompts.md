# Prompts — Website Tips Story (Day 2)

These frames were actually rendered locally in this session (real
generation, not a specification-only placeholder) — see `final-assets/`
and `delivery-manifest.md`. The prompts below let the owner reproduce or
regenerate the same concept in another tool.

## MASTER PROMPT (Frame 1)
```
Vertical 1080x1920 Instagram Story graphic. Solid dark navy background
(#0f1b2d), no imagery, no logo. Centered, right-to-left Persian text in
white, large bold sans-serif, two short lines:
Line 1: "کاربر تو چند ثانیه اول تصمیم می‌گیره بمونه یا بره."
Line 2 (smaller, below): "صفحه اول سایتتون همین الان چی نشون میده؟"
Generous margins (~80px), no borders, no additional graphic elements.
Aspect ratio: 9:16. Do not add any logo, brand color, or icon.
```

## MASTER PROMPT (Frame 2)
```
Same visual system as Frame 1 (1080x1920, #0f1b2d background, centered
white Persian sans-serif text, RTL). Text:
Line 1: "بیشتر بازدیدکننده‌ها از موبایل وارد سایت میشن."
Line 2: "سایتتون رو این هفته با موبایل خودتون چک کردید؟"
Same exclusions as Frame 1.
```

## MASTER PROMPT (Frame 3)
```
Same visual system as Frames 1–2 (1080x1920, #0f1b2d background, centered
white Persian sans-serif text, RTL), but leave the lower third of the
frame empty/uncluttered to accommodate a Question Box sticker added
afterward. Text (upper two-thirds):
Line 1: "یه سوال ساده: وقتی کاربر وارد سایتتون میشه، دقیقاً می‌دونه قدم بعدی چیه؟"
Line 2: "اگه سوالی درباره سایتتون دارید، تو پیام بپرسید."
Same exclusions as Frame 1.
```

## ALTERNATIVE PROMPT (any frame)
```
Same text and layout as the Master Prompt, but on a neutral warm-gray
background (#2a2a2a) instead of navy, testing an alternate neutral tone
while remaining non-brand-locked.
```

## REGENERATION / REVISION PROMPT
```
Regenerate [Frame N] with the same visual system, replacing the text
with: "<new text>". Keep background color, typography, and margins
identical to the original Master Prompt.
```

## NEGATIVE / AVOID INSTRUCTIONS
- No logos, icons, or brand marks
- No stock photography or illustrations
- No more than 2 lines of primary text per frame
- No color implying a final/approved brand palette

## How These Were Actually Generated
Rendered via a local headless-browser HTML/CSS render (Chromium via
Playwright, pre-installed in this environment) — a deterministic layout
render, not a generative AI image model. This is disclosed for
transparency; the prompts above are written to be reproducible in an
actual AI image tool as well, per the Prompt Portability Requirement.
