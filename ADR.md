# Architecture Decision Record (ADR)

## SLE-4: Final Viva & Architecture Decision Record

**Project:** BFS and A* Search System  
**Course:** 02AML204 – Introduction to Artificial Intelligence  
**PRN:** 25UAM028  
**Name:** Aftab Momin  
**Division:** A  
**Date:** 11 October 2026

---

# ADR-001: Selection of A* as the Preferred Search Algorithm

**Status:** Accepted

**Decision Date:** 11 October 2026

## 1. Context

The project implements Breadth-First Search (BFS) and A* Search to find a path from a starting position to a goal position in a grid maze. Both algorithms were tested on the same 60 × 60 grid maze during SLE-2. The profiling results showed that BFS expanded 2,817 nodes, whereas A* expanded 1,923 nodes. Both algorithms found a path of 118 steps in the recorded experiment. These results were used to decide which algorithm should be preferred in the Search Engine designed during SLE-3.

## 2. Decision

A* Search with the Manhattan Distance heuristic is selected as the preferred search algorithm for the tested maze. It expanded fewer nodes than BFS while finding a path of the same reported length. BFS is retained as a comparison algorithm.

## 3. Alternatives Considered

### Alternative 1: Breadth-First Search (BFS)

BFS explores nodes level by level using a queue. It can find a shortest path when all movements have equal costs. However, in the recorded experiment, it expanded more nodes than A*.

**Reason for rejection:** BFS was not selected as the preferred algorithm because it explored more nodes in the tested maze.

### Alternative 2: Depth-First Search (DFS)

DFS explores one branch deeply before backtracking. It can be useful for exploring graphs, but it does not generally guarantee the shortest path.

**Reason for rejection:** It does not meet the shortest-path requirement reliably in a general maze.

### Alternative 3: Greedy Best-First Search

Greedy Best-First Search selects nodes based mainly on the estimated distance to the goal. It may reach the goal quickly, but it does not fully consider the cost already travelled.

**Reason for rejection:** A* considers both the path cost and the estimated remaining distance, making it a more suitable choice when an optimal path is required under the appropriate conditions.

## 4. Rationale / Justification

The decision is based on the profiling results obtained in SLE-2.

- BFS expanded 2,817 nodes, while A* expanded 1,923 nodes.
- A* expanded 894 fewer nodes, approximately 31.7% fewer than BFS.
- Both algorithms found a path of 118 steps in the recorded experiment.
- A* uses the evaluation function **f(n) = g(n) + h(n)**.
- Here, `g(n)` is the actual cost from the start, and `h(n)` estimates the remaining cost to the goal.
- Manhattan Distance is used as the heuristic for four-direction grid movement.
- The heuristic is calculated as `h(n) = |x − x_goal| + |y − y_goal|`.
- The SLE-3 architecture separates system responsibilities into modules such as Input, Search, Heuristic, Visited Set, Performance Analyzer, and Output.
- This modular structure supports testing, maintenance, and comparison of search algorithms.

Based on these results, A* is preferred for the tested maze. The decision is specific to the experiment and does not mean A* will always outperform BFS for every problem.

## 5. Consequences

### Positive Consequences

- Fewer nodes were expanded by A* in the recorded experiment.
- Both algorithms found paths of the same reported length.
- Manhattan Distance is simple to calculate for four-direction grid movement.
- The modular architecture makes the system easier to understand and maintain.
- The decision is supported by measured profiling results.
- BFS remains available for comparison and future testing.

### Negative Consequences / Trade-offs

- A* requires additional data structures, such as an open list or priority queue and a closed set.
- Memory usage can increase for larger search spaces.
- Performance depends on the maze layout and heuristic.
- Results from one maze may not represent performance on every maze.
- Additional profiling is required to evaluate performance on larger grids.

## 6. References

1. SLE-2 Profiling Report – BFS and A* performance comparison.
2. SLE-3 Full C4 Architecture Design – Search System.
3. Project source code and `README.md`.

---

## Decision Summary

A* Search with Manhattan Distance was selected as the preferred algorithm because it expanded fewer nodes than BFS while finding a path of the same reported length in the tested maze. The decision connects the measured performance from SLE-2 with the modular architecture developed in SLE-3. BFS remains part of the project for comparison and further evaluation.
