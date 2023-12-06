# E05_Robotiq-2f-85
A ROS package, include Hansrobot E05 Arm and Robotiq 2f-85 gripper.

I converted from the Solidworks model on the [Hansrobot official website](https://www.hansrobot.com/service/download/3dmoxing?pagenum=3) to the URDF model, added the Robotiq 2f-85 gripper model according to [this link](https://github.com/ros-industrial/robotiq.git), and performed Moveit. I adjusted the parameters and fixed some bugs. Currently, I am able to use the Moveit Panel to control the robot movement in Gazebo and rviz.

**Environment Required:**

- Ubuntu 20.04
- ROR Noetic (Make sure you have installed moveit package: `sudo apt install ros-noetic-moveit`)

## Demonstration

![image](https://github.com/HaofeiMa/E05_Robotiq-2f-85/assets/49356049/41f2267f-478e-4662-9ed8-e414d97cec22)

## Quick Start

**(1) Prepare the environment**

```shell
mkdir -p catkin_ws/src
cd catkin_ws/src
catkin_init_workspace
git clone https://github.com/HaofeiMa/E05_Robotiq-2f-85.git
cd ..
catkin_make
```

**(2) Launch**

View robot with gripper in rviz:

```shell
source ./devel/setup.bash
roslaunch e05 display_e05_with_gripper.launch
```

View robot with gripper in gazebo:

```shell
roslaunch e05 gazebo_e05_with_gripper.launch
```

Visulaize the motion in gazebo, using moveit pannel in rviz.

```shell
roslaunch e05_moveit demo_gazebo.launch
```

## More

If you want to know the complete creation process of the repository, or if you want to use your own Solidworks model to create Gazebo simulations and Moveit controls, please refer to [my blog](https://www.mahaofei.com/post/7fec171b.html).
