---
title: "Surgical Changes"
date: 2026-04-12
tags: [coding-discipline, code-quality, vibe-coding, llm-behavior]
source: "https://github.com/forrestchang/andrej-karpathy-skills"
---

## Definition
A coding discipline where every changed line must trace directly to the user's request. You touch only what you must, and clean up only your own mess — nothing else.

## Why It Matters
LLMs have a strong tendency to "improve" adjacent code while fixing something unrelated — changing quote styles, adding type hints, reformatting whitespace, deleting dead code they noticed. This creates noisy diffs, introduces unintended regressions, and makes code review harder.

## The Four Rules
1. Don't touch adjacent code, comments, or formatting
2. Match existing style even if you'd do it differently
3. Remove only orphans YOUR changes created (not pre-existing dead code)
4. If you notice an unrelated issue — mention it, don't fix it

## The Diff Test
> "Does every changed line trace directly to the user's request?"
If any line changed for another reason — revert it.

## Related Concepts
- [Think Before Coding](./think-before-coding.md)
- [Goal-Driven Execution](./goal-driven-execution.md)
- [Simplicity First](./simplicity-first.md)

## Sources
- [Karpathy Coding Guidelines](../summaries/karpathy-coding-guidelines.md)
