### 27.1.2021
## Learning to Walk via Deep Reinforcement Learning
#### Tuomas Haarnoja, Sehoon Ha


### Summary
- This paper explores using deep reinforcement learning directly on the real robot. It used the maximum-entropy RL to achieve that. The maximum entropy encourages the policy to be as stochastic as possible while still maximizing the reward. Therefore, it is often data-efficient. However, due to the temperature parameter is not scale-invariant, and therefore for different tasks with different reward scale, it has to be tuned again. This paper adapted the original maximum-entropy RL into a constrained RL, and dualize it and alternate it into an another objective regarding to the temperature, and can be directly optimized. 

### Analysis
- Details:
    - Modularize the training process, in case some error happens in the communication and signal when experimenting on the real robot, this is a practical trick.
    - Objectives following from a standard RL problem: 
        - function approximation using Q-learning and Q function is approximated by a neural network
        - the direct reward including the entropy regularization, the temperature parameter is learned by another objective and is fixed and explicit in the direct reward
        - the objective regarding the temperature is derived from the entropy constraint that is adapted from the entropy loss
- Pros:
    - It can train the policy directly on the robot, and the robot is robust to overcome some unseen terrains. 
- Cons:
    - Not likely be able to apply to a bigger and robust robot like ANYmal, because it lacks a safety layer, and too many times of failure will damage the robot
    - There are no auto-recovery scheme and need human effort to reset the robot.
### Thoughts
- I need to take a look at maximum-entropy algorithm again
- Optimization and dual optimization is applicable in RL as well. Sounds interesting, I need to check the mathematical deviation later.