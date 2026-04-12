# 🧠 Knowledge Vault

A personal knowledge OS built on the LLM Wiki pattern (inspired by Andrej Karpathy). Instead of a flat memory blob, this is a **persistent, compounding wiki** that Kong (the LLM) incrementally maintains over time.

Every article you read, every decision you make, every project you run — ingested once, cross-linked forever, queryable always.

---

## How It Works

Kong maintains this vault through three operations: **Ingest**, **Query**, and **Lint**. The full schema and workflow instructions for Kong are in [`AGENTS.md`](./AGENTS.md).

```
You drop a source → Kong reads it → extracts ideas, entities, concepts
                  → writes wiki pages → updates the index → logs the operation
                  → everything is cross-linked and searchable
```

---

## Directory Structure

```
knowledge-vault/
  raw/                  # Drop source files here (articles, notes, PDFs)
                        # These are IMMUTABLE — never edited after drop
  wiki/
    summaries/          # One page per ingested source
    entities/           # People, companies, products, tools
    concepts/           # Ideas, frameworks, mental models, patterns
    projects/           # Active and past projects
  index.md              # Master catalog of everything in the vault
  log.md                # Append-only history of every operation
  AGENTS.md             # Kong's operating manual (schema + workflows)
  README.md             # This file
```

---

## The 3 Operations

### 🔽 INGEST
**When:** You have a new source — article, URL, note, conversation transcript.

**How to trigger:** Say to Kong:
> "Ingest this: [paste content or file path]"

**What Kong does:**
1. Reads the source fully
2. Extracts key ideas, entities, concepts, decisions, open questions
3. Writes a summary page to `wiki/summaries/`
4. Creates/updates entity pages in `wiki/entities/`
5. Creates/updates concept pages in `wiki/concepts/`
6. Adds a row to `index.md`
7. Appends an entry to `log.md`
8. Reports every file touched

---

### 🔍 QUERY
**When:** You want to know something that might be in the vault.

**How to trigger:** Just ask Kong a question. Or say:
> "Query the vault: what do we know about [topic]?"

**What Kong does:**
1. Reads `index.md` to find relevant pages
2. Reads those pages
3. Synthesizes an answer with citations (links to wiki pages)
4. Offers to file the synthesized answer as a new wiki page if it's valuable

---

### 🧹 LINT
**When:** Periodically (monthly, or when the vault feels stale).

**How to trigger:**
> "Lint the vault"

**What Kong does:**
1. Scans all wiki pages
2. Checks for: contradictions, stale claims, orphan pages, missing cross-references, concept gaps
3. Reports findings as a checklist
4. Suggests new sources to fill gaps
5. Logs the lint operation

---

## How to Add a New Source

1. **Option A — Drop and ingest:** Copy the file into `raw/`, then tell Kong:
   > "Ingest raw/my-article.md"

2. **Option B — Paste and ingest:** Paste content directly to Kong:
   > "Ingest this article: [paste text]"

3. **Option C — URL ingest:** Give Kong a URL:
   > "Ingest this URL: https://..."

Kong will handle the rest.

---

## Index & Log

- **`index.md`** — The master catalog. Every wiki page has a row here with a one-line description, tags, and last-updated date. Start here when querying.

- **`log.md`** — The append-only history. Every ingest, query, and lint operation is logged. Useful for understanding what changed and when.

---

## Design Principles

- **No RAG, no embeddings** — at personal scale, `index.md` + reading relevant pages is enough. Keep it simple.
- **Compounding value** — each ingest makes the vault more connected and useful. Cross-links are the key.
- **Immutable sources** — `raw/` is never edited. The wiki is the processed, structured view.
- **Kong as the engine** — Kong reads AGENTS.md to understand the schema and follows the workflows. The vault is designed to be operated by an LLM, not just read by one.

---

## Current Vault Contents

See [`index.md`](./index.md) for the live catalog.

---

*Built with the LLM Wiki pattern. Maintained by Kong.*
