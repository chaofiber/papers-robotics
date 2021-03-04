#

## Perceptive Locomotion in Rough Terrain - Online Foothold Optimization

### Fabian Jenelten, Takahiro Miki, Aravind E Vijayan, Marko Bjelonic, and Marco Hutter

### 3.3.2021

### Summary

- This paper proposes a method that can simultaneously optimize over the foothold position, and take into considerations of terrain heights, aggressive motions, over-extensions etc. It is also able to adjust the contact schedule to give the leg enough time to walk over the terrains.
  

### Analysis

### Thoughts

Some aspects that might be interesting also in developing foothold selection algorithms:

- Which part of the robot is relatively accurate? in this paper, the thigh is most close to the body, and therefore can relatively estimate this value first, and further we can give an estimated nominal position of the foothold based on default leg configuration.
- Foothold score, it is a score for the cell in the nominal-foothold-centered map, calculated based on some numerical values such as mean, edge, etc.
- Pushover: Mostly it is an intuitive value, along the current position and the next swing position, it should have as many nice cell as possible.
- Supporting area: The distance between the support legs should be relative large to keep balance.
- Previous foothold: should penalize too aggressive step.
  
There are also some constraints that should be considered:
- Max step height: along the current foothold and the next optimized foothold, the terrain should not have too high peaks.
- Leg collision: legs should not be too close to each other.
- Leg over-extension: some times joints not very accurately estimated, use am impedance control to deal with this:
  - Give a gain to the deviation on the desired joint position and desired joint velocity, and modify the torque correspondingly.
- Need to adjust the contact schedule (time for swing) based on the maximum height in the terrain. 
- Torso orientation is fitted with current and desired foot positions.