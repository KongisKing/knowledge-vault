---
title: "Agent Harness"
date: 2026-04-12
tags: [agent, scaffolding, llm, framework, memory]
source: "https://x.com/hwchase17/status/2042978500567609738"
---

## Definition
The scaffolding around an LLM that gives it tools, manages its context window, handles memory (short and long term), and orchestrates interactions with external systems. The harness is what turns a raw LLM into an agent.

## Why It Matters
Agents cannot exist without harnesses. Even as models improve and absorb old scaffolding needs, new scaffolding requirements emerge. The harness is not going away — it evolves.

## Examples
- LangChain, LangGraph
- nanobot (Kong's harness)
- Claude Code / Claude Agent SDK
- OpenAI Codex CLI
- MemGPT / Letta AI

## Key Insight
Memory is not a plugin you attach to a harness — it IS the harness. Every memory decision (what enters context, what's compressed, what persists) is a harness decision.

## The Lock-in Risk
Closed harnesses (especially behind APIs) mean you don't own or control your agent's memory. Open harnesses keep memory portable and under your control.

## Related Concepts
- [Agent Memory](./agent-memory.md)
- [Vendor Lock-in](./vendor-lock-in.md)
- [Context Compaction](./context-compaction.md)
- [Data Flywheel](./data-flywheel.md)

## Sources
- [Your Harness, Your Memory](../summaries/harrison-chase-your-harness-your-memory.md)
