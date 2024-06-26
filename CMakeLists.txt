cmake_minimum_required(VERSION 3.5)
project(depth_converter)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# Find package dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(tf2_ros REQUIRED)
find_package(tf2_geometry_msgs REQUIRED)
find_package(Eigen3 REQUIRED)
find_package(riptide_msgs2 REQUIRED)

include_directories(include)

add_executable(${PROJECT_NAME} src/depth_converter.cpp)

ament_target_dependencies(${PROJECT_NAME}
  rclcpp
  geometry_msgs
  tf2_ros
  tf2_geometry_msgs
  Eigen3
  riptide_msgs2
)

install(TARGETS
  ${PROJECT_NAME}
  DESTINATION lib/${PROJECT_NAME}
)

ament_package()
