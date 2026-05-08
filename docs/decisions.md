# Decisions Log

*SCRIBE maintains. Append-only. Every architectural or strategic decision lives here so future sessions can audit reasoning.*

**Format (per 02-scribe.md):**

```markdown
---
## Decision [number] — [date]

**Context:** [What situation prompted this decision?]
**Options considered:** [Alternatives]
**Decision:** [What was chosen]
**Reasoning:** [Why — in Gregg's words if possible]
**Karpathy check:** [Does this pass all three tests?]
**Reversible?:** [Yes / No / Partially]
---
```

---

## Decision 001 — 2026-05-08

**Context:** Session 1 kickoff. Need to confirm the workspace location, repo structure, and operating substrate before any priority-build work begins.

**Options considered:**
- Build the system inside an existing D8:* workspace
- Stand up a fresh BGC-scoped workspace at `~/BGC/Agentic_Excellence` with its own GitHub repo

**Decision:** Fresh workspace at `~/BGC/Agentic_Excellence` mirrored to `EggmanPDX/Road-to-Agentic-Excellence` (public).

**Reasoning:** This work is BGC-scoped (personal brand + revenue), not D8TAOPS client-scoped. Mixing it with D8 enablement work would violate the three-zone separation rule in the global CLAUDE.md. The agent system is also itself a Software 3.0 build (passes all four Karpathy criteria) — it deserves its own repo and its own narrative.

**Karpathy check:** Yes (4/4) — the agent system is the meta-build. Single prompt won't replace it. Next model release won't make a multi-agent orchestration with persistent memory native at this depth. Requires Software 3.0.

**Reversible?:** Partially — could fold into a different repo later, but the GitHub repo and folder structure are the durable substrate.

---

## Decision 002 — 2026-05-08

**Context:** Three ODIN repos exist in EggmanPDX (`ODIN`, `BGC-ODIN`, `odin-system`). Triage cannot proceed without a canonical reference.

**Options considered:**
- Pick the most recent push (`BGC-ODIN`, 2026-05-07)
- Audit all three and merge histories
- Defer the call until Gregg confirms

**Decision:** Treat `BGC-ODIN` as canonical for triage purposes. Final confirmation + archival of `ODIN` and `odin-system` is the **first task in Session 3** (the ODIN audit session).

**Reasoning:** Most recent push is the highest signal. Don't let an unanswered ambiguity block the triage of the other three priority builds. Flag it cleanly and resolve in the next ODIN-focused session.

**Karpathy check:** N/A (operational, not architectural).

**Reversible?:** Yes — easy to swap canonical if audit reveals one of the other two is more advanced.

---

## Decision 003 — 2026-05-08

**Context:** `BGC-Sensor` README shows `@google/genai` (Gemini) as the AI provider. Global tech stack in CLAUDE.md locks Claude as primary AI.

**Options considered:**
- Keep Gemini for Sensor (it was the Google AI Studio prototype origin)
- Swap to Claude before going public
- Run both via a router

**Decision:** Defer to PLAID. PLAID is the first Sensor task in Session 2. The vision.md output should explicitly resolve the AI-provider choice with reasoning.

**Reasoning:** A stack decision this load-bearing should be made inside PLAID, not as an off-the-cuff call during triage. PLAID forces the question to be answered with a vision/prd/roadmap context.

**Karpathy check:** Indirectly — wrong provider lock could weaken the "real Software 3.0" claim if the agent loop sits behind a model that ships native team-monitoring.

**Reversible?:** Partially — provider swap mid-build is possible but costly once integrations are wired.

---

## Decision 004 — 2026-05-08

**Context:** D8-SALES (`d8-sales-intel`) scored a priority of 6 in MAPPER triage but only passes 2/4 Karpathy criteria.

**Options considered:**
- Treat as a priority build alongside Sensor/ODIN/ENKI
- Demote to proof-point only and route to AMPLIFIER

**Decision:** Demote. AMPLIFIER packages it as one LinkedIn post and a portfolio tile. No further build investment.

**Reasoning:** Karpathy filter says: if a project doesn't pass all three tests (the kickoff says "all three"; CLAUDE.md says "all four" — both yield the same demotion here), it's commodity. Sales-intel tooling is increasingly native to assistants and CRMs. Build cycles spent extending D8-SALES are cycles not spent on Sensor/ODIN/ENKI.

