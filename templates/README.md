# ArasSystem Template Library (V1)

A lightweight starting-point library so production doesn't begin from
zero every time. Templates are **starting systems, not rigid designs** —
Claude may adapt any template when the content genuinely requires it,
but must preserve its quality rules (never loosen them to save effort).

Never force a template when it damages content quality — an approved
template is a default, not a mandate. Never invent a section just to
satisfy a template's structure.

## How Templates Are Used

```
Content Planner / Creative Director identifies content type
        ↓
Template Library — select closest approved template
        ↓
Adapt only where necessary
        ↓
Prompt Engineer (.claude/agents/prompt-engineer.md)
        ↓
Production Router (.claude/agents/production-connector.md)
```

Every template defines three layers:

1. **Content Structure** — e.g. Hook → Evidence → Explanation → CTA.
2. **Visual Structure** — text hierarchy, screenshot/image placement,
   spacing, margins, overlays.
3. **Production Rules** — dimensions, font, export, screenshot
   preservation, animation rules.

## Structure

```
templates/
├── README.md                              — this file
├── instagram/
│   ├── carousel/
│   │   ├── portfolio-design-breakdown-v1.md
│   │   ├── educational-v1.md
│   │   └── checklist-v1.md
│   ├── story/
│   │   ├── educational-v1.md
│   │   ├── question-box-v1.md
│   │   └── portfolio-v1.md
│   └── reel/
│       ├── website-showcase-v1.md
│       ├── educational-v1.md
│       └── human-team-v1.md
└── production/
    ├── typography-system.md               — current production font standard
    ├── screenshot-treatment.md             — how real screenshots may be cropped/animated
    ├── overlay-spacing-rules.md            — scrim/overlay and margin rules
    └── revision-policy.md                  — how many revisions a piece gets
```

## Relationship to Other Source-of-Truth Files

Templates implement — they never replace — the standards already defined
in:
- `delivery/output-standard.md` — what a complete package must contain
- `delivery/asset-delivery-rules.md` — dimensions, source/final asset handling
- `delivery/file-naming-convention.md` — naming and versioning
- `brand/visual-identity.md` — approved visual principles (final identity
  still PENDING REDESIGN)

If a template ever conflicts with one of those files, the source-of-truth
file wins — update the template, not the other way around.

## V1 Scope

This is a deliberately small V1 foundation, not an exhaustive template
catalog. Add new templates only when a real, repeated production need
justifies one — not speculatively.
