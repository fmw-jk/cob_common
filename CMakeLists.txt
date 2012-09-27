cmake_minimum_required(VERSION 2.8)
project(cob_common)

find_package(catkin REQUIRED)

catkin_stack()

add_subdirectory(brics_actuator)
add_subdirectory(cob_description)
#add_subdirectory(cob_goco)
add_subdirectory(cob_srvs)
#add_subdirectory(desire_description)
#add_subdirectory(raw_description)

