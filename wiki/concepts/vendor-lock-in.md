---
title: "Vendor Lock-in"
date: 2026-04-12
tags: [lock-in, portability, open-source, strategy, risk]
source: "https://x.com/hwchase17/status/2042978500567609738"
---

## Definition
The state where switching away from a platform becomes prohibitively costly because critical data, logic, or state lives inside that platform in a non-portable form.

## In Agentic AI — Three Levels

| Level | Example | What you lose |
|---|---|---|
| Mildly bad | OpenAI Responses API, Anthropic server-side compaction | Can't switch models mid-thread |
| Bad | Closed harnesses (Claude Agent SDK) | Memory managed in unknown, non-transferable ways |
| Worst | Full harness + memory behind API | Zero ownership, zero visibility, zero portability |

## Why Model Providers Want This
Memory creates a compounding data flywheel. Once your agent has months of user interaction history living in a provider's platform, switching costs become enormous. This is a stronger moat than the model itself — models are increasingly commoditised, memory is not.

## How to Avoid It
- Use open-source harnesses (LangChain, nanobot, etc.)
- Store memory in files/systems you control
- Avoid stateful APIs for long-term memory
- Own your compaction logic

## Related Concepts
- [Agent Harness](./agent-harness.md)
- [Agent Memory](./agent-memory.md)
- [Data Flywheel](./data-flywheel.md)

## Sources
- [Your Harness, Your Memory](../summaries/harrison-chase-your-harness-your-memory.md)
