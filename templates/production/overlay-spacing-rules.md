# Overlay & Spacing Rules (V1)

Consistent scrim, margin, and spacing rules across every template and
production route, so a multi-slide/multi-frame piece reads as one
coherent, professionally art-directed set.

## Scrim / Overlay

- Use a **short, soft, multi-stop gradient** (not a flat dark block) when
  text needs contrast against a busy background — fading from a modest
  peak opacity down to fully transparent within roughly a third to just
  under half of the frame's height.
- Prefer the lightest peak opacity that still keeps text legible. Bump it
  slightly only where the background is genuinely busy right behind the
  text (e.g. a photo with high-contrast detail) — never as a default.
- Never let a scrim's darkened band cover a website detail the slide is
  actually about (a button, a product card, a headline in the source
  UI) — reposition the text/scrim or adjust the crop instead.
- Never use a heavy drop shadow behind text as the primary legibility
  mechanism — the scrim, not the shadow, should carry contrast. A very
  subtle shadow (near-imperceptible) is acceptable as a secondary aid.

## Margins & Alignment

- Keep left/right text margins consistent across every slide/frame in
  one set (a single piece should not visibly shift its margins slide to
  slide).
- Keep vertical text position consistent by role: headline always at the
  same relative position (top-anchored or bottom-anchored per the
  template) across the set, not alternating without reason.
- Center-align Persian RTL text by default unless a template specifies
  otherwise.

## Hierarchy & Line-Height

- Maintain a clear size/weight gap between headline and supporting copy
  — see `templates/production/typography-system.md` for the exact
  weights.
- Give supporting copy enough margin-top from the headline that the two
  don't read as one run-on block (roughly half the headline's font size,
  as a starting point — adjust per composition).
- Use generous line-height (roughly 1.3–1.45× font size) — cramped
  Persian text is both harder to read and looks unpolished.

## When To Adjust a Crop Instead of the Overlay

If no combination of scrim/position solves a legibility or collision
problem, adjust the screenshot's crop region (per
`templates/production/screenshot-treatment.md`) rather than escalating
the overlay's darkness or size — a lighter overlay over a well-chosen
crop reads as more professional than a heavy overlay forcing text over a
bad crop.
