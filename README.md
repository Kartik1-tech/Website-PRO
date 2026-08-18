# WEBSITE-PRO

> **A multi-agent transformation system that turns any generic, AI-sloppy website into a million-dollar, production-ready experience.**
> One orchestrator. Twelve specialists. Zero slop. Built on context engineering for maximum output quality at minimum token cost.

---

## Why This Exists

### The Problem: AI Builds Generic Websites

Every AI coding agent produces the same website. Not by choice, but by statistics:

| AI Default | Why It Happens |
|---|---|
| Inter or Roboto everywhere | Highest-probability font in training data |
| Purple-to-blue gradient hero | The "premium" cliché every model reaches for |
| Three equal feature cards | The laiest layout that "looks designed" |
| "Elevate your workflow seamlessly" | Highest-probability marketing phrase |
| Em-dashes, fake stats, "John Doe" | Statistical fingerprints of generation |
| Static pages with no motion | Motion requires taste, which requires context |
| Broken mobile, no a11y, no states | None of it fits in one context window |

A single agent trying to fix all of this at once fails, because **one context window cannot hold twelve disciplines of expert design knowledge**. Attention dilutes. Quality collapses to the average of everything stuffed in.

### The Solution: An Agent Team With Engineered Context

WEBSITE-PRO splits the work the way a real design studio does:

- A **managing director (PRISM)** reads your site, sets direction, and dispatches work
- **Twelve specialists** each hold deep expertise in exactly one lane
- A **quality enforcer (AUDIT)** gates every phase behind a 50+ point checklist
- Context is **engineered**: loaded in layers, isolated per agent, compressed between handoffs

The result is not "an AI that writes better CSS." It is a **design department** that fits inside your coding agent.

### What You Get

- **Trending typography** - theme-matched fonts with full weight hierarchy (300-800), never the bottleneck defaults
- **Calibrated color** - one locked accent, tinted shadows, dark mode done right
- **Section-wise variety** - every section a different layout family, no templated repetition
- **Motivated motion** - 18 production transitions, spring physics, GSAP scroll choreography, reduced-motion fallbacks
- **Human copy** - clichés, fake numbers, and generic names hunted down and replaced
- **Production readiness** - WCAG AA, Core Web Vitals targets, SEO meta, mobile collapse, full component states

---

## How It Works: The 5-Phase Workflow

```
STEP 0          STEP 1           STEP 2            STEP 3-6              STEP 7-8
Reverse         DIAGNOSE         ASSEMBLE          EXECUTE (per phase)   ASSESS
Prompting  -->  (CONSCRIPT) -->  (PRISM plans) --> (specialists act) --> (AUDIT gates)
                                                                      │
                                                     pass <────────────┤
                                                     fail ──> sent back with fix list
```

| Phase | Agents | What Happens | Risk |
|---|---|---|---|
| 1. Typography & Color | TYPESET + CHROMA | Font system + palette calibration | Lowest, highest visual lift |
| 2. Layout & Structure | FLUX + GRIDIRON + RESPONSIVE | Page narrative, grids, hero discipline, mobile | Medium |
| 3. Motion & Interactions | KINETIC + SURFACE | Components with 7 states + transition library | Medium |
| 4. Content & Visuals | VERSE + VISUAL | Copy de-slopping + real image sourcing | Low |
| 5. Quality Assurance | AUDIT + GUARDIAN | 50+ point Pre-Flight, CWV, WCAG, SEO | Gate only |

Each phase ends with a review gate. **Nothing advances without passing.** Fixes are atomic (one commit per issue), rollback-ready, and screenshot-verified.

---

## Context Engineering: Why This Beats a Mega-Prompt

This system is not just "more prompts." It is architected around how LLM context actually behaves. Every structural decision exists to **optimize token usage and output quality simultaneously**.

### 1. Progressive Disclosure (Load Only What the Phase Needs)

Context is layered. An agent at layer N never loads layer N+1 until the work demands it:

