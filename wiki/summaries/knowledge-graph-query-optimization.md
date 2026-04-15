---
title: "How to Make Knowledge Graphs Blazing Fast"
date: 2026-04-14
tags: [knowledge-graph, query-optimization, indexing, graph-traversal, algorithms, data-engineering]
source: "https://x.com/techwith_ram/status/2044032272081588395"
author: "@techwith_ram (Ramakrishna)"
relevance: "Future — relevant when knowledge vault scales to thousands of nodes or WealthOS models fund/portfolio relationships"
---

## One-Line Summary
KG queries are subgraph matching problems — they explode combinatorially at scale. The fix is layered: right indexes first, then smart traversal algorithms.

## The Core Problem
Every fact in a knowledge graph is a **triple**: `(Subject, Predicate, Object)`
- e.g. `(Chandan, WORKS_AT, Zenoti)`

A query is a pattern match — find all subgraphs where the pattern appears.

**The explosion problem:**
- Each node has ~50 neighbours on average
- 4-hop query = 50⁴ = **6.25 million** candidate paths
- 6-hop query = 50⁶ = **15.6 billion** candidate paths
- Brute force simply doesn't scale

---

## Optimization Layer 1: Indexes

### Six SPO Indexes (most impactful)
Standard in Apache Jena TDB and Virtuoso. For every triple, maintain 6 sorted B-tree indexes:
```
SPO, SOP, PSO, POS, OSP, OPS
```
- Turns O(n) full scans → O(log n + k) lookups
- Cost: 6x storage. Benefit: any lookup pattern served instantly
- Example: query `(?x BORN_IN Warsaw)` → use POS index, binary search to (BORN_IN, Warsaw)

### Bitmap Indexes
- Each predicate gets a bitmap (bit i = 1 if node i has that predicate)
- Multi-predicate filter = bitwise AND — single CPU operation
- Modern CPUs process 64 bits at a time via SIMD instructions
- Best for bounded predicate sets (~200 relationship types)

### Adjacency Lists
- Per node, store neighbours grouped by edge type
- Following `KNOWS` edge from node X = just read X's KNOWS adjacency list
- Compression: delta encoding + variable-length integers → 5-10x compression (RDF-3X, HDT)

---

## Optimization Layer 2: Traversal Algorithms

### BFS (Breadth-First Search)
- Best for: shortest path, fixed-hop queries
- Explores layer by layer (distance 1, then 2, etc.)
- In KGs: filter by edge type to reduce fan-out dramatically
- Downside: high memory (stores entire frontier)

### DFS (Depth-First Search)
- Best for: deep path exploration, bounded depth queries
- Follows one path to the end before backtracking
- Low memory (only stores current path)
- **Critical:** always use `max_depth` parameter — without it, DFS disappears down infinite chains
- Most KG queries are bounded: "find paths of length at most 5"

### Weighted traversal (Dijkstra / A*)
- When edges carry weights/costs
- Dijkstra: shortest weighted path
- A*: adds heuristic to guide search toward target faster

---

## When to Use What

| Scenario | Algorithm |
|---|---|
| Shortest path between 2 nodes | BFS |
| All nodes within N hops | BFS |
| Deep chain exploration | DFS with max_depth |
| Weighted shortest path | Dijkstra |
| Directed search toward known target | A* |
| Multi-predicate filter | Bitmap index |
| Any triple lookup pattern | SPO 6-index |

---

## Relevance to Our Setup

### Now: Not needed
- Knowledge vault = flat markdown files + grep
- Tens of files, not millions of nodes
- Kong queries via grep, not graph traversal

### Future: Highly relevant when
1. **Knowledge vault scales** to thousands of entries → graph-style querying becomes necessary
2. **WealthOS** models relationships: Fund → CA → Portfolio → Investor (multi-hop queries)
3. **Vault evolution**: flat files → Neo4j or similar graph DB

### Key takeaway for future vault design
If we ever move to a graph-based vault, **start with indexes before writing a single traversal query**. Indexes are "boring, unglamorous work" but the single most impactful optimization.

---

## Related Concepts
- [Knowledge Graph](../concepts/knowledge-graph.md)
- [Graph Traversal](../concepts/graph-traversal.md)

## Related Projects
- [Knowledge OS](../projects/knowledge-os.md)
- [WealthOS](../projects/wealthos.md)
