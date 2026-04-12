---
title: "Think Before Coding"
date: 2026-04-12
tags: [coding-discipline, assumptions, ambiguity, llm-behavior]
source: "https://github.com/forrestchang/andrej-karpathy-skills"
---

## Definition
The discipline of explicitly stating assumptions, surfacing ambiguity, and presenting tradeoffs BEFORE writing any code — even a single function. Don't pick an interpretation silently and run with it.

## Why It Matters
LLMs silently make assumptions (export all users? which fields? what format?) and implement based on the wrong one. This leads to rewrites, wasted effort, and user frustration.

## The Four Checks Before Coding
1. What assumptions am I making? (state them)
2. Are there multiple valid interpretations? (present them, don't pick silently)
3. Is there a simpler approach? (say so before building the complex one)
4. What's genuinely unclear? (stop and name it, don't guess)

## The Assumption Declaration
```
Before I start:
- Assuming: [assumption 1]
- Assuming: [assumption 2]
- Unclear: [what needs clarification]
Proceeding with [approach] unless you correct me.
```

## Related Concepts
- [Surgical Changes](./surgical-changes.md)
- [Goal-Driven Execution](./goal-driven-execution.md)

## Sources
- [Karpathy Coding Guidelines](../summaries/karpathy-coding-guidelines.md)
