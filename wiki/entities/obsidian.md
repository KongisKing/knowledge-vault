---
title: "Obsidian"
date: 2026-04-12
tags: [tool, knowledge-management, markdown, second-brain, graph-view]
source: "https://x.com/defileo/status/2042241063612502162"
---

## Type
Tool / Product

## Description
A local-first markdown-based knowledge management app. Notes are plain `.md` files stored on your machine — no lock-in, no cloud dependency. Known for its graph view that visualizes connections between notes.

## Role / Relevance
In the LLM Wiki pattern, Obsidian is the **viewer/IDE** — the human browses the wiki through Obsidian while the LLM (Kong) acts as the programmer maintaining it. The LLM writes and edits files; Obsidian renders them beautifully with backlinks and graph view.

## Key Features Relevant to Our Setup
- **Graph view** — visualizes which wiki pages link to which; reveals hubs and orphans at a glance
- **Obsidian Web Clipper** — browser extension that converts web articles to markdown, drops them into `raw/` for ingestion
- **Marp plugin** — renders markdown as slide decks (useful for generating presentations from wiki content)
- **Dataview plugin** — runs queries over YAML frontmatter; can generate dynamic tables from wiki metadata
- **Local storage** — wiki is just a folder of `.md` files; works perfectly with git versioning

## Do We Need It?
Not required — Kong can operate the vault entirely from the terminal/VS Code. But Obsidian adds:
- Visual graph of knowledge connections
- Fast backlink browsing
- Web Clipper for easy article ingestion into `raw/`

## Related Projects
- [Knowledge OS — Personal LLM Wiki](../projects/knowledge-os.md)

## Related Concepts
- [LLM Wiki Pattern](../concepts/llm-wiki-pattern.md)

## Mentions
- [Karpathy LLM Wiki Pattern](../summaries/karpathy-llm-wiki-pattern.md)
