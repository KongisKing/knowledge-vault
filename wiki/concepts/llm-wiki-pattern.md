---
title: "LLM Wiki Pattern"
date: 2026-04-12
tags: [knowledge-management, llm, compounding, wiki, pattern]
source: "https://x.com/defileo/status/2042241063612502162"
---

## Definition
A pattern where an LLM incrementally builds and maintains a persistent, interlinked wiki from raw sources — rather than re-deriving answers from scratch on every query (RAG). Knowledge is compiled once and kept current.

## Why It Matters
- Answers compound over time — each new source enriches existing pages
- Cross-references and contradictions are pre-resolved, not re-discovered per query
- The human curates and directs; the LLM does all bookkeeping
- No embeddings or vector infrastructure needed at moderate scale

## Three Layers
1. **Raw sources** — immutable input docs (articles, notes, transcripts)
2. **Wiki** — LLM-maintained markdown pages (summaries, entities, concepts, projects)
3. **Schema (AGENTS.md)** — config file telling the LLM how to structure and maintain the wiki

## Three Operations
- **Ingest** — process a new source, update 10-15 wiki pages
- **Query** — scan index, read relevant pages, answer with citations
- **Lint** — health check: contradictions, orphans, gaps, stale claims

## Examples
- Kong's `~/knowledge-vault/` — our implementation of this pattern
- Personal research wikis, book companion wikis, team internal wikis

## Related Concepts
- [Compounding Knowledge](./compounding-knowledge.md)
- [RAG (Retrieval-Augmented Generation)](./rag.md)

## Sources
- [Karpathy LLM Wiki Pattern](../summaries/karpathy-llm-wiki-pattern.md)
