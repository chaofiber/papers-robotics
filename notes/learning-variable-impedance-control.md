#

## Learning Variable Impedance Control for Contact Sensitive Tasks

### Miroslav Bogdanovic, Majid Khadiv, Ludovic Righetti

### 8.2.2021

### Summary

- For a reinforcement learning based robotics task, choosing action space is important. A previous paper shows that joint positions are ideal options, and then further applied with a PD controller with some hand-tuned gain. This papers shows that these gains can also be learned.

### Analysis

- Details:
  - The robot task is two jump the hopper as high as possible, and also to control a fixed base robot arm to track a circle. From the video we can see it is able to jump higher than if we do not use variable gain.
  - Additional reward term designed to regularize these variable impedance control policies, giving them interpretability and facilitating transfer to real robots. --> penalizing the distance between the computed desired joint position and the actual position at the next step.
    - Normally, in many applications, once a desired joint position is computed, then a PD controller is used to track it, and because that controller has very high frequency, the tracking is actually very nice and easy to realize.
    - Therefore, I don't quite understand why, when we use a variable gain PD controller, and the same time, also tracking the joints explicitly in the reward function.

- Pros:
  - To learn the gain matrix is useful if the motion is contact rich, in the sense, it should encounter very steep contact force changes.

- Cons:
  - Is it really necessary? at the cost of doubling the output dimension.
  - For robust robots, like ANYmal, they don't have very extreme contact with the ground (sharp contact), most of times it is enough to use a fixed PD gain.
  - Or PD gain can actually be tuned in a easier way, for example, simply based on the position of the end-effector, the extension status of the leg, etc.

### Thoughts

- Questionable if this can be extended to more complex systems, because currently it has only two control variables, so the output of the control signals are only four (including two gain parameters, assuming diagonal gain matrix). If we have, for example, 12 joints to control, then double it means the output will be 24.

- To be honest, I think it is not very valuable work, as the main contribution is actually that the joint position control is better than torque control in many cases. I don't see lots of gains if we simply further learn the PD gain matrix.