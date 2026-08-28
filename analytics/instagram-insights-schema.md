# Instagram Insights Data Schema (V1)

Structured schema for importing real Instagram performance data once
Instagram Insights / Meta Business Suite access is available. Used by
`instagram-analyst` to record facts before any interpretation happens
(see `analytics/README.md` for the facts/interpretation/recommendation
separation).

## Universal Rules

- Missing data must be recorded as **N/A** — never estimated, never
  converted to zero, never fabricated.
- **0** means Instagram explicitly reported zero. **N/A** means the data
  was unavailable.
- Every record must carry a **DATA SOURCE** and **DATA CONFIDENCE** field
  (defined below) so facts are never mistaken for verified private data.

### DATA SOURCE (per record)
- Instagram Insights
- Meta Business Suite
- Public Observation
- Manual Owner Input
- Other Verified Source

### DATA CONFIDENCE (per record)
- VERIFIED PRIVATE INSIGHTS
- VERIFIED PUBLIC OBSERVATION
- OWNER PROVIDED
- UNKNOWN

---

## Account-Level Schema

| Field | Notes |
|---|---|
| Reporting Period | Start date – end date |
| Followers at Start | N/A if unavailable |
| Followers at End | N/A if unavailable |
| Net Follower Growth | N/A if unavailable |
| Accounts Reached | N/A if unavailable |
| Accounts Engaged | N/A if unavailable |
| Profile Visits | N/A if unavailable |
| Website/Link Clicks | N/A if unavailable |
| WhatsApp/Contact Actions | N/A if unavailable |
| Data Source | See list above |
| Data Confidence | See list above |

## Content-Level Schema

| Field | Notes |
|---|---|
| Date | Publish date |
| Content ID / URL | Unique reference |
| Format | Reel / Carousel / Static Post / Story |
| Topic | Free text |
| Content Pillar | From `strategy/content-pillars.md` |
| Primary Goal | From `strategy/content-strategy.md` Content Goal Framework |
| Category | Website Design / SEO / Cross-cutting |
| Reach | N/A if unavailable |
| Views / Plays | N/A if unavailable |
| Likes | N/A if unavailable |
| Comments | N/A if unavailable |
| Saves | N/A if unavailable |
| Shares | N/A if unavailable |
| Follows Generated | N/A if unavailable |
| Profile Activity | N/A if unavailable |
| Link Clicks | N/A if unavailable |
| Data Source | See list above |
| Data Confidence | See list above |

### Reels — Additional Fields (when available)
| Field | Notes |
|---|---|
| Watch Time | N/A if unavailable |
| Average Watch Time | N/A if unavailable |
| Retention | N/A if unavailable |
| Completion | N/A if unavailable |
| Non-Follower Reach | N/A if unavailable |

### Stories — Dedicated Schema
| Field | Notes |
|---|---|
| Story Sequence / Date | e.g. Story 1, Story 2, or timestamp |
| Views | N/A if unavailable |
| Reach | N/A if unavailable |
| Replies | N/A if unavailable |
| Sticker Interactions | N/A if unavailable |
| Link Clicks | N/A if unavailable |
| Forward | N/A if unavailable |
| Back | N/A if unavailable |
| Exits | N/A if unavailable |
| Completion | Only when derivable from the above; otherwise N/A |
| Data Source | See list above |
| Data Confidence | See list above |

---

## Usage Notes
- This schema defines structure only — it contains no actual data.
- Populate it only from real, verifiable sources; `instagram-analyst` must
  never fill a field by estimation.
- The historical baseline in `analytics/baseline/` predates this schema and
  was recorded under public-observation methodology; it is not required to
  be retrofitted into this exact table structure.
