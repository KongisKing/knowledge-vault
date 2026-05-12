# AI Agent Concepts — PM's Guide (30 Concepts)

## Source
- Self-created explainer: `/Users/echandan7/.agent/explainers/ai-agent-concepts-v2.html`
- Format: Interactive HTML — 5-Year-Old Mode + PM Mode with Deep Dive modals
- Created: 2026-05-12

## What This Is
A structured reference of 30 AI/agent engineering concepts explained at two levels:
- **5-Year-Old Mode** — intuitive analogy
- **PM Mode** — why it matters for product decisions, with nuances and real-world examples

Built to help Chandan have credible technical conversations with engineers and make better AI product decisions.

---

## Concepts by Category

### 🔵 Foundation (1–4)
1. **Python Programming Fundamentals** — Default language of AI; ecosystem > speed. Scripts ≠ production services.
2. **APIs & HTTP Requests** — How systems talk. Rate limits, reliability, versioning — all PM-relevant.
3. **Prompt Engineering Techniques** — Highest-leverage, lowest-cost quality lever. Prompts are fragile; version them.
4. **Large Language Models (LLMs) Fundamentals** — Predict next word at scale. Hallucinate by design. Smaller models often win on specific tasks.

### 🟣 Core Stack (5–10)
5. **AI Agent Architectures** — Goal → steps → actions → check → repeat. Non-deterministic; error compounds over steps.
6. **Retrieval-Augmented Generation (RAG)** — Give LLMs fresh/private knowledge at query time. Quality depends on retrieval quality.
7. **Vector Databases** — Store embeddings for semantic search. Not a replacement for traditional DBs; used alongside them.
8. **Embeddings & Semantic Search** — Numbers that capture meaning. Powers "find similar" features. Expensive to generate; cache them.
9. **Memory Management in AI Agents** — Short-term (context window) vs long-term (external storage). Context window is finite and costly.
10. **Function Calling & Tool Usage** — LLMs can trigger real actions (APIs, DBs, code). Each tool call is a potential failure point.

### 🔶 Multi-Agent (11–15)
11. **Multi-Agent Systems** — Specialized agents collaborate. Coordination overhead is real; more agents ≠ better results.
12. **Autonomous Workflows & Planning** — Agents that plan and execute multi-step tasks. Requires human checkpoints for high-stakes actions.
13. **LangChain & Agent Frameworks** — Abstractions for building agents faster. Can hide complexity that matters in production.
14. **OpenAI API & AI SDKs** — Standard interfaces to LLMs. Model updates can silently change behavior — pin versions in production.
15. **AI Model Fine-Tuning Basics** — Customize a base model on your data. Expensive; try prompting + RAG first.

### ⚙️ Infrastructure (16–24)
16. **Event-Driven Agent Systems** — Agents triggered by events (webhooks, queues). Enables async, scalable workflows.
17. **Async Programming for AI Agents** — Handle multiple tasks concurrently. Critical for responsive AI products at scale.
18. **Agent Security & Guardrails** — Prevent prompt injection, data leaks, runaway actions. Security is not optional for agentic systems.
19. **Context Window Optimization** — Fit the right info in limited context. Chunking, summarization, and retrieval are key techniques.
20. **AI Cost Optimization & Token Management** — Every token costs money. Caching, model selection, and prompt efficiency drive unit economics.
21. **AI Observability & Logging** — Trace what agents did and why. Essential for debugging and trust-building with users.
22. **Agent Evaluation & Benchmarking** — Measure agent quality systematically. Hard because outputs are non-deterministic.
23. **Databases for AI Applications** — Hybrid storage: vector + relational + document. Choose based on query patterns.
24. **AI Code Development for AI Agents** — LLMs writing code for agents. Output must always be reviewed; treat as junior dev output.

### 🔴 Ops & Safety (25–30)
25. **Real-Time Communication** — WebSockets, SSE for streaming AI responses. Users expect streaming; polling feels broken.
26. **CI/CD for AI Applications** — Automated testing and deployment pipelines for AI. Harder than traditional CI/CD due to non-determinism.
27. **Docker & Kubernetes for AI Systems** — Containerize and scale AI workloads. GPU scheduling adds complexity vs. standard apps.
28. **LangChain & Agent Frameworks (Advanced Orchestration)** — Advanced patterns: parallel agents, conditional branching, state machines.
29. **Deployment & Scaling of AI Agents** — Production concerns: latency, cost, reliability at scale. Stateless design preferred.
30. **AI Agent Testing & Quality Assurance** — Structured testing before every change. Prevents regressions; builds user trust.

---

## Key PM Takeaways
- **Hallucination is a feature of how LLMs work** — not a bug to be fixed. Design guardrails around it.
- **Agents compound errors** — a 10-step agent at 90% accuracy per step = 35% end-to-end success rate.
- **Try prompting → RAG → fine-tuning** in that order before reaching for expensive solutions.
- **Every tool call is a failure point** — design for graceful degradation.
- **Token cost = unit economics** — track it from day one.
- **Observability is non-negotiable** for agentic systems — you need to know what your agent did.

---

## Related Vault Entries
- `concepts/multi-agent-architecture.md`
- `concepts/tool-chaining-pipeline.md`
- `concepts/subagent-skill-reading-rule.md`
- `wiki/summaries/karpathy-coding-guidelines.md`
