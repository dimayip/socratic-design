# Socratic Design

<p align="left">
  <a href="./README.md"><b>English</b></a> ·
  <a href="./README.zh-CN.md">简体中文</a>
</p>

<p align="left">
  <a href="https://github.com/bellchen/socratic-design/stargazers"><img src="https://img.shields.io/github/stars/bellchen/socratic-design?style=flat-square" alt="Stars"></a>
  <a href="https://github.com/bellchen/socratic-design/network/members"><img src="https://img.shields.io/github/forks/bellchen/socratic-design?style=flat-square" alt="Forks"></a>
  <a href="https://github.com/bellchen/socratic-design/issues"><img src="https://img.shields.io/github/issues/bellchen/socratic-design?style=flat-square" alt="Issues"></a>
  <a href="./LICENSE"><img src="https://img.shields.io/github/license/bellchen/socratic-design?style=flat-square" alt="License"></a>
</p>

> **From a vague idea to a decision-locked design document — a general-purpose, domain-agnostic, self-contained Socratic facilitation skill.**

`socratic-design` turns "doing design" into an explicit, **repeatable, teachable** methodology. When a user walks in with a vague idea (a new product feature, an internal tool, a platform refactor, an AI capability, a data pipeline, a workflow, a governance mechanism…), this skill does **not** immediately produce a solution. Instead, it first uses Socratic questioning to **lock down the key decisions**, then organizes those decisions into whatever schema the **actual consumer** of the deliverable needs (PRD / RFC / Design Doc / Kickoff / ADR / One-Pager).

---

## Positioning

`socratic-design` is a **general** facilitation framework. It is **not tied to any particular domain, tech stack, or methodology**. Its value comes from three things:

1. **Questioning discipline** — ask before writing, one axis per turn, A/B/C/D candidates, devil's-advocate pass, decision lock-in reviews.
2. **Dependency ordering** — later decisions depend on earlier ones; ask in topological order, never skip.
3. **Deliverable schema library** — full templates for 6 mainstream design-document types, pick by consumer.

It does **not** provide any domain-specific best-practice judgment — that is a different job and explicitly not in scope for this skill. If you want domain-specific hard constraints to drive the design, that belongs elsewhere.

---

## Why this skill exists

Most design failures are not about *"bad writing"* — they are about **starting to write before the decisions are locked in**:

- You are halfway through the doc when you realize the success criteria were never defined → rewrite from scratch.
- A reviewer asks *"why not option B?"* after delivery → because B was never explicitly compared.
- The Kickoff checklist is too coarse for the execution team → the team drifts off-course.
- One PRD tries to serve both leadership and engineering → neither audience is satisfied.
- Critical names (system name, module name, core concept) get decided unilaterally → painful to change later.

`socratic-design` solves this whole class of failure by explicitly **separating decision-locking from writing**, and forcing decisions to progress in dependency-topological order.

---

## When to use it

Use this skill when the user's need has any of these characteristics:

- They want to design a new product / feature / system / workflow, but **key decisions are still unclear** (scope, boundaries, interfaces, roles, success criteria, …).
- They say *"I have an idea"*, *"help me think this through"*, *"help me make sense of this"*, *"help me design X"*.
- They want any of: PRD / RFC / technical proposal / design doc / Kickoff checklist / milestone plan / ADR / One-Pager.
- They need to **lock in and approve a complex multi-stakeholder design section-by-section** before delivery.

**When *not* to use it**: when the user just wants to record **already-settled requirements** in a fixed format (e.g. a pure CRUD spec). Just follow the template directly.

---

## The final deliverable is not just "a PRD"

The output of this skill is **chosen based on the real consumer**, not fixed in advance:

