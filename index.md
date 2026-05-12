# Knowledge Vault Index
_Last updated: 2026-05-12_

> Master catalog of everything in the vault. Start here when querying.
> Each row: page link | one-line description | tags | last updated.

---

## Projects

| Page | Summary | Tags | Updated |
|------|---------|------|---------|
| [Zenoti — Agentic API Strategy](wiki/projects/zenoti.md) | 3-layer agentic API strategy for Zenoti's salon platform; CPO demo milestone June 2026 | `zenoti` `agentic-api` `mcp` `product-strategy` | 2026-04-10 |
| [WealthOS — AI-Powered Wealth Management](wiki/projects/wealthos.md) | B2B SaaS for India's 800K CAs to give tax-optimized investment guidance; built on mfapi.in | `wealthos` `fintech` `india` `b2b-saas` `mutual-funds` | 2026-04-10 |
| [Knowledge OS — Personal LLM Wiki](wiki/projects/knowledge-os.md) | Personal knowledge OS inspired by Karpathy's LLM Wiki pattern; this vault | `knowledge-os` `llm-wiki` `kong` `productivity` | 2026-04-12 |
| [Kong Refinement — Closing the gstack Gap](wiki/projects/kong-refinement.md) | Active project to evolve Kong's architecture based on gstack benchmark; 18 gaps identified, 3 tracks | `kong` `gstack` `agent-architecture` `active` | 2026-05-10 |

---

## Summaries

