---
title: "Zenoti — Agentic API Strategy"
date: 2026-04-10
tags: [zenoti, agentic-api, mcp, product-strategy, api-platform]
source: "/Users/echandan7/.nanobot/workspace/contexts/zenoti.md"
---

# Zenoti — Agentic API Strategy

## Status
Active

## Summary
Zenoti is building an Agentic API strategy to position its salon/spa management platform for the AI-native era. The strategy enables LLM agents to interact with Zenoti's systems — booking appointments, managing operations — through a structured 3-layer architecture culminating in a live CPO demo milestone in June 2026.

## Key Decisions

- **3-Layer Strategy adopted:**
  1. **Action API Foundation** — clean, intent-based REST APIs for core actions
  2. **MCP Server + SDK** — open-source Model Context Protocol server on GitHub (Zenoti-Spa org) enabling any LLM to connect
  3. **Hosted Experiences** — turnkey AI copilots for Zenoti enterprise clients

- **Open-source mandate:** MCP server will be open-sourced under the Zenoti-Spa GitHub org

- **Pod resourcing:** 2 Backend Engineers + 1 Platform Engineer + 1 Solutions Architect for 3 quarters

- **June 2026 milestone:** CPO demo — Claude books a Zenoti appointment live

## Deliverables Completed

- HTML slide deck v3 (14 slides, 54KB) — built and sent ✅
- Strategy doc: `zenoti-agentic-api-strategy.md`
- Exec brief: `zenoti-agentic-exec-brief-and-deck.md`

## Next Actions

- [ ] Present deck to Anand (CPO)
- [ ] Identify 2–3 enterprise design partners for Q4 copilot beta
- [ ] Get approval on pod resourcing + open-source mandate

## Open Questions

- Has Anand seen the deck yet?
- Any feedback from leadership on the strategy?
- Timeline for pod staffing approval?

## Related Entities

- [[entities/anand]] — CPO, primary stakeholder for the strategy presentation
- [[entities/zenoti]] — The company; salon/spa management SaaS platform
- [[entities/zenoti-spa-github-org]] — GitHub org for open-source MCP server

## Related Concepts

- [[concepts/model-context-protocol]] — MCP; the open protocol enabling LLM ↔ Zenoti integration
- [[concepts/agentic-api]] — APIs designed for LLM agents to consume
- [[concepts/action-api]] — Intent-based REST API layer (Layer 1 of the strategy)

## Sources

- Source context: `/Users/echandan7/.nanobot/workspace/contexts/zenoti.md`