| Scenario | Recommended deliverable | Primary consumer |
|----------|-------------------------|------------------|
| New system from scratch (engineering-heavy) | **Design Doc + Kickoff checklist** | Developers + AI coding agent |
| Product pitch / upward reporting | **PRD + One-Pager** | Product review + leadership |
| Internal tech refactor / cross-team work | **RFC / technical proposal** | Engineering team + architecture review |
| Requirements still exploratory | **ADR + open-question list** | Self + follow-up |
| Existing plan needs execution | **Milestone plan + ownership matrix** | Execution team |

Multiple deliverables can be produced in parallel (e.g. PRD + One-Pager + Kickoff as a bundle, each aimed at a different audience). Templates and a selection decision tree live in [`references/deliverables.md`](./references/deliverables.md).

---

## Core methodology — 4-layer stacked framework

```
Layer 1: Capture Context — methodology anchor (optional) + current state + deliverable consumer
   ↓
Layer 2: Brainstorming discipline (internalized) — 6 hard rules that enforce tempo
   ↓
Layer 3: Socratic questioning — A/B/C/D candidates + dependency topology + consistency checks
   ↓
Layer 4: Deliverable organization — pick schema by consumer, slot in locked decisions
```

Each layer is mandatory, but intensity scales with task complexity.

### Layer 1 · Capture Context

