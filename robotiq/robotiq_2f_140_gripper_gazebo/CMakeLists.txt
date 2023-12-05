cmake_minimum_required(VERSION 2.8.3)
project(robotiq_2f_140_gripper_gazebo)
find_package(catkin REQUIRED)
catkin_package()

install(DIRECTORY config launch urdf
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
