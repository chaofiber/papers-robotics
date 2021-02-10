#

## Multi-Layered Safety for Legged Robots via Control Barrier Functions and Model Predictive Control

### Ruben Grandia, Andrew J. Taylor, Aaron D. Ames, Marco Hutter

### 10.2.2021

### [[video](https://www.youtube.com/watch?v=TCDIirXfByE&feature=youtu.be)]

### Summary

- This paper leverages the Control Barrier Function (CBF) in both low-rate MPC and high-rate WBC, therefore ensures the constraints are satisfied in the real experiments. This is the first experimental success in applying CBF on a real robot.

### Analysis

- Details:
  - Control Barrier Function: A function h(x,t) is control barrier function if the there exists a function in he extended class (a mathematical class), that the derivative of the function h(x,t) is smaller than -a(h(x,t)).
    - In robotics, is is used as a safety filter added as a constraint (In many cases in the form of a linear constraints).
    - In CBF, there are two conditions that can be derived, one is more general, the other one is often used by a class of exponential functions. Many cases, people only enforce the second condition, which leads to aggressive motions. In this paper, both conditions are enforced, the first is applied in the MPC level, where torque does not effect the optimization. The second condition is applied in WBC where a QP is solved.
- Pros:
  - Multi-layer safety filter
  - For the first time the control barrier function is applied in a real robot.
- Cons:
  - The constraints that are useful here are simply linear constraints, ( a polygon), and is manually decided (the robot knows already exactly where the terrain segment is). Need to automate the process of extracting those constraints.
  
### Thoughts

- Further work: It mentioned that extracting constraints can be done by a perception pipeline. That is possible even without neural network.
  - What kind of information it want the perception pipeline to do?
    - It could be simply terrain segment? In that case we can form constraints and then compute date based on the MPC solution.
    - Does reinforcement learning also need this input? maybe yes..
      - If the control barrier function related constraints are relaxed in the MPC optimization and QP optimization, so it shouldn't be different from the simple flat terrain case.
  