# Direct-and-Inverse-Kinematics
Consider the SCARA manipulator depicted below. For this project only the kinematic parameters are
needed. You have received a trajectory for the the manipulator end effector. The trajectory is provided in
a file named kinematic traj.mat and can be read using init.m.
![螢幕擷取畫面 (50)](https://user-images.githubusercontent.com/69573286/197291442-e64c6f8e-49dd-4a8d-89f7-daa7d5da6b73.png)
Table 1: Table with DH parameters.
Please not that the 0 frame is not coincident with the b frame. There is a translation from the ground
plane denoted with d0 = 1. The frame 4 is coincident with the frame 3 at the starting. Be careful on the
d3 component. The range of values is always positive. When the arm is fully extended (down towards the
floor) the value is 1m whereas 0.25 when retracted (away from the floor). However, when you build your
matrix note that d3 moves along −z2 axis and for this reason you translation in A2
3
should be negative as
−d3.
Questions:
1. Implement in Matlab/Simulink a second order algorithm for kinematic inversion with jacobian inverse
along the given trajectory. Adopt the Euler integration rule with integration time 1 ms. Implement a
final function visualize results.m for each part including for all the 2d-plots (joint value and operational
space errors). A sample function called plot outputs.m is provided for the joint errors.
1
2. Suppose to relax one component in the operational space (relax the z component), implement in
Matlab/Simulink the second order algorithm for kinematic inversion with Jacobian pseudo-inverse
along the given trajectory maximizing the distance from an obstacle along the path. Suppose that the
obstacle is a sphere centered in p =

0.4 −0.7 0.5
⊤
with radius 0.2 m.
Instructions:
• Make your code as a combination of matlab and simulink. The structure is already provided in the
folders. You should call your initialization in a function named init.m. This function should load the
trajectory and all the manipulator variables that have been previously listed. You will then define your
Jacobians in another function named Jacobian.m, which will be loaded in simulink as shown during
the class. The derivative of the Jacbian is Jacobian dot.m. The file init.m contains as well a call to a
3D visualization of the manipulator behavior in case you want to use it. The file direct kin.m can be
used if you like to write the direct kinematics in matlab in case you do not want to write that using
simulink blocks.
• Make a different folder of each question. Once init.m runs in each folder, we should be able to
automatically play the simulink environment and obtain results. Show the joint trajectories in the
joint space and the errors operational space.

