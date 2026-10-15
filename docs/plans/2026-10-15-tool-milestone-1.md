# Instagram Strategy Tool — Milestone 1 Implementation Plan (Separation, Spikes, Skeleton)

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Create the separate tool repository with sanitized prompts, measure Apify data quality/cost and Persian image rendering, and deploy a working Cloudflare skeleton (login, per-project isolated storage, project list).

**Architecture:** Pure-TypeScript core services behind ports (`Storage`, later `BlobStore`/`JobQueue`/`DataProvider`/`LLM`/`Renderer`); a thin Hono layer on a Cloudflare Worker; per-project isolated SQLite via Durable Objects behind the `Storage` port (an in-memory adapter is used for core tests).

**Tech Stack:** TypeScript, Hono, Vitest, Wrangler (Cloudflare Workers, Durable Objects SQLite), pnpm. Apify API for the data spike.

**Spec:** `docs/specs/2026-10-15-instagram-strategy-tool-design.md` (in `Arazitco/araz-content-team`; copied into the new repo in Task 1).

## Global Constraints

- UI and content language is Persian, right-to-left (`<html lang="fa" dir="rtl">`).
- No tool, route, or port may publish to Instagram. Nothing publishes without owner approval.
- Services receive only a `projectId`; no code path may read two projects' data together.
- Secrets (Apify, Anthropic, session) live only in Worker secrets / env; never in the browser, repo, or chat.
- ArasSystem is an ordinary workspace; no ArasSystem-specific data or names in code or `prompts/`.
- Prompts are versioned files in `prompts/`, never inline strings.
- Heavy work is async via jobs (applies from Milestone 2; do not design sync heavy calls).
- Cloudflare product limits and APIs are verified against current official docs when used, not from memory.
- Owner has no coding background: every task ends with a result the owner can see or a plain-language report.

## Review Focus

- Persian project name with mixed Latin/emoji/digits: stored and returned byte-identical, displayed RTL. (Task 4, Task 5)
- Two projects with identical names: distinct ids, no data bleed. (Task 4)
- Wrong/expired/missing session on any `/projects` route: 401, no data. (Task 5)
- Double-submitted `POST /projects`: no duplicate on same idempotency key. (Task 5)
- Missing `APIFY_TOKEN`, or target account private/nonexistent: report says so plainly, exit non-zero, no crash dump. (Task 2)
- Persian text with mixed RTL/LTR and digits renders with joined letters in correct order (owner visual approval). (Task 3)

---

## File Structure (new repository `ig-strategy-tool`)

```
README.md                         # what this is, how to run/deploy (plain language)
SEPARATION.md                     # manifest: what was taken from araz-content-team, what was excluded
docs/specs/…                      # spec copied from araz repo
docs/plans/…                      # this plan copied
prompts/*.md                      # sanitized, versioned prompts (front-matter: source, version)
spikes/apify-probe.ts             # Task 2 script
spikes/render-probe.ts            # Task 3 script
spikes/REPORT.md                  # measured results, written by tasks 2–3
src/core/ports.ts                 # Storage port + types
src/core/projects.ts              # ProjectService
src/adapters/memory-storage.ts    # in-memory Storage for tests
src/adapters/do-storage.ts        # Durable Object SQLite Storage (Task 6)
src/worker/app.ts                 # Hono app (routes, auth)
src/worker/index.ts               # Worker entry + DO class export
src/ui/index.html, app.js         # Persian RTL minimal UI
tests/…                           # Vitest
wrangler.jsonc, package.json, tsconfig.json
```

---

### Task 1: Create the separate repository and perform the separation

**Files:**
- Create (new repo): `README.md`, `SEPARATION.md`, `prompts/*.md`, `docs/specs/2026-10-15-instagram-strategy-tool-design.md`, `docs/plans/2026-10-15-tool-milestone-1.md`, `package.json`, `tsconfig.json`, `vitest.config.ts`
- Test: `tests/separation.test.ts`

**Interfaces:**
- Produces: `prompts/<name>.md` files each starting with YAML front-matter keys `source:` (path in the araz repo) and `version:` (integer). `SEPARATION.md` with sections `## Taken`, `## Excluded`.

