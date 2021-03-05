## Receding Horizon “Next–Best–View” Planner for 3D Exploration

### Andreas Bircher, Mina Kamel, Kostas Alexis, Helen Oleynikova1and Roland Siegwart

### 5.3.2021

### Summary

- This paper proposes a path planning algorithm for the autonomous exploration of unknown space for aerial robots. The best search branch is chosen based on the fact that it is able to find out more unknown space.

### Analysis

Basic background knowledge about exploration problems:
- An unknown map is discredited by cells, and there are occupied cells (wall, obstacle), free cells (the robot can move along), and unknown cells (need to minimize the number of unknown cells).
  -  The array of those cells are stored in an octree --> simply a storage method, is efficient to query certain cells.
  -  A gain is introduced for each node as the summation of the (weighted) unmapped cell that can be explored at the nodes along the branch. At last the node with the highest gain will be picked (as the destination) and the path connecting it with the starting point would be the best path segment.
  -  The gain is measured by the visibility at certain configuration (position) of the robot, obstacled with occupancy map (because the obstacle stops the view), and also scaled by a cost for longer path. The robot can use lidar or other cameras to capture items, the lidar has a range and we usually keep it low to make it robust and computational efficient.

### Thoughts

- Simply take the best-of-next view actually wastes quite a lot information. Maybe it would be smart to also keep the current computations for all branches.