| Page | Summary | Tags | Updated |
|------|---------|------|---------|
| [Karpathy LLM Wiki Pattern](wiki/summaries/karpathy-llm-wiki-pattern.md) | Compounding wiki pattern where LLM maintains persistent interlinked knowledge instead of re-deriving via RAG | `llm-wiki` `knowledge-management` `second-brain` | 2026-04-12 |
| [Karpathy Coding Guidelines for LLMs](wiki/summaries/karpathy-coding-guidelines.md) | Four principles to fix LLM coding pitfalls: Think Before Coding, Simplicity First, Surgical Changes, Goal-Driven Execution | `coding-guidelines` `vibe-coding` `karpathy` | 2026-04-12 |
| [Your Harness, Your Memory](wiki/summaries/harrison-chase-your-harness-your-memory.md) | Memory is inseparable from the agent harness; closed harnesses = memory lock-in; own your memory layer | `agent-harness` `memory` `lock-in` `langchain` | 2026-04-12 |
| [Knowledge Graph Query Optimization](wiki/summaries/knowledge-graph-query-optimization.md) | How to make KG queries fast at scale — SPO indexes, bitmap indexes, BFS/DFS/Dijkstra/A* traversal | `knowledge-graph` `query-optimization` `algorithms` | 2026-04-15 |
| [Kong vs gstack Gap Analysis](wiki/summaries/kong-vs-gstack-gap-analysis.md) | 18-gap benchmark of Kong vs gstack v1.30.0.0; Kong wins on routing/personalization; gstack wins on role breadth/pipelines | `kong` `gstack` `gap-analysis` `agent-architecture` | 2026-05-10 |
| [AI Agent Concepts — PM's Guide](wiki/summaries/ai-agent-concepts-pm-guide.md) | 30 AI/agent engineering concepts explained for PMs — 5YO + PM mode with nuances and real-world examples | `ai-agents` `pm-guide` `llm` `rag` `multi-agent` `reference` | 2026-05-12 |

---

## Entities

| Page | Summary | Tags | Updated |
|------|---------|------|---------|
| [Andrej Karpathy](wiki/entities/andrej-karpathy.md) | AI researcher, co-founder of OpenAI, author of the LLM Wiki pattern and coding guidelines | `person` `ai-researcher` | 2026-04-12 |
| [Harrison Chase](wiki/entities/harrison-chase.md) | LangChain founder; author of "Your Harness, Your Memory" | `person` `langchain` `agent-harness` | 2026-04-12 |
| [Obsidian](wiki/entities/obsidian.md) | Local-first markdown knowledge tool; the viewer/IDE in the LLM Wiki pattern | `tool` `knowledge-management` `markdown` | 2026-04-12 |
| [gstack](wiki/entities/gstack.md) | Garry Tan's Claude Code multi-agent setup; 23 specialist roles, gbrain memory, ML security classifier | `tool` `agent-architecture` `claude-code` | 2026-05-10 |
| [Garry Tan](wiki/entities/garry-tan.md) | President & CEO of YC; author of gstack; deeply technical founder-mode operator | `person` `yc` `investor` | 2026-05-10 |
| [nanobot](wiki/entities/nanobot.md) | Agent harness powering Kong; v0.1.5; manages tools, subagents, Dream memory, Telegram | `tool` `agent-harness` `kong` | 2026-05-10 |

---

## Concepts

| Page | Summary | Tags | Updated |
|------|---------|------|---------|
| [LLM Wiki Pattern](wiki/concepts/llm-wiki-pattern.md) | Pattern for building persistent compounding knowledge bases maintained by LLMs | `knowledge-management` `llm` `pattern` | 2026-04-12 |
| [Surgical Changes](wiki/concepts/surgical-changes.md) | Touch only what the request requires; every changed line must trace to the user's ask | `coding-discipline` `vibe-coding` | 2026-04-12 |
| [Think Before Coding](wiki/concepts/think-before-coding.md) | State assumptions, surface ambiguity, present tradeoffs before writing any code | `coding-discipline` `vibe-coding` | 2026-04-12 |
| [Goal-Driven Execution](wiki/concepts/goal-driven-execution.md) | Define verifiable success criteria first; test-first loop for bugs | `coding-discipline` `tdd` `vibe-coding` | 2026-04-12 |
| [Simplicity First](wiki/concepts/simplicity-first.md) | Minimum code that solves today's problem; no speculative features or premature abstraction | `coding-discipline` `yagni` `vibe-coding` | 2026-04-12 |
| [Agent Harness](wiki/concepts/agent-harness.md) | Scaffolding around an LLM that manages tools, context, and memory — inseparable from memory | `agent` `scaffolding` `memory` | 2026-04-12 |
| [Agent Memory](wiki/concepts/agent-memory.md) | Short and long-term memory managed by the harness; the real moat in agentic AI | `memory` `agent` `personalization` | 2026-04-12 |
| [Vendor Lock-in](wiki/concepts/vendor-lock-in.md) | Losing portability when memory/state lives inside a provider's closed platform | `lock-in` `portability` `strategy` | 2026-04-12 |
| [Data Flywheel](wiki/concepts/data-flywheel.md) | Compounding competitive advantage from accumulated user interaction data | `flywheel` `moat` `data` | 2026-04-12 |
| [Multi-Agent Architecture](wiki/concepts/multi-agent-architecture.md) | Orchestrator + specialist subagents; role vs model specialization; Kong vs gstack comparison | `multi-agent` `subagent` `orchestration` | 2026-05-10 |
| [Tool-Chaining Pipeline](wiki/concepts/tool-chaining-pipeline.md) | Formalized skill sequences with artifact handoffs; gstack's `/design→/plan→/code→/qa→/ship` | `pipeline` `tool-chaining` `workflow` | 2026-05-10 |
| [Subagent Skill-Reading Rule](wiki/concepts/subagent-skill-reading-rule.md) | Skill files only in Coder prompts; Analyst/Researcher/Writer must stay lean — root cause of May 2026 failures | `subagent` `prompt-discipline` `kong-rule` | 2026-05-10 |
| [Knowledge Graph](wiki/concepts/knowledge-graph.md) | Entities + relationships as triples (S,P,O); foundation for graph DBs and semantic querying | `knowledge-graph` `graph-db` `triples` | 2026-04-15 |
| [Graph Traversal](wiki/concepts/graph-traversal.md) | BFS, DFS, Dijkstra, A* — algorithms for navigating graphs; combinatorial explosion at scale | `graph-traversal` `BFS` `DFS` `algorithms` | 2026-04-15 |

---

_To add entries: run the INGEST workflow (see AGENTS.md). Kong will update this index automatically._
