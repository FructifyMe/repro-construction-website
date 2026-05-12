# Project agents — Repro Construction

This folder holds **subagent definitions** scoped to the Repro project. Subagents are specialized Claude instances that the main conversation can delegate work to. Each agent runs in its own isolated context window — meaning the heavy reading and research happens *outside* the main thread's token budget. Only the agent's final summary is returned.

## Why agents save tokens

Every token the main conversation reads or writes is billed. When you ask Claude to "search the codebase for X" or "fetch these 12 URLs and summarize," all of that raw content lands in the main thread's context — and stays there for the rest of the conversation. Delegating the same task to a subagent moves the raw content into the subagent's *separate* context. The main thread only sees the subagent's final report (typically 5–15 lines).

Practical numbers: a 20-URL web research task that costs ~40k tokens of inputs inline costs ~1–3k tokens of summary when delegated. Across a long session this compounds dramatically.

## Installation

These files need to live at `.claude/agents/` for Claude to find them automatically. Two paths:

**Option 1 — project-scoped (recommended for this client):** Once the Repro folder is cloned anywhere (e.g., via the GitHub repo), copy this `agents/` folder to `.claude/agents/` inside that clone. Claude Code and Cowork will pick up the agents automatically.

**Option 2 — globally available across all your projects:** Copy the files into `~/.claude/agents/` (Mac/Linux) or `%USERPROFILE%\.claude\agents\` (Windows). The token-conservator agent will then be available in every Cowork session, not just Repro.

## Agents defined here

### `token-conservator`

**When to invoke:** any task where the raw inputs are much larger than the answer.

Examples that fit:
- "Find every file that references the old Divi page IDs" — grep-heavy, returns a list
- "Read these 8 competitor sites and tell me what they all say in their hero copy" — fetch-heavy, returns a paragraph
- "Audit the project folder for stale files older than 30 days" — bash + filter, returns a list
- "Pull the keyword volume estimates for these 25 target queries" — search-heavy, returns a table

Examples that don't fit (just do them inline):
- "Edit this one line in this one file" — too small to bother delegating
- "Write the homepage copy" — generative, not extractive; the agent isn't faster at writing
- "What's the next step on the Repro project?" — purely conversational

**How to invoke from Claude:** Use the `Agent` tool with `subagent_type: "token-conservator"` and a brief that includes:
- The specific question or task (one sentence)
- Any context the agent needs that isn't obvious from the project (e.g., the canonical Repro URL, the list of competitor domains)
- What output format you want back
- A token budget hint if relevant ("under 200 words")

**Anti-pattern:** don't invoke for trivially small tasks. The agent has its own startup overhead (a few hundred tokens). For 1–2 file reads, do them inline.

## Adding new agents

Drop a new `.md` file in this folder with YAML frontmatter:

```yaml
---
name: my-agent-name
description: When this agent should be used. Be specific — Claude reads this to decide whether to invoke.
tools: Read, Grep, Glob, WebFetch, WebSearch, Bash
---

Agent system prompt goes here. This is what the subagent reads as its instructions
every time it's invoked. Keep it focused and operational, not aspirational.
```

The `tools` line restricts which tools the agent can call. For research/lookup agents, keep it to read-only tools. For agents that need to write files, add `Write` and `Edit`.

## Convention for this project

- Agents in this folder are scoped to the Repro engagement.
- Prefer one-job-only agents over multi-purpose ones — they're easier to invoke confidently.
- If an agent gets used regularly across clients, promote it to the global `~/.claude/agents/` folder.
