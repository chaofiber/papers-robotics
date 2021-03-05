## Rapidly-Exploring Random Trees: A New Tool for Path Planning

### Steven M.Lavalle

### 5.3.2021

### Summary

- This paper introduces RRT, which proves to be very popular later in path planning. The main idea of the algorithm is:
  - For a tree, first initialize with a node; Then iteratively executes following:
  - Randomly pick one state x_r;
  - Find the nearest neighbor of this node in the current tree;
  - Select an input which would drives the nearest node to this random node;
  - Update the next node it finds;
  - Update tree (node and edge)

### Analysis

- Non-holonomic constraints: usually refer to kinematic constraints in the robotics, motion planning area. It is informally explained that non-holonomic refers to differential constraints that cannot be completely integrated. This means they cannot be converted into constraints that involve no derivatives.
- All randomized path planning methods suffer from the difficulty of determining or estimating the ideal metric, usually we use simple metrics and hopefully the convergence will be fast in practice.
- An RRT is minimal in the sense that it is always able to maintain a connected structure with the fewest edges. --> How edge matters?

### Thoughts
- How edges matter? -- Man, research!