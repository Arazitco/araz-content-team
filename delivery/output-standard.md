# ArasSystem Content Delivery Standard (V1)

Defines exactly what the owner must receive for every production-ready
Instagram content item — Story, Reel, Carousel, Static Post, or Portfolio
package. This is a system-design standard: it governs the *shape* of
delivery, not the content of any specific piece. See
`delivery/content-package-template.md` for per-format templates,
`delivery/file-naming-convention.md` for naming/versioning, and
`delivery/asset-delivery-rules.md` for source/final asset handling.

## Core Owner Requirement

A content package is never text-only. Every final content item must
deliver, where applicable to its format:

1. Strategic Brief
2. Final Copy
3. Content Structure (script / storyboard / slide structure / sequence)
4. Design Direction
5. Production Instructions
6. Image Generation Prompt
7. Video Generation Prompt
8. External Tool / Alternative Prompts
9. Final PNG/JPG files — when generation capability is available
10. Final MP4 file — when generation capability is available
11. Source Asset Checklist
12. Quality Review
13. Approval Status
14. Publishing Status

This lets the owner review the strategy, review the exact text, understand
the visual direction, inspect the final media, regenerate/check the media
in another AI tool, request revisions, or manually publish approved assets
if they choose to.

## The Media Rule: Specification vs. Generated Media

The system must always distinguish:

- **A. PRODUCTION SPECIFICATION** — the brief, prompts, composition
  instructions, and requirements needed to produce the asset.
- **B. GENERATED FINAL MEDIA** — an actual PNG/JPG/MP4 file that has been
  produced.

**Never pretend a media file exists if it was not actually generated.**

- If PNG/JPG/MP4 generation is available in the current workflow: generate
  the required final media asset and include it in the package.
- If media generation is **not** available: still deliver the
  production-ready prompt, visual brief, composition instructions,
  required dimensions/aspect ratio, source asset list, text overlays,
  timing instructions (video), and transition/motion instructions — and
  mark:

  ```
  MEDIA STATUS: PENDING EXTERNAL GENERATION
  ```

Never invent a filename implying an asset exists when it does not.

## Three Mandatory Content Package Layers

### Layer 1 — Strategy / Review
- Content ID
- Content type
- Calendar reference
- Primary goal
- Content pillar
- Website Design / SEO / Cross-cutting
- Target audience
- Core message
- Hook
- CTA
- Why this content exists
- Hypothesis / experiment (if applicable)
- Source / evidence
- Required owner input

### Layer 2 — Creative / Production
- Final copy
- Caption
- Slide/frame text
- Reel script
- Storyboard
- Shot list
- Story sequence
- Design direction
- Layout direction
- Typography direction
- Image direction
- Video direction
- Motion direction
- Transitions
- Visual hierarchy
- Text-overlay instructions
- Source assets required
- Website screenshots required
- Project URL (when relevant)
- Music/audio direction (when relevant — mood/style only; never invent
  copyrighted music requirements or claim a specific usable audio source
  unless confirmed)

### Layer 3 — Media / Delivery / Control
- Generated PNG/JPG (when available)
- Generated MP4 (when available)
- Cover image (when required)
- Thumbnails/previews (when appropriate)
- Master image prompt
- Master video prompt
- Alternative external-tool prompts
- Regeneration notes
- Quality-editor result
- Owner-review status
- Final approval status
- Publishing status

## Prompt Portability Requirement

The owner needs generation prompts that can be tested in other AI tools.
Every visual/video package must include a reusable **MASTER PROMPT** that
is:

- Tool-neutral where possible
- Detailed enough to reproduce the concept on its own
- Independent from hidden/session-only context
- Explicit about aspect ratio
- Explicit about subject
- Explicit about composition
- Explicit about visual hierarchy
- Explicit about text placement (if text is part of the design)
- Explicit about photographic/illustrative style
- Explicit about camera/movement (for video, when applicable)
- Explicit about what must **NOT** appear

Include **NEGATIVE / AVOID INSTRUCTIONS** when useful. Never write vague
prompts such as "make a professional Instagram post."

## External Tool Prompts

Every media-producing package should include:

- **MASTER PROMPT**
- **ALTERNATIVE IMAGE PROMPT** (when useful)
- **ALTERNATIVE VIDEO PROMPT** (when useful)
- **REGENERATION / REVISION PROMPT** (when useful)

These must let the owner test the concept in another image/video tool
without reconstructing the brief manually. Never claim compatibility with
a specific external tool unless confirmed.

## Visual Identity Rule

Per `brand/visual-identity.md`, the final brand visual identity is
currently **PENDING REDESIGN**. Therefore every package must:

- Never invent permanent brand colors
- Never invent permanent fonts
- Never lock templates to the current, temporary identity
- Never imply temporary colors/fonts are final
- Keep layouts adaptable

If exact approved visual assets are unavailable, state:

```
BRAND VISUAL STATUS: FLEXIBLE — FINAL IDENTITY PENDING
```

When the future approved brand identity is added, this same package
structure must continue working without a system redesign — only the
visual direction content changes, not the delivery architecture.

## Quality Editor Requirement

`quality-editor` must review both **content quality** and **delivery
completeness**. A package cannot be marked QUALITY APPROVED if required
deliverables are missing without being explicitly marked as intentionally
unavailable (e.g. `MEDIA STATUS: PENDING EXTERNAL GENERATION`). See
`.claude/agents/quality-editor.md`.

## Publisher Requirement

`publisher` must never treat MEDIA GENERATED or QUALITY APPROVED as owner
approval. Publishing requires QUALITY APPROVED **+** OWNER APPROVED. If
owner approval is absent: do not publish. See
`.claude/agents/publisher.md`.
