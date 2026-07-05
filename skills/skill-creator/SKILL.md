---
name: skill-creator
description: Use this skill when the user wants to create, author, or scaffold a new Claude Code skill - e.g. "make a skill for X", "help me write a SKILL.md", "turn this workflow into a skill", or "set up a skills folder". Also use when reviewing or improving an existing skill's structure or trigger description.
---

# Skill Creator

Helps design and write a new skill: a `SKILL.md` file (plus optional supporting files) that teaches Claude a repeatable workflow.

## Workflow

### 1. Clarify the skill's purpose
Ask (or infer from context) if not already clear:
- What task should this skill handle? Get a concrete example request the user would actually type.
- What's the desired output or outcome?
- Is there an existing process/checklist/template the user already follows that should be captured?

Don't start writing until you can state the skill's job in one sentence.

### 2. Pick a name and location
- Name: kebab-case, short, descriptive (e.g. `meeting-notes`, `pdf-fill`, `changelog-writer`).
- Location: `skills/<name>/SKILL.md`. If the skill needs templates, scripts, or reference docs, put them alongside it (e.g. `skills/<name>/references/`, `skills/<name>/scripts/`) and point to them from the SKILL.md rather than inlining everything.

### 3. Write the frontmatter description carefully
This is the single most important part - it's how Claude decides *when* to invoke the skill. Requirements:
- Third person ("Use this skill when...", not "I will...").
- Name concrete trigger phrases/situations the user might actually say.
- If relevant, name what it's *not* for, to avoid false triggers on adjacent skills.
- Keep it one focused paragraph - it's read as a filter, not documentation.

### 4. Write the body
- Lead with a short workflow (numbered steps), not prose explaining the domain.
- Include a concrete template/example output if the skill produces a document or artifact.
- Default to **no comments/fluff** - every line should change what Claude does. Cut anything a competent agent would already know.
- Don't over-engineer: a skill for a narrow, one-shot task doesn't need edge-case handling for scenarios that can't occur.
- If the skill has multiple distinct modes (e.g. "create" vs "review"), give each its own short section.

### 5. Sanity-check before finishing
- Does the description alone let Claude correctly decide to trigger on 2-3 example prompts, and correctly *not* trigger on a similar-but-different prompt?
- Is the body short enough to be skimmed in a few seconds, with details pushed to reference files if long?
- Does it avoid duplicating instructions Claude already follows by default (e.g. general coding style)?

## Template

```markdown
---
name: <kebab-case-name>
description: Use this skill when <concrete trigger situations, in third person>.
---

# <Skill Title>

<One-sentence statement of what this skill produces or does.>

## Workflow

1. <step>
2. <step>

## <Template / Example / Reference section, if the skill produces a structured artifact>
```

## Notes
- Prefer one skill that does one thing well over one skill with many unrelated modes.
- If the user describes a workflow they already run manually and repeatedly, that's a strong signal it should become a skill.
