---
title: "Kong vs gstack — Gap Analysis"
date: 2026-05-10
tags: [kong, gstack, gap-analysis, agent-architecture, multi-agent]
source: "/Users/echandan7/.nanobot/workspace/kong-vs-gstack-gaps.md"
---

# Kong vs gstack — Gap Analysis

## Key Ideas
- gstack (Garry Tan's Claude Code setup, v1.30.0.0) has 23 specialist slash-command roles; Kong has 4 subagents — the biggest structural gap
- gstack uses formalized pipelines (`/design→/plan→/code→/qa→/ship`); Kong invokes skills ad-hoc with no chained output flow
- gstack has ML-scored prompt injection detection (WARN: 0.75, BLOCK: 0.92); Kong uses rule-based SOUL.md guardrails
- gstack uses gbrain (vector-indexed semantic memory); Kong uses flat markdown (MEMORY.md + knowledge-vault) — Kong's approach wins on portability
- Kong's 3 structural advantages: multi-model routing (Codex + Gemini + Sonnet), deep personalization (Chandan-specific SOUL.md), zero-dependency portability
- 18 gaps identified total: 3 High, 8 Medium, 5 Low impact
- 7 quick wins identified (all under 2 hours each): `.kong/` dir convention, fail-closed MEMORY.md rule, ADR skill, structured artifact output rule, accessibility SKILL.md stub, changelog automation, pipeline runner sketch

## Entities Mentioned
- [gstack](../entities/gstack.md)
- [Garry Tan](../entities/garry-tan.md)
- [nanobot](../entities/nanobot.md)

## Concepts Mentioned
- [Multi-Agent Architecture](../concepts/multi-agent-architecture.md)
- [Tool-Chaining Pipeline](../concepts/tool-chaining-pipeline.md)
- [Subagent Skill-Reading Rule](../concepts/subagent-skill-reading-rule.md)
- [Agent Memory](../concepts/agent-memory.md)
- [Vendor Lock-in](../concepts/vendor-lock-in.md)

## Decisions / Actions
- Added Subagent Skill-Reading Rule to MEMORY.md (Coder-only skill reading, never Analyst/Researcher/Writer)
- Established CHANGES.md at `/Users/echandan7/.nanobot/workspace/patches/CHANGES.md`
- Kong Refinement project created as active project in knowledge vault
- Priority order: G1 (specialist roles) → G2 (pipelines) → G5 (artifact output) → G7 (ADRs)

## Open Questions
- Should new specialist subagents use Gemini or Sonnet?
- Pipeline runner — SKILL.md or nanobot patch?
- Vector memory — worth the portability tradeoff?
- Open-source Kong's skill library?

## Related Pages
- [Kong Refinement Project](../projects/kong-refinement.md)
- [Agent Harness](../concepts/agent-harness.md)
- [Agent Memory](../concepts/agent-memory.md)