| Layer | Content | Loaded When | Approx. Cost |
|---|---|---|---|
| L0 | README (this file) | Orientation only | Tiny |
| L1 | WEBSITE-PRO-SKILL.md (orchestrator protocol) | Once, at start | Medium |
| L2 | ONE specialist file (e.g. TYPESET.md) | When that agent is dispatched | Small |
| L3 | ONE reference (FONT-LIBRARY or TRANSITION-LIBRARY) | Only if the agent's lane needs it | Small |
| L4 | Your actual codebase | Sliced per section, per agent | Variable |

A hero-only transformation never pays for FAQ context. A typography pass never loads GSAP skeletons. Compare that to a monolithic skill file where every request pays the full token price of all twelve disciplines.

### 2. Context Isolation (No Attention Dilution)

Each specialist receives **only its lane**:

- TYPESET sees the type audit. Not the animation brief. Not the copy rules.
- KINETIC sees the motion plan. Not the palette. Not the grid specs.
- VERSE sees the copy inventory. Not a single easing curve.

**Why:** attention is finite. A context holding twelve disciplines produces mediocre output in all twelve. A context holding one discipline produces expert output in that one. Twelve narrow experts beat one generalist, every time.

### 3. Compressed Handoffs (The Diagnostic Report as Shared Memory)

CONSCRIPT scans your entire codebase once and distills it into a structured **Diagnostic Report**: tables of `pattern | file | line | severity | fix-agent`. Downstream agents receive the *relevant slice* of that report, never the raw scan.

```
RAW CODEBASE (100% tokens)  ──CONSCRIPT──>  DIAGNOSTIC REPORT (~5% tokens)
                                                  │
                          TYPESET gets the type rows only
                          CHROMA gets the color rows only
                          GRIDIRON gets the layout rows only
```

One expensive scan, twelve cheap consumers. The report is also **externalized memory**: it persists across sessions, so re-runs never rescan what is already diagnosed.

### 4. DOD-Bounded Generation (No Over-Generation)

Every specialist has an explicit **Definition of Done** checklist. Generation stops exactly at done:

- No padding, no "here are some additional thoughts"
- No re-explaining rules already encoded in the file
- AUDIT's pass/fail gate catches under-generation; the DOD prevents over-generation
- Failed checks return a **prioritized fix list** (P0 first), not a full re-brief

Both failure modes of LLM work (too little, too much) are structurally bounded.

### 5. Routing Over Stuffing

PRISM classifies the request and routes it. It holds the *plan*, never the *implementation detail*. Ambiguity is resolved with **max one question**, and only when the design read genuinely diverges. Most dispatches are zero-question because the Diagnostic Report already answered them.

### 6. Stable, Cache-Friendly Structure

All system files are static markdown with stable content. That makes them ideal for **prompt caching**: repeated runs reuse cached context instead of re-processing the skill files, cutting cost and latency on every phase after the first.

### The Numbers View

| Scenario | Naive Mega-Prompt | WEBSITE-PRO |
|---|---|---|
| Context per request | 100% of all rules, always | 1 orchestrator + 1 specialist + 1 reference |
| Full-site transformation | 1 giant context, quality degrades | 12 small contexts, quality holds |
| Re-run after audit fail | Re-stuff everything | Fix list slice only |
| Hero-section-only job | Pays for entire skill set | Pays for 4 files |
| New session, same project | Re-explain everything | Identity files + Diagnostic Report reload |
| Outcome | Generic, 60% checklist pass | Section-aware, 50+ point gate enforced |

---

## The Agent Roster

### Management

**PRISM** - The Managing Director. Orchestrator that plans, dispatches, reviews, and validates. Never writes implementation code. Carries three identity files:

- `PRISM-soul.md` - personality and values (relentlessly premium, anti-slop, evidence over opinion)
- `PRISM-identity.md` - role, lane, authority, boundaries
- `PRISM-user.md` - your project context, populated via Reverse Prompting

### The Specialists

