---
name: skill-creator
description: >
  Create new skills, modify and improve existing skills. Use when the user wants to
  create a skill from scratch, edit or optimize an existing skill, capture a workflow
  as a reusable skill, or improve how reliably a skill triggers.

  Trigger when: "make a skill for", "create a skill that", "turn this into a skill",
  "help me write a skill", "update my skill", "my skill isn't triggering",
  "improve this skill".
---

/**
 * @propolis
 * {
 *   "role": "SKILL",
 *   "agent_instructions": "Meta-skill: use this to design, write, and iterate on any new skill. Read before creating any skill from scratch."
 * }
 */

# Skill Creator

A skill for designing, writing, and iteratively improving agent skills — reusable instruction sets that tell an agent exactly how to handle a specific type of task.

---

## What a Skill Is

A skill is a folder containing a `SKILL.md` file — structured instructions an agent reads before tackling a specific category of task. The agent reads it, follows the process, and produces better, more consistent output than freeforming.

Skills are useful when:
- A task has a repeatable structure that benefits from a defined process
- Outputs need to be consistent across different prompts or agents
- A workflow has been refined through iteration and the learning should be captured
- An agent keeps making the same mistakes on a task type

Skills are **not** useful for one-off tasks, tasks that vary too much to generalize, or tasks so simple the agent handles them well without guidance.

---

## Step 1 — Capture Intent

Start by understanding what the user wants the skill to do. If the current conversation already contains a workflow being captured (the user says "turn this into a skill"), extract answers from the conversation history first.

Otherwise, answer these four questions before writing anything:

1. **What should this skill enable an agent to do?** The core task or transformation.
2. **When should it trigger?** What user phrases, contexts, or task types should activate it?
3. **What does a good output look like?** Format, length, structure, what must be present.
4. **What are the edge cases?** Inputs that are ambiguous, unusual, or likely to trip up a naive approach.

Don't ask all four as a list. Read the context — if the user's prompt already answers some, skip those and only ask what's genuinely missing.

---

## Step 2 — Write the SKILL.md

### The description field is the most important thing you'll write

The description is what the agent reads to decide *whether to use this skill at all*. A skill with a weak description never triggers.

**Good descriptions:**
- Include both what the skill does AND the specific contexts that should activate it
- List concrete trigger phrases: "triggers on: X, Y, Z"
- Are slightly pushy — err toward over-inclusion rather than under-inclusion
- Avoid vague language like "helps with" or "can be used for"

**Bad description:**
> "Helps create Word documents."

**Good description:**
> "Produces polished .docx files from structured content. Use whenever the user asks for a Word document, report, memo, letter, or any deliverable they'll send to someone else. Triggers on: 'write a report', 'make a Word doc', 'draft a letter', 'create a template'."

### Writing the body

**Use imperative form.** Instructions read as direct commands: "Read the file before writing anything." Not "The agent should read the file before writing anything."

**Explain the why, not just the what.** Agents follow instructions better when they understand the reasoning. Instead of "ALWAYS include a summary section", write "Include a summary section at the top — readers often skim and need the conclusion before the detail."

**Avoid excessive MUST/NEVER/ALWAYS in caps.** If you need heavy-handed emphasis, the instruction isn't clear enough yet. Reframe it: explain why the thing matters.

**Use examples.** For output formats especially, show don't tell:

```markdown
## Commit message format
Good: `feat(auth): implement JWT token refresh`
Bad: `fixed the auth thing`
```

**Define output formats explicitly.** If the skill produces a file or structured output, specify the exact template.

**Keep it lean.** Remove anything that isn't actively guiding behavior. If a sentence doesn't change what the agent does, cut it.

**Domain organization.** If a skill covers multiple variants, organize by variant in `references/`:

```
skill-name/
├── SKILL.md          ← Workflow + which reference to read
└── references/
    ├── variant-a.md
    └── variant-b.md
```

---

## Step 3 — Write Test Cases

Before declaring the skill done, write 2-4 test cases and save them to `evals/evals.json`.

Test cases should be:
- **Realistic** — the kind of prompt a real user would actually write
- **Specific** — include context, file names, constraints
- **Varied** — cover different phrasings of the same intent
- **Edge-case-weighted** — the easy cases don't tell you much; the hard ones do

For each test case, write 2-4 **expectations** — specific, observable things the output should include. Not "the output is good" but "the output includes a Minimum Feature Set section with at least 5 testable items."

---

## Step 4 — Test the Skill Manually

Run each test case yourself: read the skill's SKILL.md, follow its instructions, and produce the output. Evaluate the result against the expectations.

**What to look for:**
- Did the skill's instructions guide you to the right output, or did you fill in gaps from general knowledge?
- Were any steps ambiguous enough that you had to guess?
- Did the output format match what the expectations required?
- Was anything in the skill instructions ignored because it felt redundant?

Anything you had to reason around is a gap in the skill.

---

## Step 5 — Iterate

Improve the skill based on what the manual test revealed:

**Generalize from failures.** Don't just patch the exact failing case — understand why it failed and fix the underlying instruction.

**Look for repeated improvisation.** If you did the same thing across multiple test cases that the skill didn't tell you to do, that thing belongs in the skill.

**Cut before you add.** Before adding a new instruction, check whether an existing instruction can be clarified instead. Longer skills are not better skills.

**Test again after each meaningful change.**

---

## Step 6 — Optimize the Description (if triggering is unreliable)

If the skill exists but isn't being used when it should be:

1. Write 8-10 prompts that **should** trigger the skill — realistic, casual phrasing
2. Write 8-10 prompts that **should not** trigger — near-misses that share keywords but need something else
3. Read both lists: does the current description predict correctly? Revise where it over- or under-triggers
4. Repeat until the description handles the edge cases

---

## What Not To Do

**Don't write a checklist.** A skill that's a list of 20 rules produces mechanical box-checking. Write process and reasoning instead.

**Don't over-specify.** Leave room for agent judgment. Cookie-cutter results fail on anything unexpected.

**Don't name the skill for implementation.** Name it for what it does for the user.

**Don't make the description too narrow.** Write for the range of ways a person might ask.

**Don't ship the first draft.** A skill that hasn't been tested is a hypothesis.

---

## After Creating a Skill

Add an entry to `cone/agent/skills/README.md` with the skill name, purpose, and trigger phrases.
