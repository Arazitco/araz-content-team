# ArasSystem File Naming Convention (V1)

Deterministic naming for every content package folder and file, so nothing
is ever ambiguous or accidentally overwritten. Applies to all formats
defined in `delivery/content-package-template.md`.

## The Problem This Solves

Avoid ambiguous names such as:
- `final-final2.png`
- `new-reel.mp4`
- `story-last.png`

These make it impossible to know what's current, what's superseded, or
what a file actually contains.

## Naming Pattern

**Folder:**
```
<date>-<format>-<content-id>-v<version>/
```

**Files inside a folder:**
```
<date>-<format>-<content-id>-<role>-v<version>.<ext>
```

Where:
- `date` — `YYYY-MM-DD`, the intended or actual publish date
- `format` — `reel` / `carousel` / `post` / `story`
- `content-id` — short, kebab-case, descriptive slug (e.g.
  `website-walkthrough`, `redesign`, `portfolio-01`)
- `role` — what the file is (`cover`, `final`, `slide-01`, `slide-02`,
  frame number, etc.) — omit only for the folder itself
- `version` — `v01`, `v02`, etc. — always two digits, always incremented
  on revision, never reused

## Examples

```
2026-09-01-reel-website-walkthrough-v01/
2026-09-01-reel-website-walkthrough-cover-v01.png
2026-09-01-reel-website-walkthrough-final-v01.mp4

2026-09-03-story-portfolio-v01/
2026-09-03-story-portfolio-01-v01.png
2026-09-03-story-portfolio-02-v01.png

2026-09-05-carousel-redesign-v01/
2026-09-05-carousel-redesign-slide-01-v01.png
2026-09-05-carousel-redesign-slide-02-v01.png
```

## Versioning Rule

- Start every new content item at `v01`.
- Any revision (copy change, regenerated media, creative-director rework,
  quality-editor rejection and redo) increments the version — `v02`,
  `v03`, etc. Never overwrite a prior version's files.
- The **delivery manifest** (`delivery-manifest.md`, see
  `delivery/content-package-template.md`) always states the current
  version and what changed from the prior one.
- A version is never reused, even if a later version reverts to an
  earlier approach — reverting still creates a new version number.
- Only the version referenced as current in the delivery manifest is
  eligible for owner approval and publishing; older versions remain in the
  folder for traceability but are not republished.

## Content ID Rules

- Lowercase, kebab-case, no spaces, no special characters.
- Descriptive enough to identify the content without opening the folder
  (e.g. `mobile-ux-showcase`, not `post1`).
- Stable once assigned — do not rename a content ID mid-production; if the
  concept changes materially, treat it as a new content ID and version 01.
- Should align with the Content ID used in Layer 1 (Strategy/Review) of
  the content package, per `delivery/output-standard.md`.
