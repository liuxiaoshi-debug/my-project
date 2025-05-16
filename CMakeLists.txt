cmake_minimum_required(VERSION 3.5)
project(ur5e_description)

## 查找 catkin 及所需组件
find_package(catkin REQUIRED COMPONENTS
  xacro
  urdf
  gazebo_ros           # Gazebo 插件
  robot_state_publisher
  controller_manager   # ros_control 中央管理器
  joint_state_controller
  effort_controllers
  position_controllers
  gazebo_ros_control
  controller_interface
  hardware_interface
  joint_trajectory_controller
  roscpp
)

###################################
## catkin 配置 ##
###################################
catkin_package(
  INCLUDE_DIRS urdf
  CATKIN_DEPENDS
    xacro
    urdf
    gazebo_ros
    robot_state_publisher
    controller_manager         # 新增
    joint_state_controller      # 新增
    effort_controllers          # 新增
    position_controllers      # 新增
    controller_interface
    hardware_interface
    joint_trajectory_controller
    roscpp
)

#############
## 安装规则 ##
#############
install(DIRECTORY urdf/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/urdf
  FILES_MATCHING PATTERN "*.xacro"
)
install(DIRECTORY launch/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch
  FILES_MATCHING PATTERN "*.launch"
)
install(DIRECTORY config/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/config
  FILES_MATCHING PATTERN "*.yaml"
)
install(DIRECTORY meshes/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/meshes
)
install(DIRECTORY cfg/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/cfg
  FILES_MATCHING PATTERN "*.rviz"
)
