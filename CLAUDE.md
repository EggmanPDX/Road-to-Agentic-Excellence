# CLAUDE.md — Road to Agentic Excellence
*Master instruction file. Read this first. Every session. No exceptions.*

---

## North Star

> "Become the recognized expert who builds Software 3.0 agent systems for HR, L&D, and enablement — and teaches others how to do the same."

**Three simultaneous outcomes:**
1. Inbound consulting leads — people hiring Gregg to build agent systems for their org
2. Productized tools generating revenue (Sensor, BGC-ODIN, ENKI and beyond)
3. Recognized voice in HR/L&D AI — newsletter, speaking, course revenue

**Primary audience:** HR, L&D, and enablement leaders at mid-to-large orgs. Secondary: fellow builders watching the process.

**The brand signal:** "That's cool. How did he do that?"

---

## Who Is Gregg

- 57, Beaverton OR, 20+ years L&D and performance consulting (Nike, Netflix, lululemon, Uber, Micron)
- Neurodivergent burst worker — plans in bursts, executes in parallel, not linearly
- Enablement Lead at D8TAOPS (AI agent company) + founder of BGC (Build Great Courses)
- Proprietary frameworks: RAPID, 7 Ingredients of Performance Improvement, Show/Do/Apply/Practice, Assessment Before Prescription
- Wants to be seen as an expert builder, not just a consultant who talks about AI

---

## GitHub Setup

- **EggmanPDX** — personal GitHub, our workspace. All builds in this system live here.
- **gregg-eiler_d8taops** — work GitHub, context only. Shows professional proof points (KCU, D8 Support Hub). Do not build here.

---

## Priority Builds (in order)

| # | Repo | What It Is | Karpathy Score | Status |
|---|------|-----------|---------------|--------|
| 1 | Sensor | Teams bot (consent-first) that monitors project health, morale, and communication risk — alerts manager with research-backed coaching tips via dashboard | Passes all 4 criteria | Google AI Studio prototype — needs GitHub repo |
| 2 | BGC-ODIN | 6-agent performance consulting pipeline — "The ID Killer" | Passes all 4 criteria | Partially built |
| 3 | ENKI | AI-powered teaching platform — 5-Gate Pipeline | Passes 3 criteria | Partially built |
| 4 | D8-SALES | Sales intelligence tool for D8TAOPS | Passes 2 criteria | Working, needs packaging |

**D8 work repos (proof points, not builds):**
- D8 Support Hub — live with KCU client, shipping Monday
- D8 Troubleshooter — production, in use
- D8 Sales Intel — production, in use

These are evidence of expertise. AMPLIFIER packages them as case studies. We do not build on them here.

---

## File Structure

```
/Road-to-Agentic-Excellence/
  CLAUDE.md                    ← You are here
  /agents/
    01-architect.md            ← Master agent instructions
    02-scribe.md               ← Secretary / documentation agent
    03-scout.md                ← Research agent (Reddit, X, YouTube)
    04-mapper.md               ← Planning agent
    05-amplifier.md            ← Distribution / LinkedIn / landing page agent
    06-taskmaster.md           ← Task manager agent
  /context/
    gregg-profile.md           ← Full Gregg context for agent orientation
    tech-stack.md              ← Locked stack reference
    priority-builds.md         ← Current build status per repo
    ICP.md                     ← Ideal customer profile
  /docs/
    session-log.md             ← Running log of every session (SCRIBE maintains)
    decisions.md               ← Architectural and strategic decisions
    curriculum-draft.md        ← Building toward a teachable framework
    analysis-and-synthesis.md  ← Session 1 goal analysis and project synthesis
  /SOP/
    research-workflow.md       ← How SCOUT runs research
    build-workflow.md          ← PLAID + terminal-code-mastery combined workflow
    publish-workflow.md        ← How AMPLIFIER packages and distributes work
```

---

## Tech Stack (Locked)

- **AI:** Claude (primary), Claude Code (terminal), Google AI Studio
- **Frontend:** React + Vite + Tailwind CSS
- **Language:** TypeScript
- **Backend/DB:** Supabase
- **Payments:** Stripe
- **Deploy:** Vercel
- **Version Control:** GitHub (EggmanPDX — personal only)
- **IDE:** Antigravity
- **Project Management:** Notion + GitHub Issues
- **Documentation:** GitHub markdown (decisions, curriculum, session log)

**Tool creep rule:** Before adding any new tool, ask "How would we solve this with the existing stack?"

---

## Agent Roster

| Agent | Role | Model | When to Call |
|-------|------|-------|-------------|
| ARCHITECT | Master agent, goal-keeper, router | Opus | Every session start |
| SCRIBE | Documentation, session logs, curriculum | Sonnet | Continuous |
| SCOUT | Research — Reddit, X, YouTube, best practices | Sonnet + web search | Before planning |
| MAPPER | Work planning, repo triage, build sequencing | Opus | After SCOUT returns |
| AMPLIFIER | Distribution — LinkedIn, landing page, no-video strategy | Sonnet | After builds ship |
| TASKMASTER | Task breakdown, Notion sync, agent recommendations | Sonnet | Ongoing |

---

## Session Protocol

**Every session:**
1. ARCHITECT reads this file + `/docs/session-log.md` + active Notion tasks
2. ARCHITECT states the session goal and how it connects to the North Star
3. Work executes in the correct agent context
4. SCRIBE logs the session before closing

**Plan mode rule (from terminal-code-mastery):** Any new feature = Plan Mode FIRST (Shift+Tab twice). No exceptions.

**Verification before closing:**
```
Review this session:
1. What did we complete?
2. What's the open loop?
3. Does this connect to the North Star?
4. What does TASKMASTER need to update?
```

---

## Skills Available

These Claude skills are available at `~/.claude/skills/` and should be invoked by name:

- `plaid` — Run on each priority build before coding starts (generates vision.md, prd.md, roadmap.md, gtm.md)
- `prompt-architect` — Use when writing or refining any agent instruction
- `terminal-code-mastery` — Governs all Claude Code sessions
- `fan-out-fan-in` — Run when SCOUT needs broad research coverage
- `stochastic-consensus` — Run when a strategic decision needs multi-perspective validation
- `egg-voice` — All BGC and personal LinkedIn content
- `handoff-summary` — End of every session
- `document-intelligence` — Before any deliverable ships
- `bento-box-design` — All UI/frontend work
- `debate` — When a plan needs pressure-testing before execution

---

## Karpathy Filter (Run Before Any New Build)

1. Can a single multimodal prompt replace this?
2. Will the next model release make this native?
3. Does this require Software 3.0 to exist?

If a project doesn't pass all three, it's commodity. Flag it to ARCHITECT before investing build cycles.

---

*Last updated: Session 1 — Initial system build*
*Repo: https://github.com/EggmanPDX/Road-to-Agentic-Excellence*
