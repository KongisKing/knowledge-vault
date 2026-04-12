---
title: "Simplicity First"
date: 2026-04-12
tags: [coding-discipline, yagni, over-engineering, llm-behavior]
source: "https://github.com/forrestchang/andrej-karpathy-skills"
---

## Definition
Write the minimum code that solves today's problem. No speculative features, no premature abstractions, no flexibility that wasn't requested. If 200 lines could be 50 — rewrite it.

## Why It Matters
LLMs love to over-engineer. A request for "a discount function" becomes a Strategy Pattern with abstract base classes, config objects, and validators. This code is harder to understand, slower to ship, and harder to test.

## The Senior Engineer Test
> "Would a senior engineer say this is overcomplicated?"
If yes — simplify.

## Rules
- No features beyond what was asked
- No abstractions for single-use code
- No "flexibility" or "configurability" that wasn't requested
- No error handling for impossible scenarios
- Add complexity only when the requirement actually arrives

## Related Concepts
- [Surgical Changes](./surgical-changes.md)
- [Goal-Driven Execution](./goal-driven-execution.md)

## Sources
- [Karpathy Coding Guidelines](../summaries/karpathy-coding-guidelines.md)
