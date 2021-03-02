#

## Robust Recovery Controller for a QuadrupedalRobot using Deep Reinforcement Learning

### Joonho Lee, Jemin Hwangbo, and Marco Hutter

### 15.2.2021

### Summary

- This paper proposes a robust recovery controller for ANYmal robots. It decompose the recovery process into three behaviors: self-righting, standing up and locomotion. Where the first one is the most complicated one (Policy runs at 20 Hz, most slow, but already really fast). There is an extra behavior selector network which is used as selecting components of each three behaviors, while three behaviors are pre-trained independently.

### Analysis

- Details:
  - Some key features that play a role in determining if the robot is in need of recovery: Base height, the angle between the inertial z axis and the base z axis. 
    - Traditional height estimator becomes unreliable when the robot falls, a neural network is instead used to estimate the height of the robot.
    - TSIF (Two State Implicit Filter) is used to estimate the orientation and give as input to the height neural network estimator.
  - Randomization of parameters is used, and in addition, when the robot leg is in air, additional noise is further added to increase the robustness.

- Pros:
  - The experiment of the FSM (Finite State Machine), a hand-crafted behavior selector is also implemented, it is unable to handle some corner cases. With neural network based method, it is able to generalize better.
  - The recovery is very effective and fast, about 3 seconds.
  
- Cons:
  - Can only handle flat terrain so far, need to generalize to for example, slopes and other difficult terrains.

### Thoughts

- The robot does look like recovering like how a baby learn to stand up.

