# Template: Portfolio Design Breakdown Carousel (V1)

Distilled from the completed Mahtaj Skinland carousel production run —
extracting only reusable principles, never Mahtaj's client-specific
colors, copy, or content as if they were universal brand rules.

## When To Use
A completed-project portfolio carousel that walks through real website
screenshots as an editorial design breakdown (not a sales pitch, not a
fabricated case study with invented results).

## 1. Content Structure

```
Slide 1 — Hook / project framing
Slide 2 — Primary navigation/category observation
Slide 3 — Brand/content structure observation
Slide 4 — Product/content presentation observation
Slide 5 — Trust/about/contact observation
Slide 6 — Mobile/responsive observation
Slide 7 — ArasSystem CTA
```

This 7-slide shape is a default, not a fixed requirement. Adapt the
count and order when the real website genuinely doesn't contain one of
these elements (e.g. no mobile-breakpoint capture available, no
about/contact section) — **never invent a section just to fill a slot.**
Every slide's copy must be purely observational (what is visibly true on
the real screenshot), never a claimed rationale, business result, or
invented visitor intent.

## 2. Visual Structure

- Real website screenshot, cropped tightly per slide to the specific
  element being discussed — never a full-page screenshot shrunk down to
  illegibility.
- Screenshot stays visually dominant; typography is secondary.
- One headline + at most one short supporting line per slide (except a
  pure text-only CTA slide, which may center both lines).
- A short, soft gradient/translucent scrim only where legibility genuinely
  requires it — never a heavy dark block, never covering the specific
  element the slide is about.
- Consistent alignment and margins across every slide in the set (see
  `templates/production/overlay-spacing-rules.md`).
- Final slide (CTA) is the one slide that may use a solid brand-neutral
  background with no imagery.

## 3. Production Rules

- Output: 1080×1350 (4:5), consistent across every slide.
- Typography: per `templates/production/typography-system.md` (current
  standard: Vazirmatn Bold / Medium / ExtraBold) — never FreeSans in
  final production.
- Screenshot treatment: per `templates/production/screenshot-treatment.md`
  — real screenshots only, no AI reconstruction of website UI, ever.
- Route this template through **Route A (Deterministic Local Render)**
  per `.claude/agents/production-connector.md`'s Production Routing —
  Canva cannot ingest private local screenshots without publishing them,
  which this system never does.
- Export: PNG, named per `delivery/file-naming-convention.md`.
- No AI-recreated UI, no invented sections, no invented products, no
  invented business results — ever.
- Professional agency presentation throughout: editorial, calm,
  restrained — the screenshot is the evidence, not a backdrop for
  decorative typography.

## Known Adaptation Notes (from Mahtaj)

- If a real capture proves the site's responsive/mobile breakpoint
  (e.g. a visible hamburger menu at a narrower browser width) rather than
  a literal phone-width capture, that capture may honestly support a
  "mobile view" claim — state this plainly to the owner rather than
  silently treating a desktop capture as mobile.
- If a slide's initial text size causes the headline to wrap into 3 lines
  and collide with page content below it, reduce headline size and/or
  adjust the crop's vertical framing (a crop change is allowed when
  required for text spacing, per `templates/production/overlay-spacing-rules.md`)
  rather than covering important website details with text.
