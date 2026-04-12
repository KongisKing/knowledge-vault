---
title: "Agent Memory"
date: 2026-04-12
tags: [memory, agent, context, long-term-memory, personalization]
source: "https://x.com/hwchase17/status/2042978500567609738"
---

## Definition
The mechanism by which an agent retains and uses information — both within a session (short-term) and across sessions (long-term). Memory is what makes agents improve over time and feel personalised.

## Two Types

### Short-term memory
- Messages in the current conversation
- Large tool call results
- Managed entirely within the context window
- Handled automatically by the harness

### Long-term memory
- Cross-session knowledge about users, preferences, past interactions
- Must be explicitly stored, retrieved, and updated by the harness
- This is where the real strategic value (and lock-in risk) lives

## Why It's the Real Moat
> Without memory → your agent is easily copied by anyone with the same tools
> With memory → you build a proprietary dataset of user interactions and preferences

Memory is what enables the [Data Flywheel](./data-flywheel.md) — agents that get smarter and more personalised the more they're used.

## The Ownership Problem
Memory is inseparable from the harness. If your harness is closed or behind an API, you don't own your memory. Model providers are deliberately engineering this lock-in.

## Our Implementation
Kong's memory lives in plain files on Chandan's machine:
- `MEMORY.md` — long-term facts
- `HISTORY.md` — append-only event log
- `~/knowledge-vault/` — compounding wiki (the open memory layer)

Fully portable. Zero lock-in.

## Related Concepts
- [Agent Harness](./agent-harness.md)
- [Vendor Lock-in](./vendor-lock-in.md)
- [Context Compaction](./context-compaction.md)
- [Data Flywheel](./data-flywheel.md)
- [LLM Wiki Pattern](./llm-wiki-pattern.md)

## Sources
- [Your Harness, Your Memory](../summaries/harrison-chase-your-harness-your-memory.md)
