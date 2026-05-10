---
title: "Tool-Chaining Pipeline"
date: 2026-05-10
tags: [pipeline, tool-chaining, workflow, agent-architecture]
source: "/Users/echandan7/.nanobot/workspace/kong-vs-gstack-gaps.md"
---

# Tool-Chaining Pipeline

## Definition
A formalized sequence of agent tool/skill invocations where the output of each step becomes the structured input to the next. Unlike ad-hoc skill invocation, a pipeline defines the full flow upfront and enforces artifact handoffs between steps.

## Why It Matters
Without formalized pipelines, multi-agent systems devolve into ad-hoc task delegation where outputs are freeform chat, not structured artifacts. Pipelines ensure: (1) every step produces a verifiable artifact, (2) the next step receives a defined input, (3) the full workflow is auditable.

## Examples
- **gstack pipeline:** `/design → /plan → /code → /qa → /ship` — each step produces a saved artifact (design doc, task list, code, test report, release note)
- **Kong current state:** Skills invoked ad-hoc, outputs are freeform. No enforced artifact schema or auto-save.
- **Kong target state:** Pipeline runner SKILL.md that chains existing Kong skills with artifact handoffs

## Implementation Options for Kong
1. **SKILL.md pipeline runner** — a skill that orchestrates other skills in sequence (Medium complexity, ~1-2 days)
2. **nanobot patch** — add pipeline primitives to the agent loop (High complexity, requires core changes)
3. **Convention-based** — standardize artifact output paths and Kong manually chains them (Low complexity, quick win)

## Related Concepts
- [Multi-Agent Architecture](../concepts/multi-agent-architecture.md)
- [Subagent Skill-Reading Rule](../concepts/subagent-skill-reading-rule.md)

## Sources
- [Kong vs gstack Gap Analysis](../summaries/kong-vs-gstack-gap-analysis.md)