| # | Agent | Lane | Superpower |
|---|---|---|---|
| 01 | **CONSCRIPT** | Read-only analysis | Forensic site scan → the Diagnostic Report everything else consumes |
| 02 | **TYPESET** | Typography | Theme-matched font stacks, 8-role type scale, full weight hierarchy |
| 03 | **CHROMA** | Color & surfaces | One locked accent, tinted shadows, theme lock, 8 rotating palettes |
| 04 | **GRIDIRON** | Layout | CSS Grid discipline, hero rules, bento with zero empty cells |
| 05 | **FLUX** | Page flow | AIDA funnel, section packs (4/6/8/12), narrative spine |
| 06 | **KINETIC** | Motion | 18-transition library, GSAP skeletons, spring physics, motion motivation rule |
| 07 | **SURFACE** | Components | Double-Bezel cards, button-in-button, all 7 interaction states |
| 08 | **VERSE** | Copy | Cliché exterminator, hero copy limits, testimonial discipline |
| 09 | **VISUAL** | Assets | Real images over fake divs, SVG logo walls, art-directed treatments |
| 10 | **RESPONSIVE** | Viewports | Mobile-first collapse, 44px touch targets, iOS Safari fixes |
| 11 | **GUARDIAN** | Perf & a11y | Core Web Vitals, WCAG AA, reduced-motion, SEO, legal |
| 12 | **AUDIT** | Quality gate | The 50+ point Pre-Flight Checklist. Pass or fail. No partial credit |

---

## The Three Dials

Every transformation is calibrated before work begins. Say a vibe word and the dials auto-adjust:

| Dial | Range | Default | Controls |
|---|---|---|---|
| **DESIGN_VARIANCE** | 1 symmetry - 10 chaos | 8 | Layout asymmetry, grid breaking |
| **MOTION_INTENSITY** | 1 static - 10 cinematic | 6 | Animation depth, scroll work |
| **VISUAL_DENSITY** | 1 gallery - 10 cockpit | 4 | Spacing, information per viewport |

| You Say | Dials Become |
|---|---|
| "minimalist, clean, Linear-style" | 5 / 3 / 2 |
| "premium consumer, Apple-y" | 7 / 6 / 3 |
| "Awwwards, wild, experimental" | 10 / 9 / 3 |
| "trust-first, regulated, public sector" | 3 / 2 / 5 |

---

## What Gets Enforced (Highlights)

**Typography** - Inter/Roboto/Arial banned as defaults. Fraunces/Instrument Serif banned. Full weight range (300-800) mandatory. Body capped at 65ch. Tabular numerals for data. Italic descender clearance. Zero em-dashes, anywhere, ever.

**Layout** - Hero: 2-line headline max, 20-word subtext, CTA above fold, max 4 text elements. Logo wall under hero, never inside. Max 1 eyebrow per 3 sections. Zigzag capped at 2. At least 4 layout families per 8 sections. Bento grids: exact cell count, zero voids.

**Motion** - Every animation justifies itself in one sentence. Spring physics default. Only transform + opacity animated. `window.addEventListener('scroll')` banned. Max 1 marquee per page. `prefers-reduced-motion` fallbacks mandatory.

**Copy** - "Elevate/Seamless/Unleash/Next-Gen/Revolutionize" banned. Generic names banned. Fake round numbers banned. One CTA intent per label. Testimonials max 3 lines with full attribution.

**Production** - WCAG AA contrast. LCP < 2.5s, INP < 200ms, CLS < 0.1. Touch targets 44px. Semantic HTML. SEO meta unique per page. Dark mode tested both ways. Grain only on fixed pseudo-elements.

The full ban list (40+ patterns) lives in `WEBSITE-PRO-SKILL.md`, and every item is mechanically verified by AUDIT.

---

## Quick Start

### 1. Install

Drop the `WEBSITE-PRO/` folder into any project (or reference it globally). Works with Claude Code, Codex, Cursor, ZCode, or any agent that can read files.

### 2. Invoke

Point your coding agent at the system:

```
Read WEBSITE-PRO/WEBSITE-PRO-SKILL.md and execute the full
transformation workflow on this website. Start with Step 1.
```

### 3. Answer

PRISM asks Reverse Prompting questions (project type, audience, vibe, brand assets, stack, conversion goal). Your answers populate `PRISM-user.md`.

