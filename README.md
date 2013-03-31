### Forked ROS Package: interpolated_ik_motion_planner

This is a fork of the ROS Fuerte release of interpolated_ik_motion_planner, <br>
from the arm_navigation_experimental stack.

These fixes & modifications are for using this node as part of the ROS Manipulation Pipeline, for robots other than the PR2. These changes have been tested to not break the simulated PR2 robot in ROS Fuerte Gazebo. <br>

Note: In the launch file, we specifiy robot_prefix=reem, and give each node an argument e.g. 'l' for left side. <br>
&nbsp;&nbsp;&nbsp;&nbsp; This causes it to look for Services under /reem_left_arm_kinematics/* <br>
&nbsp;&nbsp;&nbsp;&nbsp; However, the naming conventions vary, so the node's own Service is called /l_interpolated_ik_motion_plan <br>

ToDo: ik_utilities.py is hard-coded to reverse angles 0,2,4 of the left arm, because the PR2 launch file specifies <br>
&nbsp;&nbsp;&nbsp;&nbsp; a global start_angles array that is used by both the left and right-sided nodes. <br>
&nbsp;&nbsp;&nbsp;&nbsp; Need to find a way to specify start angles, without them being reversed, and without breaking the PR2 implementation.

-- David Butterworth, PAL Robotics S.L.
<br>

<br>
**Changelist:**

 - Fixed copy-paste error, the wrong variable name. (by Martin Gunther)

 - Suggested fix to the way commandline arguments are read. (by Martin Gunther)
It seems to work without this change.

 - Added a timeout, so Interpolated IK will report that it failed to find the Kinematics Service, otherwise it will just crash later.



