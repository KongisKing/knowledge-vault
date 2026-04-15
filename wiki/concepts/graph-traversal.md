---
title: "Graph Traversal"
date: 2026-04-15
tags: [graph-traversal, BFS, DFS, algorithms, knowledge-graph, pathfinding]
source: "https://x.com/techwith_ram/status/2044032272081588395"
---

## Definition
The process of visiting nodes and edges in a graph to answer a query — finding paths, matching patterns, or exploring relationships.

## The Explosion Problem
With avg 50 neighbours per node:
- 4-hop query = 50⁴ = **6.25 million** paths to check
- 6-hop query = 50⁶ = **15.6 billion** paths to check

Brute force doesn't scale. You need the right algorithm + indexes.

## Key Algorithms

### BFS — Breadth-First Search
- Explores layer by layer (all nodes at distance 1, then 2, etc.)
- **Best for:** shortest path, all nodes within N hops
- **Downside:** high memory — stores entire frontier
- **KG tip:** filter by edge type to dramatically reduce fan-out

### DFS — Depth-First Search
- Follows one path all the way before backtracking
- **Best for:** deep chain exploration
- **Low memory** — only stores current path
- **Critical rule:** always set `max_depth` — without it, DFS can run forever
- Most KG queries bounded at depth 5

### Dijkstra
- Shortest path when edges have weights/costs
- Processes lowest-cost node first

### A* (A-Star)
- Dijkstra + heuristic to guide search toward target
- Faster than Dijkstra when you know roughly where the target is

## When to Use What

| Goal | Algorithm |
|---|---|
| Shortest path | BFS (unweighted) / Dijkstra (weighted) |
| All nodes within N hops | BFS |
| Deep chain, bounded depth | DFS |
| Directed search to known target | A* |

## Related Concepts
- [Knowledge Graph](./knowledge-graph.md)

## Sources
- [Knowledge Graph Query Optimization](../summaries/knowledge-graph-query-optimization.md)
