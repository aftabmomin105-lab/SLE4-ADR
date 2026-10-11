# SLE4-ADR
# BFS and A* Search System

## 1. Project Overview

This project implements and compares two Artificial Intelligence search algorithms: Breadth-First Search (BFS) and A* Search. The system is designed to find a path from a starting position to a goal position in a grid maze.

BFS explores nodes level by level, whereas A* uses the actual path cost and a heuristic estimate to guide the search toward the goal. The project compares their performance using profiling results.

## 2. Objectives

- To understand and implement BFS and A* Search algorithms.
- To find a path between the starting position and the goal.
- To understand heuristic-based search in Artificial Intelligence.
- To compare the performance of BFS and A* Search.
- To analyze the number of nodes expanded and the resulting path length.
- To design a modular system using the C4 architecture model.

## 3. Algorithms Used

### Breadth-First Search (BFS)

BFS explores neighbouring nodes level by level using a queue. For an unweighted grid with equal movement costs, BFS can find a shortest path.

### A* Search

A* selects nodes using the evaluation function:

**f(n) = g(n) + h(n)**

Where:
- **g(n):** Actual cost from the starting position to the current node.
- **h(n):** Estimated cost from the current node to the goal.
- **f(n):** Estimated total cost of the path through the current node.

### Manhattan Distance Heuristic

For four-direction grid movement, Manhattan Distance is calculated as:

**h(n) = |x − x_goal| + |y − y_goal|**

This estimates the remaining distance to the goal without considering diagonal movement.

## 4. Technologies Used

- Programming Language: Python
- Search Algorithms: BFS and A*
- Profiling: Execution and node-expansion analysis
- Architecture: C4 Model
- Documentation: Markdown

## 5. System Workflow

1. Initialize the grid maze.
2. Define the starting and goal positions.
3. Select the search algorithm.
4. Explore neighbouring positions while avoiding invalid or blocked cells.
5. Continue searching until the goal is reached or no path is available.
6. Reconstruct the path if the goal is reached.
7. Record the search results and profiling information.
8. Compare the performance of BFS and A*.

## 6. Profiling Results

The following results were recorded during the SLE-2 experiment on a 60 × 60 grid maze.

| Measurement | BFS | A* Search |
|---|---:|---:|
| Nodes expanded | 2,817 | 1,923 |
| Path length | 118 steps | 118 steps |

In this experiment, A* expanded 894 fewer nodes than BFS, approximately 31.7% fewer. Both algorithms found a path of the same reported length.

These results apply to the tested maze and experimental conditions; they do not guarantee that A* will always outperform BFS on every problem.

## 7. Advantages

- Demonstrates two important AI search algorithms.
- Shows the difference between uninformed and heuristic-based search.
- Allows performance comparison using recorded measurements.
- Uses Manhattan Distance for informed search on a four-direction grid.
- Supports modular implementation and architecture documentation.

## 8. Limitations

- Performance depends on the maze structure and size.
- A* can require additional memory for its open list and visited or closed nodes.
- Manhattan Distance is intended for the stated four-direction movement model.
- The recorded profiling results are specific to the tested maze.

## 9. Project Structure

The exact filenames may vary depending on the implementation.

```text
BFS-A-Star-Search/
├── main.py
├── README.md
├── CONTRIBUTION_LOG.md
├── SLE-2-Profiling-Report.pdf
└── SLE-3-C4-Architecture/
    ├── Context-Diagram
    ├── Container-Diagram
    ├── Component-Diagram
    └── Code-Diagram
```

## 10. Learning Outcomes

Through this project, I learned how BFS and A* explore a search space, how heuristics guide informed search, and how profiling can be used to compare algorithms. I also learned how to document architectural decisions using the C4 model and an Architecture Decision Record (ADR).

## 11. Conclusion

This project demonstrates the implementation and comparison of BFS and A* Search for maze path-finding. In the recorded experiment, A* expanded fewer nodes while finding a path of the same length as BFS. The project helped connect AI search concepts with performance analysis, software architecture, and technical documentation.
