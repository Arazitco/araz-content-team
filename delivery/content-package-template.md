# ArasSystem Content Package Templates (V1)

Per-format folder structures and document templates implementing
`delivery/output-standard.md`'s three mandatory layers. Naming follows
`delivery/file-naming-convention.md`; asset handling follows
`delivery/asset-delivery-rules.md`.

Every package's `delivery-manifest.md` is the owner's single checklist for
that item (template at the end of this file). No item is publishable
without one.

---

## Story Package Standard

```
content/stories/<cycle>/<story-id>/
  brief.md
  sequence.md
  copy.md
  design-direction.md
  prompts.md
  quality-review.md
  delivery-manifest.md
  source-assets/
  final-assets/
```

For each Story frame, `sequence.md` defines:
- Frame number
- Purpose
- Exact text
- Visual
- Layout
- Sticker (if applicable)
- Poll / Question / Quiz (if applicable)
- CTA
- Link (if applicable)
- Source asset
- Image-generation prompt (if required)
- Media status

**Do not force the same number of frames on every Story sequence** — frame
count follows the day's actual goal and material (see
`.claude/agents/story-producer.md`).

Final assets when generated: `story-01.png` / `.jpg`, `story-02.png`,
etc., following `delivery/file-naming-convention.md`. If a Story uses
video: `story-XX.mp4`.

---

## Reel Package Standard

```
content/reels/<cycle>/<reel-id>/
  brief.md
  script.md
  storyboard.md
  shot-list.md
  caption.md
  design-direction.md
  prompts.md
  quality-review.md
  delivery-manifest.md
  source-assets/
  final-assets/
```

Production information to include across these documents:
- Hook
- Spoken script
- On-screen text
- Scene-by-scene storyboard
- Shot list
- B-roll requirements
- Website screen-recording requirements
- Timing / pacing
- Transitions
- Audio direction (mood/style only — see `delivery/output-standard.md`)
- CTA
- Cover direction

`prompts.md` must include:
- **MASTER VIDEO PROMPT**
- **MASTER COVER PROMPT**
- **ALTERNATIVE VIDEO PROMPT**
- **REVISION PROMPT**

Final assets when generated: `reel-cover.png` / `.jpg`,
`reel-final.mp4`.

---

## Carousel Package Standard

```
content/carousels/<cycle>/<carousel-id>/
  brief.md
  structure.md
  copy.md
  design-direction.md
  prompts.md
  caption.md
  quality-review.md
  delivery-manifest.md
  source-assets/
  final-assets/
```

For every slide, `structure.md` defines:
- Slide number
- Role in narrative
- Exact copy
- Hierarchy
- Layout direction
- Visual/source requirement
- Generation prompt (when needed)

Final generated assets: `slide-01.png` / `.jpg`, `slide-02.png`, etc.

---

## Static Post Package Standard

```
content/posts/<cycle>/<post-id>/
  brief.md
  copy.md
  caption.md
  design-direction.md
  prompts.md
  quality-review.md
  delivery-manifest.md
  source-assets/
  final-assets/
```

Generated asset when available: `post-final.png` / `.jpg`.

---

## Portfolio Content Package Additions

Portfolio packages (built by `portfolio-producer`) use the Reel,
Carousel, Static Post, and/or Story structures above depending on which
formats the portfolio pack includes, plus these additional required
fields in `brief.md`:

- Client/project identifier
- Project URL
- Source screenshots (listed, referencing `source-assets/`)
- Source videos (listed, referencing `source-assets/`)
- Project status: **WIP** / **COMPLETED**
- What was built
- Why design decisions were made
- Real problem being addressed
- Factual claims available
- Claims that must **NOT** be made (see `delivery/asset-delivery-rules.md`
  — never invent conversion/revenue/SEO/traffic improvements or client
  outcomes without verified data)
- Missing client information
- Owner input required

Portfolio media packages may combine any of: Website walkthrough Reel,
Before/After, Carousel case study, Static showcase, Story sequence, Mobile
showcase, UX explanation — matching `strategy/content-pillars.md`'s
Portfolio & Case Studies pillar.

### Portfolio Analysis Template

For every website portfolio project, `portfolio-producer` creates one
`portfolio-analysis.md` at
`content/portfolio/<cycle>/<project-id>/portfolio-analysis.md`, produced
after `asset-researcher` and before `creative-director` (see the
Production Pipeline in `.claude/agents/portfolio-producer.md`). It is
project-level — shared context for whichever Reel/Carousel/Story/Post
packages get produced from it — not a replacement for any package's own
`brief.md`.

```markdown
# Project Overview

Client:
Industry:
Website URL:


# Available Assets

Screenshots:
Videos:
Other materials:


# Design Highlights

Visible design strengths only.

Do not invent business results.


# Content Opportunities

Possible:
- Reel angle
- Carousel angle
- Story angle


# Missing Information

Owner input required.
```

Any asset `asset-researcher` could not acquire is listed under Available
Assets as an outstanding `OWNER ASSET REQUIRED` item (see
`.claude/agents/asset-researcher.md`), not silently omitted.

---

## Delivery Manifest Template

Every content package's `delivery-manifest.md`:

```markdown
CONTENT ID:
CONTENT TYPE:
VERSION:

DOCUMENTS:
[ ] Brief
[ ] Final Copy
[ ] Structure / Script
[ ] Design Direction
[ ] Prompts
[ ] Caption
[ ] Quality Review

MEDIA:
[ ] PNG/JPG generated
[ ] MP4 generated
[ ] Cover generated
[ ] Source assets present

MEDIA STATUS:
- READY / PARTIALLY READY / PENDING EXTERNAL GENERATION

QUALITY STATUS:
- DRAFT / NEEDS REVISION / QUALITY APPROVED

OWNER STATUS:
- NOT REVIEWED / REVISION REQUESTED / OWNER APPROVED

PUBLISHING STATUS:
- NOT READY / READY AFTER OWNER APPROVAL / PUBLISHED

Missing items:
Owner input required:
External generation required:
Known limitations:
```

This manifest is the single source of truth for where a content item
stands. `quality-editor` updates QUALITY STATUS; the owner (via
`content-manager`) updates OWNER STATUS; `publisher` updates PUBLISHING
STATUS and only acts when QUALITY STATUS = QUALITY APPROVED **and** OWNER
STATUS = OWNER APPROVED.
