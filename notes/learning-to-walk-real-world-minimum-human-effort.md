### 26.1.2021
## Learning to Walk in the Real World with Minimal Human Effort
#### Sehoon Ha, Peng Xu, Sergey Levine, Jie Tan


### Summary
- This paper explores using reinforcement learning directly on the real robot and achieved four walking tasks. To eliminate the failure case, it adds the extra cost term into the cost function and the number of failures are decreased, which can help free the people when the training is running.

### Analysis
- Details:
    - The robot is constrained in a working space, and going out of boundary would trigger early termination. (To deal with early termination, the expected future return is needed to make this rollout complete)
    - The robot has four tasks, forward, backward, turn left and turn right, a task scheduler is used to make sure the robot is heading the center of the working space, in that sense, the robot train multiple tasks simultaneously. 
- Pros:
    - It can do on-robot learning, and human interfere is reduced
    - It can train multiple policies together (by sampling a task from the task set), 4 tasks in this case
    - The safety regularizer can reduce the number of falls ( each fall needs more than 12 seconds to recover, recover scheme is not learned, but the controller has it)
- Cons:
    - The video result still shows strangely, the learning curve does not converge in the picture. However the robot can somehow walk (the first assumption of the paper that it can learn something even if it is partially trained)
    - The recover scheme is fixed, do not have a recovery learner.
### Thoughts
- I think on-robot learning is still not a future approach. Damage issues, and how to learn the recover? the robot would be damaged.
- Simulation learning and narrowing the sim-to-real gap should be more robust for big under-actuated robots.