---
name: create-agent
description: Scaffold a new Claude Code agent definition by generating the correct AGENT.md file and placing it under ~/.claude/agents/<agent-name>/AGENT.md
disable-model-invocation: true
argument-hint: <agent-name> [short description of what the agent does]
---

You are creating a new Claude Code agent. An agent lives at `~/.claude/agents/<agent-name>/AGENT.md`.

The user has provided: $ARGUMENTS

From this, extract:
1. **agent-name** — the slug (lowercase, hyphens only, no spaces)
2. **description** — a one-line summary used by the parent agent to decide when to spawn this agent
3. **purpose** — what the agent specializes in and what tasks it should handle

Then do the following:

## Step 1 — Confirm plan

State clearly:
- The file you will create: `~/.claude/agents/<agent-name>/AGENT.md`
- The name, description, and behavior you understood from the user's input
- Ask the user to confirm before writing, unless they already gave very clear instructions

## Step 2 — Write the agent file

Create the directory and file. Use this exact AGENT.md format:

```
---
name: <agent-name>
description: <one-line description — used by Claude to decide when to spawn this agent. Be specific about trigger conditions>
model: claude-sonnet-4-6          # optional: set to claude-opus-4-6 for complex reasoning, claude-haiku-4-5-20251001 for speed
---

# IDENTITY AND PURPOSE
<Who this agent is and what it specializes in>

# WHEN TO USE
<Describe the conditions under which this agent should be spawned — be specific>

# CAPABILITIES
- <Capability 1>
- <Capability 2>
- ...

# STEPS
1. <Step 1>
2. <Step 2>
...

# OUTPUT INSTRUCTIONS
- <Format, length, tone, return value constraints>
- Always return a single, complete response to the parent agent
- Do not ask clarifying questions — work with what was provided

# CONSTRAINTS
- <Any tools, topics, or behaviors to avoid or require>
```

Rules:
- `name` must be lowercase, numbers, and hyphens only — no spaces
- `description` is critical — it controls when the parent spawns this agent. Make it specific with trigger verbs (e.g. "Use this agent when...", "Spawned for...", "Handles...")
- `model` is optional; omit it to inherit from the parent. Use `claude-opus-4-6` for deep reasoning tasks, `claude-haiku-4-5-20251001` for fast/cheap tasks
- Do NOT include `disable-model-invocation` — agents are spawned by Claude, not by users
- Do NOT add `user-invocable: false` unless you want to explicitly hide it from user slash commands (agents are not slash-command invocable by default)

## Step 3 — Confirm success

After writing the file, tell the user:
- The full path written
- How the agent will be triggered (via the Agent tool by Claude, or via `subagent_type` in tool calls)
- Suggested `description` refinements if the trigger condition could be made more precise
- Any optional frontmatter fields they may want to configure (e.g. `model`, `allowed-tools`)
