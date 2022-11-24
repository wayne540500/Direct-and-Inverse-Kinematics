# Direct-and-Inverse-Kinematics
Consider the SCARA manipulator depicted below. For this project only the kinematic parameters are
needed. You have received a trajectory for the the manipulator end effector. The trajectory is provided in
a file named kinematic traj.mat and can be read using init.m.
![螢幕擷取畫面 (50)](https://user-images.githubusercontent.com/69573286/197291442-e64c6f8e-49dd-4a8d-89f7-daa7d5da6b73.png)
Please not that the 0 frame is not coincident with the b frame. There is a translation from the ground
plane denoted with d0 = 1. The frame 4 is coincident with the frame 3 at the starting. Be careful on the
d3 component. The range of values is always positive. When the arm is fully extended (down towards the
floor) the value is 1m whereas 0.25 when retracted (away from the floor). However, when you build your
matrix note that d3 moves along −z2 axis and for this reason you translation in A23 should be negative as −d3.
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
ht2383 	N15040025 	Hua Wen, Tsuei
Project2 report
Part1:
 
According to the scheme on textbook, I draw the same structure on matlab using Simulink.(run the init.m file) 

For KD KP I set them both 300.
Put scope on e, e_dot & q to observe

the scope of q:
 
the scope of error:
 
the scope of error_dot:
 
Analytic Jacobian:
-a1*sin(th1)-a2*sin(th1+th2)        -a2*sin(th1+th2)        0       0
a1*cos(th1)+a2*cos(th1+th2)         a2*cos(th1+th2)         0       0
0                                  	 0                       -1      0
1                                  	 1                       0       -1
Jacobian inverse:
-a1*sin(th1)-a2*sin(th1+th2)        -a2*sin(th1+th2)        0       0
a1*cos(th1)+a2*cos(th1+th2)         a2*cos(th1+th2)         0       0
0                                  	 0                       -1      0
1                                   	 1                       0       -1
Jacobian dot:
-a1*sin(th1)-a2*sin(th1+th2)        -a2*sin(th1+th2)        0       0
a1*cos(th1)+a2*cos(th1+th2)         a2*cos(th1+th2)         0       0
0                                   	0                       -1        0
1                                   	1                        0       -1
If you run the plot_output.m file you will get all the Joint value and Operational space Error.
Operational space Error:
  
Joint value:  
 
Part2:
 
 
There should only have 3 rows in jacobian pseudo-inverse is given by: J^†  = J^T (J J^T )^(-1)
according to the equation I think the Simulink scheme should look like below, this time I write my code inside Simulink function:
 
From the scope we can get error:
 
and q:
 
To get the Joint variables and errors in the operational space(please run the plot_output.m file):
Figure1: for theta1 theta2 d3 theta4
 
Figure2: for the error
 
Figure3: for x y z
 
