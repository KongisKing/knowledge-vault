---
title: "Goal-Driven Execution"
date: 2026-04-12
tags: [coding-discipline, test-first, success-criteria, tdd, llm-behavior]
source: "https://github.com/forrestchang/andrej-karpathy-skills"
---

## Definition
The practice of defining verifiable success criteria before implementing anything. Transform vague tasks ("fix this") into testable goals ("write a failing test that reproduces it, then make it pass").

## Why It Matters
Weak success criteria ("make it work") require constant back-and-forth. Strong criteria let an LLM loop independently until done — no clarification needed.

## The Test-First Bug Loop
1. Write a test that FAILS → reproduces the exact bug
2. Implement the fix
3. Verify test passes + full suite still green

If you can't write a failing test, you don't understand the bug yet.

## The Plan Format
```
Plan:
1. [Step] → verify: [how I'll confirm it worked]
2. [Step] → verify: [how I'll confirm it worked]
3. [Step] → verify: [how I'll confirm it worked]
```

## Strong vs Weak Criteria
| Weak | Strong |
|---|---|
| "Make it work" | "All 5 existing tests pass + new edge case test passes" |
| "Fix performance" | "Page load < 2s on throttled 3G" |
| "Make it secure" | "OWASP Top 10 checklist passes, no secrets in code" |

## Related Concepts
- [Think Before Coding](./think-before-coding.md)
- [Surgical Changes](./surgical-changes.md)

## Sources
- [Karpathy Coding Guidelines](../summaries/karpathy-coding-guidelines.md)
