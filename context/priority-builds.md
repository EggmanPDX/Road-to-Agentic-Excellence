# Priority Builds — Triage & Status

*MAPPER maintains this file. ARCHITECT references it at session start. Updated as builds advance.*

**Last updated:** 2026-05-08 (Session 1 — initial triage)

---

## Scoring Legend

**Closeness to done (1–5):** 1 = concept only · 2 = early scaffold · 3 = core works, 30–40% missing · 4 = functional, polish + deploy missing · 5 = shippable with README

**Marketing value (1–5):** 1 = no audience value · 2 = interesting, not demonstrable · 3 = demonstrable, not shareable · 4 = shareable, needs framing · 5 = immediately compelling to ICP

**Priority score = closeness + marketing value.** Highest ships first.

---

## Triage Summary — Session 1

| Build | Repo | Closeness | Marketing | Priority | Karpathy |
|-------|------|-----------|-----------|----------|----------|
| **ODIN** | `EggmanPDX/BGC-ODIN` | **4** | **5** | **9** ⬆️ | Passes 4/4 |
| Sensor | `EggmanPDX/BGC-Sensor` | 2 | 5 | 7 | Passes 4/4 |
| ENKI | `EggmanPDX/enki-project` | 3 | 3 | 6 | Passes 3/4 |
| D8-SALES | `EggmanPDX/d8-sales-intel` | 4 | 2 | 6 | Passes 2/4 |

**Sequencing call (MAPPER → ARCHITECT, revised post-Session 3 audit):** ODIN now leads. The Session 3 audit revealed ODIN is at closeness 4 (was 3) with marketing value 5 (was 4) — closer to ship and more compelling than initially scored. Agents 1-2 are live-validated; the pipeline runs. Sensor remains the second priority — highest PMF for the ICP, but earlier in the build cycle (closeness 2, no PLAID until Session 2). ENKI third. D8-SALES → AMPLIFIER as proof point.

