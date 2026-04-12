# AGENTS.md — Knowledge Vault Schema & Workflows

> This file tells Kong (the LLM) how the knowledge vault is structured and exactly how to operate on it.
> Follow these workflows precisely and consistently on every operation.

---

## 📁 Vault Structure

```
~/knowledge-vault/
  raw/                  # Immutable source docs. User drops files here. NEVER modify.
  wiki/
    summaries/          # One page per ingested source (article, URL, note)
    entities/           # People, companies, products — one page per entity
    concepts/           # Ideas, frameworks, mental models — one page per concept
    projects/           # Active or past projects — one page per project
  index.md              # Master catalog: every wiki page, one-line summary, link
  log.md                # Append-only operation log: ingest / query / lint entries
  AGENTS.md             # THIS FILE — schema + workflows
  README.md             # Human-readable overview
```

---

## 📄 Page Format (All Wiki Pages)

Every wiki page MUST start with YAML frontmatter:

```yaml
---
title: "Page Title"
date: YYYY-MM-DD
tags: [tag1, tag2, tag3]
source: "URL or file path of original source"
---
```

Followed by structured markdown content appropriate to the page type (see per-type guidance below).

### Summary pages (`wiki/summaries/[slug].md`)
- **Key Ideas** — 3–7 bullet points of the most important ideas
- **Entities Mentioned** — list of people, companies, products (link to entity pages)
- **Concepts Mentioned** — list of ideas/frameworks (link to concept pages)
- **Decisions / Actions** — any decisions made or actions to take
- **Open Questions** — unresolved questions raised by the source
- **Related Pages** — links to related wiki pages

### Entity pages (`wiki/entities/[slug].md`)
- **Type** — Person | Company | Product | Tool
- **Description** — 1–3 sentence summary
- **Role / Relevance** — why this entity matters in our context
- **Related Projects** — links to project pages
- **Related Concepts** — links to concept pages
- **Mentions** — links back to summary pages where this entity appears

### Concept pages (`wiki/concepts/[slug].md`)
- **Definition** — clear 1–3 sentence definition
- **Why It Matters** — relevance to our work
- **Examples** — concrete examples or applications
- **Related Concepts** — links to related concept pages
- **Sources** — links to summary pages where this concept appears

### Project pages (`wiki/projects/[slug].md`)
- **Status** — Active | Paused | Complete | Research
- **Summary** — 2–4 sentence overview
- **Key Decisions** — major decisions made
- **Next Actions** — what needs to happen next
- **Open Questions** — unresolved questions
- **Related Entities** — links to entity pages
- **Related Concepts** — links to concept pages
- **Sources** — links to summary or raw pages

---

## 🔄 Workflow 1: INGEST

**Trigger:** User says "ingest [file/URL]" or drops a file in `raw/`

**Steps — follow in order, do not skip:**

1. **Read** the source file or URL content fully.

2. **Extract** from the source:
   - Key ideas (what are the main points?)
   - Entities (people, companies, products mentioned)
   - Concepts (ideas, frameworks, patterns referenced)
   - Decisions (any choices made or recommended)
   - Open questions (unresolved issues)

3. **Write summary page** to `wiki/summaries/[slug].md`
   - Slug = kebab-case title (e.g., `zenoti-agentic-api-strategy`)
   - Use the standard frontmatter + Summary page format above

4. **Update or create entity pages** for each entity extracted:
   - If `wiki/entities/[entity-slug].md` exists → add new mentions, update if facts changed
   - If it doesn't exist → create it using the Entity page format

5. **Update or create concept pages** for each concept extracted:
   - If `wiki/concepts/[concept-slug].md` exists → add new sources, update if needed
   - If it doesn't exist → create it using the Concept page format

6. **Update `index.md`** — add a row to the appropriate table section:
   - Format: `| [Page Title](wiki/...) | One-line description | tags | YYYY-MM-DD |`
   - Update the `_Last updated:` date at the top

