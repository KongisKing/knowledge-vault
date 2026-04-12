---
title: "Karpathy LLM Wiki Pattern"
date: 2026-04-12
tags: [llm-wiki, knowledge-management, second-brain, obsidian, rag, compounding-knowledge]
source: "https://x.com/defileo/status/2042241063612502162"
---

## Key Ideas

- **Compounding wiki vs RAG:** RAG re-derives answers from raw docs every time — nothing accumulates. The LLM Wiki pattern instead builds a persistent, interlinked wiki that gets richer with every source added.
- **Three layers:** Raw sources (immutable) → Wiki (LLM-maintained markdown) → Schema/AGENTS.md (tells LLM how to operate).
- **Three operations:** Ingest (read source → update 10-15 wiki pages), Query (scan index → answer with citations), Lint (health check: contradictions, orphans, gaps).
- **The human's job:** Curate sources, ask good questions, direct analysis. The LLM does all bookkeeping — cross-references, summaries, consistency.
- **index.md as lightweight RAG:** At moderate scale (~100 sources), a well-maintained index file replaces the need for embeddings or vector search.
- **Answers can be filed back:** A valuable query response is itself new knowledge — file it as a wiki page so explorations compound too.
- **Obsidian as the viewer:** LLM is the programmer, wiki is the codebase, Obsidian is the IDE. Graph view reveals connections.
- **Vannevar Bush's Memex vision:** Private, actively curated knowledge store with associative trails. LLM solves the maintenance problem Bush couldn't.

## Entities Mentioned

- [Andrej Karpathy](../entities/andrej-karpathy.md) — original author of the LLM Wiki pattern
- [Obsidian](../entities/obsidian.md) — markdown-based knowledge tool used as the wiki viewer
- [Claude Code](../entities/claude-code.md) — LLM agent used to maintain the wiki

## Concepts Mentioned

- [LLM Wiki Pattern](../concepts/llm-wiki-pattern.md) — the core pattern described in this source
- [Compounding Knowledge](../concepts/compounding-knowledge.md) — knowledge that accumulates and cross-references over time
- [RAG (Retrieval-Augmented Generation)](../concepts/rag.md) — the alternative pattern this replaces
- [Prompt Injection](../concepts/prompt-injection.md) — risk when LLM ingests external content (relevant to Kong's security rules)

## Decisions / Actions

- Built `~/knowledge-vault/` implementing this pattern for Kong (2026-04-12)
- Chose file-based wiki over vector store — simpler, human-readable, git-versioned
- AGENTS.md is our schema file equivalent

## Open Questions

- At what scale does index.md break down and require search tooling (qmd)?
- How do we handle ingesting images / video transcripts?
- Should Kong run a weekly lint automatically via cron?

## Related Pages

- [Knowledge OS — Personal LLM Wiki](../projects/knowledge-os.md)
