# Applying cone-lite to an Existing Project

This guide walks you through retrofitting cone-lite onto a project that already has code, documentation, and established patterns. The goal is integration, not replacement — cone-lite layers on top of what you have.

---

## Before You Start

Understand what cone-lite adds vs. what you already have:

| cone-lite provides | Your project likely has | Integration approach |
|---|---|---|
| `AGENT.md` constitution | README, CONTRIBUTING, or custom instructions | Merge — `AGENT.md` becomes the primary entry point |
| `CLAUDE.md` companion | Possibly scattered AI instructions | Consolidate into `CLAUDE.md` |
| `cone/` knowledge system | `docs/`, wiki, or inline documentation | `cone/` sits alongside existing docs |
| Propolis metadata | Possibly JSDoc, docstrings, or nothing | Add incrementally to high-traffic files |
| Session protocol | Possibly git log, PR descriptions, or nothing | Start fresh — no need to backfill |

---

## Step 1: Add the Constitution

Copy `AGENT.md` to your project root. If you already have an instruction file (`.cursorrules`, `AGENTS.md`, custom prompt files):

1. Read your existing file. Identify which parts are **behavioral** (how to think, how to approach tasks) vs. **procedural** (specific commands, file paths, tech stack details).
2. The behavioral parts belong in `AGENT.md`. The procedural parts belong in your provider companion (`CLAUDE.md`) or in project-specific sections of `AGENT.md`.
3. Merge — don't replace. Your existing instructions contain hard-won project knowledge. The `AGENT.md` template provides the phase structure and standing rules; your content fills the guardrails, tech stack, and naming sections.

If your project uses multiple AI providers, create companion files for each one.

---

## Step 2: Add the Companion File

Copy `CLAUDE.md` (or your provider's companion) to the project root.

Customize:
- **Onboarding Sequence:** Point to your existing architecture docs if they exist. Don't duplicate — reference.
- **Non-Obvious Pointers:** Immediately useful. List the 3-5 things that trip up every new contributor.
- **Session Protocol:** Start using it from this point forward. No need to create historical session files.

---

## Step 3: Add the `cone/` Folder

Copy the entire `cone/` folder into your project. It sits alongside your existing documentation:

```
your-project/
├── AGENT.md                ← new
├── CLAUDE.md               ← new
├── docs/                   ← your existing docs (keep as-is)
├── cone/                   ← new
│   ├── PHILOSOPHY.md
│   ├── agent/              ← agent onboarding, personas, skills, sessions
│   ├── project/            ← architecture, specs, memory, roadmap, archive
│   └── evolution/          ← framework improvement proposals
├── src/
└── ...
```

### What to fill immediately:

- `cone/project/architecture/OVERVIEW.md` — Write a system overview. If you have existing architecture docs, either move them here or write a summary that links to them.
- `cone/project/memory/ANTI_PATTERNS.md` — You already know your project's pitfalls. Write down the top 3-5.
- `cone/project/memory/LESSONS.md` — You already know what works well. Capture the non-obvious ones.

### What to leave empty for now:

- `cone/agent/sessions/` — Start using with your next session.
- `cone/agent/skills/` — Add skills as recurring workflows stabilize.
- `cone/project/archive/decisions/` — Start recording ADRs for future decisions. Don't backfill unless a past decision is frequently misunderstood.

---

## Step 4: Add Propolis Metadata (Incrementally)

Do NOT try to add `@propolis` blocks to every file at once. Instead:

### Phase 1: High-Traffic Files (First Week)
Add `@propolis` blocks to files that agents touch most often:
- Entry points (main, index, app)
- Core business logic files
- Database/API adapters
- Configuration files

```typescript
/**
 * @propolis
 * {
 *   "role": "ENTRY_POINT",
 *   "constraints": ["Composition root — wires all dependencies"],
 *   "agent_instructions": "This is the application entry point. All dependency injection happens here. Do not add business logic to this file."
 * }
 */
```

### Phase 2: As You Touch Files (Ongoing)
When you modify any file during normal development, add a `@propolis` block if it doesn't have one. Coverage grows naturally with development activity.

### Phase 3: Critical Mass (When Ready)
Once ~60% of source files have `@propolis` blocks, implement the `graph:sync` script to generate a dependency graph. Before that threshold, the graph isn't useful enough to maintain.

---

## Step 5: Integrate with Existing Documentation

### If you have `docs/`
Keep it. `cone/project/` handles project-level documentation (architecture, specs, memory). `cone/agent/` handles agent-level documentation (onboarding, personas, skills). `docs/` handles user-facing or contributor-facing documentation. They serve different audiences.

### If you have a wiki
Link to it from `cone/project/architecture/OVERVIEW.md`. The wiki remains the source of truth for whatever it covers; `cone/` adds the structured layer.

### If you have inline documentation
Propolis metadata complements inline docs. `@propolis` tells agents what a file IS and what constraints apply. Inline docs explain what the code DOES. They're not redundant.

### If you have ADRs
Move them to `cone/project/archive/decisions/` or link to their current location. The ADR template in `cone/project/archive/decisions/TEMPLATE.md` is a starting point — adapt it to match your existing ADR format if you have one.

---

## Step 6: Start Your First Session

Read `cone/agent/onboarding/SESSIONS.md` for the full session protocol. Then create a session documenting the migration itself:

1. Create the folder path: `cone/agent/sessions/MM_Month/Week_N/YYYY-MM-DD/`
2. Copy `cone/agent/sessions/SESSION_TEMPLATE.md` into that folder
3. Rename it: `01_CONE_LITE_MIGRATION.md`
4. Record:
   - What you customized in `AGENT.md`
   - Which files got `@propolis` blocks
   - What existing docs you integrated
   - What you decided to leave for later

This is session #1 — every future session increments the global counter. The sessions folder becomes your project's permanent history alongside its code.

---

## Common Questions

**Should I rename my `docs/` folder to `cone/`?**
No. Keep `docs/` for its current purpose. `cone/` is specifically the structured knowledge system — agent operations and project documentation in their own pillars. They coexist.

**What about `.cursorrules` or other existing instruction files?**
Merge their content into `AGENT.md` (behavioral rules) and `CLAUDE.md` (provider-specific instructions). Once merged, you can remove the original files or keep them as symlinks.

**How do I get my team to adopt this?**
Start by using it yourself for 2-3 sessions. Once `cone/project/memory/` has useful entries and the onboarding sequence works smoothly, demonstrate the before/after to your team. Adoption is easier when the framework already has value.

**Is `cone/` git-tracked?**
Yes, entirely. Session files, memory entries, and all framework docs are part of the repository. This is intentional — the framework is as much a part of the project as the source code.
