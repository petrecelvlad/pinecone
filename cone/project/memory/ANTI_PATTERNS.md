/**
 * @propolis
 * {
 *   "role": "PROTOCOL",
 *   "constraints": ["Curated knowledge only — not a session log"],
 *   "agent_instructions": "Institutional memory: mistakes with non-obvious root causes. Add entries when a failure's root cause would surprise a future agent. Use the template format below."
 * }
 */

# Anti-Patterns

Mistakes that have been made, with root causes and fixes. Each entry captures a failure that would surprise a future agent or developer — if the root cause is obvious, it doesn't belong here.

**This is curated knowledge, not a session log.** Session logs go in `cone/agent/sessions/`. Anti-patterns are distilled from sessions into timeless entries.

---

## Entry Format

```markdown
### [Pattern Name]
**What happened:** [Brief description of the failure]
**Root cause:** [Why it actually failed — the non-obvious part]
**The fix:** [What to do instead]
```

---

<!-- Add entries below this line -->
