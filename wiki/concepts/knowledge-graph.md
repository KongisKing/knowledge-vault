---
title: "Knowledge Graph"
date: 2026-04-15
tags: [knowledge-graph, graph-database, triples, data-modeling]
source: "https://x.com/techwith_ram/status/2044032272081588395"
---

## Definition
A structured representation of knowledge as a network of entities (nodes) and relationships (edges). Every fact is stored as a **triple**: `(Subject, Predicate, Object)`.

Example: `(Chandan, WORKS_AT, Zenoti)` or `(Zenoti, IS_A, SaaS_Platform)`

## Why It Matters
- Models real-world relationships naturally
- Enables multi-hop queries: "find all funds held by CAs who advise clients with >₹1Cr portfolio"
- Powers recommendation engines, semantic search, and AI memory systems

## Key Components
- **Nodes** — entities (people, companies, products, concepts)
- **Edges** — relationships (WORKS_AT, KNOWS, PRODUCES, IS_PARTNER_OF)
- **Triples** — the atomic unit: (Subject, Predicate, Object)
- **Predicates** — the relationship types (bounded set in most systems)

## Query Model
KG queries are **subgraph matching problems** — you describe a pattern and ask the system to find all places in the graph where that pattern appears. This explodes combinatorially at scale (see [Graph Traversal](./graph-traversal.md)).

## Tools / Systems
- **Neo4j** — most popular graph DB (Cypher query language)
- **Apache Jena TDB** — RDF triple store with 6-index optimization
- **Virtuoso** — high-performance RDF/SPARQL engine
- **RDF-3X, HDT** — compressed graph storage systems

## Relevance to Kong
- Current vault: flat markdown files (not a graph DB yet)
- Future path: if vault scales to thousands of nodes, graph DB becomes necessary
- WealthOS use case: model Fund → CA → Portfolio → Investor relationships

## Related Concepts
- [Graph Traversal](./graph-traversal.md)

## Sources
- [Knowledge Graph Query Optimization](../summaries/knowledge-graph-query-optimization.md)
