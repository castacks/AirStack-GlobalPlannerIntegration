cmake_minimum_required(VERSION 3.5)
project(core_map_representation_interface)

# Find dependencies
find_package(ament_cmake REQUIRED)
find_package(airstack_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(pluginlib REQUIRED)
find_package(rclcpp REQUIRED)
find_package(rclpy REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(std_msgs REQUIRED)
find_package(tf2 REQUIRED)
find_package(tf2_ros REQUIRED)
find_package(visualization_msgs REQUIRED)

# Include directories
include_directories(
  include
  ${ament_INCLUDE_DIRS}
)

add_library(core_map_representation_interface INTERFACE)

ament_export_targets(core_map_representation_interfaceTargets HAS_LIBRARY_TARGET)
#ament_export_include_directories(include)
ament_export_dependencies(
  airstack_msgs
  geometry_msgs
  nav_msgs
  pluginlib
  rclcpp
  rclpy
  sensor_msgs
  std_msgs
  tf2
  tf2_ros
  visualization_msgs
)
install(
  TARGETS core_map_representation_interface
  EXPORT core_map_representation_interfaceTargets
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib
  RUNTIME DESTINATION bin
  INCLUDES DESTINATION include
)
# Install include files
install(
  DIRECTORY include/${PROJECT_NAME}/
  DESTINATION include/${PROJECT_NAME}
  FILES_MATCHING PATTERN "*.h"
)

# Install Python scripts (if you have any)###
# install(PROGRAMS
#   scripts/your_python_script.py
#   DESTINATION lib/${PROJECT_NAME}
# )


# Export dependencies


ament_package()
