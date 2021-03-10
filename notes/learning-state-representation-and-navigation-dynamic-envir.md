## Learning a State Representation and Navigation inCluttered and Dynamic Environments

### David Hoeller, Lorenz Wellhausen, Farbod Farshidian, Marco Hutter

### 10.3.2021

### Summary

- This paper uses a variational auto-encoders to learn the latent feature of a sequence of depth-images, and use a LSTM to predict the next state that represents the environment. Together with the goal position, this predicted latent feature is fed into a network that learn a control signal for the robot to move. The training of the policy is done on the simulation engine and the training of the VAE is done with both simulation data and the real world data.
### Analysis

- One baseline is that: Use CNN to extract a feature and augment with goal position, followed by a MLP to train the policy. (Still within the RL framework), another baselines is instead a CNN + LSTM approach. Both is not as good as the VAE version. 
  - Essentially, VAE also uses CNN and actually uses multiple images, so it is not too surprising that VAE is the best among those three.
- One advantage, I think, compared to other SLAM based method, is that it can handle dynamic environments and does not care about memorizing the environment, while the latter is usually the major task of SLAM. 
### Thoughts

- Under what situations shall we maybe consider VAE? and consider Sequential-to-sequential VAE?  In this paper, the environment changes relatively fast and uses this method may have an advantage. 
- Is it generally worse off if we train the image end-to-end without any pre-training process?

