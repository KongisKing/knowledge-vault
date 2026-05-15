# Building AI Agents: From Design Patterns to Production

## Source
- URL: https://docs.google.com/document/d/1keM4ZbbfVmdsq3EAkbAliIegOpnnuBf-_KpD4oDOF0o/mobilebasic
- Author: Unknown (practical field notes, not academic)
- Repo: https://github.com/agulli/atlas-agents
- Ingested: 2026-05-15

---

## Feynman Summary (ELI5)
Imagine you want to build a robot assistant that can do real work — not just answer questions, but actually search the web, write files, run code, coordinate with other robots. This book teaches you how to build that robot properly, from scratch to production. It uses one project (Atlas) across all chapters, so you see the full system grow. The core lesson: demos are easy, production is hard — and this book teaches you to cross that canyon.

---

## Core Thesis
> "The gap between a flashy demo and a trustworthy agent is a canyon. Nobody was writing about how to cross it."

Pattern-first, not framework-first. Teaches architectural thinking so knowledge doesn't expire when frameworks change.

---

## 10-Chapter Structure

### Preface — Why Agents, Why Now
- 2023: prompts → 2024: LLM chains → 2025: autonomous systems
- The book is built around **Atlas** — a research + coding assistant that grows from 50 lines to a full multi-agent system
- Model-agnostic: same agent runs on OpenAI, Gemini, Claude, Llama

### Ch 1 — Anatomy of an Agent
Core loop: **Perceive → Think → Act → Observe → Repeat**
- Every agent has: System Prompt, Memory, Tools, Loop
- The **ReAct pattern** (Reason + Act) is the foundation
- Three memory types: In-context (working), External (persistent), Episodic (past trajectories)
- Tool call = the agent's hands; observation = what comes back

### Ch 2 — Prompt Architecture for Agents
- Agent prompts ≠ chat prompts — they need: Role, Goal, Constraints, Tool guidance, Output format
- **Prompt layering:** System (identity) → User (task) → Tool results (observations)
- Prompts are code — version them, test them, don't treat them as afterthoughts
- Key failure mode: under-constrained prompts → runaway tool calls

### Ch 3 — Tools, Skills, and Structured Outputs
- Tools are functions the agent can call (web_search, file_read, code_exec)
- **Skill pattern:** Group related tools into a Skill class with `name`, `description`, `get_tools()`, `execute()`
- Three core skills: WebSkill, FileSkill, CodeSkill
- Structured outputs (Pydantic) prevent hallucinated tool calls
- **Security rule:** Never let file tools escape the base directory (path traversal attacks)

### Ch 4 — Handoffs and Routines
- **Handoff:** One agent passes control to another (with context)
- **Routine:** A fixed sequence of steps the agent follows (like a playbook)
- Handoffs enable specialization — triage agent routes to specialist agents
- Routines reduce non-determinism for well-understood tasks

### Ch 5 — Stateful Agent Graphs
- Agents need state that persists across tool calls
- **Graph model:** Nodes = agent steps, Edges = transitions, State = shared context
- LangGraph implements this pattern
- Key insight: state machines make agent behavior inspectable and debuggable

### Ch 6 — Multi-Agent Collaboration
- Patterns: Orchestrator + Workers, Peer-to-peer, Pipeline
- **Orchestrator pattern:** One agent plans, delegates to specialist sub-agents, aggregates results
- Communication via shared state or message passing
- Failure modes: infinite loops, contradictory instructions, context loss between agents
- Rule: each agent should have a single clear responsibility

### Ch 7 — Model Portability: One Agent, Many Models
- Abstract the LLM behind an interface — swap OpenAI for Claude/Gemini without rewriting agent logic
- **Provider abstraction layer:** `complete(messages, tools)` → same interface, different backends
- Why it matters: vendor outages, cost optimization, capability differences per task
- Test against multiple models — behavior diverges more than you expect

### Ch 8 — Open Protocols: MCP, A2A, A2UI, AP2
- **MCP (Model Context Protocol):** Anthropic's standard for tool/resource exposure to agents
- **A2A (Agent-to-Agent):** Protocol for agents to communicate and delegate to each other
- **A2UI:** Agent-to-UI protocol — agent drives a UI directly
- **AP2:** Agent Payment Protocol — agents transact autonomously
- These protocols are the "HTTP of the agentic web" — standardize how agents interoperate

### Ch 9 — Declarative Agent Skills
- Skills defined in Markdown/YAML (not code) — declarative, human-readable
- LLM interprets the skill definition at runtime
- Enables non-engineers to define agent capabilities
- **Direct connection to SkillOS** — this is the same pattern Kong uses with SKILL.md files

### Ch 10 — Building with Claude Code and Google Antigravity
- Production patterns: eval harnesses, guardrails, trajectory evaluation (not just final answer)
- **Trajectory evaluation:** Score the path the agent took, not just whether it got the right answer
- Guardrails: input validation, output filtering, action limits, human-in-the-loop checkpoints
- Google Antigravity = internal Google framework for production agent deployment
- When NOT to use an agent: simple deterministic tasks, latency-critical paths, high-stakes irreversible actions

---

## Key Concepts Map

### The Agent Loop
```
Perceive (input) → Think (LLM) → Act (tool call) → Observe (result) → back to Think
```

### Memory Taxonomy
- **In-context:** Current conversation window (fast, limited, ephemeral)
- **External:** Vector DB / file storage (persistent, slower, unlimited)
- **Episodic:** Past trajectories stored and retrieved (enables learning from experience)

### Skill Pattern (Ch 3 + Ch 9)
```
Skill = name + description + tools[] + execute()
Declarative Skill = SKILL.md (what Kong uses)
```

### Agent Collaboration Patterns
- **Pipeline:** A → B → C (sequential)
- **Orchestrator/Worker:** Planner delegates to specialists
- **Peer-to-peer:** Agents negotiate directly (A2A protocol)

### Production Checklist (Ch 10)
- [ ] Trajectory evaluation (not just output eval)
- [ ] Guardrails on inputs AND outputs
- [ ] Human-in-the-loop for irreversible actions
- [ ] Provider abstraction (model portability)
- [ ] Structured outputs (Pydantic)
- [ ] Action limits per session

---

## Relevance to Kong

| Book Concept | Kong Status |
|---|---|
| ReAct loop | ✅ Kong's core loop |
| Skill pattern (SKILL.md) | ✅ Already implemented |
| Declarative skills (Ch 9) | ✅ Kong's exact approach |
| Multi-agent orchestration | ✅ Subagent routing |
| MCP protocol (Ch 8) | ⚠️ Zenoti project — building this |
| Model portability (Ch 7) | ✅ Provider-prefixed model routing |
| Trajectory evaluation | ❌ Not implemented |
| SkillOS Curator (Ch 9 extension) | 🔨 Building now (Level 1) |
| Episodic memory | ⚠️ history.jsonl exists but not retrieved |

---

## Related Vault Entries
- `wiki/summaries/google-skillos-self-evolving-agents.md`
- `wiki/summaries/ai-agent-concepts-pm-guide.md`
- `wiki/summaries/karpathy-coding-guidelines.md`
- `concepts/multi-agent-architecture.md`
- `concepts/tool-chaining-pipeline.md`
- `wiki/projects/zenoti.md`
