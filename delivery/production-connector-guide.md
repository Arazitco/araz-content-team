# Production Connector Guide (V1)

Explains how `production-connector` (`.claude/agents/production-connector.md`)
fits into content production — an additive integration layer, not a
replacement for `media-producer`, `quality-editor`, or `publisher`.

## Pipeline

```
Content Package
        ↓
Production Connector
        ↓
External Tool
        ↓
Quality Review
        ↓
Owner Approval
```

- **Content Package** — an already-approved package (past
  `creative-director`): `design-direction.md`, `prompts.md`,
  `source-assets/`, and the format's structure file (`script.md` /
  `sequence.md` / `structure.md`).
- **Production Connector** — reads that package and prepares tool-specific
  production instructions (see Canva Workflow / Video Workflow in
  `.claude/agents/production-connector.md`) — canvas size, layout
  direction, typography, asset placement, and export requirements for
  Canva; scene timeline, duration, transitions, motion instructions, and
  export settings for video tools. It does not generate media itself.
- **External Tool** — the connected production tool (Canva, a video
  production tool, an export system) actually executes the instructions.
  `production-connector` confirms what the tool returned before reporting
  anything as done — an instruction being sent is never treated as a file
  being produced.
- **Quality Review** — `quality-editor` evaluates the resulting output
  (or the still-pending status) exactly as it would any other
  `media-producer` output, per `delivery/output-standard.md`.
- **Owner Approval** — no output from this pipeline is published without
  explicit current owner approval, per `CLAUDE.md` Rule 5 and
  `.claude/agents/publisher.md`.

## Relationship to Existing Agents

`production-connector` does not replace any existing step:
- `creative-director` still owns the creative direction this agent reads.
- `media-producer` still owns actually producing and filing
  `final-assets/`; `production-connector` supplies the tool-ready
  instructions and the confirmed outcome that `media-producer` records.
- `asset-researcher` still owns source-asset acquisition — see
  `.claude/agents/asset-researcher.md`'s Asset Source Priority rule.
- `quality-editor`, owner review, and `publisher` are unchanged and still
  mandatory.

## Rules Carried From `production-connector.md`

1. Never create fake final files.
2. Never claim an external tool completed work unless confirmed.
3. Keep `source-assets/` separate from `final-assets/`, per
   `delivery/asset-delivery-rules.md`.
4. Maintain brand consistency — per `brand/visual-identity.md` (status:
   PENDING REDESIGN), never lock in unapproved colors/fonts/logo as final.
5. Require owner approval before publishing.

## Canva Workflow — Fields Prepared

For Stories, Carousel, Static Posts, Covers:
- Canvas size (aspect ratio per `delivery/asset-delivery-rules.md`)
- Layout direction
- Typography
- Asset placement
- Export requirements (format, resolution, naming per
  `delivery/file-naming-convention.md`)

## Video Workflow — Fields Prepared

For Reels, Motion content:
- Scene timeline
- Duration
- Transitions
- Motion instructions
- Export settings
