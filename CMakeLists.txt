cmake_minimum_required(VERSION 2.8.3)
project(bpcg)
set(CMAKE_CXX_FLAGS "-std=c++0x ${CMAKE_CXX_FLAGS}")
list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

find_package(catkin REQUIRED COMPONENTS
  roscpp
)
find_package(Boost REQUIRED)
find_package(Eigen REQUIRED)

catkin_package(
 INCLUDE_DIRS include
 LIBRARIES bpcg
 CATKIN_DEPENDS roscpp
 DEPENDS system_lib Eigen Boost
)

include_directories(
  ${catkin_INCLUDE_DIRS}
  ${EIGEN_INCLUDE_DIR}
  ${Boost_INCLUDE_DIRS}
  include
)

add_library(bpcg
  src/bpcg.cpp
)

target_link_libraries(bpcg
      ${catkin_LIBRARIES}
)