**Sequencing implication:** Sprint planning may flip — running ODIN to ship first (it's closer) builds the credibility moat before Sensor's launch. AMPLIFIER can lead the public narrative with ODIN as "Software 3.0 for performance consulting" and Sensor lands as the second story. ARCHITECT to confirm with Gregg before Session 5 (Sensor Phase 0).

**Resolved 2026-05-08:** `BGC-ODIN` confirmed canonical. `ODIN` (2026-03-09) and `odin-system` (2026-03-10) are predecessors slated for archive (see Decision 006).

---

## 1. Sensor — `EggmanPDX/BGC-Sensor`

**Position:** Highest-leverage build. Lead the campaign with this.

### Karpathy filter
- Single multimodal prompt replace it? No — requires multi-source signal stream + scheduled inference + a manager dashboard.
- Native in next model release? No — orchestration and consent UX are app-layer concerns.
- Requires Software 3.0? Yes — agentic loop generating interventions from anomalies.
- **Passes all four.**

### Current state (verified via gh, 2026-05-08)
- Repo exists. Last push 2026-05-07.
- Scaffold present: `App.tsx` (7.7KB), `index.tsx`, `components/`, `services/`, `types.ts` (1.8KB), `vite.config.ts`, `package.json`, `CLAUDE.md`, `README.md`.
- Stack: React 19 · TypeScript · Vite · Recharts · `@google/genai`.
- README describes: real-time signal stream, dominant theme + sentiment surfacing, Gemini-generated interventions on anomaly. Three-pane layout (DataVisualizer · TeamPulse · Sensor Feed).
- **Not present:** PLAID artifacts (vision.md, prd.md, roadmap.md, gtm.md), Teams bot integration, consent flow, manager dashboard auth, real signal source (`services/analysisEngine` appears to simulate the stream).

### Done means (good-enough-to-ship bar)
- [ ] PLAID complete (vision, prd, roadmap, gtm)
- [ ] Teams bot adapter wired (replaces simulated stream)
- [ ] Consent-first onboarding flow — bot self-introduces, shows what it captures, opt-out path
- [ ] Manager dashboard with auth (Supabase)
- [ ] One end-to-end demo: real Teams channel → signal → alert → coaching tip
- [ ] Public README with architecture diagram and demo GIF
- [ ] Repo is public (currently PRIVATE — flip after PLAID)
- [ ] Deployed to Vercel

### Blockers (Session 2 will list as tasks)
- No PLAID has been run. Per CLAUDE.md, PLAID is non-negotiable before code. **First Session 2 task.**
- Current `services/analysisEngine` simulates the data stream — real Teams Graph API integration not started.
- Consent UX is undefined.
- No auth yet.

### Estimated sessions
- PLAID + architecture lock: 1 session
- Teams adapter + consent flow: 2–3 sessions
- Auth + dashboard polish: 2 sessions
- Ship + AMPLIFIER content: 1 session
- **Total: 6–7 focused sessions**

### Last 20% task list (raw — TASKMASTER will sequence)
1. Run PLAID on Sensor → generates vision.md, prd.md, roadmap.md, gtm.md in `BGC-Sensor/docs/`
2. Define consent-first UX in vision.md (this is the brand differentiator — get it right)
3. Decide Teams Graph API approach (bot framework vs. webhook receiver)
4. Replace `services/analysisEngine` simulation with Teams adapter
5. Add Supabase auth for manager dashboard
6. Wire Anthropic SDK for intervention generation, replacing `@google/genai` (Decision 007 — confirmed Claude)
7. End-to-end demo with one real channel
8. Public README + 60-second demo GIF
9. Flip repo to public
10. Deploy to Vercel
11. Hand to AMPLIFIER for launch post

**Resolved 2026-05-08 (Decision 007):** Sensor will use Claude (Anthropic). The current `@google/genai` wiring is a prototype artifact and will be replaced during Session 2 implementation. PLAID `vision.md` should specify Anthropic as the locked provider.

---

## 2. ODIN — `EggmanPDX/BGC-ODIN`

**Position:** Highest-credibility build. "The ID Killer." Lead with this for the expert-builder narrative.

### Karpathy filter
- Single multimodal prompt? No — 6 sequential agents, each with distinct role.
- Native in next release? No — proprietary methodology (RAPID, 7 Ingredients, ABP, SDAP) is the differentiator.
- Requires Software 3.0? Yes — orchestrated agent pipeline is the product.
- **Passes all four.**

### Current state (verified Session 3 audit, 2026-05-08)

**The actual product:** A 6-agent (plus Agent 0 orchestrator) sequential pipeline for performance consulting. Identity confirmed as "The ID Killer" per Decision 011. The repo's `README.md` currently contains stale "regression testing suite" wording that needs replacing — the actual project IS the consulting pipeline.

**Active app at `odin-app/`** (Next.js 16 + React 19 + TypeScript):
- Pages: home (`/`), `/chat` (scenario input + chat panel), `/runs/[id]` (run detail viewer)
- 4 API routes: `/api/pipeline/start`, `/api/pipeline/runs`, `/api/pipeline/[runId]/decide`, `/api/pipeline/[runId]/events`
- Pipeline orchestration: `src/lib/agents/pipeline.ts`, `pipeline-manager.ts`, `loader.ts`
- Schema validation (Zod): `output-schemas.ts`, `schema-validator.ts` — H1 through H6 handoff validators
- Mock harness with 8/8 tests passing
- Live pipeline test against Gemini 2.5 Flash/Pro
- 7 substantial agent prompts in `prompts/` (17–56 KB each — these are the proprietary IP)
- SQLite database via `better-sqlite3`: `data/odin.db` (3.2MB, with WAL = active run history)
- `src/lib/db/`: schema, queries, client, tests
- shadcn/ui components: tabs, card, scroll-area, tooltip, badge, table, button, separator, collapsible
- Pipeline UI: `agent-node.tsx`, `pipeline-panel.tsx`, `validation-badge.tsx`
- Chat UI: `chat-panel.tsx`, `chat-message.tsx`, `decision-prompt.tsx`, `scenario-cards.tsx`
- Dashboard UI: `runs-table.tsx`, `agent-output-viewer.tsx`
- Test scenarios in `src/lib/scenarios/scenarios.json` + `regression.e2e.test.ts` (4 scenarios)

**The 6 agents (plus Agent 0):**
- Agent 0 — Orchestrator
- Agent 1 — Sleuth-Gatekeeper (root cause via 7 Ingredients audit)
- Agent 2 — Behavioral Scientist Architect (4-door allocation, WIIFM)
- Agent 3 — Product Engineer
- Agent 4 — Analyst-Governor
- Agent 5 — Cultural Architect
- Agent 6 — Guardian

**Live validation status (per `state.md`, parked 2026-04-09):**
- Agents 1-2: PRODUCTION-READY ✅ — live-validated 4× this session, schema H1+H2 passing on real Gemini outputs
- Agents 3-6: BLOCKED on Gemini API quota (NOT an architecture issue — code path is identical)
- Note: "Claude Opus verified as incompatible with current Zod schemas (`propertyNames` unsupported). Not a viable alternate path without refactor."

**Repo hygiene flags:**
- 23 large `.docx` versioned files at root (~16 MB) — Mar 7 build-era artifacts. Archive to `.archive/` or `gdogsjunk` Drive.
- `.DS_Store` committed at root.
- README is a stub with stale description.
- Predecessors `ODIN` (Mar 9) and `odin-system` (Mar 10) — ✅ archived in Session 1 (Decision 006).

### Done means
- [ ] All 6 agents (plus Agent 0) live-validated end-to-end on a single reference scenario
- [ ] AI provider decision locked (Gemini paid tier OR Claude with schema refactor OR hybrid)
- [ ] Decision flag UI tested live (currently scaffolded, not exercised)
- [ ] Web UI smoke test: home → /chat → start scenario → /runs/[id] all functional
- [ ] Public README explaining "The ID Killer" + methodology + pipeline diagram
- [ ] `.docx` build artifacts archived out of the public repo
- [ ] Repo is public
- [ ] Demo accessible (hosted Vercel deploy OR recorded)
- [ ] AMPLIFIER package complete

### Blockers (Session 3 → Session 4)
- ✅ **AI provider decision RESOLVED (Decision 012, 2026-05-08):** Claude with schema refactor. Action items in decisions.md.
- Web UI not smoke-tested by ARCHITECT yet (parked since 2026-04-09)
- Repo hygiene blocks public flip (.docx files, .DS_Store, stub README)
- 4 scenarios exist; need to pick the one that goes in the public demo (KCU off-limits)

### Estimated sessions (revised after audit)
- Session 4: AI provider decision + retroactive PLAID (vision/prd/roadmap/gtm using existing scaffold)
- Session 5: Schema refactor (if Claude chosen) OR direct full-6-agent live regression (if Gemini paid)
- Session 6: Web UI smoke + decision-flag exercise; pick reference scenario
- Session 7: Repo cleanup + public README + Vercel deploy
- Session 8: Flip public + AMPLIFIER launch package
- **Total: 4–5 focused sessions** (down from 4–6 in Session 1 estimate — closeness was undersold)

### Last 20% task list (revised, Session 3)

**Session 4 (AI provider + PLAID):**
1. Decision 012 — pick AI provider; if Claude, scope the schema refactor
2. Run retroactive PLAID on ODIN — vision.json + product-vision.md + prd.md + product-roadmap.md + gtm.md (input: existing scaffold + this audit)

**Session 5 (provider implementation):**
3. If Claude: refactor Zod schemas to remove `propertyNames`; rewire pipeline.ts model selection; verify mock tests still pass; run live with Anthropic
4. If Gemini paid: upgrade billing tier; re-run live regression on agents 3-6
5. Schema H3-H6 validated live; full 6-agent run documented

**Session 6 (UI + scenario lock):**
6. Smoke-test the Next.js app: `cd odin-app && npm install && npm run dev`; walk through home → /chat → /runs/[id]
7. Trigger decision-flag scenario; exercise async resolver UI
8. Pick the reference scenario for public demo (synthetic or non-KCU real org)

**Session 7 (cleanup + public README):**
9. Move `.docx` files out of repo to `gdogsjunk` Drive's BGC archive (decision: keep `.md` versions, archive `.docx`)
10. Add `.DS_Store` to `.gitignore` if not already; remove the committed one
11. Replace README with public-grade version (positioning + how-it-works diagram + run instructions + license)
12. Vercel deploy — `sensor.buildgreatcourses.com` style subdomain or `odin.buildgreatcourses.com`

**Session 8 (public + AMPLIFIER):**
13. `gh repo edit EggmanPDX/BGC-ODIN --visibility public` (verify no secrets first)
14. Hand to AMPLIFIER: launch post + LinkedIn cadence per `gtm.md`

---

## 3. ENKI — `EggmanPDX/enki-project`

**Position:** BGC revenue play. Build to ship, but second-tier vs. Sensor + ODIN for the brand campaign.

### Karpathy filter
- Single prompt? No — 5-gate pipeline, each gate a distinct agent.
- Native in next release? Possibly — coursebuilder UX is increasingly being absorbed by general assistants. **Watch this.**
- Requires Software 3.0? Yes — gate-based progression with state.
- **Passes 3/4.** Watch the "native in next release" pressure.

### Current state
- Repo exists. Last push 2026-05-07. Description: "AI-powered teaching platform — build web apps through a 5-Gate Pipeline."
- Mature scaffold: `CLAUDE.md`, `.clauderules` (3KB), `README.md`, `src/`, `scripts/`, `supabase/`, `provision.sh`, `next.config.ts`, `tsconfig.json`, `package.json`, `package-lock.json` (122KB → real dependency graph).
- Stack: Next.js 16 (locked) · Clerk · Supabase · Portkey AI · Tailwind · TypeScript.
- Constraint noted in README: "Next.js 16 — do not migrate."

### Done means
- [ ] All 5 gates produce a deployable webapp from one course brief
- [ ] One end-to-end course → webapp run, recorded
- [ ] Public README explains the 5-gate model + who it's for
- [ ] Auth (Clerk) and persistence (Supabase) wired
- [ ] Repo is public
- [ ] Live demo URL on Vercel

### Blockers
- Need full state audit to know which gates are functional vs. stub.
- Portkey vs. Claude direct — tech stack lock says Claude primary; Portkey is a router. Confirm intentional.

### Estimated sessions
- Audit: 1 session
- Gate-by-gate completion: 4–5 sessions
- End-to-end demo + ship: 2 sessions
- **Total: 7–8 focused sessions**

### Last 20% task list (provisional)
1. Audit gate-by-gate state (G1 through G5)
2. Define the reference course (what gets taught in the demo run)
3. Complete missing gates in order
4. End-to-end run + recording
5. Public README + landing tile on portfolio
6. Flip to public
7. Hand to AMPLIFIER

---

## 4. D8-SALES — `EggmanPDX/d8-sales-intel`

**Position:** Proof point only. Do NOT triage as a build target — package as case study.

### Karpathy filter
- Passes 2/4. Commodity-adjacent. Sales-intel tools are increasingly native to assistants and CRMs.
- **Action:** AMPLIFIER packages it. We don't extend it here.

### Current state
- Repo updated 2026-05-07. Split structure: root contains an older Next.js starter, working app lives in `d8-sales-pitch/` subdir.
- Working in production for D8TAOPS (Duncan + Jared per analysis-and-synthesis).
- Heavily documented for its size: `AGENTS.md`, `CLAUDE.md`, `README.md`, `SUMMARY.md`.

### What AMPLIFIER does with it
- One LinkedIn post: "Built a sales intel tool over a weekend. Here's how, and what it taught me about Software 3.0 vs. CRM commodity."
- Portfolio tile.
- Reference in HR/L&D narrative as "I do this in adjacent functions too" credibility marker.

### Cleanup before AMPLIFIER (low-priority background task)
- [ ] Remove root-level Next.js starter cruft OR clarify in README why it's there
- [ ] Confirm repo can be made public without exposing client/customer data
- [ ] One screenshot for the portfolio tile

---

## D8 Work Builds (Proof Points Only — NOT for triage)

These belong to `gregg-eiler_d8taops` context. We do not build on them. AMPLIFIER packages them.

| Build | Status | AMPLIFIER use |
|-------|--------|---------------|
| D8 Support Hub (KCU) | Live in production | Lead case study — $1.2M savings, 97% faster, 99.5% accuracy |
| D8 Troubleshooter | Production | Secondary case study — internal tool, fast iteration story |
| D8 Sales Intel | Production | Tertiary — sales-team productivity narrative |

---

## Parking Lot — Backlog Repos (Not Priority Builds)

Surfaced from EggmanPDX repo list. Do not build here. Audit later or kill.

| Repo | Status | Disposition |
|------|--------|-------------|
| `ODIN` | Predecessor to BGC-ODIN | ✅ Archived 2026-05-08 |
| `odin-system` | Predecessor to BGC-ODIN | ✅ Archived 2026-05-08 |
| `D8-DOCUMENT-ENGINE` | Unknown | Audit Session 5+ |
| `D8-DESIGN-NERVOUS-SYSTEM` | Unknown | Audit Session 5+ |
| `D8-Brand-Architect_v1` | Media creator | Audit Session 5+ |
| `Bookwork` | Books → lessons | Audit — possible BGC reuse |
| `Life_Path_Generator` | College navigation | Likely kill |
| `second-brain-OS` | Python second brain | Audit — possible reuse for SCRIBE infra |
| `id-coach-webapp` | ID Coach v1 | Per analysis-and-synthesis: kill or rebuild from scratch |
| `D8TA_LinkedIn_Generator` | LinkedIn content tool | AMPLIFIER may use; not priority build |
| `D8-CASE_GENERATOR` | LinkedIn post creator | AMPLIFIER may use; not priority build |
| `claude-config` | Claude Code config | Infrastructure, not a build |
| `antigravity-projects` | Old | Likely archive |

---

*Next MAPPER update: end of Session 2, after Sensor PLAID + ODIN canonical decision.*
