## Planning in Learned Latent Action Spaces for Generalizable Legged Locomotion

### Tianyu Li, Roberto Calandra, Deepak Pathak, Yuandong Tian, Franziska Meier, Akshara Rai

### 6.3.2021

### Summary

- Hierarchical learning is popular in robot learning, basically, the planner and controller are usually decoupled and trained separately. This paper proposes to also optimize over the interface variable connecting the planner and the controller, therefore jointly learning the latent action space (what the robot should track, for example, desired body velocities) and the low-level controller.
### Analysis

- Multiple experts are used to learn the low-level controller via imitation supervised learning ( the number of experts can make some difference), but the essence is that the robot should be able to learn the latent action space and the policy jointly, the action space can then hopefully represents the idea of the robot better.
  - One advantage of this paper is also this policy is used for all tasks, as long as the latent action space is learned. (Does MPC-net do the same thing? because we are actually learning how to walk with the experts from the MPC controller).  
- The model learning part is also important, the latent action space is named action space is because this is employed on the dynamics of the robot, We would learn the dynamic takes inputs of this latent action, and the previous state, and then we get the next steps. Details include for example, learn the next-N-step states. But the idea is we would think the latent action space represents pretty well. (therefore can be trusted as an action)
- The model predictive control is still used in the sense that the latent action should be chosen to minimize the high-level task, for example, to track a trajectory or to reach a goal. This model predictive control actually does not (seem) to have constraints, which might speed up the computational speed.
  
### Thoughts

- In the paper, the dimension of the latent action space varies from 2 to 4 and does not make big difference, so it could be regarded as that the latent space *is* the desired CoM position, etc. The ablation study shows that in normal cases, with the model based controller outperforms the learned model a bit, but if the leg joint is fixed or so (while the kinematic constraints are violated), the learned policy is more robust (actually intuitive I would say)

