# Direct-and-Inverse-Kinematics
1 Direct and Inverse Kinematics
Consider the SCARA manipulator depicted below. For this project only the kinematic parameters are
needed. You have received a trajectory for the the manipulator end effector. The trajectory is provided in
a file named kinematic traj.mat and can be read using init.m.
The manipulator parameters are
d0 = 1 m, a1 = a2 = 0.5 m
θ1min = −π/2 rad, θ1max = π/2 rad, θ2min = −π/2 rad, θ2max = π/4 rad
d3min = 0.25 m, d3max = 1 m, θ4min = −2π rad, θ4max = 2π rad
The frames are depicted into the figure and the DH parameters are
di αi θi ai
Link 1 0 0 θ1 a1
Link 2 0 0 θ2 a2
Link 3 d3 0 0 0
Link 4 0 0 θ4 0
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
1. Implement in Matlab/Simulink the algorithms for kinematic inversion with inverse and jacobian transpose along the given trajectory. Adopt the Euler integration rule with integration time 1 ms. Implement
a final function visualize results.m for each part including everything in init.m and all the 2D-plots
(joint value and error). A sample function called plot outputs.m is provided for the joint errors.
1
2. Suppose to relax one component in the operational space, implement in Matlab/Simulink the algorithm
for kinematic inversion with Jacobian pseudo-inverse along the given trajectory maximizing in two
separate cases the distance from the mechanical joint limits (relax the orientation component ϕ). Just
implement the one considering the jacobian inverse.
Instructions:
• Make your code as a combination of matlab and simulink. The structure is already provided in the
folders. You should call your initialization in a function named init.m. This function should load the
trajectory and all the manipulator variables that have been previously listed. You will then define your
Jacobians in another function named Jacobian.m, which will be loaded in simulink. The file init.m
contains as well a call to a 3D visualization of the manipulator behavior. The file direct kin.m can be
used if you like to write the direct kinematics in matlab in case you do not want to write that using
simulink blocks.
• There is a different folder of each question. You should keep the current code structure. Once init.m
is ran in each folder, you should be able to automatically play the simulink environment and obtain
results. Show the joint trajectories in the joint space and the errors operational space.
