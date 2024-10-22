cmake_minimum_required(VERSION 2.8.3)
project(waypoint_generator)


## Turn on verbose output
set(CMAKE_VERBOSE_MAKEFILE "true")

## Set C++14 standard directly, as required by ROS Noetic and PCL 1.10+
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

## Add some compile flags
set(ADDITIONAL_CXX_FLAG "-Wall -O3 -g")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${ADDITIONAL_CXX_FLAG}")


find_package(catkin REQUIRED COMPONENTS
  roscpp
  tf
  nav_msgs
)
catkin_package()

include_directories(include)
include_directories(
  ${catkin_INCLUDE_DIRS}
)

add_executable(waypoint_generator src/waypoint_generator.cpp)

target_link_libraries(waypoint_generator
   ${catkin_LIBRARIES}
)
