#

## Robust  Rough-Terrain  Locomotion  with  a  Quadrupedal  Robot

### Peter Fankhauser, Marko Bjelonic, C. Dario Bellicoso, Takahiro Miki and Marco Hutter

### 2.3.2021

### Summary

- This paper proposes an integrate motion planner and controller for a robot to walk over tough terrains such as stairs. When walking over stairs, there are several key elements:
  - elevation map: In this paper, no learning method is used, and to score the map is relatively cheap. It use some features such as slope, curvature, roughness and uncertainty of the map data (the elevation map itself contains uncertainty measurement) as key index to measure the score of each cell. Use a threshold to finally get a binary foothold score for the map.
  - Nominal foothold position: First of all, the base pose is interpolated from the start pose to the target pose. And the nominal foothold (for the next step) for each leg is defined as a default relative position to the base (in stance position).
  - Actual desired foothold position: this is simply achieved by adding a safety filter to the nominal foothold, if the nominal foothold is feasible (by checking the elevation map), and kinematically feasible, if not, then find the closest point (region) to the nominal foothold while satisfying the constraints.
  - After having the current estimated foothold and the desired next step foothold, a swing leg planner is further used to make sure collision does not happen by Cubic interpolation method and optimize for the knots. 

### Thoughts
