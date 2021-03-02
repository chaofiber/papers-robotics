### 28.1.2021
## Practical Reinforcement Learning for MPC: Learning from sparse objectives in under an hour on a real robot
#### Napat Karnchanachari, Miguel I. Valls, David Hoeller, Marco Hutter
#### https://www.youtube.com/watch?v=PJB8XdXBP_M


### Summary
- This papers introduces some practical ways of integrating reinforcement learning into MPC. The terminal cost can be approximated by a neural network, and the stage cost can be rewritten as the deduction of two terminal functions, therefore can also be approximated as a neural network.
- Learning based method outperform the naive MPC, and can be comparable to expert MPC where parameters are tuned, and it can handle the sparse reward case, which can not be used as stage/terminal cost for MPC directly because it is not differentiable.

### Analysis
- Details:
    - The data tuple collected from the MPC with a dense/sparse reward is used to compute the gradient of the parameter that is used for computing the value function.
    - Sparse reward is obviously not able to serve MPC directly (under certain solver), because it is not differentiable.

- Pros:
    - The process is more intuitive, because in some situations, like tracking, designing the reward is pretty easy (either dense or sparse) while designing the stage/terminal cost for MPC can be difficult.
    - Can save time on designing stage costs and terminal costs for MPC problem, but the problem is still inherently a MPC problem.
- Cons:
    - The experiment is done on a wheel robot and do not have the risk of falling. But such methods can not be extended to other agile or big robots easily, because at the beginning of the phase when the robot knows nothing about the terminal/stage costs, the robot will be damaged.
    
### Thoughts
- I think this method can only be used under the branch of MPC, the performance still relies on the computation of MPC. IN many cases, I think designing a quadratic stage/terminal cost is also enough for MPC.