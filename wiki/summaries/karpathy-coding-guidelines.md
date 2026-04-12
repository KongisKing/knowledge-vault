---
title: "Karpathy Coding Guidelines for LLMs"
date: 2026-04-12
tags: [coding-guidelines, llm-behavior, vibe-coding, code-quality, karpathy]
source: "https://github.com/forrestchang/andrej-karpathy-skills"
---

## Key Ideas

- **LLMs silently pick wrong assumptions** — they run with an interpretation without checking, leading to rewrites
- **LLMs overcomplicate code** — 1000 lines when 100 would do; premature abstraction; speculative features nobody asked for
- **LLMs do drive-by edits** — change comments, formatting, adjacent code while fixing something unrelated
- **Weak success criteria cause loops** — "make it work" requires constant clarification; verifiable goals let LLMs loop independently
- **Four principles address all four failure modes:** Think Before Coding, Simplicity First, Surgical Changes, Goal-Driven Execution
- **Test-first for bugs:** write a failing test that reproduces the bug BEFORE fixing it — if you can't write the test, you don't understand the bug yet

## Entities Mentioned

- [Andrej Karpathy](../entities/andrej-karpathy.md) — original observations on LLM coding pitfalls
- [forrestchang](../entities/forrestchang.md) — distilled Karpathy's X post into CLAUDE.md (14.1k ⭐)

## Concepts Mentioned

- [Surgical Changes](../concepts/surgical-changes.md) — touch only what the request requires
- [Think Before Coding](../concepts/think-before-coding.md) — surface assumptions before implementing
- [Goal-Driven Execution](../concepts/goal-driven-execution.md) — verifiable success criteria + test-first loop
- [Simplicity First](../concepts/simplicity-first.md) — minimum code that solves the problem

## Decisions / Actions

- Installed 3 new Kong skills from this source (2026-04-12): `think-before-coding`, `surgical-changes`, `goal-driven-execution`
- Added all 3 to mandatory Codex subagent prompt rules (now skills 1-7 required before any code)
- `Simplicity First` skipped — already covered by `incremental-implementation`

## Open Questions

- Should we merge Think Before Coding delta into `spec-driven-development` or keep it standalone?
- Should EXAMPLES.md patterns be added to each skill as concrete bad/good code examples?

## Related Pages

- [Knowledge OS — Personal LLM Wiki](../projects/knowledge-os.md)
- [Karpathy LLM Wiki Pattern](./karpathy-llm-wiki-pattern.md)
