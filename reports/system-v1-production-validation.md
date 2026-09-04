# System V1 Production Validation

Documentation-level validation of the V1 System Consolidation
(Prompt Engineer, Template Library, Production Routing, Typography
System, Revision Policy, Owner Operating Guide) against the 8 questions
posed for this pass. This is a review of what the architecture now
supports on paper and, where it exists, real production precedent — it
is **not** a new real client content package.

## 1. Can a portfolio project with screenshots be routed to deterministic local render?

**Yes — and already proven in real production**, not just on paper.
`production-connector.md` Route A and
`templates/instagram/carousel/portfolio-design-breakdown-v1.md` both
route portfolio screenshot content to deterministic local render. This
is exactly how the Mahtaj Skinland carousel's Slides 1–6 (and Slide 7,
after Canva became inaccessible) were actually produced — real
committed screenshots, cropped and composited locally with Vazirmatn
typography, no AI reconstruction.

## 2. Can a creative image request be routed to ChatGPT Image?

**Architecturally yes, not yet exercised.** Route B in
`production-connector.md` and Output Type A in `prompt-engineer.md`
define this path. No live ChatGPT Image generation has actually been
run in this project yet — this route is newly documented, not yet
production-tested.

## 3. Can an editable layout be routed to Canva?

**Yes — proven in real production.** Route C in `production-connector.md`
matches how the Day 2/3/5 Story frames and Mahtaj's original Slide 7
were actually built via the Canva MCP connector. The same production
also surfaced Canva's real limitations (cannot ingest private local
files without publishing them; no font-family control via the exposed
edit operations; account-continuity issues causing designs to become
inaccessible) — these are now captured as explicit routing criteria
(asset accessibility, typography requirement) rather than discovered
fresh each time.

## 4. Can a conceptual video be routed to Video AI?

**Architecturally yes, not yet exercised.** Route D in
`production-connector.md` defines this path (this session has
Higgsfield/motion_so tools available). No conceptual video has actually
been produced through this route in this project yet.

## 5. Does Prompt Engineer know what prompt format to create?

`prompt-engineer.md` (new in this pass) defines 5 output types
(ChatGPT Image / Canva / Video AI / Deterministic Local Render /
Revision) with a required field checklist for each, and instructs it to
select the type via Production Routing. This is a newly created agent —
structurally complete, but not yet exercised end-to-end on a real task.

## 6. Does Template Library get checked before designing from zero?

**Yes, on paper.** `content-planner.md` now notes a likely template at
planning time; `creative-director.md` now explicitly checks
`templates/README.md` before specifying visual direction, and hands off
to `prompt-engineer`. Not yet exercised on a real task since the library
didn't exist before this pass.

## 7. Does revision policy prevent endless polishing?

`templates/production/revision-policy.md` (new) defines the
one-revision default and the BLOCKER/POLISH distinction;
`quality-editor.md` now explicitly classifies findings this way. This
directly addresses a real pattern seen in this project (the Mahtaj
typography pass went through several genuine rounds during system
calibration) — the policy now distinguishes that calibration-mode
iteration from what normal production should target going forward.

## 8. Can the owner operate monthly/weekly/daily workflows using the Persian guide?

`owner/how-to-run-content-system-fa.md` (new) covers all six flows asked
for: monthly strategy review, monthly calendar, weekly production,
individual portfolio content (minimum input), owner approval commands,
and strategy synchronization — entirely in Persian, with concrete
example commands for each.

## Summary

| # | Question | Status |
|---|---|---|
| 1 | Portfolio → Deterministic Local Render | ✅ Proven in real production |
| 2 | Creative image → ChatGPT Image | 🟡 Documented, not yet exercised |
| 3 | Editable layout → Canva | ✅ Proven in real production |
| 4 | Conceptual video → Video AI | 🟡 Documented, not yet exercised |
| 5 | Prompt Engineer format selection | 🟡 New agent, structurally complete, not yet exercised |
| 6 | Template Library checked first | 🟡 Wired into agent docs, not yet exercised (library is new) |
| 7 | Revision policy prevents endless polishing | ✅ Directly addresses an observed real pattern |
| 8 | Owner Persian operating guide | ✅ Complete, covers all 6 requested flows |

## Known Limitations Carried Forward

- Canva account-continuity issues (designs becoming inaccessible
  mid-session) are documented as a routing input, not solved — Route A
  exists specifically because Route C can't be relied on for
  asset-critical work.
- No Persian-capable font beyond Vazirmatn has been tested; the fallback
  rule in `templates/production/typography-system.md` still applies if
  these font files are ever unavailable in a future environment.
- Routes B and D (ChatGPT Image, Video AI) are architecturally ready but
  unvalidated by a real production run — the first real use of either
  should be treated as a small calibration test, not assumed to work
  perfectly on the first try.
