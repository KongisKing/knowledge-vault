---
title: "Your Harness, Your Memory"
date: 2026-04-12
tags: [agent-harness, memory, lock-in, langchain, open-source, agentic-systems]
source: "https://x.com/hwchase17/status/2042978500567609738"
---

## Key Ideas

- **Agent harnesses are not going away** — as models get better, old scaffolding disappears but new scaffolding replaces it. An agent is by definition an LLM + tools + data sources. There will always be a system around the LLM. Even Claude Code (from the makers of the best model) has a harness.
- **Memory IS the harness, not a plugin** — you cannot separate memory from the harness. Every decision about what goes into context, what survives compaction, what persists across sessions — these are all harness decisions. "Plugging memory into a harness is like plugging driving into a car."
- **Three levels of lock-in risk:**
  - Mildly bad: Stateful APIs (OpenAI Responses API, Anthropic server-side compaction) — state on their servers, can't switch models mid-thread
  - Bad: Closed harnesses (Claude Agent SDK) — memory managed in unknown, non-transferable ways
  - Worst: Full harness + memory behind an API — zero ownership, zero visibility, zero portability
- **Model providers are deliberately engineering lock-in via memory** — even open-source Codex generates encrypted compaction summaries only usable inside OpenAI's ecosystem. This is intentional.
- **Memory = the real moat** — without memory, any agent is replicable. With memory, you build a proprietary dataset of user interactions and preferences. That compounding flywheel is what providers are racing to own.
- **The solution: open harnesses where you own the memory layer** — your memory should live in files/systems you control, not behind a third-party API.

## Entities Mentioned

- [Harrison Chase](../entities/harrison-chase.md) — LangChain founder, author of this post
- [LangChain](../entities/langchain.md) — open-source agent harness framework
- [Sarah Wooders](../entities/sarah-wooders.md) — co-creator of MemGPT / Letta AI; wrote "memory isn't a plugin, it's the harness"
- [Letta AI](../entities/letta-ai.md) — memory-focused agent platform (formerly MemGPT)
- [OpenAI](../entities/openai.md) — model provider; Responses API and Codex referenced
- [Anthropic](../entities/anthropic.md) — model provider; Claude Agent SDK and server-side compaction referenced

## Concepts Mentioned

- [Agent Harness](../concepts/agent-harness.md) — scaffolding around an LLM that manages tools, context, and memory
- [Agent Memory](../concepts/agent-memory.md) — short-term (context window) and long-term (cross-session) memory managed by the harness
- [Vendor Lock-in](../concepts/vendor-lock-in.md) — losing portability when memory/state lives inside a provider's platform
- [Data Flywheel](../concepts/data-flywheel.md) — compounding proprietary dataset built from user interactions over time
- [Context Compaction](../concepts/context-compaction.md) — summarising/compressing long conversations to fit context windows

## Decisions / Actions

- Kong's architecture already follows this principle: MEMORY.md, HISTORY.md, knowledge-vault all live as plain files on Chandan's machine — fully portable, zero lock-in
- Knowledge vault itself IS the open memory layer — compounding, owned, portable

## Open Questions

- As memory best practices mature, will separate memory systems (like Letta) start making sense even for smaller setups?
- Should Kong's MEMORY.md be migrated into the vault structure eventually, making it fully queryable?
- How do we handle memory portability if nanobot's format changes?

## Related Pages

- [Knowledge OS — Personal LLM Wiki](../projects/knowledge-os.md)
- [Karpathy LLM Wiki Pattern](./karpathy-llm-wiki-pattern.md)
