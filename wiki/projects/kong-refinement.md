---
title: "Kong Refinement — Closing the gstack Gap"
date: 2026-05-10
tags: [kong, gstack, agent-architecture, subagent, skill-system, active]
source: "/Users/echandan7/.nanobot/workspace/kong-vs-gstack-gaps.md"
---

# Kong Refinement — Closing the gstack Gap

## Status
Active

## Summary
A structured project to evolve Kong's architecture by benchmarking it against gstack (Garry Tan's Claude Code multi-agent setup, v1.30.0.0). The gap analysis identified 18 gaps across role breadth, pipeline formalization, security, and memory quality. Kong has 3 structural advantages to protect: multi-model routing, deep personalization, and portability. The project is broken into Quick Wins, Medium Term, and Long Term tracks.

## Key Decisions
- Benchmarked Kong against gstack v1.30.0.0 (May 2026)
- Kong's 3 structural advantages to protect: multi-model routing, deep personalization (SOUL.md), file-based portability
- gstack's 3 most critical gaps to close: specialist roles, pipeline chaining, structured artifact output
- Subagent skill-reading rule added to MEMORY.md — Coder-only, never Analyst/Researcher/Writer
- CHANGES.md established at `/Users/echandan7/.nanobot/workspace/patches/CHANGES.md` for tracking all patches

## Gap Summary (18 total)

### High Impact
- **G1** — Specialist Subagent Roles: Kong has 4; gstack has 23 (QA, Doc, Security, Designer, Architect missing)
- **G2** — Formalized Tool-Chaining Pipelines: gstack has `/design→/plan→/code→/qa→/ship`; Kong is ad-hoc
- **G3** — ML-Based Security Classifier: gstack scores injections (WARN 0.75 / BLOCK 0.92); Kong uses rules only

### Medium Impact
- **G4** — Vector Memory (gbrain): gstack has semantic retrieval; Kong has flat markdown
- **G5** — Structured Artifact Output: gstack auto-saves artifacts per tool; Kong produces freeform chat
- **G6** — Per-Project State Directory: `.gstack/projects/[name]/`; Kong has global MEMORY.md only
- **G7** — Architecture Decision Records (ADR): gstack has `/adr`; Kong has none
- **G8** — Changelog & Versioning Automation: gstack has `/changelog`, `/version`, `/rollback`
- **G9** — Accessibility Auditing: gstack has `/accessibility`; Kong has none
- **G10** — Performance Analysis Role: gstack has `/perf`; Kong handles ad-hoc
- **G11** — UI/UX Design Roles: gstack has `/design`, `/ux`, `/brand`; Kong has Writer only

### Low Impact
- **G12** — Worktree-Aware State Isolation
- **G13** — Fail-Closed Error Surfacing (patched but not named principle)
- **G14** — Community / Open Contribution Model
- **G15** — Brain Model Tier (Opus 4.7 vs Sonnet 4.6)
- **G16** — Slash-Command UX in Telegram
- **G17** — MCP Remote Server Integration
- **G18** — Observability / Audit Trail

## Next Actions
- [ ] Quick wins: Add `.kong/` project directory convention, ADR skill, structured artifact output rule
- [ ] Medium term: Add QA Engineer, Doc Engineer, Security Auditor subagents; build pipeline runner skill
- [ ] Medium term: Formalize `/design→/plan→/code→/qa→/ship` pipeline as a SKILL.md
- [ ] Long term: Evaluate ML classifier for prompt injection (nanobot patch or proxy layer)
- [ ] Long term: Evaluate ChromaDB/LanceDB for semantic memory alongside MEMORY.md

## Open Questions
- Should new specialist subagents use Gemini or Sonnet? (cost vs quality tradeoff)
- Pipeline runner — build as a SKILL.md or as a nanobot patch?
- Vector memory — worth the portability tradeoff? Or keep flat markdown?
- Open-source Kong's skill library as `kong-skills` repo?

## Related Entities
- [gstack](../entities/gstack.md)
- [Garry Tan](../entities/garry-tan.md)
- [nanobot](../entities/nanobot.md)

## Related Concepts
- [Multi-Agent Architecture](../concepts/multi-agent-architecture.md)
- [Tool-Chaining Pipeline](../concepts/tool-chaining-pipeline.md)
- [Subagent Skill-Reading Rule](../concepts/subagent-skill-reading-rule.md)
- [Agent Harness](../concepts/agent-harness.md)
- [Agent Memory](../concepts/agent-memory.md)

## Sources
- [Kong vs gstack Gap Analysis](../summaries/kong-vs-gstack-gap-analysis.md)