### 4. Approve

Phases run in order. You review each gate. You control the leash at all times.

### Scope Commands

```
"Full transformation"        -> all 5 phases
"Phase 1 only"               -> typography + color
"Transform the hero only"    -> single-section mode (cheapest)
"Run audit"                  -> read-only Pre-Flight report
"Heartbeat re-audit"         -> maintenance drift check
```

---

## The Trust Protocol

Agents never get the keys on day one. Trust is earned:

| Level | Permission | How It Is Earned |
|---|---|---|
| 0 | Read-only reports | Default |
| 1 | Draft changes, you commit | 3 consecutive clean audits |
| 2 | Direct commits, section scope | Full Pre-Flight pass |
| 3 | Full-page autonomous passes | You grant it explicitly |
| 4 | Heartbeat mode (scheduled re-audits) | Track record across projects |

Every change is one atomic git commit per fix, screenshot-verified before/after, rollback-ready.

---

## System Map

```
WEBSITE-PRO/
├── WEBSITE-PRO-SKILL.md          <- MASTER: orchestrator protocol (start here)
├── AGENT-DATA-FRAMEWORK.md       <- the AGENT framework + DATA loop manual
├── README.md                     <- this file
│
├── agents/
│   ├── PRISM-soul.md             <- orchestrator personality & values
│   ├── PRISM-identity.md         <- orchestrator role, lane, authority
│   ├── PRISM-user.md             <- your project context (template)
│   └── specialists/              <- the 12 specialists, one lane each
│       ├── CONSCRIPT.md   ├── FLUX.md      ├── VERSE.md
│       ├── TYPESET.md     ├── KINETIC.md   ├── VISUAL.md
│       ├── CHROMA.md      ├── SURFACE.md   ├── RESPONSIVE.md
│       ├── GRIDIRON.md    ├── GUARDIAN.md  └── AUDIT.md
│
└── references/                   <- loaded on demand (L3), never by default
    ├── FONT-LIBRARY.md           <- 40+ trending fonts, 8 pairing recipes
    └── TRANSITION-LIBRARY.md     <- 18 production transitions, CSS-ready
```

---

## FAQ

**Does it work with my stack?**
Yes. React, Next.js, Vue, Svelte, vanilla HTML/CSS. The rules target design intent, not framework APIs. REDesign protocol detects your stack and works within it, never migrates it.

**Will it break my existing site?**
No. The redesign protocol preserves URLs, nav labels, analytics events, and brand tokens unless you explicitly approve changes. Phases are ordered by impact-vs-risk, starting with the safest (font + color).

**How is this different from just installing a design skill?**
A single skill stuffs every rule into one context and pays that price on every request. WEBSITE-PRO routes each request to a narrow specialist with exactly the context it needs. Better output, fewer tokens, per phase and per session.

**Can I use individual agents without the full workflow?**
Yes. Each specialist file is standalone. Need only a motion pass? Dispatch KINETIC with the Transition Library. Only a copy cleanup? Dispatch VERSE.

**What if I do not have image generation?**
VISUAL degrades gracefully: image-gen tool first, picsum seeded photography second, generated SVG monograms third, explicitly labeled placeholder slots last. Fake div screenshots are banned either way.

**Is it really "million-dollar"?**
It enforces the same rules that separate Awwwards-tier work from template output: typography with intent, one calibrated palette, varied section architecture, motivated motion, human copy, and a quality gate that refuses to ship slop. That is what expensive looks like.

---

## Inspiration

Systems like taste-skill, emilkowalski/skills, transitions.dev, dialkit, and gstack design-review were used as inspiration for this project. But installing all of them individually into your coding agent means every request pays the token cost of every skill, and managing them separately wastes time too.

WEBSITE-PRO solves this: everything is merged, advanced, and re-engineered into one context-engineered system. Better outcomes, fraction of the token cost, zero skill-management overhead.

## Creator

Built by **Kartik Pawar**.

---

## License

Use it on any project, any stack, any website. Evolve it. The system is the starting point, not the ceiling.
