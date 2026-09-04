# Screenshot Treatment Rules (V1)

Governs how real website/product screenshots may be used in production,
across every template and every production route. This is a
specialization of the REAL ASSET PRESERVATION RULE in
`.claude/agents/media-producer.md` — read that rule first.

## What Is Allowed
- Cropping to a specific region of a real screenshot.
- Scaling/resizing (including upscaling a smaller capture) as long as the
  result is not misrepresented as higher native resolution than it is.
- Panning and zooming (including slow Ken-Burns-style motion for Reels).
- A soft, translucent scrim/gradient behind text for legibility.
- Rounded corners, drop shadows, or a card-style frame around the
  screenshot, if it matches the template's visual structure.

## What Is Never Allowed
- Regenerating, redrawing, or "improving" the website's UI with AI.
- Replacing a real screenshot with an AI-recreated interface that merely
  resembles it.
- Inventing a page, section, or product that wasn't actually captured.
- Fabricating a "before" state of a site with no such asset.
- Claiming a screenshot represents a viewport (e.g. "mobile") it doesn't
  actually represent — verify what the capture actually shows (e.g. a
  visible mobile hamburger menu) before pairing it with a viewport claim,
  and flag any imperfect match to the owner rather than asserting it
  silently.

## Verification Before Use
Before compositing any screenshot into a production output:
1. Confirm the file actually exists on disk (not just "was shown in
   chat" — see the Asset Acquisition Rules in
   `.claude/agents/asset-researcher.md`).
2. Confirm its real dimensions and orientation.
3. Confirm which page/section it actually shows, by direct inspection —
   never assume from a filename or from an earlier chat description
   alone if the file is available to view.

## Cropping for Text Spacing
A screenshot's crop region may be adjusted specifically to give overlay
text room to breathe, or to avoid text colliding with important website
detail (a button, a headline, a product card) — this is a legitimate,
allowed adjustment, not a content change, as long as the crop still
shows real, unaltered pixels from the source file.
