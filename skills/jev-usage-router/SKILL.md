---
name: jev-usage-router
description: 5-action decision router and circuit breaker pattern to prevent agent token burn and infinite error loops.
version: 1.0.0
author: mommocmoc
license: MIT
---

# Jev Usage Router & Circuit Breaker

An autonomous agent circuit breaker skill implementing the 5-action decision router pattern (inspired by TypeSafe Jev System 1 and Grok Bot architecture).

It intercepts costly, recursive, or irreversible agent operations before they burn tokens or get trapped in repetitive loops.

## Supported Agents
- **Claude Code**: `.claude/skills/jev-usage-router/`
- **Antigravity (AGY)**: `.agent/skills/jev-usage-router/` or `~/.gemini/antigravity/skills/`
- **Codex**: `.codex/skills/jev-usage-router/`
- **Hermes**: `~/.hermes/skills/autonomous-ai-agents/jev-usage-router/`

## Quick Install
```bash
# Universal install via npx skills
npx skills add mommocmoc/jev-usage-router

# Specific agent installs
npx skills add mommocmoc/jev-usage-router -a claude-code -g -y
npx skills add mommocmoc/jev-usage-router -a antigravity -g -y
npx skills add mommocmoc/jev-usage-router -a codex -g -y
```

## The 5 Fixed Actions

Before triggering heavy browser navigation, deep web scrapes, subagent delegations, or error retries, the agent evaluates state across 5 deterministic criteria:

1. `proceed`: Nothing indicates failure; continue planned execution.
2. `reuse_cache`: Fresh artifacts or files already exist on local disk. Skip expensive network/browser calls.
3. `stop_retry`: Identical failure occurred 2+ times consecutively. Halt immediately and report root cause.
4. `research_capped`: 3–5 high-signal sources have been gathered. Stop infinite web queries and begin synthesis.
5. `ask_human`: Operation is irreversible (outbound emails, public posts, billing, deletions). Require human authorization.

## Minimal State Vector
```json
{
  "goal": "<high-level objective>",
  "task_type": "browser | research | retry | outbound | subagent",
  "last_error": "<error text or 'none'>",
  "repeats": 0
}
```