**Karpathy check:** Failed (2/4) — that's the point.

**Reversible?:** Yes — can be re-promoted if the Karpathy picture changes.

---

## Decision 005 — 2026-05-08

**Context:** Kickoff prompt assumed Sensor has no GitHub repo yet. Repo audit revealed `BGC-Sensor` exists with a working scaffold (App.tsx, services/, components/).

**Options considered:**
- Create a new repo and migrate the prototype
- Build on the existing `BGC-Sensor` scaffold

**Decision:** Build on the existing `BGC-Sensor`. PLAID runs against the current repo state; vision.md will document the prototype origin.

**Reasoning:** The scaffold is already at ~2/5 closeness. Throwing it out and starting fresh is the polish-paralysis failure mode MAPPER is supposed to prevent.

**Karpathy check:** N/A.

**Reversible?:** Yes — branch and rewrite if PLAID surfaces an architecture that demands it.

---

## Decision 006 — 2026-05-08 (post-session)

**Context:** Decision 002 deferred final ODIN canonical confirmation to Session 3. Gregg confirmed at end of Session 1.

**Decision:** `EggmanPDX/BGC-ODIN` is canonical. `EggmanPDX/ODIN` and `EggmanPDX/odin-system` are predecessors and should be archived.

**Reasoning:** Most-recent push held; no ambiguity remains. Archiving the two predecessors prevents future sessions from re-litigating which repo is real, and removes them from active triage scope.

**Karpathy check:** N/A.

**Reversible?:** Yes — GitHub archive is reversible (unarchive at any time). No data loss.

**Action:** ✅ Done 2026-05-08 — `EggmanPDX/ODIN` and `EggmanPDX/odin-system` archived via `gh repo archive`. BGC-ODIN remains active as the sole working repo.

---

## Decision 007 — 2026-05-08 (post-session)

**Context:** Decision 003 deferred Sensor AI provider choice to PLAID vision.md. Gregg called it before Session 2.

**Decision:** Sensor uses Claude (Anthropic) as the runtime AI provider. The current `@google/genai` (Gemini) wiring in `BGC-Sensor` will be swapped during Session 2 implementation.

**Reasoning:** Aligns with the global tech stack lock in CLAUDE.md (Claude is primary AI). Strengthens the Software 3.0 "I built this on Claude" narrative for AMPLIFIER content. Gemini was a Google AI Studio convenience during prototyping — not a load-bearing decision.

**Karpathy check:** Indirectly strengthens — staying on Claude keeps the system independent of Google's eventual native team-monitoring features.

**Reversible?:** Yes — provider swap is one service module rewrite (`services/geminiService` → `services/claudeService` or similar).

**Implication for Session 2:** Update PLAID vision.md to specify Anthropic. Add a Sensor Last-20% task: replace Gemini SDK with Anthropic SDK before any further feature work.

---

## Decision 008 — 2026-05-08 (post-session)

**Context:** `KCU-D8_SUPPORT_WEBAPP` exists on `EggmanPDX` AND on `gregg-eiler_d8taops`. Flagged in Session 1 log as a possible misplacement.

**Decision:** Intentional dual-repo state. The d8taops copy is the work-context truth; the EggmanPDX copy is the personal-archive copy. No action needed — it's not a misplacement.

**Reasoning:** Per Gregg, "KCU-D8 also lives on d8taops git." Confirming intentional. Rule-of-thumb refresher for ARCHITECT going forward: cross-account duplication of D8 work artifacts is allowed; cross-account ownership of build targets is not. KCU is a proof point, not a build target.

**Karpathy check:** N/A.

**Reversible?:** Yes — easy to delete the EggmanPDX copy later if desired.

---

## Decision 009 — 2026-05-08 (Session 3 start)

**Context:** Several skills referenced in CLAUDE.md and PLAID methodology (`prompt-architect`, `terminal-code-mastery`, `fan-out-fan-in`, `validate-vision.js`) are not present at `~/.claude/skills/`. PLAID itself was missing until pasted in Session 2.

**Decision:** Skills are pasted on demand, not pre-verified. Gregg inputs each skill's content when an agent needs it. ARCHITECT does not block sessions on skill availability.

