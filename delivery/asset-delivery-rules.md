# ArasSystem Asset Delivery Rules (V1)

Governs how source and generated assets are stored, separated, and
exported across every content package. Works together with
`delivery/output-standard.md` (what must be delivered) and
`delivery/file-naming-convention.md` (how it's named).

## Source vs. Generated Assets

Every content package folder separates two asset types:

- **`source-assets/`** — files supplied by the owner/client, or captured
  directly from a verified project source (e.g. a real website
  screenshot, a client-provided photo/video, a verified project URL
  recording). These are factual inputs.
- **`final-assets/`** — generated or edited publication-ready output (the
  actual PNG/JPG/MP4 produced for this content item).

**Never overwrite a source asset.** **Never modify the only copy of a
source asset.** If a source asset needs editing (cropping, color
correction, etc.), the edited result goes into `final-assets/` as a new
file — the original stays untouched in `source-assets/`.

## Portfolio Source Integrity

Portfolio content carries additional source-integrity requirements (see
`.claude/agents/portfolio-producer.md` and
`delivery/content-package-template.md`):

- Every portfolio package must record the client/project identifier and
  project URL (when public), and list exactly which source screenshots
  and videos were used.
- Project status (WIP / COMPLETED) must be explicit.
- What was built, why design decisions were made, and what real problem
  was addressed must be stated from confirmed project details only.
- Factual claims available vs. claims that must NOT be made (see below)
  must both be listed, along with missing client information and any
  owner input still required.

## Never Invent

Never invent, in any package, regardless of format:
- Conversion increases
- Revenue increases
- SEO improvements
- Traffic increases
- Client outcomes or testimonial content

...unless verified data exists and is explicitly cited. Absent evidence,
state the claim is unavailable rather than approximating one.

## Media Dimensions (Export Guidance)

Recommended Instagram-oriented export dimensions/aspect ratios. These are
**export guidance, not permanent platform guarantees** — verify against
current Instagram specifications if they materially change in the future.

| Format | Recommended Aspect Ratio | Notes |
|---|---|---|
| Story | 9:16 | Full-screen vertical |
| Reel | 9:16 | Full-screen vertical |
| Reel cover | 9:16 (crop-safe center) | Must read clearly as a static thumbnail |
| Feed portrait (single image/video) | 4:5 | Instagram's current preferred feed portrait ratio |
| Carousel (per slide) | 4:5 (consistent across all slides) | All slides in one carousel should share one ratio |
| Static post | 1:1 or 4:5 | 4:5 preferred for more feed real estate; 1:1 acceptable when the composition needs it |

## Quality & Delivery Completeness

`quality-editor` checks both content quality and delivery completeness —
a package is not QUALITY APPROVED if required assets are missing without
being explicitly marked `MEDIA STATUS: PENDING EXTERNAL GENERATION` (see
`delivery/output-standard.md`). `publisher` only uses assets from
`final-assets/` that are both QUALITY APPROVED and OWNER APPROVED — never
a source asset, a draft, or a pending-generation placeholder.
