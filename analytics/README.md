# Analytics Architecture

This folder holds factual Instagram data. Interpretation and
recommendations live in `reports/`, never here.

## Structure

- **`analytics/baseline/`** — the historical baseline: verified public
  observations of the account's history prior to V1 (see
  `analytics/baseline/arazitco-instagram-public-audit-2026-08-28.md`).
- **Future raw/private Instagram data** — once Instagram Insights / Meta
  Business Suite access is connected, real performance data is recorded
  here following `analytics/instagram-insights-schema.md`. This is the
  factual source data.
- **`reports/`** — weekly and monthly performance reports
  (`reports/weekly-performance-template.md`,
  `reports/monthly-performance-template.md`). This is where facts are
  interpreted and turned into recommendations.

## Core Rule: Raw Data Stays Separate From Analysis

**Facts ≠ Interpretation ≠ Recommendation.**

- **Facts** — what Instagram actually reported (or what was publicly
  observed), recorded per `analytics/instagram-insights-schema.md`. Never
  estimated; missing values are `N/A`, not zero or a guess.
- **Interpretation** — why something may have happened, based on facts.
  Always labeled as interpretation, never presented as fact.
- **Recommendation** — what to do next (KEEP / INCREASE / REDUCE / STOP /
  TEST NEXT WEEK, or a strategic proposal). Always traceable back to the
  facts and interpretation that produced it, and — for anything touching
  the 70/30 default — always requires owner approval before becoming
  permanent.

`analytics/` holds facts. `reports/` holds interpretation and
recommendations built from those facts. Do not blend the two in the same
place.

## Weighting Rule

New verified Instagram Insights and newly published content performance
must progressively receive **more strategic weight** than the historical
public-observation baseline in `analytics/baseline/`. The baseline is a
starting hypothesis set, not a ceiling — it must never constrain future
experimentation or growth, and it never overrides the current 70% Website
Design / 30% SEO strategic default.
