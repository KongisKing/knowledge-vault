---
title: "gstack"
date: 2026-05-10
tags: [tool, agent-architecture, claude-code, multi-agent]
source: "https://github.com/garrytan/gstack"
---

# gstack

## Type
Tool

## Description
gstack is Garry Tan's (YC President) personal Claude Code multi-agent setup, open-sourced at v1.30.0.0. It defines 23 specialist slash-command roles (QA, Doc, Security, Designer, Architect, Release Manager, Performance, Brand, UX, and more) with formalized tool-chaining pipelines and gbrain vector memory.

## Role / Relevance
Used as the primary benchmark for Kong's architectural gap analysis (May 2026). gstack represents the state-of-the-art in personal Claude Code agent setups. Its open-source nature and community PRs (21 in v1.30.0.0) make it a useful reference for Kong's evolution roadmap.

## Key Capabilities
- 23 slash-command specialist roles
- Formalized pipelines: `/design → /plan → /code → /qa → /ship`
- gbrain v0.30.0+ — vector-indexed semantic memory
- ML-scored prompt injection classifier (WARN: 0.75, BLOCK: 0.92)
- Claude Opus 4.7 as primary reasoning model
- Community contribution model (21 PRs in v1.30.0.0)
- Per-project state directories (`.gstack/projects/[name]/`)

## Kong's Advantages Over gstack
- Multi-model routing (Codex + Gemini 2.5 Pro + Sonnet 4.6 vs single Opus 4.7)
- Deep personalization (Chandan-specific SOUL.md vs generic project config)
- Zero-dependency portability (flat markdown vs gbrain vector DB requirement)
- Telegram-native interface

## Related Projects
- [Kong Refinement](../projects/kong-refinement.md)

## Related Concepts
- [Multi-Agent Architecture](../concepts/multi-agent-architecture.md)
- [Tool-Chaining Pipeline](../concepts/tool-chaining-pipeline.md)
- [Agent Memory](../concepts/agent-memory.md)

## Mentions
- [Kong vs gstack Gap Analysis](../summaries/kong-vs-gstack-gap-analysis.md)
