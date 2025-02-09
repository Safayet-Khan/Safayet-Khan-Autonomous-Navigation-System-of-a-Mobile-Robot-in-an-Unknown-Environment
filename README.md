# Autonomous Navigation System of a Mobile Robot in an Unknown Environment
This repository contains my source code and implementation video of the autonomous navigation system of a mobile robot. The proposed algorithms follow a short and smooth trajectory. The algorithm I have used is a goal-oriented algorithm that always sets its path according to the location of the goal point. But in the wall following algorithm, while the robot is trying to follow a wall, certainly it does not know the outside of its disk abstraction. The robot takes the decision depending on the data it is receiving using sonar range sensors. But the sensor does not have a wide range. The robot takes the decision about its movement based on the clock-wise and counter-clock-wise direction vector multiplication. Therefore, sometimes it may travel more path than expected.

## Source Code Files Order 
:warning: I have worked on this project in 2016. Since it's been a long time some of the code may be deprecated.

1. **pid_error_calculation.ino**
2. **encoder_sonar_setup_with_previous.ino**
3. **go_to_goal_algorithm_with_previous.ino**
4. **obstacle_avoidance_algorithm_with_previous.ino**
5. **follow_wall_algorithm_with_previous.ino**

## Steering Control System, Local Co-ordinate System, and Global Co-ordinate System
For a mathematical explanation of the full control system of this differential drive mobile robot sees the [paper mentioned below](#published-conference-paper-on-this-project). It contains proper explanations with mathematical justifications. Also, I would encourage anyone interested to do the [MOOC mentioned below](#acknowledgement).

## Simulation Results
The algorithms proposed for navigation is efficient for both types of concave and convex obstacles. The robot does not suffer from local minima in any of the cases. The simulation results show the improvement over existing approaches like Follow the Gap Method (FGM), Vector Histogram (VFH), etc. We can also see that the proposed navigation algorithm is better than the A* search algorithm, Dijkstra's Algorithm or Grassfire Algorithm, which are used for navigation in a known environment.

The simulation result (Fig. 1) shows that the agent goes from point (0,0) to (1,1) following the concave obstacle wall to a certain condition and then tries to avoid the small obstacle and reach the goal point. The simulation result (Fig. 2) shows that the agent goes from point (0,0) to (-1,1) point avoiding the convex obstacles and reaches the goal. It is to be noted that the simulation was done using [‘Sim.I.am’](https://www.mathworks.com/matlabcentral/fileexchange/40860-sim-i-am) which is a [MATLAB](https://www.mathworks.com/?s_tid=gn_logo) based mobile robot simulator developed by [GRITS laboratory](http://gritslab.gatech.edu/home/) of [Georgia Institute of Technology](https://www.gatech.edu/).

<img src="images/simulation_results.png" width=750>

## Practical Implementation
For the hardware platform, a differential drive wheeled robot is made. There are two wheels that are controlled by DC motors and a caster ball at the front side for the balancing of the robot. Five Ultrasonic distance sensors are used in the front part of the robot to take a decision about the environment and wheel encoders are used to measure the rotation of the wheel and using this information it estimates its position in the environment. The control mechanism is based on the processor [Arduino MEGA](https://store.arduino.cc/products/arduino-mega-2560-rev3). In this project, I did not use any accelerometer. I was just depending on the wheel encoder for localization. So drift is a major issue for this robot. One may use dead weight in the middle position of the wheels to get rid of drift.

<img src="images/robot_photo.jpg" width=500>


### Practical Video of the Robot
1. [Go-To-Goal Behavior](https://www.youtube.com/watch?v=mx56AGjGusU) on YouTube
2. [Obstacles Avoidance Behavior](https://www.youtube.com/watch?v=s9AxqqOxT4g) on YouTube
3. [Go-To-Goal with Obstacles Avoidance Behavior Together](https://www.youtube.com/watch?v=MwT14vDychA) on YouTube
4. [Follow Wall with Obstacles Avoidance Behavior Together](https://www.youtube.com/watch?v=S0naiIBdsRg) on YouTube


https://user-images.githubusercontent.com/17143739/135394618-da66b9b2-9d9e-4c7e-8e78-17d9edb38072.mp4


## Acknowledgement
I have learnt a lot regarding control theory from the MOOC on [“Control of Mobile Robots”](https://www.my-mooc.com/en/mooc/control-of-mobile-robots/). It was taught by [Dr. Magnus Egerstedt](https://www.ece.gatech.edu/faculty-staff-directory/magnus-egerstedt-0).


### Published Conference Paper on this Project
S. Khan and M. K. Ahmmed, ["Where am I? Autonomous navigation system of a mobile robot in an unknown environment"](https://ieeexplore.ieee.org/document/7760188) - ieee xplore document, May 13-14, [2016, 5th International Conference on Informatics, Electronics & Vision (ICIEV)](http://cennser.org/ICIEV16/#:~:text=Welcome%20to%20the%205th%20International,IPS%20will%20be%20sent%20to%20.).

