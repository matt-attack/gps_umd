cmake_minimum_required(VERSION 3.5)
project(gps_common_msgs)

if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 11)
endif()

find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(builtin_interfaces REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME} 
  "msg/GPSStatus.msg" 
  "msg/GPSFix.msg"
  DEPENDENCIES builtin_interfaces
  std_msgs
)

install(FILES mapping_rules.yaml 
  DESTINATION share/${PROJECT_NAME})


ament_export_dependencies(rosidl_default_generators)
ament_export_dependencies(ament_cmake)
ament_export_dependencies(std_msgs)
ament_export_include_directories(${INCLUDE_DIRS})

ament_package()
