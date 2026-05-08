# Goal Analysis & Project Synthesis
*Document 1 of 7 — Session 1, Initial Build*

---

## 1. Analysis of the Goal

### What You Said
> "I want to become an expert at building agents, agentic workflows, and webapps. I want people to say 'That's cool. How did he do that?' I want my work to be helpful, useful, and practical. I want to learn how to build agentic systems by building one myself. I want to come out the other side with a brand, story, and path toward becoming an expert in this field."

### What This Actually Is

This is three overlapping goals running simultaneously, and the tension between them is productive:

**Goal A — Craft mastery:** Learn to build agent systems at an expert level
**Goal B — Public signal:** Make that learning visible in a way that builds audience
**Goal C — Commercial outcome:** Turn expertise and audience into revenue and inbound work

Most people pursue these sequentially (learn → build → share → monetize). You're pursuing them in parallel — which is the right call at your stage, but it requires a system that can hold all three threads at once. That's what this agent system is.

### What You Already Have (The Real Starting Point)

The work done in the Claude Code session established something important: **you are not starting from zero.** You are starting from 80%.

Evidence:
- 21 GitHub repos — multiple shippable builds in various states of completion
- ODIN: a 6-agent performance consulting pipeline that passes all four Karpathy criteria (Software 3.0, not a wrapper)
- ENKI: a 5-gate teaching platform concept with a running repo
- D8-SALES: a sales intelligence tool built and deployed for real users (Duncan and Jared)
- D8:SUPPORT: a production AI app that ran on real infrastructure for a real client (KCU)
- A complete skills library (30+ reusable Claude skills)
- A working BRAIN system (decisions.md, schema.md, domain.md, state.md) wired into CLAUDE.md
- Notion as operational hub with active task databases
- GitHub (EggmanPDX) as version control
- A fully formed methodology (RAPID, 7 Ingredients, ABP, SDAP)

**The gap isn't capability. The gap is visibility and completion.**

The 20% problem: most builds are functionally complete but unshipped. The marketing campaign can't start until the repos are public and the READMEs tell the story.

### The Karpathy Filter Applied to the Goal

**ODIN** — passes all four criteria. This is the anchor. Lead with it.
**ENKI** — passes three. Build it to completion and ship.
**D8-SALES** — passes two. Valuable for the portfolio but not the flagship.
**The agent system you're building right now** — passes all four. Learning by building an agentic system IS the Software 3.0 project. The meta-level is the product.

### The Insight the Research Found (and the Gap to Own)

From the synthesis done in Claude Code:

- Only 1% of companies call their AI rollout "mature"
- 63% cite human factors as the primary failure cause
- 77% of L&D leaders say AI ownership within their organizations is unclear
- FDE (Forward Deployed Engineering) job postings grew 800%+ in 2025 — almost entirely in technical roles
- The equivalent role for HR/L&D/people-function teams is **unclaimed territory**

The category Gregg can own: **"Embedded AI Accelerator for HR, L&D & Enablement Teams"**

Nobody holds this term on LinkedIn. Nobody has built the Software 3.0 infrastructure to back it up — except Gregg.

---

## 2. Work Already Done (Prior to This System)

### Claude Code Session (The Foundation)
- 3-agent fan-out research completed: skill inventory, HR/L&D market research, LinkedIn positioning
- Karpathy filter applied to all active projects
- Positioning established: "the person who built the agent system AND deploys it embedded in orgs"
- Kill/keep decisions made: D8:SUPPORT → sunset or rebuild agent-first; ID Coach → kill or rebuild from scratch; ODIN → build harder; KCU pipeline → proof of concept

### GitHub Repos (21 Total)
Public (5): `d8taops_website`, `d8-sales-intel`, `D8_Troubleshooter`, `KCU-D8_SUPPORT_WEBAPP`, `DBTA_LinkedIn_Generator`

