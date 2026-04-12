---
title: "Knowledge OS — Personal LLM Wiki"
date: 2026-04-12
tags: [knowledge-os, llm-wiki, personal-knowledge, kong, productivity]
source: "/Users/echandan7/.nanobot/workspace/contexts/knowledge-os.md"
---

# Knowledge OS — Personal LLM Wiki

## Status
Active — Initial build complete

## Summary
A personal knowledge operating system inspired by Andrej Karpathy's LLM Wiki pattern. Instead of a flat MEMORY.md blob, this is a **persistent, compounding wiki** that Kong incrementally maintains. Raw sources are ingested, structured into cross-linked wiki pages, and queryable at any time. The system lives at `~/knowledge-vault/`.

## Core Idea

> "Instead of one flat MEMORY.md blob, build a persistent compounding wiki that Kong incrementally maintains."
> — from the knowledge-os context

The key insight: Kong is already doing Ingest/Query/Lint ad hoc. This project **formalizes** those operations with a schema (AGENTS.md) and a consistent directory structure.

## Architecture Decisions

- **No RAG / no embeddings** — at personal scale, `index.md` + reading relevant pages is sufficient. Keep it simple.
- **Separate vault repo** — lives at `~/knowledge-vault/`, separate from kongworkspace
- **Git-backed** — version controlled, pushed to GitHub (`KongisKing/knowledge-vault`)
- **AGENTS.md as the operating manual** — Kong reads this to understand structure and workflows
- **3 formalized operations:** INGEST, QUERY, LINT (see AGENTS.md for full workflow specs)

## Directory Structure

```
~/knowledge-vault/
  raw/          → immutable source drops
  wiki/
    summaries/  → one page per ingested source
    entities/   → people, companies, products
    concepts/   → ideas, frameworks, patterns
    projects/   → one page per active project
  index.md      → master catalog
  log.md        → append-only operation log
  AGENTS.md     → Kong's schema + workflows
  README.md     → human-readable overview
```

## Next Actions

- [ ] Ingest first real external source (article, URL, or note)
- [ ] Run first LINT to check vault health
- [ ] Decide: migrate existing MEMORY.md into vault or run in parallel?
- [ ] Evaluate Obsidian as a viewer (vs VS Code / plain markdown)

## Open Questions

- Do we migrate existing MEMORY.md into the new structure or start fresh alongside it?
- Obsidian as the viewer or just VS Code / plain markdown?
- What cadence for running LINT? (monthly? after every 10 ingests?)

## Related Entities

- [[entities/andrej-karpathy]] — Originator of the LLM Wiki pattern that inspired this system
- [[entities/kong]] — The LLM that operates and maintains this vault

## Related Concepts

- [[concepts/llm-wiki]] — The pattern: LLM as active maintainer of a structured knowledge base
- [[concepts/knowledge-compounding]] — Each ingest makes the vault more connected and useful
- [[concepts/index-based-retrieval]] — Using index.md + reading pages instead of vector embeddings

## Sources

- Source context: `/Users/echandan7/.nanobot/workspace/contexts/knowledge-os.md`
- Inspiration: Andrej Karpathy's LLM Wiki pattern (via defileo's X post)
