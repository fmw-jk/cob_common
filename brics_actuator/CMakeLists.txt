project(brics_actuator)

catkin_project(${PROJECT_NAME}
  INCLUDE_DIRS include
)

find_package(genmsg REQUIRED)

set(MSG_DEPS geometry_msgs std_msgs)

find_package(ROS REQUIRED ${MSG_DEPS})

set(MSG_FILES
	CartesianPose.msg
	CartesianTwist.msg
	CartesianVector.msg
	CartesianWrench.msg
	JointAccelerations.msg
	JointConstraint.msg
	JointImpedances.msg
	JointPositions.msg
	JointTorques.msg
	JointValue.msg
	JointVelocities.msg
	Poison.msg
)

add_message_files(DIRECTORY msg FILES ${MSG_FILES})

generate_messages(DEPENDENCIES ${MSG_DEPS})

# install all manifests; for compatibility with old build system
install(FILES manifest-to-install.xml
        DESTINATION share/cob_srvs RENAME manifest.xml)

