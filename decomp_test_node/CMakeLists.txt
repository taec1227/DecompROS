cmake_minimum_required(VERSION 2.8.3)
project(decomp_test_node)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -Wno-deprecated-declarations")

find_package(cmake_modules REQUIRED)
find_package(Eigen3 REQUIRED)
find_package(decomp_util REQUIRED)
find_package(catkin REQUIRED COMPONENTS roscpp decomp_ros_utils rosbag)

catkin_package(
    CATKIN_DEPENDS decomp_ros_utils rosbag
)

include_directories(include ${catkin_INCLUDE_DIRS}
    ${EIGEN3_INCLUDE_DIRS}
    ${DECOMP_UTIL_INCLUDE_DIRS}
)

add_executable(test_path_decomp_2d src/test_path_decomp_2d.cpp)
target_link_libraries(test_path_decomp_2d ${catkin_LIBRARIES})

add_executable(test_path_decomp_3d src/test_path_decomp_3d.cpp)
target_link_libraries(test_path_decomp_3d ${catkin_LIBRARIES})

add_executable(test_seed_decomp src/test_seed_decomp.cpp)
target_link_libraries(test_seed_decomp ${catkin_LIBRARIES})