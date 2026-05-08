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

*Next decisions will append below as they emerge in Session 2+.*
