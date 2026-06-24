# cone-lite

A universal documentation framework for AI-assisted software development. A project-agnostic template that any team or solo developer can fork, customize, and grow.

cone-lite turns documentation from passive reference into active behavioral programming. Instead of READMEs that agents skim and forget, it provides a structured system where every document has one job, agents onboard through a dependency-ordered sequence, and institutional knowledge accumulates across conversations.

---

## The Core Innovations

1. **`AGENT.md` Constitution** — A root-level instruction set agents adopt as identity, not rules they follow. First-person voice. Phased operation (Orient, Plan, Implement, Review, Recover).

2. **Two-Pillar Architecture** — Clean separation between agent docs (`cone/agent/` — onboarding, personas, skills, sessions) and project docs (`cone/project/` — architecture, specs, memory, roadmap). They evolve independently.

3. **Phased Onboarding** — Agents don't "read everything." They follow a dependency-ordered sequence where each document gives them a specific capability. SRP applied to documentation.

4. **Personas (How I Think) vs Skills (How I Do)** — Mental models for reasoning (personas) compose with procedural workflows (skills). The persona shapes thinking; the skill guides execution.

5. **Propolis Metadata** — Every source file begins with a `@propolis` block declaring its role, constraints, and agent instructions. Makes the codebase self-describing.

6. **Session Archive** — Sessions serve dual purpose: live tracking during work AND permanent history after. Organized chronologically with global numbering, handoff protocols, and searchable semantic titles.

7. **Self-Evolution** — The framework includes an evolution skill that generates improvement proposals, ensuring the documentation system itself grows and improves over time.

---

## Structure

```
cone-lite/
├── AGENT.md                       — The Constitution (provider-agnostic)
├── CLAUDE.md                      — Claude companion file
├── package.json                   — Script stubs for tooling
├── START_NEW.md                   — Guide: new project foundation
├── APPLY_TO_EXISTING.md           — Guide: retrofit onto existing project
│
└── cone/                          — The knowledge system
    ├── PHILOSOPHY.md              — Framework philosophy & evolution principles
    │
    ├── agent/                     — THE AGENT PILLAR
    │   ├── onboarding/            — How to get started
    │   ├── personas/              — Mental models (how to think)
    │   ├── skills/                — Procedural workflows (how to do)
    │   └── sessions/              — Session archive (live tracking + history)
    │
    ├── project/                   — THE PROJECT PILLAR
    │   ├── architecture/          — System design, guardrails, per-system docs
    │   ├── specs/                 — Technical specifications & feature proposals
    │   ├── operations/            — Setup, deployment, environment config
    │   ├── memory/                — Institutional knowledge (curated)
    │   ├── roadmap/               — Active work queue
    │   └── archive/               — ADRs, reports, historical docs
    │
    └── evolution/                 — Framework improvement proposals
```

---

## Getting Started

**Starting a new project?** Read [START_NEW.md](START_NEW.md).

**Adding to an existing project?** Read [APPLY_TO_EXISTING.md](APPLY_TO_EXISTING.md).

---

## License

MIT

---