7. **Append to `log.md`**:
   ```
   ## [YYYY-MM-DD HH:MM] ingest | [Source Title]
   
   - Created: wiki/summaries/[slug].md
   - Updated: index.md
   - Entity pages touched: [list]
   - Concept pages touched: [list]
   ```

8. **Report** — list every file created or modified, with a one-line description of what changed.

**Quality checks before finishing:**
- [ ] Every entity mentioned in the summary has a link to its entity page
- [ ] Every concept mentioned has a link to its concept page
- [ ] index.md row added
- [ ] log.md entry appended
- [ ] Frontmatter is valid YAML

---

## 🔍 Workflow 2: QUERY

**Trigger:** User asks a question about anything in the vault

**Steps — follow in order:**

1. **Read `index.md`** — scan all page titles and one-line summaries to identify which pages are relevant to the question.

2. **Read relevant pages** — pull the 2–5 most relevant wiki pages in full.

3. **Synthesize answer** — write a clear, direct answer that:
   - Cites specific wiki pages (use markdown links)
   - Distinguishes what is known (in the wiki) vs. inferred
   - Notes if any information appears contradictory between pages

4. **Offer to file** — if the synthesized answer is itself a valuable new piece of knowledge (a decision, a comparison, a new insight), offer:
   > "This answer synthesizes new insight. Want me to file it as a new wiki page?"

**Quality checks:**
- [ ] Every claim is backed by a citation to a wiki page
- [ ] Contradictions between pages are surfaced, not hidden
- [ ] The answer distinguishes facts (in wiki) from inference

---

## 🧹 Workflow 3: LINT

**Trigger:** User says "lint the vault" or on a scheduled basis

**Steps — follow in order:**

1. **Scan all wiki pages** — read every file under `wiki/`

2. **Check for these issues** and compile a checklist:

   **Contradictions**
   - [ ] Do any two pages make conflicting factual claims?

   **Stale claims**
   - [ ] Are there pages with dates older than 90 days that reference "upcoming" or "next" events?
   - [ ] Are there "Next Actions" that are likely completed based on other pages?

   **Orphan pages**
   - [ ] Are there pages in `wiki/` that are not linked from `index.md`?
   - [ ] Are there pages with no inbound links from other wiki pages?

   **Missing cross-references**
   - [ ] Does page A mention entity X but not link to `wiki/entities/x.md`?
   - [ ] Does page A mention concept Y but not link to `wiki/concepts/y.md`?

   **Concept gaps**
   - [ ] Are there concepts mentioned across multiple pages that don't have their own concept page?

3. **Report findings** as a numbered checklist with file:line references where possible.

4. **Suggest sources** — for each identified gap, suggest what type of source would fill it:
   > "Concept 'MCP (Model Context Protocol)' is mentioned in 3 pages but has no concept page. Suggest: create `wiki/concepts/mcp.md` or ingest the Anthropic MCP docs."

5. **Append to `log.md`**:
   ```
   ## [YYYY-MM-DD HH:MM] lint | vault health check
   
   - Pages scanned: N
   - Issues found: N
   - [summary of top issues]
   ```

---

## 📏 Naming Conventions

| Item | Convention | Example |
|------|-----------|---------|
| File slugs | kebab-case | `zenoti-agentic-api.md` |
| Tags | lowercase, hyphenated | `api-strategy`, `b2b-saas` |
| Entity slugs | kebab-case full name | `andrej-karpathy.md` |
| Concept slugs | kebab-case concept name | `model-context-protocol.md` |
| Log timestamps | `YYYY-MM-DD HH:MM` (IST) | `2026-04-12 10:53` |

---

## ⚠️ Rules Kong Must Always Follow

- **NEVER** modify files in `raw/` — they are immutable sources
- **ALWAYS** update `index.md` and `log.md` on every INGEST
- **ALWAYS** use YAML frontmatter on every wiki page
- **ALWAYS** link entities and concepts — no orphan references
- **NEVER** delete existing log entries — `log.md` is append-only
- **PREFER** updating existing pages over creating duplicates
- When in doubt about where a page belongs, prefer creating it and noting the uncertainty in the page itself
