# Google SkillOS — Self-Evolving Agents via Skill Curation

## Source
- URL: https://x.com/neural_avb/status/2053873358853591435
- Author: AVB (@neural_avb) — written with GPT-5.5 inside Paper Breakdown harness
- Original paper: Google Research — "Skill Curation for Self-Evolving Agents"
- Ingested: 2026-05-12

---

## Feynman Summary (ELI5)
Imagine a student (the Agent Executor) who tries to solve problems using a notebook full of tips (the SkillRepo). After each attempt, a teacher (the Skill Curator) watches what the student did, figures out what worked or failed, and rewrites the notebook to make future attempts better. The teacher is trained using reinforcement learning — it gets rewarded when its notebook updates lead to the student succeeding.

SkillOS automates the loop: **Experience → Memory → Skill**, so agents get smarter over time without retraining the base model.

---

## What Is SkillOS?
A framework by Google Research for LLM agents to **automatically evolve their own skill library** through exploration and RL-trained curation.

Core insight: You don't need to retrain the agent's weights. You just need to give it better instructions (skills) over time.

---

## Three Components

### 1. Agent Executor (Frozen)
- The "actor" LLM that solves tasks
- Retrieves relevant skills from the SkillRepo using **BM25 keyword matching** on YAML descriptions
- Weights are never updated — performance improves purely through better skills
- Produces a **trajectory**: sequence of observations and actions

### 2. Skill Curator (Trainable)
- Watches the Executor's trajectories + success/failure signal
- Decides how to update the SkillRepo via three operations:
  - `new_skill_insert` — create a new skill from a generalizable pattern
  - `skill_update` — refine or rename an existing skill
  - `skill_delete` — remove redundant or misleading skills
- Operates as a **ReAct agent** (Reason + Act loop)
- Trained via **RL** — rewarded when its skill updates lead to future task success

### 3. SkillRepo
- A directory of structured **Markdown files**
- Each skill has:
  - YAML frontmatter: `name` + `description` (used for BM25 retrieval)
  - Markdown body: Workflow steps, "When NOT to use", examples, edge cases
- Skills must be: **atomic, modular, actionable, no hallucination, no specifics** (variables over hardcoded values)

---

## The Training Loop
1. Executor attempts task → produces trajectory
2. LLM-as-Judge (Qwen3-32B) scores success/failure
3. Curator receives: task + past skills + trajectory + result
4. Curator generates skill operations (insert/update/delete)
5. Curator is rewarded if updated skills help future tasks succeed
6. Repeat → SkillRepo improves over time

---

## Skill File Format
```yaml
---
name: <human-readable skill name>
description: <one-sentence what/when/why/how — must be concise for BM25 retrieval>
---

## Workflow
Step-by-step instructions...

## When NOT to use
Negative conditions to avoid misapplication...
```

The `description` field is **critical** — it's what BM25 uses to match tasks to skills at retrieval time.

---

## Key Insights for Kong / Chandan

- **Kong's SKILL.md system is already the Anthropic skills architecture** that SkillOS builds on — Kong is architecturally ahead of most agents here
- **The missing piece in Kong:** an automated Curator loop — Kong's `auto-skill-learning` skill approximates this but is heuristic, not RL-trained
- **BM25 retrieval** is simpler than vector search for skill matching — worth noting that Kong's skill loading is currently list-based (all headers in system prompt), not retrieval-based
- **Executor stays frozen** — the key insight is that you can improve agent performance dramatically without touching model weights; better skills = better output
- **RL for skill quality** — the Curator is trained to write skills that *actually improve task success*, not just skills that look good

---

## Relevance to Kong Architecture
| SkillOS Component | Kong Equivalent | Gap |
|---|---|---|
| SkillRepo (Markdown files) | `~/.nanobot/workspace/skills/` | ✅ Already exists |
| Skill headers in system prompt | Dream loads skill list at startup | ✅ Already exists |
| Lazy skill loading (file-read) | `read_file` on SKILL.md | ✅ Already exists |
| Skill Curator (auto-evolve) | `auto-skill-learning` skill (heuristic) | ⚠️ Heuristic only, not RL-trained |
| BM25 retrieval | Not implemented — all skills listed | ❌ Gap: as skills grow, retrieval needed |
| LLM-as-Judge | Not implemented | ❌ Gap: no automated quality signal |

---

## Related Vault Entries
- `concepts/multi-agent-architecture.md`
- `concepts/subagent-skill-reading-rule.md`
- `wiki/summaries/ai-agent-concepts-pm-guide.md`
- `wiki/projects/kong-refinement.md`
