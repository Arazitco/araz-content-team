# Typography System — Current Production Standard (V1)

**This is the CURRENT PRODUCTION STANDARD, not permanent ArasSystem brand
identity.** Per `brand/visual-identity.md` (status: PENDING REDESIGN),
the owner may replace this typography when the final visual identity is
approved — nothing here should be treated as locked in.

## Current Approved Fonts

Font files live in `brand/typography/fonts/`:
- `Vazirmatn-Medium.ttf`
- `Vazirmatn-Bold.ttf`
- `Vazirmatn-ExtraBold.ttf`

## Hierarchy

- **Persian headline:** Vazirmatn Bold
- **Persian supporting copy:** Vazirmatn Medium
- **Selective emphasis only** (e.g. a Hook slide that genuinely needs
  stronger weight): Vazirmatn ExtraBold — not used everywhere.

## Rules

- Do not use FreeSans for final Persian production — it was only ever an
  honest fallback while Vazirmatn was unavailable, never the standard.
- Do not use ExtraBold everywhere — it's for selective emphasis, not a
  default weight.
- Avoid oversized typography — reduce headline size when text wraps to
  more lines than the layout has room for, rather than letting it
  collide with important content.
- Avoid heavy text shadows — prefer a subtle gradient/overlay for
  contrast (see `templates/production/overlay-spacing-rules.md`).
- Maintain clean RTL layout — correct Persian shaping and right-to-left
  flow at all times.
- Use sufficient line-height and whitespace — cramped text reads as
  unprofessional.
- Use a subtle gradient/overlay only when contrast actually requires it —
  never as decoration.
- **A website screenshot must remain more visually important than
  decorative typography** — typography supports the evidence, it is
  never the point of the slide.

## Fallback Rule

If, in a future session, the Vazirmatn font files are unavailable (e.g. a
fresh environment without `brand/typography/fonts/` installed), **do not
silently fall back to a generic system font (e.g. FreeSans/DejaVu Sans)
for final production media.** Instead:

a) Use another **explicitly owner-approved** professional Persian font,
   if one has been designated, exactly as if it were Vazirmatn (same
   Bold/Medium/ExtraBold hierarchy rules above); or
b) If no approved alternative exists, stop and report:

   ```
   TYPOGRAPHY ASSET REQUIRED

   Need: Vazirmatn-Bold.ttf / Vazirmatn-Medium.ttf / Vazirmatn-ExtraBold.ttf
         (or another owner-approved Persian font)
   Reason: <content item> requires final Persian typography and no
           approved font is available in this session
   ```

   and do not produce final media for the affected item until the font
   is available — the same way a missing screenshot blocks only the
   slides that depend on it (see
   `.claude/agents/asset-researcher.md`), a missing approved font blocks
   only final-media production, not draft/specification work.

A generic-font render may still be used for an internal **draft
preview** explicitly labeled as such (never presented as final), exactly
as FreeSans draft previews were labeled and later replaced once
Vazirmatn became available in this project's own history — but it must
never be delivered or approved as final production media.
