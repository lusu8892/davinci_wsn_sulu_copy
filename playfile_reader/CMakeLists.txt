cmake_minimum_required(VERSION 2.8.3)
project(playfile_reader)

find_package(catkin_simple REQUIRED)
find_package(Eigen3 REQUIRED)

include_directories(${EIGEN3_INCLUDE_DIR})
add_definitions(${EIGEN_DEFINITIONS})

catkin_simple()

# example boost usage
# find_package(Boost REQUIRED COMPONENTS system thread)

# C++0x support - not quite the same as final C++11!
# SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x")

# Libraries
# cs_add_library(my_lib src/my_lib.cpp)   

# Executables
cs_add_executable(playfile_jointspace src/davinci_playfile_jointspace.cpp)
cs_add_executable(playfile_cartspace src/davinci_playfile_cartspace.cpp)
cs_add_executable(playfile_cameraspace src/davinci_playfile_cameraspace.cpp)
target_link_libraries(playfile_jointspace davinci_joint_publisher ${catkin_LIBRARIES})
target_link_libraries(playfile_cartspace davinci_joint_publisher davinci_kinematics ${catkin_LIBRARIES})
target_link_libraries(playfile_cameraspace davinci_joint_publisher davinci_kinematics ${catkin_LIBRARIES})
cs_install()
cs_export()
    