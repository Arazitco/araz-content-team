# Revision Policy (V1)

Goal: stop endless polishing loops while still catching real problems.

## Default Production Target

```
Production V1 → Owner Review → Maximum one normal revision → Final
```

A piece gets **one** normal revision round after the first owner review.
After that revision, the piece is final unless a BLOCKER (below) is
found.

## When a Second Revision Is Justified

Only when one of these is true:
- A factual error.
- An asset error (wrong file, wrong crop losing real information, wrong
  screenshot).
- A brand-rule violation (per `CLAUDE.md`, `brand/visual-identity.md`,
  or this system's honesty rules).
- A genuine technical production problem (wrong dimensions, broken
  export, unreadable text).
- The owner explicitly requests a different creative direction — this
  restarts the piece at Creative Direction, it is not a "revision" of the
  same design.

## BLOCKER vs. POLISH

`quality-editor` (and anyone reviewing a production output) must
distinguish these explicitly:

**BLOCKER** — must be fixed before the piece can be owner-ready:
- Wrong information.
- A fake asset or AI-reconstructed UI standing in for a real one.
- Unreadable text.
- Broken RTL layout.
- Wrong dimensions/aspect ratio.
- A brand-rule violation.

**POLISH** — worth noting, but does not by itself justify another
revision round:
- Minor spacing preference.
- A small aesthetic preference with no functional problem.
- A non-critical crop difference (the same content is legible and
  accurate, just framed slightly differently than an alternative would
  be).

POLISH feedback alone should not create an endless revision cycle. Note
it, but don't loop on it past the one normal revision above.

## Calibration vs. Normal Production

**During system calibration/testing** (building or validating a new
template, agent, or production route — like the Carlin Ladies and
Mahtaj Skinland end-to-end tests), multiple iterations are expected and
allowed — that's how the system learns what actually works.

**Once a template is approved for normal production**, target:
first output → one revision maximum → final. Don't apply calibration-mode
iteration patience to routine content production — that defeats the
point of having an approved template.
