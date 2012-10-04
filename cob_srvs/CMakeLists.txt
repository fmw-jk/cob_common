cmake_minimum_required(VERSION 2.8)
project(cob_srvs)

find_package(genmsg REQUIRED)

set(MSG_DEPS geometry_msgs std_msgs trajectory_msgs)

find_package(catkin REQUIRED ${MSG_DEPS})

catkin_project(${PROJECT_NAME}
  INCLUDE_DIRS include
  )

set(SRV_FILES 
  GetPoseStampedTransformed.srv
  SetDefaultVel.srv
  SetJointStiffness.srv
  SetJointTrajectory.srv
  SetMaxVel.srv
  SetOperationMode.srv
  Trigger.srv
)

add_service_files(DIRECTORY srv FILES ${SRV_FILES})

generate_messages(DEPENDENCIES ${MSG_DEPS})


