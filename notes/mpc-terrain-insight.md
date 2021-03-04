
## MPC-based  Controller  with  Terrain  Insight  for  Dynamic  Legged Locomotion

### Octavio Villarreal, Victor Barasuol
https://www.youtube.com/watch?v=oIw_EyzsmnM
### 4.3.2021

### Summary

- This paper continues this group's previous work on CNN for foothold prediction, and further combine it with a MPC controller, to walk across difficult terrains. This is the first approach in combining machine learning as perception pipeline and a MPC controller for a quadruped robot.
- Because foothold selection is fast, so it can leverage the advantage of CNN and predict more footholds, which are used for MPC to track.

### Analysis
- The MPC used here is like MIT cheetah MPC, it is a linear model and the state dimension is 15 (base 12 + gravity 3 (fake state)). Not sure how the desired foothold position effect the desired trajectory in the way that the contact force (MPC optimized variable) go through the foothold position to exert moment to the robot.
- This paper also uses leg inertia compensation to compensate the neglect in the dynamics by simply adding a modification term in the torque as proportional to the desired joint acceleration.
- The CNN takes care of two steps forward, so it predicts two potential footholds for each leg. The design of this nominal foothold is, to be honest, case by case and should base on the real robot. But the idea is intuitive and engineering-perspective.
### Thoughts