Ask four things up front: **methodology anchor** (if none, say so explicitly — don't invent one), **current-state key numbers**, **deliverable form**, and **deliverable consumer**. Then **restate your understanding** so the user can correct you — 30 seconds that prevents an entire round of misalignment.

### Layer 2 · 6 hard discipline rules (internalized)

1. Do not write the deliverable until the key decisions are locked (lock → write, one-way flow).
2. One axis per turn (avoid cognitive overload).
3. Present the plan section-by-section, approve section-by-section.
4. Run a decision lock-in review every ~3 turns.
5. Play devil's advocate on critical decisions (proactively raise counter-views).
6. Do not auto-decide names (system name, repo name, core concept — always offer candidates).

### Layer 3 · Socratic questioning

Standard question template:

```
❓ On <axis>, here are the candidates:

A. <option A> — <pros/cons>
B. <option B> — <pros/cons>
C. <option C> — <pros/cons>
D. <option D> — <pros/cons>

💡 My recommendation: __ (stated preference + why)

Which one do you pick, or how would you rank them?
```

Ask in **dependency-topological order** — later decisions depend on earlier ones. A warning signal is when the user says *"I haven't figured this out yet, it depends on X"* — that means you asked a question whose **dependency wasn't satisfied**, and you should back up to the prerequisite.

After every locked decision, run 3 consistency checks silently: **against the methodology anchor**, **against prior decisions**, and **against business reality**.

### Layer 4 · Deliverable organization (6 schemas)

Once all decisions are locked, organize them under the user-chosen deliverable type: **PRD / Design Doc / RFC / Kickoff Checklist / ADR / One-Pager**. Full schemas in [`SKILL.md`](./SKILL.md) Layer 4 and [`references/deliverables.md`](./references/deliverables.md).

---

## Standard workflow

```
Step 0  Decide whether this skill applies (30 seconds)
   │
   ▼
Step 1  Capture Context (turn 1: current state + anchor + deliverable form + consumer, with restatement)
   │
   ▼
Step 2  Socratic questioning (N turns, dependency-ordered, lock-in review every ~3 turns)
   │
   ▼
Step 3  Section-by-section presentation (2–5 sections, each ends with "approve or adjust?")
   │
   ▼
Step 4  Organize the deliverable by chosen schema (ship multiple deliverables in parallel + name each consumer)
   │
   ▼
Step 5  Retrospective (optional but strongly recommended) — answer honestly: "what framework did I actually use?"
```

---

## Repository layout

```
socratic-design/
├── SKILL.md                               # Full skill spec — 4-layer framework + 6 discipline rules + workflow + anti-patterns
├── README.md                              # (this file) overview for humans browsing the repo
├── README.zh-CN.md                        # Chinese translation
├── assets/                                # reserved for diagrams and visuals
└── references/
    ├── decision-checklists.md             # per-system-type decision checklists
    └── deliverables.md                    # full templates for 6 deliverable types (PRD / Design Doc / RFC / Kickoff / ADR / One-Pager) + selection decision tree
```

- **[`SKILL.md`](./SKILL.md)** — Canonical spec. The file an AI agent actually loads to operate. Start here if you want to use or port the skill.
- **[`references/decision-checklists.md`](./references/decision-checklists.md)** — Checklists to make sure Socratic questioning **does not miss any critical axis**. Broken down by system type, plus three universal axes: cost, risk, naming.
- **[`references/deliverables.md`](./references/deliverables.md)** — Full templates for the 6 deliverable types + Capture-phase selection decision tree. **This is the ammunition for Layer 4.**

---

## Anti-patterns (do not do these)

| ❌ Anti-pattern | ✅ Correct move |
|----------------|----------------|
| Start writing the plan the moment the user finishes speaking | Capture Context first, then Socratic |
| Ask about 5 axes per turn | One axis per turn |
| Use open-ended questions (*"how would you design this?"*) | Use A/B/C/D candidates + a recommendation + reasoning |
| Accept a decision with no consistency check | Every turn, verify against anchor + prior decisions |
| Hand over the full plan in one shot | Section-by-section, approve each section |
| Use MUST / NEVER hard constraints | Use *"because X, I suggest Y"* reasoning |
| Skip lock-in and start writing | Lock first, write after — strictly one-way |
| Auto-decide a repo / module / concept name | Offer 2–3 candidates, let the user pick |
| Assume the user wants a PRD by default | Ask which deliverable form first |
| Delegate the final write-up to another skill | This skill is self-contained; write directly via Layer 4 |

---

## Self-contained by design

`socratic-design` internalizes Socratic brainstorming discipline + the schema knowledge for 6 mainstream document types, and **does not depend on other skills**. Why:

1. **Keeping the complete methodology in one skill** makes it easier to teach, evolve, and retrospect on.
2. **Eliminates orchestration risk** — if an external dependency fails to trigger, the whole chain breaks.
3. **Allows cross-phase references** — decisions locked in the Capture phase can be used directly in the Layer 4 write-up without losing context.

---

## How to use this skill with an AI agent

On platforms that support skill loading (CodeBuddy, Claude skills, or similar):

1. Place this directory under the platform's skills folder (e.g. `.codebuddy/skills/socratic-design/`).
2. When the user's request matches the skill description (*"help me design X"*, *"help me think this through"*, wanting a PRD / RFC / Design Doc / Kickoff / ADR / One-Pager, …), the agent loads `SKILL.md` automatically.
3. Files under `references/` are loaded **on demand** — the agent pulls them only when the current turn genuinely needs the decision checklist or a deliverable template, keeping `SKILL.md` itself lean.

If you want to use it as a human facilitator: read `SKILL.md` end-to-end once, internalize the 6 discipline rules, and keep both reference files open during the conversation.

---

## Meta principle

> **The point of this skill is not to make an agent better at *writing* — it's to make an agent better at *asking*.**
>
> Because **good questions = good decisions = good deliverables** (whether the output is a PRD, RFC, Design Doc, or something else).
> The user always owns the decisions — the agent just helps the user express them.

---

## ⭐ Star History

[![Star History Chart](https://api.star-history.com/svg?repos=bellchen/socratic-design&type=Date)](https://star-history.com/#bellchen/socratic-design&Date)

---

## License

Unless noted otherwise in individual files, content in this repository is released under the MIT License. See [`LICENSE`](./LICENSE).

---

## Credits

Designed and maintained by [@bellchen](https://github.com/bellchen). Combines Socratic facilitation discipline, dependency-topological ordering, decision consistency checks, and mainstream design-document systems (PRD / RFC / ADR / Design Doc / Kickoff / One-Pager), compressed into a rule set that **actually runs inside a real conversation** and is **domain-agnostic**.
