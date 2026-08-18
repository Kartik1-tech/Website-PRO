# THE AGENT + DATA FRAMEWORK (Fully Updated)

> The complete operating system for building, deploying, and trusting AI agent workflows.
> Merged with the PRISM multi-agent architecture. This is the manual for WEBSITE-PRO.

---

## 1. The Master System Prompt (The Setup)

To make your work transferable, use this "Reverse Prompting" block. It forces the LLM to understand the user's specific context before acting.

**The Prompt:**

> "I want to transform this website into a production-ready, million-dollar experience using the WEBSITE-PRO multi-agent system. Your goal is to first populate the three identity files: a Soul file, an Identity file, and a User file. Before you write them, ask me any questions you need to fill these in accurately for my specific website. Once I answer, write all three files in plain English, then begin the DIAGNOSE phase."

**Why this works:** The agent cannot fall back to generic defaults because it must first extract your specific context. The identity files become the DNA that every downstream decision inherits from.

---

## 2. The Identity Files (The "G" in AGENT)

These files act as the "DNA" of the agent. By keeping them as separate files, you can swap them out or update them without breaking the agent's logic.

* **Soul File** (`PRISM-soul.md`): Defines personality and values.
  (e.g., "Direct, no corporate fluff, calm, never pushy. Relentlessly premium. Anti-slop by default.")
* **Identity File** (`PRISM-identity.md`): Defines the role and the Lane.
  (e.g., "Role: Master Orchestrator. Lane: Planning, dispatching, reviewing. NEVER writes implementation code directly.")
* **User File** (`PRISM-user.md`): Defines you (the user). Includes goals, role, tech stack, brand assets, audience, risk tolerance, and constraints.

**The upgrade over plain identity files:** In WEBSITE-PRO, every specialist agent (TYPESET, CHROMA, KINETIC...) has its OWN mini identity: role, lane, personality, and Definition of Done. Context rot dies because no single context window ever holds the whole system.

---

## 3. Creating the System Prompt (The "E" in AGENT)

Once the identity is set, you must "Equip" the agent with playbooks. Instead of writing them yourself, use the Reverse Engineering method:

1. **Read Patterns:** Tell the LLM:
   > "Scan this entire codebase. Study the existing fonts, colors, spacing, components, animations, and copy patterns. Identify which are generic AI defaults and which carry real brand intent."
2. **Solidify into Prompts:** Once the patterns are found, instruct it:
   > "Create a step-by-step transformation playbook for each sub-process (typography, color, layout, motion, copy, assets) based on what you found."
3. **The Result:** You now have a "Context Window" where the agent has its identity, playbooks (procedures), and tools all neatly organized. In WEBSITE-PRO this is the Diagnostic Report that CONSCRIPT produces, which becomes the brief every specialist agent works from.

---

## 4. Narrowing the Scope (The "N" in AGENT)

To avoid "context rot" (confusion from too much info), use a Manager-Sub-agent structure.

* **The Manager Agent (PRISM):** Never does the work itself. Its only job is to receive a request, set the Three Dials, and route it to the correct specialist.
* **Specialist Sub-agents (12 total):**

| Agent | Specialty | Lane |
|---|---|---|
| CONSCRIPT | Site archaeology & diagnosis | Read-only analysis |
| TYPESET | Typography architecture | Fonts & type system only |
| CHROMA | Color & surface engineering | Palette & theme only |
| GRIDIRON | Layout strategy | Grid & spacing only |
| FLUX | Page flow & narrative | Section order & funnel only |
| KINETIC | Motion choreography | Animations only |
| SURFACE | Component engineering | UI components only |
| VERSE | Copywriting | Visible text only |
| VISUAL | Art direction | Images & icons only |
| RESPONSIVE | Device adaptation | Viewports only |
| GUARDIAN | Performance & a11y | Vitals & compliance only |
| AUDIT | Quality enforcement | Read-only pass/fail review |

Each agent receives ONLY its slice of context. A typography agent never sees animation briefs. A copy agent never sees grid specs. This is how you get expert-level output instead of mile-wide, inch-deep mediocrity.

---

## 5. Trust in Stages: The 4-Step Protocol (The "T" in AGENT)

You should never give an agent "the keys to the car" on day one. Follow these four stages:

### Stage 1: Set Guardrails First
Define exactly what the agent is allowed to do. Set these in the Identity File:
- "Drafts only, no commits" (default mode)
- "Section-scoped: hero only this run"
- "Style-preserving: never touch brand colors without approval"

### Stage 2: Approve Everything at First
Do not let the agent act autonomously immediately. Use the "Show me what you would do" phase:
- Every phase ends with a review gate
- Before/after screenshots for every fix
- One atomic git commit per fix (rollback-ready)

### Stage 3: Loosen the Leash
Once the agent consistently hits the "Definition of Done" (DOD):
- Allow direct commits for low-risk changes (font swaps, spacing fixes)
- Expand scope to adjacent sections
- Enable batch processing for repetitive fixes

### Stage 4: Give it a Heartbeat
Set the agent on a recurring schedule:
- Re-audit the site every sprint (drift detection)
- Auto-fix regression against the design system tokens
- Monitor Core Web Vitals and flag degradation

**DOD escalation ladder:**
| Trust Level | Permission | Trigger |
|---|---|---|
| 0 | Read-only reports | Default |
| 1 | Draft changes, human commits | 3 consecutive clean audits |
| 2 | Direct commits, section scope | Full Pre-Flight pass |
| 3 | Full-page autonomous passes | User grants explicitly |
| 4 | Heartbeat mode (scheduled re-audits) | Track record across projects |

---

## 6. The Internal Logic: The DATA Loop

While the AGENT framework is how you build it, the DATA Loop is how the agent thinks while it works:

* **D (Diagnose):** CONSCRIPT scans the whole website. What is broken, generic, or missing? Framework, fonts, colors, slop inventory, performance flags, a11y gaps.
* **A (Assemble):** PRISM builds the transformation plan. Sets the Three Dials (VARIANCE / MOTION / DENSITY). Assigns phases: Typography & Color > Layout > Motion > Content > QA.
* **T (Take Action):** Specialist agents execute their scoped briefs. Each produces complete, reviewable output against a clear DOD.
* **A (Assess):** AUDIT runs the 50+ point Pre-Flight Checklist. Fail = sent back with specific fix instructions. Pass = integrate and advance. Lessons feed the next cycle.

**The loop never ends at "shipped."** Heartbeat mode restarts the loop on schedule.

---

## 7. Installation & Usage (For Any Project)

This system is project-agnostic. It installs on any website codebase:

1. Drop the `WEBSITE-PRO/` folder into your project (or reference it globally).
2. Open your coding agent (Claude Code, Codex, Cursor, ZCode) and point it at `WEBSITE-PRO-SKILL.md`.
3. Answer the Reverse Prompting questions (populates the User File).
4. PRISM runs DIAGNOSE > ASSEMBLE > ACT > ASSESS through all 5 phases.
5. Approve each phase gate. Grant trust as DODs are hit.

**Minimal invocation for your coding agent:**

> "Read WEBSITE-PRO/WEBSITE-PRO-SKILL.md and execute the full transformation workflow on this website. Start with Step 1 (Reverse Prompting) and wait for my answers."

**Scope control:**
- "Transform only the hero section" (single-section mode)
- "Phase 1 only" (typography + color)
- "Run the full 5-phase transformation" (complete mode)
- "Heartbeat: re-audit" (maintenance mode)

By providing these identity files, the narrow specialist prompts, and the 4-step trust protocol, you can hand this system to anyone, and it will act as a professional, safe, and autonomous design department.
