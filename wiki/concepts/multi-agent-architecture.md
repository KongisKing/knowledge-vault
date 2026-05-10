---
title: "Multi-Agent Architecture"
date: 2026-05-10
tags: [multi-agent, subagent, orchestration, agent-architecture]
source: "/Users/echandan7/.nanobot/workspace/kong-vs-gstack-gaps.md"
---

# Multi-Agent Architecture

## Definition
A system where a primary orchestrator agent delegates specialized tasks to purpose-built subagents, each optimized for a specific role (coding, research, writing, analysis). The orchestrator routes tasks, verifies outputs, and maintains context across the full workflow.

## Why It Matters
Single-agent systems hit token limits, model capability ceilings, and context bloat. Multi-agent systems allow each task to be handled by the best-fit model at the right temperature — e.g., Codex for code (low temp), Gemini for research (high context window), Haiku for writing (creative temp).

## Examples
- **Kong:** 4 subagents (Coder/Codex, Researcher/Gemini, Writer/Haiku, Analyst/Gemini) orchestrated by Sonnet 4.6
- **gstack:** 23 specialist slash-command roles orchestrated by Claude Opus 4.7
- **Key difference:** gstack has role breadth; Kong has multi-model routing and personalization depth

## Key Design Decisions
- Role specialization vs model specialization — Kong does both; gstack does role only
- Subagent prompt discipline: lean prompts, no unnecessary skill file reading (Coder-only)
- Verification rule: never trust subagent self-reported success — always verify independently
- Fail-closed: subagents should surface errors, not silently pass

## Related Concepts
- [Tool-Chaining Pipeline](../concepts/tool-chaining-pipeline.md)
- [Agent Harness](../concepts/agent-harness.md)
- [Agent Memory](../concepts/agent-memory.md)
- [Subagent Skill-Reading Rule](../concepts/subagent-skill-reading-rule.md)

## Sources
- [Kong vs gstack Gap Analysis](../summaries/kong-vs-gstack-gap-analysis.md)
