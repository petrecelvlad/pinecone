# Starting a New Project with cone-lite

This guide walks you through using cone-lite as the foundation for a new software project. By the end, you'll have a fully operational documentation framework that grows with your project.

---

## Prerequisites

- A new or empty project directory
- An AI coding agent (Claude, Gemini, Copilot, etc.)
- A general idea of what you're building

---

## Step 1: Copy the Template

Copy the entire `cone-lite/` contents into your project root. Your project should look like:

```
your-project/
├── AGENT.md
├── CLAUDE.md
├── package.json
├── cone/
│   ├── PHILOSOPHY.md
│   ├── agent/              ← agent onboarding, personas, skills, sessions
│   ├── project/            ← architecture, specs, memory, roadmap, archive
│   └── evolution/          ← framework improvement proposals
├── src/                    ← your code (added by you)
└── ...
```

Delete `START_NEW.md`, `APPLY_TO_EXISTING.md`, and `README.md` from the root — those are cone-lite docs, not your project docs. Create your own README if needed.

---

## Step 2: Customize `AGENT.md`

This is the most important step. Open `AGENT.md` and fill in the placeholder sections:

### 2a. Architectural Guardrails
Replace the `<!-- CUSTOMIZE -->` section with your project's hard constraints. Examples:
- "The `core/` package never imports from `api/` or `ui/`"
- "All database access goes through repository adapters"
- "No synchronous I/O in the request path"

If you don't have architectural constraints yet, leave the section with a note: *"To be defined as the architecture emerges."*

### 2b. Tech Stack
List your actual technologies. Be specific about versions when they matter.

### 2c. Naming Conventions
Review the defaults. Adjust if your project uses different conventions (e.g., `snake_case` files for Python projects).

### 2d. Hexagonal Architecture
If your project is small (a script, a CLI tool, a simple API), you may not need hex architecture. Remove or simplify Section 6. For anything with external dependencies (database, APIs, auth), keep it — it pays for itself quickly.

---

## Step 3: Customize `CLAUDE.md` (or your provider's companion)

### 3a. Onboarding Sequence
The default sequence works out of the box. As your project grows, you may add project-specific documents to the sequence (e.g., a graph spine, a domain glossary).

### 3b. Non-Obvious Pointers
Start empty. Add entries as you discover things that would trip up a new agent. After 3-5 sessions, this section becomes one of the most valuable parts of the framework.

### 3c. Other Providers
If you use Gemini or another provider, create a companion file following the template at the bottom of `CLAUDE.md`.

---

## Step 4: Write Your Architecture Overview

Open `cone/project/architecture/OVERVIEW.md` and fill in the template. This doesn't need to be comprehensive on day one — write what you know:

- What the system does (one paragraph)
- The major components and how they relate
- Key constraints that shape the design

As the project grows, add per-system documents in `cone/project/architecture/systems/`.

---

## Step 5: Review Starter Personas

cone-lite ships with two personas:

- **Communicator** (`cone/agent/personas/COMMUNICATOR.md`) — Always-active. Governs information density and response calibration. Review it; adjust the calibration section if you prefer a different communication style.

- **Developer** (`cone/agent/personas/DEVELOPER.md`) — On-demand, activated during coding sessions. Review the mental model; it's intentionally universal but you may want to add project-specific heuristics.

To create additional personas (Architect, Reviewer, etc.), use `cone/agent/personas/PERSONA_CREATOR.md`.

---

## Step 6: Start Your First Session

Read `cone/agent/onboarding/SESSIONS.md` for the full session protocol. Then create your first session:

1. Create the folder path: `cone/agent/sessions/MM_Month/Week_N/YYYY-MM-DD/`
2. Copy `cone/agent/sessions/SESSION_TEMPLATE.md` into that folder
3. Rename it: `01_INITIAL_SETUP.md`
4. Fill in the metadata and initial tasks

This is session #1 — every future session increments the global counter. The sessions folder becomes both your live work tracker and your project's permanent history.

---

## Step 7: Begin Working

The framework is live. From here:

- **Every session** creates a session file in `cone/agent/sessions/`
- **Every mistake** worth remembering goes in `cone/project/memory/ANTI_PATTERNS.md`
- **Every confirmed practice** goes in `cone/project/memory/LESSONS.md`
- **Every recurring workflow** becomes a skill in `cone/agent/skills/`
- **Every new source file** gets a `@propolis` block (see `cone/agent/onboarding/PROPOLIS.md`)
- **Every framework improvement idea** becomes a proposal via `cone/agent/skills/evolution/SKILL.md`

The framework grows with you. Don't try to fill everything in advance — add documents as the project creates the need for them.

---

## What to Add as You Grow

| When... | Add... |
|---|---|
| Project has 20+ source files | `graph:sync` script implementation |
| You notice repeated debugging patterns | Entries in `cone/project/memory/PLAYBOOK.md` |
| A major design decision is made | An ADR in `cone/project/archive/decisions/` |
| You onboard a second contributor | Review and flesh out the onboarding sequence |
| A complex workflow stabilizes | A new skill in `cone/agent/skills/` |
| A new role pattern emerges | A new persona in `cone/agent/personas/` |
| The framework feels incomplete | Run the evolution skill to generate proposals |
