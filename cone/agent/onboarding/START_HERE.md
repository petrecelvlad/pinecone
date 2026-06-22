/**
 * @propolis
 * {
 *   "role": "BOOTLOADER",
 *   "constraints": ["Must be read before any other cone/ document"],
 *   "agent_instructions": "This is the framework entry point. Follow the phased onboarding sequence exactly. Each phase gives you a specific capability — do not skip ahead."
 * }
 */

# Start Here: Onboarding Sequence

This document defines the order in which you read the framework. The sequence is dependency-ordered — each document builds on the previous one. Skipping ahead means operating without context that later documents assume you have.

---

## The Two Pillars

This framework is organized into two pillars:

- **`cone/agent/`** — Everything the agent needs to operate: onboarding, personas, skills, sessions. This is YOUR operating system.
- **`cone/project/`** — Everything about what was built: architecture, specs, memory, roadmap, archive. This is the PROJECT's documentation.

The separation matters. Agent docs change when workflows improve. Project docs change when the system changes. They evolve independently.

---

## Why Order Matters

This framework applies the Single Responsibility Principle to documentation. Each document has one job:

- `AGENT.md` gives you your operational rules and constraints
- `PHILOSOPHY.md` gives you the framework's purpose and principles
- Your companion file (`CLAUDE.md`, etc.) gives you your provider-specific protocols
- `CODING_COMPANION.md` gives you your coding discipline
- `OVERVIEW.md` gives you the system's architecture
- Personas give you your mode of thinking

Reading them out of order means reading a document that references concepts you haven't encountered yet. Reading them in order means each document clicks into place.

---

## Phase 1: Rules (How I Operate)

**Goal:** Understand the project's constraints, my behavioral standards, and my operational protocols.

| Step | Document | What I gain |
|---|---|---|
| 1 | `AGENT.md` | My constitution: phases, guardrails, standing rules |
| 2 | `cone/PHILOSOPHY.md` | Framework purpose, principles, and evolution model |
| 3 | `CLAUDE.md` (or provider companion) | My onboarding sequence, session protocol, memory rules |
| 4 | `cone/agent/onboarding/CODING_COMPANION.md` | My coding discipline: naming, functions, errors, types |

After Phase 1, I can operate safely on any task. I know the rules, the constraints, and how to write code that meets the project's standards.

---

## Phase 2: Territory (What Was Built)

**Goal:** Understand the system's architecture, components, and key relationships.

| Step | Document | What I gain |
|---|---|---|
| 5 | `cone/project/architecture/OVERVIEW.md` | System design, key decisions, component structure |
| 6 | `cone/project/architecture/systems/*.md` | Deep-dive into specific subsystems (read as needed) |
| 7 | `GRAPH_SPINE.md` (when available) | Dependency graph, god nodes, blast radius awareness |

After Phase 2, I understand what was built and why. I can assess blast radius before making changes and navigate the codebase with context.

---

## Phase 3: Identity (How I Think)

**Goal:** Adopt the mental models that shape my reasoning for this session.

| Step | Document | What I gain |
|---|---|---|
| 8 | `cone/agent/personas/COMMUNICATOR.md` | Information density, response calibration (always-active) |
| 9 | `cone/agent/personas/DEVELOPER.md` | Coding mental model (activate if coding this session) |
| 10 | Other personas as needed | Task-specific mental models |

After Phase 3, I'm fully onboarded. I have rules, territory, and identity. I can begin work.

---

## On-Demand Reading

These documents are consulted during work, not during onboarding:

| When I need to... | I read... |
|---|---|
| Create or manage a session file | `cone/agent/onboarding/SESSIONS.md` |
| Add file metadata | `cone/agent/onboarding/PROPOLIS.md` |
| Understand hex architecture | `cone/project/architecture/HEXAGONAL.md` |
| Check architectural constraints | `cone/project/architecture/GUARDRAILS.md` |
| Document a subsystem | `cone/project/architecture/systems/TEMPLATE.md` |
| Write a technical spec | `cone/project/specs/` |
| Propose a project feature/change | `cone/project/specs/proposals/TEMPLATE.md` |
| Set up local dev environment | `cone/project/operations/SETUP.md` |
| Understand deployment | `cone/project/operations/DEPLOYMENT.md` |
| Check env vars or platform quirks | `cone/project/operations/ENVIRONMENT.md` |
| Check known failure modes | `cone/project/memory/PLAYBOOK.md` |
| Check anti-patterns | `cone/project/memory/ANTI_PATTERNS.md` |
| Check confirmed practices | `cone/project/memory/LESSONS.md` |
| Make an architectural decision | `cone/project/archive/decisions/TEMPLATE.md` |
| Create a new persona | `cone/agent/personas/PERSONA_CREATOR.md` |
| Create a new skill | `cone/agent/skills/skill-creator/SKILL.md` |
| Propose framework improvements | `cone/agent/skills/evolution/SKILL.md` |

---

## Continuing a Previous Session

Before creating a new session file, check `cone/agent/sessions/` for any file with `IN-PROGRESS` or `HANDOFF` status.
- `IN-PROGRESS` → continue from it. Do not create a new file.
- `HANDOFF` → read the handoff section to understand remaining work, then create a new session file.

See `cone/agent/onboarding/SESSIONS.md` for the full session protocol.