- [ ] **Step 1 (owner):** Owner creates an empty GitHub repository named `ig-strategy-tool`; this session attaches it with `add_repo` (access: push) and clones it. If attach is denied, report the exact reason to the owner and stop.
- [ ] **Step 2: Write the failing test** `tests/separation.test.ts`:
  - `it("prompts contain no ArasSystem-specific terms")`: for every file in `prompts/`, assert content matches none of `/ArasSystem|Araz|arazit|Carlin|Mahtaj|Skinland/i`.
  - `it("every prompt has source and version front-matter")`: parse front-matter; assert `source` is a non-empty string and `version` is an integer ≥ 1.
  - `it("SEPARATION.md lists Taken and Excluded")`: assert both headings exist and every file in `prompts/` appears under `## Taken`.
- [ ] **Step 3: Run** `pnpm vitest run tests/separation.test.ts` — Expected: FAIL (no `prompts/` yet).
- [ ] **Step 4: Scaffold** the repo (package.json with vitest/typescript/hono/wrangler dev deps, tsconfig strict, vitest config). Commit.
- [ ] **Step 5: Separate.** Read each candidate in the araz repo and write a generalized copy into `prompts/`: `.claude/agents/{research-intelligence,growth-strategist,content-planner,content-writer,story-producer,quality-editor,prompt-engineer}.md`; the quality/originality/approval/data-driven rules from `CLAUDE.md` sections 3, 4, 5, 6 as `prompts/rules-core.md`; carousel/story/reel structure and typography/overlay rules from `templates/` as `prompts/templates-*.md`; output structure from `delivery/`. Replace brand-, client-, and agency-specific content with neutral placeholders (`{{brand_profile}}`, `{{project_name}}`). Do NOT take `brand/`, `knowledge/`, `strategy/`, `portfolio/`, `competitors/`, `analytics/`, `calendar/`, `articles/`, `content/`, or any client data.
- [ ] **Step 6: Write `SEPARATION.md`** listing every taken file (source → destination, what was generalized) and every excluded directory with a one-line reason.
- [ ] **Step 7: Run** `pnpm vitest run tests/separation.test.ts` — Expected: PASS. Copy the spec and this plan into `docs/`.
- [ ] **Step 8: Commit** `feat: separate tool repo with sanitized prompts` and push. Owner reviews `SEPARATION.md` (plain-language list) and approves before Task 2.

### Task 2: Apify data-quality and cost spike

**Files:**
- Create: `spikes/apify-probe.ts`, `src/core/profile.ts` (normalizer), `spikes/REPORT.md` (section "Apify")
- Test: `tests/profile.test.ts`

**Interfaces:**
- Produces: `normalizeProfile(raw: unknown): ProfileSnapshot` where `ProfileSnapshot = { handle: string; bio: string; followers: number | null; posts: { url: string; caption: string; likes: number | null; comments: number | null; takenAt: string; type: "image" | "carousel" | "video" | "unknown" }[] }`. Unknown/missing numeric fields become `null`, never `0`.

