---
name: create-skill
description: Scaffold a new Claude Code skill by generating the SKILL.md file with correct frontmatter and prompt body, then placing it under ~/.claude/skills/<skill-name>/SKILL.md
disable-model-invocation: true
argument-hint: <skill-name> [short description of what it does]
---

You are creating a new Claude Code skill. A skill lives at `~/.claude/skills/<skill-name>/SKILL.md`.

The user has provided: $ARGUMENTS

From this, extract:
1. **skill-name** — the slug (lowercase, hyphens only, no spaces)
2. **description** — a one-line summary of when/why to use the skill
3. **purpose** — what the skill should actually do when invoked

Then do the following:

## Step 1 — Confirm plan

State clearly:
- The file you will create: `~/.claude/skills/<skill-name>/SKILL.md`
- The name, description, and behavior you understood from the user's input
- Ask the user to confirm before writing, unless they already gave very clear instructions

## Step 2 — Write the skill file

Create the directory and file. Use this exact SKILL.md format:

```
---
name: <skill-name>
description: <one-line description — this is what Claude reads to decide relevance>
disable-model-invocation: true        # remove this line if agents should also be able to invoke it
argument-hint: <hint shown during autocomplete, e.g. "<input text>" or "<file path>">
---

# PURPOSE
<What this skill does and why>

# STEPS
- <Step 1>
- <Step 2>
- ...

# OUTPUT INSTRUCTIONS
- <Format, length, tone constraints>

# INPUT
$ARGUMENTS
```

Rules:
- `name` must be lowercase, numbers, and hyphens only — no spaces
- `description` should be specific enough that Claude can decide when to auto-invoke it
- Keep `disable-model-invocation: true` unless the user explicitly wants agents to invoke this skill
- `$ARGUMENTS` must appear verbatim in the body — it is replaced at runtime with the user's input
- Do NOT add extra frontmatter fields unless the user asks for them (e.g. `allowed-tools`, `model`, `context`)

## Step 3 — Confirm success

After writing the file, tell the user:
- The full path written
- How to invoke the skill: `/<skill-name> [arguments]`
- Any optional frontmatter fields they may want to add later (e.g. `allowed-tools`, `model`)