**Reasoning:** Gregg's chosen workflow. Avoids the alternative (pre-flight verification of every skill before each session) which adds overhead and forces a snapshot of skills that change.

**Karpathy check:** N/A.

**Reversible?:** Yes — can flip to a manifest-based skill registry later if churn becomes painful.

**Implication for ARCHITECT:** When a skill is needed, name it explicitly in chat ("Need PLAID methodology") rather than calling Skill tool blindly. Wait for paste before proceeding.

---

## Decision 010 — 2026-05-08 (Session 3 start)

**Context:** Open Loop on Notion BGC Tasks category — schema has `Content & LinkedIn`, `Workshops`, `Frameworks`, `Personal Projects` but no Builds category for Sensor/ODIN/ENKI work.

**Decision:** Use **Personal Projects** as the category for build work. Sensor, ODIN, ENKI sprint tasks all land here. Type field distinguishes umbrella (`Project`) from individual sprint items (`Task`).

**Reasoning:** Per Gregg's call. The DB is already named "BGC Tasks & Projects" — every row is BGC-scoped, so a "BGC" sub-category would be redundant. "Personal Projects" reads cleanly. Future split possible if the category gets crowded.

**Karpathy check:** N/A.

**Reversible?:** Yes — Notion select options can be added/renamed at any time.

---

## Decision 011 — 2026-05-08 (Session 3 start)

**Context:** ODIN identity ambiguity — `~/Developer/CLAUDE.md` calls BGC:ODIN "Pipeline regression testing for 6-agent system"; Road-to-Agentic-Excellence kickoff and Session 1 docs call ODIN "The ID Killer 6-agent performance consulting pipeline."

**Decision:** **ODIN is "The ID Killer" — a 6-agent performance consulting pipeline.** This is the canonical product description. The "regression testing" wording in `~/Developer/CLAUDE.md` is stale/wrong and will be corrected in this session.

**Reasoning:** Per Gregg's call. The kickoff prompt for this whole initiative names ODIN's product identity explicitly. The local Developer/CLAUDE.md description likely lags an earlier-life version of the project.

**Karpathy check:** N/A (clarification, not architecture).

**Reversible?:** Yes — wording is metadata, not implementation.

**Action:** ARCHITECT updates `~/Developer/CLAUDE.md` ODIN row in this session.

---

## Decision 012 — 2026-05-08 (Session 3)

**Context:** ODIN audit confirmed agents 1-2 live-validated against Gemini 2.5 Flash; agents 3-6 parked since 2026-04-09 on free-tier quota. `state.md` notes Claude Opus is incompatible with the current Zod schemas because of `propertyNames` usage — a refactor item, not a wall.

**Options considered:**
- Claude with schema refactor (~30–45 min per state.md note)
- Gemini paid tier (fastest, no refactor, but stack split with Sensor)
- Hybrid Claude + Gemini fallback (most complex, defer)

**Decision:** **Claude with schema refactor.** Refactor Zod schemas to remove `propertyNames` usage, rewire pipeline.ts to use `@ai-sdk/anthropic` (already in `package.json` deps), validate mocks still pass, then full live run on Anthropic.

**Reasoning:** Per Gregg's call. Brand consistency matters more than refactor speed. Sensor uses Claude (Decision 007), and a unified "Software 3.0 on Claude" narrative is cleaner for AMPLIFIER than a stack split that has to be explained in every post. The schema refactor is bounded scope.

**Karpathy check:** Strengthens — staying on Claude keeps the system independent of Google's eventual native offerings and aligns with the tech-stack lock in CLAUDE.md.

**Reversible?:** Yes, but costly — provider swap mid-build is one major refactor cycle. Locked for the foreseeable horizon.

**Action items (Session 5):**
1. Refactor Zod schemas in `odin-app/src/lib/agents/output-schemas.ts` to remove `propertyNames` usage
2. Update `odin-app/src/lib/agents/pipeline.ts` model selection to call `@ai-sdk/anthropic`
3. Verify `mock-pipeline.test.ts` still passes (8/8)
4. Run `live-pipeline.test.ts` end-to-end on Anthropic
5. Confirm H3-H6 schema validation passes live
6. Document any output-shape differences vs. mock data

---

*Next decisions will append below as they emerge in Session 3+.*