- [ ] **Step 1: Write failing tests** in `tests/profile.test.ts`: (a) a fixture with hidden likes yields `likes: null`; (b) a post with an unknown media type yields `type: "unknown"`; (c) Persian caption and bio are preserved exactly; (d) a malformed/empty input throws an `Error` whose message starts with `"Invalid profile data"`.
- [ ] **Step 2: Run** `pnpm vitest run tests/profile.test.ts` — Expected: FAIL (function missing).
- [ ] **Step 3: Implement** `normalizeProfile` in `src/core/profile.ts`, mapping the field names found in the actual Apify actor output (read the chosen actor's current docs and one real response saved as a redacted fixture).
- [ ] **Step 4: Run tests** — Expected: PASS.
- [ ] **Step 5: Write `spikes/apify-probe.ts`**: takes one target handle and up to two competitor handles from CLI args; reads `APIFY_TOKEN` from env (missing → print "APIFY_TOKEN is not set", exit code 2); private or nonexistent account → print which handle and why, exit code 3; otherwise runs the profile actor, normalizes, and writes measured values to `spikes/REPORT.md`: items returned per account, which fields were null, run duration, and **actual cost from the Apify run usage data** (no estimates).
- [ ] **Step 6 (owner provides token + handles via environment, not chat; run):** `pnpm tsx spikes/apify-probe.ts <target> <comp1> <comp2>` — Expected: REPORT.md filled with real measurements.
- [ ] **Step 7: Write a plain-Persian verdict** at the top of the Apify section (usable / marginal / not usable, with the measured cost per account). Do not propose thresholds not measured. Commit. **Owner decision gate:** go / change data source.

### Task 3: Persian image-render spike

**Files:**
- Create: `spikes/render-probe.ts`, `spikes/fixtures/post.html`, `spikes/REPORT.md` (section "Persian render"), fonts in `assets/fonts/` (owner-approved Persian font; the araz repo's current standard is Vazirmatn Bold/Medium/ExtraBold under its typography rules)
- Test: `tests/render.test.ts`

**Interfaces:**
- Produces: `renderHtmlToPng(html: string, size: { width: number; height: number }): Promise<Uint8Array>` (PNG bytes).

- [ ] **Step 1: Write failing test** in `tests/render.test.ts`: `renderHtmlToPng(fixtureHtml, {width:1080,height:1350})` returns bytes whose PNG header is valid and whose decoded width/height equal the requested size. (Dimensions are the test's input, not a product decision; product sizes come from the araz repo's `delivery/asset-delivery-rules.md` when Milestone 3 reads it.)
- [ ] **Step 2: Run** — Expected: FAIL (function missing).
- [ ] **Step 3: Implement** `renderHtmlToPng` using headless Chromium locally (Playwright, pre-installed at `/opt/pw-browsers`); keep the signature renderer-agnostic so a Cloudflare Browser Rendering adapter can implement it later.
- [ ] **Step 4: Run** — Expected: PASS.
- [ ] **Step 5: Create `fixtures/post.html`** with RTL Persian headline, body mixing Persian, Latin brand name, digits, and emoji, using the bundled font; render to `spikes/out/post.png`.
- [ ] **Step 6: Verify on Cloudflare:** read current Browser Rendering docs; deploy a throwaway Worker that renders the same fixture; record in REPORT.md whether letters join correctly, whether the font loads, and any plan/limit requirements found in the docs.
- [ ] **Step 7: Commit.** **Owner visual gate:** owner views `post.png` (and the Cloudflare output) and approves or rejects the Persian rendering.

### Task 4: Core ports and ProjectService with isolation

**Files:**
- Create: `src/core/ports.ts`, `src/core/projects.ts`, `src/adapters/memory-storage.ts`
- Test: `tests/projects.test.ts`

**Interfaces:**
- Produces:
  - `interface Storage { forProject(projectId: string): ProjectStore; registry(): RegistryStore }`
  - `interface RegistryStore { list(): Promise<Project[]>; put(p: Project): Promise<void>; get(id: string): Promise<Project | null> }`
  - `interface ProjectStore { get(key: string): Promise<unknown | null>; put(key: string, value: unknown): Promise<void> }`
  - `type Project = { id: string; name: string; createdAt: string }`
  - `class ProjectService { constructor(storage: Storage, newId: () => string, now: () => string); create(name: string, idempotencyKey?: string): Promise<Project>; list(): Promise<Project[]> }`

- [ ] **Step 1: Write failing tests** `tests/projects.test.ts`:
  - `create` with name `"کلینیک رز ✨ Rose 24"` returns the same name byte-identical after `list()`.
  - two projects with identical names get different ids.
  - data `put("k", 1)` into project A via `storage.forProject(A.id)` is `null` when read from project B.
  - `create` twice with the same `idempotencyKey` returns the same project and `list()` has length 1.
  - `create("")` and a 201-character name reject with `Error("Invalid project name")`.
- [ ] **Step 2: Run** — Expected: FAIL.
- [ ] **Step 3: Implement** ports, `ProjectService`, and the in-memory adapter (separate `Map` per `projectId`; registry holds only `Project` rows).
- [ ] **Step 4: Run** — Expected: PASS.
- [ ] **Step 5: Commit.**

### Task 5: Worker API, single-user auth, and Persian UI

**Files:**
- Create: `src/worker/app.ts`, `src/worker/index.ts`, `src/ui/index.html`, `src/ui/app.js`, `wrangler.jsonc`
- Test: `tests/app.test.ts`

**Interfaces:**
- Consumes: `ProjectService`, `Storage` (Task 4).
- Produces: `createApp(deps: { projects: ProjectService; auth: { password: string; sessionSecret: string } }): Hono`. Routes: `POST /api/login {password}` → sets `HttpOnly; Secure; SameSite=Strict` cookie; `GET /api/projects` → `Project[]`; `POST /api/projects {name}` with optional header `Idempotency-Key` → `201 Project`; `GET /` serves UI. No route anywhere publishes to Instagram.

- [ ] **Step 1: Write failing tests** with `app.request`:
  - `GET /api/projects` without cookie → 401 and empty body of data.
  - `POST /api/login` wrong password → 401; no cookie set.
  - after correct login, `POST /api/projects {name:"پروژه ۱"}` → 201 and `GET /api/projects` returns it with the same name.
  - same `Idempotency-Key` twice → one project in the list.
  - invalid/expired cookie → 401.
  - `GET /` HTML contains `lang="fa"` and `dir="rtl"`.
- [ ] **Step 2: Run** — Expected: FAIL.
- [ ] **Step 3: Implement** `createApp` with a signed-cookie session (HMAC with `sessionSecret`); password and secret come from Worker secrets, never source.
- [ ] **Step 4: Implement the UI**: one RTL page with a login form, project list, and a "new project" form calling the API; no keys or secrets in the page.
- [ ] **Step 5: Run tests** — Expected: PASS.
- [ ] **Step 6: Commit.**

### Task 6: Durable Object SQLite storage adapter and first deploy

**Files:**
- Create: `src/adapters/do-storage.ts`
- Modify: `src/worker/index.ts`, `wrangler.jsonc`
- Test: `tests/do-storage.test.ts`

**Interfaces:**
- Consumes: `Storage` port (Task 4).
- Produces: `class DoStorage implements Storage` where `forProject(id)` routes to one Durable Object (SQLite-backed, named by `id`) and `registry()` uses one dedicated registry object. Verify the current Durable Objects SQLite storage API and configuration (migrations, bindings) in official Cloudflare docs before writing.

- [ ] **Step 1: Write failing test** `tests/do-storage.test.ts` (run in the Workers test pool if available in current docs; otherwise run against `wrangler dev` locally): the same isolation assertions as Task 4 — project A's key is `null` in project B; registry lists both; data persists across a Worker restart.
- [ ] **Step 2: Run** — Expected: FAIL.
- [ ] **Step 3: Implement** `DoStorage` and wire it in `src/worker/index.ts`; configure the DO binding and migration in `wrangler.jsonc`.
- [ ] **Step 4: Run** — Expected: PASS.
- [ ] **Step 5 (owner):** logs in to Cloudflare via `wrangler login`; set secrets `APP_PASSWORD` and `SESSION_SECRET` with `wrangler secret put` (entered in the owner's terminal, not in chat).
- [ ] **Step 6: Deploy** with `pnpm wrangler deploy`. Verification: owner opens the returned URL, logs in, creates two projects (one Persian name), reloads and still sees both.
- [ ] **Step 7: Commit** and write the plain-language "Milestone 1 done" note in `README.md` (URL, how to log in, what exists, what is next).

---

## Self-Review Notes

- Spec coverage: separation (Task 1), Apify spike (2), Persian render spike (3), per-project isolation and control/data split (4, 6), single-user auth and RTL UI (5), no-publish rule (5 constraint), secrets server-side (5, 6). Brand profile, competitors, strategy, content, preview/calendar, MCP, and image production are Milestones 2+ and get their own plans after the Task 2 and Task 3 gates.
- Types: `Project`, `Storage`, `ProjectStore`, `RegistryStore`, `ProjectService`, `ProfileSnapshot`, `renderHtmlToPng` are used with identical signatures across tasks.
- Gates: Task 1 owner approval of `SEPARATION.md`; Task 2 go/no-go on data; Task 3 owner visual approval; Task 6 owner login test.
