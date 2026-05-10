---
title: "Subagent Skill-Reading Rule"
date: 2026-05-10
tags: [subagent, skill-reading, prompt-discipline, kong-rule]
source: "/Users/echandan7/.nanobot/workspace/memory/MEMORY.md"
---

# Subagent Skill-Reading Rule

## Definition
A mandatory Kong operating rule: skill file reading instructions are ONLY included in Coder (Codex) subagent prompts when writing code. Analyst, Researcher, Writer, and all other non-Coder subagents must never be instructed to read skill files, MEMORY.md, SOUL.md, AGENTS.md, TOOLS.md, config.json, or HEARTBEAT.md unless the task explicitly requires it.

## Why It Matters
Each skill file read = 1 tool call. With 40 max iterations per subagent, reading 7+ skill files before doing any work burns 15–20 iterations on overhead, leaving insufficient budget for the actual task. This was the root cause of multiple Analyst subagent failures in May 2026 (subagents `588c11ac`, `34bd3b99`).

## Examples
- **Wrong:** Analyst subagent prompt includes 7 Coder skill files → burns 18 tool calls → hits iteration limit → fails silently
- **Right:** Analyst subagent prompt says "read the research file, write the report" → 3 tool calls overhead → completes in budget

## Rule (verbatim from MEMORY.md)
- Skill file reading is ONLY for the Coder (Codex) subagent when writing code
- NEVER include skill reading in Analyst, Researcher, Writer, or non-Coder prompts
- NEVER let a subagent read MEMORY.md, SOUL.md, AGENTS.md, TOOLS.md, config.json, or HEARTBEAT.md unless explicitly required
- Subagent prompts must be lean and task-focused

## Related Concepts
- [Multi-Agent Architecture](../concepts/multi-agent-architecture.md)
- [Goal-Driven Execution](../concepts/goal-driven-execution.md)

## Sources
- [Kong vs gstack Gap Analysis](../summaries/kong-vs-gstack-gap-analysis.md)
