cmake_minimum_required(VERSION 2.8.3)
project(vrep_plugin_velodyne)




find_package(
catkin REQUIRED COMPONENTS
  roscpp
  std_msgs
	)

catkin_package(
               CATKIN_DEPENDS roscpp rosconsole std_msgs roslib
               DEPENDS roscpp rosconsole std_msgs roslib)

include_directories(${catkin_INCLUDE_DIRS})


link_directories("/opt/ros/melodic/lib")

add_library(
            v_repExtRosVelodyne
            src/v_repLib.cpp
            src/ros_server_velodyne.cpp
            src/velodyneROSModel.cpp
            src/velodyneROSModelCont.cpp
            src/v_repExtVelodyneROS.cpp
            src/scriptFunctionDataItem.cpp
            src/scriptFunctionData.cpp
            include/v_repLib.h
            include/scriptFunctionData.h
            include/scriptFunctionDataItem.h
            include/vrep_plugin_velodyne/ros_server_velodyne.h
            include/vrep_plugin_velodyne/velodyneROSModel.h
            include/vrep_plugin_velodyne/velodyneROSModelCont.h
            include/vrep_plugin_velodyne/v_repExtVelodyneROS.h)

add_dependencies(v_repExtRosVelodyne ${catkin_EXPORTED_TARGETS})
target_link_libraries(v_repExtRosVelodyne
    pthread
    dl
    roslib
    rosconsole
    rostime
    rospack
    roscpp_serialization
    roscpp
    boost_system
   ${catkin_LIBRARIES}
)
