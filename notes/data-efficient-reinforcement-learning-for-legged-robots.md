### 27.1.2021
## Data Efficient Reinforcement Learning for Legged Robots
#### Yuxiang Yang, Ken Caluwaerts, Atil Iscen, Tingnan Zhang, Jie Tan, Vikas Sindhwani, 2019 CoRL


### Summary
- This paper uses a neural network to learn the dynamics of the robot. With this learned dynamics, a MPC framework is used to plan the actions, which trigger the trajectory generator to control the robot. The experiment is also done on a real robot. Because we only need to learn the dynamic of the robot instead of direct end-to-end training, this method is very data-efficient.

### Analysis
- Details:
    - MPC is used to generate a sequence of actions, in this paper CEM(Cross Entropy Method) is used to optimize MPC. The reward/objective function of MPC and the constraints of the MPC is not very clear, to be honest, easy robot makes it possible, but for big robots, very likely will damage the robot.
    - MPC helps smooth the motion
    - Dynamic learning and data collection is processed alternately.
- Pros:
    - Data-efficient for training. A nice try with combining MPC and learning.
- Cons:
    - However, it loses the end-to-end feature of using neural networks in robot locomotion. With MPC we still have computation burden and cannot generalize well to unknown terrains.
    - If the robot is simply moving on the flat terrain, why would we need to learn the dynamics? the dynamic is anyway very simple in that case.
### Thoughts
- Similar approach is also used in ANYmal, where trajectory generator is used, etc. And actually the neural network does not change too much in term of state and action (MDP):
    - state: sensors, TG parameters
    - action: TG parameters that used to generate trajectory --> inversely can compute joint angles.
- Need to check the MPC method: CEM
    - Not sure if MPC here applies very well.