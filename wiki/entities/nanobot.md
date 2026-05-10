---
title: "nanobot"
date: 2026-05-10
tags: [tool, agent-harness, kong, open-source]
source: "https://pypi.org/project/nanobot-ai/"
---

# nanobot

## Type
Tool

## Description
nanobot-ai is the agent harness that powers Kong. An open-source Python framework (PyPI: `nanobot-ai`) that manages tools, subagents, memory consolidation (Dream), and Telegram/Discord channel integrations. Current version: v0.1.5.

## Role / Relevance
Kong's runtime environment. All of Kong's capabilities — subagent spawning, cron scheduling, file tools, web fetch — are provided by nanobot. Manual patches have been applied to nanobot internals to fix subagent silent failures, surface errors, and enable per-subagent model routing.

## Key Facts
- Version: v0.1.5 (as of May 2026)
- Dream: built-in memory consolidation (runs every 2h via cron)
- SSRF protection added in v0.1.5
- Manual patches applied: `fail_on_tool_error=False`, model param threading in spawn tool, subagent error surfacing
- ⚠️ Manual patches will be overwritten on `pip install --upgrade nanobot-ai`

## Related Projects
- [Kong Refinement](../projects/kong-refinement.md)
- [Knowledge OS](../projects/knowledge-os.md)

## Related Concepts
- [Agent Harness](../concepts/agent-harness.md)
- [Agent Memory](../concepts/agent-memory.md)

## Mentions
- [Kong vs gstack Gap Analysis](../summaries/kong-vs-gstack-gap-analysis.md)
