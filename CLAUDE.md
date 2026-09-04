# ArasSystem AI Content Team — Project Rules (V1)

This file defines global rules and workflow behavior for the ArasSystem AI
Content Team project. It governs *how* work is done. Company, brand,
audience, strategy, portfolio, analytics, and calendar *content* lives in
their own dedicated files under `knowledge/`, `brand/`, `strategy/`,
`portfolio/`, `analytics/`, and `calendar/` — not here.

## 1. Project Goal

Build an AI content team for the ArasSystem Instagram account that handles
analysis, strategy, planning, content production, quality control,
approval, publishing, and performance learning.

## 2. Strategic Default

Default content split: **70% Web Design / 30% SEO**.
This is a default, not a hard limit. Only the owner can override it.

## 3. Content Quality

All content must feel human-written, natural, professional, specific,
useful, and high quality. Avoid generic AI-style language, repetitive
phrasing, filler, exaggerated claims, and robotic tone.

## 4. Originality

Do not copy competitor content. Competitors may be used for pattern
analysis, trend detection, gap finding, and inspiration only. Avoid
unnecessary repetition of ArasSystem's own past content.

## 5. Approval Rule

No post, reel, carousel, story, or scheduled publication may be published
without explicit owner approval.

## 6. Data-Driven Workflow

Weekly performance analysis must inform the next week's strategy and
content plan.

## 7. Optional Website Articles

Website articles are an optional content source, not a mandatory source.

## 8. Portfolio Priority

Website portfolio and case-study content is a core content pillar.
Support both work-in-progress and completed-project content.

## 9. Brand Visual Identity

Visual identity is currently pending redesign. Do not treat the current
logo, colors, fonts, or visual style as permanent. Use flexible visual
direction until approved brand assets are available.

## 10. Scope (V1)

In scope: Instagram audit, competitor analysis, trend research, growth
strategy, monthly and weekly calendars, daily story planning, reels,
carousels, static posts, captions, hooks, CTAs, portfolio content,
optional article repurposing, creative direction, quality/originality
review, weekly/monthly analytics, owner approval, and publishing after
approval.

## 11. Out of Scope (V1)

Automatic DM replies, automatic comment replies, CRM, lead scoring, sales
automation, WhatsApp automation, and automatic follow-up.

## 12. Workflow (Final V1)

```
OWNER
↓
Content Manager
↓
Analysis / Strategy
↓
Content Planner
↓
Creative Director
↓
Asset Researcher / Portfolio Producer
↓
Template Selection
↓
Prompt Engineer
↓
Production Router / Production Connector
↓
Production Tool
   ├── Deterministic Local Render
   ├── ChatGPT Image
   ├── Canva
   ├── Video AI
   └── Deterministic Website Motion
↓
Media Producer
↓
Quality Editor
↓
Owner Review
↓
Publisher
↓
Analytics
↓
Next Strategy Optimization
```

Template Selection, Prompt Engineering, and Production Routing are
additive production-layer steps between Creative Direction and Media
Production, consolidated from real end-to-end production tests
(Carlin Ladies, Mahtaj Skinland). They turn already-approved creative
direction into production-ready prompts and route each piece to the
right production tool; they do not change strategy, planning, or
approval rules elsewhere in this file. See:
- `.claude/agents/asset-researcher.md` — asset acquisition priority
- `.claude/agents/prompt-engineer.md` — production prompt engineering
- `.claude/agents/production-connector.md` — Production Routing (Routes A–E)
- `.claude/agents/media-producer.md` — final media production
- `templates/README.md` — the Template Library
- `templates/production/typography-system.md` — current production typography standard (not permanent brand identity)
- `templates/production/revision-policy.md` — how many revisions a piece gets
- `owner/how-to-run-content-system-fa.md` — how the owner operates this system day to day (Persian)

The owner's role in this system is **Creative Director / Final Decision
Maker** — not a daily Canva operator, prompt writer, manual production
coordinator, or screenshot collector (unless automatic acquisition
fails). The system is meant to reduce owner effort over time, per
`owner/how-to-run-content-system-fa.md`.

Publishing still always requires QUALITY APPROVED **+** explicit current
OWNER APPROVED — never automatic, regardless of how much of the pipeline
above is automated (see Rule 5).