Private (16) — notable builds:
- `ODIN` — The ID Killer (6-agent performance consulting pipeline)
- `enki-project` — 5-Gate Pipeline teaching platform
- `D8-Brand-Architect_v1` — Media creator
- `D8-LINKEDIN` — LinkedIn content management
- `D8_SUPPORT_v2` — Support chatbot v2
- `Bookwork` — Turn books into lessons
- `Life_Path_Generator` — College navigation
- `second-brain-OS` — Claude's second brain (Python)
- `id-coach-webapp` — ID Coach v1
- `D8-CASE_GENERATOR` — LinkedIn post creator
- `claude-config` — Claude Code config (updated live during this work)

### Google AI Studio Builds
Additional builds in various states of completion — not yet in GitHub. These need to be imported as repos and triaged by MAPPER.

### Skills Library
30+ Claude skills at `~/.claude/skills/` covering: writing, agent design, research, build workflows, design systems, task management, and more.

---

## 3. What This System Is Designed to Produce

**In 30 days:**
- ODIN shipped publicly with a GitHub README that tells the story
- ENKI shipped or in final sprint
- Portfolio landing page live with 2-3 projects showcased
- 8-12 LinkedIn posts published (build posts, lesson posts, reframe posts)
- Session log documenting every build decision (the curriculum foundation)

**In 90 days:**
- All priority builds shipped and on the landing page
- Newsletter launched ("AI at Work: The Practitioner's Guide for HR & L&D Teams")
- Inbound LinkedIn conversations starting from the content
- Curriculum draft at 50%+ completion

**In 12 months:**
- Inbound consulting leads arriving from LinkedIn and the newsletter
- At least one productized tool with paying users
- Recognized voice in the HR/L&D AI practitioner space
- Curriculum publishable as a BGC course or guide

---

## 4. How to Use This System in Claude Code

### Setup Steps
```bash
# 1. Clone or create the repo
git init eggman-build-system
cd eggman-build-system

# 2. The files are already created:
# CLAUDE.md — master instructions
# /agents/ — all 6 agent files
# /docs/ — session log, decisions, curriculum (create these)
# /context/ — Gregg profile, tech stack, ICP, priority builds

# 3. Create the empty docs
touch docs/session-log.md
touch docs/decisions.md  
touch docs/curriculum-draft.md
touch context/priority-builds.md
touch context/ICP.md

# 4. Push to GitHub (EggmanPDX)
git add .
git commit -m "Session 1: Build system initialized"
git push origin main
```

### Starting a Session in Claude Code
```
"Read CLAUDE.md. Then read /docs/session-log.md. 
ARCHITECT, start the session. Today's focus is [ODIN last 20% / ENKI build / AMPLIFIER packages ODIN for LinkedIn]."
```

### Running an Agent
```
"SCOUT, run Mission 2: HR/L&D audience intelligence. 
Use fan-out-fan-in skill. Return a brief to MAPPER."
```

```
"MAPPER, triage the repos against the scoring criteria in your instructions. 
Start with ODIN, ENKI, and D8-SALES."
```

```
"TASKMASTER, produce today's session plan. 
Pull active tasks from Notion. State the session goal and hard stop."
```

### PLAID Integration (Before Every New Build)
```
"Run PLAID on [project name]. 
We have [existing context]. Generate vision.md, prd.md, roadmap.md, gtm.md."
```

---

## 5. The North Star (Keep This Visible)

> **"Become the recognized expert who builds Software 3.0 agent systems for HR, L&D, and enablement — and teaches others how to do the same."**

Every session, every task, every piece of content either moves toward this or it doesn't. If it doesn't, it goes in the backlog or gets cut.

The test before any new work: **Does this connect to the North Star?**

If yes → ARCHITECT approves, TASKMASTER tracks it, SCRIBE logs it.
If no → Parking lot. Not now.

---

*This document is Document 1 of the build system. SCRIBE maintains it. ARCHITECT references it at every session start.*
