project(cob_srvs)

catkin_project(${PROJECT_NAME}
  INCLUDE_DIRS include
  )

find_package(genmsg REQUIRED)

set(MSG_DEPS std_msgs trajectory_msgs geometry_msgs)

find_package(ROS REQUIRED ${MSG_DEPS})

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

# install all manifests; for compatibility with old build system
install(FILES manifest-to-install.xml
        DESTINATION share/cob_srvs RENAME manifest.xml)

