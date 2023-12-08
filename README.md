# E05_Robotiq-2f-85
A ROS package for simulation in gazebo and mujoco, include Hansrobot E05 Arm and Robotiq 2f-85 gripper.

I converted from the Solidworks model on the [Hansrobot official website](https://www.hansrobot.com/service/download/3dmoxing?pagenum=3) to the URDF model, added the Robotiq 2f-85 gripper model according to [this link](https://github.com/ros-industrial/robotiq.git), and performed Moveit. I adjusted the parameters and fixed some bugs. Currently, the robot can be controlled using the Moveit Panel in Gazebo and rviz.

And the mujoco configuration process also be finished, it can be seen in `e05/urdf_mujoco/e05_mujoco.xml`.

**Environment Required:**

- Ubuntu 20.04
- ROR Noetic (Make sure you have installed moveit package: `sudo apt install ros-noetic-moveit`)

## Quick Start

**(1) Prepare the ros workspace**

```shell
mkdir -p catkin_ws/src
cd catkin_ws/src
catkin_init_workspace
git clone https://github.com/HaofeiMa/E05_Robotiq-2f-85.git
cd ..
catkin_make
```

**(2) Launch Gazebo simulation**

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

![gazebo](https://github.com/HaofeiMa/E05_Robotiq-2f-85/assets/49356049/41f2267f-478e-4662-9ed8-e414d97cec22)

**(3) Prepare the mujoco environment**

Install the mujoco-210:

```shell
wget https://mujoco.org/download/mujoco210-linux-x86_64.tar.gz
mkdir ~/.mujoco
tar -xvzf mujoco210-linux-x86_64.tar.gz -C ~/.mujoco
gedit ~/.bashrc
```

Add following config

```shell
# Mujoco environment
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/nvidia
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/USERNAME/.mujoco/mujoco210/bin
export LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libGLEW.so
```

Test the mujoco

```shell
source ~/.bashrc
cd ~/.mujoco/mujoco210/bin
./simulate ../model/arm26.xml
```

**(4) Simulate in mujoco**

```shell
cd ~/.mujoco/mujoco210/bin
./simulate /path/to/workspace/src/E05_Robotiq-2f-85/e05_mujoco/mujoco/e05_with_robotiq_exp.xml
```

![image](https://github.com/HaofeiMa/E05_Robotiq-2f-85/assets/49356049/a60747b2-7964-4eed-96b1-a0e8c6a15499)


## More

If you want to know the complete creation process of the repository, or if you want to use your own Solidworks model to create Gazebo simulations and Moveit controls, please refer to [my blog for gazebo and moveit configuration process](https://www.mahaofei.com/post/7fec171b.html) and [this blog for mujoco configuration process](https://www.mahaofei.com/post/f67206dd.html).
