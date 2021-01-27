### 26.1.2021
## MPC-Net: A First Principle Guided Policy Search
#### Jan Carius, Farbod Farshidian, Marco Hutter
#### video: https://www.youtube.com/watch?v=VI7wt5PCJ14

### Summary
- For a nonlinear optimal control problem, the optimality principle is that the control input should minimize the Hamiltonian. In a Sequential Linear-Quadratic solver, it returns all elements that needed to compute the Hamiltonian actually. Therefore, the intuition is that this Hamiltonian can be used as the objective for the control policy to optimize over. Therefore, this paper bridges the nonlinear MPC problem and the policy gradient approach. In a typical RL problem, we need to design a reward function, then in this paper, this is simplified by rollout the MPC (with the target) and use the generated data as training sample (to compute the Hamiltonian)
- An end-to-end control policy can be learned.

### Analysis
- Details:
    - State augmentation is required, e.g. in every rollout, need to sample a starting point from the nominal starting point, and compute all related values for Hamiltonian and collect data tuple.
    - The policy gradient is executed after the rollout from the current staring point is done. --> therefore the equivalence of using expectation over per-sample Hamiltonian is guaranteed.
    - Multi-expert neural network is used to model the policy function.
    - The states and inputs of this system is the same as other ANYmal robots I think, 24 states and 24 inputs. (could check other ANYmal papers)
- Pros:
    - It is very novel in using MPC as a guidance for RL policy training. 
    - It is also data-efficient.
- Cons:
    - I don't think a planning problem can be tackled with this approach. The policy only takes the state as input and need to output a policy, from the video it only achieves the standing-by task. 
    - A more complex problem, if it cannot handled by MPC, then it cannot be handled by this MPC-net either.
### Thoughts
- My thoughts are that using MPC as guidance, the performance of this approach is restricted by the performance of the MPC approach. Therefore, for complex terrains or tasks, it is still not applicable.
    - But, if MPC improves a lot, this method might grow as MPC grows.