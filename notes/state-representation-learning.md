## State representation learning for control:An overview

### Timothée Lesort, David Filliat

### 12.3.2021

### Summary

- This paper is an overview of approaches dealing with state presentation problems for control. It can be used in a RL setting, and can also be used in more general cases. Some presentation characteristics include following tradeoff:
  - Markovian (the dimension cannot be too low, because it should summarize all the necessary information to be able to choose an action within the policy, by looking only at the current state)
  - Low dimensional for efficient estimation.
- Some popular approaches include:
  - Reconstruction the observations (usually for example, images)
    - an encode and a decoder, the dimension of the latent state is sort of a constraint for the model.
  - Learning a forward model, this kind of method often requires an action, because without action, we do not have next states.
    - Usually the state evolution would be assumed as linear over the previous state and the action.
    - Or the next state is sampling from the distribution whose mean and variance is dependent on the linear combination of the last state and the action
  - Learning an inverse model: to approximate the actual action and use that as loss function.

### Analysis

- Auto-Encoder: (encoder + decoder) 
  - Denoising auto-encoders: it adds noise to the input. I think there are also methods used inversely, that the denoise the input image first and then compute the reconstruction error based on the denoised image. The denoise approach actually depends on how easy an auto-encoder can find representations:
    - If it find a simple one but not capturing the essence, then need to make it difficult by adding noise to the input image
    - If it is too difficult, then use denoised image to compute reconstruction error.
  - Variational auto-encoders (VAE):
    - The latent representation follows a distribution *p0(s|o)*, which we will try to approximate is with a distribution *q(s|o)*. The generator is also approximated by a distribution *p(o|s)*. The two approximates are both trained to minimize the reconstruction error and the KL divergence between *q* and a normal distribution. 
      - Generators are parametrized by a neural network so it does not matter what distribution it exactly follows (numerically optimized).
  
### Thoughts

- Sometimes dynamics constraints are also considered, in the sense that multiple time-dependent inputs are fed into the encoders. Usually this will relate to predicting a next state and also will need actions.
- When we say constraints, we usually simply refer the dimension of the latent representation.
