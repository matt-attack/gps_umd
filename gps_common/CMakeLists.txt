cmake_minimum_required(VERSION 3.5)
project(gps_common)

# Add support for C++11
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 11)
endif()

#find_package(rosidl_default_generators REQUIRED)
find_package(ament_cmake REQUIRED)
#find_package(${DEPS} REQUIRED)
find_package(std_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(builtin_interfaces REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME} 
  "msg/GPSStatus.msg" 
  "msg/GPSFix.msg"
  DEPENDENCIES builtin_interfaces
  std_msgs
)

#set(INCLUDE_DIRS include ${rosidl_default_generators_INCLUDE_DIRS}
#  ${ament_cmake_INCLUDE_DIRS} ${${DEPS}_INCLUDE_DIRS})
#include_directories(${INCLUDE_DIRS})

#set(LIBRARY_DIRS ${rosidl_default_generators_LIBRARY_DIRS}
#  ${ament_cmake_LIBRARY_DIRS} ${${DEPS}_LIBRARY_DIRS})

#link_directories(${LIBRARY_DIRS})

set(LIBS ${rosidl_default_generators_LIBRARIES} ${ament_cmake_LIBRARIES})
#  ${${DEPS}_LIBRARIES})

############
## Catkin ##
############

set(DEPS std_msgs)#nav_msgs sensor_msgs std_msgs)

#######################################
## Declare ROS messages and services ##
#######################################

###################################################
## Declare things to be passed to other projects ##
###################################################

###########
## Build ##
###########

#add_executable(${PROJECT_NAME}/utm_odometry_node src/utm_odometry_node.cpp)
#set_target_properties(${PROJECT_NAME}/utm_odometry_node
#  PROPERTIES
#  OUTPUT_NAME "utm_odometry_node")
#target_link_libraries(${PROJECT_NAME}/utm_odometry_node ${LIBS})

#############
## Install ##
#############

#install(TARGETS ${PROJECT_NAME}/utm_odometry_node
#  ARCHIVE
#  DESTINATION lib
#  LIBRARY
#  DESTINATION lib
#  RUNTIME
#  DESTINATION lib/${PROJECT_NAME})

#install(DIRECTORY include/${PROJECT_NAME}/
#  DESTINATION include/${PROJECT_NAME})

#catkin_install_python(PROGRAMS nodes/fix_translator
#  DESTINATION lib/${PROJECT_NAME})

ament_export_dependencies(rosidl_default_generators)
ament_export_dependencies(ament_cmake)
ament_export_dependencies(std_msgs)
ament_export_include_directories(${INCLUDE_DIRS})

ament_package()
