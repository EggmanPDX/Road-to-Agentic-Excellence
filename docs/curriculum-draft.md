# How I Built a Software 3.0 Agent System
*A practitioner's guide by Gregg Eiler*

*Living document. SCRIBE evolves it across sessions, never more than 2 sessions behind. Builds toward a teachable course or guide for HR / L&D / Enablement leaders learning to build AI agent systems.*

**Audience:** Smart, experienced in their domain, new to building. Not engineers.
**Voice:** Practitioner teaching a peer. Direct, no corporate softening, peer-to-peer, no jargon, real examples.

---

## Module 1 — Why Agents (Not Just Prompts)

*Distilled from Sessions 1+. Build progressively.*

### 1.1 The honest starting point
Most "AI strategy" rolls in with a deck and rolls out with a chatbot. That's not the work.

The actual work is recognizing that you're not starting from zero. You probably already have:
- A methodology that works (yours, hard-won, proprietary in a real sense)
- Documents and decisions scattered across tools
- Things you do that nobody else in your org can do

Software 3.0 is what you get when you encode **the methodology** — not the chat — into a system of specialized agents that hold context, hand off cleanly, and produce artifacts you can ship.

### 1.2 The Karpathy filter (a builder's litmus test)
Before you spend a build cycle on anything, run it against three questions:

1. Could a single multimodal prompt replace this?
2. Will the next model release make this native?
3. Does this require Software 3.0 to exist?

If a project doesn't pass all three, it's commodity. Don't build it. Find the Software 3.0 version of the same goal.

> **Worked example — D8-SALES.** Built it. Used it. Useful. Failed Karpathy 2 of 3. Kept it as a proof point. Did not extend it. That's how you keep your build cycles pointed at the right targets.

### 1.3 The 20% problem
Most builders don't have a building problem. They have a finishing problem. 80% built, 0% shipped.

The cure isn't more discipline. It's a planning agent (we'll meet MAPPER in Module 2) whose only job is to define what "done" means before the next session begins.

---

## Module 2 — The Architecture Before the Code

*Distilled from Sessions 1+. PLAID + prompt-architect applied to agent design.*

### 2.1 PLAID before code (no exceptions)
PLAID generates four documents — vision, prd, roadmap, gtm — before a line of code touches a new project. The point isn't bureaucracy. The point is forcing the four hardest questions to the surface while they're still cheap to answer.

### 2.2 What an agent actually is
An agent is three things plus one rule.

The three:
- **Identity** — who it is, in one sentence
- **Job** — what it produces, in observable terms
- **Knowledge** — what it knows, including the boundaries of what it doesn't

The rule: **it must be invokable in a single line.** "ARCHITECT, start the session." If you can't say that, you don't have an agent. You have a prompt.

### 2.3 The 6-agent skeleton (mapped to L&D-shaped work)
- **ARCHITECT** — keeps the goal visible (the program manager)
- **SCRIBE** — captures what happened (the documenter)
- **SCOUT** — gathers signal (the researcher)
- **MAPPER** — converts research to plan (the instructional designer)
- **AMPLIFIER** — packages the work for the audience (the marketer / curriculum designer)
- **TASKMASTER** — runs the day-to-day (the project manager)

You already do all six of these jobs in your week. Encoding them as agents lets you do them simultaneously instead of serially.

---

## Module 3 — Building in Public Without Burning Out

*Stub — populate after Sessions 4–6 once the AMPLIFIER engine is running.*

Topics to cover:
- Written-first content, no video as a non-negotiable
- The "what shipped this week" cadence and why it sustains
- Mistakes-as-content — why naming the failure builds more authority than hiding it
- The newsletter decision (when, why, what cadence)

---

## Module 4 — The Embedded AI Model for People Teams

*Stub — populate after first inbound consulting conversation lands.*

Topics to cover:
- The FDE analogy translated for HR / L&D
- What an "embedded accelerator" engagement actually looks like
- Pricing logic for embedded vs. project work
- The ownership-handoff rubric (when does the client take over)

---

## Module 5 — Stack Decisions That Don't Age Out

*Stub — populate as stack decisions accumulate.*

Topics to cover:
- Why React + Vite + Tailwind + Supabase + Vercel is the right boring choice
- Claude as primary AI and what the boundaries are with other providers (Gemini, Portkey, etc.)
- Notion as the operational substrate, not the build substrate
- Why GitHub markdown is the right home for a curriculum

---

## Module 6 — The Methodology Behind the Methodology

*Stub — captures Gregg's proprietary frameworks (RAPID, 7 Ingredients, ABP, SDAP) and how they survive the translation into agent-system form.*

This module is the differentiator. Without it, the curriculum is just "I built six agents in a folder." With it, the curriculum is "here's a 20-year methodology being run through a 2026 substrate, and here's how you'd do the same with yours."

---

## Curriculum Notes — Session 1

*Each session contributes one teachable insight here. SCRIBE pulls these into the modules above as they accumulate.*

### Session 1 (2026-05-08)
**Insight:** The architecture work IS the lesson. The temptation in Session 1 is to skip ahead to Sensor and start building. The discipline of writing CLAUDE.md, agent definitions, and a triage doc *first* is exactly the move that separates Software 3.0 from "I prompted Claude a bunch of times."

When this gets taught, the headline is: **"Your first agent isn't the one that does the work. It's the one that decides what work to do."** That's ARCHITECT. And the lesson the audience needs is that the planning substrate isn't overhead — it's the difference between a system and a script.

### Session 2 (2026-05-08)
**Insight:** PLAID before code is not bureaucracy. It's the moment the founder argues with themselves about the questions they've been avoiding.

Sensor's scaffold had been "almost ready to build" for weeks. The actual blockers weren't engineering — they were:
1. A stack mismatch (Gemini in code vs. Claude in policy) that nobody had named
2. An adapter shape (Teams bot vs. webhook receiver) that was unowned
3. A pricing model that was undefined
4. A magic moment that was implicit in the data model but never written down

PLAID surfaced all four in a single session. The building can now happen — and crucially, future build sessions don't need to re-litigate any of these because they're locked in `vision.json`, `prd.md`, and `gtm.md`.

When this gets taught, the headline is: **"PLAID's job isn't to write a spec. It's to surface the four questions you've been avoiding so the build session that follows is actually productive."**

This is also the first time the system produced a *durable artifact* — the four PLAID docs are read by every future Sensor session. That changes the cost equation. One PLAID session amortizes across 6–7 build sessions.

---

*Next curriculum touch: Session 3 (ODIN audit) — likely a lesson about archaeology vs. greenfield (auditing existing code through the same PLAID frame).*
